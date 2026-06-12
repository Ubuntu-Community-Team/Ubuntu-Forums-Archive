---
title: "Unifying Sound Volume"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by Jussi01 on 2006-12-06
So Everything seems to be running fine, but it seems like not all of the applications have the same sound settings. like if I exit sopcast with the volume low it affects other applications and i have to go back, turn it up and exit again. is there a way to have a master volume? I would have thought the one in the tray would do that...

---

### Post by Jussi01 on 2006-12-07
Bump - is thee no one who has had this problem? or am I not clear enough?

---

### Post by robinl on 2006-12-07
Uhhh isn't that what you want? You lower the volumn in one programme and all other programme's volumn are lowered is well. Isn't that the meaning of a unified volumn control or master volumn?

---

### Post by aliyanage on 2006-12-07
Hi all,

I have the same issue, I would prefer having just one controler to adjust the sounds of all running applications, is there someone having a solution to this?

aliyanage

---

### Post by Jussi01 on 2006-12-07
> **robinl said:**
> Uhhh isn't that what you want? You lower the volumn in one programme and all other programme's volumn are lowered is well. Isn't that the meaning of a unified volumn control or master volumn?

I think maybe you missed what I meant. What I would like is that the systray volume will control the whole system volume and the other apps volumes would be independent of each other - so sopcasts volume should not affect mplayer volume and totems volume should not affect vlc etc - but the systray volume should affect all volumes - which it currently doesnt.

---

### Post by Delkster on 2006-12-07
> **Jussi01 said:**
> I think maybe you missed what I meant. What I would like is that the systray volume will control the whole system volume and the other apps volumes would be independent of each other - so sopcasts volume should not affect mplayer volume and totems volume should not affect vlc etc - but the systray volume should affect all volumes - which it currently doesnt.

To achieve that the applications would need to perform their own volume adjustment in software. If the applications don't do that and instead rely on the system-wide volume settings in the sound driver, there's little the sound system can do for that. There aren't separate volume channels for every applications in the hardware (or wherever the actual adjustment is done on the driver level).

I believe it would be up for the applications to do that.

---

### Post by Delkster on 2006-12-07
> **Jussi01 said:**
> but the systray volume should affect all volumes - which it currently doesnt.

Sorry, I missed this part.

The notification area icon can adjust any of the available volume channels. You can select which one it affects by right-clicking on the icon and opening Settings from the menu. Select "Master" as the volume channel to adjust -- that should affect all sound.

(The English names of the menu items may not be exactly correct since I currently have my desktop set to a non-English language and can't check the correct English names right now.)

---

### Post by Jussi01 on 2006-12-07
Thanks a lot for your help so far. Unfortunately I have set it to master but it still doesn't help - To give a scenario, If I have amorak playing and suddenly I need to mute it, I need to be able to hit the button on the front of the computer which controls the tray volume and and mute it. right now it doesn't do this. 

Could this be a driver issue?

My sound hardware is the Sigmatel ST-AC 97. (dell inspiron 6000 laptop)

---

### Post by Delkster on 2006-12-07
Doesn't adjusting the master volume affect the volume of the music from Amarok *at all*?

---

### Post by Jussi01 on 2006-12-07
> **Delkster said:**
> Doesn't adjusting the master volume affect the volume of the music from Amarok *at all*?

No, absolutely not at all. It is a little confusing...

---

### Post by Jussi01 on 2006-12-07
I have also tried setting the volume to headphone, speakers and a variety of others, but no joy.

---

### Post by Delkster on 2006-12-07
> **Jussi01 said:**
> No, absolutely not at all. It is a little confusing...

To be frank, that confuses me, too.

How do you have things set up in System > Preferences > Sound (assuming that you're using Ubuntu/Gnome)? What sound output systems do you have in use for sounds and music/videos?

---

### Post by Jussi01 on 2006-12-13
ok, I have figured out that the volume control needs to be set to PCM. that works well, but now could someone help me with binding the control keys on the front of the machine to the PCM volume?

Thanks a lot!!

EDIT - PS. I already tried system -> preferences -> keyboard shortcuts

---

### Post by Jussi01 on 2006-12-13
Bump - anyone?

---

### Post by DrMilo on 2006-12-13
It's far from a perfect solution but the ALSA mixer gui, which on mine is located under applications> sound and video, can be dragged and dropped on to the taskbar. This makes access to its controls more convenient. Nobody seems to have ever addressed this problem properly though. As far as I know there has never been a universal volume control, for Linux or Windows. Everything has its own, nothing is in charge.

---

### Post by Jussi01 on 2006-12-18
SOlved it for all those who were wondering - I bound the front keys on my laptop to the PCM volume instead of the normal volume.  - thanks to the guys on Irc for helping!!

---

