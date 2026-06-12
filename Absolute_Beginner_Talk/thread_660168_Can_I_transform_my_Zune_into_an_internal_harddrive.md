---
title: "Can I transform my Zune into an internal harddrive?"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by 449 on 2008-01-06
Is this possible? I would like to use it as another partition.

---

### Post by 449 on 2008-01-06
anyone?

---

### Post by PeterJS on 2008-01-06
Obviously it's an external device and can be made in to an internal disk without dismantling it and sticking it in side the system. But it can be made a more permanent part of the file system. Is there a specific function you had in mind that it can't accomplished from /media/zune?

---

### Post by 449 on 2008-01-06
> **PeterJS said:**
> Obviously it's an external device and can be made in to an internal disk without dismantling it and sticking it in side the system. But it can be made a more permanent part of the file system. Is there a specific function you had in mind that it can't accomplished from /media/zune?

How would I make it show up in Gparted? Is it just as easy as opening it up and plugging it in to my computer?

---

### Post by PeterJS on 2008-01-06
I was joking about dismantling it, by definition it will never be internal. But you can certainly use as a hard drive. Plug it in, and open up gparted and it should show up in there.

---

### Post by metalpancake on 2008-01-06
You should be able to install Ubuntu on it as if it were an internal hdd.:)

---

### Post by 449 on 2008-01-06
> **metalpancake said:**
> You should be able to install Ubuntu on it as if it were an internal hdd.:)

It doesn't show up in Gparted...

---

### Post by PeterJS on 2008-01-06
That's no good. Does it show up in /media/ ?

---

### Post by ryanVickers on 2008-01-06
I bet m$ blocked it from showing up in non-windows OS's or something...

---

### Post by 449 on 2008-01-06
> **PeterJS said:**
> That's no good. Does it show up in /media/ ?

Yes.

---

### Post by codesplice on 2008-01-06
Last I saw on the zune hacking boards, it required a sneaky registry hack in windows to make it even show up as a portable device under My Computer - and you still had to use the Zune software to enable write access to it.  I'm not sure that there's a *nix solution for it yet, though I could be wrong.

---

### Post by 449 on 2008-01-06
> **PeterJS said:**
> That's no good. Does it show up in /media/ ?

I take that back it doesn't now.

But when I plugged my camera in and went to select device it showed up there.

---

### Post by Salpiche on 2008-01-06
what size and what model? I have the micro 1g and it shows up on gparted, are you using it in a windows machine as well? if so make sure that you eject it before you plug it in your Ubuntu box, I had times when it didn't show because I didn't eject.

---

### Post by 449 on 2008-01-06
> **Salpiche said:**
> what size and what model? I have the micro 1g and it shows up on gparted, are you using it in a windows machine as well? if so make sure that you eject it before you plug it in your Ubuntu box, I had times when it didn't show because I didn't eject.

It's a 30GB, original model. Right now I'm using it on Ubuntu ,but I have a windows machine I can use. I did completely format it so there's no firmware or anything on it. How do I eject it?

---

### Post by Salpiche on 2008-01-06
> **449 said:**
> It's a 30GB, original model. Right now I'm using it on Ubuntu ,but I have a windows machine I can use. I did completely format it so there's no firmware or anything on it. How do I eject it?

on the windows machine? while still plugged in, go:  start>my computer>  right click on the drive and click "eject" from the menu. Wait for 20 to 30 seconds before you unplug it.

---

### Post by 449 on 2008-01-06
> **Salpiche said:**
> on the windows machine? while still plugged in, go:  start>my computer>  right click on the drive and click "eject" from the menu. Wait for 20 to 30 seconds before you unplug it.

It's not showing up in windows should I install the firmware onto it?

---

### Post by Salpiche on 2008-01-06
> **449 said:**
> It's not showing up in windows should I install the firmware onto it?

You shouldn't have to. 
On Windows go to > control panel> Administrative tools> computer management> disk management> and then check if it shows up. It might be showing up and just not being assigned a drive letter.

---

