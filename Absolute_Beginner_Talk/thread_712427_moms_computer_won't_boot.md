---
title: "moms computer won't boot"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by AnLGP on 2008-03-01
at all.  she was running XP.  I don't know what happened (i'm coming in late to the game) and now it goes to a black screen and all it says is this:  "reboot and select proper boot device OR" (paraphrase ->) insert proper boot media device.  I'm running off an ubuntu live CD, have already installed ubuntu on here using the guided part to use the whole system and I get that black screen when I try and boot.  I don't think there was windows on here when I arrived but now i'm about 95% sure there is not.  Any help?  Thanks.

---

### Post by herbster on 2008-03-01
You're talking about one computer, right? Seems to me you wiped any Windows drive/partition during your install, so you just have Ubuntu on your system. Open a terminal and paste the output of:

```
df -h
```

and

```
sudo fdisk -l
```

---

### Post by AnLGP on 2008-03-01
Yes, one computer.  here's the df -h output:

Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 252M   33M  219M  14% /lib/modules/2.6.20-15-generic/volatile
tmpfs                 252M   33M  219M  14% /lib/modules/2.6.20-15-generic/volatile
varrun                252M   96K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M  132K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
tmpfs                 252M  240K  252M   1% /tmp

and here's sudo fdisk -l:


Disk /dev/hde: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1       14405   115708131   83  Linux
/dev/hde2           14406       14593     1510110    5  Extended
/dev/hde5           14406       14593     1510078+  82  Linux swap / Solaris

Disk /dev/hdg: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdg1   *           1       14405   115708131   83  Linux
/dev/hdg2           14406       14593     1510110    5  Extended
/dev/hdg5           14406       14593     1510078+  82  Linux swap / Solaris

---

### Post by benerivo on 2008-03-01
How far in to the boot sequence does it get before it presents you with this messsage? Was XP working fine before Ubuntu was installed?

Try going in to the /boot/grub/menu.lst file (using the live cd), and changing the text at the bottom of the file (where your primary boot option is) so that it ends in verbose, like this...

kernel	/boot/vmlinuz-2.6.24-1-686 root=/dev/sda3 verbose


This might bring up more error messages that could help you diagnose what the exact problem is.

---

### Post by herbster on 2008-03-01
Okay, I think I misunderstood your problem. I was assuming you were wondering where your XP install had gone, but I see it's a GRUB issue most likely. Paste your grub menu:

```
cat /boot/grub/menu.lst
```

---

### Post by AnLGP on 2008-03-01
I don't know the exact story but no, XP was not working OK before I installed Ubuntu.  It gets right past the "Hit F2 to go into SETUP mode".  There's no "GRUB" in my /Boot Directory.  This is what's listed in /boot:

abi-2.6.20-15-generic

config-2.6.20-15-generic

initrd.img-2.6.20-15-generic.bak

memtest86+.bin

System.map-2.6.20-15-generic

vmlinuz-2.6.20-15-generic

aditionally, herbster, it says this:

ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory

---

### Post by herbster on 2008-03-01
Hmmm, you appear to not have grub installed, or not on the correct partition. Just out of curiosity, paste the output of:

```
locate menu.lst
```

May have to reinstall grub or change your boot device in BIOS.

---

### Post by AnLGP on 2008-03-01
locate: warning: database /var/lib/slocate/slocate.db' is more than 8 days old
/usr/share/doc/memtest86+/examples/grub-menu.lst
/usr/share/doc/grub/examples/menu.lst
/usr/share/ubuntu-docs/ubuntu/sample/menu.lst_addwindowsentrygrubmenu
/usr/share/ubuntu-docs/ubuntu/sample/menu.lst_changegrubpasswordforgotten
/usr/share/ubuntu-docs/ubuntu/sample/menu.lst_displaysplashimagegrub

---

### Post by herbster on 2008-03-01
Okay, paste the output again, but do this first:

```
sudo updatedb
```

When it's done do the locate menu.lst.

---

### Post by AnLGP on 2008-03-01
/usr/share/doc/grub/examples/menu.lst
/usr/share/doc/memtest86+/examples/grub-menu.lst
/usr/share/ubuntu-docs/ubuntu/sample/menu.lst_addwindowsentrygrubmenu
/usr/share/ubuntu-docs/ubuntu/sample/menu.lst_changegrubpasswordforgotten
/usr/share/ubuntu-docs/ubuntu/sample/menu.lst_displaysplashimagegrub
/rofs/usr/share/doc/grub/examples/menu.lst
/rofs/usr/share/doc/memtest86+/examples/grub-menu.lst
/rofs/usr/share/ubuntu-docs/ubuntu/sample/menu.lst_addwindowsentrygrubmenu
/rofs/usr/share/ubuntu-docs/ubuntu/sample/menu.lst_changegrubpasswordforgotten
/rofs/usr/share/ubuntu-docs/ubuntu/sample/menu.lst_displaysplashimagegrub

---

### Post by lolzlolz on 2008-03-01
im gonna jump in, it should boot fine now i think, try it 
i think herbsters command worked

---

### Post by ugm6hr on 2008-03-01
I would suggest running a diagnostic test on the HD.

The HD manufacturer should have them available, or the UltimateBootCD ([http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)) has them too.

If that says everything is OK, wipe the HD completely (including MBR) with something like Killdisk (again - see UltimateBootCD).

Then try reinstalling Ubuntu again.

This appears to be a hardware issue if a fresh Ubuntu install has gone awry (assuming your LiveCD is OK).

---

### Post by herbster on 2008-03-01
Yeah you don't seem to have GRUB installed, there's definitely something wrong and it could be the HD. You may have missed a step/wrongly configured a part of the install process as well.

---

### Post by AnLGP on 2008-03-01
Which one of these do I choose from?  And yes, live CD is OK.  Thanks for all your help so far everyone.  If I knew how to thank you guys on here I would (via thanked in 'x' amount of posts').  Also, I'm attempting to install 7.04; to which I realize (and have installed on my own box at home) there is a 7.10 available -- this shouldn't matter, should it?  Figured I'd CMA.

---

### Post by herbster on 2008-03-01
Are you asking which option do you choose during install? If you're wiping your system clean and can afford to do a clean install, then the default should be okay IIRC. Using 7.04 isn't a problem, just that of course 7.10 will have a newer kernel and may support your hardware more efficiently.

---

### Post by AnLGP on 2008-03-02
Nope that's not what I was saying but thank you for your response.  I will clear it up:

Which test should I get off of ultimatebootcd.com?

---

### Post by herbster on 2008-03-02
[http://www.ultimatebootcd.com/download.html](http://www.ultimatebootcd.com/download.html)

Get the ISO and burn it, then boot up into it.

---

### Post by ugm6hr on 2008-03-02
> **AnLGP said:**
> Which test should I get off of ultimatebootcd.com?

You have to burn the ISO as suggested.

Then use the HD diagnostic program that matches the manufacturer of your HD.  If you don't know who the manufacturer is, check in the computer's BIOS (or open the case and look).

---

