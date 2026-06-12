---
title: "Create a custom Mactel kernel?"
date: 2008-12-01
forum: Apple Hardware Users
---

### Post by Rog-Mahal on 2008-12-01
I think I'd like to try my hand with making a pared down Macbook-centered kernel. I've compiled kernels before, but I'm looking to really just keep the modules and options necessary for macbook functionality. So I have a few questions:

First of all, is this a worthwhile pursuit? The last kernel I compiled was 2.6.25 I think in order to gain some speed improvements and there was some new powersaving option that finally became available for 64 bit.

Second, what should I keep and what can I toss on the kernel options front? I want to keep the functionality of all my devices (wifi, bluetooth, isight etc.) and allow for as many powersaving options as possible. 

Any advice/ input is welcome. I've only done this once before.

---

### Post by user12021 on 2008-12-01
I'd be very interested in this. I have the same macbook as you, so I'd like to know what options you use.

---

### Post by volanin on 2008-12-01
When building your own customized kernel, you have to consider mainly three
things: the kernel core components, the hardware support and the software
support.

What I mean by kernel core components are the essential pieces to make your
kernel work, like the I/O scheduler and multiple cpu cores support. These
parts are known as kernel-land and their workings are usually not directly
visible to the users.

Hardware support is quite obvious, of course!

And software support corresponds to the infra-structure to allow certain
user-land programs to work. For example the IPCONFIG tables for firewalls,
and even the types of filesystems that you will use.


I have the same macbook as you do, and I have build my kernel with this
design in mind: support every piece of hardware, but only the essential
software parts and filesystems that I really use, and the essential
core components that I care for.

It's built mostly static, with only ath9k and iSight being built as
modules, so that I can disable them for powersaving when necessary.
For comparison, my macbook consumes 19.5W with ath9k, iSight and
full brightness when idle, but only 11.9W with these modules
unloaded and minimum brightness.


Check it out, and modify it according to your desired design!
One thing you will immediately want to change are the CPU governors.
I just enabled the performance governor, so you may wat to include ondemand as well.

Copy the isight.fw file into the kernel-tree firmware folder before compiling!
It will be compiled into the kernel.
Enjoy!
:)

---

### Post by cyberdork33 on 2008-12-01
yep, I'd say the safest way to proceed is to just try compiling a kernel that you have eliminated hardware support for items that are not on your machine. This could take a few iterations if you are not familiar with this. Some of the easy items are disabling any AMD hardware items since you have an Intel machine. Much of the other hardware items are Intel as well (sound, SATA controller, etc) and you can eliminate driver for other wifi cards.

Once you get an idea of what you have and do not have and what to enable, you can experiment with disabling the software items that you think you will not need and tweak some of the basic kernel functions to try and gain speed / stability (depending on your goal).

---

### Post by led_scorched on 2008-12-02
I have been looking for a distro built for the macbook, and am shocked to not find anything.  I would love this!

---

### Post by Rog-Mahal on 2008-12-02
Great! Thanks for the advice, I'll start experimenting right away.

Volanin: Does your config.gz include functionality for bluetooth and anything I would need for internet connectivity? Also, how does your kernel compare vs. the generic version?

Will I need to add any mactel patches? Should I use the Ubuntu kernel or download a vanilla from kernel.org?

---

### Post by volanin on 2008-12-03
> **Rog-Mahal said:**
> Great! Thanks for the advice, I'll start experimenting right away.

Volanin: Does your config.gz include functionality for bluetooth and anything I would need for internet connectivity? Also, how does your kernel compare vs. the generic version?

Will I need to add any mactel patches? Should I use the Ubuntu kernel or download a vanilla from kernel.org?

Yes, it has full functionality for everything, except firewall.
What it purposefully lacks is:

- No IPTables at all (for firewall).
- Only EXT2/3, FAT/NTFS, HFS+ and CDROM filesystems supported.
- Only the performance CPU governor is supported.
- All non-macbook stuff is deselected.
- Experimental stuff is deselected.

It's the configuration for the current Ubuntu kernel.
No mactel patches necessary.

Install it with **$ sudo aptitude install linux-source**
The tar.bz2 kernel source will be installed in /usr/src

Uncompress the kernel source anywhere.
Uncompress the config.gz to a file called .config in the kernel tree.
Copy the firmware isight.fw to the firmware folder in the kernel tree.
Compile away!
:)

---

### Post by Rog-Mahal on 2008-12-03
Great! One last question: Since I have rEFIt installed and therefore grub loads in stage2, if for some reason I do have a problem and need to go back to a standard kernel where do I get to something like a grub menu?

---

### Post by volanin on 2008-12-03
> **Rog-Mahal said:**
> Great! One last question: Since I have rEFIt installed and therefore grub loads in stage2, if for some reason I do have a problem and need to go back to a standard kernel where do I get to something like a grub menu?

GRUB loads directly to stage 2?
That's new for me!

