---
title: "[SOLVED] No sound  . . . well maybe a little . . . well no"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by Phurious on 2007-08-04
I seen MANY posts on sound issues, but not one that seems to address my problem.  I am new to this, so please forgive my ignorance.  I have tried Linux, gotten so frustrated I walked away back to Windows, and then come back again - and the cycle continues.

I have Ubuntu 7.04 successfully(?) installed on a Dell GX620 for learning purposes.  Everything seemed to go fine during the install, and here I am posting online, so I know my network drivers were installed fine.  My issue is sound, and I have to say I am really confused.  I disabled the onboard sound on my PC because I thought it might make it easier for Ubuntu to recognize and configure my Plantronics USB headset.  I assume the headset was discovered and installed during install, but I can get NO system sounds through them.  If I start System > Preferences > Sound, and MANUALLY select "USB Audio" on the "Devices" tab and press the "Test" button, I can hear a solid tone.  If I immediately switch to the "Sounds" tab, and try playing . . . anything, I hear nothing.  To further confuse me, I can launch Rythmbox and listen to Internet Radio through the headset fine.  Can anyone tell me what I am doing wrong?

If I execute the command 'aplay -l" in the terminal I get:
```
**** List of PLAYBACK Hardware Devices ****
card 1: Headset [Plantronics Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Is this not a good sign?

---

### Post by apswartz on 2007-08-04
Okay, I'm confused. You can hear when playing Rhythmbox, right? What apps fail for you? Maybe I'm misunderstanding something.

---

### Post by Aurdal on 2007-08-04
Have you tried chaning the audio output modules for the applications in which sound don't work?

---

### Post by Phurious on 2007-08-05
apswartz:  Yes, I can hear sound while in Rythmbox, but no system sounds.

Aurdal:  What are "audio output modules"?

---

### Post by Dr Small on 2007-08-05
Check the permissions on your account. I messed them up once, and couldn't access any system sounds.

---

### Post by carloslosgrande on 2007-08-05
[FONT="Comic Sans MS"]Audio output modules like OSS or ALSA. When I double click on the sound icon in my top panel a gui pops up for my alsa mixer. Different apps sometimes use different modules and you may have to change the settings for whichever app you choose.
I use AmaroK and it sets itself up.[/FONT]

---

### Post by sailor2001 on 2007-08-05
right click your sound icon on the taskbar to open volume control. click 'edit' 'references'and tic the idems you need. (pc speaker for one) Also if you are using a head set, is your mic plugged into the front of your pc? That would be 'mic2' (mic select)

---

### Post by Phurious on 2007-08-14
Thanks for the replies, but the problem continues.  Not sure where to go next.  I changed my audio device, and STILL have no system sounds (log in/log out).  I am able to play MP3 and hear them in Rythmbox, and I can play DIVX movies in Movie Player and hear the audio fine.  

What I can't hear (That I know of)
Video in Firefox (YouTube, CNN, etc)
System Sounds
Sound in VLC (This is supposed to be a bug from what I have read)
Skype is dodgy

The new hardware is a Bose Companion 5 system, and it appears the system sees it fine.  aplay -l yields

```
**** List of PLAYBACK Hardware Devices ****
card 1: Audio [Bose USB Audio], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by Phurious on 2007-08-24
In order to troubleshoot my problem further, I installed a SB Audigy 2 I had laying around.  Using this as my primary sound device everything worked - movies, MP3, system sound, even sound in videos from CNN or YouTube.  I then plugged in a Plantronics USB headset and under the sound control panel switched everything to USB - Did I mention I switched everything to USB?  Now, through the headset I can hear the audio on movies and MP3's, but system sounds and audio from Flash video still comes through my Audigy and speakers.  Can anyone tell me why and hope to fix this issue?

---

### Post by kvonb on 2007-08-24
> **Phurious said:**
> In order to troubleshoot my problem further, I installed a SB Audigy 2 I had laying around.  Using this as my primary sound device everything worked - movies, MP3, system sound, even sound in videos from CNN or YouTube.  I then plugged in a Plantronics USB headset and under the sound control panel switched everything to USB - Did I mention I switched everything to USB?  Now, through the headset I can hear the audio on movies and MP3's, but system sounds and audio from Flash video still comes through my Audigy and speakers.  Can anyone tell me why and hope to fix this issue?

Yes, have a look through this thread, it will answer all your questions:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

As for the sound coming out of different sources, see the section:
 _**[SIZE=3]Configuring default soundcards / stopping multiple soundcards from switching[/SIZE]**_

---

### Post by Phurious on 2007-08-24
Thanks kvonb - that was exactly what I needed.  Ironically, I had read through that post before, but I am sure by the point in time I got to the section you referenced my sound was so hosed nothing worked.  Working on a fresh install, and seeing I already had sound working, I skipped to the "Configuring default soundcards" section.

Thanks again!

---

