---
title: "Can I bless a partition without OS X install disc?"
date: 2009-03-14
forum: Apple Hardware Users
---

### Post by perpetualcacophany on 2009-03-14
Alright,
So, I just repartitioned my MacBook 4.1 to have a separate home partition. In doing so my Linux boot option doesn't show in rEFIt. I've re-done the partition tables on the rEFIt menu, but that did not bring up a bootable drive. It does bring up an option other than OS X, but I'm pretty sure that it's my "home" partition.

I am currently away from where my OS X install cd is, so I can't use it to bless my Ubuntu partition (I'm fairly certain that this is what I need to do because I also moved everything around when I repartitioned). I won't have access to my OS X cd for another week, so I was wondering if there is a way to bless the partition without using the cd (maybe something in the OS X terminal). I can still access OS X, so it is not absolutely essential, but I would prefer to be in Ubuntu.

Any help would be appreciated. Thank You.

---

### Post by sunbird on 2009-03-14
I don't think it's possible to do this. You need that OS X install disk. 

But, just to be clear, when you rebless, you need to bless your rEFIt install folder location, which is most likely on your OS X drive. Probably what happened is that you created a new partition before the OS X partition, so the blesser is looking in your home partition for the rEFIt folder. 

Blessing your ubuntu install location won't help at all because the rEFIt install folder isn't there and, even if it was, mac firmware can't read ext3.

---

### Post by cyberdork33 on 2009-03-15
> **perpetualcacophany said:**
> I was wondering if there is a way to bless the partition without using the cd (maybe something in the OS X terminal). 

yes, the only reason that you boot the OSX cd is to get an OSX terminal. If you have an installed OSX system already, then you can use the terminal there.

> **sunbird said:**
> But, just to be clear, when you rebless, you need to bless your rEFIt install folder location, which is most likely on your OS X drive. Probably what happened is that you created a new partition before the OS X partition, so the blesser is looking in your home partition for the rEFIt folder. 

Blessing your ubuntu install location won't help at all because the rEFIt install folder isn't there and, even if it was, mac firmware can't read ext3.
You can bless your Linux partition (and the filesystem doesn't matter), but if you are using rEFIt and dual-booting with OSX, there is no need to bless the linux partition anyway. It sounds like you may need to reinstall grub to your Linux root partition.

[http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11)

---

### Post by mplinux on 2009-03-16
Ck this out: I'm having an issue with dual boot....While booting I'm not going directly into the ubuntu 8.10 login screen after selecting the Ubuntu Partition on my dual boot system. It takes me to a command prompt and I have to enter > [QUOTE]```
Linux nosplash
```[/QUOTE] and hit enter and then it takes me to login screen. Any work around that? I found on a forum that I should go to terminal and enter the following command: ```
sudo nano /etc/yaboot/conf
```
and replace ```
append"=quiet splash"
``` with ```
append"=video=ofonly nosplash"
```

Here's the catch: when I enter ```
sudo nano /etc/yaboot/conf 
```it opens a window, but its blank where is all the script? 

any tips will be of great help! I'm a newbie on a mission to get my PPC G4 running on ubuntu 8.10. Help!

---

### Post by cyberdork33 on 2009-03-16
> **mplinux said:**
> Ck this out: I'm having an issue with dual boot....While booting I'm not going directly into the ubuntu 8.10 login screen after selecting the Ubuntu Partition on my dual boot system. It takes me to a command prompt and I have to enter  and hit enter and then it takes me to login screen. Any work around that? I found on a forum that I should go to terminal and enter the following command: ```
sudo nano /etc/yaboot/conf
```and replace ```
append"=quiet splash"
``` with ```
append"=video=ofonly nosplash"
```Here's the catch: when I enter ```
sudo nano /etc/yaboot/conf 
```it opens a window, but its blank where is all the script? 

any tips will be of great help! I'm a newbie on a mission to get my PPC G4 running on ubuntu 8.10. Help!
you are dealing with a powerpc mac, the others in this thread have an Intel Mac. They are very different in how they startup.

---

