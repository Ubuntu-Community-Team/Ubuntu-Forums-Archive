---
title: "XMMS soundcard problem"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by Frank Golden on 2006-05-29
Hi All Again,
     I am using XMMS in Dapper to play my MP3's and it works fine. I am using an Audigy 2 USB external sound card but I also have a USB headset with mic attached for use when I'm booted into XP. This is on a laptop with an internal sound card. My Audigy 2 external card is set as default on system and in XMMS. Often upon reboot XMMS insists on configuring itself to use my USB phones instead of the default Audigy 2 forcing me to manually reconfigure. My question is there a way (command or config file I could edit to force Dapper to ignore or not see my headset and internal sound card?  BIOS is no help.
Any help would be appreciated.
Thanks

---

### Post by christhemonkey on 2006-05-29
What sort of internal sound card do you have?
To stop it from working (thats sounds wrong somehow) you just have to blacklist the modules so they dont load on boot.

To do this you need the name of your onboard soundcards driver (we can help with that) and then you need to add it to the end of a file in /etc/ somewhere.

---

### Post by Frank Golden on 2006-05-29
[QUOTE=christhemonkey]What sort of internal sound card do you have?
To stop it from working (thats sounds wrong somehow) you just have to blacklist the modules so they dont load on boot.

To do this you need the name of your onboard soundcards driver (we can help with that) and then you need to add it to the end of a file in /etc/ somewhere.[/QUOTE]

Hi Chris,
    Yeah that does sound wrong what with problems people seem to have with detecting sound etc. LOL. But to answer your questions my internal sound is listed in XMMS's Alsa configuration utility as HDA Intel: ALC 882 Analog (HW:0,0) and
HDA Intel ALC 822 Digital (HW:0,2) there are actually 2 listings as above. My USB headset is listed as Logitech USB Headset:USB Audio (HW:2,0) and lastly my preffered (read default) sound card is listed as Audigy 2 NX:USB audio (HW:1.0)
I could just leave the headset unplugged while booting to Dapper. But would like to leave it plugged in to use in Windows XP.  I only use it for voice messaging in Google Talk while in Windows XP. If you haven't figgured out yet this is a dual boot setup. LOL
    What I would like to do is at least "blacklist" my headset device and maybe my internal sound.
    As a sidenote an annoyance I have been struggling with for months on two separate machines (laptops) is the fact that Flash content in Firefox ( I use Pandora, a streaming audio service that uses Flash) will only play through the laptops internal sound.
    This in Breezy all versions and now Dapper. If I could disable my internal Sound Card maybe it would force the Flash web content to play through my USB sound card?? Dunno
Hope you guys can help.
Thanks

---

### Post by Frank Golden on 2006-05-30
Hi Chris,
    Any Ideas?

---

### Post by christhemonkey on 2006-05-30
Sorry, was out.

You need to add to the end of /etc/hotplug/blacklist.d/blacklist (or it might be /etc/modprobe.d/blacklist) the line
```
blacklist             snd-hda-intel
```

I may have it wrong though, it might be snd-intel8x0, but i do believe it is snd-hda-intel.

Not sure what to do about the usb-headset, as it uses snd-usb-audio module, which is also used for your other one.

---

### Post by Frank Golden on 2006-05-30
Hi Chris,
    That did the trick for the onboard sound. It is no longer available as an option in >preferences>sounds. And as a huge bonus my web based sounds (like Pandora)
now play through my external sound card and 5.1 speakers. If I ever need my internal sound card all I have to do is remove from blacklist. HAH. Will try adding Logitech headset to list.
[update]
added snd-hda-logitech usb headset no dice. think you are right both (USB devices) seem to share snd-usb-audio module. No big deal to unplug before bootup. BTW the blacklist file is at /etc/modprobe.d/blacklist.

This to me is a big breakthrough to be able to play my web (Flash)
sounds through my Audigy 2 NX external card. Been struggling with this issue for 5-6 months, spanning 2 laptops (an HP pavillion and this one
an Acer Aspire 5672WLMi) and both Breezy and Dapper.
The Acer is/was supposed to be a problem child according to early reports with Dapper but the latest beta installed well and responded well to ATi driver updates. Except for the sound issues I outlined earlier sound just worked out of the box. Kudos to the developement team.

---

