---
title: "help installing Mint 9"
date: 2010-10-22
forum: Apple Hardware Users
---

### Post by thepotatobasher on 2010-10-22
**So I understand what to do until this part...**

Can I just use my ubuntu livecd to install this??? I have 10.10 on my machine now.  I'm just freaked out about the partitioning manually





**3. Installation type**

          If you type TAB, you will find several installation methods. You then  type "expert" as we will be installing Squeeze from a Lenny  netinstaller. We cannot yet install Squeeze natively as there is still a  bug in the Debian Installer with respect to yaboot.
        We will install a base system without a graphical user interface. We  will add that later ourselves. At the "Choose Mirror" page I selected  Squeeze-testing as the Debian version to install. Later I opted for no  additional installer components.
        In the partioner you select Manual. I hope you know what to do here,  it can seriously damage your contents of your drive if you don't know  what you are doing. You need a bootloader partition, a partition with  EXT3 set as root (/) as mount point and you need to format that  partition. You will also need some swap space the amount of your RAM. It  will look similar to this:
          [[IMG]http://mac.linux.be/sites/default/files/large_partition_table.JPG[/IMG]]("http://mac.linux.be/files/Isadora/partition_table.JPG")
          I chose as kernel linux-image-2.6.32-5-powerpc. I took all generic drivers in initrd.
        In the Package Manager I opted for non-free as well. In the "Select  software" section I unticked the graphical environment with the space  bar, as we will add it manually later. Let it install everything and  reboot into base system.

---

### Post by linuxopjemac on 2010-10-22
You can use the liveCD to create the partitions. You cannot install a Debian base system with Ubuntu.

---

### Post by thepotatobasher on 2010-10-22
> **linuxopjemac said:**
> You can use the liveCD to create the partitions. You cannot install a Debian base system with Ubuntu.

I'm still at bit new at the whole linux thing.  can you explain how I would do this?

Would i use something like gparted? [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by linuxopjemac on 2010-10-22
You can use the Debian installer itself to do that. Don't be afraid. Just be very cautious not to delete/format partitions you use. In fact, within Debian installer it's basically the same as gparted, or what Ubuntu uses in the liveCD. If you have important data on an OSX partition, back it up with carbon copy cloner. I cannot be more precise. Just follow the manual, it's clear enough I'd say.

Or you wait for my iso-based installer, but there you can do "use whole disk" or use an empty space. It's less flexible.

The iso will take a week I hope.

---

### Post by linuxopjemac on 2010-10-22
If you want, I can make a customised iso for you to install a Debian base system, without partitioning yourself. You can then choose "use whole disk".

Up to you.

---

### Post by thepotatobasher on 2010-10-22
That would be awesome if that's not a problem for you!

---

### Post by linuxopjemac on 2010-10-22
You have to realize that all data on your computer will go...you want that ?

---

### Post by thepotatobasher on 2010-10-22
yeah, that's fine.  As long as it doesn't take you too long to change the ISO.  I'd feel bad if you had to spend a few hours doing it. 

This is a fresh install on a system that I wasn't using to begin with.  it's 100% Linux because OSX 10.3 is pretty much unsupported and useless now.

---

### Post by linuxopjemac on 2010-10-23
I am at the point of giving the iso project up. It's such a pain with my customised settings. It borks at every single change I make. I try one more day. The script I made, which is using everyone now, is working absolutely fine.

---

### Post by linuxopjemac on 2010-10-23
Your base system install iso (**without confirmation that all data will be lost**) can be found here:
[http://mintppc.org/temp/debian-testing-powerpc-CD-1.iso](http://mintppc.org/temp/debian-testing-powerpc-CD-1.iso)

Try it out and tell me if it worked. You should have a base system after this. I don't want to test such an iso, I like to have control over what I'm doing.

---

### Post by linuxopjemac on 2010-10-23
Ignore the error message about the yaboot installation It will work.

---

### Post by thepotatobasher on 2010-10-23
Cool.  I really appreciate it!  I'll try it out

---

### Post by thepotatobasher on 2010-10-23
> **linuxopjemac said:**
> Ignore the error message about the yaboot installation It will work.

i might be approaching this wrong, but I did get the yaboot error and continued the install without a boot loader. 
As far as I can tell, the only thing I can do at this point is boot with open firmware or use a live CD to add yaboot.conf

What would you suggest at this point?

EDIT. i found this and am trying it 
[http://mac.linux.be/content/installing-debian-external-firewire-disk](http://mac.linux.be/content/installing-debian-external-firewire-disk)


when I exited installer without boot loader i was given: 
"boot manually the  /boot/vmlinux kernel on partition /dev/hda3 and root=/dev/hda3 as kernal argument

there is no yaboot.conf in /etc, but I did find one in /target
I tried to copy that to /etc and edited it in nano to direct boot to hda3 but to no avail.

---

### Post by linuxopjemac on 2010-10-24
I will have a look what that iso does. I stopped working on the installer iso, so I can have a look what this iso does. Will keep you updated.

---

### Post by linuxopjemac on 2010-10-24
I did it myself. I chose install on entire disk and then, after I got the yaboot error, continue without bootloader. It rebooted and then it brought me into yaboot 1.3.16. From there I chose default Linux and I booted into a Debian base system. I don't see the problem.

---

### Post by thepotatobasher on 2010-10-24
yesterday when I tried to reboot all I got was the apple flashing computer question mark.  I had no options of utilizing yaboot.

Since there is a version of yaboot in /target, should i copy that to /etc?
I'll probably try that this next time and hopefully it will recognize it

---

### Post by linuxopjemac on 2010-10-24
Maybe yaboot-installer does not work for all Apple machines. Yaboot is still buggy, Squeeze is not finished yet. That is all I can say about it. What I would do is download and burn the Lenny Mini.iso. Do expert and immediately go to install Bootloader. Skip all the rest as you have a working system on your Mac already.

Just follow the first few steps of Linux MintPPC 8:
[http://www.mintppc.org/content/installation-mintppc-8](http://www.mintppc.org/content/installation-mintppc-8)

---

### Post by thepotatobasher on 2010-10-24
> **linuxopjemac said:**
> Maybe yaboot-installer does not work for all Apple machines. Yaboot is still buggy, Squeeze is not finished yet. That is all I can say about it. What I would do is download and burn the Lenny Mini.iso. Do expert and immediately go to install Bootloader. Skip all the rest as you have a working system on your Mac already.

Just follow the first few steps of Linux MintPPC 8:
[http://www.mintppc.org/content/installation-mintppc-8](http://www.mintppc.org/content/installation-mintppc-8)


Alright.  I just got scared by your comments about "knowing what you're doing" apparently you can do a full format with the mini iso so hopefully this goes better

---

### Post by linuxopjemac on 2010-10-24
Don't install the Debian Lenny base install! Only use the Debian Lenny mini.iso to install the bootloader.

---

### Post by thepotatobasher on 2010-10-24
I couldn't figure out how to just install the bootloaded so I installed the base system for lenny. I followed the directions on mintppc and didn't install the graphical interface, downloaded and installed mint. 

The install went pretty well.  Over the next few days I will have to probably consult with you about a few minor issues that I have encountered.  

i got an error running isdnutils init scrip
boot shows that there is an error with the ondemand governor (i think this has something to do with cpu temp or something) i have a TI book and I installed the recommended temperature program for allluminum powerbooks just in case it could help. 

for some reason synaptic package manager seems to have problems searching, updating etc.  

I have  a GTK+ error on startup (icon theme not properly set)

and i tried to install fw-cutter but the final step produced an error.
 
Is there a way to get an output of boot errors?
I'd assume that it would be better to address those issues on the mintppc forums or your forums?

---

### Post by linuxopjemac on 2010-10-25
MintPPC related problem you post in the forums of MintPPC.

---

### Post by Perfect Storm on 2010-10-25
Please use mint forum: [http://www.mintppc.org/](http://www.mintppc.org/)


Thread closed.

---

