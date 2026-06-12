---
title: "Microphone not working - please help a new girl"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by duckgoesoink on 2008-02-17
Hi everyone,

I am a new Ubuntu user (installed Feisty three days ago), and everything is working perfectly on my Asus Z53Jc, except for the integrated webcam and microphone. I do have another USB webcam with integrated microphone, but on this the microphone doesn't work (the video does though).

I have searched through the documentation and forums for solutions over the last three days, and ended up more than confused (I'm also an ex Mac and Windows user, so command lines are unfamiliar, although I'm willing to learn). I realise that many people have similar problems, but there is so much conflicting advice and I'm hesitant to use terminal commands unless they are recommended for my situation - it looks like some people have had terrrible experiences running commands not suitable for their setup.

I tried playing with the Volume Control, and checking all boxes, raising levels, etc. I also tried adjusting Sound Preferences, but when I try to test sound capture, everything freezes up and I get error messages. Below is the message I get when doing this with the capture option set to USB Audio or ALSA:

> Sound capture: Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'

Skype recognises the USB webcam video but not it's microphone - test calls send back no recorded sound. Sound Recorder doesn't record either, and the window freezes.

If anyone could help me figure this out (either through my integrated webcam/microphone or the USB one) I would be very grateful.

Cheers,
Hin :-)

P.S. If I can get a microphone working, it will save having to boot into Vista just to make a Skype call (I hate Vista, it's heavy and sluggish). And I do have all normal sound coming from speakers and such. It's just the microphone not recording.

P.P.S. Both devices work on Vista.

---

### Post by olejorgen on 2008-02-17
I'm by no means a expert, but I'll think it would be useful if you posted the result of:
```

arecord -l

```
This will simply list all (alsa) recoding devices the system finds.

---

### Post by duckgoesoink on 2008-02-17
Results of arecord -l

> **** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: Camera [USB Video Camera], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---

### Post by jan quark on 2008-02-17
hi and welcome 
good choice :)

try the following

1.run in terminal 

```
alsamixer
```

and see if you get some more options to change

2 Check "Microphone Capture" option on the "Switches" tab within the volume control. wild guess

3 also try to set in system > preferences <sound the sound capture driver from alsa to oss

PS : I liked the first avatar pic more ;)

---

### Post by duckgoesoink on 2008-02-17
After running alsamixer in the terminal it just says: 
> 
Card: USB Video Camera
Chip: USB Mixer
View: [playback] Capture All
Item: Auto Gain Control

I don't know what I can do with that (it's all text based).

I tried enabling all the microphone capture options in the volume control, no change.

> **jan quark said:**
> 3 also try to set in system > preferences <sound the sound capture driver from alsa to oss
Tried this, then went to sound recorder - now it pretends it's recording, but it actually isn't.


P.S. Yeah both avatars are kinda old now though. :-)

---

### Post by duckgoesoink on 2008-02-17
Does anyone have any ideas I could try? I really don't want to be booting into sucky Vista just to use Skype...

Please?

Or perhaps I should post in another section?

---

### Post by jan quark on 2008-02-18
try to post in the multimedia and video section 
but perhaps someone will have a sudden inspiration :)

here some solutions to try out

