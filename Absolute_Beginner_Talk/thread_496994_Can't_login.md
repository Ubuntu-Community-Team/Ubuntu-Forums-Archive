---
title: "Can't login"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by kfrance on 2007-07-09
I can't seem to log into my machine using the graphical interface.  I get the login screen type, enter my username and password and then I get a blank screen.  I don't get a hour glass like I've seen others talk about.  Using a terminal, ctr-alt-F1, I can log in and do stuff.  I've tried "sudo dpkg-reconfigure xerver-xorg" and "sudo dpkg-reconfigure gdm" but with no luck.  I've been using my system for some time with no problems.  As far as I can remember I haven't changed anything.  I installed some updates but I think they were fairly unrelated.  I have plenty of hard-drive space (although when I started debugging I had used 98% of my root partition but I'm now down to 33%), as a I saw this was a problem on other people's machines.  I've run fsck and there doesn't seem to be any problems with my partitions.  I've tried my original xorg.conf file that I know should work.  It seems to be a problem with gdm but I don't know where to go from here.

---

### Post by MikeDX on 2007-07-09
Try creating another user and logging in with that instead. It could be that you've buggered your gnome settings up.

Have you tried any of the failsafe terminals at the login screen?

---

### Post by kfrance on 2007-07-09
I've tried logging into other user names with no luck.  Let me go try using a failsafe terminal.  I'm going to guess that that will work but I want to get into gnome.

---

### Post by bodhi.zazen on 2007-07-09
go to your terminal (Ctlr-Alt-F1) ; Log in if needed

```
sudo /etc/init.d/gdm stop
startx
```

Post any error messages.

---

### Post by kfrance on 2007-07-09
I messed with that a little and it might have brought up something.  I was hoping to have everything that startx spit out but I couldn't seem to capture it into a file with startx > startx.log.  When I do startx I get a grey screen with a x for the mouse cursor.  When I do a CTRL-ALT-BACKSPACE I get back to the terminal and the last thing that I see is FreeFontPath: FPE "/usr/share/fonts/X11/misc" recount is 3, should be 2; fixing.  But it says it is fixing everytime I try and log in.  I've tried letting it run for two minutes but perhaps it needs more time to fix the problem.

---

### Post by kfrance on 2007-07-10
If I leave my computer booting for ten minutes I'm able to get in.  I get an error message once I get in saying that there was a problem with the gnome settings daemon.  My settings all appear to be in order however and I'm able to use my computer without problems.  I've attached a screen shot of the error message.  How do I fix this?  I don't want to wait ten minutes every time I boot.

---

### Post by twiceasworn on 2007-07-10
That is a bit strange.  You say that you did some updates.  Do you by chance remember what they were?  Sounds like something borked gnome.

---

### Post by kfrance on 2007-07-10
I know for sure that gimp was updated but I can't remember anything else.  Is there a way there a way to view what updates have been made recently in a log file or something.  I searched google briefly but didn't find anything.

---

### Post by kfrance on 2007-07-12
It seems that other people who have solved this problem have had different problems.  Some it is because their /etc/networking/interfaces file is messed up.  Others just have to delete their gnome settings and then reboot.  It seems weird that such different things that seem unrelated can lead to the same problem.  There must be an explanation for all of this.  Anybody have any ideas where I can look.

---

### Post by kfrance on 2007-07-12
It is a little frustrating but this morning when I logged in I didn't have the problem.  I hadn't worked on fixing the problem since yesterday morning and it wasn't working then.  I wish I could post here how I fixed the problem.  It just went away.

---

### Post by family on 2007-07-12
anybody try 

acpi=force

at the end of the line booting your kernel in the menu.lst file in the grub folder? It was recommended to me but I never got around to doing it since it requires root user privileges.

---

