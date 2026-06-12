---
title: "Slow boot up."
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by netnut on 2006-09-22
Hi all,

Can anyone tell me why my Ubuntu 6.06 install is insanely slow to boot up? It takes in excess of 5 minutes to get to the welcome screen! When I had run it off the liveCD... it was zippy while its sluggish while running from the hard drive. Contradictory to what I expect.

Can anyone tell me what I'm doing wrong? My system specs are: Intel Pentium 4 2.8GHz, 512 MB RAM, 80 GB HDD, 512 MB swap file. Dual boot with WinXP.

Thanks in advance.

Netnut.

---

### Post by Brunellus on 2006-09-22
where does it seem to be hanging up?

---

### Post by netnut on 2006-09-23
The boot up process seems to get stuck on everything for a second at least! But it spends a lot of time "Preparing restricted drivers.." I bet it takes in excess of 4 minutes... and that is the  real problem. But I don't know what to do (and that's another problem altogether)

Netnut.

---

### Post by MWAAAHAAA on 2006-09-23
A look at the output from dmesg may be helpful. It may also be helpful to indicate exactly which points take so long.

On my computer it takes a lot of time (>1 min) to mount my disks (reiserfs) as I have a fairly large amount of disk space that I am using.

---

### Post by bri_06 on 2006-09-23
For me ubuntu is a bit slower at 'booting & shutting down' then XP.

- Celeron D 2.4GHz
- 1GB Ram
- 2x 30GB - ATA/133 - 7200RPM HDs
(one with XP installed, the other drive with ubuntu)

Don't know.. guess its normal. :|

---

### Post by netnut on 2006-09-23
Ok.. here is the output from dmesg file... hope you get a clue as to what is wrong. The text is a bit too long so I have saved it as a text file.

Thanks again.

Netnut.

---

### Post by guitarist549 on 2006-11-15
Mine is very slow as well. It seems to take the longest in loading GNOME, so is GNOME the problem? HEre are my specs:

Vaio VGN 2Z-240
1.6 MHZ Centrino Duo
Nvidia GeForce 7400
1 GB Ram

---

### Post by nickpaton on 2006-11-15
Looking at this line:

> [4294667.296000] Kernel command line: root=/dev/hda8 ro quiet splash

Can I suggest you modify grub/menu.lst file as follows:

```
gksudo gedit /boot/grub/menu.lst
```

scroll down to kernel section at bottom, and at most recent kernel at the top, against "kernel" add to line:

> noapic nolapic

so that section should now look similar to:

> title  		   Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		   /boot/vmlinuz-2.6.17-10-generic root=/dev/hdc2 ro quiet splash noapic nolapic
initrd		   /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
 

You may also want to add before noapic:

> vga=791

Which gives smaller text size as the PC is booting.

Note that each time a new kernel is added, you will need to do this.

I've done this to all my PC's and it speeds up booting and general performance.

---

### Post by guitarist549 on 2006-11-15
> **nickpaton said:**
> Looking at this line:



Can I suggest you modify grub/menu.lst file as follows:

```
gksudo gedit /boot/grub/menu.lst
```

scroll down to kernel section at bottom, and at most recent kernel at the top, against "kernel" add to line:



so that section should now look similar to:

 

You may also want to add before noapic:



Which gives smaller text size as the PC is booting.

Note that each time a new kernel is added, you will need to do this.

I've done this to all my PC's and it speeds up booting and general performance.

What exactly does this do? Does it turn off power management?

---

### Post by nickpaton on 2006-11-15
Thanks to T700 for this on post 2 of:

[http://ubuntuforums.org/showthread.php?t=228499]("http://ubuntuforums.org/showthread.php?t=228499")

> APIC stands for Advanced Programmable Interrupt Controller. It was a chip designed to use the timing circut from the computer's silicon quartz clock to coordinate multiple (up to 60, as I recall) processors. It never worked very well and many modern computers don't implement it, so it is not generally accessed by default in Linux.

I know that when installing Breezy and Dapper that many, many times, this had to be disabled to make the distro work properly.

For further information look at 

[http://en.wikipedia.org/wiki/Intel_APIC_Architecture]("http://en.wikipedia.org/wiki/Intel_APIC_Architecture")

Finally seaching "noapic" on the forum pulls up many useful posts.

---

### Post by guitarist549 on 2006-11-15
> **nickpaton said:**
> Thanks to T700 for this on post 2 of:

[http://ubuntuforums.org/showthread.php?t=228499]("http://ubuntuforums.org/showthread.php?t=228499")



I know that when installing Breezy and Dapper that many, many times, this had to be disabled to make the distro work properly.

For further information look at 

[http://en.wikipedia.org/wiki/Intel_APIC_Architecture]("http://en.wikipedia.org/wiki/Intel_APIC_Architecture")

Finally seaching "noapic" on the forum pulls up many useful posts.

Ok,thanks... will do. What do you think would cause GNOME to have a huge delay after logging in?

---

### Post by nickpaton on 2006-11-15
> **guitarist549 said:**
> Ok,thanks... will do. What do you think would cause GNOME to have a huge delay after logging in?

In all honesty no.

If the noapic suggestion doesn't work, can I suggest that you post dmesg file as well and that should help find out.

---

