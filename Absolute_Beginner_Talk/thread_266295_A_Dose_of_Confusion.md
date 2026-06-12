---
title: "A Dose of Confusion"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by Zibeon on 2006-09-27
I have a sata 200GB hdd and a 40GB hdd.
Problem is I installed ubuntu to my 200GB for testing, (as well as SuSe and Debian) so far ubuntu is working fine. But I need to uninstall ubuntu, and at the time i did not know about the fdisk cmd. So I tried to use Magic Partition which failed dismally and now my partition is more like:

|D:\|Native Linux                  |swap file|

Where D:\ is a NTFS formatted section.
And now in ubuntu when i use fdisk /dev/hda or sdc it returns an error, "Unable to Open hda" or "sdc" in the console and in recovery mode.

Another issue is that after installing debian The 200GB hdd has some how lost 70 GB of space](*,) , how? I have no clue. After installing SuSe and Ubuntu I now have 20Gb lost and Magic Partition won't pick it up as a 200GB but rather as an approx. 187GB hdd. Windows won't even Pick up the SATA hdd at all now :-?.

All i need to do is get back my full 200GB hdd and my 40GB hdd and install Windows to my 200GB hdd and Ubuntu to my 40GB.

Hope that helps, I will try answer any of your questions if you don't understand my predicament.

Thanks for your time.

~Zibeon

---

### Post by davmac on 2006-09-27
Hi Zibeon,

Have you tried gparted (within Ubuntu) to have a look at the state of your disk? You can install it with synaptic if you don't already have it. Fire it up and it gives you a good visual representation of the partitions on your disk and unused space. I suspect that if you';re having problems with fdisk, this won't work.

If ever I'm doing anything more than a quick look, I personally prefer to use Ranish from "The Ultimate Boot CD". You can download this (free) from [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) burn it to a disk, reboot. Select File system tools [f2] and then Ranish [f1]. This will allow you to delete and reallocate any partitions you no longer need and, if you want to get rid of grub or lilo, restore the MBR.

Obviously, before you start, you need to make sure that you've got a *working* backup of everything you care about.

Hope this helps,

Dave Mac

---

### Post by Zibeon on 2006-09-27
Thanks for the reply, I will give this a go when I get home. ;)

---

### Post by Zibeon on 2006-09-28
Well I have tried this. 
I used Ranish to "fill my 200GB with zeros" and formatted it in FAT32, which returned a total size of 195,000 mb which is accurate in as much as 200,000 / 1024 = 195GB.

I went into my 40GB hdd with windows installed on it (now ubuntu) and formatted it using the NTFS system and it registered 187GB free and 70MB used. This is fine with me, but in the Windows setup, When I create a "Raw Partition" as required, but this only returns me with ~ 131,000MB free.

I have also tryed using Free fdisk, yet it is still returning odd figures.

Anything else I can try? or answer?

---

### Post by podunk on 2006-09-28
I'm assuming that you've looked at your bootup screen and the drives are being detected properly? And that you've gone into your BIOS and checked stuff to make sure everything is what it should be.

Something you might want to try is visit the website for the maker of your hard drives. They will have a boot disk program that runs some advanced diagnostics and does a low level format.

---

### Post by Zibeon on 2006-09-28
The drives are detected yes, every thing is working properly, as far as detecting the hardware is concerned.

I have some screens of the process, I will try explain what I am doing along the way.

Here I have opened it in Ranish and doing a FAT 32, as I was hoping windows would reconise it.
[ATTACH]16503[/ATTACH]

It finished Formating with a clear ~195GB of space.

[ATTACH]16504[/ATTACH]

Now when I start up Windows XP I get 190GB of space.

[ATTACH]16505[/ATTACH]

But as soon as I delete the partition and recreate it as a "RAW" partition, The results are more confusing (for me :-? )

[ATTACH]16506[/ATTACH]

And EVEN after I do this, XP still refuses to install, complaining it is unreadable, or to that extent.

Here is a pic of the BIOS displaying the hard drive attributs.

[ATTACH]16507[/ATTACH]

I also tried enabling 32bit transfer, but no difference.

If i have over looked anything please tell me, Still new to the formation of drives, but I have a reasonable idea about what I am doing.

