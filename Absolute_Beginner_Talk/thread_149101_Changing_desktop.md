---
title: "Changing desktop"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by gr0kzer0 on 2006-03-23
I recently installed Breezy on a Compaq Presario 1246 laptop. It's only got 156MB of RAM, so it's understandably sluggish under the default Gnome desktop. Could anyone explain how to change to one of the lighter desktops? And which would people recommend?

---

### Post by OffHand on 2006-03-23
This link might help: [http://www.psychocats.net/linux/xubuntu.php](http://www.psychocats.net/linux/xubuntu.php)
Xfce is one of the lightest desktop environments.

Basicly it's "sudo apt-get install xubuntu-desktop" (without quotes) if you got all the repositories enabled.

---

### Post by drummer on 2006-03-23
I'd give xfce a go. Very easy to install, just do```
sudo apt-get install xubuntu-desktop
```
after of course enabling extra repositories ( [http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories) ).

---

### Post by frodon on 2006-03-23
Then to remove GNOME desktop and related apps : [http://ubuntuforums.org/showthread.php?t=96046](http://ubuntuforums.org/showthread.php?t=96046)

---

### Post by jbmalone on 2006-03-23
Before you completely ditch GNOME, I'd look into running Openbox as your window manager.  I tried Xubuntu, and really liked it, but it seemed to minimalist for me.

---

### Post by frodon on 2006-03-23
Or just use the XFCE window manager, it respect your GTK themes, it has an embedded compositor and it's lighter than metacity ;)
A link to a quick guide to do that : [http://doc.gwos.org/index.php/Xfwm4](http://doc.gwos.org/index.php/Xfwm4)

---

### Post by gr0kzer0 on 2006-03-23
Thanks for the help everyone. Is xfce on the Breezy cd? I don't have internet access. Or can i use, say, the windows pc at the library to download it and stick it on a disk to take home?

---

### Post by gr0kzer0 on 2006-03-27
Sorry to be a pest, i still need help. Went to packages.ubuntu.com, couldnt find xfce. I've got to change from gnome, it eats my ram! Where can i get xfce? And... what do i do when i have got it on cd? Plz note, my computer is not online, i'll download the files to cd using a windows box at the library, then load from cd to my laptop. But i'm a n00b, i know nothing about installing stuff. Plz help

---

### Post by engla on 2006-03-27
[QUOTE=gr0kzer0]Sorry to be a pest, i still need help. Went to packages.ubuntu.com, couldnt find xfce. I've got to change from gnome, it eats my ram! Where can i get xfce? And... what do i do when i have got it on cd? Plz note, my computer is not online, i'll download the files to cd using a windows box at the library, then load from cd to my laptop. But i'm a n00b, i know nothing about installing stuff. Plz help[/QUOTE]
There are lots of packages in xubuntu-desktop, so one person made a whole addon CD used for installing it. 

There is a small note about it [here on the Ubuntu wiki.]("https://wiki.ubuntu.com/UnofficialUbuntu510AddOnCD?highlight=%28addon%29") There are torrent links to the CD image [(one here)]("http://24.76.176.29/Xubuntu%20add-on%20CD.torrent"), it weighs 200M and should have everything you need to install xubuntu-desktop on an ubuntu system.

The problem is that you need a friend to download the big file and burn it to a disc.   To use it later, you should use synaptic the package manager, use "Add CD" (found in the menus) and then just search for xubuntu-desktop and mark it for install, apply.


But, if you just want to install a single package .deb file that you downloaded, you do this in a terminal to install it:
**sudo dpkg -i** *~/Desktop/package.deb*
Where you have to fill in the correct path to the package.


**Added:** [Here is XFCE4 on packages.ubuntu.com]("http://packages.ubuntu.com/breezy/x11/xfce4"). You can get it there, but that package has lots of *dependencies* (the packages listed with red dots) that are also needed. Many are already installed, but those named xfce4-* certainly are not.. so there is not single file to download, but you have to collect a huge heap of them :(. Hence, someone made a CD.

---

### Post by wsanders on 2006-03-27
[http://packages.ubuntu.com/breezy/x11/xfce4](http://packages.ubuntu.com/breezy/x11/xfce4)

Then, when you load them from the CD, type 
[code]sudo dpkg -i *package name*[\code]

---

### Post by gr0kzer0 on 2006-03-27
Thanks a lot everyone! I really appreciate the help! Now to find someone to burn a cd for me. That, or get ready for a marathon download. Still, gotta be done... I gotta get a less ram-hungry desktop going here.

---

### Post by gr0kzer0 on 2006-03-27
Um... sorry, i got another question. I'm gonna install xfce and get rid of gnome, right? Well, playing music is one of my main computer activities, and i use rhythmbox. Well, the packages site calls rhythmbox the _gnome_ music player. So when i get rid of gnome, am i gonna break rhythmbox? If so, which player will go ok with xfce? or can i keep rhythmbox with the new desktop?

---

### Post by aysiu on 2006-03-27
Get rid of Gnome, and then install Rhythmbox--any dependencies Rhythmbox needs will also be installed, and I don't think it needs the entire Gnome desktop.

---

### Post by RedKnight on 2006-03-27
I would deffinetly recommend xfce its such a lightweight and fast desktop.
I've run it on fedora core 4 with 128mb ram.

---

### Post by gr0kzer0 on 2006-03-27
Yeah redknight, i've got just 156MB of RAM, thats why i gotta dump gnome - i tried to create a database in OpenOffice earlier, and it wouldnt even start! And the word processor is so _slow_, i need that lighter gui. So guys, i install xfce, uninstall gnome and rhythmbox, then reinstall rhythmbox? Have i got that straight? Dont wanna screw it up. And remember, i'll be manually downloading it all.

---

