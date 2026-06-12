---
title: "Ubuntu on an external drive for my iBook"
date: 2005-06-09
forum: Apple PPC Users
---

### Post by petermichaux on 2005-06-09
Hi,

I am interested in trying Ubuntu on my iBook. Until I am ready to leave OS X behind I would like to install Ubuntu on an external drive and hook it to my laptop when I want to use it. Is this possible? Would it be a difficult thing to do? I assume this would require a dual boot system, true?

Thanks,
Peter

---

### Post by Lost-in-North-Dakota on 2005-06-14
I am interested in this question also, with regards to Mac hardware in general.

Thanks.

Lost

---

### Post by interrupt on 2005-07-08
lost in north dakota and petermichaux,

Hi, I posted a HowTo which explained the proceedure for getting Ubuntu 4.10 booting off an external firewire drive.

[It is here](http://www.ubuntuforums.org/showthread.php?t=29837) 

I haven't logged on to these forums for a while now and I noticed that quite a few other people posted questions in response to  the HowTo. 

So, sorry to them for not replying  ;-) but I will be checking this thread now so feel free to post questions again.

cheers.

---

### Post by dwarf75 on 2005-07-13
Hi Interrupt,
excellent work with the boot of a firewire disk. Sadly enough, the whole thing goes completely over my head, even with some research on the internet.

AS you are the only one having ever solved this problem, could you please explain the following:

From your post I understand the following:
-Boot up the mac from the Install CD with the firewire disk connetct.
-Install Ubuntu on FW disk.
-Install will fail during install of yaboot.
-install initrd on internal harddisk (I can't find it in directory /dev with command "ls -la" in OS X.4 using the terminal)
- write/install script called "linuxrc" and link with initrd. This script raises the FW bus so you can access the root directories on both the internal and external hdd during initial start up.
- Install yaboot and set it up for dual boot (if you so wish).

Is this so far correct?

-Then restart computer.
- the boot sequence should be now:
     - start up
     - call initrd
     - initrd runs linuxrd
     - linuxrd raises FW bus making root on FW disk accessible
     - quit initrd
     - call yaboot
     - choose operating system
     - boot into OS on either disk

Now here is where my problems start:
1. where do i get initrd from? I can't find it on my internal hdd
2. how do i edit Initrd and what do i write in it?
3. where do i save linuxrc, what is the script code inside?
4. If I look in the /dev there is nothing starting with SD** (like your sda5). so where is my disk?
5. Where do I get yaboot from and how do i get the computer to boot of it after initrd is finished.
6. how do i need to alter the yaboto file to have dual boot.


I hope you or someone else can help me with this, as I really would like to give Kubuntu a go.
Sorry for being so dumb in this respect, but when it comes to linux i'm absolutely new newbie brew.

Thanks for any help.
m

---

### Post by interrupt on 2005-07-18
Hi dwarf75,

Have a quick re-read of my post because I first installed ubuntu onto my internal drive. This is because it is neccessary to have a working system in order to create the initrd and it's linuxrc script.

You'll certainly need some familiarity with a working linux machine before trying to boot off a firewire drive.

> 1. where do i get initrd from? I can't find it on my internal hdd
2. how do i edit Initrd and what do i write in it?
3. where do i save linuxrc, what is the script code inside?
 

initrd is the initial RAM-disk. you "get it" by using the  ```
mkinitrd
``` command. I can't talk you through this but trust me, there is plenty of information out there that will teach you how to do it and in the process you will answer your own question (3 above) about linuxrc.

But you must have your working linux system first to do these steps so I would make that your first priority, then find out about and get familiar with mkinitrd and the linuxrc script. Once you understand how they work and can make a system that boots via a RAM-disk, I will be happy to show you how you can boot from the firewire drive.

cheers.

---

### Post by dwarf75 on 2005-07-18
Hi interrupt,
thanks for your reply.
since my post, me and our it guy had a play and realised that we needed a working system first. 

Hence the whole idea got binned. The original idea was to just modify the boot sector of my ibook but otherwise to leave the internal hdd alone.

So, now i'm just going to buy myself an old windoze machine and make a linux server out of it and just VNC into it.

Easier then all the other stuff (although maybe a bit more expernsive)

Thank again.

Cheers
Mike

---

### Post by interrupt on 2005-07-19
Thought I'd post my linuxrc script as it may be useful to people attempting to do the external firewire boot thing. This is where the actual swap is made from the temporary root filesystem on the RAM-disk to the root filesystem on the external firewire drive.

```
#!/bin/sh
#
# $Id: linuxrc,v 1.11 2004/04/26 12:04:46 herbert Exp $
# this file is located at /usr/share/initrd-tools

mount -t proc /proc /proc

# loop rescanning SCSI bus

echo "scsi add-single-device 0 0 0 0" > /proc/scsi/scsi
sleep 1
echo "scsi add-single-device 0 0 0 0" > /proc/scsi/scsi
sleep 1

echo 0x805 > proc/sys/kernel/real-root-dev

umount /proc

exit 0

``` 

I can now plug my firewire drive into most new PPC macs and by holding down the 'option' key at startup I can boot into my linux system. ;-)

