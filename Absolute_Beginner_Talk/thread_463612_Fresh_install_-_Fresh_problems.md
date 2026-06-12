---
title: "Fresh install - Fresh problems"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by linuxnovice on 2007-06-03
Hello,

Today I installed Kubuntu 7.04 Fiesty Fawn on my Laptop. Here are the specifications of my laptop:

Toshiba A105-S4284
100GB Hardisk
1GB memory
Windows XP Professional

I installed Kubuntu on a 25 GB partition. I reserved 2.5GB for root and 1.5GB for swap as the installation instructions said. Finally, for the rest of the space, I used mount point as /home.
I dont know whether if this is ok or not. Because when I left it blank, it said that I couldnt use the partition if I dont chose a mount point.

The problems that I have noticed till now are:

1) After my first login, I tried to restart and it says,

Xsession: warning: unable to write to /tmp: error

2) During my first login, there was no sound. The sound card on my laptop is RealTek audio for Toshiba.

3) I couldnt install any extensions for firefox. When I try to, it says that there is not enough space in the disk. I am assuming it is because I am not using root. But I do not know, how to use root to install the extensions.

4) When I open kate using terminal, I get a bunch of garbage after it saying that,
Failure: Couldnt open device...
..
...

I dont remember the the other stuff. I do not know why this happens.

5) I want to edit GRUB so that Xp is the default operating system. I used sudo to open the menu.lst and changed the it and tried to save it. But it said that either there is not enough space or I do not have proper access. But I used sudo...

I hope I have provided all the info needed to solve my problems. I have nearly 20GB of hardisk space on linux.
If any more info is required I would be happy to give, provided I can login into Kubuntu.

Thanks,
SS.

---

### Post by icechen1 on 2007-06-03
You should let at least 5gb to root because all the program you install(and firefox plugins) are installed to there.
for your last last question(about GRUB) see [http://ubuntuforums.org/showthread.php?t=462356&highlight=grub+windows+default](http://ubuntuforums.org/showthread.php?t=462356&highlight=grub+windows+default)

---

### Post by linuxnovice on 2007-06-03
Hello,

1) For the grub problem, I already did that. The problem is, I couldnt save it. I used sudo, but it still told me that I dont have proper access or that  I dont have enough space. 

2) Since I just installed Kubuntu, I dont mind doing it again as I dont have data in it. So is it better to reinstall it with 5GB or more in root?

3) The code you pasted, I am not sure what it is for....

Thanks,
SS.

---

### Post by BHelts on 2007-06-03
LoL.... the code is his signature.  at this point i'd either reinstall giving root 5-10GB depending on how many programs you will be installing, or download the GParted LiveCD and resize your / partition.
As far as the sound goes, i too have a toshiba laptop and I had to run through a how to, to get it to work, it's not too hard.  [Here's]("https://help.ubuntu.com/community/HdaIntelSoundHowto") the link.  best of luck.

---

### Post by icechen1 on 2007-06-03
> **linuxnovice said:**
> Hello,

1) For the grub problem, I already did that. The problem is, I couldnt save it. I used sudo, but it still told me that I dont have proper access or that  I dont have enough space. 

2) Since I just installed Kubuntu, I dont mind doing it again as I dont have data in it. So is it better to reinstall it with 5GB or more in root?

3) The code you pasted, I am not sure what it is for....

Thanks,
SS.
1)You might be out of space.See 2)
2)Yes(i use 19 gb for root)
3)That is my signature,it has nothing to do.

---

### Post by linuxnovice on 2007-06-03
I have a working copy of Partition magic on xp (dont ask me how i got it :)). Can I use that to allocate more space to root?

I still cant login into kubuntu. In the event I reinstall, is it ok to have my entire drive (apart from swap) to be root? I might be installing stuff like matlab and gazebo (a robot simulation software required for my research) etc.

---

### Post by icechen1 on 2007-06-03
> **linuxnovice said:**
> I have a working copy of Partition magic on xp (dont ask me how i got it :)). Can I use that to allocate more space to root?

I still cant login into kubuntu. In the event I reinstall, is it ok to have my entire drive (apart from swap) to be root? I might be installing stuff like matlab and gazebo (a robot simulation software required for my research) etc.

Yes,i think you can do it as i did the same thing to make my root partition from 10 gb to 19 gb.

---

### Post by linuxnovice on 2007-06-03
Ok,

I have decided to a reinstall (probably tomorrow, going to bed now). So I just need to know a few things first. 

I have 25GB to spare. So is it ok I have 1.5GB for swap and 20GB for root? 
What mount point should I select for the rest of the space? (Previously I selected /home, is that ok or should I select something else?)

Is it ok if I have the entire drive (excluding swap) to be root? I am afraid, I dont understand how this works. If someone could guide me through this partitioning task, it would be helpful. 

In windows, when you install any program, it normally gets installed in C:\Program Files. Is there a common folder like that in Kubuntu where all the software gets installed? 
 
Thanks,
SS

---

