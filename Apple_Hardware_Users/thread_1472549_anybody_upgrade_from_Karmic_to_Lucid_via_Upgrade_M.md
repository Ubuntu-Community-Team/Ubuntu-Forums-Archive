---
title: "anybody upgrade from Karmic to Lucid via Upgrade Manager?"
date: 2010-05-04
forum: Apple Hardware Users
---

### Post by miatawnt2b on 2010-05-04
How did it work out?  What model machine are you using?

Just wanted to get some idea of stability/functionality.
-J

---

### Post by avtolle on 2010-05-04
I did, when 10.04 was at Beta2. Model: G4 Cube. Have not had any issues on this computer with stability, etc. All updates have gone well, no problems on this end. However, tip (works for me) on shutdown/log off. If there is anything running, e.g., OpenOffice Quickstarter, the computer won't shut down, etc. Closing everything before shutting down  or logging out takes care of the problem. Same issue with another Cube with fresh install (from alternate CD), same solution.

---

### Post by linuxopjemac on 2010-05-05
If you can afford it to have a broken box I would say do it. If you rely on it for daily work, I would not recommend to upgrade, until all issues about your specific computer are solved.

---

### Post by npfthunfan on 2010-05-05
I had to do an upgrade because of my lack of working superdrive (won't read burned discs only pressed ones)... seems to work fine.

---

### Post by Nikos.Alexandris on 2010-05-05
Anybody upgraded to Lucid an MBP5,1?

Thanks

---

### Post by DougieFresh4U on 2010-05-06
I tried on my **iMac G3 750 POWERPC**
Did not work, machine would 'lock up' and the monitor did not work. Had to use external monitor to see the 'lock up'

---

### Post by jacques4x4 on 2010-05-06
I tried it on a MBP 5,5  I ended up with a flashing cursor..

---

### Post by linuxopjemac on 2010-05-06
I think for us Mac users the advise is clear: don't upgrade unless you are brave.

---

### Post by cyberco on 2010-05-06
I managed to on my macbook air 2,1. I had to repair GRUB in the MBR (sudo grub-install --recheck --root-directory=/mnt/sda4 /dev/sda), and a few things didn't work out of the box, but all in all I am glad I upgraded. The most important reason being that Lucid runs MUCH faster on my Air.

More info here:
[https://help.ubuntu.com/community/MacBookAir2-1/Lucid](https://help.ubuntu.com/community/MacBookAir2-1/Lucid)

---

### Post by grimsbyguy on 2010-05-06
On a whitebox PC - mobo is Gigabyte MA785GMT-UD2H, CPU is AMD Athalon II quad, 4 gig ram, 1 Terra HD (was Ubuntu 9.10) and 500gig (Win XP/NTFS) dual boot and working flawlessly after a few initial kinks last December.

I ran the upgrade and it was bad news. Had to reinstall XP and fresh install Lucid (luckily all data was backed up - not that I am paranoid but I don't trust updates). Initial symptoms were black screen and no response but did notice that it was not running and from system response (beeps, etc) I did find that something was running "behind" that black display. - Spent 2 days on the basic rebuild and gave me an excuse to do a bit of revamping. BUT... a very bad experience and I will avoid "upgrades" in future. (Not a newbie here, have about 12 years Linux experience and never had issues like this with any other distro).

FWIW

---

### Post by Nikos.Alexandris on 2010-05-09
> **Nikos.Alexandris said:**
> Anybody upgraded to Lucid an MBP5,1?

Folks,

successful on-line upgrade here under Kubuntu Karmic Koala 64-bit to Kubuntu Lucid Lynx 64-bit :D

I've checked if grub is installed under **/dev/sda** (not **/dev/sda3**) and I got both before and after the upgrade:

```
sudo file -s /dev/sda

/dev/sda: x86 boot sector; partition 1: ID=0xee, starthead 254, startsector 1, 409639 sectors; partition 2: ID=0xaf, active, starthead 254, startsector 409640, 48565976 sectors; partition 3: ID=0x83, starthead 254, startsector 48975616, 58593751 sectors; partition 4: ID=0x83, starthead 254, startsector 107569367, 97656251 sectors, code offset 0x63
```

Could this (**sda** vs. **sda3** or some partition) be the problem why people end-up with broken grub?

Happy upgrading to everyone!

---

### Post by Nikos.Alexandris on 2010-05-09
> **npfthunfan said:**
> I had to do an upgrade because of my lack of working superdrive (won't read burned discs only pressed ones)... seems to work fine.

Not sure why I did not read your post before (as it was before my question). So, you also did an on-line upgrade on the MacBook Pro 5,1 without problems?

Cheers!

---

### Post by nmilyaev on 2010-05-14
I use MBP 5.3 aluminium unibody and it's been under BootCamp from the beginning - about 6 mont, all the time under 9.10.

I had a myriad of sorfware installed, including Wine, Apache, Tomcat, and a bagfull of other IDEs and tools.

Today I upgraded by hitting the "Upgrade" button in the Upgrade manager. After 2 hours of waiting and an initial blip with a wrong video mode that went away after 2nd setup, it all looks dandy. It all went really smooth.

Have not tested it all in detail yet.

On the downside - can't see my volume applet in the toolbar ;-(.

---

### Post by JoeMac42 on 2010-05-14
Going from Karmic to Lucid Beta 1 in VMWare virtual machine on a MBP 3,1 went fine, Beta 2 upgrade broke keyboard input - fixes found via forums, RC and final worked fine.  

Going from Karmic to Lucid PowerPC port on Windtunnel G4 broke keyboard input and I could not find a work around to bring it back.  Clean Lucid install fixed this and video worked out of the box in X for the first time ever.  I think the only time an Ubuntu version upgrade on the Windtunnel worked was 8.10 to 9.04 and I still had to edit xorg.conf to get video working in X.

---

### Post by jeffmings on 2010-12-04
I have a Compaq with an Athlon X2 that runs Ubuntu beautifully.  Just upgraded from Karmic to Lucid without any issues.  I was expecting to find a problem or too, but it went very smoothly.  I was impressed by how easy it was.
Great work Ubuntu!  I love you guys!

---

