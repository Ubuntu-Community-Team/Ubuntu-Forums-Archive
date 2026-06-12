---
title: "[SOLVED] ATI Graphics Card - Cannot Boot Ubuntu"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by sirfox86 on 2007-10-03
Hello,

I'm relatively new to Ubuntu, but I've worked with it a few times in the past.  My computer has an AMD  64 processor and an ATI X700 graphics card.   So I downloaded the alt install disk for Feisy Fawn, installed in text mode a rebooted.  I then followed the directions below to install the ATI drivers.  However when I restart and try to book, Ubuntu starts to load for a second, and then the screen goes completely black (no signal at all), and my keyboard lights flash at me after a few seconds (but nothing happens).

I've repeated all of these steps again to make sure I didn't miss anything, yet I still have the same problem.  I've even tried changing xorg to use the vesa drivers by going through xsetup, but when I get to the option about setting color depth, the system gives me an error that by saving I would be overwriting customized settings, and returns me to the command prompt (I assume this relates back to the ati drivers I installed).

So now I'm stuck, and I'd just like to be able to load Ubuntu  (right now I'm not concerned about any fancy video effects, I just want it to work.)

Thanks for any help!

Here are the instructions I followed:

 Installing Ubuntu 7.04: ATI X**** Cards
This post could be related to an Ubuntu bug filed at: [https://bugs.launchpad.net/ubuntu/+s...ver/+bug/89853](https://bugs.launchpad.net/ubuntu/+s...ver/+bug/89853)
----------------------------


Many people are having problems installing Ubuntu 7.04 (Feisty Fawn) on machine with ATI X**** series video cards. This is caused by this bug that unfortunately could not fixed before the release of Ubuntu 7.04.

This quick guide will get Feisty installed and X.org 7.2 up and running.

   1. Boot using PC (Intel x86) alternate install CD for Ubuntu or Kubuntu.
   2. Start text mode installer and install Ubuntu/Kubuntu.
   3. Finish Install and reboot.
   4. Update package list and upgrade any packages needed.
      Code:

      sudo apt-get update
      sudo apt-get dist-upgrade

   5. Install fglrx closed source driver for ATI video cards.
      Code:

      sudo apt-get install xorg-driver-fglrx

   6. Update loaded modules.
      Code:

      sudo depmod -a

   7. Configure /etc/X11/xorg.conf
      Code:

      sudo aticonfig --initial
      sudo aticonfig --overlay-type=Xv

   8. Reboot


Ubuntu 7.04 should now boot into GDM/KDM.
__________________

---

### Post by hotweiss on 2007-10-03
Try Gutsy Gibbon...

---

### Post by Terl on 2007-10-03
I notice you said you used the alternate cd and installed in text mode.  Did you install xorg?

---

### Post by sirfox86 on 2007-10-03
As far as I can tell I installed xorg, since I can go in and start changing the configuration.  I definitely didn't de-select it while installing.  Is there an easy way I can check to make sure its installed, and a way to do it if for some reason it is not?

---

### Post by Terl on 2007-10-03
Interesting.  I used that same post to install the drivers for my X1600 without a problem.  Of course major difference is I am on 32 bit.  Are you running the 64 bit version?

Does it boot to command line?  Or does it fail to boot at all?  Are there any error messages.

---

### Post by sirfox86 on 2007-10-03
I can boot into recovery mode, but not into the standard mode.  If I try to, I get perhaps 1 second of loading time where some text appears on the screen (I can't read it because it passes so fast) before the screen goes blank from a loss of signal.  Recovery mode works (thats how I was able to run the code I already ran).

Yes, I'm using the 64 bit processor version.  It's even been updated, since I did that through the command line as well.  Perhaps I should try reinstalling everything and then trying to use the vesa drivers??  After searching through the forums, I can't seem to find this problem that wasn't fixed by doing what I already did.

---

### Post by master_kernel on 2007-10-03
What is the model of your ATi card? I know that some are supported by xorg-driver-fglrx and some by xorg-driver-ati. There is a list here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by sirfox86 on 2007-10-03
Its an X700 Pro.

---

### Post by Terl on 2007-10-03
Have you tried editing your xorg.cong back to vesa?  You can do it easily using > sudo dpkg-reconfigure xserver-xorg and select vesa as the driver.  After you are done you can try a startx and see what gives.  Have you tried booting with the noapic option?

---

### Post by sirfox86 on 2007-10-03
Yeah, I tried seting xorg to VESA, but as Im going throw the prompts, it kicks me back out into the command line when I try to proceed past the question about color bit depth.  I get an error message that warns me that I'm changing a customized setting... but I can't (or at least dont know how) to get back into the xserver window without starting over (and therefore repeating it all over again).

---

### Post by sirfox86 on 2007-10-03
Yeah, I tried setting xorg to VESA, but as I'm going throw the prompts, it kicks me back out into the command line when I try to proceed past the question about color bit depth.  I get an error message that warns me that I'm changing a customized setting... but I can't (or at least don't know how) to get back into the xserver window without starting over (and therefore repeating it all over again).

---

### Post by crjackson on 2007-10-03
Open up a terminal and type:
```
gksudo gedit /boot/grub/menu.lst
```

Look through the file and you will find 2 entries that say "splash" without the quotes.  Change this to "nosplash" without the quotes.  

Save the file and reboot.  That should do it...

---

### Post by sirfox86 on 2007-10-04
Ok, so I tried the last bit of code from crjackson and got this error:

```
(gksudo:4568) Gtk-WARNING **:cannot open display:
```


For further reference, I also wrote down the error I now get when I try to switch xorg to use the VESA drivers (or any driver for that matter from within the xorg configuration).  It kicks me back to command line and gives me this message:
```

xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/corg.conf.2007100400185
```

Any advice from here out?

---

### Post by Terl on 2007-10-04
That warning is a "just so you know" warning.  It is telling you it is backing up your xorg.conf.  It is alright to ok this.

---

### Post by sirfox86 on 2007-10-04
How do I get back to what I was doing after that warning appears?  That has been part of my problem, since when the warning appears, I go back to command line instead of still being in the xorg configuration.

---

### Post by crjackson on 2007-10-04
> **sirfox86 said:**
> Ok, so I tried the last bit of code from crjackson and got this error:

```
(gksudo:4568) Gtk-WARNING **:cannot open display:
```


For further reference, I also wrote down the error I now get when I try to switch xorg to use the VESA drivers (or any driver for that matter from within the xorg configuration).  It kicks me back to command line and gives me this message:
```

xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/corg.conf.2007100400185
```

Any advice from here out?

```
sudo nano /boot/grub/menu.lst
```

---

### Post by sirfox86 on 2007-10-05
Thanks!  That worked after I replaced the quiet splash lines in there.  Once I load it, it works great.

---

