---
title: "Triple booting - adding slack to xp/ubuntu dual boot"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by sbooth on 2006-09-18
I'm not a total newbie but I've still got lots to learn - and I want to play with other distros in the process.

I currently have a dual boot xp/ubuntu desktop machine with one SATA drive; current partition info:

sda1   82 Gb     HPFS/NTFS (XP Pro) <-- Boot flag on
sda2   19.5 Gb   Ubuntu Linux /
sda4 - extended partition
sda5   19.5 Gb   Ubuntu Linux /home
sda6   1.5 Gb    /swap
sda7   85 Gb     FAT32 (XP/Linux shared 'data' drive)
sda8   36.7 Gb   <-- currently ext3 formatted empty space

My immediate plan is to install slackware in the empty space/sda8 - but I'm not sure that it's all I want to do - I might want to play with another distro as well.  I use Ubuntu most of the time, have some (minor) irritations with it... I use XP when I want to do particular tasks (Photoshop, DVD copying) with particular software that I like.  Probably 98% of the time booted into Ubuntu.

Questions:

Given that a slackware install is mainly for me to learn linux stuff, how much space should I give it?

I know I can re-use the /swap partition, how should I divide up the 36.7 Gb space I have for installing slack and possibly another distro to play with?  (My current thoughts are to have root and home on separate partitions... should I consider more separate partitions?)

How do I deal with Grub?  Do I install slackware with its Lilo bootloader in its root partition and edit Grub... or with no bootloader and edit Grub?

I don't want to go blading in and risk messing up my carefully set up Ubuntu install! It's a happy machine at the moment - but it's also the only one I have space on to play with another distro!

Any advice and suggestions would be very welcome.  I've done lots of googling and searched here - and have seen situations that seem similar but none quite the same... adding slack to an Ubuntu/XP dual boot.

If there is a thread I haven't spotted, please do point me in the right direction.

Many thanks in advance

Sarah

---

### Post by bodhi.zazen on 2006-09-18
> Given that a slackware install is mainly for me to learn linux stuff, how much space should I give it?

Break sda8 into 3-10 GB partitions. You can go as small as 5 GB/OS. If you find one you like, give it room.

> How do I deal with Grub? Do I install slackware with its Lilo bootloader in its root partition and edit Grub... or with no bootloader and edit Grub?

No problem. Install you rnew OS, when it gets to install of GRUB/LILO install into / (root partition) [color=red]NOT THE MBR[/color].

Then add a grub entry (even if you just installed LILO) in the /ubuntu_root/boot/grub/menu.lst.

If you overwrite your MBR restore is with your /ubuntu_root_partition as your GRUB root partition.

> I don't want to go blading in and risk messing up my carefully set up Ubuntu install! It's a happy machine at the moment - but it's also the only one I have space on to play with another distro!

Should not be a problem.

> 
Any advice and suggestions would be very welcome. I've done lots of googling and searched here - and have seen situations that seem similar but none quite the same... adding slack to an Ubuntu/XP dual boot.

Go for something new. In place of Slax I advise you start with Zenwalk. Try Fedora core/BLAGG. SUSE is also nice.

My favorite is Arch. It will take some reading to install, but beyond the install it is very easy to sys admin.

[[color=red]Check out Distrowatch[/color]](http://distrowatch.com/)

---

### Post by sbooth on 2006-09-19
Thank you ever so much :-)  That's *exactly* the help I was hoping for!

---

### Post by pvlbill on 2007-01-23
> **bodhi.zazen said:**
> Break sda8 into 3-10 GB partitions. You can go as small as 5 GB/OS. If you find one you like, give it room.



No problem. Install you rnew OS, when it gets to install of GRUB/LILO install into / (root partition) [color=red]NOT THE MBR[/color].

Then add a grub entry (even if you just installed LILO) in the /ubuntu_root/boot/grub/menu.lst.

If you overwrite your MBR restore is with your /ubuntu_root_partition as your GRUB root partition.



Should not be a problem.



Go for something new. In place of Slax I advise you start with Zenwalk. Try Fedora core/BLAGG. SUSE is also nice.

My favorite is Arch. It will take some reading to install, but beyond the install it is very easy to sys admin.

[[color=red]Check out Distrowatch[/color]](http://distrowatch.com/)

Hi, pvlbill here, a relative newcomer to the posting process.

I am currently dual booting Windows Me & ubuntu 6.06 LTS. Would like to add Suse linux
 10.2 to the mix and triple boot. 

I can fathom GRUB being placed in /root partition and not MBR, however, I am confused by the rest of the instruction.

Would it be possible for bodhi.zazen to explain his last two sentences ("Then add a grub entry (even if you just installed LILO) in the /ubuntu_root/boot/grub/menu.lst.

If you overwrite your MBR restore is with your /ubuntu_root_partition as your GRUB root partition.")

Thanks for any help, I enjoy checking your replies to other posts.

pvlbill

---

### Post by bodhi.zazen on 2007-01-23
> **pvlbill said:**
> Hi, pvlbill here, a relative newcomer to the posting process.

I am currently dual booting Windows Me & ubuntu 6.06 LTS. Would like to add Suse linux
 10.2 to the mix and triple boot. 

I can fathom GRUB being placed in /root partition and not MBR, however, I am confused by the rest of the instruction.

Sorry, grub speak is cryptic :)

> Would it be possible for bodhi.zazen to explain his last two sentences ("Then add a grub entry (even if you just installed LILO) in the /ubuntu_root/boot/grub/menu.lst.

If you overwrite your MBR restore is with your /ubuntu_root_partition as your GRUB root partition.")

OK, see if this helps

The confusing vaible in your case is your partitioning table.

Lest assume:

/dev/hda1 = windows = ntfs = grub (hd0,0)
/dev/hda2 = swap
/dev/hda3  = extended partition (so we can have more then 4)

/dev/hda5 = ubuntu_root_partition = grub (hd0,4)
/dev/hda6 = suse_root_partition = grub (hd0,5)

Now, before you install suse, the MBR boots to /dev/hda5

So install suse, and when it comes to installing grub, install to /dev/hda6 rather then the MBR.

But we need to be able to boot suse. So we need to mount and edit /boot/grub/menu.lst on /dev/hda5

Open /boot/grub/menu.lst on /dev/hda5 and add:

> title SUSE
root (hd0,5)
kernel /boot/vmlinux-xyz root=/dev/hda6 ro quiet splash
initrd /boot/initrd-xyz.img
boot

You will need to look at the suse root partition, /dev/hda6 in /boot for information on the exact numbers for vmlinuz and initrd.

Or you can chainload:

> title SUSE
root (hd0,5)
chainloader +1
boot

As long as grub is installed on the suse root (/dev/hda6)

> If you overwrite your MBR restore is with your /ubuntu_root_partition as your GRUB root partition.

If when installing Slackware, LILO is installed to the MBR and you want to use grub, you need to:

```
sudo grub
root (hd0,4) # this is the ubuntu_root_partition
setup (hd0)
quit
```

> Thanks for any help, I enjoy checking your replies to other posts.

pvlbill

Clear as mud ?

See if this helps: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

