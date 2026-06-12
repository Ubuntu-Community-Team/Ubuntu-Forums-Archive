---
title: "Share home partition OSX-Ubuntu"
date: 2009-05-07
forum: Apple Hardware Users
---

### Post by guja on 2009-05-07
I am planning to make 3 partitions on my hard disk - one for Ubuntu root, one for install Leopard and one more for storage.

I want to be able to read & write that partition from OSX and from Ubuntu. Is it possible and how to do that?

If anyone answers, please tell some kind of tutorial and exact steps since I am not quite experienced.

I am using Intel Macbook 2,1.

Thank you!

---

### Post by cyberdork33 on 2009-05-07
> **guja said:**
> I am planning to make 3 partitions on my hard disk - one for Ubuntu root, one for install Leopard and one more for storage.That really sounds like 5:

1. EFI partition
2. OSX partition
3. Ubuntu Root
4. Storage
5. Swap

however, your title seems to indicate that you want to share a home partition which is not the same as a generic storage partition.

> **guja said:**
> I want to be able to read & write that partition from OSX and from Ubuntu. Is it possible and how to do that?

If anyone answers, please tell some kind of tutorial and exact steps since I am not quite experienced.

I would use Disk Utility to resize your OSX partition and add two other partitions. The first one a msdos partition and the second free space.

Then use the Ubuntu installer to install to the free space.

---

### Post by guja on 2009-05-07
> **cyberdork33 said:**
> That really sounds like 5:

1. EFI partition
2. OSX partition
3. Ubuntu Root
4. Storage
5. Swap

Nope, it sounds like 4, since I am making swap file on Ubuntu root.

> **cyberdork33 said:**
> That really sounds like 5:

I would use Disk Utility to resize your OSX partition and add two other partitions. The first one a msdos partition and the second free space.

Then use the Ubuntu installer to install to the free space.

Okay. Use free space for root. Is this msdos supposed to be that shared partition? And how can I read and write that partition from both systems? Which FS to put? ext3 can't be written from OSX.

How to solve that?

---

### Post by cyberdork33 on 2009-05-07
> **guja said:**
> Nope, it sounds like 4, since I am making swap file on Ubuntu root.then you cannot hibernate.

> **guja said:**
> Okay. Use free space for root. Is this msdos supposed to be that shared partition? And how can I read and write that partition from both systems? Which FS to put? ext3 can't be written from OSX.
msdos is FAT.

---

### Post by guja on 2009-05-07
> **cyberdork33 said:**
> then you cannot hibernate.

Hm. Can not hibernate from OSX or not at all?

> **cyberdork33 said:**
> 
msdos is FAT.

Am I gonna be able to r+w FAT partition from both systems?

---

### Post by cyberdork33 on 2009-05-08
> **guja said:**
> Hm. Can not hibernate from OSX or not at all?
no just ubuntu.

> **guja said:**
> Am I gonna be able to r+w FAT partition from both systems?
yes, that is why it is typically used for thumbdrives and the sort. There is a 4GB Filesize limitation though.

---

### Post by mickie.kext on 2009-05-08
FAT32 is not god file system. It not support files bigger than 4GB, it is slow, unreliable... it is garbage. It is beter to use NTFS, and NTFS-3G (or MAC FUSE) for OS X. Ubuntu writes ti NTFS, OS X only with NTFS 3G software. 

I am using it that way. Only bad thing is that files deleted from NTFS not go to trash, they are deleted instantly

---

### Post by jwhendy on 2009-05-08
I just choose to keep my 'shared' stuff on the Mac size since I can access it from linux anyway.

I dual boot with FreeBSD now, but my setup used to be:
disk0s1: EFI
disk0s2: Leopard
disk0s3: linux
disk0s4: linux swap

I could easily mount my OS X volume from linux to get at whatever I wanted. It worked extremely well:
- I could point media players to my iTunes folder
- I setup Thunderbird on linux to use the same profile folder that already existed on OS X so that I had seamless email access

I don't know if it was necessary, but I found a nice little trick (or at least I think it's a trick) of setting my username, password, and UID (typically 501 on OS X for the first user created) the same on linux and being able to access all OS X folders without having to either 1) be root or use sudo, or 2) unsecure things from the OS X side in any way.

