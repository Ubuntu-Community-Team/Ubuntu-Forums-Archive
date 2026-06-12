---
title: "Why is the sound quality in Ubuntu so much worse than Mac OS X? (MBP 3rd gen)"
date: 2008-06-11
forum: Apple Hardware Users
---

### Post by psyke83 on 2008-06-11
*This is a reposted reply to an archived thread [here]("http://ubuntuforums.org/showthread.php?t=707092") asking why sound quality is worse in Ubuntu compared to MacOS X. Since I do not own a Mac I cannot say for certain this is the same reason why users experience poor audio in Ubuntu, so take everything with a grain of salt. ;)*

Hi,

I don't have any Mac hardware, but I did make a discovery about Sigmatel audio chipsets on laptops. On my Dell Inspiron 510m (with a Sigmatel STAC9750,51 / ICH4 chipset), here is an overview of the audio quality under different conditions:

1. Windows XP, using generic WHQL "Intel AC'97 Audio" drivers: audio sounds bad. Built-in laptop speakers sound distorted at medium to high volume (almost as though the speakers are loose/damaged) with bad frequency response (high quality audio sounds closer to 22050Hz).

2. Windows XP, using Sigmatel drivers from Dell: audio quality is very good, sounds are richer with no distortion even at high volume.

3. Ubuntu (also Fedora, openSUSE and I presume all Linux distributions): audio quality is identical to case 1 above (bad).

After doing some research, I discovered that Sigmatel's XP drivers have a built-in 10-band equalizer. Even though there is no Control Panel applet or GUI to configure these bands, all the bands and their gains are visible from the Windows registry. Oddly enough, if you edit any of the bands via the registry, they reset to defaults upon a reboot.

After doing some hacking I realized that EQ settings are not stored in the driver, but in the laptop's BIOS, and the generic AC'97 driver does not use these settings. I chatted with somebody (who may or may not work for Dell... under the condition of anonymity, heh) and they confirmed my theory; it seems that Sigmatel chipsets contain proprietary extensions to handle equalization, of which neither ALSA or OSS can exploit.

Although we may not be able to expose the same part of the hardware to use hardware EQ, we have other solutions. For Hardy/PulseAudio users, I wrote a guide that includes instructions to set up a 15-band EQ with settings that gives my laptop perfect sounding audio. All I can suggest is that you give it a shot and see if it helps you too!

Here's the guide, and Part D deals with the EQ: [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

### Post by +peter on 2008-06-11
I have been wondering the exact same question. Thanks for the research, I will be checking out your guide soon!

---

