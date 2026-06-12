---
title: "Mounting my iPod"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by tylerjroach on 2007-06-06
I am on a fresh install of Ubuntu Feisty and when I plug in my iPod it recognizes it but an error message comes up saying Cannot Mount Volume. You are not privileged to mount ipod. How can i run this through the command line to get permission to mount it. Please help. thanks.

---

### Post by Ek0nomik on 2007-06-06
Where is the device mounted?

This should help you find out:

```
sudo fdisk -l
```

```
sudo mount
```

You can mount it by using:

```
sudo mkdir /media/ipod
sudo mount **/dev/sdb1** /media/ipod/
```

**Note**:  sdb1 was just an example, yours might be sdb1, sdc1, etc.

---

### Post by bobbybobington on 2007-06-06
It seems others are getting the same error for other usb devices:( , There are some workarounds in [this thread]("http://ubuntuforums.org/showthread.php?t=428958") that might work for you.

---

### Post by tylerjroach on 2007-06-06
Thank you for the directions on how to mount it and i finally got it to mount. I am wanting to use amarok to manage my ipod and when i hit connect it is now saying:

failed to create lockfile on ipod mounted. Permission denied. How can i give amarok permission. thanks.

---

### Post by Ek0nomik on 2007-06-06
> **tylerjroach said:**
> Thank you for the directions on how to mount it and i finally got it to mount. I am wanting to use amarok to manage my ipod and when i hit connect it is now saying:

failed to create lockfile on ipod mounted. Permission denied. How can i give amarok permission. thanks.

Out of curiosity, was it my directions that got it working?

If you want to allow write permissions to your device, you can try:

```
chmod +w /media/ipod
```

If that doesn't work, you may need to get your hands on a Mac.  (I haven't done this personally, but this is from other users responses).

Your iPod might be formated as HFS+.  Linux won't allow you to write until you turn journaling off in your device.  If you boot up with a Mac and use the disk utility to turn off journaling, you should be good to go.

Let me know what happens.

---

### Post by tylerjroach on 2007-06-06
Yes your directions did work but now if i click eject it says it can because my ipod is mounted and it is removed from my computer. I had it working without without having to set it up on feisty but i reinstalled the o/s and it hasn't worked since.

---

### Post by Ek0nomik on 2007-06-06
> **tylerjroach said:**
> Yes your directions did work but now if i click eject it says it can because my ipod is mounted and it is removed from my computer. I had it working without without having to set it up on feisty but i reinstalled the o/s and it hasn't worked since.

I don't have an iPod personally, I am just trying to help.  ;)  I have a Creative Zen, which worked by simply installing one single program to transfer files and edit playlists, etc.

So what is your current problem?  You just can't remove it from your computer?

---

### Post by tylerjroach on 2007-06-06
It says it mounts but I can't transfer any songs over. Then when i try to eject it safely from the computer it says it isn't mounted and it will not disconnect. when I reconnect it, it does not mount and I have to go through the steps you gave me earlier again.

---

### Post by Ek0nomik on 2007-06-06
> **tylerjroach said:**
> It says it mounts but I can't transfer any songs over. Then when i try to eject it safely from the computer it says it isn't mounted and it will not disconnect. when I reconnect it, it does not mount and I have to go through the steps you gave me earlier again.

If you want the iPod to mount as soon as you plug it in, then you need to edit your /etc/fstab file to do it automatically for you.

```
gksudo gedit /etc/fstab
```

You simply add the device to your file as you can see the others already done.

If you want to transfer files to your iPod, you need to use some sort of software to do it.  I have seen people use Amarok (which is an awesome audio player too, my roommate uses Amarok for his iPod actually), and gtkpod is another.  I don't know which one is better, but you can take a stab at them both by searching around the forums.

I quote from Amarok:

> **Amarok]Amarok is a GNU/Linux audio player. While developed initially for KDE, it’s currently desktop independent. One of its advantages is support for many audio devices, including iPod, iRiver, etc. Upon the first run, you’re given the opportunity to set up your library. Unfortunately, out of the box on Ubuntu 6.10, the iPod wasn’t detected, but a quick configuration change made all the difference: Settings&#8594 said:**
>  advantages is support for many audio devices, including iPod, iRiver...

Copying music from the iPod is as simple as right-clicking and selecting Manage Files&#8594;Copy Track to Collection. As it adds files to Amarok’s library, the file is neatly named and placed in an appropriate folder (you’re given the option of which folder naming scheme you’d like). Copying to the iPod from your collection is similarly easy: right-click, Transfer to Media Device, select the Media Device and click Transfer. Amarok automatically checks for duplicate tracks, which is nice. The album cover function works quite nicely, fetching the image from Amazon or another external source. Playlists also work quite well.

---

