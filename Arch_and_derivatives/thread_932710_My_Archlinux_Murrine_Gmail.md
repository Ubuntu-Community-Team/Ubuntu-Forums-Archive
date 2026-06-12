---
title: "My Archlinux Murrine Gmail"
date: 2008-09-28
forum: Arch and derivatives
---

### Post by crimesaucer on 2008-09-28
Check out my Archxfce4 Murrine gmail:

[img]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-16b.png[/img]
Large View: [http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-16a.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-16a.png)

---

### Post by MisfitI38 on 2008-09-28
*Very* cool.

---

### Post by SkonesMickLoud on 2008-09-29
Nice, I'm in the process of getting my shiny new @archlinux.us all set up.

---

### Post by K.Mandla on 2008-10-01
:shock:

[IMG]http://icanhascheezburger.files.wordpress.com/2007/05/do-want.jpg[/IMG]

---

### Post by crimesaucer on 2008-10-01
> **K.Mandla said:**
> :shock:

[IMG]http://icanhascheezburger.files.wordpress.com/2007/05/do-want.jpg[/IMG]

This is the page from Stylish: [http://userstyles.org/styles/10529](http://userstyles.org/styles/10529)

This is the gray/black re-write.... you can change the colors and the font:

```

/*
 * Better Gmail2 Skin - Brownie
 *
 * Author      : PP Lanceret
 * Created     : Sep. 16 2008
 * Updated     : 
 * Website     : http://lazhaus.com/
 * Description : Restyled page for Gmail.
 * Usage       : Use with Stylish Firefox extension (http://userstyles.org/) or copy to your Firefox userContent.css file
 */
@namespace url(http://www.w3.org/1999/xhtml);
@-moz-document domain("mail.google.com") {

/* --------------- base --------------- */
*{
color : #000000 !important;
font-family : eurofurence, arial, san-serif !important;}

.e7Tcgd, #loading {background-color : #EBEBEB !important;}

/********************************************************************/

/* --------------- header --------------- */
.UiIfsf{background-color : #858685 !important;
border-color : #000 !important;}

#gbar{padding-left : 5px !important;}
.gb1{margin-right : .3em !important;
color : #f2f1df !important;}

#gbar a, #gbar a:active, #gbar a:visited, .VUNkxf u, .VUNkxf small,
.l73JSe, .nQ6QTe nobr, .nQ6QTe nobr b{
color : #f2f1df !important;
text-decoration : none !important;}

/* more menu */
#gbi {border : 1px solid #673c56 !important;}
#gbar a.gb2.VUNkxf {color : #000000 !important;}
#gbar a.gb2.VUNkxf:hover {background: #F8F8F8 !important;}

/* --------------- input textarea select --------------- */
input, textarea, select,
.OYmQme, .Y1jEjc .JRJslf,
.manager-page .toolbar .search-box,
.manager-page .add-to-group-box,
.manager-page .goog-flat-button{
border: 1px solid #673c56 !important;
background-color: #f2efef !important;
-moz-appearance: none !important;}

input[type=checkbox], input[type=radio] {
-moz-appearance: checkbox !important;}

.iE5Yyc, .manager-page input{
font-size : 15px !important;
border : none !important;
background-color : #f2efef !important;}

#contact-pane input{
border: 1px solid #673c56 !important;}

.Gjckbb {font-size : 14px !important;}

/********************************************************************/

/* --------------- frame color --------------- */
/* main */
.oi23Hf .R7iiN, .lLzmXd .R7iiN,
/* Editer main*/
.Gdbtkf .c1I77d, .Y1jEjc .c1I77d,
.Y1jEjc .c1norb, .Y1jEjc .kwmAmd, .Y1jEjc .m8lwn, .Y1jEjc .vHYYR,
.Y1jEjc .P0tbHb, .uQLZXb form, .VByZEe, .BldZyd,
.Gdbtkf .c1I77d, .uQLZXb,
/* selected menu */
.cOSVMd .c1norb, .cOSVMd .kwmAmd, .cOSVMd .m8lwn,
.cOSVMd .vHYYR, .cOSVMd .wRoeNc, .cOSVMd .Hemrjb,
.ybaOyc .c1norb, .ybaOyc .kwmAmd, .ybaOyc .m8lwn, 
.ybaOyc .vHYYR, .ybaOyc .wRoeNc, .ybaOyc .Hemrjb,
.cBhtOe .NIPhib .zD5BAe,
/* Contacts */
.manager-page .toolbar
{background-color : #969696 !important;}

/* main corner */
.oi23Hf .P0tbHb, .lLzmXd .P0tbHb, .oi23Hf .wRoeNc, .lLzmXd .wRoeNc,
.oi23Hf .F2yfRe, .lLzmXd .F2yfRe, .oi23Hf .Hemrjb, .lLzmXd .Hemrjb,
/* Editer main coner */
.Y1jEjc .wRoeNc, .Y1jEjc .P0tbHb, .Y1jEjc .Hemrjb, .Y1jEjc .F2yfRe,
/* selected menu corner */
.ybaOyc .P0tbHb, .ybaOyc .F2yfRe, .cOSVMd .P0tbHb, .cOSVMd .F2yfRe
{background-image : url(https://mail.google.com/mail/rc?a=af&c=b59389969696&w=4&h=4) !important;}

/* Spam Trash main */
.xNSvsd .R7iiN,
/* selected Spam Trash */
.cBhtOe .NIPhib,
.IyrUZb .c1norb, .IyrUZb .kwmAmd, .IyrUZb .vHYYR, .IyrUZb .m8lwn,
.IyrUZb .wRoeNc, .IyrUZb .Hemrjb
{background-color : #A59A8E !important;}

/* Spam Trash main corner */
.xNSvsd .P0tbHb, .xNSvsd .wRoeNc, .xNSvsd .F2yfRe, .xNSvsd .Hemrjb,
/* selected Spam Trash menu corner */
.IyrUZb .P0tbHb, .IyrUZb .F2yfRe
{background-image : url(https://mail.google.com/mail/rc?a=af&c=a0a58eA59A8E&w=4&h=4) !important;}

/* Labels Item main */
.ar6Hkf .R7iiN,
/* Search Options main */
.BBrt4c .kwmAmd, .BBrt4c .wWwc8d, .BBrt4c .c1norb, .ny3hZb .c1norb,
.ny3hZb .kwmAmd, .ny3hZb .vHYYR, .ny3hZb .m8lwn, .ny3hZb .wRoeNc
{background-color : #92b5b0 !important;}

/* Labels Item main corner*/
.ar6Hkf .P0tbHb, .ar6Hkf .wRoeNc, .ar6Hkf .F2yfRe, .ar6Hkf .Hemrjb,
/* Search Options corner */
.BBrt4c .P0tbHb, .BBrt4c .wRoeNc, .ny3hZb .P0tbHb,
.ny3hZb .F2yfRe, .ny3hZb .Hemrjb
{background-image : url(https://mail.google.com/mail/rc?a=af&c=92b5b0&w=4&h=4) !important;}

/* Settings main */
.TPdeOc .R7iiN, .lowmzb, .tAYBjb .GVhBfc, .tAYBjb .AiCerc,
/* Create a filter main */
.YKsXMe .kwmAmd, .YKsXMe .wWwc8d, .YKsXMe .c1norb, .Z1uQkf .c1norb,
.Z1uQkf .kwmAmd, .Z1uQkf .vHYYR, .Z1uQkf .m8lwn, .Z1uQkf .wRoeNc{
background-color : #bca37c !important;}

/* Settings corner */
.TPdeOc .P0tbHb, .TPdeOc .wRoeNc, .TPdeOc .F2yfRe, .TPdeOc .Hemrjb,
/* Create a filter corner */
.YKsXMe .P0tbHb, .YKsXMe .wRoeNc, .Z1uQkf .P0tbHb,
.Z1uQkf .F2yfRe, .Z1uQkf .Hemrjb{
background-image : url(https://mail.google.com/mail/rc?a=af&c=bca37c&w=4&h=4) !important;}

/* Chat Window main*/
.AWqJIf .kwmAmd ,.AWqJIf .c1norb, .AWqJIf .vHYYR, .AWqJIf .wWwc8d
{background-color : #966b6b !important;}

/* Chat Window corner */
.AWqJIf .P0tbHb , .AWqJIf .wRoeNc{
background-image : url(https://mail.google.com/mail/rc?a=af&c=966b6b&w=3&h=3) !important;}


/* message */
.n38jzf .Ptde9b, .n38jzf .m14Grb{
background: #f2e8c9 !important;}

.n38jzf .zIVQRb, .n38jzf .Qrjz3e, .n38jzf .Gbtri, .n38jzf .gmNpMd{
background-image : url(https://mail.google.com/mail/rc?a=af&c=f2e8c9&w=4&h=4) !important;}

/********************************************************************/

/* --------------- main menu --------------- */
/* select, refresh, counter */
.bKmyId, .bsABdf, .DiWSpb,.vZFPPc, .z8N7nd, .vwcZUe,
.xNSvsd .bSwwie .l73JSe{
font-size : 14px !important;}

span[selector^="all"],span[selector^="none"],
span[selector^="read"],span[selector^="unread"],
span[selector^="starred"]{
padding-right : 5px !important;}

/* info space */
.Ch5Hj, .YdYocf {background : #CECECE !important;}

/* more action hover */
.QOD9Ec {border : 1px solid #673c56 !important;}
.P0GJpc{background-color : #F8F8F8 !important;}

/* read mail */
.AnqB9d {background : #E2E2E2 !important;}

/* unread mail */
.QhHSYc {background-color : #f4eff4 !important;}

/* selected mail */
.rfza3e {background-color : #A59A8E !important;}

/* hover item */
tr[class^="xweT7d AnqB9d"]:hover,
tr[class^="xweT7d QhHSYc"]:hover {
background-color : #fff9ff !important;}

.Cipym{
background-color : #f2f2ed !important;
border : none !important;}

/* --------------- left menu --------------- */
/* hide ion */
.gUlKtd, .aBJ8he {display : none !important;}

/* menu */
.XoqCub .NIPhib{
margin-left : -2px !important;
border-bottom : 1px dashed #000 !important;}

.NIPhib .zD5BAe, .NIPhib .Tm9rOd{
padding : 2px 0 2px 3px !important;
text-decoration : none !important;
background-color : transparent !important;
font-size : 15px !important;
color : #000000 !important;
display: block !important;}

.XoqCub .NIPhib:hover{
color : #ec7000 !important;
border-bottom : 1px dashed #ec7000 !important;}

.NIPhib .zD5BAe:hover, .NIPhib .Tm9rOd:hover{
color : #ec7000 !important;}

.ACpQre .R7iiN, .ACpQre .wWwc8d{
background-color : transparent !important;}

/* chat & labels */
.Tzvkxd .XoqCub .Pj5gjf, .XoqCub .Hc3Vg .XoqCub .Pj5gjf
{display : none !important;}

.a3hTGd .R7iiN, .XPj4ef .R7iiN{
width : 145px !important;
background-color : transparent !important;}

.qHJVCb{
background-color : #F8F8F8 !important;
border-bottom : 1px solid #c6c5b1 !important;}

.M3aZbb td{border-top : 1px solid #c6c5b1 !important;}

.WDwv9d, .dH86Yd, .GTx9Hd {background : #CECECE !important;}

.nM7i0, .WDwv9d{
font-family : arial, san-serif !important;}

.HQ6yBd {background-color : #e2eff4 !important;}

/* Popup menu*/
.FVNmUc .Pbwkb, .FVNmUc .Pbwkb, .FVNmUc .exMFFe, .FVNmUc .exMFFe{
background-color : #c6aaa3 !important;}

.V3nuZd .goog-menuitem
{background-image : none !important;
background-color : #F8F8F8 !important;
border-bottom : 1px solid #c6c5b1 !important;}

.V3nuZd .goog-menuseparator{
background-color : #F8F8F8 !important;
border-right : 1px solid #c6c5b1 !important;}

.wcU0wf, .VwVWqc, .GCQ5W, .pBgL5e, .zoHs5e, .AWvUZb, .qlMg0e{
background-image : none !important;}


/* Status Options, Chat Options */
.I24Uab {border : none !important;}

.O7GAEf, .DYHi6d, .a3hTGd .DYHi6d{
background-color : #fff !important;
border : 1px solid #673c56 !important;}

.O7GAEf hr {background-color : #CECECE !important;}
.j665Sd, .a3hTGd .McPZQe{background-color : #F8F8F8 !important;}

.E4KNxe {border-top : 1px solid #F8F8F8 !important;}

.a3hTGd .Tzvkxd .P0tbHb, .a3hTGd .Tzvkxd .wRoeNc,
.a3hTGd .F2yfRe, .a3hTGd .Hemrjb,
.XPj4ef .Tzvkxd .P0tbHb, .XPj4ef .Tzvkxd .wRoeNc,
.XPj4ef .F2yfRe, .XPj4ef .Hemrjb{
background-image : none !important;}

.HSZged{font-size : 15px !important;}

.oggeve, .uAn3he, .XPj4ef .Qj7Rff{
border-bottom : 1px dashed #000 !important;}

.WnHkDd:hover, .HSZged:hover {color : #ec7000 !important;}
.oggeve:hover {border-bottom : 1px dashed #ec7000 !important;}

td.o186ac, td.G6Lv5d, td.FKRsx, td.UXL9pb, td.hdc97, td.EcrCQe{
border : none !important;}

.a3hTGd .dH86Yd, .a3hTGd .GTx9Hd{
border-color : transparent !important;}

/* Labels background */
.pvSW6e, .Qj7Rff{background-color: #F8F8F8 !important;}

.pvSW6e .zD5BAe{
text-decoration : none !important;
display: block;}

.pvSW6e .zD5BAe:hover{text-decoration : underline !important;}

/* chat search & invite a friend */
.aBJ8he, .gUlKtd, .I94Sdc .R7iiN,.p9ILHf,
.I94Sdc .Tzvkxd .P0tbHb, .I94Sdc .F2yfRe,
.I94Sdc .Tzvkxd .wRoeNc, .I94Sdc .Hemrjb{
display:none !important;}

/********************************************************************/
/* --------------- mail view --------------- */

/* Hide Ads */
.yxEQwb, .iFOJMb{display : none !important;}

table[class*="PwUwPb XoqCub MMcQxe"], td.eWTfhb > div.ice3Ad{
width : 99% !important;}

.f3hr3b > table.PwUwPb > tr > td.eWTfhb > .XoqCub{
width : 100% !important;}

.yMuNaf{
position : absolute !important;
left : 0 !important;
top : 20px !important;}

.jsbnre{padding-bottom : 20px !important;}

.OZly4d, .m2U49e{
float : left !important;
margin-right : 10px !important;}

td.eWTfhb > .XoqCub{
width : 0px !important;
overflow : visible !important;}

.aWL81 .z1IiMc{display : none !important;}

/* background(outer) */
.MMcQxe{
top : 2px !important;
background-color : #CECECE !important;
-moz-border-radius: 3px ! important;}

.R7iiN .m8lwn {display : none !important;}

/* background(inner) */
.YrSjGe{
background-color : #F8F8F8 !important;
-moz-border-radius: 3px ! important;}

/* Subject */
.VrHWId {font-size : 15px !important;}

/* details */
.InqsWb .ObUWHc, .qNeRme, .un3FG{
border-bottom : 1px dashed #000 !important;
margin : 0 10px 20px 10px !important;}

/* display message */
.XwckWe {background-color: #d8ddd3 !important;}

/* text */
.ArwC7c {font-size : 15px !important;}

/* text link */
.YrSjGe a:hover, .YrSjGe a:visited{
color : #904060 !important;}
.YrSjGe a{color : #5b6d82 !important;}

.rGOYzc .P0tbHb, .rGOYzc .c1norb,
.rGOYzc .vHYYR, .rGOYzc .F2yfRe,
.rGOYzc .Hemrjb, .rGOYzc .m8lwn, .rGOYzc .kwmAmd {
background-image : none !important;
background-color: #F8F8F8 !important;}

.LYI6Sd, .eNXyxd{
background-color : #CECECE !important;
background-image : none !important;}

/********************************************************************/
/* --------------- Contacts --------------- */
.manager-page body, .manager-page td, .manager-page div{
font-family : arial, san-serif !important;}

.scrollable > .scroll-content{
background-color : #f7f6f2 !important;}

.manager-page .rightsep{
border-right : 2px solid #c1ada8 !important;}

.manager-page .menu{
border : 1px solid #673c56 !important;}

.contacts-list-actions,
.manager-page .editbar{
background-color : #F8F8F8 !important;
border-top : 1px solid #CECECE !important;
border-bottom : 1px solid #CECECE !important;}

.group-list hr.header,
.group-list-secondary .selected,
.group-list .selected, .checkable-list .selected{
background-color : #CECECE !important;}

.manager-page .menu .menu-item-selected,
.group-list .active, .checkable-list .active{
background-color : #F8F8F8 !important;}

.contact-pane .contact-banner{
border-top : 1px solid #CECECE !important;
border-bottom : 1px solid #CECECE !important;}

/* --------------- editer --------------- */
.Gdbtkf .R7iiN, .Gdbtkf .z1IiMc{
background-color : #d6baaf !important;}

/* Rich Text icon */
.rwfzSd {border : none !important;}

/* Check Spelling */
.NQ52{
background : #fff !important;
border : 1px solid #673c56 !important;}
.NQ52 .goog-menuitem-highlight{
background : #F8F8F8 !important;}

.l4dHEb .wRoeNc{background : #F8F8F8 !important;}

/* Drafts */
.opUkHb .yaEVMb {border : 1px solid #673c56 !important;}

/* --------------- Chat Window --------------- */
.gMivnd, .v0fLnc{background : #f9f9f9 !important;}

.w85PXe, .AhBfRd{
background : #F8F8F8 !important;
border : 1px solid #673c56 !important;}

.HFJj2b:hover {background : #CECECE !important;}

/* --------------- Settings --------------- */
.tAYBjb .ZOB6Zc, .eGbrz{
background :  #f2e8c9 !important;}
.GorKne td.Wnp2lb, .GorKne td.WwReqb,
.IoBQdd, .DwFWUd, .A5gIhd, .NuOXpe, .FceqAb{
background :  #f2e8c9 !important;
border-bottom : 2px solid #ebe1a9 !important;}

.GorKne td.TtHZK {border-top : 2px solid #ebe1a9 !important;}
.YVweLb .ZOB6Zc, .yolZre {border :none !important;}
.lwwhL {background :  #ebe1a9 !important;}

.GorKne .l73JSe {color : #000000 !important;}

/* --------------- Search Options --------------- */
.ny3hZb .wWwc8d{background :  #c9d6d8 !important;}

/* --------------- Create a filter --------------- */
.Z1uQkf .wWwc8d{background :  #f2e8c9 !important;}
.Z1uQkf .l73JSe {color : #000000 !important;}

/* --------------- footer --------------- */
.s7hnoe, .VfONdd, .IUntof {display : none !important;}

}

```


This is the gmail logo page: [http://userstyles.org/styles/4579](http://userstyles.org/styles/4579)

This is my gray/black logo base64 script: 

```

/*Coded by gnf 12/27/07 Ver 1.0*/
@namespace url(http://www.w3.org/1999/xhtml);
@-moz-document domain(mail.google.com) {

/*logo [for using an own logo: change data-url to a png-image you like (143px x 59px)]*/
.zYsCRb 
{ background: url("data:image/png;base64,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
xiPjH+H/ACifI83KhxfeAAAAAElFTkSuQmCC")  !important; }

}

```


Then get the new Murrine-SVN from AUR: [http://aur.archlinux.org/packages.php?ID=18624](http://aur.archlinux.org/packages.php?ID=18624)


And after that, create your own directory: /usr/share/themes/MurrineNEW_silver/gtk-2.0/

and put my gtkrc in it:

```

style "theme-default"
{
  GtkButton      ::default_border    = { 0, 0, 0, 0 }
  GtkRange       ::trough_border     = 0
  GtkPaned       ::handle_size       = 3
  GtkRange       ::slider_width      = 15
  GtkRange       ::stepper_size      = 15

  GtkScrollbar   ::min_slider_length = 35
  GtkCheckButton ::indicator_size    = 15
  GtkMenuBar     ::internal-padding  = 0
  GtkTreeView    ::expander_size     = 15
  GtkExpander    ::expander_size     = 15
  GtkScale       ::slider-length     = 24
  
  xthickness = 1
  ythickness = 1

  fg[NORMAL]        = "#000000" # option menu, button font, open tab
  fg[PRELIGHT]      = "#000000" # font color of menu roll over, and roll over fro radio/check boxes as well as button, Option button, and toggle button prelights.
  fg[SELECTED]      = "#000000" # Gtk combo font for drop down
  fg[ACTIVE]        = "#000000" # toggle font color, and active font for check/radio boxes, also for un-clicked tabs.
  fg[INSENSITIVE]   = "#4b4440" # little arrows on scrolls

  bg[NORMAL]        = "#E2E2E2"
  bg[PRELIGHT]      = "#E2E2E2"
  bg[SELECTED]	     = "#D6D6D6" # menu selected roll over, and xfwm4 color 
  bg[INSENSITIVE]   = "#E2E2E2"  # background scroll arrows
  bg[ACTIVE]        = "#E2E2E2" # this (strangely) controls inactive tab BGs

  base[NORMAL]      = "#FFFFFF"
  base[PRELIGHT]    = "#878887"
  base[ACTIVE]      = "#B0B0B0"
  base[SELECTED]    = "#878887"
  base[INSENSITIVE] = "#878887"

  text[NORMAL]      = "#000000" # font color for combo box (lame setting)
  text[PRELIGHT]    = "#000000" 
  text[ACTIVE]      = "#000001"
  text[SELECTED]    = "#FFFFFF"
  text[INSENSITIVE] = "#4b4440"

  engine "murrine" 
  {
menuitemstyle = 2 # 0 = flat, 1 = glassy, 2 = striped
	 scrollbar_color     = "#D6D6D6"
	 contrast 			   = 1.0
glazestyle = 0 # 0 = flat hilight, 1 = curved hilight, 2 = concave style
	 menubarstyle = 3 # 0 = flat, 1 = glassy, 2 = gradient, 3 = striped
	 menubaritemstyle = 0 # 0 = menuitem look, 1 = button look
menuitemstyle = 1 # 0 = flat, 1 = glassy, 2 = striped
	 listviewheaderstyle = 1 # 0 = flat, 1 = glassy
	 roundness = 0 # 0 = squared, 1 = old default, more will increase roundness
    animation = TRUE # FALSE = disabled, TRUE = enabled
  }
}


style "theme-wide" = "theme-default"
{
  xthickness = 2
  ythickness = 2
}

style "theme-wider" = "theme-default"
{
  xthickness = 3
  ythickness = 3
}

style "theme-entry" = "theme-wider"
{
  bg[SELECTED]	    = "#878887" # url box outline
}

style "theme-button" = "theme-wider"
{
  bg[NORMAL]        = "#D6D6D6"
  bg[INSENSITIVE]   = "#D6D6D6"
  bg[PRELIGHT]      = "#EBEBEB"
  bg[ACTIVE]	     = "#878887"
  text[NORMAL]      = "#000001"
}

style "theme-notebook" = "theme-wide"
{
  bg[NORMAL]      = "#EBEBEB"
  bg[INSENSITIVE] = "#EBEBEB"
  bg[SELECTED]    = "#878887"
}

style "theme-tasklist" = "theme-default"
{
  xthickness = 5
  ythickness = 3
}

style "theme-menu" = "theme-default"
{
  xthickness = 2
  ythickness = 1
}

style "theme-menu-item" = "theme-default"
{
  ythickness = 3
  fg[NORMAL] = "#000000"  # text for menubar and drop down menu
  #fg[PRELIGHT] = "#FFFFFF"
  text[PRELIGHT] = "#000000" # text on combox entry dropdown menu prelight-roll over
}

style "theme-menubar" = "theme-default"
{
  bg[NORMAL] = "#878887"
  fg[NORMAL] = "#FFFFFF"
  fg[ACTIVE] = "#FFFFFF"
  text[NORMAL] = "#FFFFFF"
  text[PRELIGHT] = "#FFFFFF"
  base[PRELIGHT] = "#5D8D76"
  base[SELECTED] = "#4DB224"
}

style "theme-menubar-item"
{
	ythickness = 4
	fg[PRELIGHT] = "#000000"  # prelight font color of menubar
	bg[PRELIGHT] = "#000000"
}

style "theme-tree" = "theme-default"
{
  xthickness = 2
  ythickness = 2
}

style "theme-frame-title" = "theme-default"
{
  fg[NORMAL] = "#000000"
}

style "theme-tooltips" = "theme-default"
{
  xthickness = 4
  ythickness = 4
  bg[NORMAL] = { 1.0,1.0,0.75 }
}

style "theme-progressbar" = "theme-wide"
{
  xthickness = 1
  ythickness = 1
  fg[PRELIGHT]  = "#878887"
}

style "theme-combo" = "theme-button"
{
  text[NORMAL]      = "#000000"
}

style "metacity-frame"
{
  # Normal base color
  #bg[NORMAL]  = "#bbbbbb"

  # Unfocused title background color
  #bg[INSENSITIVE]  = { 0.8, 0.8, 0.8 }

  # Unfocused title text color
  #fg[INSENSITIVE]  = { 1.55, 1.55, 1.55 }

  # Focused icon color
  #fg[NORMAL]  = { 0.2, 0.2, 0.2 }

  # Focused title background color
  #bg[SELECTED]  = "#444444"
  #base[ACTIVE]  = "#f2f2f2"

  # Focused title text color
  fg[SELECTED]  = "#E2E2E2"
}
class "MetaFrames" 	  style "metacity-frame"
class "GtkWindow"      style "metacity-frame"

# widget styles
class "GtkWidget"      style "theme-default"
class "GtkButton"      style "theme-button"
class "GtkScale"       style "theme-button"
class "GtkCombo"       style "theme-button"
class "GtkRange"       style "theme-wide"
class "GtkFrame"       style "theme-wide"
class "GtkMenu"        style "theme-menu"
class "GtkEntry"       style "theme-entry"
class "GtkMenuItem"    style "theme-menu-item"
class "GtkNotebook"    style "theme-notebook"
class "GtkProgressBar" style "theme-progressbar"
class "*MenuBar*"      style "theme-menubar"

widget_class "*MenuItem.*" style "theme-menu-item"
widget_class "*MenuBar.*"  style "theme-menubar-item"

# combobox stuff
widget_class "*.GtkComboBox.GtkButton" style "theme-combo"
widget_class "*.GtkCombo.GtkButton"    style "theme-combo"
# tooltips stuff
widget_class "*.tooltips.*.GtkToggleButton" style "theme-tasklist"
widget "gtk-tooltips" style "theme-tooltips"

# treeview stuff
widget_class "*.GtkTreeView.GtkButton" style "theme-tree"
widget_class "*.GtkCTree.GtkButton" style "theme-tree"
widget_class "*.GtkList.GtkButton" style "theme-tree"
widget_class "*.GtkCList.GtkButton" style "theme-tree"
widget_class "*.GtkFrame.GtkLabel" style "theme-frame-title"

# notebook stuff
widget_class "*.GtkNotebook.*.GtkEventBox" style "theme-notebook"
widget_class "*.GtkNotebook.*.GtkViewport" style "theme-notebook"


```

---

### Post by crimesaucer on 2008-10-02
I just made this for the default Archlinux forums look:

[IMG]http://i480.photobucket.com/albums/rr169/Arch-newb/Gmail-Arch-1.png[/IMG]

Large View: [http://i480.photobucket.com/albums/rr169/Arch-newb/Gmail-Arch.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Gmail-Arch.png)


You will want this font: [http://www.urbanfonts.com/fonts/Karat.htm](http://www.urbanfonts.com/fonts/Karat.htm)
..... or you might want the real Archlinux font that cost's money.


Here is the user script:

```

/*
 * Better Gmail2 Skin - Brownie
 *
 * Author      : PP Lanceret
 * Created     : Sep. 16 2008
 * Updated     : 
 * Website     : http://lazhaus.com/
 * Description : Restyled page for Gmail.
 * Usage       : Use with Stylish Firefox extension (http://userstyles.org/) or copy to your Firefox userContent.css file
 */
@namespace url(http://www.w3.org/1999/xhtml);
@-moz-document domain("mail.google.com") {

/* --------------- base --------------- */
*{
color : #4D4D4D !important;
font-family : KaratMedium, arial, san-serif !important;}

.e7Tcgd, #loading {background-color : #FFFFFF !important;}

/********************************************************************/

/* --------------- header --------------- */
.UiIfsf{background-color : #333333 !important;
border-color : #000 !important;}

#gbar{padding-left : 5px !important;}
.gb1{margin-right : .3em !important;
color : #f2f1df !important;}

#gbar a, #gbar a:active, #gbar a:visited, .VUNkxf u, .VUNkxf small,
.l73JSe, .nQ6QTe nobr, .nQ6QTe nobr b{
color : #f2f1df !important;
text-decoration : none !important;}

/* more menu */
#gbi {border : 1px solid #673c56 !important;}
#gbar a.gb2.VUNkxf {color : #46494D !important;}
#gbar a.gb2.VUNkxf:hover {background: #F8F8F8 !important;}

/* --------------- input textarea select --------------- */
input, textarea, select,
.OYmQme, .Y1jEjc .JRJslf,
.manager-page .toolbar .search-box,
.manager-page .add-to-group-box,
.manager-page .goog-flat-button{
border: 1px solid #673c56 !important;
background-color: #f2efef !important;
-moz-appearance: none !important;}

input[type=checkbox], input[type=radio] {
-moz-appearance: checkbox !important;}

.iE5Yyc, .manager-page input{
font-size : 15px !important;
border : none !important;
background-color : #f2efef !important;}

#contact-pane input{
border: 1px solid #673c56 !important;}

.Gjckbb {font-size : 14px !important;}

/********************************************************************/

/* --------------- frame color --------------- */
/* main */
.oi23Hf .R7iiN, .lLzmXd .R7iiN,
/* Editer main*/
.Gdbtkf .c1I77d, .Y1jEjc .c1I77d,
.Y1jEjc .c1norb, .Y1jEjc .kwmAmd, .Y1jEjc .m8lwn, .Y1jEjc .vHYYR,
.Y1jEjc .P0tbHb, .uQLZXb form, .VByZEe, .BldZyd,
.Gdbtkf .c1I77d, .uQLZXb,
/* selected menu */
.cOSVMd .c1norb, .cOSVMd .kwmAmd, .cOSVMd .m8lwn,
.cOSVMd .vHYYR, .cOSVMd .wRoeNc, .cOSVMd .Hemrjb,
.ybaOyc .c1norb, .ybaOyc .kwmAmd, .ybaOyc .m8lwn, 
.ybaOyc .vHYYR, .ybaOyc .wRoeNc, .ybaOyc .Hemrjb,
.cBhtOe .NIPhib .zD5BAe,
/* Contacts */
.manager-page .toolbar
{background-color : #1793D1 !important;}

/* main corner */
.oi23Hf .P0tbHb, .lLzmXd .P0tbHb, .oi23Hf .wRoeNc, .lLzmXd .wRoeNc,
.oi23Hf .F2yfRe, .lLzmXd .F2yfRe, .oi23Hf .Hemrjb, .lLzmXd .Hemrjb,
/* Editer main coner */
.Y1jEjc .wRoeNc, .Y1jEjc .P0tbHb, .Y1jEjc .Hemrjb, .Y1jEjc .F2yfRe,
/* selected menu corner */
.ybaOyc .P0tbHb, .ybaOyc .F2yfRe, .cOSVMd .P0tbHb, .cOSVMd .F2yfRe
{background-image : url(https://mail.google.com/mail/rc?a=af&c=b593891793D1&w=4&h=4) !important;}

/* Spam Trash main */
.xNSvsd .R7iiN,
/* selected Spam Trash */
.cBhtOe .NIPhib,
.IyrUZb .c1norb, .IyrUZb .kwmAmd, .IyrUZb .vHYYR, .IyrUZb .m8lwn,
.IyrUZb .wRoeNc, .IyrUZb .Hemrjb
{background-color : #1793D1 !important;}

/* Spam Trash main corner */
.xNSvsd .P0tbHb, .xNSvsd .wRoeNc, .xNSvsd .F2yfRe, .xNSvsd .Hemrjb,
/* selected Spam Trash menu corner */
.IyrUZb .P0tbHb, .IyrUZb .F2yfRe
{background-image : url(https://mail.google.com/mail/rc?a=af&c=a0a58e1793D1&w=4&h=4) !important;}

/* Labels Item main */
.ar6Hkf .R7iiN,
/* Search Options main */
.BBrt4c .kwmAmd, .BBrt4c .wWwc8d, .BBrt4c .c1norb, .ny3hZb .c1norb,
.ny3hZb .kwmAmd, .ny3hZb .vHYYR, .ny3hZb .m8lwn, .ny3hZb .wRoeNc
{background-color : #92b5b0 !important;}

/* Labels Item main corner*/
.ar6Hkf .P0tbHb, .ar6Hkf .wRoeNc, .ar6Hkf .F2yfRe, .ar6Hkf .Hemrjb,
/* Search Options corner */
.BBrt4c .P0tbHb, .BBrt4c .wRoeNc, .ny3hZb .P0tbHb,
.ny3hZb .F2yfRe, .ny3hZb .Hemrjb
{background-image : url(https://mail.google.com/mail/rc?a=af&c=92b5b0&w=4&h=4) !important;}

/* Settings main */
.TPdeOc .R7iiN, .lowmzb, .tAYBjb .GVhBfc, .tAYBjb .AiCerc,
/* Create a filter main */
.YKsXMe .kwmAmd, .YKsXMe .wWwc8d, .YKsXMe .c1norb, .Z1uQkf .c1norb,
.Z1uQkf .kwmAmd, .Z1uQkf .vHYYR, .Z1uQkf .m8lwn, .Z1uQkf .wRoeNc{
background-color : #bca37c !important;}

/* Settings corner */
.TPdeOc .P0tbHb, .TPdeOc .wRoeNc, .TPdeOc .F2yfRe, .TPdeOc .Hemrjb,
/* Create a filter corner */
.YKsXMe .P0tbHb, .YKsXMe .wRoeNc, .Z1uQkf .P0tbHb,
.Z1uQkf .F2yfRe, .Z1uQkf .Hemrjb{
background-image : url(https://mail.google.com/mail/rc?a=af&c=bca37c&w=4&h=4) !important;}

/* Chat Window main*/
.AWqJIf .kwmAmd ,.AWqJIf .c1norb, .AWqJIf .vHYYR, .AWqJIf .wWwc8d
{background-color : #966b6b !important;}

/* Chat Window corner */
.AWqJIf .P0tbHb , .AWqJIf .wRoeNc{
background-image : url(https://mail.google.com/mail/rc?a=af&c=966b6b&w=3&h=3) !important;}


/* message */
.n38jzf .Ptde9b, .n38jzf .m14Grb{
background: #f2e8c9 !important;}

.n38jzf .zIVQRb, .n38jzf .Qrjz3e, .n38jzf .Gbtri, .n38jzf .gmNpMd{
background-image : url(https://mail.google.com/mail/rc?a=af&c=f2e8c9&w=4&h=4) !important;}

/********************************************************************/

/* --------------- main menu --------------- */
/* select, refresh, counter */
.bKmyId, .bsABdf, .DiWSpb,.vZFPPc, .z8N7nd, .vwcZUe,
.xNSvsd .bSwwie .l73JSe{
font-size : 14px !important;}

span[selector^="all"],span[selector^="none"],
span[selector^="read"],span[selector^="unread"],
span[selector^="starred"]{
padding-right : 5px !important;}

/* info space */
.Ch5Hj, .YdYocf {background : #F6EFE1 !important;}

/* more action hover */
.QOD9Ec {border : 1px solid #673c56 !important;}
.P0GJpc{background-color : #F8F8F8 !important;}

/* read mail */
.AnqB9d {background : #F6EFE0 !important;}

/* unread mail */
.QhHSYc {background-color : #f4eff4 !important;}

/* selected mail */
.rfza3e {background-color : #EEEEEE !important;}

/* hover item */
tr[class^="xweT7d AnqB9d"]:hover,
tr[class^="xweT7d QhHSYc"]:hover {
background-color : #fff9ff !important;}

.Cipym{
background-color : #F0F0F0 !important;
border : none !important;}

/* --------------- left menu --------------- */
/* hide ion */
.gUlKtd, .aBJ8he {display : none !important;}

/* menu */
.XoqCub .NIPhib{
margin-left : -2px !important;
border-bottom : 1px dashed #000 !important;}

.NIPhib .zD5BAe, .NIPhib .Tm9rOd{
padding : 2px 0 2px 3px !important;
text-decoration : none !important;
background-color : transparent !important;
font-size : 15px !important;
color : #333333 !important;
display: block !important;}

.XoqCub .NIPhib:hover{
color : #333333 !important;
border-bottom : 1px dashed #1793D1 !important;}

.NIPhib .zD5BAe:hover, .NIPhib .Tm9rOd:hover{
color : #000000 !important;}

.ACpQre .R7iiN, .ACpQre .wWwc8d{
background-color : transparent !important;}

/* chat & labels */
.Tzvkxd .XoqCub .Pj5gjf, .XoqCub .Hc3Vg .XoqCub .Pj5gjf
{display : none !important;}

.a3hTGd .R7iiN, .XPj4ef .R7iiN{
width : 145px !important;
background-color : transparent !important;}

.qHJVCb{
background-color : #F8F8F8 !important;
border-bottom : 1px solid #c6c5b1 !important;}

.M3aZbb td{border-top : 1px solid #c6c5b1 !important;}

.WDwv9d, .dH86Yd, .GTx9Hd {background : #F6EFE1 !important;}

.nM7i0, .WDwv9d{
font-family : arial, san-serif !important;}

.HQ6yBd {background-color : #e2eff4 !important;}

/* Popup menu*/
.FVNmUc .Pbwkb, .FVNmUc .Pbwkb, .FVNmUc .exMFFe, .FVNmUc .exMFFe{
background-color : #c6aaa3 !important;}

.V3nuZd .goog-menuitem
{background-image : none !important;
background-color : #F8F8F8 !important;
border-bottom : 1px solid #c6c5b1 !important;}

.V3nuZd .goog-menuseparator{
background-color : #F8F8F8 !important;
border-right : 1px solid #c6c5b1 !important;}

.wcU0wf, .VwVWqc, .GCQ5W, .pBgL5e, .zoHs5e, .AWvUZb, .qlMg0e{
background-image : none !important;}


/* Status Options, Chat Options */
.I24Uab {border : none !important;}

.O7GAEf, .DYHi6d, .a3hTGd .DYHi6d{
background-color : #fff !important;
border : 1px solid #673c56 !important;}

.O7GAEf hr {background-color : #F6EFE1 !important;}
.j665Sd, .a3hTGd .McPZQe{background-color : #F8F8F8 !important;}

.E4KNxe {border-top : 1px solid #F8F8F8 !important;}

.a3hTGd .Tzvkxd .P0tbHb, .a3hTGd .Tzvkxd .wRoeNc,
.a3hTGd .F2yfRe, .a3hTGd .Hemrjb,
.XPj4ef .Tzvkxd .P0tbHb, .XPj4ef .Tzvkxd .wRoeNc,
.XPj4ef .F2yfRe, .XPj4ef .Hemrjb{
background-image : none !important;}

.HSZged{font-size : 15px !important;}

.oggeve, .uAn3he, .XPj4ef .Qj7Rff{
border-bottom : 1px dashed #000 !important;}

.WnHkDd:hover, .HSZged:hover {color : #333333 !important;}
.oggeve:hover {border-bottom : 1px dashed #333334 !important;}

td.o186ac, td.G6Lv5d, td.FKRsx, td.UXL9pb, td.hdc97, td.EcrCQe{
border : none !important;}

.a3hTGd .dH86Yd, .a3hTGd .GTx9Hd{
border-color : transparent !important;}

/* Labels background */
.pvSW6e, .Qj7Rff{background-color: #F8F8F8 !important;}

.pvSW6e .zD5BAe{
text-decoration : none !important;
display: block;}

.pvSW6e .zD5BAe:hover{text-decoration : underline !important;}

/* chat search & invite a friend */
.aBJ8he, .gUlKtd, .I94Sdc .R7iiN,.p9ILHf,
.I94Sdc .Tzvkxd .P0tbHb, .I94Sdc .F2yfRe,
.I94Sdc .Tzvkxd .wRoeNc, .I94Sdc .Hemrjb{
display:none !important;}

/********************************************************************/
/* --------------- mail view --------------- */

/* Hide Ads */
.yxEQwb, .iFOJMb{display : none !important;}

table[class*="PwUwPb XoqCub MMcQxe"], td.eWTfhb > div.ice3Ad{
width : 99% !important;}

.f3hr3b > table.PwUwPb > tr > td.eWTfhb > .XoqCub{
width : 100% !important;}

.yMuNaf{
position : absolute !important;
left : 0 !important;
top : 20px !important;}

.jsbnre{padding-bottom : 20px !important;}

.OZly4d, .m2U49e{
float : left !important;
margin-right : 10px !important;}

td.eWTfhb > .XoqCub{
width : 0px !important;
overflow : visible !important;}

.aWL81 .z1IiMc{display : none !important;}

/* background(outer) */
.MMcQxe{
top : 2px !important;
background-color : #F6EFE1 !important;
-moz-border-radius: 3px ! important;}

.R7iiN .m8lwn {display : none !important;}

/* background(inner) */
.YrSjGe{
background-color : #F8F8F8 !important;
-moz-border-radius: 3px ! important;}

/* Subject */
.VrHWId {font-size : 15px !important;}

/* details */
.InqsWb .ObUWHc, .qNeRme, .un3FG{
border-bottom : 1px dashed #000 !important;
margin : 0 10px 20px 10px !important;}

/* display message */
.XwckWe {background-color: #d8ddd3 !important;}

/* text */
.ArwC7c {font-size : 15px !important;}

/* text link */
.YrSjGe a:hover, .YrSjGe a:visited{
color : #904060 !important;}
.YrSjGe a{color : #5b6d82 !important;}

.rGOYzc .P0tbHb, .rGOYzc .c1norb,
.rGOYzc .vHYYR, .rGOYzc .F2yfRe,
.rGOYzc .Hemrjb, .rGOYzc .m8lwn, .rGOYzc .kwmAmd {
background-image : none !important;
background-color: #F8F8F8 !important;}

.LYI6Sd, .eNXyxd{
background-color : #F6EFE1 !important;
background-image : none !important;}

/********************************************************************/
/* --------------- Contacts --------------- */
.manager-page body, .manager-page td, .manager-page div{
font-family : arial, san-serif !important;}

.scrollable > .scroll-content{
background-color : #f7f6f2 !important;}

.manager-page .rightsep{
border-right : 2px solid #c1ada8 !important;}

.manager-page .menu{
border : 1px solid #673c56 !important;}

.contacts-list-actions,
.manager-page .editbar{
background-color : #F8F8F8 !important;
border-top : 1px solid #F6EFE1 !important;
border-bottom : 1px solid #F6EFE1 !important;}

.group-list hr.header,
.group-list-secondary .selected,
.group-list .selected, .checkable-list .selected{
background-color : #F6EFE1 !important;}

.manager-page .menu .menu-item-selected,
.group-list .active, .checkable-list .active{
background-color : #F8F8F8 !important;}

.contact-pane .contact-banner{
border-top : 1px solid #F6EFE1 !important;
border-bottom : 1px solid #F6EFE1 !important;}

/* --------------- editer --------------- */
.Gdbtkf .R7iiN, .Gdbtkf .z1IiMc{
background-color : #d6baaf !important;}

/* Rich Text icon */
.rwfzSd {border : none !important;}

/* Check Spelling */
.NQ52{
background : #fff !important;
border : 1px solid #673c56 !important;}
.NQ52 .goog-menuitem-highlight{
background : #F8F8F8 !important;}

.l4dHEb .wRoeNc{background : #F8F8F8 !important;}

/* Drafts */
.opUkHb .yaEVMb {border : 1px solid #673c56 !important;}

/* --------------- Chat Window --------------- */
.gMivnd, .v0fLnc{background : #f9f9f9 !important;}

.w85PXe, .AhBfRd{
background : #F8F8F8 !important;
border : 1px solid #673c56 !important;}

.HFJj2b:hover {background : #F6EFE1 !important;}

/* --------------- Settings --------------- */
.tAYBjb .ZOB6Zc, .eGbrz{
background :  #f2e8c9 !important;}
.GorKne td.Wnp2lb, .GorKne td.WwReqb,
.IoBQdd, .DwFWUd, .A5gIhd, .NuOXpe, .FceqAb{
background :  #f2e8c9 !important;
border-bottom : 2px solid #ebe1a9 !important;}

.GorKne td.TtHZK {border-top : 2px solid #ebe1a9 !important;}
.YVweLb .ZOB6Zc, .yolZre {border :none !important;}
.lwwhL {background :  #ebe1a9 !important;}

.GorKne .l73JSe {color : #46494D !important;}

/* --------------- Search Options --------------- */
.ny3hZb .wWwc8d{background :  #c9d6d8 !important;}

/* --------------- Create a filter --------------- */
.Z1uQkf .wWwc8d{background :  #f2e8c9 !important;}
.Z1uQkf .l73JSe {color : #46494D !important;}

/* --------------- footer --------------- */
.s7hnoe, .VfONdd, .IUntof {display : none !important;}

}

```


Here is the base64 default Arch logo:

```

/*Coded by gnf 12/27/07 Ver 1.0*/
@namespace url(http://www.w3.org/1999/xhtml);
@-moz-document domain(mail.google.com) {

/*logo [for using an own logo: change data-url to a png-image you like (143px x 59px)]*/
.zYsCRb 
{ background: url("data:image/png;base64,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
")  !important; }

}

```

---

