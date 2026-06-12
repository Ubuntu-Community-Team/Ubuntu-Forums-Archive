---
title: "DIY: Fan Control with terminal"
date: 2010-09-01
forum: Apple Hardware Users
---

### Post by TesX on 2010-09-01
[B]EDIT: Don't do this... Why it is explained below...
However you can change the fanX_min if you want...
But don't change 
fanX_manual
and 
fanX_output[/B]
> Yep this is correct - you should NEVER set fanX_manual != 0 as this disables the automatic SMC firmware control of your fan and so if the temperature rises, the fan speed will NOT rise to compensate and hence your machine may get fried.

ALWAYS leave fanX_manual = 0

Hello, I dont' know if this has been posted before, but I found a way to control the fans speed of the computer.

I needed this because I've installed ubuntu maverick meerkat alpha 3 on my iMac 27, and it became hot after a while.

Fire up the terminal and do
[FONT=Courier New]cd /sys/devices/platform/applesmc.768/[/FONT]
(I don't know if the number is the same, just change it with yours and should work)
now do
[FONT=Courier New]sudo su[/FONT]
(to login as root without having to retype sudo every time)

for each fan in your system you should have those files:
(substitute X with the fan number)
fanX_min
fanX_max
fanX_input
fanX_label
fanX_output
fanX_safe
fanX_manual

Ok, now do
[FONT=Fixedsys]cat fanX_label[/FONT]
to see what fan it is
and
[FONT=Fixedsys]cat fanX_min
cat fanX_max[/FONT]
to find out he available range of values.

Now you need to switch to "manual" mode:
[FONT=Fixedsys]echo '1' > fanX_manual[/FONT]

Now set the value you want
[FONT=Courier New]echo '2000' > fanX_output[/FONT]

(if you don't set 1 in fanX_manual the value you try to set in fanX_output won't be applied and if you do 
[FONT=Courier New]cat fanX_output[/FONT]
you'll see the value given by the system)

If you want to revert to automatic mode
[FONT=Courier New]echo '0' > fanX_manual[/FONT]

I hope this was useful to you.

PS: I've tested it and worked on my imac, however I don't want any resposibility :P )
PS2: Sorry if my English is not correct...

---

### Post by TesX on 2010-09-01
Maybe I will create an app for that... who knows... :)

---

### Post by dngfng on 2010-09-01
Hi,
SwedishWings coded a Fan Control daemon that works pretty well on MacBook's and MacBook Pro's (as most of us have experience Heat/Fan issues). 
Have a look at it, it may solve your fan control issues - if the code is not 100% suitable for  iMacs yet just let him know, he keeps updating it.