Here I installed GRUB in the root partition instead of the MBR.
REFIT detects it and boots to GRUB stage 1.
Then GRUB stage 1 calls GRUB stage 2.

How did you manage to call stage 2 directly?
:)

---

### Post by cyberdork33 on 2008-12-03
yea that is a new one for me too. rEFIt should only be able to boot stage1. Maybe you have the timeout set to zero in your grub config?

---

### Post by user12021 on 2008-12-03
What kind of speed increase would I see if I used a custom kernel?
Would it be noticeable at all?

---

### Post by pxwpxw on 2008-12-03
> **Rog-Mahal said:**
> Great! One last question: Since I have rEFIt installed and therefore grub loads in stage2, if for some reason I do have a problem and need to go back to a standard kernel where do I get to something like a grub menu?

There is a 'hiddenmenu" option in menu.lst might be the cuprit.

---

### Post by volanin on 2008-12-04
That really might be his situation.
In my case for example, I have in my menu.lst:

```
default		0
timeout		0
hiddenmenu
```

So GRUB boots directly without waiting.
But I still can access the menu by holding ESC after REFIT.


> What kind of speed increase would I see if I used a custom kernel?
Would it be noticeable at all?

Honestly, no noticeable speed increase at all.
The Ubuntu kernel is already pretty good.
:)

---

### Post by pxwpxw on 2008-12-04
I would  like to know how to reconfigure an amd64 kernel to be compatible with grub.efi booting which works very well for i386. I will try a few changes to BIOS switches, noting that the i386 config which works, has differences. May not be that of course.
Kernel and initramfs load ok, then the thing dies before any logs or any keyboard, so no clues.
Well except ata5 timeout repeating and root device not found.

---

### Post by cyberdork33 on 2008-12-04
> **volanin said:**
> That really might be his situation.
In my case for example, I have in my menu.lst:

```
default		0
timeout		0
hiddenmenu
```

So GRUB boots directly without waiting.
But I still can access the menu by holding ESC after REFIT.It's like Windows! (except it uses F8 )

The hiddenmenu option will still show a message about hitting Esc to see the menu for a few seconds in the timeout is greater than 0.

> Honestly, no noticeable speed increase at all.
The Ubuntu kernel is already pretty good.
:)
Yea, I just use the generic kernel now. If you really want to compile one, just compile the Ubuntu Kernel, but remove the extra hardware support and such so that your kernel takes up less ram, but that is really the only benefit you will get.

---

### Post by Rog-Mahal on 2008-12-04
If I remember correctly, I tried installing grub to my linux partition and mucked things up. Then I reinstalled everything and just had grub install where it does by default, making sure to sync my partition tables with a refit rescue cd. Upon closer inspection of my bootup process, it looks like grub loads stage2, but I still have a timeout allows me to get into the grub menu... let me make sure that's the case, I'll reboot and check.

Confirmed. Grub loads stage2 and I still have the esc option to get into the menu. Perhaps it had something to do with installing it to the MBR?

---

### Post by cyberdork33 on 2008-12-05
> **Rog-Mahal said:**
> Confirmed. Grub loads stage2 and I still have the esc option to get into the menu. Perhaps it had something to do with installing it to the MBR?

Nothing sounds wrong with that operation... That is how it is by default. So... going back to your original question:
> **Rog-Mahal said:**
> Great! One last question: Since I have rEFIt installed and therefore grub loads in stage2, if for some reason I do have a problem and need to go back to a standard kernel where do I get to something like a grub menu?
You will have to modify your menu.lst to add your new kernel to the list to boot, so to boot the older kernel, you just hit escape to see the menu, then select the ubuntu kernel.

---

### Post by Rog-Mahal on 2009-01-04
Well, I finally got around to compiling a new kernel using a slightly modified version of volanin's config, unfortunately I got a kernel panic when I booted into it. It said something about being unable to sync the filesystem (is there a way I could get the exact kernel readout?) Any thoughts?

---

### Post by cyberdork33 on 2009-01-05
> **Rog-Mahal said:**
> Well, I finally got around to compiling a new kernel using a slightly modified version of volanin's config, unfortunately I got a kernel panic when I booted into it. It said something about being unable to sync the filesystem (is there a way I could get the exact kernel readout?) Any thoughts?
That is actually a pretty common error and can mean a lot of things.

Check to make sure that the filesystem you are using is COMPILED IN to the kernel, not built as a module...

---

### Post by Rog-Mahal on 2009-01-07
As in ext3? I set EXT3_FS and EXT3_FS_XATTR to "y" in my config.

---

### Post by cyberdork33 on 2009-01-07
> **Rog-Mahal said:**
> As in ext3? I set EXT3_FS and EXT3_FS_XATTR to "y" in my config.
IDK then, something else. Maybe a chipset or other driver needs to be compiled in rather than built as a module.

---

### Post by Rog-Mahal on 2009-01-08
Well, back to the drawing board :)

---

