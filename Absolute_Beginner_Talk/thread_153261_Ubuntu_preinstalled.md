---
title: "Ubuntu preinstalled"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by wolfee on 2006-03-31
If I have ubuntu on my hard drive and take my hd out and put it in another computer will it preconfigure for devices? Like video,sound,monitor,ethernet card.ect?

---

### Post by Razorback on 2006-03-31
I recently changed out my mobo, ram and cpu.  All I did was reconfigure my xorg.conf file and everything came back up and worked fine.  I had to do this because X crashed on the first boot.  I still need to d/l the smp kernel for my P4 since it has HT but otherwise everything works great.

---

### Post by wolfee on 2006-03-31
[QUOTE=Razorback]I recently changed out my mobo, ram and cpu.  All I did was reconfigure my xorg.conf file and everything came back up and worked fine.     

How do I do that?:-k 
I want to have a 2nd hd to take over friends homes to show them on their machines so I don't need to spend 45 min installing. Does it take a long time to configure? I ask becaus I did my kermal from 1386 to i586 in termunal and it took 2hrs!!!

---

### Post by NeghVar on 2006-03-31
You might try a Live CD unless your trying to show all the software and how simple it is, although for that you could have your friend over to see yours and use the LiveCD to show them the hardware recognition on their machine, hopefully it actually detects it all lol

---

### Post by Razorback on 2006-03-31
Try to boot the pc on the hard drive.  It will probably stop just before the login screen saying X could not start because your hardware has changed.  You will need to get to the command line interface or terminal interface.  You can possibly get there by Ctrl-Alt-F1.  Then type:

sudo dpkg-reconfigure xserver-xorg

to reconfigure X.  Have you had to do this before?

Another way is to hit the esc key while grub is loading and start in recovery mode.  This will take you to the CLI where you can reconfigure X.  It has worked for me.  Someone else my have some other suggestions.

Or you can do what NeghVar suggested.

---

### Post by wolfee on 2006-03-31
Thanx! sorry my spelling is horrible!!! Anyway I did consider the live cd but in order to "convert" them I want to show all the bells and whistles!! I even have the mutiverse and universe on the 2 dvd set!! And Automatix on cd!! So I'm dead serious about getting all my friends out of microshaft!!

---

### Post by Razorback on 2006-03-31
You may also run into video and sound issues depending on their hardware but hopefully it will be automatically detected.  Good luck - they should be amazed.  I know I was when I first started trying ubuntu out.

---

### Post by wolfee on 2006-03-31
Good luck - they should be amazed.  I know I was when I first started trying ubuntu out.[/QUOTE]
 I was too!!! So much that I no longer even have a microshaft os!!!

---

