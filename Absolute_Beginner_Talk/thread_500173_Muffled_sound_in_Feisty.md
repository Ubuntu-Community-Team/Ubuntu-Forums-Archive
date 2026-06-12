---
title: "Muffled sound in Feisty"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by chawillia on 2007-07-13
I have a VIA technologies sound card which is recognised by Ubuntu but
gives a distorted muffled sound both at the login screen and in normal
usage playing back MP3 file, videos etc.

The sound card works successfully using Knoppix and Mandriva but not Ubuntu
(or MEPIS where the sound is equally distorted).

I have compared the output of the Sound card info using Kinfocentre for
Ubuntu and Mandriva.

The output is virtually identical

Soundcard
Sound Driver:3.8.1a-980706 (ALSA v1.0.14rc1 emulation code)  [Ubuntu]
Sound Driver:3.8.1a-980706 (ALSA v1.0.12 emulation code) [Mandriva]

Kernel: car-ubun 2.6.20-16-generic #2 SMP THU jun 7 20:19:32 UTC 2007 i686
 [Ubuntu]
Kernel: Linux localhost 2.6.17-13mdv #1 5MP Fri Mar 23 19:03:31 UTC 2007
i686 [Mandriva]

Installed drivers
Type 10:ALSA emulation  [both Mandriva and Ubuntu]

Card config
VIA 8237 with AD1980 at 0xc800,irq 21 [Ubuntu] irq 20 [Mandriva]

Audio devices
0 VIA 8237 (DUPLEX) [both Mandriva and Ubuntu] 

Synth devices :NOT ENABLED IN CONFIG [both Mandriva and Ubuntu]

Midi devices: NOT ENABLED IN CONFIG [both Mandriva and Ubuntu]

Timers:
31: system timer [Ubuntu]
7:system timer [Mandriva]

Mixers:
0: Analog Devices AD1980 [both Mandriva and Ubuntu]




I have Googled with no success and followed the driver reloads suggestion
in the ubuntuguide.org with no success.
I have played around with the settings in alsamixer and kmix with  no success.
It is if all the sound is coming from the bass speaker and virtually none from the left and right speakers


Any help would be gratefully received as I really do not want to have to
revert to Mandriva!

This message was previously posted on al.os.linux.ubuntu

Chris

---

### Post by VoiceOvGod on 2007-07-13
Have you tried adjusting the settings in Ubuntu to see if that changes anything?

---

### Post by mgmiller on 2007-07-13
This is a weird answer, but I had a similar problem with a new build and an Nforce 4 mobo with integrated sound.  

Many of the new integrated sound systems are configurable so that the jacks on the back of the machine can serve multiple purposes.  When I set up the mobo with windows, all the sound was fine, once i switched to Ubuntu, I had to move the front and rear speaker plugs to different jacks to get it to work correctly.  

I forget which ones finally worked, but I just took the front speaker plug and moved it to each jack in turn till it worked right, I then did the same with the rear channels.  I did this while running one of the commands listed below which will tell you which channel is which.

Here is a brief synopsis of what I did:

To turn on surround sound:
1) Open the volume control by double clicking the speaker icon in the top panel.
2) Click on edit preferences.
3) Put check marks in both the surround and channel mode boxes.
(you will have to scroll down the list to find channel mode)
4) Make sure the slider for surround is turned up and not muted.
5) On the Options tab, select 4ch, 6ch or 8ch as appropriate. 


To test the speaker set up with a spoken voice for each speaker,
copy the following commands to a terminal.

7.1 channel surround:
```
speaker-test -Dplug:surround71 -c8 -l1 -twav 
```

5.1 channel surround:
```
speaker-test -Dplug:surround51 -c6 -l1 -twav
```

4 channel surround:
 ```
speaker-test -Dplug:surround40 -c4 -l1 -twav
```

2 channel:
 ```
speaker-test -Dplug:front -c2 - l1 -twav
```

the -l1 makes it play the voice 1 time.  If you omit this part, it will continue to loop till you exit the terminal.

for more info:
 ```
man speaker-test
```

---

### Post by chawillia on 2007-07-14
mgmillar,
Many Thanks for replying to  the query.
Turning on Surround Sound and slamming the sliders to max has indeed started the left and right speakers to work 
Looks as if I will be staying with Feisty a bit longer.
Weird though that some other distros work correctly out of the box and Feisty doesn't!
Thank goodness for the Ubuntu community

Thanks again
Chris

---

### Post by mgmiller on 2007-07-14
Glad I could help...:popcorn:

By the way, did the sound utility commands tell you the speakers were plugged into the right jacks or did you have to move them around  as I did?

---

### Post by chawillia on 2007-07-14
mgmiller  (sorry about the wrong spelling in the last post!)
Hi
Some of the speaker tests did not work for me, but one did.

The system thinks my front left and right speakers are my rear left and right speakers!

I did not bother to unplug and replug them as they work correctly in Windows

All very strange.
I would be keen to find out an explanation if you ever get one

Chris

---

### Post by mgmiller on 2007-07-14
I think this happens with newer motherboards with very configurable sound cards that can change their output jacks around based on speaker configuration and driver input.  I don't know how to make the Alsa driver in Ubuntu change the output, but the windows driver probably can.  Sometimes, all you have to do is move the cables and boot windows and it auto configures the jacks, sometimes you have to change a driver setting.  But with a little fiddling, if it bothers you enough, you could probably get both OS's to agree on which speakers are which.

---

### Post by rahimveron on 2007-08-01
thank you

---

### Post by mgmiller on 2007-08-01
you're welcome:popcorn:

---

