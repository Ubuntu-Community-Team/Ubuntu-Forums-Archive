---
title: "Installing Ubuntu on partition of main HD"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by Man In Black on 2007-02-22
When I did a fresh install of Windows XP on my 320GB hard drive recently, I installed Windows on a 80Gb partition, made a 13GB linux partition for playing around with Linux on, and made the rest as storage for files.

I want to install Ubuntu on that 13GB partition without disturbing my files or my Windows install...I tried to install, but I got to the partitioning section, selected the partition to install in, and then the next screen...I wasn't sure what was going on. I dont want to mess up my main Windows install or anything. How do I do this.

Thanks

---

### Post by madsporkmurderer on 2007-02-22
When you are asked where to install, choose custom. Then, assuming it is all partitioned already continue through the partitioning bit, although you will want to remember(or write down) the device names(hda1 etc.) and which partitions they refer to.

Next you should be presented with a series of dropdown boxes relating to devices and mount points; firstly select the partition you want to install ubuntu on and set its mount point to / .
That is the important bit, but you will probably also want to select the windows partition to be mounted somewhere like /media/windows and the other partition as /media/bigpartition but that is not strictly nessicary at this stage.

I think I've answered your question but feel free to ask for clarification or if I've totally missed the point.

---

### Post by ukimo on 2007-02-22
[SIZE="2"][FONT="Arial Black"][/FONT][/SIZE]
I am in the same boat. Have not installed ubuntu yet - just running from cd. I have XP on C:\ @ 12.6 gig (almost out of space). A new 200 gig HD as D: through L: (various sizes ~ 15 - 20 gig). Would like to install Ubuntu on D: as a dual boot but am unsure how this reformats the drive. I have backups (.iso) of XP on the drive (K, L) and don't want these erased in the format. If I install do the D drive will Ubuntu just format and partition only this drive without overwriting anything else? I don't mind screwing up but do NOT want to have to re-install XP if I can help it. How can I just re-partition D: to have the root and swap drive contained in D:?

---

### Post by Man In Black on 2007-02-22
Kay, heres where I'm getting confused.

I have two HD's btw, a 320GB main HD, with Windows XP on it, and a 80GB slave for backups.

Anyway..

I come to this screen, and select the option you see there
[IMG]http://img.photobucket.com/albums/v605/atticwindow/1.jpg[/IMG]

I get the next screen and select the selected option

[IMG]http://img.photobucket.com/albums/v605/atticwindow/2-1.jpg[/IMG]

Then the next one, and I select the 13GB partition

[IMG]http://img.photobucket.com/albums/v605/atticwindow/3.jpg[/IMG]

And, then on the next screen, im completely lost.

[IMG]http://img.photobucket.com/albums/v605/atticwindow/4.jpg[/IMG]

Thanks

---

### Post by rusty4r on 2007-02-22
first thing I noticed is you only made one partition for Linux. you'll also need a second partition for swap ( 2 x ram, 1Gig Max. ) So go back to that page and resize the linux just a little and make a second partition of "swap" this should leave you with 12.08 Gig for "/". Read the bottom of step 5 "Preparing Partitions". That's what those instructions are refering to.

Hope that helps

---

### Post by Man In Black on 2007-02-22
Im not sure what to do on that last screen though....

---

### Post by tonyr1988 on 2007-02-23
First, have you gotten a swap partition set up? I doesn't have to be huge, but you've got to have something (generally speaking, the larger swap, the better performance). I'm assuming you've got it set up like this:

/dev/sda1 NTFS
/dev/sda2 NTFS
/dev/sda3 ext2
/dev/sda4 swap

When you get to the last screen, to identify the partitions, look at the drop-down boxes (don't click them...there's no need to change any of the drop-down boxes) and see the very last thing (such as [sda3], [sdb1], etc.).

The [sdb1], [sdb2], and [sdb3] belong to your second hard drive - ignore those and make sure the "reformat" box is *unchecked*.

The [sda1] and [sda2] are your NTFS partitions - also make sure they are unchecked. You don't wanna mess with those (make sure you backup important data, just in case).

For [sda3], the Mount Point should say / - if it doesn't, pick it from the first drop-down box.

