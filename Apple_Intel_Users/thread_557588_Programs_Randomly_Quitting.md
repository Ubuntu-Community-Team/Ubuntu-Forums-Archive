---
title: "Programs Randomly Quitting"
date: 2007-09-22
forum: Apple Intel Users
---

### Post by czechman86 on 2007-09-22
Every other boot up or so, I experience a problem where my programs just quit. I think that it may be related to beryl, but not sure. It takes about fifteen minutes into the boot and then bam, everything quits and when i try to reopen them, they quit the second that the window comes back. i have checked the other forums on this subject and found no answers there. Is this possible kernel panic? i was unable to enter the code at the initial boot up, and have concluded that this could be one problem. i have plenty of memory and a good machine. is anyone having these same problems or does anyone have a any fixes for this problem. thanks!

---

### Post by cyberdork33 on 2007-09-22
> **czechman86 said:**
> Every other boot up or so, I experience a problem where my programs just quit. I think that it may be related to beryl, but not sure. It takes about fifteen minutes into the boot and then bam, everything quits and when i try to reopen them, they quit the second that the window comes back. i have checked the other forums on this subject and found no answers there. Is this possible kernel panic? i was unable to enter the code at the initial boot up, and have concluded that this could be one problem. i have plenty of memory and a good machine. is anyone having these same problems or does anyone have a any fixes for this problem. thanks!
dmesg would show any panics.

Have you tried using your computer normally without Beryl? that could limit the possibilities.

---

### Post by czechman86 on 2007-09-22
> dmesg would show any panics.

how would it appear in the terminal if there were any panics, after running dmesg?  Tomorrow when i boot up, i will try running the comp without using beryl. I will post the results after a few boot ups and about 30 minutes on each.

thanks!

---

### Post by cyberdork33 on 2007-09-23
> **czechman86 said:**
> how would it appear in the terminal if there were any panics, after running dmesg?  Tomorrow when i boot up, i will try running the comp without using beryl. I will post the results after a few boot ups and about 30 minutes on each.

thanks!
What I am trying to say is that the system should log it, and you would likely see a kernel panic message if you had a kernel panic, and I kinda doubt that is the issue from what you said anyway.

---

### Post by czechman86 on 2007-09-23
i do have an update. i am currently running the system without beryl and things were going fine until i opened my terminal, which quit randomly and then i had to reopen and things were fine. after i installed a new metacity and gtk theme and started to use them however, i got the following message:

> There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Process /usr/lib/control-center/gnome-settings-daemon received signal 11

GNOME will still try to restart the Settings Daemon next time you log in.

the theme completely changed, but i reopened the theme preference box and things went back to normal. just an update, but wondering if daemon could be the cause of the problems.

EDIT: After the error appeared, no other programs would launch and when i tried restarting the system, it hung and i had to do a force shut down (was not running beryl at the time). could this possibly have been a kernel panic? like i said, i was unable to enter the lpj=8000000 at the boot menu. is there a way to enter this now, even though i have already done an install. thanks.

EDIT 2: This is kernel panic, as a result of not entering lpj=8000000. could anyone please tell me how and where in the menu.lst file to enter this, so that i do not have to shut down my computer every hour or so, because the gui stops working. thank you!

---

### Post by cyberdork33 on 2007-09-23
> **czechman86 said:**
> This is kernel panic, as a result of not entering lpj=8000000. could anyone please tell me how and where in the menu.lst file to enter this, so that i do not have to shut down my computer every hour or so, because the gui stops working. thank you!

just add it to the end of your kernel lines. (You can also just edit a line in grub to test it first.

---

### Post by czechman86 on 2007-09-24
Thank you for the help, here is what i did:

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash lpj=8000000
```

and

```
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=13ec6168-8d1e-4daf-9fca-c0d295118062 ro quiet splash lpj=8000000
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=13ec6168-8d1e-4daf-9fca-c0d295118062 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=13ec6168-8d1e-4daf-9fca-c0d295118062 ro quiet splash lpj=8000000
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=13ec6168-8d1e-4daf-9fca-c0d295118062 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I now have one question regarding this, and a new issue that has appeared. my question is, did i enter it in correctly? my issue is now, my system will do a random log off and when i try to log back on, it only gives me a terminal, or in the case of this morning, the desktop would not work. i could click on applications and the panels, but the wallpaper area would not select anything and the right click function would not work. any ideas? thanks again!

---

### Post by czechman86 on 2007-09-25
I just reinstalled my system with another burned disk and things appear to have worked out this time. thanks again.

---

### Post by czechman86 on 2007-10-25
well, i am having this problem in gusty now and am confused as to what is going on. here is a brief synopsis of what i have been experiencing: the window decorator quits and then programs wont open, the fan starts to spin super fast and then the whole system crashes, but there is no log of anything out of the norm. i found this: Oct 26 04:00:55 macbook syslogd 1.4.1#21ubuntu3: restart. I had not pressed the restart button, this just randomly appeared. if anyone has any similar trouble or answers please post. thank you for your help!

---