### Post by 449 on 2008-01-06
> **Salpiche said:**
> You shouldn't have to. 
On Windows go to > control panel> Administrative tools> computer management> disk management> and then check if it shows up. It might be showing up and just not being assigned a drive letter.

I installed the firmware, however it still doesn't show up in My Computer and I tried won't you suggested and wasn't there either.

---

### Post by Salpiche on 2008-01-06
> **449 said:**
> I installed the firmware, however it still doesn't show up in My Computer and I tried won't you suggested and wasn't there either.

Are you on dual boot? if so leave it plugged and boot on to ubuntu, then check in /media or /dev. also open a terminal and use ```
fdisk -l
``` to see if it is mounted at all, post the output here.

---

### Post by 449 on 2008-01-06
erik@erik-desktop:~$ sudo fdisk -l
[sudo] password for erik:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       28305   227359881   83  Linux
/dev/sda2           30218       30401     1477980    5  Extended
/dev/sda3           28306       30217    15358140    7  HPFS/NTFS
/dev/sda5           30218       30401     1477948+  82  Linux swap / Solaris

Partition table entries are not in disk order
erik@erik-desktop:~$ 


](*,)

---

### Post by Salpiche on 2008-01-06
> **449 said:**
> erik@erik-desktop:~$ sudo fdisk -l
[sudo] password for erik:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       28305   227359881   83  Linux
/dev/sda2           30218       30401     1477980    5  Extended
/dev/sda3           28306       30217    15358140    7  HPFS/NTFS
/dev/sda5           30218       30401     1477948+  82  Linux swap / Solaris

Partition table entries are not in disk order
erik@erik-desktop:~$ 


](*,)

hmm... and you want to use it as an internal drive, planing on installing linux in it? if so you can try and let us know. since I have no clue as of why it isn't mounting. Maybe some one else can think of something.

Passing the baton while I research...

---

### Post by 449 on 2008-01-06
Yeah, for Linux, Windows, or even storage. I cracked the screen pretty badly on it so it's hardly usable. The main reason is really, I'm hoping it will be be faster than my WD 250GB HDD, because that's what I'm currently running Ubuntu off of. If not it will still be put to good use.

---

### Post by 449 on 2008-01-06
Is nautilus the Linux equivalent to regedt32? Any chance it could be done similarly?

---

### Post by 449 on 2008-01-07
i havn't had any luck with this. Is it possible to remove the hdd and connect more directly?

---

### Post by Luinfana on 2008-02-24
Your Zune isn't going to mount under Linux at all (show up in /media/, etc), because it's not a normal mass storage device, It's designed to use Microsoft's Media Transfer Protocol to send and recieve data over its USB connection. There has been some progress using [libmtp]("http://libmtp.sourceforge.net") to communicate with the Zune, but files can only be *read or deleted*. Write-access (when the Zune displays "connected" on the screen) is not enabled until the Zune recieves a secret passkey from the Zune software, and thus Linux-based media managers (amarok, rhythmbox, etc) can't manage the Zune and you can't browse it like a normal drive.

If you really want the 30GB hard drive from the Zune that badly, you're going to have to crack it open yourself and remove it...you can't really do anything with it while it's being locked down by the Zune hardware itself. The drive is a Toshiba MK3008GAL.

There's some instructions [here]("http://www.zunescene.com/80gb-zune/") that might help you in dismantling the unit. They're based on upgrading the hard drive to an 80GB model...but you'll just need to follow them up to where they remove the original drive.

It's not going to be faster than your WD 250GB drive, though. The WD is a 5400 rpm drive if I remember correctly, and the MK3008GAL is a 4200.

Good luck, anyway.

---

### Post by AllWires on 2008-04-11
> **449 said:**
> Yeah, for Linux, Windows, or even storage. I cracked the screen pretty badly on it so it's hardly usable. The main reason is really, I'm hoping it will be be faster than my WD 250GB HDD, because that's what I'm currently running Ubuntu off of. If not it will still be put to good use.

Thats the same exact thing I did. I dropped it when I was leaning my chair back and then when I put my chair down I heard a crack and it came down right on the screen and the screen doesn't work -at all-  :(

so I was hoping there would be some way I could turn it into a hard drive or something

---

