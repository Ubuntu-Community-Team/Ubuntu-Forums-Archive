---
title: "Linux on thin client PCs"
date: 2017-02-26
forum: Any Other OS
---

### Post by andymacsteve on 2017-02-26
Hi

I got this HP thin client PC and I was wondering what OS I could install on it. It only has 2 GB of flash (IDE module on-board), and has an option for internal USB ports, but I want to run an OS off the flash storage instead, even if I can install some Linux to a USB and connect it to the internal USB, because it's probably easier

I even tried Lubuntu and it was failing because I was getting an error when trying to select and install software during the install phase

What would you recommend? I need something because I accidentally deleted the Windows Embedded that was on there, bc it was one of the WinXP based version of Embedded. 

Thanks!

PS: It has 2 GB of DDR3, and an Atom N280 (single core + HT)

---

### Post by DuckHook on 2017-02-26
Welcome to the forums, andymacsteve

2GB of flash will not allow you to install any kind of dynamic OS, but you can try installing an ISO image and run it as a LiveUSB/DVD. 2 GB is not enough for persistence, so you will only have a static OS—i.e can't add apps or internally save data (except to external storage). With 2GB RAM, I would stick with Lubuntu. You could also try Puppy, Tiny Core or Slitaz, all of which run as LiveUSB/DVD static images by default.

To be honest, these sorts of thin clients are very hobbled—as you are discovering—though useful in kiosks and other static uses, they haven't much other modern-day use.

---

### Post by andymacsteve on 2017-02-27
Thanks, but I tried installing Lubuntu and I think I was getting an error trying to install the software packages during installation 

I think its because there's not enough space on the flash storage. However, I want a way to install a Linux OS of some sort, straight to the flash as opposed to having a USB drive plugged in all the time. 

Also, I can't really remove the flash module either. I can, but I don't really want to. So, how can I install A Linux OS to there

---

### Post by DuckHook on 2017-02-27
Perhaps I wasn't being clear. You won't be able to install Lubuntu the "regular" way. That is, by booting into a USB stick and then choosing *Install*. This installs a dynamically functioning OS. What you must do is turn your flash memory itself into a Live/USB stick, and then run only LiveUSB sessions from it, if you catch my meaning.

In general terms, the strategy is this:

[LIST=1]
[*]You need ***two*** USB sticks.
[*]On the first one, you need to install a proper LiveUSB session. You already have that. It's the one that you typically install with.
[*]On the second stick, you want a copy of the actual ISO image itself. You do ***not*** want this expanded into a LiveUSB.
[*]Using the LiveUSB, you do ***not*** do an "Install".
[*]Instead, using an app like *Startup Disk Creator* and using the ISO on your second USB stick as your source image, you create a Startup Disk *on your 2GB flash module* in your computer. To reiterate, you would normally use this process to create a LiveUSB for installation purposes. In this case, you are using your flash module as that LiveUSB.
[*]Every time you boot up, your computer will now ask you whether you want to install Lubuntu or run a LiveUSB session. Of course, you choose the live session.
[/LIST]
**CAVEAT**

The above is just theory. I've never tried it, since I've never had occasion to do so. In theory it should work. But in practice, I don't know what odd real-world thing may prevent it from doing so.

As already mentioned, the resulting installation will behave very much as a LiveUSB. The OS itself will be read only. You won't be able to update or upgrade. Any apps you install will be only in RAM and will disappear as soon as you power down. You won't be able to change any of your /home settings or, indeed, store anything into /home at all. You will, in short, have a very limiting computing experience,  but it's one way to get your severely hobbled hardware running Lubuntu.

And again, as already mentioned, since Puppy, Slitaz and Tiny Core are already designed to run as static LiveUSB installations (with persistence) they may actually prove to be better choices for your situation. You should give them a try.

---

### Post by andymacsteve on 2017-03-05
I think Arch Linux fits but I need an i686 version which I can only find x86_64 versions because they supposedly dont support i686 anymore. Does anyone know where I can get a i686 ISO of Arch Linux??

---