[http://grega.wordpress.com/2008/02/04/ubuntu-skype-microphone-problems/](http://grega.wordpress.com/2008/02/04/ubuntu-skype-microphone-problems/)

[http://jadmadi.net/blog/2007/12/27/ubuntu-gutsy-skype-microphone/](http://jadmadi.net/blog/2007/12/27/ubuntu-gutsy-skype-microphone/)

---

### Post by Fot! on 2008-02-18
Hello Im in Ubuntu Gutsy 7.10 - 64 bit and
I have the same problem with my mic not working..
The output of the arecord -l command (if that is any helpful) is:

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 2: ALC883 Analog [ALC883 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: default [Camera         ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and I've tried almost everything in my sound preferences.
My sound recorder doesnt seem to record any sound.
However, when i test my aMSN audio settings in configuring mic
I have three choices for input device: 1)default, 2)plughw1 and 3)plughw2.
So, when I choose plughw1 I can hear my voice in the test!!!
Please, any ideas for fixing it? 
I need to get my mic working for skype!

---

### Post by sglow on 2008-02-18
I've been using Skype without problems, but just found that my mic didn't work this morning for some reason.

Here's how I fixed it:

Started alsamixer, this only showed the playback settings by default, I want to look at capture settings.

Pressed 'h' for a help screen so I could figure out how to get to the capture display.  It's the F4 button.

Press F4 to show my capture settings.

Noticed that the channel being captured was CD for some reason.  I wanted to capture the microphone, so I used the left/right arrow keys to highlight that, and pressed the space bar to select it.

Hit escape to quit alsamixer

Tried Skype again.  It's working now.

Perhaps there's a better GUI program around to do this, but alsamixer is the one that I've used in the past.  Hope it helps you.

Good luck,
Steve

---

### Post by Fot! on 2008-02-18
Steve thanx for the quick reply..
Unfortunately I didnt see anything wrong in alsamixer.
I attached a screenshot of my settings there.
Any other ideas? 
Thank you

---

### Post by sryth on 2008-02-18
I had this problem the other day, maybe yours is the same.  If you have your mic plugged into a mic jack on the front of your computer rather than the back, check volume control and see if your preferences menu will let you control a setting called "Front"  If so, it'll give you a new slider that is all the way down, slide it up and you're good to go.

---

### Post by Fot! on 2008-02-18
> **sryth said:**
> I had this problem the other day, maybe yours is the same.  If you have your mic plugged into a mic jack on the front of your computer rather than the back, check volume control and see if your preferences menu will let you control a setting called "Front"  If so, it'll give you a new slider that is all the way down, slide it up and you're good to go.

Actually i've tried plugging it into both front and back.
Now I have it on the front.
Unfortunatelly, there is no "Front" Setting in my preferences menu
but only volume, line-in, microphone, pcm-2, in-gain, digital-1.
Forgive me for being completely newbie :P

---

### Post by sryth on 2008-02-18
You've probably already done this, but I'm going to step it out to be sure you and I are on the same page.

Right-click the volume control to bring up the full control board, click edit, then preferences in that menu.  See if you have an option for front.  Make sure it is enabled.  Leave that menu and click the options tab in the main volume control window and make sure input device is set to Front, if that option is available there.

If you've done these.  My apologies, can't help ya. :(

---

### Post by v.cube on 2008-02-18
> **duckgoesoink said:**
> Hi everyone,

I am a new Ubuntu user (installed Feisty three days ago), and everything is working perfectly on my Asus Z53Jc, except for the integrated webcam and microphone. I do have another USB webcam with integrated microphone, but on this the microphone doesn't work (the video does though).

I have searched through the documentation and forums for solutions over the last three days, and ended up more than confused (I'm also an ex Mac and Windows user, so command lines are unfamiliar, although I'm willing to learn). I realise that many people have similar problems, but there is so much conflicting advice and I'm hesitant to use terminal commands unless they are recommended for my situation - it looks like some people have had terrrible experiences running commands not suitable for their setup.

I tried playing with the Volume Control, and checking all boxes, raising levels, etc. I also tried adjusting Sound Preferences, but when I try to test sound capture, everything freezes up and I get error messages. Below is the message I get when doing this with the capture option set to USB Audio or ALSA:



Skype recognises the USB webcam video but not it's microphone - test calls send back no recorded sound. Sound Recorder doesn't record either, and the window freezes.

If anyone could help me figure this out (either through my integrated webcam/microphone or the USB one) I would be very grateful.

Cheers,
Hin :-)

P.S. If I can get a microphone working, it will save having to boot into Vista just to make a Skype call (I hate Vista, it's heavy and sluggish). And I do have all normal sound coming from speakers and such. It's just the microphone not recording.

P.P.S. Both devices work on Vista.

if u want immediate and fast help, i suggest that u use Ubuntu's IRC channel.

To use the above feature, Goto Applications---> Add/Remove...---> Internet----> X-chat. Install it. When X-chat is installed, open it from Applications--->Internet----> X-chat. 

Use #ubuntu at Freenode channel.

All the best and welcome to Ubuntu, the world's no.1 Linux distribution.

---

### Post by Torgas Prim on 2008-02-18
I had the same error when trying to get my sound working properly for Wine and windows games.

The only solution I could do to resolve it was uninstall Wine, and reinstall Alsa by compliing.

I don't have links but I think they will be easy to find on the WineHq website.

---

### Post by luke16 on 2008-02-18
I am having the same problem. Anyone out there know how to fix this?

---

### Post by sglow on 2008-02-19
> **Fot! said:**
> Steve thanx for the quick reply..
Unfortunately I didnt see anything wrong in alsamixer.
I attached a screenshot of my settings there.
Any other ideas? 
Thank you

The screen shot you posted seems to show the playback settings in alsamixer.  Please press F4 to show the capture settings and make sure you have selected the microphone.

S

---

### Post by duckgoesoink on 2008-02-19
Ok, after following advice I found all over google, forums, wikis, etc. I stuffed up my sound settings completely (mostly by using command lines I don't understand). So I just reinstalled Ubuntu again to get everything back to original settings - it only took 15 minutes.

BUT - I did manage to solve the major part of my problem after this - I could change the input source to Front Mic, and now I can record (albeit very bad quality) sound. My microphone is built-in to my laptop, and it got confusing with all the different setting combinations, including the USB mic/webcam.

Now to figure out how to fix the quality of recording - and the Sound Recorder program won't work for me either (I tested in Skype).

---

