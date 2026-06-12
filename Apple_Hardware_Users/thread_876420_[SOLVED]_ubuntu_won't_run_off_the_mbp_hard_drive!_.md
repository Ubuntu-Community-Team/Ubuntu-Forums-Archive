---
title: "[SOLVED] ubuntu won't run off the mbp hard drive! help!"
date: 2008-07-31
forum: Apple Hardware Users
---

### Post by jeh0753 on 2008-07-31
I have a 3,1 macbook pro - its an intel based system and i'm trying to run hardy on it (this will be my first time trying linux, i am used to using a pc). I successfully installed gutsy, but due to problems with the wireless i wanted to try hardy. i did so successfully, but more problems with the wireless lead me to try to reinstall hardy again, and thats where i ran into this problem.

so, to install ubuntu the approach i took was to partition with bootcamp and write ubuntu to the partition. I used rEFIt, and the penguin came up, as expected. when i hit it to start ubuntu, i get the following error message:
'no bootable device -- insert boot disk and press any key'
if i then put in the live cd, it boots right off the disk from there.

so far, in order to solve the problem, i removed the linux partition, reinstalled mac osx and thus reformatted the drive, and then repartitioned and reinstalled linux. but somehow, after i reinstalled rEFIt, the penguin icon was still there! 

I also tried to reinstall ubuntu a few more times, hoping it would fix itself. i tried it once, then tried it again and selected the 'advanced' option in the installer, which allowed me to choose where the bootloader would be installed. it defaulted at 'hd0', but i changed it to 'sda3', which was where i had installed ubuntu. no luck.

so, i took it to the macshop hoping they could get rid of the penguin so i could start over. the technician told me that i had written linux to the memory permanently and the only way to get rid of the penguin would be to give the mac a new logicboard. I (hope!) this was a cop-out, and i still have hope for ubuntu! 
any thoughts??

---

### Post by cyberdork33 on 2008-07-31
The Apple guy apparently had no idea what he was talking about. You have a Tux icon in refit because you installed grub to the MBR of the hard disk. This will not be erased or overwritten unless you clear out the MBR which just repartitioning does not do. Don't worry about it though, because it doesn't matter, it will be overwritten (again) when you reinstall.


the "no bootable device" error is normal with Hardy. There is a installation bug. Please check the FAQ, the answer was linked there.

[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by hajk on 2008-08-01
The link given in Cyberdork's post points to a great source of information on boot problems that is well worth a read. Some (like myself) don't consider it a bug though, whether peculiar to Hardy or otherwise. But a good read anyway, recommended!

However, when you're anxious to get your newly-installed Ubuntu to be recognized despite its icon being visible in rEFIt, then all you have to do is first select (with the arrow keys) the rEFIt Partitioner tool and resynch the GPT and MBR partition tables (say yes), then reboot the computer using the rEFIt Restart button. 

This needs to be done only once.

---

### Post by jeh0753 on 2008-08-01
oh my god, that solved my problem!!! Thanks so much. The mac guy did clear the mbr, but it didn't do anything. but resyncing with refit solved it! thanks again!
-jake

---

### Post by cyberdork33 on 2008-08-01
> **hajk said:**
> The link given in Cyberdork's post points to a great source of information on boot problems that is well worth a read. Some (like myself) don't consider it a bug though, whether peculiar to Hardy or otherwise. 
Just curious, what do you think is the problem then? This only reared it's head in Hardy... Feisty installs fine without error. and actually the Hardy alphas installed fine too, it wasn't until beta2 or RC of Hardy that the problem showed up.

---

### Post by hajk on 2008-08-01
No problem, and there has never been one for over two years now when the MacIntels first hit the market. A necessary step in the installation of GNU/Linux next to Mac OS X is that the GUID and MBR partition tables must be synchronized -- various methods to do so (as you well know), such as using gptsync. Easiest is to use the built-in facility in rEFIt if you happen to have rEFIt installed. The OP (and others like him) don't seem to have any problem with that.

Now, as to having that done automatically by the Ubuntu or Debian installer, that seems a great idea -- and more power to ya for promoting that! But, I don't consider not having it a bug. Anyway, all of this will soon become moot with the way Grub-Efi is moving along.

:guitar:

---

### Post by cyberdork33 on 2008-08-01
> **hajk said:**
> Now, as to having that done automatically by the Ubuntu or Debian installer, that seems a great idea -- and more power to ya for promoting that! But, I don't consider not having it a bug. Anyway, all of this will soon become moot with the way Grub-Efi is moving along.

:guitar:
The issue is that emulating an MBR table is part of the EFI spec. Thus, if changing the GPT, you should in turn, also update the MBR table. Gparted actually does this correctly. There is some other issue with the installer. That is why I don't believe it is libparted that is to blame, I think it is the installer doing something funky somewhere. Either way, it doesn't hurt anything to have the code to update both independantly if that is required as it should only be done if the drive contains a GPT at all.

I will probably do a test install of Intrepid on the next release. Hopefully I won't kill my system.

---

