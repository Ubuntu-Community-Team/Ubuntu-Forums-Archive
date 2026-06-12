---
title: "Accidentally reset panel length"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by Eric Weir on 2007-10-29
I've posted this on the Kubuntu forums, but haven't gotten any help there yet, and thought I'd try here, since there seem to be a lot more people here, perhaps many with Kubuntu experience.

Somehow over the weekend I accidently reset the length of the panel at the bottom of the page. It now extends a little past the middle of the screen. At the time this happened I had been customizing size and position of the various windows used by various applications. Somewhere in this process I noticed that the panel was no longer extending all the way across the screen. 

This made me think Kubuntu considered the panel a window, but that doesn't seem to be the case, and there doesn't seem to be any way of resetting panel length in the "configure panel" window -- unless it's not set at 100%, but it is.

Anybody got any suggestions?

Thanks in advance,

---

### Post by skyjacker on 2007-10-29
right click on an empty space on the panel and choose "configure panel". If the panel length is set at 100%, take a look at the "position of the panel. To take the whole width of the screen at 100%, the panel should be in the "center" position. To get it there click on the middle of the three buttons in the bottom row of the square. Finally, look at the screen to the right. Does it cover the entire width of the screen now? If it does click on apply and then ok. Close the configure panel and you are done. let me know if this works.:)  Good Luck

---

### Post by Eric Weir on 2007-10-30
> **skyjacker said:**
> right click on an empty space on the panel and choose "configure panel". If the panel length is set at 100%, take a look at the "position of the panel. To take the whole width of the screen at 100%, the panel should be in the "center" position. To get it there click on the middle of the three buttons in the bottom row of the square. Finally, look at the screen to the right. Does it cover the entire width of the screen now? If it does click on apply and then ok. Close the configure panel and you are done. let me know if this works.:)  Good Luck

Hey, Decatur, Illinois, Decatur, Georgia! To top it off, I'm originally from Champaign! I've come to love the South, but I do miss the prairie.

I was hopeful when I read your post. Alas, it didn't work. While I was at it, I tried adding the other panels that are available as options when you right-click on the panel, thinking I could create a new version of the old one and then get rid of the old one. 

Well, that was going to work, but interestingly all of the panels I added [and then removed] also covered only a little over half of the bottom [or side] of the screen.

Any more thoughts? Anybody else got a thought?

Thanks,

---

### Post by skyjacker on 2007-10-30
Did you accidentaly change the position of your screen in the horizontal mode? The newer monitors have an "automatic " adjustment on them which sets the size of the picture based on the settings of your resolution. Worth a try. Don't know what else it could be. :confused:

---

### Post by Eric Weir on 2007-10-31
> **skyjacker said:**
> Finally, look at the screen to the right. Does it cover the entire width of the screen now? If it does click on apply and then ok.

I'm responding to your previous post again, because I just retried your suggestion and got the same result, but noticed something related to what I've quoted above. On the screen to the right, the panel appears as extending the full width of the screen. Also, if I make other changes and "apply" them, those changes or reflected in what's displayed in the screen on the panel configuration window. 

It appears that as far as the configuration window is concerned, the panel is the full width of the screen. 

I wish I knew how I did this. I hope I don't have to live with it forever. I don't know if it'll cause me to abandon Ubuntu, but it sure is irritating, as well as puzzling.

---

### Post by Eric Weir on 2007-10-31
> **skyjacker said:**
> Did you accidentaly change the position of your screen in the horizontal mode? The newer monitors have an "automatic " adjustment on them which sets the size of the picture based on the settings of your resolution. 

Nope. Haven't touched the monitor controls. Also have an older monitor.

Thanks for the suggestion.

---

### Post by skyjacker on 2007-10-31
Eric, you could try making a new panel to see if it does the same thing.  Right click on panel, pick "add new panel. If it isn't the full width of the screen go to the previous suggestion and see what the right side window shows. I've played around with my desktop and can't find a way around your problem. One last thought --- you might try re-installing your kdesktop and see if that fixes things. Do a back-up of you /home file first. Go to the synaptic package manager and search for kdesktop. choose it, right click, and choose "mark for re-installation". Drastic, but it will probably cure your problem. Good Luck!!

---

### Post by Eric Weir on 2007-11-01
> **skyjacker said:**
> Eric, you could try making a new panel to see if it does the same thing.  Right click on panel, pick "add new panel. If it isn't the full width of the screen go to the previous suggestion and see what the right side window shows. 

I've tried that. All the panel options show up on the actual screen as shortened. They all show up on the screen on the configuration window, however, as covering the full width, or height, of the screen.

