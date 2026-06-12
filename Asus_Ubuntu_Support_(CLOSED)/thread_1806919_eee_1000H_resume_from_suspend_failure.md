---
title: "eee 1000H resume from suspend failure"
date: 2011-07-18
forum: Asus Ubuntu Support (CLOSED)
---

### Post by bez654 on 2011-07-18
Dear All

I have an eee pc 1000H with ubuntu 11.04 32bit installed. Most things work really well, even unity is ok - although unity 2D is faster. 
However, I have a problem with resuming from suspend (standby). If the mains is plugged in and I suspend my computer, most of the time it comes back and works fine. There maybe an issue with the wi-fi not working first time, but turning wi-fi off then on again solves this. 
If I suspend my computer on battery power then it will not resume. It appears to go into suspend fine (flashing power light) and then starts to resume when i press any button (the lights come on). But, that's it. I get nothing on the screen - it doesn't turn on, and after about 30secs the computer turns off. When I then press the power button it boots from a power off state. 
Hibernate, on the other hand, works fine on both battery and mains power. This is except for the odd hicup with the wi-fi resuming. 
The laptop is a stock laptop with the exception of upgraded RAM to 2gb.

Has anybody else had this problem with resume from suspend (standby), or any clue as to where to look to start trying to fix this problem?

Thanks
John

---

### Post by toor58 on 2011-07-19
My asus 1001px has no problem, knock on wood. Try the advice in this article:

[http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html]("http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html")

It is a little dated but may still help. Make sure to back up any files you modify before changing anything.

Good luck.

---

### Post by bez654 on 2011-07-20
Thanks for the tip.
However, that doesn't work for me. s2ram gives me a login screen and doesn't actually suspend the laptop. 
Hibernate works great for me normally, which seems to be the opposite to the problems most people are having.

I've tried a couple of other things
[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

this doesn't make any difference - this script unloads a couple of devices before suspending so they wont stop the computer resuming. Seems to work for a lot of people. 
However, as this unloads networking before hibernate, my network reconnects much better when resuming from hibernate.

also tried blacklisting one copy of the wi-fi driver - as per
[http://ubuntuforums.org/showthread.php?t=1661070](http://ubuntuforums.org/showthread.php?t=1661070)
this didn't help

---

### Post by Toz on 2011-07-20
You could try a newer kernel. See: [http://ubuntuforums.org/showpost.php?p=10848055&postcount=20]("http://ubuntuforums.org/showpost.php?p=10848055&postcount=20")

---

### Post by bez654 on 2011-07-20
Hi. Ta for the suggestion.
I'm running kernel 2.6.38-10 (32bit) which is the latest release. I've added the ppa suggested in the link you provided and the only pre-release kernel available through apt-get is 2.6.38-11, not 2.6.39-0 as suggested in the link. 
Do you know how I would install the 2.6.39 kernel?

---

### Post by Toz on 2011-07-20
Looks like the PPA has changed. Have a look at this blog entry: [http://www.khattam.info/howto-install-linux-kernel-3-0-in-ubuntu-11-04-natty-narwhal-2011-06-03.html]("http://www.khattam.info/howto-install-linux-kernel-3-0-in-ubuntu-11-04-natty-narwhal-2011-06-03.html") for information about installing the new 3.0 kernel into Natty. If you follow the link in that article to: [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/"), you'll notice a directory for the 2.6.39rc4 for natty - you could use the same instructions but use those files instead.

---

### Post by JosephWheatley on 2011-10-18
I have made a clean install of **Oneiric Ocelot** ** 11.10** on my** Eee PC** **1000h **and all of the above issues have gone.

It is pleasing to use ***suspend*** again without losing wireless and having to reboot.

---

### Post by bez654 on 2011-10-19
Thanks for posting that 11.10 works.

Are there any other issues with 11.10 which I should be aware of? I presume that you have to use unity 2D? (not a problem, just curious).

I wonder if a clean install was necessary or if an upgrade will do the trick?

I'll do an upgrade in a few days and see if it solves my suspend problem...

---

### Post by bez654 on 2011-10-24
Hi

I tried an in-place upgrade on my eee 1000H from 11.04 to 11.10. This didn't really work as it lost my wireless card, so I lost all wi-fi connections. The standby problem still existed.
So I tried a clean install - formatting my drive and starting again with new user accounts. This was to remove all settings I may have changed in my accounts and all system wide settings. 
however, i still have a problem with standby not working everytime. It seems better than before, but invariably I cannot resume from standby. It seems to go into standby ok, but every other time wont resume. 
I guess I will have to treat this as not working.

If anyone would like to let me know how to debug this problem I would be happy to try to get to the bottom of this problem.

Everything else seems to work with 11.10. I did have a glitch with the trackpad stopping working after logging into a user account for the first time - it would stop working after using the unity menu bar. This seemed to solve its after logging out and in again and hasn't been a problem since. 

John

---

### Post by JosephWheatley on 2011-10-26
There is an ongoing issue with 11.10 on the eee pcs namely kernel panics.

There is a bug report on it here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/869502](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/869502)

This is disappointing as 11.10 is working very well otherwise.

The crashes are unpredictable.

I do hope that with a kernel update in the future it is sorted out.

---

### Post by bez654 on 2011-10-28
I have to admit, other than my standby issue, i've not had any other problems with a 11.10 clean install. I've not seen any kernel panics.

---

### Post by JosephWheatley on 2012-01-07
I know your issue is with resume from suspend as I had had in 11.04 but it may be that the following is of help.

This [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/869502") came to the conclusion after a few months that the kernel panics were caused by the power management. You can check if this is on with the command
```
iwconfig
```gives 

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"ScottJoplin"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:11:50:F9:EF:D4   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          [SIZE=4]Power Management:off[/SIZE]
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:347   Missed beacon:0
```the command ```
iwconfig wlan0 power off
``` will turn off the power management for the time you are logged in but to keep the power management off permanently I used the advice here
[http://askubuntu.com/questions/85214/how-can-i-prevent-iwconfig-power-management-from-being-turned-on/85223#85223](http://askubuntu.com/questions/85214/how-can-i-prevent-iwconfig-power-management-from-being-turned-on/85223#85223)

---

