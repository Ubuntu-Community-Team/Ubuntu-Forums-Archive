---
title: "Help a noob follow these instructions....."
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by jksdua on 2007-06-09
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/95277](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/95277) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hey,

I have been using Linux for less than a day and just need some help in how to follow these instructions. They are a little vague for my understanding. I just want MythTV to recognise my TV tuner card.

Edit: how do I open a ".fw" file?

[https://bugs.launchpad.net/ubuntu/+s....20/+bug/95277](https://bugs.launchpad.net/ubuntu/+s....20/+bug/95277)
__________________

---

### Post by cantormath on 2007-06-09
that page does not seem resolve anymore.

What kind of card do you have?

---

### Post by jksdua on 2007-06-09
I have a Asus My Cinema U3000 mini.

Also, how do I open a .fw file?
and how do i install a program as root. i can't login as root on welcome screen and when i login in terminal and install the program, it opens another terminal window and says i can't install becuase i am not logged in as root. i am trying to install my display drivers.

---

### Post by cantormath on 2007-06-09
> **jksdua said:**
> I have a Asus My Cinema U3000 mini.

Also, how do I open a .fw file?
and how do i install a program as root. i can't login as root on welcome screen and when i login in terminal and install the program, it opens another terminal window and says i can't install becuase i am not logged in as root. i am trying to install my display drivers.

You dont login as root.  You dont need to.  You use the sudo command anything you need to do something as root.  This is a much safer way to do things.
what are you trying to install.  If you want to install something, and if you are a noob, you should use Applications>Add/Remove... or use System>Administration>synaptic

If you are trying to set codecs and flash etc and you have no patients, try Automatix or Easy Ubuntu.

I dont know what a .fw file is.

---

### Post by jksdua on 2007-06-09
a .fw file is a firmware file for the TV tuner card.

and i tried the sudo and gksudo command to run it but it just opens in another terminal and says it needs to run as a root. is there like a "safe mode" option where i can login as root and install it?

---

### Post by Outrunner on 2007-06-09
```
sudo <command>
```

To run something as root. You DO NOT login as root in Ubuntu.

---

### Post by jksdua on 2007-06-09
So does anyone have a way through which I can get my USB TV tuner card to work?

---

### Post by cantormath on 2007-06-09
> **jksdua said:**
> So does anyone have a way through which I can get my USB TV tuner card to work?

How do you know that your card is not working and do you have a program (ie tvtime) to watch tv with?

---

### Post by newlinux on 2007-06-09
Just looking at the bug report, you don't need to "open" the firmware file. You need to place the firmware file in the :

/lib/firmware/`uname -r`

directory (your kernel firmware directory), and then patch the driver files dib0700_devices.c  and dvb-usb-ids.h  (adding vendor and product id specific to this card)l. There is an example of how to change the dib0700_devices.c and dvb-usb-ids.h files in the bug report.. If you are not familiar with patching kernels, you should become familiar before doing this type of thing.

---

### Post by jksdua on 2007-06-09
ok i have put the firmware file in the directory...how do i patch it? just copy the code in the terminal?

---

### Post by newlinux on 2007-06-09
I'm no expert at patching kernels, but you would need get the the kernel source code from the repositories, modify the those two files referenced in the bug report and then recompile the kernel and install it.

---

### Post by Baptiste on 2007-12-16
There are linux drivers here :

[http://dlsvr01.asus.com/pub/ASUS/vga/tvtuner/EeePC_TVDrv_Src_11.zip](http://dlsvr01.asus.com/pub/ASUS/vga/tvtuner/EeePC_TVDrv_Src_11.zip) (the driver)
[http://dlsvr02.asus.com/pub/ASUS/vga/tvtuner/EeePC_TVAP_Src_15711.zip](http://dlsvr02.asus.com/pub/ASUS/vga/tvtuner/EeePC_TVAP_Src_15711.zip) (the player)

However I don't know how to compile it.

---

### Post by DagMan on 2008-01-01
I'm really annoyed.  Firstly with myself, that I didn't realise the error I was looking at.  Mostly though, that asus would host driver source code for this device on their site for over a month and not fix it.  Obviously they were able to compile it for their product.  Likely it is already up on the linux tv site, however if not, here's the bug report I had been keeping my eye on in relation to it and just very recently did someone compile it and post.
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/95277](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/95277)

sudo apt-get install build-essential linux-headers-`uname -r`
unpack it, cd into it, 
chmod +x v4l/scripts/*
make all
sudo make load to just load the drivers and test it
sudo make install to install them permanently

It's as if they intentionally made all the scripts non-executable and indeed there isn't an abundance of people noticing what the problem was either.
I haven't looked yet if there needs to be a module loaded at boot as I did make load since this isn't the machine I want it on.

Installing the player isn't needed but I thnk it had the firmware file in it, which is needed, and it can't hurt to have it.

Download links are there in the bug report or it can be found on the asus website.  There's also a much better how to linked to there than this post.

---

