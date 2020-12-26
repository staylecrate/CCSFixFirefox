# CCSFixFirefox
Fixes for Firefox &amp; Waterfox
## How to fix Multirow Bookmarks Toolbar on 69+ in Windows
1. Open <em>about:config</em> in the URL bar and click "Accept the Risk and Continue"
2. Search for the <em>toolkit.legacyUserProfileCustomizations.stylesheets</em> key and change its value to <strong>true</strong>.
3. Open the folder "AppData/Roaming/Mozilla/Firefox/Profiles/<em>profile name</em>" and create a folder named <em>chrome</em>. For Example "AppData/Roaming/Mozilla/Firefox/Profiles/ay0hc227.default/chrome".
4. Create a new text document. Make sure that the "Hide extensions for known file types" option is unchecked in Folder Options.
5. Change the name of the file from New Text Document.txt to userChrome.css
6. Right-click on the file and click Edit or Open With>Notepad
7. Copy and paste this what is below and save it. If Firefox is open, close and relaunch it.

/* Makes bookmarks toolbar span multiple rows */

#PersonalToolbar{
  --multirow-bmb-n-rows: 3; /* Control how many rows are shown before scrolling */
  --multirow-bmb-row-margin: 2px; /* Control how much spacing is between rows */
  max-height: none !important;
}

#PlacesToolbar > hbox{ 
  display: block;
  width: 100vw;
}

#PlacesToolbarItems{
  display: flex;
  flex-wrap: wrap;
  /* --uc-bm-padding is defined in autohide_bookmarks_toolbar.css */
  max-height: calc(var(--multirow-bmb-n-rows) * (5px + 1em + (2 * (var(--multirow-bmb-row-margin) + var(--uc-bm-padding,2px))))) !important;
  overflow-y:auto;
  scrollbar-color: var(--lwt-accent-color) var(--toolbar-bgcolor) ;
  scrollbar-width: thin;
}

/* Hide the all-bookmarks button */
#PlacesChevron{ display: none }

/* Add some spacing between rows */
#PlacesToolbarItems > .bookmark-item{ margin: var(--multirow-bmb-row-margin) 3px !important; }
