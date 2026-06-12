---
title: "Ubuntu 7.10 installs okay; installing recommended updates gives brown screen"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by jck99nz on 2008-01-05
I've successfully installed Ubuntu from disk (no other OS on computer, new formatted partitions etc). Everything works fine. I then accept the 149 recommended updates. After restarting, I get graphical login prompt, and after logging in I here the Ubuntu sound.

At that point, white bars appear at the top and bottom of the screen (where app menu bars would normally be), flash a few times, then go away leaving a blank sandy screen. I can't do anything (except move the mouse pointer). No menus, can't open a terminal window. After a while, ctrl-alt-del lets me restart, but exactly the same thing happens.

I tried another clean install, and unchecked around 20 updates relating to Gnome, but ended up with same problem.

I've used the same CD on the same computer to successfully install Gutsy (and updates) over last month, but I began experiencing this problem a few days ago.

Does anyone know which update might be causing the problem? 

Dell Optiplex, 1GB RAM, ATI Radeon X1650 graphics, 500 GB HDD, Hauppauge PVR 150.
PS: Using Esc during grub loader and entering recovery mode let me look at dmesg; nothing strange. Not sure what else to look at or check.

---

### Post by scotty2 on 2008-01-05
Sorry I cannot offer help but I am experiencing the same symptoms.  I used the 7.10 Desktop AMD64 install (Windows Vista dual boot).  I get the brown screen and am unable to do anything (except PrintScrn brings up dialogue to save screen dump).  Computer specs are:
HP dx2250
AMD 64 X2 5000+
2 G RAM
ATI Radeon Xpress 1150

---

### Post by Xavieran on 2008-01-05
Looks like it could be an ATi problem (ARGH!);)

Have you enabled desktop effects?

Try Alt-F2 to launch the Ubuntu Appearances manager (What command is that?)

---

### Post by jck99nz on 2008-01-05
I haven't consciously enabled desktop effects; is it enabled by default? 

Alt-F2 does nothing. The only way I can do anything is to restart, Esc into grub, and enter recovery mode. 

Jeff

---

### Post by Xavieran on 2008-01-05
Try selecting failsafe GNOME ...or KDE depending on which DE you use...
Have you looked at .xsessionerrors?
Command for that would be cat .xsessionerrors |less

---

### Post by jck99nz on 2008-01-05
Not sure how to select failsafe GNOME. I rebooted, and chose recovery mode in Grub. cat .xsessionerrors gives a 'no such file or directory', and 'find' didn't find it. Do you know what directory it will be in?

I went into /var/log and looked at some logs. Only serious sounding error was:

jklinux-desktop gdm[4911]: Glib-CRITICAL: g_key_file_get_string: assertion `key_file != NULL' failed

No idea what that means, but it sounds bad.

Jeff

---

### Post by Xavieran on 2008-01-05
Should be in your home folder...
When you login in recovery mode you are automatically in / (I think)

---

### Post by jck99nz on 2008-01-05
When I boot in recovery mode, I'm in root home directory (# prompt), and ls shows no files. Sorry to be stupid, but is there a way to change to the user I log in under graphical login? I tried sudo - u jklinux (where jklinux is my user name), but it doesn't like it.

---

### Post by scotty2 on 2008-01-05
I have re-installed Ubuntu and have a working system.  I have added the repository for the canonical supported software only.  I can try loading  selected packages to identify which one causes the problem.  Can you suggest which of the 148 updates to try?

---

### Post by jck99nz on 2008-01-05
Hi Scotty2, it's reassuring to know I'm not the only one with this problem. I can't really advise - I've done around five clean installs, I've tried downloading from different mirrors, and I've tried unchecking updates related to gnome. Nothing's worked for me so far.

You could try looking for any updates which include 'Glib' in them, as this is the error message I got. Uncheck those before installing updates.

I'm getting tired of clean installs - have to go out shortly, perhaps I'll try again tomorrow.

Jeff

---

### Post by scotty2 on 2008-01-05
I will try only the security updates but excluding the kernel updates and see how that goes.

---

### Post by scotty2 on 2008-01-05
No problem after the security updates.  I will now try the linux-headers-2.6.22-14.

---

### Post by Krydahl on 2008-01-05
How long have you left it on that brown screen? There's a long thread about very slow startup here:

[http://ohioloco.ubuntuforums.org/showthread.php?t=585635](http://ohioloco.ubuntuforums.org/showthread.php?t=585635)

If I remember correctly, many people were seeing that brown screen for several minutes. Might make interesting reading even if it isn't your problem.

---

### Post by scotty2 on 2008-01-05
Linux-headers-2.6.22-14 updates install OK.  This appears to point to the problem being in one of the recommended updates.

---

### Post by godz on 2008-01-05
I have exactly the same problem. And it worked fine before I took some updates a couple of days ago. Ctrl+Alt+<- does work in order to kill all, but that is not a solution....

I can move the mouse pointer but not do anything, so my next plan is to ssh from another computer and try killing the gnome power and screensaver processes. Maybe a temp workaround could be to disable the screensaver/power mangare processes.

I have a Nvidia Geforce 7300 GT (by other words, the problem is not ATI related) and I am 100% sure this problem is connected to one of the recent updates.

I will post the ssh ps kill results ASAP.

---

### Post by jck99nz on 2008-01-05
Did you have any joy Godz? I agree it's a recent update. My system works fine until I install the updates (using default repositories as installed by Ubuntu). The problem occurs after I install updates. Over a week ago, I was clean installing and installing updates without getting any problem, so it must be related to a recent update.

Is there any way to get a list of chronological order of updates? If we can identify which ones were released in last ten days or so, it would narrow down the field.

---

### Post by jck99nz on 2008-01-05
Krydahl, thanks for the note re long login time. I've left the brown screen on for a couple of hours and no change. I get HDD activity for up to about a minute after the white (blank) windows menu bar stops flashing and disappears. From that point on, ctrl-alt-del works to get shutdown menu, so I think all processes that are going to run are up and running at that point.

---

### Post by jck99nz on 2008-01-05
To confirm Scotty's findings, I've done a clean install. Left all default repositories enabled,but unchecked all the 'recommended updates' and only installed security (64 of them). Rebooted, and things work fine.

---

### Post by godz on 2008-01-07
The "brown" (actually a faded brown ubuntu screen) has not appeard since last time so I have not been able to investigate different processes. Will keep you posted if it appear again. Strange if it never happens again......the only difference is the installed ssh daemon.

---

### Post by scotty2 on 2008-02-10
I finally plucked up courage (or was foolhardy enough) to apply all updates.  Install has completed successfully.  It would appear that whatever the problem was with the recommended updates has been fixed.

---

### Post by Sween on 2008-03-17
I just installed Ubuntu 7.10 last night and I had 199 updates to install. This morning I had the same problem as you guys have been having. I have nothing to say others than thanks for your dialog on the problem.

I'm just going to reinstall and pick updates that seem okay.

---

