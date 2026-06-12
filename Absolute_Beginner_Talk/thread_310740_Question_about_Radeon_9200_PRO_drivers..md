---
title: "Question about Radeon 9200 PRO drivers."
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by blakkinferno on 2006-12-01
I want to install Ubuntu and WINE, almost solely because i want to try Linux, but also because what ive read of it appeals to me. Okay, i have a few questions about Graphics card...

Well, i have a Radeon 9200 Pro Graphics Card (thats what it says in the display options of the Control Panel) with Omega drivers (Omega 3.8.221 drivers to be exact).

When i install Ubuntu, it completely will erase my drive, correct? What do i need to do to have these drivers/gfx card working correctly when i install Ubuntu?

Do i have to backup the driver, and install it afterward? Or will it automatically work? Or do i have to use the official Radeon drivers instead of the third party Omega ones? (Omega drivers are better for gaming, or so ive heard.)

And, my last question regards WINE. Will WINE work with my Radeon 9200 Pro and Omega Drivers, or will i have to change the drivers to official, or will it not work at all?

Thanks for your time, i just want to get these questions answered before i install Ubuntu, because naturally, if my GFX Card won't work, i probably shouldn't install Ubuntu.

---

### Post by SyvanX on 2006-12-01
You don't have to erase your hard drive completely, but the installation will partition it, so you'll have essentially a smaller windows hard-drive to make room for your Ubuntu installation.  

It sounds like you're trying to switch to Ubuntu, but still play the latest games on WINE?  You're probably going to be disappointed.  Also, you would be using Linux ATI drivers, which probably aren't going to squeeze as much performance out of your card as you're trying to get.  

If you have room on your hard drive, you could try the installation, give Ubuntu ~10 gigs or so.  It's worth a shot if you've gone this far.

---

### Post by mushroom on 2006-12-01
I think you'll have to install the fglrx driver. Wine will utilize your video card where needed (such as with 3D games), but I don't think it can use Windows drivers. To install the driver, do the following:

```
sudo apt-get install xorg-driver-fglrx
```

then

```
sudo dpkg-reconfigure xserver-xorg
```

go through the prompts and when it comes time to choose a driver, choose "fglrx". You should be set, then. Fair warning, though: these aren't the greatest drivers in the world, so you may not get fantastic performance, especially considering that you want to use Wine. Another warning: Windows games are still an iffy issue when running them through Wine, so you may want to go for Cedega instead (which costs). Either that, or you can keep a Windows partition around for gaming, which the installer allows you to do (but remember to back up your files before doing so).

---

### Post by blakkinferno on 2006-12-01
So your suggesting i dual boot it, right?

If i dual boot it, can i use my windows drivers for my Radeon while on the Ubuntu OS? Or should i go download Linux drivers?

If i have to go download Linux drivers, could someone tell me where to get them and how to install them please?

---

### Post by mushroom on 2006-12-01
You'll have to use Linux drivers in Ubuntu. Installation instructions detailed above.

---

### Post by blakkinferno on 2006-12-01
Okay, i have a couple last questions.

One, that driver that you gave me, do i have to download it? Or can i just run that straight from Ubuntu?

Second... What does it show you before you have any graphics card drivers? How am i supposed to do stuff with Ubuntu if i dont have a graphics card with drivers yet? Is it just like a little console, or what?

And third... If i dual-booted it, would i have to have Windows drivers for the windows part and linux drivers for the linux part.

Thanks :).

I'll probably end up dual-booting then, once these questions are answered.

PS: I have to reinstall windows to dual-boot though, don't I? Or can i just install Linux over it in a seperate partition? Thanks.

---

### Post by mushroom on 2006-12-01
Well, they do come with drivers, but the drivers probably won't be able to take advantage of 3D. You'll be able to do stuff, just not stuff that involves 3D (like games). You input that stuff in the terminal (which should be under "Applications>Accessories>Terminal"). And yes, dual-booting would involve Windows having its own drivers and Ubuntu having its own drivers.

---

### Post by blakkinferno on 2006-12-01
MMk, i think i get it. I am working on getting applications to resize the partition right now, so i dont have to reboot windows.

Also, what appears on Ubuntu before you have any linux graphics card drivers? How does it show anything?!

---

### Post by mushroom on 2006-12-01
You will have drivers installed by default, but the drivers won't be able to do any 3D stuff. The reason for this is because ATI won't reveal its card specifications, so the free ones only support 3D on old cards, though they still work minimally on newer ones. fglrx is ATI's official Linux driver, but it's not open source, so it isn't included with Ubuntu by default. I've also heard it's not that great compared to ATI's official Windows driver.

---

### Post by blakkinferno on 2006-12-01
Thanks for all your help, man, its appreciated.

However, i have 1 more question. I have got all of it ready, im about to install... but i cant. Please help, its a stupid problem, i just hope there is a way around it.

Okay, a while ago, i accidently deleted my integrated Intel GFX Cards drivers. (^^U WOOPS). Anyway, all went well, because i am using my Radeon. However, at bootup, it says "Cannot display video mode", and then when it gets to login screen, it switches into Radeon and starts showing up.

So... maybe this isn't the correct way to do this but...

How do you make it so that your computer will boot from a CD instead of Hard Drive first?

[ I dont know if Ubuntu does this automatically, but i have a CD to resise NTFS partitions, and i dont know how to use it. I really need the answer to this question please... I AM EAGER.]

---

### Post by mushroom on 2006-12-01
I'm having a bit of trouble understanding your problem, so bear with me. Your problem is that when you boot the computer it boots from the HD, even if the CD's in the drive? If that's the case, then go into your BIOS settings, and there should be an option to boot from CD first.

However, if your problem is that nothing shows up on your screen until you get to the Windows login, then I can't really help you there. Sorry.

As for driver concerns, nothing on your hard drive will affect the live CD's operation. Also, should you dual-boot, nothing on your Windows partition will affect anything on your Ubuntu partition.

---

