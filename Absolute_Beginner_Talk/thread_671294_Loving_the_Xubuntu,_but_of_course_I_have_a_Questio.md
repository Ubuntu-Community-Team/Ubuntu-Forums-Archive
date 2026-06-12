---
title: "Loving the Xubuntu, but of course I have a Question."
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by OZFive on 2008-01-18
Hi all,

After the untimely death of my beloved CRT iMac (sage) I was in need of a new computer but with no $ I was up the creek. But I finally got my hands on an old Dell Latitude CPi laptop.  It was running Windows 98 (not even the Second Edition!)  I was able to "upgrade" it to Windows XP but was not pleased with the responsiveness and all the updates was so "kind" to load on there after I was satisfied it was internet ready.  I only have a 6gb HD on the thing and all that took up about 4.5gb!  Geeze.  So I decided to do what I wanted to do in the first place but was unsure to try.  I installed Xubuntu!  After a few hours of cursing it to get the resolution right and not VGA, I got it right and started to configure it to make it more easy for me to use.

So here is the issue,  I wanted to place the XFCE Menu up in the left corner like it does wiht install and have another down in the platform along the bottom that I am configuring like a Mac OSX Dock.  So I started to configure the top left corner one to be system prefrences and help  and related tasks.  But then when I went to the bottom to use it as an application launcher (kind of like a folder tree in the OSX Dock) I found it had also been configured to mirror the upper left one!  Yikes!

So my question is.. is there an easy way to reset it to the installed Menus?  Or if not, I can configure it manually but I need to know where all the applications are kept so I can place them in the menu.  

Thanks for the help!

Loving the Xubuntu!

---

### Post by spiderbatdad on 2008-01-18
most applications found in the  menu can be added to the panel by right click on the application and choose add to panel. If its on the top panel but you want it on the bottom, just drag it down there. You may have to right click on the icon to make sure it isn't locked to the panel. If you want to create custom launchers, right click on the panel and choose add to panel, then select custom application launcher. The command is generally the name that launches the program and not necessarily the complete path...gkrellm, for example would be the command for a launcher of that name, if you had installed gkrellm and wanted a launcher on your panel.

---

### Post by gn2 on 2008-01-18
The panels can be customised very easily.
Right-clicking on a panel iten, select Move and drag and drop it where you want it to go, either along the panel or to the other panel.
In Settings manager>Panel you can make the Panel Freely Moveable, this will reduce it's size and will make it sit above open windows.
[IMG]http://i174.photobucket.com/albums/w109/gn1v/Screenshot-2.png[/IMG]

---

### Post by OZFive on 2008-01-19
Well I was able to fix it thanks folks!  It was actually a matter of going ~/.config/xfce4/desktop and getting a file named something about a menu.  It is late night and I did it earlier today and I forgot!  Sorry but it is fully restored and I am a happy camper!

:D

---

