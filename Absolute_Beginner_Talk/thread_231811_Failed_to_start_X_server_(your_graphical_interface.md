---
title: "Failed to start X server (your graphical interface)."
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by SeaRox on 2006-08-07
I am new to Ubuntu and Linux.  I loaded Ubuntu a few days ago and it had been working fine except for firefox.  I loaded the new version of firefox using the wiki instruction and then used EasyUbuntu to load the flash and java pulugins and it worked fine but when I started my Lunux box today it seemed to going fine and then it popped upt with a bunch of funky symbols an the error message:

"Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?"

When I hit yes it gives me:

"X Window System Version 6.8.2 (Ubuntu 6.8.2-77.1  20060503192905 [email]root@terranova.warthogs.hbd.com[/email])
Release Date: 9 February 2005
X protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.12 i686 [ELF]
Current Operating System: Linux Ubuntu 2.6.12-10-386 #1 Tue Jul 18 22:08:27 UTC 2006 i686
Build Date: 03 May 2006
     Before Reporting problems, check [http://wiki.X.org](http://wiki.X.org)
     to make sure that you have the latest version.
Module loader Present
OS Kernel: Linux Version 2.6.12-10-386 (build@terranova)
(gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6 Ubuntu8.1)) #1 Tue Jul 18 22:08:27 UTC 2006 T
Markers: (--) probed, (**) from config file, (==) default setting,"

I checked wiki.x.org and it looks like there is a version 7.1 but there weren't any FAQs on my error.  I couldn't find any threads on my error here in the Ubuntu forums either.  I don't know where to go from here.  Any help would be appreciated.

SeaRox

---

### Post by Ziox on 2006-08-07
hit ctrl + alt+ F1, this will bring you to another console, login and do this command:

sudo dpkg-reconfigure xserver-xorg

and just hit enter all the way through...

then after it's done, type

sudo reboot

that should solve your problem, but there are always exceptions...

---

### Post by SeaRox on 2006-08-07
Thanks Ziox!  It worked!

---

### Post by Ziox on 2006-08-07
> **SeaRox said:**
> Thanks Ziox!  It worked!

glad to help :p

---

### Post by dmgriver on 2006-08-21
I got the same error after upgrading, but the dpkg-reconfigure didn't work for me.  Any other ideas would be much appreciated.  I'm trying to learn, but this is still beyond me.

---

### Post by meng on 2006-08-21
dmgriver, have you tried
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
startx

---

### Post by Ek0nomik on 2006-08-21
> **meng said:**
> dmgriver, have you tried
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
startx

Thanks.  I was having troubles too.

What you said to do, just reverted back to the default right?

---

### Post by richardward101 on 2006-08-21
I also had to downgrade, anyone got any idea why yet? I'm running Xgl/Compiz if that makes a difference. (Its working fine now that I downgrade).

---

### Post by meng on 2006-08-22
> **Ek0nomik said:**
> What you said to do, just reverted back to the default right?
As I understand it, it undid the upgrade. Just to be safe (for now) I went to Synaptic and locked that version of xserver-xorg-core so that my machine will ignore upgrades for that package until the bugs are worked out.

---

### Post by HeyGabe on 2006-08-22
> **meng said:**
> dmgriver, have you tried
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
startx
Reverting to the old version worked for me, but the question is why did it the auto upgrade break X in the first place?

---

### Post by HeyGabe on 2006-08-22
Also: In case you're not checking the stickies: [Look here]("http://www.ubuntuforums.org/showthread.php?t=241254") for the latest info on the issue.

---

### Post by Ariam on 2006-08-22
> **meng said:**
> As I understand it, it undid the upgrade. Just to be safe (for now) I went to Synaptic and locked that version of xserver-xorg-core so that my machine will ignore upgrades for that package until the bugs are worked out.

Meng, 
I too had a similar problem after I updated, had to revert  back to 10.0.
  Now how do I lock in Synaptic, in order I don’t accidentally  up date this file. What are the steps.

ariam

---

### Post by meng on 2006-08-22
Go to Synaptic, find or otherwise navigate to the xserver-xorg-core package, highlight it, then somewhere in the window menu (Packages perhaps?) there is an option to Lock Package (meaning that the installed version is flagged not to be upgraded).

Mind you, when newer (fixed) versions of xserver-xorg-core come out, you'll have to manually undo this.

Another solution is just to deselect the xserver-xorg-core each time the update manager tries to convince you to update it. I'm just worried that I will forget to do this!

---

### Post by mostwanted on 2006-08-22
> **meng said:**
> 
Mind you, when newer (fixed) versions of xserver-xorg-core come out, you'll have to manually undo this.

They *ARE* out, no use in locking versions now.

---

### Post by mikelinux on 2006-08-22
Hello guys,

none of the fixing above worked for me.
I updated from 5.10 to 6.06, then run the:
sudo dpkg-reconfigure xserver-xorg
then the downgrade...
but still no success.

I am running it (and was working great with 5.10) in a IBM T20 laptop.

Thanks for your help.
mik

---

### Post by Ziox on 2006-08-22
> **mikelinux said:**
> Hello guys,

none of the fixing above worked for me.
I updated from 5.10 to 6.06, then run the:
sudo dpkg-reconfigure xserver-xorg
then the downgrade...
but still no success.

I am running it (and was working great with 5.10) in a IBM T20 laptop.

Thanks for your help.
mik

A fixed version of Xorg has already came out, just do:

sudo aptitude update&&sudo aptitude dist-upgrade

---

### Post by mikelinux on 2006-08-23
Thanks a lot,
it worked!

---

### Post by tombott on 2006-08-23
Cheers to everyone you helped solve the problem for me, although I tried everything but the last fix. Had to use simple settings the whole way through  on xsevrer config and do the downgrade to get it working again.

---

### Post by dmgriver on 2006-08-23
Worked great.  Thank you so much.

> **Ziox said:**
> A fixed version of Xorg has already came out, just do:

sudo aptitude update&&sudo aptitude dist-upgrade

---

### Post by mistypotato on 2007-01-05
> **Ziox said:**
> hit ctrl + alt+ F1, this will bring you to another console, login and do this command:

sudo dpkg-reconfigure xserver-xorg

and just hit enter all the way through...

then after it's done, type

sudo reboot

that should solve your problem, but there are always exceptions...



[B]Worked Exactly as described!  Kewl!!!!

Hail to ZIOX !!!!  [/B]

---

### Post by Hishgraphics on 2007-01-07
Tried the sudo dpkg-reconfigure xserver-xorg...

But when I reached "Please select your desired default color depth in bits" and hit enter, it tells me: 
```

xserver-xorg postinst warning: overwriting possibily-customised configuration file; backup in /etc/X11/xorg.conf.20070107155321
```

Earlier I tried to install the NV5 TNT2 graphic driver because video playback was stuttering. Any help would be hot. Thanks.

---

### Post by MkfIbK7a on 2007-01-07
nothing is wrong with that message...

---

### Post by Hishgraphics on 2007-01-07
> **wert613 said:**
> nothing is wrong with that message...
Aaand... apparently you're right. ](*,) 

The sudo reboot went well. I'll be over the with my head buried in the sand in embarrassment.

Thanks, wert613.

---

### Post by MkfIbK7a on 2007-01-07
lol its ok everyone makes mistakes :mrgreen:

---

### Post by Shakarhaba on 2007-03-01
Hey, Im having a problem when Installing Ubuntu 6.10 (Its a new installation) the CD is correct as I installed it into another computer without problems the thing is that my laptop a AMILO M1437G has an ATI card.

I did what I read in the Ubuntu wiki.
Hit F6 in the installation screen delete "splash" and add break=bottom
I changed everything said there [https://wiki.ubuntu.com/EdgyKnownIssues/59618](https://wiki.ubuntu.com/EdgyKnownIssues/59618)

But I still get one error when tryng to install, the X Server error in the first post.
I did what you said, I pressed Enter in every screen and then I typed 
sudo reboot.

but it just open the physical CD-drive and a message appears "The system is going o reebot NOW!" after that nothing happens, I can  write but I cant hit control or backspace for example I get ^M for ENTER and ^? for Backspace

I cant continue with the installation, what should I do?

---