> One last thought --- you might try re-installing your kdesktop and see if that fixes things. Do a back-up of you /home file first. Go to the synaptic package manager and search for kdesktop. choose it, right click, and choose "mark for re-installation". Drastic, but it will probably cure your problem.I think that's what I'm gonna have to do.  Not right away, though. I've been neglecting work, work that I love, for this stuff. I need to concentrate for a while on the work. Maybe sometime this weekend. 

There are so many things I want to try -- e.g., seeing if I can run an old DOS program that I use a lot under DOSbox -- that I could do nothing else.

Thanks for the suggestions. I'll keep you up to date.

Regards,

---

### Post by Eric Weir on 2007-11-04
> **skyjacker said:**
> One last thought --- you might try re-installing your kdesktop and see if that fixes things. Do a back-up of you /home file first. Go to the synaptic package manager and search for kdesktop. choose it, right click, and choose "mark for re-installation". Drastic, but it will probably cure your problem. Good Luck!!

Well, I tried what you suggested without any noticeable effect. Then I uninstalled the destop altogether and reinstalled it. Again, it came back the same way -- with the panel extending just barely over half the screen width. 

Apparently when the desktop was uninstalled my configurations were not deleted, since the panel not only came back the same length, but with the same launchers installed, etc. 

Is there a way I could really, completely uninstall, i.e., get ride of all my configurations, etc.? If so, then perhaps on reinstallatioon the panel commme back the full width of the screen.

---

### Post by skyjacker on 2007-11-04
> **Eric Weir said:**
> Well, I tried what you suggested without any noticeable effect. Then I uninstalled the destop altogether and reinstalled it. Again, it came back the same way -- with the panel extending just barely over half the screen width. 

Apparently when the desktop was uninstalled my configurations were not deleted, since the panel not only came back the same length, but with the same launchers installed, etc. 

Is there a way I could really, completely uninstall, i.e., get ride of all my configurations, etc.? If so, then perhaps on reinstallatioon the panel commme back the full width of the screen.In Synaptic choose "Mark for Complete Removal" instead of "Mark for Removal". ...or type  "sudo apt-get remove --purge application" using terminal ...  Good luck!

---

### Post by Eric Weir on 2007-11-04
> **skyjacker said:**
> In Synaptic choose "Mark for Complete Removal" instead of "Mark for Removal". ...or type  "sudo apt-get remove --purge application" using terminal ...  Good luck!

Thanks.

One other thing I forgot to mention, though I made note of it for myself. The first time the desktop installed, i.e., at the very end of the boot process, an error message displayed. It said, "Error KDE Panel. Malformed URL "system:/" The first time I clicked on the Kmenu another error message displayed: "Error KDE Panel. Malformed URL "trash:/"

Perhaps not significant, but I wouldn't know.

Thanks again,

---

### Post by skyjacker on 2007-11-04
> **Eric Weir said:**
> Thanks.

One other thing I forgot to mention, though I made note of it for myself. The first time the desktop installed, i.e., at the very end of the boot process, an error message displayed. It said, "Error KDE Panel. Malformed URL "system:/" The first time I clicked on the Kmenu another error message displayed: "Error KDE Panel. Malformed URL "trash:/"

Perhaps not significant, but I wouldn't know.

Thanks again,
Don't have a clue about that message, but it sounds like you have a bad install. try the complete removal, and re-install typing the following in  the terminal  "sudo apttitude update && sudo aptitude install kubuntu-desktop"

---

### Post by Eric Weir on 2007-11-04
> **skyjacker said:**
> Don't have a clue about that message, but it sounds like you have a bad install. try the complete removal, and re-install typing the following in  the terminal  "sudo apttitude update && sudo aptitude install kubuntu-desktop"

I did the complete removal once, using Synaptic -- interestingly, Adept could not find kdesktop in the repositories! -- and in the reinstall afterward I got the same result. That panel doesn't want to be normal.

As I write kdesktop is not installed. I tried another complete removal. I'll do the reinstall tomorrow using the terminal per above.

I'm beginning to wonder if I'm going to have to did a completely new installation of K/Ubuntu.

---

### Post by skyjacker on 2007-11-04
Before you do another install, type "whereis kdestop" in terminal, and see if it is in your system. then try the "purge"  command followed by another whereis kdestop. If the second whereis comes up blank, you have probably gotten rid of it completly. Sorry, I'm out of ideas. Good Luck1

---

### Post by Eric Weir on 2007-11-05
> **skyjacker said:**
> Before you do another install, type "whereis kdestop" in terminal, and see if it is in your system. then try the "purge"  command followed by another whereis kdestop. If the second whereis comes up blank, you have probably gotten rid of it completly. 