Really need to get this running soon.

Thanks for your time

[-o<

PS: This is a SATA 2 drive, but XP never had issues before :-?

---

### Post by gn2 on 2006-09-28
Is your XP disc pre service pack 1?

Perhaps you have encountered the upper Gb limit?

[http://support.microsoft.com/?scid=303013](http://support.microsoft.com/?scid=303013)

---

### Post by Zibeon on 2006-09-28
The XP is SP1, Thanks for the link it could be usefull.

But what i don't understand is this never happened before.

According to the link i will have to uninstall ubuntu and reinstall XP on the 40 hdd.

I will give that ago, and see if it helps, again, thanks for the link and fast response 8)

---

### Post by mongooseman1128 on 2006-09-28
gn2 is definitely right, that's a problem I see at my work all the time. (what's the difference between windows and virii? virii are written well.) Try running Gparted from the live CD, sometimes it will have better results. Also, on a side note, you might want to change your thread name. you'll get much better help and it's more helpful for other forum users if the name of threads are relevant to their subject.

---

### Post by Zibeon on 2006-09-28
True.

Just to clarify.

I wish to end up with:

-------------------
XP - 200GB SATAII
-------------------
Ubuntu - 38.5GB IDE
Swap - 1.5 GB IDE
-------------------

Thanks for all the support, I will go try the live Gparted. If that fails I will try Windows again, and start from squar one. 8-[

---

### Post by gn2 on 2006-09-28
I read somewhere that if you run an XP install disc backwards it plays the voice of satan?  Worse, if you play it forwards it installs XP!

Isn't it Ironic that help with XP is available here.

I've had a few XP issues fixed myself by reading this forum.

---

### Post by mongooseman1128 on 2006-09-28
HAHAHAHAHAHAHAHAHAHA the moment I read that I burst out laughing

---

### Post by Zibeon on 2006-09-29
So Ture, lol.

If only people made 3Dsmax and Photoshop and games compatible with linux, I would get rid of my XP completely, but i'm not paying so I win either way, I guess :twisted:

---

### Post by Zibeon on 2006-09-29
Well I have what I planned to get, had to reinstall windows, then use Gparted from the live CD, but now the problem is I can't (or don't know how) to boot Windows, the ubuntu GRUB loader isn't detecting it and it can't read the windows hdd in ubuntu it's self.
help... :-k

---

### Post by bulldog on 2006-09-29
Is windows on your **first ** bootdevice??

Windows wants to be ont it.
But you can fool windows by mapping your drives

Is there an entry in your menu.lst for your windows?

---

### Post by Zibeon on 2006-09-29
By Saying Windows on my first boot device. When i set the windows hdd to boot first in the BIOS it returns:

Please insert a media device and press any key.

or to that extent.

I'm still new to linux (always wanted to use it), so could you explain how to map the drives.

Thanks

PS: I don't have internet on my PC, i am running off a secondary PC.

---

### Post by bulldog on 2006-09-29
To map your windows you have to alter your menu.lst.

You get it by typing in your terminal ```
gksudo gedit /boot/grub/menu.lst 
```

You have to alter your windows section like this ```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by Zibeon on 2006-09-30
Okay, I just found out that when I try to install Windows 
(Btw, the ubuntu didn't start up last night, stopped at configuring network)

even if i format in ntfs, although I can "keep existing file system"
It doesn't really install XP properly. 
But i know how you said i need to enable 48 bit transfer, How will that help if windows isn't even installed? Or do I have to do this after I installed to a ||130 GB [ntfs]||70GB [unallocated]|| harddrive and it will suddenly realise I have extra space?

I do have a SP1 XP cd though.

This is really odd that this has never happened to me before I messed with linux. Could the drive be damaged from the formatting and re-formatting?

I really don't know what to do now :(

Atm I just have two hdd's with primary ext3 partitions.

(XP is really annoying me now!, why can't it just be nice and simple like linux!)

---

### Post by Zibeon on 2006-10-02
Nvm, I solved it, by just installing windows to the 130 GB hdd, and once installed it reads it as 190GB, so thats all good.

Thanks for the help and quick responses :D

---

