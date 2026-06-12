---
title: "Fresh install of Gutsy - And it's slower than Windows Vista!"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Exershio on 2007-10-20
I have just returned to Ubuntu after about a year, and I'm quite disappointed with Gutsy. I just installed a fresh copy of it on my system and it's running quite slow. I even turned off all the special effects and it still runs really slow. Doing anything on gutsy eats up a ton of CPU, nearly 5x as much as the same task on Windows XP would take (even takes more CPU than Vista!)

My system specs:
2.0ghz p4 processor
768mb ram
Radeon 9200 AGP card

I don't see why simply loading a new page in firefox takes 100% cpu, and opening a new window of anything takes 30-40%.

Can someone help enlighten me as to what the problem is?

---

### Post by Espreon on 2007-10-20
Hmm, I have a $1,000 Dell E1705 Laptop and EVERYTHING works faster than XP.
I have 4 explanations

1: Gutsy Might hate you
2: Maybe M$ made a tool to sabotage Linux distros
3: Maybe the changes made in Gutsy got buggy
4: Maybe something wrong happened during the installation process

Try to reinstall Gutsy and a TOTALLY fresh one too.

---

### Post by Colro on 2007-10-20
I wouldn't call it 'slower then vista' -- but I am having problems with firefox taking 100% CPU load to just render a page (not to mention that it just runs sluggish in general). Hell, it seems like Gutsy is unable to IDLE at 0% CPU usage with minimal programs open.

1.8ghz AMD Athlon+
1.5gb ram
Radeon 9600 pro

---

### Post by nudnik on 2007-10-20
There could indeed be something wrong with your install. However, its also been my experience that distros and versions of distros can behave quite differently from one another on a given collection of hardware. For example, Debian Etch performs well enough on an old Pentium III machine of mine, but Ubuntu 7.04 is a bit faster and more agreeable on the same unit. Similarly, the 386 version of Debian had a tendency to become corrupt on a certain AMD machine, whereas the 64 bit version of the same distro, as well as all versions of Windows ran fine. The point of all this rambling....if all else fails, try Debian, Fedora or some other species of Linux. One of the preceding may function flawlessly on your machine. 

Remember the Ubuntu Mascot....](*,)  (am considering renaming it the *nix mascot as all of UNIX's children can be equally frustrating. The head wounds eventually heal, and you are rewarded with an OS that doesn't send your love letters to the NSA)

---

### Post by sayuki288 on 2007-10-20
maybe linux hated you for using windows too long :lolflag:

---

### Post by Colro on 2007-10-20
I'd really prefer to not switch to a different distro because of a performance issue that seems fairly common. I am seeming to notice that it's happening to ATI card users the most --
OP: Do you happen to be using XGL? I've got it in order to use desktop effects, and when the effects are disabled this problem grows **worse**, leading me to believe that it could be part of the problem.

---

### Post by nudnik on 2007-10-20
> **Colro said:**
> I wouldn't call it 'slower then vista' -- but I am having problems with firefox taking 100% CPU load to just render a page (not to mention that it just runs sluggish in general). Hell, it seems like Gutsy is unable to IDLE at 0% CPU usage with minimal programs open.

1.8ghz AMD Athlon+
1.5gb ram
Radeon 9600 pro

Verily....I seeth an ATI pattern emerging. Lets keep an eye out to see if other ATI users are having similar troubles. I'm running an Intel chipset with a Nvidia card and have suffered no ill effects thus far.

---

### Post by Exershio on 2007-10-20
> **Colro said:**
> I'd really prefer to not switch to a different distro because of a performance issue that seems fairly common. I am seeming to notice that it's happening to ATI card users the most --
OP: Do you happen to be using XGL? I've got it in order to use desktop effects, and when the effects are disabled this problem grows **worse**, leading me to believe that it could be part of the problem.
I really don't know what XGL is. I just hope this problem gets fixed, whatever it may be. I don't really want to try another distro.

---

### Post by Espreon on 2007-10-20
Like me, your gonna need it for those effects.

All you do is do this in a terminal:

```

sudo apt-get install xserver-xgl

```

Make sure the restricted driver is enabled if not reboot, if it is enabled then just log out and back in and enjoy.

---

### Post by sayuki288 on 2007-10-20
why don't you try xubuntu/xfce desktop instead of gnome its for old desktops :)

---

### Post by sandysandy on 2007-10-20
Hi

i am using the live CD of 7.10 (64 bit) and am contemplating loading it to hard disk. My previous attempt with 7.04 was unsuccessful in booting from HDD. I had to use windows disc to restore MBR which got corrupted that time after trying dual booting.

Sytem Specs 
Intel 64 bit Pentium D 3.00 GHz
160HDD (Win XP) and second HDD 40GB.
1GB Ram

would appreciate tips on dual booting with gutsy and not mucking up the MBR.

hope i am not posting to wrong forum

Thanx:guitar:

---

### Post by s.victor on 2007-10-20
You can try to fix your Firefox as shown [here]("http://ubuntuforums.org/showthread.php?t=550571").

---

### Post by Virion on 2007-10-20
Mine works fine, smooth and fast. But why I can't use the 3D desktop? My 3d desktop is like a card, only flips, instead of rotating like a box.:confused:

---

