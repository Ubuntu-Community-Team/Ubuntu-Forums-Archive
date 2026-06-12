---
title: "Just installed ubuntu 7.04 and there is no sound"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Lordcoca on 2007-04-23
Is there an easy fix to this? I'd consider myself tech savvy, but after reading through some of the fixes posted around here I'm just left scratching my head thinking, wtf are they talking about?

I typed in aplay -l into the terminal and got this:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

So I guess my sound card is recognized? Any advice as to where to do next? Also the comptuer isn't muted :confused:

---

### Post by Lordcoca on 2007-04-23
I'm dual booting vista btw, and when I switch over to vista the sound works just fine.

---

### Post by Pobega on 2007-04-23
lspci | grep Audio

If a card is listed then you might want to run "alsaconf" and load the drivers for your sound card. After you load it, if it works, run alsactl to save your settings for the next reboot.

---

### Post by Lordcoca on 2007-04-23
> **Pobega said:**
> lspci | grep Audio

If a card is listed then you might want to run "alsaconf" and load the drivers for your sound card. After you load it, if it works, run alsactl to save your settings for the next reboot.

Alright, sounds good, now how I go about doing any of that?

---

### Post by Lordcoca on 2007-04-23
I'm using a Toshiba A135-s4427 laptop if that info helps at all.

---

### Post by Lordcoca on 2007-04-23
> **Pobega said:**
> lspci | grep Audio

If a card is listed then you might want to run "alsaconf" and load the drivers for your sound card. After you load it, if it works, run alsactl to save your settings for the next reboot.

Ok, when I run lspci | grep Audio I get this:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

when I type alsaconf in it gives me bash: alsaconf command not found

---

### Post by faylix on 2007-04-23
I am having sort of the same problem, My sound just quit working after i tried to hibernate. I have the same output from both commands he ran, but an IBM Thinkpad. My sound was working before however. 

-J

---

### Post by IainT on 2007-04-23
I've had a couple of issues with sound in 7.04

My not particularly expert solution was to uninstall and then reinstall alsa. It's worked for me after two bizarre gnome crashes seemingly caused by me opening synaptic with a terminal already open.

Here's the thread - [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

NB - when uninstalling alsa as per those instructions it does remove gnome-desktop so make sure that you reinstall as he says.

---

### Post by s@bertooth on 2007-04-23
same problem here...the sound worked great on edgy but now on feisty it doesn't...hda-intel soundcard...if i type alsaconf it says command not found... :(

IainT...i'm going to try that thanks

---

### Post by Lordcoca on 2007-04-23
This is ridiculous, as annoying as Vista was, this problem is 1000x times more irritating :mad:

---

### Post by Lordcoca on 2007-04-23
Should I just uninstall 7.04 and downgrade to the last release of ubuntu? Would that solve this?

---

### Post by faylix on 2007-04-23
I have found that completely powering down my laptop, then powering it back up restores the sound. 

Just restarting does not. 


Can anyone explain this? :mad: 

-J

---

### Post by Lordcoca on 2007-04-23
Doesn't anyone have any easy advice? All this working through the terminal is the least user friendly system I've ever encountered :mad:

---

### Post by madscientist on 2007-04-24
I upgraded to Feisty today and my sound stopped working as well.  I rebooted and used my older Edgy kernel, and sound worked again, so it was pretty obviously a kernel problem and nothing to do with userspace.

I followed the note in this thread [http://ubuntuforums.org/showthread.php?t=414827](http://ubuntuforums.org/showthread.php?t=414827) and after modifying /etc/modprobe.d/alsa-base as described and rebooting into the standard Feisty kernel, sound now works!

HTH!

---

### Post by kittyhawk63 on 2007-04-25
I have no sound either.
Dapper, Kubuntu, Xubuntu, and Edgy all had sound.

lspci | grep Aucio gave the following:

[B]kittyhawk63@kittyhawk63:~$ lspci | grep Audio
00:14.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)
kittyhawk63@kittyhawk63:~$[/B]

Any help would be greatly appreciated. 

BTW, how do you type the character:** |** that you see between**lspci | grep**?
kh

---

### Post by 007Bond on 2007-04-25
Try going into the sound preferences by clicking on the sound icon ( top right corner ) and go to preferences and click duplicate front. This worked for me. Hope it helps.:)

---

### Post by Loki-uk on 2007-04-25
There is an easier way to get 'most' sound cards working and it's here > [http://www.aotk50.dsl.pipex.com/install-ubuntu-sb16/install-ubuntu-sb16.htm](http://www.aotk50.dsl.pipex.com/install-ubuntu-sb16/install-ubuntu-sb16.htm) This is an SB16 install guide but it tells you what to change for different sound cards.

Loki

---

### Post by kittyhawk63 on 2007-04-25
Well, I discovered that Feisty had "turned off" my speakers. I clicked on the volume control with my right mouse button and chose **Open Volume Control**. There I found that everything had been deactivated but the first choice...**Master**. 
I clicked all the other  choices, **PCM**...**Line-in** ...**CD**...**Microphone**...**Speaker**.
Thanks for putting me onto the right trail. It helped me resolve my problem. Now if only fixing my screen freezes was as easy.
kh

---

### Post by 007Bond on 2007-04-25
Yeah np I just love to share my discoveries with others to make their life simpler.

---

