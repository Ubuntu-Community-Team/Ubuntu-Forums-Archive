---
title: "My mouse cursor has become ugly"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by LinuxIsInnovation on 2007-12-31
I installed a package "artwiz-cursor" yesterday. Since then, I lost my default Human-theme cursor and I have a black ugly cursor :(
Earlier, when I clicked on the Default cursor option in Preferences -> Appearance -> Customize -> Pointer, I used to have the white gutsy cursor as default. But as the Human cursor is no longer present, a black ugly cursor is what I get on clicking default. When I tried to install the package "human-cursors-theme", it asks me to remove human-theme, ubuntu-desktop and ubuntu-artwork.

```
root@Muzic-Jukebox:~# sudo aptitude install human-cursors-theme
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  human-theme 
The following packages are unused and will be REMOVED:
  devhelp-common fuseiso libgbf-1-common libglitz-glx1 libglitz1 
The following NEW packages will be installed:
  human-cursors-theme 
0 packages upgraded, 1 newly installed, 5 to remove and 0 not upgraded.
Need to get 19.2kB of archives. After unpacking 2245kB will be freed.
The following packages have unmet dependencies:
  human-theme: Conflicts: human-cursors-theme (<= 0.5) but 0.5 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
human-theme
ubuntu-artwork
ubuntu-desktop

Install the following packages:
xubuntu-default-settings [0.35 (gutsy)]

Score is 248

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
root@Muzic-Jukebox:~# 

```

It also asks me to install xubuntu-default-settings???? :o
Why? I haven't installed XFCE, I am using Gnome + KDE4..
How do I get back the human cursors theme?

---

### Post by LinuxIsInnovation on 2007-12-31
Also, it says that human-theme is broken. But I dont see anything when I click on Broken filter in synaptic.

---

### Post by LinuxIsInnovation on 2008-01-05
Bump.. :(

---

### Post by darylb on 2008-01-10
Have you seen this thread?:

[http://ubuntuforums.org/showthread.php?t=597855](http://ubuntuforums.org/showthread.php?t=597855)

I have the same problem at home. I'm going to try that fix when I'm there, it reportedly worked for someone already though :)

Good luck!

---

### Post by LinuxIsInnovation on 2008-01-11
> **darylb said:**
> Have you seen this thread?:

[http://ubuntuforums.org/showthread.php?t=597855](http://ubuntuforums.org/showthread.php?t=597855)

I have the same problem at home. I'm going to try that fix when I'm there, it reportedly worked for someone already though :)

Good luck!

 But for me, the field is already blank.. :o

---

### Post by LinuxIsInnovation on 2008-01-11
Is there some way to change the default pointer from HUman to DMZ (White)??

---

