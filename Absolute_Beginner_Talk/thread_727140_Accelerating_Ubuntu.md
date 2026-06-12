---
title: "Accelerating Ubuntu?"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by R2Khimself on 2008-03-17
Hey all! Another noob to Ubuntu, here.  I am just wondering if there is any way I can speed up the system without purchasing any external hardware. I heard that there are a couple apps that constantly run when booting and that you can turn those off.  Any ideas?  Thanks for the ideas.

---

### Post by NightwishFan on 2008-03-17
There is not too much optimization possible. I would advise if you want more speed to try Xubuntu or Fluxbuntu. There are a few threads about this you can search for.

---

### Post by staticvoid on 2008-03-17
And even if you are a noob you should check out Archlinux, it is FAST.

Starts out in cli, a little dark and spooky... but if you have the wiki open and an irc in the #archlinux channel, you should survive :)

you get the fastest cutting edge software around..

to keep this ubuntu though, yes, do try fluxbuntu. +1

sv

---

### Post by linuxtoindia on 2008-03-17
FAST LINUX?
TAKE YOUR CPU IN HAND AND RUN AS FAST AS YOU CAN!:lolflag:

---

### Post by NightwishFan on 2008-03-17
What a first post! Welcome to Ubuntu Forums. =D

---

### Post by finferflu on 2008-03-17
I'm not using Ubuntu right now, but as far as I can tell, there is a desktop search engine enabled by default (either tracker or beagle). If you turn that off, you should notice some improvement. Also, you can use htop (sudo apt-get install htop) to see which process is eating RAM and CPU, then try to suppress it :P

Please correct me if I said something wrong about the desktop search engine.

---

### Post by AnRa on 2008-03-17
You should disable Tracker.

---

### Post by kryth on 2008-03-17
hmm....maybe install preload
> sudo apt-get install preload
it will start things faster.
OpenOffice starts in about 3-4 seconds for me. 
I think that's the right command but i may be wrong.

---

### Post by R2Khimself on 2008-03-17
Thanks for the advice everyone!

---

### Post by NightwishFan on 2008-03-17
You need like 1gb of ram for preload otherwise you can choke your ram, (think vista)

---

### Post by sayakb on 2008-03-17
+1 to preload
Plus, you might disable compiz to speed things up
Also, disable Picture/Sound file previews under Nautilus settings

If you go for XFCE or fluxbox, rather than going for a clean install, just install the corresponding desktop environment via Synaptic.. You would get XFCE plus you wont have to reinstall your currently installed packages.

---

### Post by AlanR8 on 2008-03-17
Totally agree about Preload! Have been using for over a yea now and NO problems. 

I have an old desktop 1.6 Mhz P4 with a GIG of RAM, and this Laptop, Sony VAIO FZ21S with 2 GIGS of RAM and Preload works a treat. OO opens in 4 seconds. I don't use Dolphin (Kubuntu user) rather Konqueror and all is fast.

---

### Post by sayakb on 2008-03-17
Yes, but it is absolutely true that we need atleast a GiG of RAM for preload.. I have seen 512MiB RAM PCs showing unconventionally high RAM usage because of preload.

---

### Post by timzak on 2008-03-17
To speed up hard disk accesses, partition your disks like so:
1st partition=swap (1 GB should be plenty; I've never seen more than 50 MB used w/2GB RAM)
2nd partition=root (8 GB works well for me, I still have 5 GB free)
3rd partition=home (as much as you want/need)

There are two reasons why this partitioning strategy yields noticeable improvements.
1) hard disk transfer speeds are fastest at the beginning of the disk, and slow down as you move out to the end of the disk.  Thus, keeping your swap and root on the fastest portion of your disk ensures maximum transfers for the files that are most used.
2) The more sequential your seeks are, the faster performance is (random seeks all over the drive are slowest, which is why you don't want to put your swap as the last partition on your hard disk).  Since the swap and root are right next to each other (home also very close too), you are minimizing the hard disk actuator arm travel, which reduces seek times.

You probably won't notice a huge difference, but it will definitely make some difference, and you'll have peace of mind that your setup is very efficient.  The best part is this is it is completely independent of which distro you run.

I don't know if anyone else mentioned, but go through Sessions and Services and disable any apps/services you are sure you don't need or want running.  This frees up resource space and RAM for what you do want to run.

Good luck!

---

### Post by Redptc on 2008-03-17
Is it sufficient to disable things like 'Tracker' in the Sessions table? There are a couple of things I have disabled that I never use.

---

### Post by tad1073 on 2008-03-17
> **timzak said:**
> To speed up hard disk accesses, partition your disks like so:
1st partition=swap (1 GB should be plenty; I've never seen more than 50 MB used w/2GB RAM)
2nd partition=root (8 GB works well for me, I still have 5 GB free)
3rd partition=home (as much as you want/need)

There are two reasons why this partitioning strategy yields noticeable improvements.
1) hard disk transfer speeds are fastest at the beginning of the disk, and slow down as you move out to the end of the disk.  Thus, keeping your swap and root on the fastest portion of your disk ensures maximum transfers for the files that are most used.
2) The more sequential your seeks are, the faster performance is (random seeks all over the drive are slowest, which is why you don't want to put your swap as the last partition on your hard disk).  Since the swap and root are right next to each other (home also very close too), you are minimizing the hard disk actuator arm travel, which reduces seek times.

You probably won't notice a huge difference, but it will definitely make some difference, and you'll have peace of mind that your setup is very efficient.  The best part is this is it is completely independent of which distro you run.

I don't know if anyone else mentioned, but go through Sessions and Services and disable any apps/services you are sure you don't need or want running.  This frees up resource space and RAM for what you do want to run.

Good luck!

Putting swap in front of root won't effect the boot process?

Here is what I have:
sda1/root
sda2/swap
sdb1/home
sdc1/media
so, if I chane it to:
sda1/swap
sda2/root

I will still be able to boot?

---

### Post by jken146 on 2008-03-17
> **tad1073 said:**
> Putting swap in front of root won't effect the boot process?

Here is what I have:
sda1/root
sda2/swap
sdb1/home
sdc1/media
so, if I chane it to:
sda1/swap
sda2/root

I will still be able to boot?

Yes, as long as you reinstall GRUB after making the change.

---

### Post by tad1073 on 2008-03-17
That is too much of a chore, I think I will just leave well enough alone. Besides, I plan on getting 2gb of ram soon.

---

### Post by timzak on 2008-03-18
> **tad1073 said:**
> That is too much of a chore, I think I will just leave well enough alone. Besides, I plan on getting 2gb of ram soon.

Yeah, not worth the trouble.  I set mine up when I installed Ubuntu.  Your placement of swap between root and home is just fine.  I think the only case where I'd go through the trouble is if swap was placed clear at the end of the disk.

---

