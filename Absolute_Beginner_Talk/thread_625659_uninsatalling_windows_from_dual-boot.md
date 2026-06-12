---
title: "uninsatalling windows from dual-boot"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by crisdean on 2007-11-28
Hi all - I am totally new to Ubuntu.

I want to move to Ubuntu from Windows - mostly to get away from the tyrany of M.S!!

I have Ubuntu for non geeks (i.e me!) by Rickford Grant.
As am totaly new to Ubuntu but know windows well - I am tempted at first to set up  a dual boot Ubuntu/Windows for prestent till get used to Ubuntu (and hopefully find all is well). If it all goes well - then hope to remove windows. Unfortunately the book tells you how to install dual boot but I can not find anything on how to remove windows after you have tried the dual boot.

I am presuming it is either:

reinstalling Ubuntu to single install from disk (which appears would be a pain if you then lost all your old window docs etc had imported into Ubuntu)?

or

There is some way when you have Ubuntu installed, that you could remove windows from dual boot (i.e remove windows totally!) just from Ubuntu?

I realise that this is prob a simple answer from those out there with experience - but I am a total Ubuntu newbie

Any help would be gratefully recievded to help me escape from the M.S clutches! Your help would be a humaniterian action :)

---

### Post by Matthew Bartram on 2007-11-28
You can uninstall Windows simply by deleting or reformating its partition. Uninstall only differs from delete if something else has to know about it. So the only other thing you probably want to do is then tell GRUB that windows doesn't exist anymore (by editing /boot/grub/menu.lst) - if you don't do this your boot loader will think Windows is still there, but if you try and boot into Windows nothing will happen.

You can then format the old Windows partition to an EXT3 (or anything else that suits your fancy), and use it as extra space. Or install another OS on it.

One concern I have - can someone help here please? - I have a suspicion that the master boot record (or something related), which then points to GRUB on your ubuntu partition, is on the first partition (normally windows, if you have windows). If so, you'll probably need to re-set that up, which I think is fairly easy from an Ubuntu disk.
I would wait for someone to confirm this before reformatting your Windows partition!

---

### Post by Dr Small on 2007-11-28
I have never done it, then again, I don't have Windows, but you should be able to just delete the Windows partition and then resize the Ubuntu partiton to make it bigger, from the empty Windows partition. Then remove the Windows entry in Grub and everything should be good to go.

---

### Post by siciliancasanova on 2007-11-28
I just deleted, reformated and resized my current NTFS partition into my EXT3 /home partition.  Worked fine.

I suppose I should have read up or something before I just went ahead and did it but I've had no problems.

But the grub menu list was still there asking if I wanted to boot into Windows or Ubuntu and I hadn't had time to look up what to do yet.

Do we answer each others questions?

---

### Post by Dr Small on 2007-11-28
Sure :)
Run:
```
gksudo gedit /boot/grub/menu.lst
```

Go down to the bottom of the file and find your entry for booting Windows (it will start with title, and then the name of it.) Remove that entry, and save it, and reboot. Make sure it worked. If you did something wrong and can't boot, you can always pop in a livecd to correct the problem ;)

Dr Small

---

### Post by crisdean on 2007-11-28
thanks for eveeryone whio replied :-). Hope to be finished with Windows forver soon!!!

Farewell M.S - you will never willingly be part of my life any more -and hallo Ubuntu :-)))))

---

### Post by seantm on 2008-01-15
[SIZE="5"][FONT="Arial"][SIZE="4"]Hey all,

I have a similar issue related to a dual boot system but in my case what I want to do is RE-partioning the size of my Windoze XP partition-- downsize it actually --make it smaller. 

Is it possible for me to do this? If so how? any tips or advice would be greatly appreciated. 

tia!  -S. [/SIZE][/FONT][/SIZE]

---

### Post by BandD on 2008-01-15
> **seantm said:**
> [SIZE="5"][FONT="Arial"][SIZE="4"]Hey all,

I have a similar issue related to a dual boot system but in my case what I want to do is RE-partioning the size of my Windoze XP partition-- downsize it actually --make it smaller. 

Is it possible for me to do this? If so how? any tips or advice would be greatly appreciated. 

tia!  -S. [/SIZE][/FONT][/SIZE]

It is certianly possible.  The easiest way is to install gparted via synaptic (this is a very good GUI partitioning tool).  But first you will have to organize the data stored on your Windows partition, because it is scattered all about the partition at present.  One of the best tools I've found to do this from within Windows is JKDefrag. You can download it here: 

[http://www.kessels.com/JkDefrag/]("http://www.kessels.com/JkDefrag/") 

Run it with the -5 (force together) option.  And then you'll be ready to downsize the partition.

Go ahead and run Gparted from within Ubuntu and make sure your Windows partition is UNMOUNTED.  It's pretty intuitive and you can find the guides and screenshots you need here:  [http://gparted.sourceforge.net/index.php]("http://gparted.sourceforge.net/index.php")

Hope that helps!

---

### Post by seantm on 2008-01-16
Wow --that's great, I'll try it out----thanks so much!

---

### Post by JamesAG on 2008-01-16
I have done this with my laptop, dual booting windows / ubuntu.
Gparted went very smoothly. I was able to resize my NTFS partition without a problem, even with some scattered files. 
GParted is able to handle an NTFS partition that has some fragmentiation (Scattering)... I wouldn't recommend it for a highly fragmented drive. But running the windows defrag should work just fine. =)
Gparted acts quickly once you confirm, this is what you want to do.
I was kinda on edge about it, I do rely on alot of data on my windows partition. But I copied my data to a safe location, with the ability to rebuild the bootable partition in case of failure. But I've had no problems!

Good luck. And Always backup your stuff before doing something like this. You'll never know if something wrong happens (and everything is gone) :(

---

### Post by seantm on 2008-01-16
very reassuring.... Much appreciated... -will try -thanks again...

---