### Post by sayuki288 on 2007-10-20
you just have fix your compiz configuration to make your desktop look like a box

---

### Post by Exershio on 2007-10-20
Man, I can't believe it's running this horribly. I've even reformatted and reinstalling. The disc is error free too. Why does the system never go below 5% CPU usage even when I'm not even moving the mouse? Windows XP is starting to look really good right now >_<

---

### Post by Espreon on 2007-10-20
> **Exershio said:**
> Man, I can't believe it's running this horribly. I've even reformatted and reinstalling. The disc is error free too. Why does the system never go below 5% CPU usage even when I'm not even moving the mouse? Windows XP is starting to look really good right now >_<

Maybe your hardware isn't ready for Linux.

---

### Post by amlucent23 on 2007-10-20
> **Espreon said:**
> Like me, your gonna need it for those effects.

All you do is do this in a terminal:

```

sudo apt-get install xserver-xgl

```

Make sure the restricted driver is enabled if not reboot, if it is enabled then just log out and back in and enjoy.

One of my PCs was having the same problem. I fixed it by using this xserver I had forgotten I even had to do it as I have been using gutsy for weeks. The problem is ATIs propritary video driver not playing nice with compiz fusions default xserver. This is a stable work around (In other words blame ATI proprietary drivers). 

I am 95% sure this will fix your woes.

---

### Post by argie on 2007-10-20
Hmm, it's probably a problem with the video drivers. I've seen this before, but I don't know the fix. Perhaps enabling the restricted driver for your card, if it's possible, would help?

EDIT: Ah, just noticed that previous post. Very well then.

---

### Post by Colro on 2007-10-20
Disableing IPV6 in Firefox does help rendering times somewhat, but my processor is still idling at 10-30% as I sit here typing this with only Firefox open.

---

### Post by stijngysemans on 2007-10-20
I've got somewhat the same system as you and everything runs smooth.
Maybe it's a chipset problem?

---

### Post by 001100 on 2007-10-20
7.10 works wonders for me the desktop effetes and over all proformance in creased. I just wated 48 hrs. after the release so i couldd update it.(the servers were overloaded) But yes just redownload ubuntu 7.10 and reinstall make sure u have an internet connection
heres my hardware config....
========================
Intel P4 1.8ghz
512mb of ram
128mb nvidia mx4k
120gb hdd

---

### Post by coffeecat on 2007-10-20
> **Exershio said:**
> I just installed a fresh copy of it on my system and it's running quite slow.

With a fresh install, Beagle is doing its first big index. Could this be the problem? Either wait for Beagle to finish, or kill the process and see if this makes any difference. If this is the problem and you re-install, Beagle will have to start all over again. :)

I've seen a comment somewhere that some people found the initial Beagle indexing on Opensuse 10.3 quite intrusive, but I don't know whether that's true for Ubuntu. The niceness might be set differently in the two distros. I certainly didn't notice anything unusual with my two Gutsy Beta installations. I haven't downloaded the final yet - waiting for the servers to cool down first. :wink:

---

### Post by RSingh on 2007-10-20
Well on my system, gutsy performs flawlessly that too with full effects running. System idles at 0 - 9%. I believe it is due to the different hardware used.

My system.

1.73 Ghz CoreD
1 GB RAM
i945GM Chipset
Graphics: Onboard 950 GMA

---

### Post by knedle on 2007-10-20
Hi, I've got the same problem.
Just updated form Ubuntu 7.04 and Xorg takes aboout 60% of my CPU all the time.
I've got AMD 3000+ with 2GB of RAM and GF7600GS, so I'm 100% sure it's not old hardware. :(

---

### Post by Colro on 2007-10-20
bump

---

### Post by frozenskunk on 2007-10-26
I had this problem on an upgrade from Feisty, here is the solution that worked for me:

Upon the initial reboot from the upgrade, things were SLOW, when typing in the URL bar in firefox, there was a 3-5 second delay between characters appearing, windows would take forever to move and resize, changing desktops was painful, and so on. 

I ran top in a terminal window, and saw that XGL was taking a big chunk of resources (as a side note, I do have an ATI card with the restricted drivers enabled).

I checked my desktop  visual effects settings, and it was set to 'None', for whatever reason when I set it to 'Normal' my system immediately became responsive again, changing it to 'Extra' didn't slow it back down, and if anything speeded things up just a bit more...

No idea why enabling effects would improve performance, but without a doubt that was the thing that fixed it for me.

My hardware isn't that impressive, an old Athlon 1800+ with 512M ram, and an ATI 9600.

---

### Post by ronmarley1 on 2007-10-26
> **Virion said:**
> Mine works fine, smooth and fast. But why I can't use the 3D desktop? My 3d desktop is like a card, only flips, instead of rotating like a box.:confused:
Right click on the switcher and go to Preferences.  Change columns to 4.

---

### Post by jenhsun on 2007-10-26
Or this thread to up your net speed.
[http://ubuntuforums.org/showthread.php?t=590242](http://ubuntuforums.org/showthread.php?t=590242)

Speed up gutsy boot time, try
edit /etc/usplash.conf to 1024x768
run sudo update-initramfs -u -k 'uname -r'

---

### Post by philinux on 2007-10-26
have a look at system monitor to see whats using the processor.

It might be trackerd. it might need configuring

---

