---
title: "Intel 965GM HP Compaq laptop 6720s Xorg problem"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by malmistry on 2007-09-28
Hi! Can someone pls help urgently. I have gone through the Ubuntu forum threads and am still not able to solve my problem. I have a new HP Compaq 6720s laptop with Intel 965GM Graphics. Problem is the same xorg. Since I can only start Ubuntu 7.04 (I used alternate CD to install) in recovery mode (command prompt), I am unable to connect to internet to do 'apt-get update'. My kernel is 2.6.20-15-generic and I am unable to upgrade it to 2.6.20-16. I edited the xorg.conf file 'media to intel' after doing the required sudo dpkg xserver-video-intel...

Is there anyways anyone can email the correct intel xorg and 2.6.20-16-generic package so that i can save it to my flash drive and try and update it from there. 

I also tried installing Ubuntu Gutsy 7.10 but the alternate cd just starts in text mode and the screen goes blank. pls help as i urgently require Ubuntu. many thanks...malcolm

---

### Post by overdrank on 2007-09-28
> **malmistry said:**
> Hi! Can someone pls help urgently. I have gone through the Ubuntu forum threads and am still not able to solve my problem. I have a new HP Compaq 6720s laptop with Intel 965GM Graphics. Problem is the same xorg. Since I can only start Ubuntu 7.04 (I used alternate CD to install) in recovery mode (command prompt), I am unable to connect to internet to do 'apt-get update'. My kernel is 2.6.20-15-generic and I am unable to upgrade it to 2.6.20-16. I edited the xorg.conf file 'media to intel' after doing the required sudo dpkg xserver-video-intel...

Is there anyways anyone can email the correct intel xorg and 2.6.20-16-generic package so that i can save it to my flash drive and try and update it from there. 

I also tried installing Ubuntu Gutsy 7.10 but the alternate cd just starts in text mode and the screen goes blank. pls help as i urgently require Ubuntu. many thanks...malcolm

Hi and welcome, have you tried to reconfigure your xorg using vesa as the driver, that has helped others in the forum. To do this at the command prompt use the command ```
sudo dpkg-reconfigure xserver-xorg
```
Choose vesa for the driver and then answer the question and if you do not know the answer then leave as the default answer is given. 
This is found in  a thread in the forums

Hey guys, solved my problem. I add this driver xserver-xorg-video-intel_2.1.0-1ubuntu1_i386.deb here:

[http://ubuntuforums.org/showthread.php?t=494943](http://ubuntuforums.org/showthread.php?t=494943)
KEYWORDS
Intel intel-video xserver-xorg-video-intel xf86-video-intel 965 965GM i965 i965GM X3100 Santa Rosa SantaRosa CentrinoDuo Centrino Duo Dell Latitude D630

Then reconfigured X11 with sudo dpkg-reconfigure xserver-xorg to manually set driver as intel and not vesa and my LCD parameters with correct screen resolutions and voila, I am even having wobbly windows now!
__________________
Hope this helps and good luck!

---

### Post by malmistry on 2007-09-29
Thks for ur reply. "have you tried to reconfigure your xorg using vesa as the driver, that has helped others in the forum".....yes i did, i tried almost everything posted on similar threads but yet not successful. My biggest problem is that I am unable to connect to internet ....i don't know why but inspite of entering the correct ip for my ISP during installation, destination host is unreachable. Thus, I am not able to do 'apt-get update' as I feel my kernel first needs to be udpated to 'linux-image-2.6.20-16-generic". I can download using my XP from the same laptop, save stuff to the other partition and access that from Ubuntu command prompt. But I don't know how to download the latest intel drivers from 'http://www.intellinuxgraphics.org/download.html' using git-clone on XP.
Pls help! thks

---

### Post by czato on 2007-10-02
I just wanted to say I have 6710s HP laptop and I'm stuck on the same problem - no network, don't know how to install drivers, no graphics.

---

### Post by gljubej on 2007-10-18
Guys, first install windows XP, then download from HP site utility for flashing BIOS with their windows XP LAN driver.

After you flash BIOS, then you will have internet connection in ubuntu through Ethernet.

Here is the link for BIOS flashing.

[http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=pl&taskId=125&prodSeriesId=3442832&prodTypeId=321957&objectID=c01185888](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=pl&taskId=125&prodSeriesId=3442832&prodTypeId=321957&objectID=c01185888)

---

### Post by gritsul on 2007-10-19
Hello,
Same problem (no ethernet card working)
same notebook HP 6720s core 2 duo (freedos initially).

Ubuntu upgraded to Gutsy (but I think it does not matter)

Does anybody knows how to do this without installing XP?
I have no such  OS distro :(

---

### Post by gritsul on 2007-10-19
Furthermore, I found something that looks like solution:

[http://forum.ubuntu.pl/viewtopic.php?t=45726](http://forum.ubuntu.pl/viewtopic.php?t=45726)

Could somebody translate it to English?

---

### Post by msylw on 2007-10-19
Essentially you have to add "pci=noacpi" to kernel options in grub configuration. 

I had the same problem and this was sufficient to fix it.

---

### Post by MrDog on 2007-11-05
Hi, I found a guide that claims to lead to a successful install of Ubuntu on the HP 6720s Laptop. Haven't tried it yet (getting the laptop in 2 days) Hope it's helpful, let us know how you go.
ahem..
[http://marcin.af.gliwice.pl/if-then-else-20071022085850](http://marcin.af.gliwice.pl/if-then-else-20071022085850)

---

