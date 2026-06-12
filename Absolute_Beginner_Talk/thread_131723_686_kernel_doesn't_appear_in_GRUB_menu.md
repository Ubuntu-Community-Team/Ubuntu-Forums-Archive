---
title: "686 kernel doesn't appear in GRUB menu"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by johnraff on 2006-02-17
On a partition with Gnome, I've just installed the Linux-686 kernel package via synaptic, rebooted, but the new kernel doesn't appear in the GRUB menu. 

The 386 I had already got upgraded at the same time and the new 386 version shows up OK.
Synaptic shows 686 as installed, I tried reinstalling it but it's still not in GRUB, so I can't use it.

On a different partition (with Xubuntu-desktop) 686 got installed and shows on GRUB no problems.

Does anyone have any suggestions?

---

### Post by kenweill on 2006-02-17
Manually edit your GRUB.

sudo gedit /boot/grub/menu.lst

Then add this lines:
Under ## ## End Default Options ##

> 
title		Ubuntu, kernel 2.6.12-10-686 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-686
savedefault
boot


Watch out for your kernel version. Replace the numbers with your kernel version.

---

### Post by johnraff on 2006-02-18
It gets wierder.
/boot/grub/menu.lst already contains the 686 kernel.
What I have in detail is two partitions, Xubuntu on hda3 and Ubuntu on hda1.
(just for testing out later I'll cut down to one)
For some reason Grub takes the hda3 partition as the default one.

The Grub menu I get on bootup looks like this:
-----------------------------------------
```

Ubuntu, kernel 2.6.12-10-686      [this is Xubuntu on hda3, and OK]
  "           "             "            (recovery mode)
  "           "   2.6.12-10-386
  "           "            "             (recovery mode)
Ubuntu, memtest 86+
other operating systems:
Ubuntu kernel 2.6.12-10-386(on /dev/hda1)  [this is my Ubuntu setup]
  "          "            "            (recovery mode) (on /dev/hda1)
  "          "   2.6.12-9-386 (on /dev/hda1)
  "          "            "           (recovery mode) (on /dev/hda1)
memtest 86+ (on...)

```
----------------------------------------
But the menu.lst file showed 686 installed and NO 2.6.12-9-386 kernel!
I thought I'd left that in when I upgraded to 10-386 but checked Synaptic and it wasn't there, so I installed it to see if it helped...
Now the menu.lst file shows all three kernels:10-686, 10-386 and 9-386.
uname -a in a terminal said I was running 386 as per Grub login...
Reboot and Grub's login menu still only shows 10-386 and 9-386, no sign of 10-686...
It looks as if Grub is getting its login menu from somewhere other than /boot/grub/menu.lst ?

---

### Post by David Corrales on 2006-02-18
Might want to try running: **sudo update-grub**

---

### Post by kenweill on 2006-02-18
I forgot, it was my mistake.
The "savedefault" line should only exist once. Remove that line from the other option.

And make sure that you edit the file with the sudo command. Otherwise, it will not be saved or updated once you exit.

Hope this helps.

---

### Post by johnraff on 2006-02-18
I've just realized- there are *two* /boot/grub/menu.lst files, one in the hda1 partition, and one in hda3.
The hda3 went in later and so seems to have been made the "default", so the Grub boot screen seems to be based on that menu.lst .

I copied the entry for the new kernel from the file in hda1 and pasted it into the menu.lst in hda3 and - wow - there's my new kernel in the boot menu!
Booted into it and "uname -a" confirmed that I'm now running the 686 kernel.

But I had to do all this manually. There's no way for the two /boot/grub/menu.lst files to update each other automatically I suppose?

---

