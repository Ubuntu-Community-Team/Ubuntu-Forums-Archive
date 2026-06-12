---
title: "Dual-booting + GRUB"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2007-02-05
I've got Ubuntu Dapper with GRUB working on it now (thanks to those who helped!), and I just partitioned 5 GB for Linux XP, which I just installed.

Anyone know how to add Linux XP to the GRUB menu.list?

```
fdisk -l

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6591    52942176   83  Linux
/dev/sda2            7114        7297     1477980    5  Extended
/dev/sda3            6592        7113     4192965   83  Linux
/dev/sda5            7114        7297     1477948+  82  Linux swap / Solaris

```

Also, does anyone have a Linux XP activation code I can have? :lolflag:


:D Thanks

---

### Post by kebes on 2007-02-05
Edit /boot/grub/menu.lst

You should see entries like:
```

title           Ubuntu, kernel 2.6.15-27-k7
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-k7 root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-k7
savedefault
boot

```

You'll need to add another section like that to the list. Just update the (hd0,0) to point to the correct partition on your hard-drive, and make sure that you update the other lines to point to valid kernels.

However normally when you install any version of Linux, the grub installer will create a new "menu.lst" and add any detected Linux partitions to the list. That didn't happen this time?

---

### Post by kbsuperstar on 2007-02-05
Linux XP, not Windows XP ...

But I'll see if it helps. Thanks :D

EDIT:

So what do I put to boot sda3 (Linux XP) instead of (hd0,0) ?

---

### Post by kebes on 2007-02-05
> **kbsuperstar said:**
> Linux XP, not Windows XP ...

So what do I put to boot sda3 (Linux XP) instead of (hd0,0) ?


Sorry I read your original post too fast! (See my newly edited reply...)

