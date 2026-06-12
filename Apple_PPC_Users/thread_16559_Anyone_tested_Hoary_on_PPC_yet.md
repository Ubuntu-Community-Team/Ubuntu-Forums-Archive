---
title: "Anyone tested Hoary on PPC yet?"
date: 2005-02-22
forum: Apple PPC Users
---

### Post by jocknerd on 2005-02-22
I tried upgrading last week to it but had lots of problems.  Mainly seemed to be around some Python modules from what I recall.  I added the Hoary lines in my sources.list file and tried both apt-get dist-upgrade and apt-get upgrade but still was unable to upgrade.

---

### Post by Pineault on 2005-02-22
Lots of people have, look through the threads and take a look at the hoary development list archives, here: [http://ubuntuforums.org/forumdisplay.php?f=21](http://ubuntuforums.org/forumdisplay.php?f=21)
BTW I have hoary running on a G4 Ibook
started with warty, then added hoary to apt sources (did you add all the sources), did a n apt-get update, apt-get dist-upgrade, then a couple more shots of apt-get upgrade till things stabilized. Didnt't use synaptics, don't know why but don't trust it for this kind of important work...

System is running well mimium of glithches, just haven't gotten around to configuring sleep yet, have to patch kernel, big job...

good luck

---

### Post by wsg on 2005-02-23
[QUOTE=Pineault]Lots of people have, look through the threads and take a look at the hoary development list archives, here: [http://ubuntuforums.org/forumdisplay.php?f=21](http://ubuntuforums.org/forumdisplay.php?f=21)
BTW I have hoary running on a G4 Ibook
started with warty, then added hoary to apt sources (did you add all the sources), did a n apt-get update, apt-get dist-upgrade, then a couple more shots of apt-get upgrade till things stabilized. Didnt't use synaptics, don't know why but don't trust it for this kind of important work...

System is running well mimium of glithches, just haven't gotten around to configuring sleep yet, have to patch kernel, big job...

good luck[/QUOTE]
 How about the LIVE CD version?  Any reports?

Thanks...

---

### Post by ssam on 2005-02-23
it runs very well for me. i installed from array cd 4. i am running a powerbook ti G4 1GHz, which seems to be a very easy mac to use for linux

---

### Post by wsg on 2005-02-23
[QUOTE=ssam]it runs very well for me. i installed from array cd 4. i am running a powerbook ti G4 1GHz, which seems to be a very easy mac to use for linux[/QUOTE]
 Hi, ssam...

Are you running from a hard-drive installation...or from the CD-drive ?

Thanks...

---

### Post by Leonida on 2005-02-23
[QUOTE=wsg]How about the LIVE CD version?  Any reports?
Thanks...[/QUOTE]

Hoary live-CD PPC works very fine on my iBook G4 933Mhz, see this [page](http://www.freesmug.org/newsitems/news065).
Instead I've a lot of menu icons missing with the install CD :(

---

### Post by betterok5 on 2005-02-23
No success to report here yet.  Have been working with hoary live cd.  Have not been able to boot from it but have gotten the installer to start.  It goes south when it can't find the cd.  Using a beige G3.  I did, however, get Debian/woody going yesterday after fighting with it off and on for 6 months or so.  Am writing this from linux now.  Linux is a beautiful thing if you can manage to get it going. I have ordered the cd installer and intend to try it.  I will probably use a separate drive for it since I now have a intall of Debian that I don't want to erase.
 kk

---

### Post by wsg on 2005-02-23
[QUOTE=Leonida]Hoary live-CD PPC works very fine on my iBook G4 933Mhz, see this [page](http://www.freesmug.org/newsitems/news065).
Instead I've a lot of menu icons missing with the install CD :([/QUOTE]
 Thanks, Leonida...

Can you access the internet via dialup modem using the CD ?

Regards...

---

### Post by nubeiro on 2005-02-25
[QUOTE=Pineault]
System is running well mimium of glithches, just haven't gotten around to configuring sleep yet, have to patch kernel, big job...
[/QUOTE]

Not with latest kernel image (2.6.10-4). I'm on a G4 ibook (800mhz) and sleep is working. Trouble is that usb devices don't seem to wake up. Any ideas?

---

### Post by statico on 2005-02-27
I'm running Hoary on my Powerbook G3 (Pismo/dual firewire).

Close-lid-suspend and open-lid-resume work fantastically. At one point I resumed the laptop and it immediately kernel panicked -- except that it was a Solaris kernel panic. Once I nudged the trackpad I realized it was the Blue Screen Of Death (bsod) screensaver. (slaps forehead)

The no-icons-in-menu bug bit me after the upgrade, which I cured with ```
sudo rm -f /usr/share/icons/*/*.cache
```
I also forced the Warty version of the gtk2-engines-industrial package, otherwise the white cursor disappears after an upgrade.

For some reason, Firefox's icons revert to the default Gnome browser icons, so I installed a separate Firefox theme to make the browser buttons look pretty again.

---

### Post by Leonida on 2005-02-28
[QUOTE=wsg]Thanks, Leonida...
Can you access the internet via dialup modem using the CD ?
Regards...[/QUOTE]
Sorry, I access internet via ethernet/lan and it work both using live CD and HD install.

---

### Post by Ubuntu_User on 2005-03-12
[QUOTE=Leonida]Hoary live-CD PPC works very fine on my iBook G4 933Mhz, see this [page](http://www.freesmug.org/newsitems/news065).
Instead I've a lot of menu icons missing with the install CD :([/QUOTE]

I upgraded from Warty to Hoary online. If you mean in the Gnome menu (i.e. the trash icon, folder icons, etc.) it might be a theme problem (as it was for me)

from the Gnome Menu, select:

**System - Preferences - Theme**

and then click:

**Theme Details**

poke around at the settings until you find what you like and the icons should return if that is what the problem was.

Disclaimer: I am an ubuntu newbie, but learning (also, I logged in via BugMeNot ;)

---

### Post by panabar on 2005-03-12
I couldn't use the gnome with hoary preview release. My Imac G5 booted normally but hardware detection stuck at cdrom detection. 
The message was clear " No common CDROM devices detected." :(

I've changed into another console and looked into /dev and to my suprise there was no hdx or sdx or anything that could be hdd or superdrive. :(

I have a superdrived Imac G5 1.8.

I Hope, one day I can to use Ubuntu on Imac G5.

---

### Post by meyerm on 2005-03-13
Hi,

has anybody also tested the CD on a pegasos2? I don't want to waste bandwith for another "doesn't even boot" image *.

Thank you

Marcel

*) The CD is burned correctly - there are issues with the kernel.

---

### Post by DJ_Max on 2005-03-13
You can see my experiences at [http://ubuntuppc.webplazahosting.com/index.php?Ubuntu%20Linux%205.04%20%28Alpha%29%20iMac%20G3](http://ubuntuppc.webplazahosting.com/index.php?Ubuntu%20Linux%205.04%20%28Alpha%29%20iMac%20G3)

---

### Post by Suparious on 2005-04-28
BTW, did dyou need to use Xpostfacto to boot the install CD? I have a Beige G3 300MHz, which I have 10.3.x running on it and even if I disable aqua it still takes 1-2secs to resolve a hostname. I would like to use it as my primary nameserver and pop/smtp/webmail server. I don't care is mail is slow, but 2secs to translate a name to an IP is just to long.

I figured that I would try opendarwin, but I really have no attachments to the Mac. I simply bought my G3 (for $100CDN!!) to learn how to troubleshoot mac's for my work (I'm a TSR for an ISP). I began investigating other distros for my mac and was quite happy to understand that PPC support was in the kernel.

I have been successfully running Ubuntu 5 on my two Athlon machines. One with MythTV as my PVR/game station, the other is my personal desktop. Ubuntu has been flawless (despite OpenGL [which I finally got working on my R300], but that's ATI's poor dirver support). Unless I can find something somewhere, I would like to make a step-by-step checklist to getting ubuntu on my beige g3.

Shaun

---

### Post by DJ_Max on 2005-04-28
No, the standard OpenFirmware booted it fine.

Just hold down 'c'.

---

