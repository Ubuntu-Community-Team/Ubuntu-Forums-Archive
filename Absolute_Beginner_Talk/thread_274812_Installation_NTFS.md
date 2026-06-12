---
title: "Installation NTFS"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by hyby on 2006-10-10
Howdy, im trying to install the CD...but i am having a few problems with paritions.

I have an 80 gig drive. 

C: - 5 NTFS
d: - 10 NTFS
e: - 35 NTFS
f: - 10 unpartitioned

When i try to install 6.06.1, it asks for the parition but doesnt recognise it. Is it because i am using NTFS. Or is there a way around it.

---

### Post by Kateikyoushi on 2006-10-10
Are you trying to partition manually ?
You have to create a partition in that unpartitioned space.

[Can find plenty of info here.]("http://users.bigpond.net.au/hermanzone/")

---

### Post by hyby on 2006-10-10
Sorry i guess i didnt explain it properly. When i try to install it, the installer does not recognise any partitions on my hard-drive.

---

### Post by Theimon on 2006-10-10
You have to install it on, for example, ext3. Linux won't work from NTFS, although it can interact with it. You're gonna have to partition the unpartitioned space to a new filesystem and then go ahead with the install.
It looks like the unpartitioned space is at the end of your drive so you could get trouble booting the system. Try to create a small (~100MB max) ext3 partition at the beginning of your drive and let the installation call it /boot. That way you can avoid booting trouble.
I guess you still got Windows installed? Try to get your hands on Partition Manager or Acronis Disk Director, they give a fairly clear GUI so it's easier to make new partitions. Especially when it's all new to you, it's easier to keep some sort of oversight on your drive when making new partitions,

---

### Post by dannyboy79 on 2006-10-10
actually, if you are trying to dual boot i would look at the instructions for dual booting before you do anything.

could you post the error you get. does it say that there is no hard drive to install to? if i were you i would chose to partition manually. you can't install onto ntfs, then once you are in there you can select the unallocated space and chose to format it ext3. you should be on your way. if the normal ubuntu installer doesn't work, download the alternate cd and DON'T chose the OEM install, just chose the normal install from the alternate cd, then do the manual partition creation and you should be ok.

---

### Post by hyby on 2006-10-10
I am currently running the Live CD. With Disks manager i can actually see my paritions. However, when i try run gnome partition editor or the install, it recognises my drive as unparitioned. I was wondering does this help.

---

### Post by equal on 2006-10-10
Linux can't run on an NTFS partition, it's proprietary to Microsoft, and Linux just isn't programmed that way. So installing will have to take place on the unpartitioned space. Dual boot it!

---

### Post by hyby on 2006-10-10
Well in the past whenever ive tried to install mandriva 2006, it would recognise my partitions. I would set aside 10 gig and the mandriva setup would recognise it and allow me to select it for installation. However, with ubuntu i cant seem to do it.

---

### Post by bulldog on 2006-10-10
I suggest you do a reboot and see if the BIOS recognize your hdd properly.

If so,Ubuntu should do to.

Have you done the partitioning with your windows cd or in a later stage with something like Partition Magic?

---

### Post by hyby on 2006-10-10
My bios recognises the hardrive, windows boot.

I set aside the 10 gig and formated into a ext3 partion. The installation wont even recognise it. I was wondering can someone please direct me the dual booty link

---

### Post by bulldog on 2006-10-10
> **hyby said:**
> My bios recognises the hardrive, windows boot.

I set aside the 10 gig and formated into a ext3 partion. The installation wont even recognise it. I was wondering can someone please direct me the dual booty link

Did you check the media on your cd?

Maybe the disk isn't entirely fresh afterall.

If the media check fails,try to burn it on a lower speed and don't use cd-rw disks.

---

### Post by hyby on 2006-10-10
Yeah just checked it..no problems...

Just tried to install mandriva...recognised my paritions

---

### Post by hyby on 2006-10-10
I was looking through windoz and realised i have a hidden partition that was setup by Benq to load my XP image. 
Now my this is my hard-drive partitioning setup now

c: 5 gig - ntfs
d: 10 gig -ntfs
e: 47 gig - ntfs
f: 2 gig - fat32 -eisa32 (hidden)
g: 10 gig *tried fat32, ext 3* 

For particular reason ubunty's paritioning tool and installation program does not see these partitions. However disk manager does. Would the hidden partition effect the installation or how ubuntu recognises the hard-drives paritioning. I know there is nothing wrong with my hard-drive or my laptop mobo-bios because mandriva runs flawlessly with a lot of excess baggage. 

I am desperate of trying to run ubuntu, but i do not want wipe my whole hd so i can create partition.

---

### Post by CatKiller on 2006-10-10
Possibly. It depends on whether those partitions are Primary partitions or not. You can only have four primary partitions. If they are all primary, then you'll have to remove one of them before you can create another.

If one of them is an extended partition with a logical drive, then you may be in luck.

---

### Post by hyby on 2006-10-10
Had a look at my, d,e,f drives and they are all logical drives so...im wondering whether if there something else buggering it up

---

### Post by CatKiller on 2006-10-10
> **hyby said:**
> Had a look at my, d,e,f drives and they are all logical drives so...im wondering whether if there something else buggering it up

It seems there must be. You could try the [GParted live cd]("http://gparted.sourceforge.net/livecd.php"). That will have a later version of GParted than the one the Ubuntu installer uses, and possibly that won't be affected by whatever wrinkle is affecting you. It is promising that other Linux distributions are able to accurately assess the partitioning scheme in use on that drive.

There's also the option of the Alternate cd. This uses a text-based installer that they've been using for longer than the live install. Possibly that will work better for you.

---