[http://ubuntuforums.org/showthread.php?p=9778072#post9778072](http://ubuntuforums.org/showthread.php?p=9778072#post9778072)

---

### Post by SwedishWings on 2010-09-01
> **dngfng said:**
> Hi,
SwedishWings coded a Fan Control daemon that works pretty well on MacBook's and MacBook Pro's (as most of us have experience Heat/Fan issues). 
Have a look at it, it may solve your fan control issues - if the code is not 100% suitable for  iMacs yet just let him know, he keeps updating it.

[http://ubuntuforums.org/showthread.php?p=9778072#post9778072](http://ubuntuforums.org/showthread.php?p=9778072#post9778072)

The Fan Control daemon is now available in the mactel ppa. It supports karmic, lucid and maverick. To install it, do

```
$ sudo apt-get update
$ sudo apt-get install macfanctld
```

To learn more about it, do look at the man page, 'man macfanctld'.

Cheers!

/Mike

---

### Post by SwedishWings on 2010-09-01
> **TesX said:**
> Now you need to switch to "manual" mode:
[FONT=Fixedsys]echo '1' > fanX_manual[/FONT]

Now set the value you want
[FONT=Courier New]echo '2000' > fanX_output[/FONT]


I'm not sure this is a good idea. 

When fanX_manual != 0, I suspect it disables the built in fan control. Instead, use **only** fanX_min which has the same effect but does not disable the internal control. I could be wrong about this, but i got a red hot machine early when used the manual override.

/Mike

---

### Post by TesX on 2010-09-01
> **SwedishWings said:**
> The Fan Control daemon is now available in the mactel ppa. It supports karmic, lucid and maverick. To install it, do

```
$ sudo apt-get update
$ sudo apt-get install macfanctld
```To learn more about it, do look at the man page, 'man macfanctld'.

Cheers!

/Mike


Ah ok, thanks.
I'll try it ASAP :)

---

About the bad idea to use manual mode, I can't tell you surely, but I presume you're right... However setting it to a 'middle' value should be fine enough...

---

### Post by alexmurray on 2010-09-01
> **SwedishWings said:**
> I'm not sure this is a good idea. 

When fanX_manual != 0, I suspect it disables the built in fan control. Instead, use **only** fanX_min which has the same effect but does not disable the internal control. I could be wrong about this, but i got a red hot machine early when used the manual override.

/Mike
Yep this is correct - you should **NEVER** set fanX_manual != 0 as this disables the automatic SMC firmware control of your fan and so if the temperature rises, the fan speed will NOT rise to compensate and hence your machine may get fried.

**ALWAYS leave fanX_manual = 0**

---

### Post by TesX on 2010-09-02
> 
 					Originally Posted by **SwedishWings** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9793480#post9793480") 				
 				[I]The Fan Control daemon is now available in the mactel ppa. It supports karmic, lucid and maverick. To install it, do

 	Code:
 	$ sudo apt-get update
$ sudo apt-get install macfanctld 
To learn more about it, do look at the man page, 'man macfanctld'.

Cheers!

/Mike[/I]


Thanks, it worked! :D

---

### Post by PBG4 on 2010-09-03
Hi, Just checking, is macfanctld only suitable for intel macs?

Cheers,

Allen

---

### Post by SwedishWings on 2010-09-03
> **PBG4 said:**
> Hi, Just checking, is macfanctld only suitable for intel macs?

Cheers,

Allen

It requires applesmc-dkms to work. I'm not sure if applesmc-dkms is ported to PowerPC. If it is, it should be working, or at least be relatively simple to port.

/Mike

---

### Post by linuxopjemac on 2010-09-03
It looks it can run on PPC too (jaunty_all.deb karmic_all.deb, lucid_all.deb):
[http://ppa.launchpad.net/mactel-support/ppa/ubuntu/pool/main/a/applesmc-dkms/](http://ppa.launchpad.net/mactel-support/ppa/ubuntu/pool/main/a/applesmc-dkms/)

---

### Post by SwedishWings on 2010-09-03
> **linuxopjemac said:**
> It looks it can run on PPC too (jaunty_all.deb karmic_all.deb, lucid_all.deb):
[http://ppa.launchpad.net/mactel-support/ppa/ubuntu/pool/main/a/applesmc-dkms/](http://ppa.launchpad.net/mactel-support/ppa/ubuntu/pool/main/a/applesmc-dkms/)

Looking in the control file of the package (applesmc-dkms_0.16.1~0ubuntu1~mactel1~karmic_all.deb), it says that it's for intel macs only, but give it a shot and see if it plays!. 

```
Package: applesmc-dkms
Version: 0.16.1~0ubuntu1~mactel1~karmic
Architecture: all
Maintainer: Henrik Rydberg <rydberg@euromail.se>
Installed-Size: 40
Depends: dkms (>= 1.95), bash (>> 1.99)
Section: misc
Priority: optional
Homepage: http://bitmath.org/code/applesmc-dkms/
Description: Supplementary applesmc support
 This driver adds applesmc support for the [B][I]latest intel-based Apple
 computers[/I][/B].
```

Good luck!

EDIT:
Just browsed through the code. The known models listed in the code is as follows:

```
/* Set 0: Macbook Pro */
/* Set 1: Macbook2 set */
/* Set 2: Macbook set */
/* Set 3: Macmini set */
/* Set 4: Mac Pro (2 x Quad-Core) */
/* Set 5: iMac */
/* Set 6: Macbook3 set */
/* Set 7: Macbook Air */
/* Set 8: Macbook Pro 4,1 (Penryn) */
/* Set 9: Macbook Pro 3,1 (Santa Rosa) */
/* Set 10: iMac 5,1 */
/* Set 11: Macbook 5,1 */
/* Set 12: Macbook Pro 5,1 */
/* Set 13: iMac 8,1 */
/* Set 14: iMac 6,1 */
/* Set 15: MacBook Air 2,1 */
/* Set 16: Mac Pro 3,1 (2 x Quad-Core) */
/* Set 17: iMac 9,1 */
/* Set 18: MacBook Pro 2,2 */
/* Set 19: Macbook Pro 5,3 */
/* Set 20: MacBook Pro 5,4 */
/* Set 21: MacBook Pro 6,2 */
/* Set 22: MacBook Pro 7,1 */
```

I would not even bother to try.

/Mike

---

