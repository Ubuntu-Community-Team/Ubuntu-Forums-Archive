---
title: "many questions! includes virtual windows, beryl, hdd, widescreen"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by stonecold23 on 2007-04-25
1. still cant get widescreen res have tried the things suggested like manually entering 1440 x 900 res in xorg or whatever but it was already there!

2. run virtual windows? how is this done. and how simple is it if i already have windows installed?

2.5 is virtual windows going to be alot slower than normal windows???
system spec
amd 4600 x2
msi nforce 570 
3gb ddr 2 ram (2gb hasnt arived in post yet)
7600gt xxx 256

3. mount windows hdd automatically at start up

4. beryl worked first time on my first install!!! i didnt break it... now how do i get a background manager that supports view ports and how do i change the the desktop from loading the ubuntu gnome desktop and instead automatically load beryl?

thanks in advance if you can help

would like to also say thanks to all the people who have helped me so far in my first few cups of ubuntu

---

### Post by dfreer on 2007-04-25
1. what's the original thread link?

2. You can use vmware, QEmu, virtualbox (vmware player or server is prolly the best, and free too!):
[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

It is almost always eaisest and best to install windows fresh using one of these programs, here's a thread about wanting to use an existing windows partition:
[http://ubuntuforums.org/showthread.php?t=388426](http://ubuntuforums.org/showthread.php?t=388426)

3. if you run the virtual XP from the same HD as ubuntu, you'll encounter speed issues due to both OS's making multiple I/O requests. Best to run it from a second HD, and it should run decently fast with your system specs (is that a dual core? should run amazingly well). Note that 3D gaming is prolly not going to happen with a virtual machine.

4. if you have beryl-manager installed, go to System > Preferences > Session and add the command beryl-manager to startup.

---

### Post by bobbocanfly on 2007-04-25
To get Beryl / other apps running at startup i created startup.sh in my home folder then told the Sessions GUI to load the script at startup, works perfectly for me.....

Code to mount the HDD and run beryl

```
sleep 1s; beryl-manager
mount -t ntfs /dev/<whatever partition its> /mnt/<destination mount point>
```

---

### Post by stonecold23 on 2007-04-25
ok thanks. will try that and yes it is dual core but needs overclocking i think. not making the most of my arctic freezer pro. i think cpu is currentlu 3 degrees above room temp at 0.2 ghz overclock

i was asking bout the virtual windows because i wanted to play games on linux. and frankly for a beginner linux is very hard to use. wouldnt mind so much if it was different code. but its unix which i know nothing about. and obviously the filing system is the main problem for people switching over from windows. as everything is different.

so please tell me there are people out there who have a different oppinion about playing gamis in a virtual xp!
and sadly both os are on the same drive. and i'm not changing that! i dont even want to think about being that nerdy. its on the drive and it goes! so no fiddling!

---

### Post by igknighted on 2007-04-25
> **stonecold23 said:**
> ok thanks. will try that and yes it is dual core but needs overclocking i think. not making the most of my arctic freezer pro. i think cpu is currentlu 3 degrees above room temp at 0.2 ghz overclock

i was asking bout the virtual windows because i wanted to play games on linux. and frankly for a beginner linux is very hard to use. wouldnt mind so much if it was different code. but its unix which i know nothing about. and obviously the filing system is the main problem for people switching over from windows. as everything is different.

so please tell me there are people out there who have a different oppinion about playing gamis in a virtual xp!
and sadly both os are on the same drive. and i'm not changing that! i dont even want to think about being that nerdy. its on the drive and it goes! so no fiddling!

Well, be aware that virtual machines cannot have 3d.  This is because all the current virtualization software creates "fake" hardware and shows it to the client OS, and this fake graphics card has no 3d.  It cannot give access to your true graphics card.

Also, for gaming on linux there are many choices.  Check out Sauerbraten, Open Arena, Alien Arena, America's Army, Unreal Tournament, all the quake titles, and many more.  Most of those are available for free, just search in synaptic or google.  Also to run some windows games in linux, look into wine or Cedega.  Cedega costs $15 but is well worth it.

---

### Post by stonecold23 on 2007-04-27
ok thanks
i have quake 4 for windows already does this mean i can just install it on linux?

---