Good luck with your solution! I do the same thing now with FreeBSD, except my setup is:
disk0s1: EFI
disk0s2: OS X System and my /Users/Library and /Users/Desktop folders
disk0s3: ZFS partition with all other folders in /User/
disk0s4: FreeBSD partition from which I can import my zpool on disk0s3 and access everything I would want of my data.


-John
disk0

---

### Post by Shevek0506 on 2009-05-19
I'm preparing to set up a dual boot Ubuntu/OS X 10.4.11 on my MacBook Pro 2,1, and I'd like some input on my partition scheme.  I have a 150G internal hd and a 1.5T external hd.  The current plan is to have, as suggested, 5 partitions on the internal:

disk0s1: EFI
disk0s2: (JHFS+) Mac OS X root
disk0s3: (HFS+) ~ for both Mac OS X and Ubuntu
disk0s4: (ext3) Ubuntu root
disk0s5: Ubuntu swap

Is unjournalled HFS+ a reasonable choice for disk0s3 (I'll probably use the same thing for the partitions on my external)?  I know FAT32 is more assuredly compatible, but as I do audio work I will have files way over 4G.

[http://forums.macosxhints.com/archive/index.php/t-78462.html](http://forums.macosxhints.com/archive/index.php/t-78462.html) seems to suggest that since in OS X I can't just mount another partition as ~, I'd have to minimally symlink disk0s2/Users/<me> to disk0s3/.  Symlinking the actual ~ directory instead of its contents supposedly may break certain things in OS X, but I have a feeling most of them don't matter to me.  Do you think having ~/Desktop and ~/Library in a symlinked partition, and Desktop shared with Ubuntu, will cause OS X problems?

My main concern is conflicts between hidden preferences folders in ~, between OS X and Ubuntu.  I'm going to be using many of the same applications to edit many of the same files, so it would be nice to have settings carry over by having just one preferences folder; what do you think the chances are of that breaking something?

Supposing that actually sharing ~ between Ubuntu and OS X is a bad idea, any suggestions as to the most elegant way to get the effect I want?

In the process of repartitioning my internal, I'll also be messing with my external, and I'm wondering why it has an EFI partition.  Is it safe to/should I remove it?

---

### Post by jwhendy on 2009-05-19
Hey Shevek,


A few response items:
- I don't think Ubuntu, using an MBR, will be able to recognize disk0s5 since it can only see 4 logical/primary partitions. OS X, using GUID Partitioning can see a lot more (I forget how many, but more than most mortals would ever need).

- UHFS+ worked for me just fine. As you see from my previous post, I didn't even have a separate partition for it; I just mounted my OS X partition from linux. Saved me a partition.

- I don't know how well you'll be able to share preferences... OS X uses ~/Libary/Preferences/com.SomeName.plist and linux often uses ~/.applicationName files. I don't know how you'll use OS X preferences to carry over to Ubuntu so I don't think your Users folder makes much difference with respect to that.

- You can change your Users folder location. I'd recommend creating a temporary administrative new account. Then log out of your account and into the temp account. Go to system preferences -> accounts and control+click your account on the left. It will bring up a popup menu for advanced options. From there you can set the location of your Users folder to a custom location. I do not believe that doing that alone actually moves any files there; you should copy everything from the default ~/ folder to your new location (separate partition if you'd like), and then afterwards change the preferences option to /Volumes/volName/.../userName and you're golden. I've done this before with a ZFS partition.

- Elegant solution? If it were me, as I've already said, I'd just keep everything on the OS X side except for Ubuntu root and just access whatever you need from Ubuntu off your OS X partition. I think it's the simplest way to go. All your personal data is in one place for you to backup; there's one version of everything; and one hierarchy of folders. I actually have a separate folder within ~/ that I call 'Vault'. The structure is:
-Vault
--work
---bunch of work folders
--personal
---family
---financial
---code
---contacts&cal
---manuals
---songs&tabs (guitar stuff)
---wedding (planning material)

The only thing I use the designated OS X folders for are Music and Movies because I want to access them from Front Row and iTunes. If I didn't have to do that, I probably wouldn't even use those folders. Other than music and movies, then, EVERYTHING I care about is in Vault :) Yes, I keep an external HD backup!

- Your external probably does not need an EFI partition; someone else would know this answer better than me :) I think EFI is just needed to boot from the external drive, but I'm not even sure you need it for that!