---

### Post by dwarf75 on 2005-08-07
Hi Interrupt,
I've been doing a lot of reading since my last post, and here is a different thought to the whole thing (The main reason is the fact that I don't want to take OS X of my internal hard disk for the installation, as Carbon Copy Cloner does not work under Tiger). Anyway, here we go:

To have a bootable external disk, we definitely need an initrd ram disk with the linuxrc script to load th scsi module before booting the kernal, hence how about the following approach (summary):

Start ubuntu install disk
go through initial set-up, but partition external disk by hand into:
              - Newworld boot partition (less then 1 mb)
              - Swap space (about 500 mb)
              - main partition (the rest)
go through installation until the bit where yaboot can't be installed.
abort installation
remove install disk and replace with liveCD
boot from liveCd (use same kernel as on firewire disk)
download yaboot binay from the net
copy into root directory on firewire disk using sudo
unpack tar in root (follow instructions on penguinppc.org/bootloaders/yaboot/)
create a yaboot.conf file that uses the arguments from the firewire disk.
create initrd with linuxrc script 
install yaboot into root partition of firewire disk
and viola it "should" be running

What do you think?
The main problem I have at the moment is the fact that it won't let me execute the yaboot binaries on the firewire disk.

Any ideas? Or am I going down the completely wrong track? 
Maybe there is just no way of installing ubuntu onto a firewire disk without having an existing system first????

Cheers and any help once again appreciated.

---

### Post by interrupt on 2005-08-10
Hi,

I think it should be possible to use a liveCD to prepare everything for firewire boot. 

> The main problem I have at the moment is the fact that it won't let me execute the yaboot binaries on the firewire disk. 

Not quite sure what you mean here. Do you mean you can't use the
```
ybin
``` 
command? If so that's a problem, as I'm sure you know ;-). What happens when you try it? 

It's possible that all the yaboot files were already placed by the initial install (the one you had to abort). I think the install has to be aborted *after* the binaries are written to the firewire disk. So, if you then untar the yaboot binaries you downloaded on top, it will screw things up.

From [http://penguinppc.org/bootloaders/yaboot/](http://penguinppc.org/bootloaders/yaboot/) 

 > IMPORTANT: if you have yaboot installed via your distribution's packaging system you MUST remove it before installing with either of these methods.  

So I would check that out next.

cheers.

---

### Post by dwarf75 on 2005-08-10
excellent point. might have time over the weekend to have a go at it.
Thanks. Will let you know how i fare.

Cheers
M

---

### Post by king_arthur on 2005-09-09
[QUOTE=interrupt]Hi,

I think it should be possible to use a liveCD to prepare everything for firewire boot. 

 

Not quite sure what you mean here. Do you mean you can't use the ybin command? If so that's a problem, as I'm sure you know ;). What happens when you try it? 

[/QUOTE]

I am just dropping into this discussion now.
Also looking for a solution to make my external F/W bootable in Ubuntu-PPC.

Getting **ybin** to work while in live-CD mode should be easy: just type **#apt-get install yaboot**

This can be done from the live CD no problem, provided you have updated your Synaptic repositories.

@interrupt
Do you think it is possible to implement  [this]("https://wiki.ubuntu.com/BootFromFirewireHardDisk") trick from the installation WiKi?

Would like to get Ubuntu to work without the need to touch my OSX install.
It's gotta be possible... :D

/P

---

### Post by nulio on 2005-09-13
Hello !
I am also very interested in that. The best would be to have a "firewire ubuntu installer" build which allows you to start your computer from the cd and install an "firewire" version on the hard drive....

Please make it happen :-)

