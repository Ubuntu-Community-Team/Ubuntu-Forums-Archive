---
title: "Found firestarter"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by georgetoon on 2006-04-30
I found firestarter, installed it through the add applications routine.  At least I *think* it's installed.  I can't find it anywhere but it is shown as checked in the add apps area. 

Where do i find Firestarter?

---

### Post by bluevoodoo1 on 2006-04-30
Yeah it might not be in the menus... but from a terminal you can check to see if it's been installed.

gksudo firestarter

---

### Post by Sef on 2006-04-30
If you have Breezy, then it is under Applications > System Tools.  If you have Dapper, it is under Applications > Internet.

---

### Post by georgetoon on 2006-04-30
[QUOTE=bluevoodoo1]Yeah it might not be in the menus... but from a terminal you can check to see if it's been installed.

gksudo firestarter[/QUOTE]

that appeared to launch the program so I could get it configured, but I do not see it on the menus.

also, I closed the window and the program appears to stil be running...but again, I cannot find it on the menus.

Wait!  I just went to edit the menu and it's now there.

Okay, so how do I make sure that this net little app starts up each time I boot the system?

---

### Post by bluevoodoo1 on 2006-04-30
You'll have to add it manually... from a terminal

```
smeg
```

then browse to what folder you want to add firestarter to. 

then hit 'new entry,' name 'firestarter,' command 'gksudo firestarter' and for the icon i think it's named firestarter.png (it should be in the /usr/share/pixmaps folder)

---

### Post by Sef on 2006-04-30
Sometimes I just rebooted and firestarter was there under System Tools in Breezy.

---

### Post by georgetoon on 2006-04-30
[QUOTE=Sef]Sometimes I just rebooted and firestarter was there under System Tools in Breezy.[/QUOTE]

Yes!:) that was the same for me.:)

Now, how do I get FS to stsart on boot?  I see the tool for "Sessions" where I can add start programs...but where do I ad FS?  not sure which folder to navigate to grab the app.

---

### Post by confused57 on 2006-05-01
In Breezy, you can go to System---Preferences---Sessions---Startup Programs
and enter  gksudo firestarter.  When gnome is starting up, you'll be prompted to enter your password to start firestarter.  
Firestarter is just a gui configuration tool for the iptables; so once you get it configured  the way you want, you don't actually need to start firestarter when you login to your gnome session.  Your iptables are automatically running when you start your session and firestarter is just to make configuration changes.   I think there is a way to start firestarter without using your password, but it's not recommended for security reasons.  

Correct me if I'm wrong, but that is my understanding of firestarter.

Before I got my hardware router, I'd start firestarter when I logged on just to see the hits or probes to my computer; but once I installed the router, I almost never get any probes.

---

