---
title: "Video not working"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by InsertNameHere on 2007-10-28
This is gutsy
Video wont work sound works...
I have every possible codec and VLC.

I removed a package earlier then i saw it going wild then I found out it's tring to remove everything desktop based on my computer... I reinstalled just about everything right now.. Sound works but video wont. It freezes everytime I try to play something (by sound works I mean Amarok, when I use totem and VLC to play sound AND video files it doesnt work). 

Can someone tell me what packages might I be possibly missing? (or if you will list them all so I can hand check one by one)

I tried reinstalling VLC but it didn't work.

Thanks.....

---

### Post by InsertNameHere on 2007-10-28
Am I hopeless............?

---

### Post by Crafty Kisses on 2007-10-28
> **InsertNameHere said:**
> Am I hopeless............?

What error did you get when you tried to reinstall VLC?

---

### Post by InsertNameHere on 2007-10-28
There was no error, it reinstalled fine then when I try to play a media it freezes.

---

### Post by Crafty Kisses on 2007-10-28
> **InsertNameHere said:**
> There was no error, it reinstalled fine then when I try to play a media it freezes.

The only thing I could think of is something is using a lot of resources, and when you try to play the video it just crashes the Web browser.

---

### Post by InsertNameHere on 2007-10-28
It worked fine when I played anything last night, just after I accidently removed all packages.

---

### Post by lpevey on 2007-10-28
Open vlc from a terminal.  Go to Applications -> Accessories - > Terminal and type vlc.  When you try to open a video file, what error message is displayed in the terminal?

If you think you may have removed some important desktop packages by accident, you could try a complete re-install of your desktop environment.  I would only do this if all else fails.  

Type (or cut and paste) into a terminal:

sudo /etc/init.d/gdm stop

This will kill X, the graphical display manager, and take you to a text login screen.  If you don't see a login screen, type:

Ctrl + Alt + F1

Enter your username and password.

sudo apt-get remove ubuntu-desktop

(This might take a while.  It will remove a LOT of stuff.  You will have to reinstall a lot of packages.  Again, only do this if nothing else works and you don't want to reinstall Ubuntu from scratch.)

sudo apt-get install ubuntu-desktop

Then, type the following to get back into Gnome and re-install the rest of your packages:

sudo /etc/init.d/gdm start

---

### Post by InsertNameHere on 2007-10-28
OK, its working, I typed sudo apt-get install ubuntu-desktop (without removing first) then it did stuff and I rebooted and it works.

Thanks for the help =)

---

