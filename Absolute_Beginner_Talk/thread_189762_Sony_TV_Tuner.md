---
title: "Sony TV Tuner?"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by theacoustician on 2006-06-05
Hello all.  I've sucessfully have gotten 6.06 LTS running on my Sony PCV-W600G EXCEPT for the TV tuner card.  This one is a real head scratcher.  By all accounts, this thing is nearly identical to a Hauppauge card.  I've even found mention in other forums from other people who claim to have gotten it working, however, they never elaborate as to how.

I've tried installing IVTV, but I can't get it to work.  It spits out a bunch of errors about not being able to load the firmware.

So the question is : Is it possible or is this a lost cause?

Info on the tuner card
Name : Sony Giga Pocket PVR
Front PCB : 1-860-696-31 ENV-26 AOI
Back PCB : A8119675A 000 4108 PCVA-IMB5A
RF Demod : 8-598-629-10  /  BTF-PA401Z SONY     
MPEG encoder : Conexant CX23416-22
Video decoder : Philips SAA7115HC
Audio DSP ??? : Sony CDX9795BR

If any other info needed to solve this problem, let me know.  Otherwise, thanks in advance for any help.

---

### Post by Blondie on 2006-06-05
Try installing Kaffeine. It has built in support for DVB. See if it lets you scan for channels.

Otherwise / as well see,
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

Even if you aren't going to do the full MythTV install you might like to test it out without MythTV to see if you have problems and if so find out what they are.

---

### Post by richbarna on 2006-06-05
I heard about this problem on Windows, that you need the Giga pocket software and sony drivers.
People were using sagetv.
This is available for Linux but costs about $70.

---

### Post by theacoustician on 2006-06-05
[QUOTE=Blondie]Try installing Kaffeine. It has built in support for DVB. See if it lets you scan for channels.

Otherwise / as well see,
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

Even if you aren't going to do the full MythTV install you might like to test it out without MythTV to see if you have problems and if so find out what they are.[/QUOTE]
Ah, I wish it was DVB, NTSC here :( 

I'll give her a go anyways

[QUOTE=richbarna]I heard about this problem on Windows, that you need the Giga pocket software and sony drivers.
People were using sagetv.
This is available for Linux but costs about $70.[/QUOTE]
$70?  Holy crap. :(

---

### Post by innactpro on 2006-09-26
I contacted Sony and got this...

"Thank you for contacting Sony Online Support.

The SONY VAIO desktop computers are designed specifically to work with the Windows operating system with which they ship. While we have heard that Linux will work on the PC by SONY, SONY has not tested Linux on our VAIO computer systems.

SONY has not designed and is currently not in the process of developing Linux drivers for the hardware components of our VAIO systems. If you intend to install the Linux operating system on your PC, you will need to contact your Linux distributor for any available Linux hardware device drivers, software applications or system utilities. A few websites that may prove helpful to you are:

[http://www.linux.org/](http://www.linux.org/)

[http://www.cs.utexas.edu/users/kharker/linux-laptop/](http://www.cs.utexas.edu/users/kharker/linux-laptop/)

[http://sunsite.unc.edu/mdw/linux.html](http://sunsite.unc.edu/mdw/linux.html)

[http://linux.about.com/compute/linux/](http://linux.about.com/compute/linux/)

NOTE: The internal modem is designed to work with the Windows
operating system only.

NOTE: The installation of a "Dual Boot" hard drive format may
disable several Windows advanced features and utilities.
We do not assist in, or support our VAIO systems in a
Linux "Dual Boot" configuration.

The VAIO Customer Information Services Center is unable to support any operating system or configuration other than the one originally shipped from SONY.

Thank you for the opportunity to be of assistance."

](*,) 

The provided links weren't very useful. It looks like we won't be able to use Giga Pocket in an linux environment. There are two other threads about this and they are having the same problem.

---

### Post by Kateikyoushi on 2006-09-26
My girlfriend has the same PC so in the end we stick with windows on it.

---

### Post by innactpro on 2007-04-03
Has anyone tried using Wine or some other windows emulation? I still haven't made the switch to Linux and I am aware that emulating windows in a Linux environment isn't always the most stable approach.

---

### Post by innactpro on 2007-04-04
From another forum I came across.

"In my experience, the only piece of hardware that didn't have a driver in Linux was the Sony Mpeg Gigapocket, and I wrote a driver for that so that I could use it with MythTV."

[http://www.msforums.com/index.php?sh...findpost&p=714](http://www.msforums.com/index.php?sh...findpost&p=714)

Maybe if we ask this guy for help...

---

