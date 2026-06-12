---
title: "Dual-Boot to windows xp"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by eiknarf05 on 2007-07-20
I made the switch to Ubuntu 7.04. But it wasn't easy... :popcorn:


I bought my dell xps 400 about a year ago and its been working fine (meaning no crashes). The past month I've been experiencing problems with windows. I also have been pondering about the move to linux. I think my XP picked up on that.

I was getting ready to create a partition for Ubuntu by degragging but Windows XP said NO! and gave me a blue screen of death. So I try installing different dragging software to get all my space to oneside but again, windows wouldn't have it. I could actually time when the blue screen showed when i defragged. I finally said F** it and ran ubuntu live cd and wipped out my entire HDD for linux. (It was satisfactory at this point). 

But now it seems I could my windows back :mad: . My wife has vista on her laptop but she gets frustrated with it and wants my comp to have XP again. I wouldn't mind it either (certain software). I have to make a partition for windows and be able to dual-boot to it. Here are my questions:

1) When I use gparted to do so, do I have to use NTFS format for windows or could i use FAT32? so my ubuntu could play on that side.

2) After the partition (hope it works) do i just pop my windows CD in and point it to my new partition, install as normal?

3) Any advice for me?


Thanks in advanced.

---

### Post by Frak on 2007-07-20
1) Install the [Linux-Driver]("http://www.fs-driver.org/") for Windows that lets you write to Linux Partitions, and the NTFS-3G driver for Linux that lets you write to Windows Partitions.

2) Partitioning in Ubuntu is completely automatic, it will configure the boot loader to do it for you

3) Everything is automatic, it will give you a slider bar to select how much of the drive you want to give to Ubuntu to use.

---

### Post by jimbob on 2007-07-20
1)  Yes you can use FAT32 ( I believe ex pee will give you the choice).

2)  You may have a problem with the ex pee installation because it wants to be the first partition on the HD.  I think it will call your Ubuntu partition C: and the new partition where it will install itself D:   The install will work just fine but you could run into conflicts down the road when installing other apps that want to go on C:
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by eiknarf05 on 2007-07-20
Thanks so much, Will have to get to it once I get home. Will be back if any problems arise. 

I've heard many good things about this forum and so far I feel its all true! Glad to be apart of the community.

---

### Post by Frak on 2007-07-20
Oh, my bad, I thought you were installing Ubuntu instead of XP.
You ever think of [Seamless Virtualization]("http://ace2016.net/tutorials/linux/run-windows-xp-applications-seamlessly-on-your-linux-desktop").

---

### Post by eiknarf05 on 2007-07-20
I tried a virtual box before and it was very choppy and slow. I installed it on windows xp to try out ubuntu.

I also wanted to try Wine. I downloaded it but have yet to see it work. Kinda confused about it. Is it a emulator like software? or does it run in the background? How do you install .exe apps?

---

### Post by Frak on 2007-07-20
First of all Wine is a recursive acronym, meaning, WINE IS NOT an EMULATOR, it is a compatability layer that converts Windows System32 System calls, into Linux/Unix System calls.
To install a .exe app, just double click it, sometimes it will work, sometimes it'll kinda work, and sometimes it'll miserably fail.

---

