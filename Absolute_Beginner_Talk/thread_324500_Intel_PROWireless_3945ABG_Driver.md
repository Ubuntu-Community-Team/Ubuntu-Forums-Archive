---
title: "Intel PRO/Wireless 3945ABG Driver"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by sevak316 on 2006-12-23
Hello,
I am new and need help.

I have a HP dv2000t, and running it on UBUNTU 6.10.

I am trying to get my wireless drivers installed and I am stuck.

I went on Intel's website and downloaded the Linux drivers.  After reading the instructions its told me before i even can install the drivers, i have to install ieee80211 subsystem.

After I installed the ieee80211 subsystem, i attempted to install the driver and this is the error i get:


---------------------------------------------------------------------------------------------------------------------------
sevak@sevak-laptop:~/Desktop/wireless/ipw3945-linux-1.1.0/ipw3945-1.1.0$ sudo make
/bin/sh: Syntax error: "(" unexpected
/bin/sh: Syntax error: "(" unexpected
sed: can't read net/ieee80211.h: No such file or directory
/bin/sh: [[: not found
-e 
 WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.

 
-e  Aborting the build.  You can force the build to continue by adding:

        IEEE80211_IGNORE_DUPLICATE=y

to your make command line.


make: *** [check_inc] Error 1
-------------------------------------------------------------------------------------------------------------------------

[SIZE="3"][B]
So.... I tried adding that line to my command line, and this is the error i got:[/B][/SIZE]


----------------------------------------------------------------------------------------------------------------------------
sevak@sevak-laptop:~/Desktop/wireless/ipw3945-linux-1.1.0/ipw3945-1.1.0$ sudo make IEEE80211_IGNORE_DUPLICATE=y
/bin/sh: Syntax error: "(" unexpected
/bin/sh: Syntax error: "(" unexpected
sed: can't read net/ieee80211.h: No such file or directory
/bin/sh: [[: not found
-e 
 WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.

 
-e 
 ERROR: A compatible subsystem was not found in the following path[s]:

        /lib/modules/2.6.17-10-generic/include/ /lib/modules/2.6.17-10-generic/

You need to install the ieee80211 subsystem from [http://ieee80211.sf.net](http://ieee80211.sf.net)
and point this build to the location where you installed those sources, eg.:

        % make IEEE80211_INC=/usr/src/ieee80211/

or use the 'make patch_kernel' within the ieee80211 subsystem to patch your
kernel sources.

make: *** [check_inc] Error 1
-----------------------------------------------------------------------------------------------------------------------


Does anyone know what the problem is and how i can fix it? please! ](*,)

---

### Post by Bachstelze on 2006-12-23
That's weird, I have an IPW3945 too and Ubuntu detected it OOTB... Are you quite sure it doesn't appear in iwconfig ?

---

### Post by sevak316 on 2006-12-23
ok this is what i get for iwconfig.

sevak@sevak-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"wireless"  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1509   Missed beacon:0

sit0      no wireless extensions.



what am i suppose to do?

---

### Post by shanepardue on 2006-12-23
I have the same wireless card and mine worked out of the box also. Go to System >  Administration > Networking and configure your wireless card the way you want it. Let us know if you have questions!

---

### Post by macogw on 2006-12-23
Like others said, should work OOTB

---

### Post by sevak316 on 2006-12-23
i am fairly new to the LINUX enviroment so please tell me what i need to configure in the "Networking" section. As far as i know, you can name the ESSID to whatever you want. So, i did that. Than on the top right corner when i click them 2 computers, in the name section i put eth1 and it says Status == Disconnected. What am i suppose to do??

and this is what i have for iwconfig:

sevak@sevak-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"wireless"  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5567   Missed beacon:0

sit0      no wireless extensions.

---

### Post by macogw on 2006-12-23
You don't name the ESSID whatever you want.  ESSID is the name of the wifi network you're connecting to.

---

### Post by Atomic Dog on 2006-12-23
I have a dv6000 series with the same centrino setup and it worked out of the box.  I'm perplexed that you have a problem.  Perhaps reinstall?

---

### Post by macogw on 2006-12-23
> **Atomic Dog said:**
> I have a dv6000 series with the same centrino setup and it worked out of the box.  I'm perplexed that you have a problem.  Perhaps reinstall?

I think the problem is just in figuring out what info to put in the "Networking" fields.  They can be ornery.

---

### Post by Atomic Dog on 2006-12-23
> **macogw said:**
> I think the problem is just in figuring out what info to put in the "Networking" fields.  They can be ornery.

Oh oh oh.  Maybe wifi-radar would help?  I use it.  I love it.  Make more sense to me and the profiles make switching wireless networks a snap.

---

### Post by sevak316 on 2006-12-23
macogw, thanx for the advice, my dumbass friend told me that i can name it whatever i want. he is a complete idiot and i dunno why i trusted him in the first place since i have computer exprience exceeding 10 years. I just need to buff up my Linux skills.

---

### Post by raldz on 2006-12-23
3945abg should work out of the box.. your problems seems to be figuring out how to connect..
try to use connection manager..

install:
connection-manager
connection-manager-systray  (this will help you choose wireless networks to connect with support for both WEP and WPA)

then add connection-manager-systray to your session start up..

---

### Post by esouris on 2007-02-21
Guys just to let you know everything's cool for me with Intel PRO/Wireless 3945ABG on my Acer Aspire 5684WLMi just opened wireless with the button in front of the laptop and I used wi-fi assistant (actual name : wlassistant) and its working really cool for me everything's ok!!!!

And remember i have an **Acer Aspire 5684WLMi**[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR], if anyone knows any site for configuration with linux generally for acer aspire 5680 series please let me know thanks for the understanding 

Greetings from Crete in Greece
Ubuntu newbie!!!!:popcorn:

---

### Post by penvzila on 2007-04-29
This does work OOB -- in 32bit.  Not in 64bit.  I had to compile the driver on my dv2000t in edgy-amd64.

---

### Post by penvzila on 2007-04-29
I just re-installed because of an unrelated issue, and it did work right out of the box in 64bit.  Strange... but I'm not complaining.

---

### Post by timbudtwo on 2007-05-13
I am having the same problem. Have you figured out a solution to it yet?

---

### Post by smylie on 2007-05-26
> **timbudtwo said:**
> I am having the same problem. Have you figured out a solution to it yet?

ahh. wasted many hours on this before I noticed that 
a) the error mentioned /bin/sh: unexpected token . . .
b) the ieee subsystem (which i had installed), in the Makefile it mentioned it didn't like being run under anything other than bash.

so. . .  putting 1 and 1 together to make 3, i tried from the ipw3945-1.2.1 directory:

```
$ make SHELL=/bin/bash
```

and the unexpected token "(" errors went away, it detected the ieee subsystem correctly and compiled okay...

however, all was still not good . . . the install documents being somewhat muddled.
the ipw3945 install directory contains a load script - this didn't work for me. however, a simple 
  make install  (not documented in INSTALL) manually installed it to the right place, so i could modprobe as per normal.

however, all was still not good ... i had gone thru and installed the regulatory daemon (just copy it to /sbin/ipw3945d - the INSTALL says just to copy it there (which i did), but modprobe wouldn't load the module as it couldn't find one with the matching kernel version appended to the name.
so i just did an 
```
ln -s ipw3945d ipw3945d-2.6.21.3 
``` from the /sbin directory, and **finally** i could modprobe ipw3945 and have wireless =)

Hope that helps you

Dave Smylie

---

