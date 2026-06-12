---
title: "Zenwalk install.. stupid mistake"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by xerox on 2007-04-05
Somehow, I find this flavor of linux named "Zenwalk". The name sounded pretty funky, so I decided to download it - and burn it on a CD. Today though,  I seriously screwed up. *Without* backing up any files on ubuntu (edgy eft, 6.10 if i remember), I decided to install zenwalk on the **same** partition. Yes, you read me correct. 

Why? For some unknown reason, I thought linux distros were all compatable with eachother, and can recognize the fact that another distro is on the same partition, and work around that fact (by naming their system files boot2, bin2, tmp2, etc2, etc.)

Unfortunately, my theory (heh..) didn't quite turn out to be true.

Now I'm stuck. I know I should (and probably deserve to) format my entire partition, and reinstall from the ubuntu disk. Yet, I have a few files on that partition i want to save.. (they're in /home/shell/.. my username)

Misc. Info you might need for diagnostics:
- running a Sony Vaio VGN S260 laptop
- have partitions 1&2 set up for windows (one as a fat32 transfer partition between linux and windows, the other for windows itself)
- using Windows XP Home Edition, Ubuntu 6.10 Edgy Eft, and Zenwalk (??)
- right now typing from Ubuntu install disk. (only thing that works, other than windows.)

Already tried..
- Booting up Ubuntu, from both Linux Kernel versions (2.6.17 and 2.6.16 or something like that.. if you need exact numbers just give a shout)
- Also, booting up Ubuntu from both Linux Kernel version recovery modes (stops at recognizing a third USB port)
- Booting from the Zenwalk install CD (only options are installing several different irrelevant-to-my-problem ways)


... yeah.. I probably screwed up big time on this one.. 

P.S. 

A  question, that might help with my problem (self diagnostics going on here.. well I'm a newb anyway)

- If I'm on the Ubuntu install disk, is it possible to mount a partition? Because if it were, then I would simply mount my linux partition and my windows-linux transfer one, and then back up my files (a step too late for that eh?) then just wipe the thing, starting from a fresh slate. (probably then, safely experimenting with ZenWalk)

I have a feeling this has something to do with there not being any system files for Ubuntu (or them being wiped out by the ZenWalk install.. if this is the case, for those more Ubuntu-experienced readers, then is it possible to reinstall ubuntu without it wiping out my home directory?)

Lastly.. I have a feeling this is in the wrong section (heh..)

Well, thanks for reading.

---

### Post by deadgobby on 2007-04-05
Well Ubie would be gone now if you installed the other distro on the partition Ubie was on. Sorry to tell you that. At least you know now that to be careful when installing any other distro. 
Gobby

---

### Post by irwa82 on 2007-04-05
Hi,

It sounds like you really got yourself into a mess.

Number 1 rule when installing a new os or upgrading an existing one like going from edgy to feisty is to back up all important data especially if you don't know what you are doing.

The only hope I can see for your data is if you had a separate home partition that you have your data on and a root partition that you installed over.

You should be able to mount any partitions that you have on the drive.

The command below will list all of your partitions.

$ /sbin/fdisk -l


If you see a partition you would like to mount the you can mount it.

e.g.

$ sudo mkdir /mnt/hda1   (make somewhere to mount to)
$ sudo mount /dev/hda1 /mnt/hda1

Then you can look at /mnt/hda1 and see what is there.

You can look at all the partitions and see if your data is there.

I can't remember what partitions the default ubuntu has I have separate home partition etc but I may have made them myself.

You may not be able to get the data back if there was only one ubunut partition for everything which may be the case.

Remember all important data should be backed up regularly as hard drives can and do die quite often.

---

### Post by xerox on 2007-04-05
"Anthony Irwin":

IT WORKS!! 

Now I can transfer all of my semi-important files to my pre-made hda1 (linux to windows transfer partition) and reinstall ubuntu! I'm RESCUED!

Thank you. :)

P.S. - If I can repay you in any way, (now I'm in deep debt to you), please let me know.

P.S.S. - Thanks. 

P.S.S.S. - Thank you.

=)

---

### Post by irwa82 on 2007-04-05
Hi,

Good to hear that you got your data back. Now make sure you burn it to cd so you won't loose it if the drive fails or what ever else may happen.

Learn as much as you can about linux and free software and promote it to others and help others with their questions if you want to do something in return for me.

---