I've followed your directions using the terminal: Uninstall with purge. Whereis, which returned a result I didn't understand, followed by another uninstall with purge which informed me that there was nothing to uninstall, then install with update.

At the end of in reinstall the terminal displayed this message:

> 
    Postfix Configuration    
  &#9474; You have several choices for general configuration at this point.  If     
  &#9474; you have your debconf priority set to 'low' or 'medium', you will be    
  &#9474; asked more questions later.  You can always run "dpkg-reconfigure    
  &#9474; --priority=low postfix" at a later point if you want to see these    
  &#9474; questions again.    
  &#9474;    
   &#9474; No configuration - IF YOU WANT THE INSTALL TO LEAVE YOUR CONFIG ALONE, 

&#9474; CHOOSE THIS OPTION.  No configuration changes will be done now:  If you    
  &#9474; have not already configured Postfix, your mail system will be broken and    
  &#9474; should not be used. You must then do the configuration yourself by    
  &#9474; editing /usr/share/postfix/main.cf.dist and saving your changes as    
  &#9474; /etc/postfix/main.cf, or by running dpkg-reconfigure Postfix.  main.cf   
  &#9474; will not be modified by the Postfix install process. I'm operating under GNOME at the moment. I haven't booted Kubuntu. What do I do?

---

### Post by skyjacker on 2007-11-05
I have no idea, as I have re-insalled kdesktop twice because of broken things and have never had this message. maybe someone else will be able to help you with this. Sorry:confused:

---

### Post by Eric Weir on 2007-11-05
> **skyjacker said:**
> I have no idea, as I have re-insalled kdesktop twice because of broken things and have never had this message. maybe someone else will be able to help you with this.

I went ahead and rebooted as a Kubuntu session. Can't believe it. [1] The panel is unchanged. [2] The wallpaper looks like what I created for Ubtuntu to get away from its orange and tan theme before I tried Kubuntu. I don't know if I'm running Kubuntu or not. I guess I am, since that's what I selected on log-in. 

Is there a way of resinstalling Kubuntu that would completely replace everything Kubuntu-related but leave my data files untouched? 

I've backed up my home folder to another folder on my single hard disk.

---

### Post by Eric Weir on 2007-11-05
>     &#9474; No configuration - IF YOU WANT THE INSTALL TO LEAVE YOUR CONFIG ALONE, 
&#9474; CHOOSE THIS OPTION.  No configuration changes will be done now:  If you    
  &#9474; have not already configured Postfix, your mail system will be broken and    
  &#9474; should not be used. You must then do the configuration yourself by    
  &#9474; editing /usr/share/postfix/main.cf.dist and saving your changes as    
  &#9474; /etc/postfix/main.cf, or by running dpkg-reconfigure Postfix.  main.cf   
  &#9474; will not be modified by the Postfix install process.I guess this is the option I took. My "mail system" seems to be fine. Thunderbird runs. It downloads my mail. 

I'm curious what's in /usr/share/postfix/main.cf.dist, but I have no idea how to open a file in terminal. Or do I simply use an editor?

---