Hope these answers help and I'm sure others will chime in too with suggestions and to correct me where I might have been wrong!



-John

---

### Post by cyberdork33 on 2009-05-19
> **Shevek0506 said:**
> I'm preparing to set up a dual boot Ubuntu/OS X 10.4.11 on my MacBook Pro 2,1, and I'd like some input on my partition scheme.  I have a 150G internal hd and a 1.5T external hd.  The current plan is to have, as suggested, 5 partitions on the internal:

disk0s1: EFI
disk0s2: (JHFS+) Mac OS X root
disk0s3: (HFS+) ~ for both Mac OS X and Ubuntu
disk0s4: (ext3) Ubuntu root
disk0s5: Ubuntu swap

Is unjournalled HFS+ a reasonable choice for disk0s3 (I'll probably use the same thing for the partitions on my external)?  I know FAT32 is more assuredly compatible, but as I do audio work I will have files way over 4G.
looks good. Your other option would be NTFS using macfuse. Also note that you will have to deal with user permissions on the HFS+ volume. You can change your Ubuntu uid to match the OS X one, though I do not know how to properly do that.
> **Shevek0506 said:**
>  [http://forums.macosxhints.com/archive/index.php/t-78462.html](http://forums.macosxhints.com/archive/index.php/t-78462.html) seems to suggest that since in OS X I can't just mount another partition as ~, I'd have to minimally symlink disk0s2/Users/<me> to disk0s3/.  Symlinking the actual ~ directory instead of its contents supposedly may break certain things in OS X, but I have a feeling most of them don't matter to me.  Do you think having ~/Desktop and ~/Library in a symlinked partition, and Desktop shared with Ubuntu, will cause OS X problems?
I've done the separate /Users partition before. I came to the conclusion that it really isn't worth it. What you CAN do, and do pretty easily, it symlink the Pictures, Movies, Music, (etc) folders in your Home directory somewhere else. Those directories don't have any hidden settings files usually.

> **Shevek0506 said:**
> My main concern is conflicts between hidden preferences folders in ~, between OS X and Ubuntu.  I'm going to be using many of the same applications to edit many of the same files, so it would be nice to have settings carry over by having just one preferences folder; what do you think the chances are of that breaking something?

I don't know that it is BREAK something, but I wouldn't recommend sharing a home directory anyway. OSX and Ubuntu use different versions of applications, and even have settings in different files. For instance, OSX has a .profile files for bash, but Ubuntu has a .bashrc I think that if there are certain hidden files that you want to sync between the two, it would be easier to have a shutdown script in either that copies the specific files you want to the appropriate location. People have done this before though... If you do this, you will have to make sure that your users' uid are the same.

> **Shevek0506 said:**
>  In the process of repartitioning my internal, I'll also be messing with my external, and I'm wondering why it has an EFI partition.  Is it safe to/should I remove it? If your hard drive uses the GPT/EFI format, it should have an EFI partition. that is normal and standard. remember though that once the linux kernel is loaded, the GPT is available for use and you are not limited to the MBR table any longer.

> **jwhendy said:**
>  - I don't think Ubuntu, using an MBR, will be able to recognize disk0s5 since it can only see 4 logical/primary partitions. OS X, using GUID Partitioning can see a lot more (I forget how many, but more than most mortals would ever need).
swap is fine there. It is really just the partition containing the kernel that you need to have accessible in the MBR. once the kernel loads, all GUID Partitions are available.

> **Shevek0506 said:**
> - Elegant solution? If it were me, as I've already said, I'd just keep everything on the OS X side except for Ubuntu root and just access whatever you need from Ubuntu off your OS X partition. I think it's the simplest way to go. All your personal data is in one place for you to backup; there's one version of everything; and one hierarchy of folders. I actually have a separate folder within ~/ that I call 'Vault'. The structure is:Just if you disable journaling, you are taking a lot of protection away from your OS files.
[http://en.wikipedia.org/wiki/Journaling_file_system](http://en.wikipedia.org/wiki/Journaling_file_system)

> **Shevek0506 said:**
> The only thing I use the designated OS X folders for are Music and Movies because I want to access them from Front Row and iTunes. If I didn't have to do that, I probably wouldn't even use those folders. Other than music and movies, then, EVERYTHING I care about is in Vault :) Yes, I keep an external HD backup!that really where I was going too. just share the stuff you want, not the entire home directory.

---

