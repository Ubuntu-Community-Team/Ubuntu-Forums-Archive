---
title: "I Need Serious Help !!!!!!!!"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by xXx 0wn3d xXx on 2006-03-24
I have a Gateway MX7118 and here are the specs:

2.2 ghz AMD processor
512 of ram
Ati Radeon Xpress 200M graphics card

Now, when I boot the live cd, everything goes fine until I get past the splash screen and then I get "Failed to Start X." What should I do ? I really need some help.

---

### Post by KansasJoe on 2006-03-24
sudo nano etc/X11/xorg.conf

change the driver under your video card to vesa

---

### Post by trent dillman on 2006-03-24
Well...have you tried any other Live CDs? Knoppix? Damn Small?

Try booting the live disk, and when you get in and it fails again, drop to CLI by pressing CTRL+ALT+F2. This should drop you to a prompt. Then try this:

```
startx > xerror.txt 2>&1
```

After that, post that file here and let's see what's up.

Also, follow KansasJoe's advice, and while you're reading through the config check and make sure your BusID is correct (probably "PCI:1:0:0").

---

### Post by xXx 0wn3d xXx on 2006-03-24
Thanks, this is the only help I got so far. Let me try those ideas, I really want Ubunt on my new laptop :(

---

### Post by xXx 0wn3d xXx on 2006-03-24
Nothing worked. Should I just try to install or should I try another linux distro like Fedora Core or SuSE ?

---

### Post by JoshHendo on 2006-03-24
I have got this a few times before, though only on really old computers, with a old sis graphics card. I gave up there, becuase it wasn't worth fixing, though this could be. When you go "OK" or something, it will send you to a DOS like screen. Type in there what trent and joe said. You will need to type in the super user password. I don't know what the default super user password for Ubuntu live is, though someone else may know.

---

### Post by xXx 0wn3d xXx on 2006-03-24
[QUOTE=JoshHendo]I have got this a few times before, though only on really old computers, with a old sis graphics card. I gave up there, becuase it wasn't worth fixing, though this could be. When you go "OK" or something, it will send you to a DOS like screen. Type in there what trent and joe said. You will need to type in the super user password. I don't know what the default super user password for Ubuntu live is, though someone else may know.[/QUOTE]
I don't think there is a superuser for ubuntu live. You can run and execute all commands without sudo.

---

### Post by trent dillman on 2006-03-24
I'll tell you, MasterChief... you might just want to try out Mandriva Linux. It is very user friendly, and it also has a live CD you can try.

---

### Post by gerbman on 2006-03-24
[QUOTE=MasterChief1234]Nothing worked. Should I just try to install or should I try another linux distro like Fedora Core or SuSE ?[/QUOTE]

Can you provide any information aside from "it didn't work"? Were you able to get to the command line as suggested in the above post? If not, what happened? Any error messages?

---

### Post by Sef on 2006-03-24
> Now, when I boot the live cd, everything goes fine until I get past the splash screen and then I get "Failed to Start X." What should I do ??? I really need some help.

Have you another computer that you could check the live cd on?  The Live Cd may be bad.

---

### Post by xXx 0wn3d xXx on 2006-03-24
[QUOTE=gerbman]Can you provide any information aside from "it didn't work"? Were you able to get to the command line as suggested in the above post? If not, what happened? Any error messages?[/QUOTE]
Yes, I am able to get to a command line. The error message is as follows:

"Failed to start the X server (Your Graphical Interface). It is likely that it is not set up correctly. Would You like to view the X server output to diagnose the problem."

Then

"The X server is now diabled. Restart GDM when it is configered correctly."

---

### Post by trent dillman on 2006-03-24
hey, you're doing great then....when it asks about details, say yes and post those...i'll bet it didn't autodetect the right BusID!

that was my problem when it asks during the disk install for the BusID....

---

### Post by dcstar on 2006-03-24
[QUOTE=MasterChief1234]THIS IS MY 6th THREAD IN 3 DAYS AND I HAVE GOTTEN NO RESPONSE TO ANY OF THEM. RIGHT NOW I AM VERY ANGRY AND READY TO GIVE UP ON UBUNTU. PLEASE HELP !!!
.......[/QUOTE]
There are sub-forums on Installation and Upgrade Help, as well as Laptop sub-forum and a search function where you may have found this:

[http://ubuntuforums.org/showthread.php?t=127344&highlight=x200m](http://ubuntuforums.org/showthread.php?t=127344&highlight=x200m)

---

