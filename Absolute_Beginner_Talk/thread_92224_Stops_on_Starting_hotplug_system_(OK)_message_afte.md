---
title: "Stops on Starting hotplug system (OK) message after reboot on new installation"
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by Boh on 2005-11-19
Hi all, am new to Linux OS & the first time I had installed Linux Ubuntu V5.10 was said to be initially successfull, CD tray opened then I removed the Install CD, reboot system. After reboot I press "enter" It now load on Ubunto message screen detect some devices & controllers then mark them OK ..now I was stop on "Starting hotplug subsystem (OK)" as listed on screen. then nothing comes out next. I already press "enter" key to check if there's any screen come out next on it but nothing happenes. I don't know on what to type or correct instruction to do next to this stage just to enter the Linux screen like Windows in which I could browse. Kindly help..am like an icecream to melt here! thanks !!!!!!:(

---

### Post by schdefan on 2005-11-19
Hi!
Welcome to ubuntu. When the hotplug message appears press 
STRG C to abort the hotplug (This is for hardware scanning) and the bot progress should go on,
Do you have some special hardware in your machine?
schdefan

---

### Post by Boh on 2005-11-19
Thanks for the help, can you pls let me know on what " STRG C " means? 
My system have no special device but only an new mobo model.

mobo:AOpen i915gm-Hfs 
CPU: Intel mobile Pentium 725 1.6Ghz
Apacer 256MB DDR memory
Seagate barracuda 20GB HDD on IDE1(master)
USB mouse(unplugging it ,no difference)
DVDRW 1616 drive on IDE1(slave)
The floppy drive has a 20 pins adapter
Onboard VGA

tnx!:smile:

---

### Post by desquer on 2005-11-20
It's supposed to read "ctrl c"

Dave

---

### Post by schdefan on 2005-11-21
STRG C kills thr process so that it doesn't run anymore. So in your case the hotplug system will be stopped.

---

### Post by syd3n on 2005-11-23
i am seeing the same problem on a desktop that has pretty much all peripherals integrated into the mobo.  i can't even hit ctrl-c when the system stalls after displaying "Starting hotplug subsystem".  i am using Ubuntu 5.10.

---

### Post by syd3n on 2005-11-23
i have been searching through all the forums and see a few other people with the same issue, but no definitive resolution out there.  here are the links to the other posts:

[http://ubuntuforums.org/showthread.php?t=93011](http://ubuntuforums.org/showthread.php?t=93011)

[http://ubuntuforums.org/showthread.php?t=92098](http://ubuntuforums.org/showthread.php?t=92098)

[http://ubuntuforums.org/showthread.php?t=93551](http://ubuntuforums.org/showthread.php?t=93551)

not sure if there are any others that i missed during my searches.

help please!  i love ubuntu!!

---

### Post by schdefan on 2005-11-24
What happens if you boot into recovery mode? THis is the second entry in grub menu? Does this error appear also when you boot from Ubuntu Live CD?
schdefan

---

