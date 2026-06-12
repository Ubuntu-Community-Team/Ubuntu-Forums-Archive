---
title: "Introduction to Desktop Customization with Ubunt 7.10 (Beginner's View)"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by KOld Iron on 2007-12-23
Hi all,

I am still fairly new with Ubuntu, running 7.10 since it came out in October. Most of the initial problems have been solved by now (there were few to begin with and this forum was a big help).  And of course, once I got my system working, it was time also to get the looks of it a bit more personalized. 

Fortunately there is a wealth of modifications available and [_gnome-look.org_]("http://www.gnome-look.org") is a good place to start. But when you start looking there, you might get confused at first, at least I certainly did. I mean the wallpapers are straight-forward, but what are GTK 2.x, GDM Themes, Metacity and so on? And how do you get these installed anyways? So to save some of the troubles I went through, here is an introduction, from a beginner's point of view (I still haven't figured all the details out), which hopefully will help you a bit. Anybody who wants to add something, please do so. Also, if you find any mistakes (hope not, but wouldn't be surprised), please let me know.

**Note:** I will not cover anything on Compiz Fusion and Emerald.

**First some „definitions“:**
- Wallpapers: The image shown in the background, when all windows are minimized
- GTK 1.x/2.x: User interface elements (or widgets) like radio buttons, progress bars, drop-down lists. Window borders may be included or not.
- Metacity: Windows „dressing“ = Window borders and buttons
- Icons: All the icons used by the system for built-in (e.g. Nautilus) and additional applications (e.g. OpenOffice). Not all sets are complete, in such cases the applications not covered by the set will keep the default icons.
- X11 Mouse Themes: Just that, different mouse cursors.
- GDM Themes: Gnome Desktop Manager theme, this is essentially the logon screen. Often GDM designs are paired with wallpapers to provide a consistent look.
- Splash Screen: Okay, this is a bit confusing, because there are several types of splash screens and they are all found in this category. The different kinds are:
   * Boot splash screen: This is the picture shown during the GRUB phase (typically low resolution)
   * Usplash: This is the background shown during boot-up of the system incl. the progress bar. Since this requires a special format, there are only a few alternatives to the standard Ubuntu usplash.
   * Gnome splash: After you entered your username/password, a short progress screen can be optionally shown (if selected). It should match your GDM theme and sometimes is packaged with such a theme.
   * Application splash screens: Sometimes an application will use a splash screen (i.e. „pictures“) during starting, (e.g. GIMP, OpenOffice), which you can replace with your own. In some cases this includes the About splash as well (shown when you select in the application menu the entry „help/about“).

**Download:**
Single pictures (e.g. wallpapers) may be offered for download directly in their native format (e.g. as JPEG). In such cases it may be necessary to download by selecting the image and then do „save image as ...“ from the browser (context) menu. But often the download will be compressed and the package will be available in a *.tar.gz, sometimes in a *.bz2 format. Download them to a directory specificially made for desktop enhancements, since normally you can use them directly from that directory (and you don't want them to get messed up with your other downloads). If decompression is needed you can then also just select „Extract here ...“ and it will create the subdirectories right there.

**Installation:**
Depending which component you want to modify, there are at least four differnt places for modifying the appearance of your desktop.

*Boot (GRUB) splash and Usplash*
 1.Install Start-up Manager, if you haven't done yet so.
 2.Start „System/Administration/Start-up Manager“
 3.Select the register card „Appearance“
 4.Add new images through „manage bootloader themes ...“ or „manage usplash themes“
 5.Usplash themes require the special *.so format, the bootloader image can be the one of the usual image formats.
 6.Select the new theme in the drop-down list
 7.In the register card „Boot options“ you may have to adapt the display resolution and color depth to make the themes work correctly. Otherwise it can happen that you will have a dark display during boot-up (common problem)
 8.Close and re-boot to verify the change

*GDM theme*
1.Start „System/Administration/Login Window“
2.Select the register card „Local“
3.Add new themes using the „Add ... „ button
4.Select the new theme in the drop-down list
5.Close, log off and back on again to verify the change
Note: If you de-select the „Show Actions menu“ your Shutdown and Restart buttons will disappear!

*Gnome splash screen*
Although it would be logical to configure this together with the GDM theme, that's not possible. Instead you need to use „System/Preferences/Splash Screen“, which is a little GUI for just that configuration item (you may need to install that first). Select „Install“ to add a new splash image, then select „Activate“.

*Application splash screen*
The details depend on the application, but in general you need to replace the existing splash screen (rename it to something else) with the new splash screen (giving it the default name). That means you have to locate the necessary directory and then do the switch. Typically this will require root permission, so either you navigate there on the command line and then use „sudo“ with the necessary copy (cp) and rename (mv) commands, or run „gksudo nautilus“, which will give you a graphical file browser with root credentials (be careful, what you are doing!). Also your splash screen may be overwritten during an application update.

*Last but not least: Background, Widgets, Icons, Pointers and Windows*
 1.Start with „System/Preferences/Appearance“
 2.Background
   a) For changing the background select the register card „Background“ (surprise!)
   b) Add images from your preferred folder using „Add ...“
   c) Select by clicking the image
   d) Changes will apply immediately (therefore no apply button)
 3.Everything else
   a) Select the register card „Theme“
   b) You can change to a different existing theme just by selecting it (again, immediate apply after selection)
   c) Or you can click „Customize ...“ to create any mixture of existing theme components (icons from one theme, controls from another one, and so on). Your customized theme will automatically get the default name „Custom“, which you can change and save („Custom“ gets saved automatically)
   d) Or you can „Install ...“ new theme packages (*.tar.gz). Be aware, that not all packages have all components included (e.g. some may only have icons and nothing else, etc.). Also, the *.tar.gz (or *.bz2) file may have the actual package as another *.tar.gz inside (uncompress first in your file explorer). You can use those themes from your download directory directly, however, in that case, they will only be available to you. If you want other users to access them as well, it is necessary to move those files to the relevat shared directories. In some cases this may be required anyways (should say so in the installation information or README, e.g. for icon sets). Again, writing to shared directories will normally require root permissions.
   e) Select those components of the newly installed themes that you want to use. Sometimes it may be necessary to at least log off (e.g. for mouse cursors) for the changes to become fully effective, because the logging off and back on again will restart the graphics system.
 4.Fonts
