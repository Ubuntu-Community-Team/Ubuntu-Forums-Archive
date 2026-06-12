---
title: "Dual booting Edgy w/ XP clarification~"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by lemoniceblock on 2007-02-16
Hi all!

I've been using Ubuntu on my laptop and now that I have a bit of a break from school, I'd really like to get my desktop to dual boot with Ubuntu.  I've read through guides etc but I'd like some clarification =^^=

Currently, my desktop has:
[LIST]
[*]1 primary partition with Windows XP
[*]1 10GB logical partition that I had left empty (see, playing with Linux has been on my mind for quite some time :P ). 
[*]The rest for storage (work, media etc)
[/LIST]

I know that Linux can't write NTFS and Windows can't read/write EXT3 but having 10 gigs for Ubuntu really isn't going to be a problem since I write most of my work to my USB anyway.
I am planning to have a 256MB partition for swap and the rest for / and home.  I was going through the installation CD when I came across some questions:
[LIST]
[*]Do I need a /boot partition for Ubuntu?
[*]Does the /boot or / partition need to be primary?  I don't really understand the need for primary ones; I know that they boot but then, I read somewhere that a computer would work fine with no primary partitions...:confused: The free 10gigs are in an extended partition so I don't think I can make it into a primary one...
[*]When I was going through the installation steps, I the swap partition and intended / parition were labelled SDA 6 and 7 respectively, but later on, the installer said that GRUB would be installed on hd0...should I change this?  I am most worried that this might mess up my Windows XP.
[*]It seems that Ubuntu @ installation wants me to assign mounting points to all partitions including my Windows XP one...should I just write mounting points like /windows and /storage?  Will this affect my Ubuntu partition or can I remove them later?
[/LIST]

Thanks  in advance!

---

### Post by dbbolton on 2007-02-16
/boot partition isn't necessary but sometimes recommended.

i have always had / as a primary partition

grub will not affect XP

you can make the mount points for windows and storage whatever you want, and change them later with fstab.

---

### Post by Quintin Riis on 2007-02-17
Yes, Linux **can** write to NTFS, and yes Windows **can** write to ext2 filesystems.  Reiser as well, but that's trickier.

You can install linux on a logical partition.  

You don't need /boot, this isn't 1996.

GRUB is installed on the master boot record of the hard drive.  Has nothing to do with your Windows installation.  It's the first 512bytes of the hard disk, not the area with any of you programs or data.  GRUB can boot pretty much everything, hence the name "Grand Unified Boot Loader".  You can get rid of it later if you choose by booting from a Windows NT 5 or 5.1 install disc, going to the recovery console, and using the 'fixmbr' command.

> It seems that Ubuntu @ installation wants me to assign mounting points to all partitions including my Windows XP one...should I just write mounting points like /windows and /storage? Will this affect my Ubuntu partition or can I remove them later?
That's fine.  No, it won't.  Yes, you can.

Usually the question is 'how', not 'can'.  You can do pretty much anything.

Let me know if you have further questions.

---

### Post by lemoniceblock on 2007-02-17
Thanks dbbolton and Quintin Riis =^^=
I just need one more clarification (sorry if this is repetitive but I'm kinda nervous about this and don't know a lot about the master boot record :P )~

I should install GRUB on hda0 and not something else like sda0 and when this is done, when I reboot, I should be able to choose between XP and Ubuntu?

Thanks again, enjoy your weekend! =D

---

### Post by Fahuadai on 2007-02-17
In answer to an earlier question, 

Windows can read and write to ext3 using a program available from [www.fs-driver.org]("http://www.fs-driver.org")

I have a windows partition, a ubunut partition, who then both share a third partition of ext3 which stores all my documents and music files. Windows has My Documents pointing to this partition, and ubuntu's /home folder is set to the same. 


About the /boot, myself i didn't use one. I believe GRUB installed by default to the same partition that ubuntu was installed to. (hda2 in my case) Could someone else confirm this though, I not want to give bad advice.


After the install, GRUB will always boot and then give you the option to boot ubuntu or windows. 

To be safe, make sure all your data is backed up on either cd/dvd or another computer or anywhere.  Nothing is worse than losing important data. Hope it goes well for you.

---

### Post by Quintin Riis on 2007-02-17
GRUB gets installed to whatever hard disk you are booting from now.

Yes, you will get to choose between Ubuntu and Windows.  If for some reason Windows isn't detected it's trivial to add an entry for it to menu.lst.

(hda0.. there is no such thing..)

---

### Post by lemoniceblock on 2007-02-18
Yup~ I got that mixed up; I meant hd0 or sd0.
Alright, everything's working great now, thanks everyone! =D
If I were to install the fglrx or the opensource radeon drivers for my graphics card, would this affect my graphics card when I'm in Windows?
I know there shouldn't really be any need for antiviruses etc on Ubuntu but would it be a good idea to install one in case I get a 'bad' file or something while I'm on Ubuntu but it might infect my XP as well?
Thanks again ^^

---

### Post by Fahuadai on 2007-02-19
> If I were to install the fglrx or the opensource radeon drivers for my graphics card, would this affect my graphics card when I'm in Windows?

No, Windows will use it's own drivers, as will linux. They are different files and will be on their respective partitions. They are completely seperate.


> I know there shouldn't really be any need for antiviruses etc on Ubuntu but would it be a good idea to install one in case I get a 'bad' file or something while I'm on Ubuntu but it might infect my XP as well?

You will find the majority of ubuntu and linux normal users (ie. non-professional/corporate) will not install AV software on their linux install, myself included. 

As for infecting windows, no. Your windows OS is installed on a seperate partition. Effectively consider this to be a different hard drive, which is inaccessible (unless you configure it otherwise) from one OS to the other. The OS's can not read or write to the other's partition and thus no programs running on the OS can either.

I would recommend highly running AV software on the windows box, to protect it from viruses and other security risks, but this is only to protect itself, not your linux.

If you are concerned, I'm sure there is AV software available. The three places I would start my search would be the package manager, (Adept or Synamtic) followed by google then these forums.  Like I said, I don't feel a need for one and so don't run one and so can not name, let alone recommend any for you. 

The main reason for this is because the majority of virus's are written for windows machines (because the majority of computers are running MS windows), thuslinux machines are generally immune. I'm sure other people can explain this further, and if you want you can search around for them. 


Hope this helps.

Finally sorry for the slow reply, but have had quite a busy day.

---

### Post by lemoniceblock on 2007-02-21
Hihi~
Thanks, that really clear things up (and please don't apologise ~ the reply wasn't slow ^^ )!~

---