For [sda4], I honestly don't remember what is says. It should be "swap space" or a "swap partition." It may have a "swap" option in the Mount Point drop-down box. Sorry I can't be much of a help on exactly what it says.

If you're worried about doing things correctly, re-post those last two screens and we can make sure everything is set up alright before you click "Next."

---

### Post by Man In Black on 2007-02-23
Thanks for the help guys. I got it successfully installed. Breezy Badger was the last version I used, theyve made a lot of improvements, at least visually, since then, hehe.

A question, how do I select a certain OS to boot automatically? Right now I get a screen at boot with a list of 3 Ubuntu boot options, Windows XP, a windows troubleshooting partition, etc. How do I make it so Windows boots by default unless I say otherwise?

Also, whats the difference in Ubuntu and Kubuntu?

Thanks!

---

### Post by Man In Black on 2007-02-23
Oh, and how do I turn off anti-aliasing on the fonts? Im using a analog monitor, and the fonts look fuzzy and make me strain my eyes.

---

### Post by chewearn on 2007-02-23
> A question, how do I select a certain OS to boot automatically? Right now I get a screen at boot with a list of 3 Ubuntu boot options, Windows XP, a windows troubleshooting partition, etc. How do I make it so Windows boots by default unless I say otherwise?

$ sudo gedit /boot/grub/menu.lst

At the bottom of the file, you should see the list of boot menu items.  Don't change anything here, just take note of the order for the Windows XP (probably the second item?)

Near the top of the file, you should see:
> default		0

Which means the first item is default.  Change the number to 1 (if Windows Xp is the second item).

---

### Post by Man In Black on 2007-02-25
Um, heres what I see at the end

> ## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Windows NT/2000/XP (loader)
root		(hd1,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


---

### Post by chewearn on 2007-02-25
Ok, I saw entries 4 and 5 are for XP, that means you need to set the default parameter to either 3 or 4.

For the "Microsoft Windows XP Home Edition" entry:
```
default 3
```

or the "Windows NT/2000/XP (loader)" entry:
```
default 4
```

---

### Post by Man In Black on 2007-02-25
Ah, nevermind...I changed default to "4" and everythings cool. Thanks for the advice.

So whats the diff between ubuntu and kubunto? Just that one has Gnome and the other KDE?

EDIT:OOp, posted at the same time. I used 4 because using 3 made "Other Operating Systems" be defaulyt at boot.

---

### Post by steve.horsley on 2007-02-25
I it were me, I would have moved the Windows stanza to above the "automagic" section so it was the first entry, and left the default at 0. Still, now it's done, if it ain't broke don't fix it. 

Yes, the difference is Ubuntu uses Gnome, Kubuntu uses KDE and Xubuntu uses XFCE. Once one is installed, you can install the other desktops too - it's really a question of which is installed by default.

---

### Post by ukimo on 2007-03-24
I still haven't installed yet but am keeping a copy of this thread til I get home next month and do it. Am sure it will help alot! Thanks! :)

---

### Post by ukimo on 2007-12-18
I have another question for you gurus out there...

Some one hijacked my copy of Ubuntu 6.1...! I now have a copy of 7.1.
Here's what I have set up.

c:\ 12.6 gig HD loaded with a working copy of XP (FAT 32). maxxed out with not much room left.

D:\ 210 gig HD formatted/partitioned off as D:\ (FAT 32) through L:\  (various sizes -  some NTFS)

problems:
D:\ was not formatted as a boot HD but can be erased.
Can D: be reformatted as a boot drive without wiping out the other partitions on this drive?

CD burner does NOT burn without errors so can't use for backup or storage. (need new one)
Need another new large HD too...

Here's what I would like to do.
If D: can be reformatted as a boot drive without screwing with the rest I can install XP on it and wipe clean the 12.6g HD and install Ubuntu to it. Will have to re-partition it off 

Another question: If I install ubuntu to this drive (Pentium III machine), remove HD and re-install it on a 486-33 (32 bit) (using all the limitations of the size of the HD, etc) will it still work (after changing the video driver, etc..? OR should I just reformat, move to other 'puter, then install?

ANY help or suggestions would be appreciated...

---