You change your fonts in this interface as well, but I have not tried to install other fonts yet, so no details here for doing that (shouldn't be too hard, though)
**Note:** You may want to play around a little bit with this whole utility, to get a feeling for what setting affects what. Also sometimes applications are affected negatively (example: I lost my OpenOffice toolbar icons by using one particular theme and needed to change the option within OpenOffice to use the default icons again). Other applications, like Firefox or Thunderbird, have their own themes, but still will use e.g. the changed window borders.

And that's it. As I said, this is by no means a complete description on how to customize your desktop, but it should get you started and maybe it helps you to save a few clicks ;-)

Any extension / correction / feedback is welcome.
Heinrich

---

### Post by Sorivenul on 2007-12-23
Great introduction to customization for beginners.  I've got mine all set up, but I wanted to say if I had had this when I did it I would have been much happier!  Cheers!

---

### Post by foo25 on 2007-12-25
Very nice guide especially for beginners! Got all this set up myself, but as Sorivenul said, this would have made life much easier! Thanks

Just wanted to note the minor typo in the title, but I'm sure you'll notice.

---

### Post by KOld Iron on 2007-12-25
Thanks for the feedback so far (also for pointing out the typo in the title, I had not noticed it yet). I appreciate it very much.

---

### Post by powerman988 on 2008-04-21
this is realy usefull for me, thank you very much. just what i was looking for

---

### Post by boomdiddly on 2008-04-21
Thanks great overview. :) would thank you but the button to do this doesn't show against you name for some reason

---

