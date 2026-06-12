---
title: "Will Ubuntu auto discover new hardware"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by cdbillups on 2007-09-19
My machine is on it's way out.  When I get another machine, can I just move my hard drive over to it?  Will Ubuntu auto detect the new machine's hardware?  Should I just plan on installing it fresh on the new machine?

---

### Post by tszanon on 2007-09-19
> **cdbillups said:**
> My machine is on it's way out.  When I get another machine, can I just move my hard drive over to it?  Will Ubuntu auto detect the new machine's hardware?  Should I just plan on installing it fresh on the new machine?
I don't know if it will discover new hardware automatically, nor how would you do it manually.
But I would reinstall it. If you have a seperate /home, then it's even easier.

---

### Post by LaRoza on 2007-09-19
Do a fresh install.

---

### Post by FuturePilot on 2007-09-19
Do a fresh install. The install on your old computer was configured specifically for that computer and that computer only. If you try to move the hard drive to another computer it will kernel panic and not boot.

---

### Post by zero244 on 2007-09-19
I agree a fresh install and like one poster mentioned this time setup a separate partition for your home folder, because you dont have to format your home partition. So if you have your music etc stored there you dont lose it.
Also it makes setting up a fresh install much easier.
Good luck

---

### Post by tszanon on 2007-09-19
> **FuturePilot said:**
> If you try to move the hard drive to another computer it will kernel panic and not boot.
I never thought that it would be that bad...

---

### Post by cdbillups on 2007-09-19
Thanks for the input.  The computer I'm looking at will have at least a 40gb drive in it.  I'll just reinstall on that and then move my old hdd over for storage.

---

### Post by david on 2007-09-19
I disagree with previous posts, you don't really need a fresh install, Ubuntu will autodetect most of your hardware, at least it worked for me two months ago when upgraded everything but the drive. The only trouble is X which you probably need to reconfigure if you have a new video card. 

Of course, if you just wait for Gutsy and upgrade before you do the switch  even that won't be a problem, since it has [*BulletProofX*]("https://wiki.ubuntu.com/BulletProofX")

---

### Post by cdbillups on 2007-09-21
The machine I'm getting is one of our old ones from work.  I looked and it also has an Nvidia video card like my current machine.  Knowing that, I'm hoping everything will go smoothly with just putting my drive in the new machine.

---

### Post by MrHippocampus on 2007-09-21
> If you try to move the hard drive to another computer it will kernel panic and not boot.
Admittedly it can, but it would be very rare, the livecd happily boots on the majority of systems without a panic. That would be true for a stripped down customised kernel but not a generic one like ubuntu. 

The only problem with simply moving the hard drive is that the device node of the hard drive may change, which means although the kernel may boot, it wont be able to find your ubuntu install. (im not sure if UUID's of partitions solve this problem)

In theory if you moved the hard drive, then booted a livecd and changed problems (if any) with the existing /etc/fstab to reflect the new settings it should work.

Regardless of that though, you should probably just go for gutsy.

---

### Post by frodon on 2007-09-21
> **MrHippocampus said:**
> The only problem with simply moving the hard drive is that the device node of the hard drive may change, which means although the kernel may boot, it wont be able to find your ubuntu install. (im not sure if UUID's of partitions solve this problem)It is made for this purpose :KS, so if your fstab use UUID your new system will recognize your partitions without any problem as the UUID won't change.

You can try it as it will work except in case of unrecognized new hardware, ubuntu will detect new hardware and will use the right drivers if they are installed. One thing you will surely need is a "sudo dpkg-reconfigure xserver-xorg" as i guess your graphic card will be different and may use other drivers.
Except the display reconfiguration i would say that if your hardware is compatible _**it should work.**_

---

### Post by C.S.Cameron on 2007-09-21
I am running Ubuntu from a 8G thumbdrive, It works on different computers.
No reason a hard drive shouldn't work either.
Ubuntu is not locked to a single processor like windows.
Might have to reinstall video drivers if the cards are different.

---

### Post by cdbillups on 2007-09-21
As best as I can tell it all went okay.  I had used Envy previously to install my Nvidia drivers.  I simply uninstalled / reinstalled with Envy and it reconfigured everything for me.  The only thing I noticed is that I had to set my ethernet card back to static.  Everything else looks a-ok so far.  Thanks for all the input!  I love this place!

---

