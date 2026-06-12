---
title: "How Do I Install KDE Styles"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-07-26
Hi I'm trying to install a kde theme on my laptop but Im kind of stuck! Im following this readme file that came with the theme I downloaded: Im stuck where it says that I should install the [COLOR="Red"]Domino style[/COLOR] the style is in the folder I downloaded in the folder style/domino where three files resides, i guess three styles: domino_bluerc, domino_brushedrc and domino_orangerc. How do I install them so that I can select them in the dropdown menu as suggested underneath?
> Please read carefully.This theme is little more compicated than just importing colorscheme.
First,unpack the tarball.
 
Step 1
Configure Colors
  Go to KDE Control Center>Colors
   Click on Import Scheme button
   Import the colorscheme Dark Plastic.kcsrc from the Color-Scheme folder extracted from this tarball.
 
Step 2
Configure Kicker
Go to KDE Control Center>Desktop>Panels
Go to 4th tab Appearance
Click Enable background image checkbox
Browse and set the kicker background Background.png from the kicker folder extracted from this tarball.
 
Step 3
[COLOR="Red"]Configure Style[/COLOR]
 Domino (THIS THEME DEPENDS ON DOMINO.YOU HAVE TO INSTALL IT FIRST)
    
 Go to KDE Control Center>Style
 
Choose Domino style from the drop down combobox then click Configure next to it to bring up the Domino configurator
Go to the last tab Load/Save
Press Import Config
Browse and apply Domino_versionrc located in the Style/Domino folder that you extracted from the tarball
(You should be able to see three entries)   
Choose any one of the schemes then press Load Config
 
Step 4  
Configure Windeco
This theme uses CRYSTAL windeco.Install it first then choose it from your Kcontrol Window Decoration module.Underneath it you will see a list of tabs.Configure one by one.
 
1.General
  Choose Title alignment,Round corners,Border width,Titlebar Height according to your liking.
 
2.Buttons
 Choose any button you like.I am using Crystal Knifty.
 
3.Backgorund
 DISABLE TRANSPARENCY
 you will see two combo-boxes under active and inactive tabs.Choose Simple Outline and Simple Inline.Click on the colorboxes next to them and select #000000(BLACK).
 
4.Logo  
 none
 
5.Overlay
 THIS IS THE MOST IMPORTANT PART.
 
 Under the overlay for active window heading
 Select the third radiobox Userdefined
 browse through and use the Active window overlay.png from the windeco/crystal folder included in this tarball.
 
 Under the overlay for inactive window heading
 select the third radiobox Userdefined
 browse through and use the Inactive window overlay.png from the windeco/crystal folder included in this tarball.
 
 STEP 5  (OPTIONAL)
 KBFX theme 
You need kbfx=4.9.3
  Dark Plastic  Kbfx theme is in kbfx folder extracted from this tarball.Install it using kbfx configurator.Load  the menu buttons before you apply.

---

### Post by tbroderick on 2007-07-27
Go [here]("http://kde-look.org/content/show.php/Domino+Kubuntu+package?content=52864"). It's a link to kde-look.org where someone as already taken the time to package Domino for Kubuntu. Download and then open a terminal and enter;

```
sudo dpkg -i /path/to/domino.deb
```

---

### Post by kasperbs on 2007-07-27
Hi and thanks for pointing that out, it worked nicely.

Do you know where I can find an easy how to for installing KDE themes, The readme files that comes with the themes are pretty hard to understand!

I would also like to try the [lightgrey]("http://www.kde-look.org/content/show.php/LightGrey+for+Domino?content=52721") theme but the instructions are pretty bad
I understand nothing of this:
> ----------------------------------------------
DOMINOTHEME =

$HOME/.kde/share/config

kwindominorc

$HOME/.qt

domino_dominolightgreyrc

----------------------------------------------
COLORSHEME =

$HOME/.kde/share/apps/kdisplay/color-schemes

DominoLightGrey.kcsrc

----------------------------------------------
WINEtheme =

to install type

regedit DominoLightGrey.reg

----------------------------------------------
GTk2theme =

You need gtk2-engines-pixbuf

on debian

su -c 'apt-get install gtk2-engines-pixbuf'

Installation

open included /gtk-2.0/iconrc and change the pixmap_path to your KDE icon path (pixmap_path "INSERTICONPATHHERE:/usr/share/icons/default.kde/")

or

If you used GTK-QT engine you can find an iconrc for your kdeicontheme in ~/.gtk_qt_engine_rc

copy theme to your GTK2 theme directory (on debian /usr/share/themes)

open GTK-QT Config dialog and Choose 'use another theme' > LightGreyGTK

!!! if the Gtk theme looks ugly go to your colorsettings in kcontrol and disable "apply colors to non-KDE applications" !!!


----------------------------------------------


Wallpaper on the Screenshots is [http://www.deviantart.com/deviation/13478311/](http://www.deviantart.com/deviation/13478311/)
amaroK theme is [http://www.kde-look.org/content/show.php?content=38771](http://www.kde-look.org/content/show.php?content=38771)
GTK2theme is based on Vicious Lime which can be fond her > [http://www.viciouslime.co.uk/](http://www.viciouslime.co.uk/)

and sorry for my bad english

---

