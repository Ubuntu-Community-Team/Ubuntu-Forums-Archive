---
title: "Trying to install Ubuntu alongside OSX via USB"
date: 2013-12-25
forum: Apple Hardware Users
---

### Post by hello3 on 2013-12-25
Hello, 

I'm a long-time Mac user and I really want to give Linux a try. For the past few days, I have been trying to install Ubuntu alongside OSX by making a Live USB. I have been searching pretty hard, and have tried several methods. I tried the instructions on the ubuntu website (converting the .iso to an .img using the command line) and I have tried using a method that uses something called syslinux to allow unebootin to create a live usb bootable on the mac. And of course I have tried the Mac Linux USB Installer. Nothing seems to work. I installed rEFIt, and when I restart with my live USB in, I get a bunch of things to the right of the apple, instead of just one 'boot from [my flash drive]' option. if i click on one, it will either give me an error message (alloc magic is broken, etc) or a black screen that simply states 'No bootable device detected -- insert boot disk'. Or, sometimes, I will actually manage to get an option to start ubuntu. After a glitchy loading screen appears, it appears to work ok, but when i try to install, the internet disconnects and it can't detect that there is OSX on this computer, and the default option is to erase the disk. So I quit the installation and try to shut down, and then my computer freezes on the same glitchy screen from start up. By now, my computer is probably plotting a terrible vengeance upon me after all the hard resets. 

I really don't want to buy a pack of black CDs just for this, because I will never use the rest of them. And, I plan on building a computer soon that won't have an optical drive, and it would be really helpful to know how to do this. And, I am a very stubborn person and I just must get this to work! I have seen many blog posts of people getting this to work, so I know it is possible. 

I would really appreciate any help in figuring out what is preventing Linux from installing smoothly. I hope this made any sense. If it doesn't, I can provide pictures, specific links, error messages, etc. Thanks so much!

---

### Post by QIII on 2013-12-25
[I]Moved to [B]Apple Users


[/B][/I]Hopefully you'll get some more specialized help over here.

Cheers.

---

### Post by ggodone on 2013-12-25
Follow [this guide]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx") to create a bootable USB drive, and resize your Macintosh HD partition in Disk Utility to allow room for Linux (backup first, just in case). Then when booting up press option, select the drive to the right of Macintosh HD, then once in the live USB install it **alongside OS X**. Worked flawlessly for me.

---

### Post by eightace on 2013-12-27
> **ggodone said:**
> Follow [this guide]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx") to create a bootable USB drive, and resize your Macintosh HD partition in Disk Utility to allow room for Linux (backup first, just in case). Then when booting up press option, select the drive to the right of Macintosh HD, then once in the live USB install it **alongside OS X**. Worked flawlessly for me.

What happened to your boot partition?
Did you have to use ReFit or ReFind?

Did you have to make a partition before in Disk Utility?

Thanks

---

### Post by Quackers on 2013-12-27
What Mac do you have? Can it boot from a USB?
If it came with a dvd drive you'll need to use that to install with.

---

### Post by cool3 on 2013-12-30
You might have to boot from a disc. Sometimes even if a computer has USB as an bootable option for whatever reason it won't.  More likely the Mac you have is not setup for booting from a usb key though.  

Discs are good for making backups of files.

---

