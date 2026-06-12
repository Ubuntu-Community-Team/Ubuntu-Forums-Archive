---
title: "Tons of Newbie Questions."
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by eric5279 on 2006-03-06
It has been a long time since I have used any LInux OS.  So long that I have pretty much forgottten how to do everything.  SO here are afew questions I hope maybe I can get some help with.

1.  I am having a probelm with adding my print software to the computer.  The mount command I am using is just not the right one.  Also I have a windows based print server.  How would I go about haiving the UNix based OS work with this server?

2.  This is a simple one, and I am almost ashamed to ask this.  How do I change the look of my desktop.  For example, the wallpaer, the color oof the task bars and so on?  As far as wallpaper goeshow do I take one from the web and save it for later?

3.  I got my video drivers to work, but I have not been able to get my sound card drivers to work.  Any tips.  Mounting issues AGAIN.

There are a few other questions Ihave, but I will just post these two for now.  Hope you call can help.  Thanks.

---

### Post by aysiu on 2006-03-06
Are you using Kubuntu or Ubuntu?

---

### Post by WelterPelter on 2006-03-06
[QUOTE=eric5279]
2.  This is a simple one, and I am almost ashamed to ask this.  How do I change the look of my desktop.  For example, the wallpaer, the color oof the task bars and so on?
[/QUOTE]

Try System -> Preferences -> Theme (in ubuntu)

---

### Post by az on 2006-03-06
1.  Samba can share and use shared windows printers.  The samba client is installed by default.  I think you can see shared windows printers out-of-the-box.  Since I don't run any windows boxes I cannot confirm this, though.

3.  What kind of sound card?  Is it an older isa card?  See [https://wiki.ubuntu.com/HowToSetupSoundCards](https://wiki.ubuntu.com/HowToSetupSoundCards)

---

### Post by eric5279 on 2006-03-06
I ma sorry.  I mean Ubuntu.

---

### Post by eric5279 on 2006-03-06
The card is a soundblaster card and I boughtitback in 2002 or so.  So it is not to old.

---

### Post by az on 2006-03-06
[QUOTE=eric5279]The card is a soundblaster card and I boughtitback in 2002 or so.  So it is not to old.[/QUOTE]
What does the device manager say, or show the output of
lspci
in a terminal.

---

### Post by armana on 2006-03-06
Hey everybody...
First of all I would like to thank all the volantairely partisipents, that make this forum !!
Iam new to ubuntu... Iam going to innstall it after XP pro and dual boot in the future...
i was wondering if its possible to innstall ubuntu or do something magical wich gives one the uppertunety to have access to some folders from both OS? For eksampal: if i can access my mp3 files wich i got in xp from ubuntu?
if this is possible...it wil make things easier.....
By the way...its -25 in oslo right now...brrrrr

---

### Post by Bartender on 2006-03-06
[QUOTE=eric5279]This is a simple one, and I am almost ashamed to ask this.  How do I change the look of my desktop.  For example, the wallpaer, the color oof the task bars and so on?  As far as wallpaper goeshow do I take one from the web and save it for later?[/QUOTE]
Well, not too simple.  If you google "gnome" you'll find a few neat websites with all kinds of themes, wallpapers, etc.  I haven't figured out how to make any of the themes install, but was able to change the desktop wallpaper!  Make sure to d/l wallpaper at the proper resolution for your settings (1024X768, etc.)
Right-click inside of either the top or bottom panel (apparently they're called 'panels' in Ubuntu, not taskbars), and left-click on "Properties".  Under the "General" tab, you'll probly just want to play with the size.  It'll expand or shrink as you click the "up" or "down" arrows so you can see what you want.
If you want to have a little fun with the colors, click on the "Background" tab, then click on "Solid Color", then click in the box next to "Color".  A neat color wheel comes up.  When you think you've got a pleasant color, click "OK".  You can slide the "Style" tab back and forth to tweak the panel's translucency.
Right-click in either panel, then click on "Add to Panel".  A new window comes up.  You might want to add a couple of the utilities, such as the "System Monitor" or "Network Monitor".  I had better success dragging & dropping the items instead of highliting them and clicking "Add".  That way you can put them where you want.  For some odd reason if I click "Add" for the Modem Monitor I get 2 of them, whereas if I drag & drop I only get one.

---

### Post by aysiu on 2006-03-06
[QUOTE=armana]
Iam new to ubuntu... Iam going to innstall it after XP pro and dual boot in the future...
i was wondering if its possible to innstall ubuntu or do something magical wich gives one the uppertunety to have access to some folders from both OS? For eksampal: if i can access my mp3 files wich i got in xp from ubuntu?
if this is possible...it wil make things easier.....[/QUOTE] The best dual-boot guide around is Herman's: [http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

And, yes, you can share files between XP and Ubuntu, but you can't store those files on the XP partition unless you want them to be read-only. If you make a separate FAT32 partition, both OSes can read from and write to it. Otherwise, you can store everything on Ubuntu--I think there's a program you can use to read/write Ext3 from XP.

[quote=eric5279]
This is a simple one, and I am almost ashamed to ask this. How do I change the look of my desktop. For example, the wallpaer, the color oof the task bars and so on? As far as wallpaper goeshow do I take one from the web and save it for later?[/quote] Go to [http://www.gnome-look.org](http://www.gnome-look.org)
You can find desktop wallpapers, themes, icons--whatever.

Wallpapers, just right-click on the desktop
Themes go to System > Preferences > Themes and drag and drop Gtk themes into the window (make sure you don't unzip them--keep them as .tar.gz files).

---

### Post by cotcot on 2006-03-07
[QUOTE=aysiu]I think there's a program you can use to read/write Ext3 from XP. 


 [/QUOTE]
You can install a driver in XP to read write on ext2/3. The driver is on [www.fs-driver.org](www.fs-driver.org). This releives you from the max 4 GB per file restriction on FAT. Install is easy.

---

