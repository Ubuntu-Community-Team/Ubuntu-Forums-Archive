---
title: "help get mic to work..."
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2006-09-13
I can not seem to configure my microphone to record.



Ive posted an image of all my sound options. 
When I got to multimedia systems selector and choose OSS- Open Sound System for my default input plugin it seems to test ok when i click "test" but when i try to record using "record from input: microphone" i get nothing. 

when i try to select ALSA I get: ALSA - Advanced Linux Sound Architecture: Could not open resource for reading.

please help!

---

### Post by bodhi.zazen on 2006-09-13
On the "Options tab" select a different microphone (ie Mic or Mic1)?

---

### Post by jinxjinx on 2006-09-13
no luck. it records but i hear no playback.


for some reason it will only let me record input from Line-1.

where can i read about what all these different names mean?

thanks!

---

### Post by xyz on 2006-09-13
Did you go Application > Sound & Video > Volume Control?
Click the "Capture" tab - is volume up? is there a red x under Microphone?

---

### Post by xyz on 2006-09-13
Also in a console, type:
```
alsamixer
```
in a terminal to see if everything's on and set at appropriate levels.
Use left/right-up/down arrows to modify.
Hope it works. Let us know...

---

### Post by jinxjinx on 2006-09-13
alsamixer wont work...

k$ alsamixer
alsamixer: function snd_ctl_open failed for default: No such device

for some reason there is a red x. i can remove it temporarily but when i close and open the volume control the red x comes back.

---

### Post by bodhi.zazen on 2006-09-13
> **jinxjinx said:**
> no luck. it records but i hear no playback.


for some reason it will only let me record input from Line-1.

where can i read about what all these different names mean?

thanks!

So it is not a hardware problem then...

May I ask what program or task you are attempting.

alsamixer is a good suggestion, although if the mic is recording then the problem would seem to be in playback. So what is the task exactly?

Also, I found (when I was configuring my mic) kmixer has more options then most mixers. You could try that.

---

### Post by jinxjinx on 2006-09-13
well using kmixer i can set the rec button to volume and record stuff coming out of my speaker but no matter how i play with the other options i can not record from the mic. 
i tested the mic on a windows pc and its fine.

---

### Post by bodhi.zazen on 2006-09-13
I am confused. You state both you can and cannot record, I'm not following. Restate your question and I'll try my best.

---

### Post by xyz on 2006-09-13
> **xyz said:**
> Did you go Application > Sound & Video > Volume Control?
Click the "Capture" tab - is volume up? is there a red x under Microphone?
o
One more try! It works for me:
Again Volume Control > Edit > Preferences
Little window comes up, check them all. OK. Try enabling mic again.

---

### Post by jinxjinx on 2006-09-13
ok i did that. checked all boxes and took a screen shot. 

to put it simply i just cant record from the microphone. 

for some reason i have two sound devices as you can see in the pic. neither of them seem to help the mic.

---

### Post by xyz on 2006-09-13
I found a very nice, clear, all-in-one-page HowTo here:
[http://ubuntufs.wordpress.com/2006/06/08/trouble-with-your-microphone/](http://ubuntufs.wordpress.com/2006/06/08/trouble-with-your-microphone/)

There's also been a bug reported which should be fixed iif you have gnome-media 2.14.2-0ubuntu1:
[https://launchpad.net/distros/ubuntu/+source/gnome-media/+bug/39119](https://launchpad.net/distros/ubuntu/+source/gnome-media/+bug/39119)

---

### Post by jinxjinx on 2006-09-13
ok. when i try to run "recording level monitor" it wont open and says "cannot connect to sound daemon. Please run 'esd' at a command prompt.

when i run esd i get this:
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card 'CS46xx'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default


when i try to enable ALSA from "multimedia systems selector" i get this: 
ALSA - Advanced Linux Sound Architecture: Could not open resource for reading.


when i try to run alsamixer i get this: alsamixer: function snd_ctl_open failed for default: No such devic

= (

thanks for all the help guys. i really appreciate it.

---

### Post by bodhi.zazen on 2006-09-13
This was one of th emost useful sites I found:

[Skype How to Microphone](http://www.skype.com/help/guides/soundsetup_linux.html)

Includes a skype forum for help with microphones.

You could also try:

sudo alsaconf

sudo modprobe snd-cs4236

---

### Post by jinxjinx on 2006-09-14
thanks for the continuing help. the problem seems to be with the gnome sound daemon or this alsa thing.

when i run: sudo modprobe snd-cs4236
FATAL: Error inserting snd_cs4236 (/lib/modules/2.6.15-26-386/kernel/sound/isa/cs423x/snd-cs4236.ko): No such device


this is really frustrating...

---

### Post by bodhi.zazen on 2006-09-14
This is a known bug. Here is a potential work-arround:

[Bug 40116](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg42117.html)

---

### Post by jinxjinx on 2006-09-14
same result: 
sudo modprobe snd-cs4236
FATAL: Error inserting snd_cs4236 (/lib/modules/2.6.15-26-386/kernel/sound/isa/cs423x/snd-cs4236.ko): No such device

and i followed those instructions to the T. even edited my boot params...
this is a sad day...

---

