---
title: "PROBLEM BOOTING A TRIPLE BOOT WITH WINDOWS XP sp2,UBUNTU 7.04 &amp; FEDORA 7"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by arifiqbal7 on 2007-08-01
[B]Hi,
     Recently i had installed Fedora 7 on on my system. i had windows xp and ubuntu 7.04 already on my drive. I had added ubuntu to boot loader during installation of Fedora with mount point as /dev/hda8. But I was not able to boot ubuntu anymore. _[U]Anyone please guide me for i am totally new to  linux  and still have to go a long way._[/U]
     i searched all post on this forum and other forum for a suitable solution. i used my live Ubuntu cd to get  menu list from /boot/grub of Ubuntu and found out out these code [/B]

[HTML]title Ubuntu,kernel 2.6.20-15-generic
root (hd0,7)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=e0d2187f-55f5-48ca-8406-8ba5bca74547 ro quiet splash 
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title Ubuntu,kernel 2.6.20-15-generic(recovery mode)
root (hd0,7)
kernel /boot/vmlinuz-2.6.20-generic root=UUID=e0d2187f-55f5-48ca-8406-8ba5bca74547 ro single
initrd /boot/initrd.img-2.620-15-generic
         
title Ubuntu,memtest 86+
root (hd0,7)
kernel /boot/memtest86+.bin
quiet[/HTML]


[B]I tried to put these code on the grub.conf on fedora as I had read somewhere else but it said that 'permission denied' to view the file. I tried to do the same with menu.lst and got the same response.
However I tried to put these code with grubedit during booting process and the Ubuntu booted successfully. My problem is that these code are not saved after booting but grub reverts back to what was there before editing. When i try to reboot to Ubuntu,i have retype those code again. how can I save those code permanently?
[/B]


                            MY HDD configuration

/dev/hda1   windows xp                        FAT32         20GB
/dev/hda2   extended partition                                 50GB
/dev/hda3   fedora 7                             ext3             102MB
/dev/hda4   lvm for fedora                    LVM              20GB
/dev/hda5                                             NTFS            10GB
/dev/hda6                                             FAT32          10GB
/dev/hda7                                             SWAP           1GB
/dev/hda8   Ubuntu                              ext3              10GB

---

### Post by Tux Aubrey on 2007-08-01
You have just about solved this yourself!  menu.lst is a read only file so you need to open it as administrator (root priveleges)

Now that you know which version (Fedora's or Ubuntu's) is booting, you just need to open that version's menu.lst as admin and do the edits.

From a terminal in Ubuntu:
> 
gksu gedit

open the "correct" menu.lst, edit and save.

---

### Post by arifiqbal7 on 2007-08-02
Thanks a lot,it works with that.:)

---

### Post by Tux Aubrey on 2007-08-03
Just a postscript - while I remember it (and more for posterity than for the current OP):

When setting up a system with two or more Linux distros as alternatives, only one of the Grub installations is actually active - the last one you installed.  

This becomes an issue if there is a kernel update for the other distro/s because they will automatically trigger an edit to the wrong version of menu.lst (to add lines for the new kernel).  You will need to copy over the new entries to the active version after an update.

This confused the heck out of me for months.

In the OP's case (Fedora having been installed last), the new grub menu entries inserted after an Ubuntu kernel update will need to be copied to the version of menu.lst on the Fedora partition (in /boot/grub/).

---

### Post by phidia on 2007-08-03
I'm going to follow up on what you posted Tux Aubrey.
If you plan you can leave one grub on the mbr permanently and just install subsquent grubs to their respective root partition. All that needs to be done after that is editing menu.lst to chainload each distro from it's own grub. I don't multiboot a dozen distros anymore-i have three actually but the method I've outlined is what I use and it allows each distro to boot through it's own grub.

An example of that, in this case, would be during the fedora install to select "install grub bootloader to the root partition" 
After the install completes boot into the distro that still has grub installed to the mbr Again in this case ubuntu. Open an editor with root permission
i.e "sudo vim menu.lst" and add the necessary lines there e.g 
"title Fedora7"
"rootnoverify (hd?,?)" (the question marks need to get replaced by the actual values)
"chainloader +1"
Save changes and reboot.

---

### Post by flatwombat on 2007-08-03
Next time around with Fedora, leave Ubuntu as the bootloader in the mbr (check 'advanced' under bootloader for Fedora) and then add Fedora as:

title   Fedora
root (hdx,x)  < supply your hard drive and partition info here for Fedora)
rootnoverify (hdx,x)  <ditto
chainloader +1

That way, you'll still keep Ubuntu's menu but will pass the boot to the Fedora bootloader as soon as you select it.  Fedora in turn will automatically boot it's most recent kernel but still give you the option to boot other Fedora kernels.  Let's face it, Fedora goes through kernels like a kid goes through cheap sneakers and it's a pain to keep adding them to the Ubuntu menu.lst .  Better to let Fedora do it's thing on it's grub.conf and pass the boot to it.

Okay, another "short and simple" option:
title Fedora
configfile (hdx,x)/boot/grub/menu.lst

Also works, but avoids passing the boot to another grub menu, so you don't get to choose your kernel.  Simple, but hope you don't have a bad one!


(waymorethanyouneedtoknow)
One other 'tweak'.  If you have replaced an existing distro or version with a new one on Ubuntu, the UUID number will be affected for that menu.lst entry and it's going to bork Ubuntu's boot.  You'll find yourself looking at a text failure instead of your desktop.  Once the smoke clears, simply type "reboot" and you'll be back into the desktop, although not fully functioning, and can adjust Ubuntu's /boot/grub/menu.lst to remove the UUID and change /media to /dev and straighten things out. (/waymorethanyouneedtoknow)

---

