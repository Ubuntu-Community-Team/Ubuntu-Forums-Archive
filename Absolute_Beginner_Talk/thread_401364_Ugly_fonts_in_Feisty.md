---
title: "Ugly fonts in Feisty"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Crakie on 2007-04-04
I noticed some fonts really look terrible in Kubuntu Feisty. What I am looking at now while typing, for example, is awful. Open Office is not great either. Strange thing is, the menus look fine to me. So not ALL fonts are rendered ugly. Any ideas on how to improve this?

---

### Post by chalex on 2007-04-04
First, look at your sub-pixel smoothing options if you're using an LCD.  In GNOME, it's System->Preferences->Font.

Second, install the MS fonts. The package name is msttcorefonts.

---

### Post by Michaelt74 on 2007-04-04
This may help, I agree, the default Ubuntu fonts are weird

[http://ubuntuforums.org/showthread.php?t=208396](http://ubuntuforums.org/showthread.php?t=208396)

---

### Post by Crakie on 2007-04-06
I installed the Lucida Grande font, well known from the Mac OSX and enabled sub-pixel smoothing. Everything is looking nice now OUTSIDE Firefox, which somehow does not accept the system default. Menus, tab titles etc are still ugly. Fiddling with Firefox's own settings does not help either. I also think the rendered webpages don't look particularly attractive. 

I don't like the skin-and-bones look of MS fonts. I like them with some meat on the bones... not to say fat ;)

---

### Post by lebabyg on 2007-04-06
I agree, Lucida Grande is definitely the way forward when it comes to fonts on KDE.  The problem that you're having with firefox (and thunderbird if you use it), is that they use their own font rendering system.  This is accessed by changing a file called userChrome.css located in the .mozilla/firefox/{loadofnumbers}.default/chrome.  You need to edit this to make fonts look good.  I couldn't get the Lucida family to work, so I use Tahoma which also looks good.  Here is my file (that I copied from somebody's website, and changed to Tahoma), copy and paste, and edit to suit:
> /* The following four lines were added by KDE */
scrollbarbutton[sbattr="scrollbar-up-top"] { display: -moz-box !important; }
scrollbarbutton[sbattr="scrollbar-down-top"] { display: none !important; }
scrollbarbutton[sbattr="scrollbar-up-bottom"] { display: -moz-box !important; }
scrollbarbutton[sbattr="scrollbar-down-bottom"] { display: -moz-box !important; }
/*===========================================================================
*   Author:  Daigoro F. Toyama
*==========================================================================*/
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul");

/*===========================================================================
*   Main Window Edits
*==========================================================================*/
window {
  font-size: 8pt !important;
  font-family: Tahoma !important;
}

#sidebar {
  font-size: 8pt !important;
  font-family: Tahoma !important;
}

/*===========================================================================
*   Dialog Box Edits
*==========================================================================*/
dialog, box, button, page {
    font-size: 8pt !important;
    font-family: Tahoma !important;
}

label {
    font-size: 8pt !important;
    font-family: Tahoma !important;
}

caption {
    font-size: 8pt !important;
    font-family: Tahoma !important;
}

textbox {
    font-size: 8pt !important;
    font-family: Tahoma !important;
}

/*===========================================================================
*   Menu Edits
*==========================================================================*/
menubar > menu {
  font-size: 8pt !important;
  font-family: Tahoma !important;
  /* font-weight: bold !important; */
}

menupopup > * {
  font-size: 8pt !important;
  font-family: Tahoma !important;
}

/*===========================================================================
*    Toolbar Edits
*==========================================================================*/
/* Reduce the space between text and borders */
toolbarbutton.bookmark-item {
  padding: 1px !important;
}

/* Change the font style on the bookmark toolbar */
.toolbarbutton-text {
  font-size: 8pt !important;
  font-family: Tahoma !important;
  /* color: #ffffff !important; */
  color: #000000 !important;
}

/*===========================================================================
*   Tab Edits
*==========================================================================*/
/* change the font style on the tabs */
.tab-text {
    font-size: 8pt !important;
    font-family: Tahoma !important;
}

/* make inactive tabs hardly visible :) */
tab:not([selected="true"]) {
    -moz-opacity: 0.5 !important;
}

/*
.tabbrowser-strip tab:not([selected="true"]) .tab-text {
    font-size: 14pt !important;
    font-weight: bold !important;
}
*/

/* hide the text of the inactive tabs */
/*
.tabbrowser-strip tab:not([selected="true"]) .tab-text {
 display: none !important;
}
*/

/* never show "Open in New Window" when right clicking */
#context-openlink {
    display: none !important;
}

/*===========================================================================
*   Throbber Edits
*==========================================================================*/
/* change the throbber icons */
/*
#navigator-throbber {
    list-style-image : url("../../../../icons/icon20_s.jpg") !important;
}

#navigator-throbber[busy="true"] {
    list-style-image : url("inukag_gif.gif") !important;
}
*/

/*===========================================================================
*   Turn off the dropdown functionality of the URL and search bars
*==========================================================================*/
/*
autocomplete-history-dropmarker {
    display:none !important;
}
.autocomplete-tree {
    display:none !important;

I also changed some fonts in firefox by entering about:config in the URL window and changing font.default.x-western to sans-serif
font.name.monospace.x-western to DejaVu Sans Mono
font.name.sans-serif.x-western to DejaVu Sans
font.name.serif.x-western to Nimbus Roman No9 L

Firefox now looks an aweful lot nicer!!!

---

