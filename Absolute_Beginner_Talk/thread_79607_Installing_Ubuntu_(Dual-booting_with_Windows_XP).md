---
title: "Installing Ubuntu (Dual-booting with Windows XP)"
date: 2005-10-20
forum: Absolute Beginner Talk
---

### Post by tarun88 on 2005-10-20
> You can also set up a dual-boot whereby you can choose whether to boot into Windows or Ubuntu.
I have Windows XP installed on c: (40 GB, NTFS). d: (20GB FAT32) and e: (20GB FAT32) are empty and I want to install Ubuntu 5.04 on one of them without formatting my entire HD.

Ubuntu Setup lost me after the part where you select that you want to manually configure your partitions. I was told I would need to get GRUB to do this. All I know is that GRUB is an alternate boot-loader. 

Can you please point me to a guide to installing Ubuntu on another partition while retaining Windows XP?

**This** guide [here]("https://wiki.ubuntu.com/WindowsDualBootHowTo") (Wiki) doesnt mention GRUB. Is this all I need?

Thanks in advance

---

### Post by Kapre on 2005-10-20
[QUOTE=tarun88]I have Windows XP installed on c: (40 GB, NTFS). d: (20GB FAT32) and e: (20GB FAT32) are empty and I want to install Ubuntu 5.04 on one of them without formatting my entire HD.[/quote]

Are the above mentioned sizes disks or partitions? if they are partitions, you just select one of them where you'd like to install Ubuntu and you're done.

> Ubuntu Setup lost me after the part where you select that you want to manually configure your partitions. I was told I would need to get GRUB to do this. All I know is that GRUB is an alternate boot-loader. 
GRUB will not ask you tell you to partition the drive, it is asking you where (what partition) you want it installed. If your dual booting with XP, I would suggest to place GRUB in the MBR.

> Can you please point me to a guide to installing Ubuntu on another partition while retaining Windows XP?

I would recommend you reading the threads below before you dwelve into Ubuntu. The guide is on my signature below.

[Linux desktop]("http://www.psychocats.net/essays/linuxdesktop.php")
[Whining & Weeping]("http://www.ubuntuforums.org/showthread.php?t=78741")

---

### Post by Shiner on 2005-10-20
Yes... DO read other posts / guides before trying to dual boot with XP.
 
I installed Breezy last Sunday evening, hoping to dual-boot with XP..... Wednesday night I finally gave up and reinstalled XP.
 
Putting Grub in the MBR is what started the problems.  I was able to boot into XP ONE time before my 'puter began an endless boot cycle.
 
I tried using my XP cd to 'fixmbr' via Recovery console, but I could not, for the life of me, remember my administrator password.
 
So, I reinstalled XP and, for now at least, will install Breezy on another 'puter. Or... maybe.... reinstall on a separate disk, leaving the windows disk unplugged when running it.  Hmmmm.....

---

### Post by tarun88 on 2005-10-20
Thanks Shiner, will do my homework.

Kapre, you can rest assured that I will not take up your time by whining. Thanks for your help, sorry for any inconvenience caused - I get the message, I will bugger off until I know more about Ubuntu.

---

### Post by Herman on 2005-10-20
Tarun88, just have a read of my signature link first and see if that answers some of your questions. (Don't go away mad.) You will find illustrated examples of most of the things you want to know.
I think dual booting with Windows is the way to go, and normally, installing GRUB on the MBR works fine for most people. (You'll know what I mean when you look at the link).
If you are one of the unlucky few who have trouble with it, there are ways of fixing it, and the newest is something called 'GAG', which might be pretty good if GRUB doesn't 'do it for you'.
Just make sure you back up all your data first, of course, and defrag too.
If you are really scared, just take the precaution of having a Windows boot disk handy too, like ' boot98c_seoem.exe ', which you should be able to download for free from somewhere and make a boot floppy out of to have ready just in case. I doubt if you'll need it though. (Herman).

---

### Post by paddyg on 2005-10-20
If still interested in dual booting my advice is:

1. prepare the linux swap (about 2 times your ram) and ext3 partitions by using Windows Partition Magic (extended instead of primary will be ok)

2. get familiar (if you are not) with linux way of naming disks and partitions (when you install ubuntu you'll also need a mount point to attach to the linux partition: / , which the sys root)

3. always install Grub (you're right it's a bootloader) in the MBR, so it will detect other os and let it boot. Grub is very tolerant...

4. I don't think the WIKi guide is enough to boost confidence. Try something else on the net

---

### Post by Kapre on 2005-10-20
[QUOTE=tarun88]Thanks Shiner, will do my homework.

Kapre, you can rest assured that I will not take up your time by whining. Thanks for your help, sorry for any inconvenience caused - I get the message, I will bugger off until I know more about Ubuntu.[/QUOTE]

tarun88 - Don't get me wrong. Reason we are all here is to help. I just placed all the threads so that you'll know if what you're getting into is really good for you. Guess you've interpreted it on different way. :eek: 

K

---

### Post by tarun88 on 2005-10-21
Thanks Herman, the link in your sig makes it easy as pie. Thanks paddyg, I can always format and reinstall XP if something goes wrong.

Sorry if I misunderstood you Kapre, I guess I have my share of not-so-good days... its all good. Its just that I wouldn't even consider blaming either Ubuntu Linux or someone else for any sorrt of misguidance when I *choose* to try Ubuntu.

Thanks again.

---

### Post by matthewv on 2005-10-21
I always find, when dual booting with grub or lilo, the safest way to go is to install the bootloader to floppy disk. Boot off floppy --> linux; remove floppy --> windows

---

### Post by Herman on 2005-10-21
mattewv,  I like that idea too, it would save some greif for quite a lot of people, they could install GRUB to a floppy first, and then have the option of installing ot to their MBR if they decide to and when they're ready for it. I have experimented with this myself, actually, from reading some of your suggestions (links) in other threads. (Thanks!).
For me anyway, having GRUB on a floppy works fine, and I love the idea. But I'd like to be able to duplicate the floppy disk so I have back-up copies of that floppy, or better yet, copy GRUB to a CD, as floppy disks are not as reliable as a CD and might get corrupted or become unuseable. (Coffee spilled on them, placed too close to a magnet, left under a hot window, dust ,etc.)
 I have tried to make duplicates of my GRUB floppy, but either I don't know how yet, or my computer won't do it. Any suggestions?
I have also been trying to get GRUB on a CD, it's supposed to be possible, but so far I haven't been able to get it to work. Check thread below:
[http://ubuntuforums.org/showthread.php?t=78119&highlight=%28Herman%29](http://ubuntuforums.org/showthread.php?t=78119&highlight=%28Herman%29)
 The best I've been able to do so far is try out this new 'GAG' thing that isander suggested:
[http://ubuntuforums.org/showthread.php?t=79286&highlight=%28Herman%29](http://ubuntuforums.org/showthread.php?t=79286&highlight=%28Herman%29)
What do you think about it?    Regards, (Herman).

---

