---
title: "Ubuntu went crazy on me!!!!"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by hottshot104 on 2008-02-23
After searching the forums for a remedy as to why my audio volume was so low, I came across a page that had me update alsa-mixer.

After following that process step by step, and rebooting the computer, I came across a screen at boot up that said ubuntu couldn't recognize my screen and video card even though it was fine before.

I need help on fixing this (i'm using the ubuntu live cd to post this btw). Please help!

---

### Post by steveneddy on 2008-02-23
Reboot without the CD, get to a login prompt in a text screen

Ctrl+Alt+F1 or F2 or F3

and type in (after logging in with your user name and password)

```

 sudo dpkg-reconfigure -phigh xserver-xorg

```

That may save you.

---

### Post by taurus on 2008-02-23
Boot into recovery mode from GRUB menu and reconfigure your X server again.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by radiocognition on 2008-02-23
Im not familiar with what this package does, but I have had graphics issues in the past.  Although Gutsy comes with a screens and displays menu, I have found it to be very buggy,  Your graphics prefrences are kept in a file called /etc/X11/xorg.conf.  Whatever you did to to your system, it probably made a change to this file.  One way that I recovered from graphics problems is by copying the xorg.conf file that the live CD generates for my system and storing it as a backup in the X11 folder.  If something ever happens to my graphics, I can just overwrite the version that doesnt work with the .conf file that I know works.  You can do the same thing right from your live CD.  If you can mount your Ubuntu install from the live CD, you can copy the file directly to somewhere on your system.

[Copy xorg.conf from live CD]("http://ubuntuforums.org/showthread.php?t=662665")

---

### Post by hottshot104 on 2008-02-23
Right now I cannot even make it to the user screen.

The computer loads, the ubuntu loading screen comes up, then it goes back to some prompt on the computer and then flashes a distorted picture of the ubuntu loading screen before telling me that it cannot recognize my graphics card. Then even if I choose to proceed with low graphics, the computer restarts.

I'm not sure what happened :(

---

### Post by radiocognition on 2008-02-23
When you restart your computer, you should open the GRUB bootloader, giving you options on how to open the OS.  Choose boot into safe mode and follow the advice of taurus: 
> 
Boot into recovery mode from GRUB menu and reconfigure your X server again.



dpkg-reconfigure -phigh xserver-xorg
shutdown -r now

__________________


---

### Post by hottshot104 on 2008-02-23
I tried that to no avail. I think I am just going to reformat the computer and do a fresh installation.

Anyway, could you help me by answering:

How can I raise my sound? I clicked the sounds icon and raised the PCM volume and checked the alsa-mixer and the bars were all the way up.

---

### Post by radiocognition on 2008-02-23
If you want to, go ahead with the reinstallation.  I personally went through a few of those my own before I got the hang of how to use the terminal.  However, if this is a problem with just your graphics, you most likely will be able to recover by using the xorg.conf trick.

---

