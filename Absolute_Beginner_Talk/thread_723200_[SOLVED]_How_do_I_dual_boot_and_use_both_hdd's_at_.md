---
title: "[SOLVED] How do I dual boot and use both hdd's at same time"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by iiDopDop!! on 2008-03-13
Hey i ahve successfully installed ubuntu on one HDD and have been using it for like a year or 2 now but i have an mp3 player that will only seem to work on window. so i installed windows on my other harddrive and configured the grub and its all hunky dory... sort of al i need now is to be able to access my ubuntu drive while i am using windows so i can access music. Or be able to transfer the music from my ubuntu onto the windows one and have music on both drives. 




any help appreciated Thx

---

### Post by taurus on 2008-03-13
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by MegaJim on 2008-03-13
You can do it a variety of ways.  There are drivers for various linux filesystems that run under windows, as there are drivers for the windows filesystems under linux.  However most people (Including myself) seem to favour letting each operating system handle its own affairs and instead keep user files on a neutral partition (usually NTFS) for sharing common data between the systems.

---

### Post by Oldsoldier2003 on 2008-03-13
> **MegaJim said:**
> You can do it a variety of ways.  There are drivers for various linux filesystems that run under windows, as there are drivers for the windows filesystems under linux.  However most people (Including myself) seem to favour letting each operating system handle its own affairs and instead keep user files on a neutral partition (usually NTFS) for sharing common data between the systems.
Agreed a shared NTFS partition for data is the best solution in my opinion because it keeps you from having to use windows drivers to wirte to your ext2/3 partitions. I just dont trust the stability of winodws enough to allow it to write to my linux partitions. Better safe than sorry!

---

### Post by SpenceMakesSense on 2008-03-13
Well I know its possible to access NTFS drive from Ubuntu. One problem I ran into though is that if you dont let Windows shut down completely(as in sitting there as it just down as apposed to just holding the shutdown button down or un plugging it) then Ubuntu will be un able to Mount it. But I've yet to be able to access my Ubuntu drive using Windows.

---

### Post by cotcot on 2008-03-13
Be aware that the fs-driver deals with an ext3 partition as if it is an ext2. So you will not have the journaling of the filesystem. Here is a quote that explains journaling fs :
> Journaling results in massively reduced time spent recovering a filesystem after a crash, and is therefore in high demand in environments where high availability is important, not only to improve recovery times on single machines but also to allow a crashed machine's filesystem to be recovered on another machine when we have a cluster of nodes with a shared disk.

---

### Post by Oldsoldier2003 on 2008-03-13
> **SpenceMakesSense said:**
> Well I know its possible to access NTFS drive from Ubuntu. One problem I ran into though is that if you dont let Windows shut down completely(as in sitting there as it just down as apposed to just holding the shutdown button down or un plugging it) then Ubuntu will be un able to Mount it. But I've yet to be able to access my Ubuntu drive using Windows.

If you restart windows and cleanly exit the drive will be able to be mounted again under Ubuntu. as far as writing to your linux partitions from windows... it requires you install  special drivers. But the opinion of many is that even though these drivers work, the windows implementation of them isn't stable enough to trust for critical data.

---

### Post by garyed on 2008-03-13
> **iiDopDop!! said:**
> ..... Or be able to transfer the music from my ubuntu onto the windows one and have music on both drives. 

any help appreciated Thx

Do you have your windows drive mounted in Ubuntu? 
Maybe I'm misunderstanding you but couldn't you boot into Ubuntu & transfer  your music through the filesystem back to your Windows drive easily or is that not what you're wanting to do?

---

### Post by brennydoogles on 2008-03-13
> **Oldsoldier2003 said:**
> If you restart windows and cleanly exit the drive will be able to be mounted again under Ubuntu. as far as writing to your linux partitions from windows... it requires you install  special drivers. But the opinion of many is that even though these drivers work, the windows implementation of them isn't stable enough to trust for critical data.

I used those drivers in woindows, and every time I mounted one of my drives from Windows, it would create random files (named with random numbers and letters) all over my Linux partitions. I ended up having to reinstall to get rid of them.

I recommend using ntfs-config and ntfsprogs from the repositories to allow read/write to your windows partition. When you are done, you can run (I think it's called) ntfs-clean from the ntfsprogs package, and it will clean your Windows drive so that Windows doesn't think it is corrupted the next time you boot into it. Hope that helps!

---

### Post by rockinlinux on 2008-03-13
i agree, a seperate ntfs partition is the only way to fly. what kind of mp3 player do you have? ahve you tried to run it in virtualbox?

---

### Post by iiDopDop!! on 2008-03-14
I have 2 HDD's not partitions. One HDD (my main one with all the music, documents etc.....) wich is the ubuntu one. and the Second HDD wich is a windows XP HDD i installed it last night got barely anything on it... i was wondering hopw do i access the windows drive while using ubuntu and vise versa.....  Just to clarify my problem/......

---

