---
title: "realtek ac97 - audio not syncing with video"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-08-10
while playing videos, the sound will not match the video. some videos are better than others, but rarely do they sync.

i've tried using alsa-oss for playback and it's no better. every drivers i've seen for this soundcard has caused me to lose sound completely and beyond repair (followed comprehensive sound guide)

it may be a driver/codec issue, if it is..how do i fix it?
if it's not a driver issue, what can be done?

thanks

---

### Post by hatman on 2006-08-10
I've noticed this also, mailnly when using both totem and mplayer, but everything appears to be syncing when I use VLC... dunno if that helps...

---

### Post by xpod on 2006-08-10
I have onboard realtek ac97 and have nothing but problems with it when im in xp...im always having to rollback the driver or uninstall and reinstall for some reason.It initially had all the wrong drivers and was a right mess when i got and it still does it to this day but rarely.

And when i installed ubunto and eventually got automatix to install all the usual java,flash etc i still did`nt have sound but somebody told me a couple of lines of code to try and its worked ever since

I`ll try and find them and see what they were for again.somebody else will need to tell you if they would help you though.

edit:I really doubt these are relevant to your specific problem and were given to me when my sound still would`nt work AFTER using "automatix2 to install flash and java.I was`nt getting proper sound on places like you tube and google video etc

I dont even know what they mean so dont go trying them till somebody else tells you what they will do......I just know they got my realtek ac 97 sound working properly


OOP```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
ln -s /tmp/.esd-1000 /tmp/.esd 
```

---

### Post by shanepardue on 2006-08-10
so was your sound working at all before those lines or was it not syncing like mine?

---

### Post by xpod on 2006-08-10
Basically it was`nt working at all but you could tell it was there and trying to work . i could hear bits coming through but they were`nt anything i could hear properly

Im quite sure the rhythimbox worked okay even though videos would`nt play properly.Ive forgotten the exact sequence of events but those lines were something i was given after being told to get automatix for the flash and java etc and still not hearing real sound watching video`s.

I dont know if they sorted the sound or if they sorted something else that the sound relyed on???Sorry if IVE confused you even more

---

### Post by shanepardue on 2006-08-10
mine stopped working after i tried to update the driver, but i since restored a partition image and i have my sound back, but still no sync.

---

### Post by xpod on 2006-08-10
Do you mean you had sound previously in ubunto and you updated the driver on here before it stopped working.

Ive not got round to copying partition images yet so is`nt something i can comment on(neither is much else mind you..lol)

Mabey that is muddled up with whatever was there before you put the image on??

---

### Post by shanepardue on 2006-08-10
the audio worked but was lagging...i tried to update the driver and i loss my sound completely. i restored my partition image and it's back to where it's lagging again.

---

### Post by xpod on 2006-08-10
I get you now......you obviously just need to find the right driver but it`s usually different ones you need here on ubunto i believe  to those your used of using.....Somebody will know for sure

---

### Post by shanepardue on 2006-08-10
yeah for some reason every driver i use kills the sound. i used the old one from asus and a much more recent one from realtek. the one from realtek is only source as they don't have an ubuntu/debian package.

i installed the source and it seemed to work great, but no sound at all at that point.

---

### Post by xpod on 2006-08-10
You sound like your having the same troubles here on ubunto with realtek as what i did in xp

Is it the onboard sound you have ?

---

### Post by shanepardue on 2006-08-10
> **xpod said:**
> You sound like your having the same troubles here on ubunto with realtek as what i did in xp

Is it the onboard sound you have ?

yep..onboard and out of sync. ha

---

### Post by xpod on 2006-08-10
i mean like some people have soundcards and some have those little onboard chips...that was where i was breaking down.

I had been trying allsorts of drivers and even the one from my motherboards site(when i finally figured it out) was`nt working as it should.

I probably made more mess than i started with but i ended up getting a realtek package from driverguide that somehow just worked even though it was`nt what i should have been using.

I still have the proper realtek ac97 driver for my motherboard but it does not work in xp.

So i could`nt be exactly sure just WHAT ubunto is even using.it must have its own drivers that run my sound as it all works fine.

Im still trying to learn what everything is and what it does and what the differences are with various things......Im not just new to linux as i had only been on a pc for a few months prior to this

Thought i`d better get ahead of my kids in the computer education so i knew they were ok(safe)and so i could help them instead of them helping me.

---

### Post by shanepardue on 2006-08-10
so are you using a driver from realtek's website (the linux source)? or are you just using ubuntu's default?

---

### Post by xpod on 2006-08-10
Sorry....im not sure what its using..

If i look in the device manager it lists this lot
VT8233/A/8235/8237 AC97 Audio Controller

And it`s driver is listed as..
   KEY                     TYPE           VALUE
info.linux.driver         strlist        VIA 82xx Audio

info.parent     /org/freedesktop/hal/devices/computer


theres a lot more sub menus under the main audio tab with all the specific devices but thats my main tab and its driver

Ps....i aint installed anything other than those lines i got

---

### Post by shanepardue on 2006-08-10
i've been told that it's probably a software settings issue.

dvd's work fine in totem, but compressed video and streaming internet video is still experiencing many problems.

---

