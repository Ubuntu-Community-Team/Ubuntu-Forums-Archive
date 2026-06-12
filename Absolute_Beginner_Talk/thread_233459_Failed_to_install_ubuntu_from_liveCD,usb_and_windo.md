---
title: "Failed to install ubuntu from liveCD,usb and windows"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by tiktakit on 2006-08-10
Hi,
Im trying for two weeks to install ubuntu-desktop 6.06 on my computer:
Celeron 2.4 Ghz, 256 Ram, which i allocated 10 GB free memory.

I recently erased mandriva (newest version) that was installed from CD and worked well.
This is a description of my installation sessions, and the problem i encountered:

1. I burned 4 diifferent ISO images (Live Cd version), d/l from different servers, two of ubunutu desktop, two of ubunutu-server. 
The liveCD is running VERY slow, and in 3 of the 4 (2 desktop,1 server) the installation stucked at stage 3 (after language chosen). the forth cd was defected. I successfully managed to install twice the ubuntu from my CD's on 2 other different comupter: a laptop and a regular one.

2. I tried USB stick installation, followed ubuntu's site manual. after rebooting from USB i got this error: "boot: canno't open /casper/.vml"

3. Then I tried from windows installation. I was first trying to change boot.ini myself and write menu.lst, and copy the cd content to C:\,as described in this site appropriate manual. After booting, i recivied this error: "the file hal.dll is missing 
or corrupt, please re-install it". 

4. So I tried INSTLUX, which suppose to automate what i did in stage 3 (i think without copying the ubuntu content cd, but i left the ubuntu folder i copied on stage 3). It worked halfway. the installation did start (non-graphic) but when trying to copy from CD (why?? anyway i ejected the installation CD inside when it was requested - tried both) i got an error: "cannot read from CD. check CD for defects". I again remind that from these Cd's i installed ubuntu on other computers.

5. Trying again stage 4, i tried SOMEHOW, with my very short understanding of linux, to define my USB stick as the cdrom that should be read from. i tried something like ln -s /dev/sda1 cdrom0, but i recivied a msg that cdrom0 already exist - These commands were receivied from the USBstick manual.

6. I also tried, thanks tu Jack_spparow from #ubuntu, to set my usb stick from full speed to high speed (from 2.0 to 1.1 i think) on the bios def's, and install from CD/stick again. filed the same as described above.

So i figured (....) i have hardware problem. I suppose.. but i did install mandriva, so is there a way to skip this problem ?? 
I didn't try network installation, I fear the most that it will not be perfect and i'll spent all my waking time in installing missing packages like language and key support, etc etc.. I also didn't try non-liveCD installation - if any1 tells me it'll work, i'll d\l the version :].

So what do u suggest? i'm very intrested of installing ubuntu. :confused:

---

### Post by aeiah on 2006-08-10
did you try the alternative cd installation? it uses the old install method, not the live cd method. or perhaps you could install ubuntu 5.10 and upgrade.

if you suspect its a hdd error (which seems odd if mandriva installed fine) you could check it out with some diagnostic software

---

### Post by tiktakit on 2006-08-10
I ran memtest and it worked ok.
I didn't not try the alternate install. so i shall try and update u.

---

### Post by tiktakit on 2006-08-10
can u get me a link to the download page ? i can't find it

---

### Post by aeiah on 2006-08-10
ubuntu.com, then click download, then select your country. the file that you'll want for the alternate install is probably 'ubuntu-6.06.1-alternate-i386.iso'

unless you have a non x86 cpu or want a specialised kernel

---

