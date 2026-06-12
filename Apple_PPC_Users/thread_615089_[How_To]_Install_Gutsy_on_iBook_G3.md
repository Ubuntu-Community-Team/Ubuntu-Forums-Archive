---
title: "[How To] Install Gutsy on iBook G3"
date: 2007-11-16
forum: Apple PPC Users
---

### Post by St3aMco0ker on 2007-11-16
First and foremost, I'd like to say thanks to those people who contributed and came up with the solution to fix the live cd boot problems.

I have put together a guide to help those who have trouble installing gutsy on their PowerPC Apple computers.

Like usual, boot from your CD, then follow this guide:

```
1. live-nosplash break=top
2. modprobe ide_core;exit
3. press ctrl+alt(option)+F1 once desktop is about to load (hour glass) to bring back to console
4. sudo date -s "Fri Nov 11 19:11:32 PST 2007"
5. ctrl+alt(option)+F7 to bring back desktop and do your normal installation. Once done, reboot.
6. repeat step 1-3
7. sudo fdisk -l
8. look for your system partition, mine is hda3
9. sudo mount /dev/hda3 /mnt
10. sudo nano /mnt/etc/yaboot.conf (ctrl + x, press y, press enter to save)
11. sudo /mnt/usr/sbin/ybin -C /mnt/etc/yaboot.conf
12. sudo reboot
13. it will take awhile for the system to kick you to BusyBox again
14. modprobe ide_core;modprobe ide_disk;exit
15. wait for your computer to be started
16. sudo nano /etc/initramfs-tools/modules
17. add the line ide_core and ide_disk (ctrl + x, press y, press enter to save)
18. sudo reboot
19. That is it! GOOD LUCK!
```

---

### Post by ik80 on 2007-11-17
thanks for this tutorial.
one question: would this work also for an iBook G4?
i want to dualBoot my laptop, and until now i have only OSX installed.

---

### Post by Auria on 2007-11-17
> **ik80 said:**
> thanks for this tutorial.
one question: would this work also for an iBook G4?
i want to dualBoot my laptop, and until now i have only OSX installed.

Sorry, i don't know (hopefully someone else will) i would just like to say that for a first experience on linux version 7.04 may be a better choice ( unless you feel like getting your feet wet in solving ubuntu PPC problems :D )

---

### Post by ik80 on 2007-11-17
> **Auria said:**
> Sorry, i don't know (hopefully someone else will) i would just like to say that for a first experience on linux version 7.04 may be a better choice ( unless you feel like getting your feet wet in solving ubuntu PPC problems :D )

thanks Auria. i think i'll try the 7.04 version for now.

---

### Post by Xumbi on 2008-04-17
Thanks very much for putting this together.  I just tried this on my 800MHz G3 iBook.  I did find a couple of things that you missed though:

1. live-nosplash break=top
2. modprobe ide_core;exit
3. press ctrl+alt(option)+F1 once desktop is about to load (hour glass) to bring back to console
4. sudo date -s "Fri Nov 11 19:11:32 PST 2007"
5. ctrl+alt(option)+F7 to bring back desktop and do your normal installation. Once done, reboot.
6. repeat step 1-3
7. sudo fdisk -l
8. look for your system partition, mine is hda3
9. sudo mount /dev/hda3 /mnt
10. sudo nano /mnt/etc/yaboot.conf**, add 'break=top' to the 'append=' lines** (ctrl + x, press y, press enter to save)
11. sudo /mnt/usr/sbin/ybin -C /mnt/etc/yaboot.conf
12. sudo reboot
13. it will take awhile for the system to kick you to BusyBox again
14. modprobe ide_core;modprobe ide_disk;exit
15. wait for your computer to be started
16. sudo nano /etc/initramfs-tools/modules
17. add the line ide_core and ide_disk (ctrl + x, press y, press enter to save)
**17a. sudo update-initramfs -u -k all -v**
18. sudo reboot
[B]18a. when the system comes back up, remove 'break=top' from the 'append=' lines in /etc/yaboot.conf
18b. sudo /usr/sbin/ybin -C /etc/yaboot.conf
18c. sudo reboot[/B]
19. That is it! GOOD LUCK!

That's everything I did.  Thanks again!

---

