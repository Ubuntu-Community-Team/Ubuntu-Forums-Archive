---
title: "Ventrilo Problems...Again"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by diggydong on 2008-02-28
I have read through pretty much every post I have come across with similar problems and nothing seems to match what I have.  I am running the latest version of wine to date (0.9.55) and the all the updates I can get for gutsy (7.10).

My problem is that I can't get my usb headset to get the mic working correctly, I can use it in any other portion of gutsy just fine but when I try to run ventrilo through wine it sees my headset but all I get is static through it (using ALSA drivers and worse through OSS), can't even hear my voice.  I can hear everyone but can't return the favor.  I have tried all the configuration combinations I can see.  I'm a complete beginner to this so if I need to post any information for help please let me know what it is and how to get there.  Changing voip is not really an option since I play WoW and no one else uses mumble or teamspeak.  Any help would be greatly appreciated

---

### Post by northern lights on 2008-02-28
Can you please post the output of ```
cat/proc/asound/cards
```

Thanks.

---

### Post by diggydong on 2008-02-29
Apologies again, I am trying to learn but "cat/proc/asound/cards: No such file or directory" comes up when I type that

---

### Post by northern lights on 2008-02-29
My bad, typo.

Please try

```
cat /proc/asound/cards
```
(note the space)

Sorry.

---

### Post by diggydong on 2008-02-29
0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xde300000 irq 22
 1 [Headset        ]: USB-Audio - Logitech USB Headset
                      Logitech Logitech USB Headset at usb-0000:00:1d.0-1, full speed

thank you very much for the quick response

---

### Post by northern lights on 2008-02-29
Is there an option, where you can manually select the sound device in ventrilo?

If so, try with alsa as your output plugin and as device set "plughw:1,0"...

---

### Post by Oldsoldier2003 on 2008-02-29
> **diggydong said:**
> I have read through pretty much every post I have come across with similar problems and nothing seems to match what I have.  I am running the latest version of wine to date (0.9.55) and the all the updates I can get for gutsy (7.10).

My problem is that I can't get my usb headset to get the mic working correctly, I can use it in any other portion of gutsy just fine but when I try to run ventrilo through wine it sees my headset but all I get is static through it (using ALSA drivers and worse through OSS), can't even hear my voice.  I can hear everyone but can't return the favor.  I have tried all the configuration combinations I can see.  I'm a complete beginner to this so if I need to post any information for help please let me know what it is and how to get there.  Changing voip is not really an option since I play WoW and no one else uses mumble or teamspeak.  Any help would be greatly appreciated
If your apps worked fine before i'd downgrade to 0.9.46 since its the release supported by the Ubuntu repos. I've found that upgrading Wine often breaks my stable apps,

---

### Post by diggydong on 2008-03-01
Yes there is a place where I can select the sound output for ventrilo in wine.  I have tried every combination that is currently available to me.  As for the other response, I didn't think of downgrading, so I uninstalled wine and installed the suggested version of wine along with a fresh copy of ventrilo with same results of sound input working perfectly, can hear everything through the headset just no sound output from the mic, same static as before.  I can switch from internal speakers to headset, so its recognizing both perfectly on that side of it.  If anyone else has any suggestions I'd love to try them, even though its a problem I'm having fun troubleshooting, I'm just out of ideas on where I can look.

---