### Post by califman831 on 2007-11-05
different panel problem but this might work for you
[http://ubuntuforums.org/showthread.php?t=407218](http://ubuntuforums.org/showthread.php?t=407218)

---

### Post by Eric Weir on 2007-11-05
I checked /usr/share.There's no postfix folder there.

I'm calling it a day. I've done some of my paying work. I'm headed to the Y for a workout, probably a run outdoors on a beautiful, warm, sunny day in Atlanta.

I'd really like to just start over with Ubuntu/Kubuntu. Maybe just as a pure Kubuntu system. I still have my Windows system with the same data files, so there wouldn't be any risk, except maybe ending up without a workable K/Ubuntu system.

Is there a way?

---

### Post by Eric Weir on 2007-11-05
> **califman831 said:**
> different panel problem but this might work for you
[http://ubuntuforums.org/showthread.php?t=407218](http://ubuntuforums.org/showthread.php?t=407218)

Thanks, it sounds like it might.

From the thread it was unclear whether renaming the file caused KDE to restore the panel defaults. It seems to have worked for you, but another poster ended up without a new file. 

I checked the contents of kickerrc. I'm gonna past em below. Maybe you or someone else can tell me which value needs to be changed. 
> [$Version]
update_info=kickerrc.upd:kde_3_1_sizeChanges,kickerrc.upd:kde_3_4_reverseLayout,kickerrc.upd:kde_3_5_kconfigXTize

[Applet_1]
FreeSpace2=0
WidthForHeightHint=48

[Applet_2]
ConfigFile=taskbar_panelapplet_tjag9q8ovb8hdfcmfqbe_rc
WidthForHeightHint=210

[Applet_3]
FreeSpace2=0
WidthForHeightHint=60

[Applet_4]
FreeSpace2=0
WidthForHeightHint=88

[Applet_5]
WidthForHeightHint=68

[Applet_6]
ConfigFile=trash_panelapplet_zddtxaz5inkcutqejyqe_rc
FreeSpace2=0
WidthForHeightHint=68

[Extension_1]
ConfigFile=childpanel_panelextension_pf9ofshg1qrmxys1gyzo_rc
DesktopFile=childpanelextension.desktop
UserHidden=0

[General]
Alignment=1
AutoHideDelay=3
AutoHidePanel=false
AutoHideSwitch=false
BackgroundHide=false
CustomSize=40
ExpandSize=false
Extensions2=
HideAnimation=true
HideAnimationSpeed=40
IExist=true
Position=3
Size=3
SizePercentage=100
UnhideLocation=0
UntrustedApplets=
UntrustedExtensions=
XineramaScreen=0

[button_tiles]
EnableBrowserTiles=false
EnableDesktopButtonTiles=false
EnableKMenuTiles=false
EnableURLTiles=false
EnableWindowListTiles=false

[buttons]
EnableTileBackground=false

[menus]
MenuEntryFormat=NameOnly
RecentAppsStat=29 1194204402 /usr/share/applications/kde/systemsettings.desktop,8 1193255608 /usr/share/applications/evolution.desktop,8 1194212020 /usr/share/applications/synaptic-kde.desktop,8 1194211844 /usr/share/applications/gnome-terminal.desktop,6 1194225971 /usr/share/applications/kde/adept_installer.desktop,5 1194054857 /usr/share/applications/evolution-mail.desktop,4 1194287340 /home/eric/.local/share/applications/kde-konqbrowser.desktop,4 1193336686 /usr/share/applications/kde/Kontact.desktop,4 1193601573 /usr/share/applications/shares.desktop,3 1193096919 /usr/share/applications/services.desktop,2 1192650061 /usr/share/applications/gnome-cups-manager.desktop,2 1192547901 /usr/share/applications/firefox.desktop,2 1192655077 /usr/share/applications/network.desktop,2 1192548942 /usr/share/applications/ooo-writer.desktop,2 1192655172 /usr/share/applications/kde/knetworkmanager.desktop,2 1193444704 /usr/share/applications/kde/groupwarewizard.desktop,2 1194289353 /usr/share/applications/gedit.desktop,2 1194225954 /usr/share/applications/kde/Kfind.desktop,2 1193684720 /usr/share/applications/update-manager.desktop,2 1192548288 /usr/share/applications/mozilla-thunderbird.desktop,1 1193505372 /usr/share/applications/kde/Help.desktop,1 1193444777 /usr/share/applications/hal-device-manager.desktop,1 1192567138 /usr/share/applications/kde/karm.desktop,1 1193428933 /usr/share/applications/gnome-app-install-xfce.desktop,1 1193097188 /usr/share/applications/kde/kate.desktop,1 1192645317 /usr/share/applications/kde/konqbrowser.desktop,1 1193429552 /usr/share/applications/thunderbird.desktop,1 1193428554 /usr/share/applications/kde/adept_manager.desktop,1 1193944422 /home/eric/.local/share/applications/alacarte-made-1.desktop,1 1192655381 /usr/share/applications/baobab.desktop,1 1193097109 /usr/share/applications/gnome-screenshot.desktop,1 1194286134 /usr/share/applications/kde/konsole.desktopMy guess is it's 
>  CustomSize=40in the General section.

Maybe 
>  ExpandSize=falseShould be changed, too?

Thanks again,

---

### Post by califman831 on 2007-11-05
from what i could tell it recreates a fresh copy of the file, renaming just allows u to keep a backup.  I'm a newb on linux, hopefully some one better qualified will chime in.

---

### Post by Eric Weir on 2007-11-06
> **califman831 said:**
> from what i could tell it recreates a fresh copy of the file, renaming just allows u to keep a backup.  I'm a newb on linux, hopefully some one better qualified will chime in.

Well, I tried it and got the same &*@#$* result. 

The Georgia Ubuntu LoCo is having an "installfest" at Emory University this Saturday, which is about a mile from my home. I think I'm gonna backup my data, my emails, my bookmarks, and anything else I wouldn't want be overwritten, and have them walk me through a new install, possibly just of Kubuntu, if they can do that. 

I haven't done that much configuring, either of Ubuntu, Kubuntu, or applications, and I have my Windows system with everything I need on it, including all the same data, etc., so starting over shouldn't be that big a deal.

I wonder, though, if there isn't just a line in the kickerrc file that could make this unnecessary. 

Regards,

---

