---
title: "configure my mic"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Atmuh on 2007-05-06
I need to configure my mic but I'm not sure how.
can someone point me in the right direction?

---

### Post by Tundro Walker on 2007-05-06
If your sound card was detected successfully, then you shouldn't have problems with your mic.  Easiest way would probably be to use the sound control applet that you usually have on one of the panels (EG: like the sound "speaker" icon you usually see in the MS Windows task bar).

If you don't have it, then right click on a panel somewhere.   Select "**Add to Panel**" and drag-drop the sound / speaker applet icon onto your panel (or just double-click the speaker icon...it'll dump it somewhere on your panel).

Right-clicking on the speaker icon should give you something like 

> Mute
Open Volume Control...
------------------
Preferences
Help
About
(etc)

Click on the "**Open Volume Control**" option.  In that screen, you can select the sound card to use, and "Edit > Preferences" to select the sound (controls?) to enable/disable on your sound control panel.  From there, you should be able to checkmark your Mic control to get it onto the sound panel.  Then, switch on your mic (or plug it in...whatever), and adjust the volume level of the Mic control.

Also, in the Sound Control Panel GUI, look for the "Mic Boost" and "Mic Select" check boxes.  You may or may not have these, depending on your sound card.   Toggling these should add some tabs to the left of the "Playback" tab, called "Switches" where you can boost the mic gain, and "Options" where you can select your mic.

Ok, leave that Sound Control GUI / Screen open, and flip on over to "**(Start) > Sound & Video > Sound Recorder**".  Fiddle with that a bit, and record some mic tests (check one, check one...yo Brooklyn, WASSUP!?)  I personally don't like mic boost, since it tends to pick up the slightest sound, like breathing into the mic.  So, if I record, I usually turn off mic gain/boost, and simply increase the mic / recording volume.  This is especially true if I'm speaking to others over the mic, because they don't want to hear somebody breathing into the mic like some kind of psycho phone call.

Hope this helps.

---

### Post by rfs1970 on 2007-05-06
If you don't have the "Mic Boost" option available,
(well... I dont)... you can create a file into your home folder
called micboost.sh. Then add the follow lines into it:
> 
#!/bin/sh
if amixer cget numid=17 | grep on; then
amixer cset numid=17 off
else
amixer cset numid=17 on
fi


Save the file and then, via terminal give this file 
the permission to be executed :

> 
chmod +x micboost.sh


So... from now on, everytime that you execute this file,
it will turn on/off the extra "sensitivity" of your microphone.

to execute the file, just type in your terminal:
> 
./micboost.sh


r.

---

### Post by Atmuh on 2007-05-07
My problem is a tad strange.
I can hear whatever I say come out of my speakers but I won't record/capture anything.
The option that I can hear with it is the "front mic" option.
Any ideas to what I should do?

---

### Post by rfs1970 on 2007-05-07
Hi There,

Probably its happen because in your volume control windows,
the microphone is set in the speaker bar...
You have to unable microphone there...

Take a look at the picture that I have attached here.

r.

---

### Post by nobodie on 2007-05-14
rfs1970: 
I have a similar but different problem, something I have seen mentioned but not solved and perhaps you have addressed it somewhere else. It looks like it will need some CLI interference to solve anyway:

Skype, microphone setup: I got it working no problem on my Fedora machine (P4 VIA soundcard) but now this new machine I have set up inn FF and it is not working.

The Fedora setup required that after reboot I go back to the Volume control and turn the mike back on (unmute) in OSS/capture while increasing the PCM volume in ALSA/playback. while this is clumsy it kept my skype up and running and i don't reboot that often. 

In FF however I don't have an OSS/capture option, only playback for OSS. Adjusting ALSA produces no results with the exception of unmuting an "analog" slider (what is that all about, OSS is the analog sound program and ALSA the digital, I thought anyway) which gives some nasty, scratchy, staticy sound through the headphones which can be shut off but turning off the mike boost or some of the mike controls.

So, how do I get the microphone working in Skype. It seems to clearly want an analog capture procedure through OSS. So is there a simple CLI way to turn on the OSS capture functions (and leave them on perhaps, why go for just good enough whenwe could actually have it fixed?) 

If you have a solution for this then we could have a major improvement in the Skype situation.

love and peace up

---

### Post by rfs1970 on 2007-05-14
Hi Nobodie,

Can you describe your computer and what skype version you have installed ?
(I pressume that you are using feisty faw, right?)

r.

---

### Post by brittney on 2007-05-14
> **nobodie said:**
> rfs1970: 
I have a similar but different problem, something I have seen mentioned but not solved and perhaps you have addressed it somewhere else. It looks like it will need some CLI interference to solve anyway:

Skype, microphone setup: I got it working no problem on my Fedora machine (P4 VIA soundcard) but now this new machine I have set up inn FF and it is not working.

The Fedora setup required that after reboot I go back to the Volume control and turn the mike back on (unmute) in OSS/capture while increasing the PCM volume in ALSA/playback. while this is clumsy it kept my skype up and running and i don't reboot that often. 

In FF however I don't have an OSS/capture option, only playback for OSS. Adjusting ALSA produces no results with the exception of unmuting an "analog" slider (what is that all about, OSS is the analog sound program and ALSA the digital, I thought anyway) which gives some nasty, scratchy, staticy sound through the headphones which can be shut off but turning off the mike boost or some of the mike controls.

So, how do I get the microphone working in Skype. It seems to clearly want an analog capture procedure through OSS. So is there a simple CLI way to turn on the OSS capture functions (and leave them on perhaps, why go for just good enough whenwe could actually have it fixed?) 

If you have a solution for this then we could have a major improvement in the Skype situation.

love and peace up


I have the same problem i think. I just reinstalled ubuntu (feisty) and installed skype through the custom repository. My mic works for recording stuff and i can hear my voice through the speakers. But in skype the mic wont work. I hear perfectly but cant talk.

Ive found something about this when I googled about emul-linux-x86-soundlibs that was to low version but i cant find them in Ubuntu, im not that advanced maybe. 

Cheers
-bri

---

### Post by Jawsman on 2007-09-09
Hey, I have a similar problem:

I can get to hear my voice through the speaker but I get no sound when recording!!

When opening the 'recording level monitor' I can't make the volume bar move...
anyone can help?

---