sda3 corresponds to (hd0,2) in grub naming scheme:
[http://www.gnu.org/software/grub/manual/grub.html#Device-syntax](http://www.gnu.org/software/grub/manual/grub.html#Device-syntax)

Note that grub calls all hard-drives "hd" (even SATA ones), and it starts counting from zero. Hence the first hard drive is hd0, and the 3rd partition is 2.


Hope that helps.

---

### Post by kbsuperstar on 2007-02-05
Yeah, it does help, thanks!

But I'm still a little confused.

I still don't know exactly what to put in the file. This GRUB manual is pretty confusing to me.

---

### Post by kebes on 2007-02-05
So, in more detail, open your "/boot/grub/menu.lst" in a text editor.

Towards the bottom you should find a list of grub menu entries. They will look like:
```

title           Ubuntu, kernel 2.6.15-27-k7
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-k7 root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-k7
savedefault
boot

```

Copy one of those and paste it at the end of the file. Then update it with the following changes:

1. Change the "title" line to whatever you want, like "Linux XP"

2. Change "root (hd0,0)" to "root (hd0,2)"

3. Change the kernel line to whatever your kernel actually is! You should look at the "/boot/" directory on your Linux XP install, and see what the kernel is called. Update "root=/dev/sda1" to be "root=/dev/sda3" also.

4. Same thing for the initrd line. Go see what images exist.




You can post your menu.lst here if you want more specific help.

Another option would be to run the program "grub-install" from a LiveCD session, which should do all of this automatically, detecting bootable partitions and adding them to the list. (As I said, I'm a little surprised that this wasn't done automatically during the Linux XP install...)

P.S.: I agree, the grub manual is *very* confusing!

---

### Post by kbsuperstar on 2007-02-05
K, thanks! I'll see if I can find the menu.list from Linux XP. 

Where can I get the GRUB-install Live CD from?

---

### Post by kbsuperstar on 2007-02-05
Well, I'm unable to mount the partition that's dedicated to Linux XP, so, I guess I need that GRUB-install Live CD :D

EDIT:

Hmm... I can't find a GRUB live CD online... can I get some more help :)?

---

### Post by kebes on 2007-02-05
> **kbsuperstar said:**
> K, thanks! I'll see if I can find the menu.list from Linux XP. 

Where can I get the GRUB-install Live CD from?

The standard Ubuntu install-CD/LiveCD has grub and grub-install available on it. ([System Rescue CD]("http://www.sysresccd.org/Main_Page") does, too.) So boot up a Ubuntu CD, but don't activate the installer. Instead go to a console and try running "grub" or "grub-install". You will probably have to issue a command like:

grub-install /dev/sda

Note that this is "/dev/sda" and not "/dev/sda1" or "/dev/sda3" ... it means "install grub to the master boot record of hard drive "/dev/sda".

I think issuing this command will generate automatic entries for any bootable unix partitions.

---

### Post by kbsuperstar on 2007-02-05
Thanks, again! I'll try it and re-post the results.

---

### Post by kebes on 2007-02-05
Note that grub-install can be tricky to use... it's probably 'safer' to just edit the menu.lst file.

What was the problem with mounting your Linux XP partition?

---

### Post by kbsuperstar on 2007-02-05
Yeah, grub-install didn't work. I kept getting errors like "Couldn't find device with /boot" or something.

When I try opening/mounting my Ubuntu partition and my Linux XP partition it just says that they're unmountable...

```
error: device /dev/sda3 is not removable

error: could not execute pmount
```

*sigh* Any suggestions on how to get around this?

---

### Post by bodhi.zazen on 2007-02-05
Easiest way is with chainloader ...

Boot the Ubuntu CD

Open a terminal

enter ```
sudo grub
```

Now at the grub prompt:

root (hd0,0)
setup (hd0)

root (hd0,2)
setup (hd0,2)

quit

reboot.

If that does not work, or if you like, set up Linux XP with chaninloader (this was the reason to setup (hd0,2) ).

Boot Ubuntu from HD.

In a terminal: ```
gksudo /boot/grub/menu.lst
```

Use this entry for Linux XP:

> title Linux XP
root (hd0,2)
savedefault
chainloader +1
boot

You will get 2 grub screens ....

If that works, boot Linux XP, now open /boot/grub/menu.lst (on the Linux XP partition)

Edit these lines to:> timeout 0
defalut 0

Now you will boot directly to Linux XP when you select the menu (no double grub screen)

The advantage of this is you will not need to manually maintain menu.lst when you update the Linux XP kernel.

You can also see here: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

And you can also look at the supergrub disk  

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by kbsuperstar on 2007-02-05
Ha, k, neither of those worked.

The chainloader command thing just sent me into a GRUB bash menu...


So, I think i'll just delete and re-install Linux XP, hmmm...

---

### Post by bodhi.zazen on 2007-02-05
You know, now that you mention it, the line may be just chainloader without the +1 :p

Also, good to see you are learning a little about GRUB ....

---

### Post by confused57 on 2007-02-05
> **bodhi.zazen said:**
> You know, now that you mention it, the line may be just chainloader without the +1 :p

Also, good to see you are learning a little about GRUB ....

Your instructions were excellent, I always use the following to chainload:

title   Linux XP
rootnoverify (hd0,2)
chainloader +1

The only time I received just a grub prompt was when I installed Sabayon and opted not to install grub at all(used Ubuntu's live cd to install grub to the Sabayon root partition)...ended up having to boot up the Sabayon live cd & selecting rescue system, then installing grub to the root partition.

---

### Post by kbsuperstar on 2007-02-06
Ok, now my GRUB is totally screwed up. I installed Linux XP and allowed it to install GRUB on the MBR; after checking out Linux XP for about 5 min, I realized that it totally sucked, ha. So, I deleted the Linux XP partition and resized the Ubuntu partition to my entire HD (via GParted live CD). After rebooting, GRUB loaded, but after the load time it just sent me to the GRUB bash command line.

This was frustrating... I booted into Ubuntu Live CD and tried the following

```
sudo su -
grub
find /boot/grub/stage1
root (hd0,0)
setup (hd0,0)
```

2 of the 5(or 6?) results failed. I tried rebooting, but same thing happened.

I tried Ubuntu Live CD again, and this:

```
sudo su -
grub-install /dev/sda
grub-install /dev/sda1

```

But it just said that the device wasn't mountable/removable

I tried manually mounting/accessing the ubuntu HD partition in the Live CD, but it just said:

> Device not removable
Couldn't execute pmount

So, I ended up re-partitioning 10 GB and installed Fedora Core 5, just so I could have a bootloader.

Now I can boot into FC5, but I haven't edited the menu.lst to add Ubuntu to GRUB.

I want to just trash FC5 .... so how do I get GRUB fixed back onto Ubuntu???

*sigh*

---

### Post by confused57 on 2007-02-06
You could boot up the live cd, open a terminal, enter:
```
sudo grub
find /boot/grub/stage1
root (hd0,0)
setup (hd0)
quit
```

see this thread:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

this should install Ubuntu's grub(if Ubuntu is on the first paritition) to the mbr... you'll probably have 2 instances of grub?...since you installed grub to (hd0,0), I'm not sure.

---

### Post by kbsuperstar on 2007-02-06
I already tried that :(

I'll try again, though

---

### Post by bodhi.zazen on 2007-02-06
> **kbsuperstar said:**
> Ok, now my GRUB is totally screwed up. I installed Linux XP and allowed it to install GRUB on the MBR; after checking out Linux XP for about 5 min, I realized that it totally sucked, ha. So, I deleted the Linux XP partition and resized the Ubuntu partition to my entire HD (via GParted live CD). After rebooting, GRUB loaded, but after the load time it just sent me to the GRUB bash command line.

This was frustrating... I booted into Ubuntu Live CD and tried the following

```
sudo su -
grub
find /boot/grub/stage1
root (hd0,0)
setup (hd0,0)
```

2 of the 5(or 6?) results failed. I tried rebooting, but same thing happened.

I tried Ubuntu Live CD again, and this:

```
sudo su -
grub-install /dev/sda
grub-install /dev/sda1

```

But it just said that the device wasn't mountable/removable

I tried manually mounting/accessing the ubuntu HD partition in the Live CD, but it just said:



So, I ended up re-partitioning 10 GB and installed Fedora Core 5, just so I could have a bootloader.

Now I can boot into FC5, but I haven't edited the menu.lst to add Ubuntu to GRUB.

I want to just trash FC5 .... so how do I get GRUB fixed back onto Ubuntu???

*sigh*

To be honest, grub is not this difficult. I would advise you do some reading :p


[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

You may also look at supergrub:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)



confused57 gave you the current solution.

Your "problem" is you deleted the Linux XP partition, which was referenced but your MBR. Next issue is setup (hd0,0) installs grub to the first partition while setup (hd0) installs to the MBR.

You need to understand the difference between installing grub into the MBR vs the root partition.

If you install grub into the root partition you can then chainload from a boot partition to the root partition.

If you do not chainload, you will need to edit/update menu.lst

Your boot partition is the one indicate when you install grub:

root (hdx,y)

The boot partition can be a root partition, for example your Linux XP or Ubuntu root partition in which case the path will be /boot/grub/menu.lst

You must re-configure grub if you delete your boot partition.

If this makes sense, good. If not read and ask if you have questions.

---

### Post by kbsuperstar on 2007-02-06
Wow, I feel stupid :P I figured out that when I was typing the "setup" command, I would type ```
 setup (hd0,0)
``` instead of ```
setup (hd0)
```

Ha! Well thanks for all the help, guys! I really appreciate it :D

---

### Post by bodhi.zazen on 2007-02-06
:idea:

---

