---
title: "New to linux - Few minor issues with lappy setup"
date: 2005-07-26
forum: Absolute Beginner Talk
---

### Post by YuriSEAL on 2005-07-26
So far, this has all been much easier than expected, but I was wondering how to do a few things:
1)Eventually, I managed to get my audio working through the hda-intel ALSA mixer, but the Realtek audio OSS mixer still doesn't work. This doesn't seem to be a big problem with most apps, but Realplayer isn't working and I'd rather like to watch some vids I have kicking around in .rm format. So can anyone recommend a solution for getting the OSS up and running? My specs are as follows:

Asus Z71V (Z7100)
1.86 GHz Pentium M (533 MHz FSB)
1 GB DDR2 533 (2x512MB)
GeForce 6600 Go
Intel a/b/g wireless card (not sure of the exact model)
Onboard Realtek audio (Azalia)
80 GB 5400 RPM drive (partitioned: 25 GB Windows XP (NTFS) / 15 GB Linux (ext2/3?) / ~40 GB data (FAT32/VFAT)

2)My wireless connection is detected and it claims that there is connectivity. However, it doesn't get any DNS information, so I'm dubious. I'm using WEP on the connection, and I put in both the key and the host name (paying attention to caps). Still, nothing's coming up.

3)As I noted already, I have a data partition. I've already figured out how to mount it, but I understand that I would be able to edit a file to have the partition auto-mounted every time I boot. This would be preferable, as the partition is simply there to hold data (music, videos, etc) that I want to keep common between Windows and Linux.

4)I'm using a Logitech MX3100 duo (MX3000 keyboard and MX1000 mouse.) They work out of the box (which is to be expected, as they even work in my BIOS), but it doesn't support all of their extra buttons. Has anyone made drivers for these? Are there any applications that may be able to detect a 8+ button mouse and a keyboard with extra buttons properly and configure them?

5)Similarly, the notebook has buttons on the front for media playback. Is there any way to get the system to recognize these?

I must say, this has all been much easier than I expected so far, and the things I took for granted that I'd lose weren't lost - although some things were lost that I didn't fully expect.

Thanks for any help you can offer!

---

### Post by sigma2805 on 2005-07-26
regarding your wireless connectivity, are you using ndiswrapper?

---

### Post by poofyhairguy on 2005-07-26
Welcome. Sorry for the delay.

[QUOTE=YuriSEAL]
1)Eventually, I managed to get my audio working through the hda-intel ALSA mixer, but the Realtek audio OSS mixer still doesn't work. This doesn't seem to be a big problem with most apps, but Realplayer isn't working and I'd rather like to watch some vids I have kicking around in .rm format. So can anyone recommend a solution for getting the OSS up and running? My specs are as follows:

Asus Z71V (Z7100)
1.86 GHz Pentium M (533 MHz FSB)
1 GB DDR2 533 (2x512MB)
GeForce 6600 Go
Intel a/b/g wireless card (not sure of the exact model)
Onboard Realtek audio (Azalia)
80 GB 5400 RPM drive (partitioned: 25 GB Windows XP (NTFS) / 15 GB Linux (ext2/3?) / ~40 GB data (FAT32/VFAT)[/QUOTE]

I'll tell you my personal answer: wait for Breezy. Its big feature will be that the sound stuff will be ironed out. If you can't wait there are howtos on the forum to "fix" that stuff, but I won't link them because a few broke my box to the point of reinstall.

> 
2)My wireless connection is detected and it claims that there is connectivity. However, it doesn't get any DNS information, so I'm dubious. I'm using WEP on the connection, and I put in both the key and the host name (paying attention to caps). Still, nothing's coming up.

Just to find out: does it work when you disable WEP on both ends? Then we know where the problem lies.

> 3)As I noted already, I have a data partition. I've already figured out how to mount it, but I understand that I would be able to edit a file to have the partition auto-mounted every time I boot. This would be preferable, as the partition is simply there to hold data (music, videos, etc) that I want to keep common between Windows and Linux.

[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

Remember, Linux can only read NTFS partitions, not write to them.


> 4)I'm using a Logitech MX3100 duo (MX3000 keyboard and MX1000 mouse.) They work out of the box (which is to be expected, as they even work in my BIOS), but it doesn't support all of their extra buttons. Has anyone made drivers for these? Are there any applications that may be able to detect a 8+ button mouse and a keyboard with extra buttons properly and configure them?

Well...there is not a simple way. There is this, ways that work:

[http://www.ubuntuforums.org/showthread.php?t=28374](http://www.ubuntuforums.org/showthread.php?t=28374)

[http://www.ubuntuforums.org/showthread.php?t=34680&highlight=button](http://www.ubuntuforums.org/showthread.php?t=34680&highlight=button)

> 5)Similarly, the notebook has buttons on the front for media playback. Is there any way to get the system to recognize these?

Maybe. Only if its a Thinkpad or some toshibas...only with Thinkpads is it easy to do. Search synaptic.

> 
I must say, this has all been much easier than I expected so far, and the things I took for granted that I'd lose weren't lost - although some things were lost that I didn't fully expect.


Can you explain that please?

---

### Post by YuriSEAL on 2005-07-26
[QUOTE=sigma2805]regarding your wireless connectivity, are you using ndiswrapper?[/QUOTE]
No, I'm not. It was detected out of the box (during the install, actually), so I didn't expect that to be a big problem. :-/ I'll try with ndis.

[QUOTE=poofyhairguy]I'll tell you my personal answer: wait for Breezy. Its big feature will be that the sound stuff will be ironed out. If you can't wait there are howtos on the forum to "fix" that stuff, but I won't link them because a few broke my box to the point of reinstall.[/QUOTE]
I can manage that, I suppose, since most applications seem to have sound and I can switch back to Windows for most.

[QUOTE=poofyhairguy]Just to find out: does it work when you disable WEP on both ends? Then we know where the problem lies.[/QUOTE]
I'll try that before I start playing with ndiswrapper.

[QUOTE=poofyhairguy][http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)
Remember, Linux can only read NTFS partitions, not write to them.[/QUOTE]
No problem, as I'm using a FAT32 partition for data. I just wanted to know how to auto-mount it.

[QUOTE=poofyhairguy]Well...there is not a simple way. There is this, ways that work:

[http://www.ubuntuforums.org/showthread.php?t=28374](http://www.ubuntuforums.org/showthread.php?t=28374)

[http://www.ubuntuforums.org/showthread.php?t=34680&highlight=button](http://www.ubuntuforums.org/showthread.php?t=34680&highlight=button)[/QUOTE]
Thanks! I'll try those out.

[QUOTE=poofyhairguy]Maybe. Only if its a Thinkpad or some toshibas...only with Thinkpads is it easy to do. Search synaptic.[/QUOTE]
Damn. It's an Asus notebook, so I'm out of luck, it seems.

[QUOTE=poofyhairguy]Can you explain that please?[/QUOTE]
I just was surprised by some of the things that worked out of the box, and surprised again by a few of the things that didn't. Nothing big.

---

