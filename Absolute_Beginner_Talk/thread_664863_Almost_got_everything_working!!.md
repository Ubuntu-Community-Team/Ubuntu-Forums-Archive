---
title: "Almost got everything working!!"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by kevin_mccauley22 on 2008-01-11
I almost got everything working on my installation of Unbuntu 7.04.  I had to install ubuntu because my internal Hard Drive went bad.  

LAN works, Video works, keyboard & mouse works.

However, the only real glitch is the Realtek HD ALC883 Audio Card.

> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
**_00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)_**
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)


This is what I get with the lspci command.  I can live without the WLAN card, the Graphic 3-D features.  However I do not own a stereo and I want to listen to my music.  Thus I want the sound card to work.  I can even live with out the Multi-card reader.  If anyone can help, please do.  I will appricate it greatly.  I am kind of a newbie when it comes to linux.  (got certified 3x for Windows).  Thanks in advance.

PS - When I tried the drivers from Realtek, I got error messages saying "Your session did not last at least 10 seconds..."  <---Don't know what that is about.

---

### Post by geirha on 2008-01-11
That type of audio card is a bit problematic in linux, you might have luck installing the latest version of alsa. The procedure is explained here: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by Arthur Archnix on 2008-01-11
You may also find that the latest version of Ubuntu (7.10, Gutsy) fixes a lot of these issues. You should download the live cd and boot it up to see if it detects your hardware better than 7.04, Feisty.

---

### Post by kevin_mccauley22 on 2008-01-11
Thanks, I did not realize that there was a new version out already.  I will try that one first then I will try the ALSA way.  Thanks for all the help.

---

### Post by kevin_mccauley22 on 2008-01-15
after several hours of not finding anything, I stumbled upon this and it works (well almost)

> The intel ICH7 chipset (yours) has well-discussed problems.

gedit /etc/modprobe.d/alsa-base ...and add:

snd-hda-intel model=3stack

reboot.

Now I have sound in everything EXCEPT the web browser...and it is only when  headphones are plugged in (which is fine with me because I have a set of powered speakers and an amplifier to use in place of headphones) however I like to watch internet cartoons like Neurotically Yours, but after installing both versions of flash, I still have NO sound in my browser.  Did I do something wrong?

---

### Post by Arthur Archnix on 2008-01-16
No, if there's just one program where sound isn't working it's almost certainly an issue with that program alone. You can test this by installing a different browser and testing to see if you have sound.

Try installing opera and seeing if you can replicate the sound problem. If you currently have firefox installed, try completely removing it via synaptic, then reinstalling it.

---

