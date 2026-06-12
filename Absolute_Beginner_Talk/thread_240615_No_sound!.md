---
title: "No sound!"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by kedarm on 2006-08-21
Hi!

After a couple of attempts, I finally managed to upgrade to DAPPER. But, when I restarted my computer, there is no sound! When I click on the volume icon (that now sits on the top corner of my screen), it gives me an ERROR message saying :
"No volume control GStreamer plugins and/or devices found."

I am using a "DELL INSPIRON 600m", and the sound card is an "Integrated AC'97 Audio Controller"

Please help! Thanks!

Zzypty Zzyp

---

### Post by xpod on 2006-08-21
I cant help much but i can tell you i got ac97 integrated sound and ive had a couple of probs with it.
Theres a multmedia selector under SYS-PREFS-MULTIMEDIA SYSTEM SELECTOR..
Have a look in there......thats where i started.Things can get messed up.
I suppose you probably know this but just a thought.

EDIT:Theres also apparently some sound check that you need to look in your "user and groups" to check where you click the "groups" tab and scroll down to "sound" and make sure your user name is there on the right hand pane

EDIT":...sorry,what about typing "alsamixer" in to terminal...i suppose that produces the same result as volume icon.just another thought

---

### Post by kedarm on 2006-08-21
Every time I start the computer, the following error message is displayed :

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured."

Also, I can't find the "Multimedia System Selector". And when I type 'alsamixer' in console, I get the following error message:
"alsamixer: function snd_ctl_open failed for default: No such device"

---

### Post by xpod on 2006-08-21
You might need to activate the "multimedia system selector" in the alcarte memenu editor.
You might just need to get the alsa or alsa-oss sound packages or something like that if they did`nt come with any upgrade.

I cant really help too much as im new to this game too but ive had a couple of sound probs along the way.

Also is your onboard sound still enabled in your bios.just another thought?
I just sort of stumble along mate but i usually get there in the end.

---