---

### Post by nicholaspaul on 2005-09-28
I second that motion. In all my Ubuntu innocence, I can't follow most of the thread! If it was possible to build an ext.FW install that would be great. 
Maybe with the next version?

---

### Post by matthis on 2005-10-01
Hi there,

My ubuntu install is on /dev/sda5 as well, so I would like to test your initrd if possible. Would you mind making it available?

Also, would it be possible to edit the existing initrd rather than creating a new one? I couldn't find in the man pages how to modify a file within the initrd when creating with mkinitrd...

Thanks for any help,

matthis

---

### Post by interrupt on 2005-10-02
Sorry I can't upload files to the internet. But you need to make your own initrd - mine will not work (it is very machine/set-up specific). It is not difficult and whilst I agree the man pages are not completely comprehensive - you should also try googling "makeinitrd debian".

I posted some of my configuration files here:

[http://ubuntuforums.org/showthread.php?t=64012&page=1](http://ubuntuforums.org/showthread.php?t=64012&page=1)

maybe that will help too.

good luck and you will learn a lot by doing it yourself.

---

### Post by matthis on 2005-10-02
Thanks, I'm slowly getting there ;) 
I get a message from ybin saying: Driver sbp2 is not supported...
Does this mean that I have to recompile the kernel with firewire support not as a module?

Matthis

---

### Post by interrupt on 2005-10-03
Hi,

What did you get this error in response to? What were you trying to do?

---

### Post by matthis on 2005-10-03
I got this in response to  ybin, specifying --boot=/dev/sda2; This was after having built the modified initrd with your linuxrc script.

matthis

---

### Post by interrupt on 2005-10-03
Don't try to write the boot-loader to your firewire disk until you are sure that device is being raised properly by the initrd and the boot process completes. 
I'm assuming you have a working linux system on your internal drive, if so then just add a section to that system's yaboot.config file for the linux on the firewire drive. So, if you also have OS X on the internal, your yaboot prompt will have three options:
OS X
linux (internal drive)
linux (firewire drive)
This will allow you to test booting into the external drive. Once it is working only then should you write a boot-loader to the firewire drive's boot partition with ybin.
Regarding the question you had about modules, or compiling vital firewire drivers into the kernel. It doesn't matter. But if you use modules you must remember to include them when you build your initrd. Do this by specifying the required modules in /etc/mkinitrd/modules
cheers

---

### Post by matthis on 2005-10-03
Thanks a lot for your help. I will keep people informed of how this goes.
Best regards,

matthis

---

### Post by brent.stephens on 2005-11-20
I have found out that using an initrd is actually not necessary at all.  Check out my post [here](http://www.ubuntuforums.org/showpost.php?p=498516&postcount=5) and follow the instructions given, and you should have Linux booting off of Firewire in no time.  :D

---

### Post by boborosso on 2005-11-25
[QUOTE=brent.stephens]I have found out that using an initrd is actually not necessary at all.  Check out my post [here](http://www.ubuntuforums.org/showpost.php?p=498516&postcount=5) and follow the instructions given, and you should have Linux booting off of Firewire in no time.  :D[/QUOTE]
Hello from a debianist. I had followed the gentoo user advice with my 2001 tibook and was succesful too. I used a slightly longer rootdelay time - 12. I had to explain to a friend so i ended up putting a detailed page in my [under construction site](http://www.boborosso.com).

---

### Post by iBix on 2007-04-20
hmm i would need to get wine working in order to play an online game with a friend that is windows only. I could follow these directions in order to get my powerbook to boot from an external FW hd, but there are some things that are not clearly mentioned here. 

the most important? Do the procedures described include tweaking the internal drive ?? I don't want to mess up anything else than my external hd while trying this.

---

