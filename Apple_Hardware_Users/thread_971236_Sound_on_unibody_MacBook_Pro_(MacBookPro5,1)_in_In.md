---
title: "Sound on unibody MacBook Pro (MacBookPro5,1) in Intrepid Ibex (Ubuntu 8.10)"
date: 2008-11-04
forum: Apple Hardware Users
---

### Post by calebio on 2008-11-04
Following up to this thread: _[no sound macbook 3,1 with hardy 8.04]("http://ubuntuforums.org/showthread.php?t=777014")_.

Sound from the speakers does not work out of the box on the new MacBook Pro (late 2008, MacBookPro5,1). This seems odd to me, since audio works from the headphone jack, but not the speakers. That should be a clue, but I'm not sure of what-- sound drivers work, but routing is incorrect, or something of the sort. How can I start to debug this?

---

### Post by calebio on 2008-11-11
> **calebio said:**
> Following up to this thread: _[no sound macbook 3,1 with hardy 8.04]("http://ubuntuforums.org/showthread.php?t=777014")_.

Sound from the speakers does not work out of the box on the new MacBook Pro (late 2008, MacBookPro5,1)....

The solution is given [here]("https://help.ubuntu.com/community/MacBook%20Aluminum?#Sound").

---

### Post by guggi on 2008-11-12
hey ur welcome ;-)

cheers guggi :guitar:

---

### Post by Nikos.Alexandris on 2008-11-12
> **guggi said:**
> hey ur welcome ;-)

cheers guggi :guitar:

Hi! Could you post any details? I 've followed tha latest alsa-script thread but it doesn't work for me (built-in speakers). Thanks, Nikos

---

### Post by calebio on 2008-11-12
> **Nikos.Alexandris said:**
> Hi! Could you post any details? I 've followed tha latest alsa-script thread...

Have you done everything here?
[LIST=1]
[*]run the script
[*]reboot
[*]start **alsamixer** in terminal, set up Master, PCM, Line-Out and switch from 2ch to 6ch
[*]call "**sudo alsactl store**" in terminal
[/LIST]

---

### Post by Nikos.Alexandris on 2008-11-12
> **calebio said:**
> Have you done everything here?
[LIST=1]
[*]run the script
[*]reboot
[*]start **alsamixer** in terminal, set up Master, PCM, Line-Out and switch from 2ch to 6ch
[*]call "**sudo alsactl store**" in terminal
[/LIST]

Yep! All four of the steps. I just have the impression that I hear just something eXtremely short and low... just some tiny little short noise :D That's all... it doesn't work :-(

Could it be affected from anything else besides alsamixer? Do the settings in OSX have anything to do with it (probably not but I try to check all possibilities)?

Thank you for your time. Regards, Nikos

---

### Post by Nikos.Alexandris on 2008-11-12
Folks,

I have something really strange (for me at least):
I have sound only on the right speaker and *only* when I set to 6ch!!

EDIT: Sorry, I misunderstood the instructions: I thought it should work when on 2ch and not on 6ch. Anyway, I get no stereo sound only mono(right)!

Who is ready to solve this puzzle?? :D

---

### Post by Nikos.Alexandris on 2008-11-13
> **Nikos.Alexandris said:**
> Folks,

I have something really strange (for me at least):
I have sound only on the right speaker and *only* when I set to 6ch!!

Who is ready to solve this puzzle?? :D

I have even lost the three "Input Sources" fields under the Options tab !!

---

### Post by Nikos.Alexandris on 2008-11-13
Could somebody (using MBP5,1) post the output of the following command:
```
amixer
```

Mine is (note the *Mono* on the third line):

```
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  **Playback channels: Mono**
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Line Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%]
  Front Right: 3 [100%]
Simple mixer control 'Line-Out',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB]
  Front Right: Playback 64 [100%] [0.00dB]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%]
  Front Right: 3 [100%]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '6ch'
  Item0: '6ch'
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 120 [100%] [30.00dB]
  Front Right: Capture 120 [100%] [30.00dB]
Simple mixer control 'Speaker',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
```

**EDIT**: Another example is when i play a .wav file using aplay:
```
aplay -Dplughw:0,0 -fcd /usr/share/sounds/question.wav

Playing WAVE '/usr/share/sounds/question.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, **Mono**
```

If this is what "mutes" the left speaker... any ideas how to change it?

---

### Post by guggi on 2008-11-14
```
dmidecode -s system-product-name
MacBook5,1
```

```
amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65536
  Mono:
  Front Left: Playback 65536 [100%] [on]
  Front Right: Playback 65536 [100%] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 65536
  Front Left: Capture 65536 [100%] [on]
  Front Right: Capture 65536 [100%] [on]

```

```

aplay -Dplughw:0,0 -fcd /usr/share/sounds/question.wav
Wiedergabe Wave '/usr/share/sounds/question.wav' : Signed 16 bit Little Endian, Samplingrate: 44100 Hz, Mono
aplay -Dplughw:0,0 -fcd /usr/share/sounds/card_shuffle.wav 
Wiedergabe Wave '/usr/share/sounds/card_shuffle.wav' : Signed 16 bit Little Endian, Samplingrate: 44100 Hz, Stereo

```

---

### Post by Nikos.Alexandris on 2008-11-14
> **guggi said:**
> ```
dmidecode -s system-product-name
MacBook5,1
```

```
amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65536
  Mono:
  Front Left: Playback 65536 [100%] [on]
  Front Right: Playback 65536 [100%] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 65536
  Front Left: Capture 65536 [100%] [on]
  Front Right: Capture 65536 [100%] [on]

```

Thank you guggi! I don't know why my setings are stuck to Mono (!?). If and whenever I get it fixed I'll post here back.

Regards, Nikos

---

### Post by ecamacho.mx on 2008-11-19
Hi Nikos, I have the same problem as you.. have you found a workaround?

greetings, Erick

---

### Post by Nikos.Alexandris on 2008-11-19
> **ecamacho.mx said:**
> Hi Nikos, I have the same problem as you.. have you found a workaround?

greetings, Erick

And I started feeling that I am the only one with this. Solution: unfortunately not :-(

I've re-installed Intrepid and now I got sound working without any tweak but *only* Mono. What has been changed is that I got back the three "Input Sources" (under the Options Tab) and the output of **amixer** (look below) does not say *Mono* anymore.

```

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65536
  Mono:
  Front Left: Playback 65536 [100%] [on]
  Front Right: Playback 65536 [100%] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 65536
  Front Left: Capture 65536 [100%] [on]
  Front Right: Capture 65536 [100%] [on]
```

All tests, like for example:
```
speaker-test -c2
```
...give only sound from the right speaker (some output below).

```

speaker-test 1.0.17

Playback device is default
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 96 to 1048576
Period size range from 32 to 349526
Using max buffer size 1048576
Periods = 4
was set period_size = 262144
was set buffer_size = 1048576
 0 - Front Left
 1 - Front Right
Time per period = 10.964288
 0 - Front Left
 1 - Front Right
[...]
```

I am searching on the net but haven't found a concrete answer.
Cheers, Nikos

---

### Post by ercoppa on 2008-11-19
> I have the same problem as you
Also me. Same output of Nikos.Alexandris (first posted). Sound only from right speaker. I don't have Input Sources (and the mic doesn't work).

---

### Post by Nikos.Alexandris on 2008-11-19
> **ercoppa said:**
> Also me. Same output of Nikos.Alexandris (first posted). Sound only from right speaker. I don't have Input Sources (and the mic doesn't work).

So we are already 3 people with the same issue. Let us support each other... searching for ALC889A, alsa, linux and related stuff.

Maybe we could file a bug (?)

---

### Post by ecamacho.mx on 2008-11-19
Hi

I couldn't fix the bug, but I manage to get my soundcard working by reinstalling all again. In my case the problem seemed that I hadn' install the package support for intel mac before installing the alsa update. Even when i install it, my soundcard wasn't working. 

Then, i make a fresh install of Ubuntu Intrepid, [install the mactel support]("https://wiki.ubuntu.com/MactelSupportTeam/PPA") and reboot. By this point and by adding the line   
> options snd_hda_intel model=mbp3
to the /etc/modprobe.d/options file i had sound using headphones.

It was no until this point that i install the Alsa upgrade using the script and follow the steps explained on the wiki. Now i have full sound in both of my speakers. Hope it helps to others.

Greetings
Erick

---

### Post by bsolar on 2008-11-20
I still have this problem, sound coming only from right speaker.

I did install the mactel support and run the alsa upgrade script, but still no luck...

---

### Post by josmannen on 2008-11-20
Same problem for me. I just had sound from the right speaker. I ran the script again and did get sound from both speakers. Finally I thought, BUT it seems like I have 2 right speakers - one for each speaker. If I for example listen to Aerosmith's Dude looks like a lady I hear straight away that no sound is coming to the left speaker. Hope you guys understand what I'm trying to say...

Edit: I have perfect stereo sound from the headphone port though

---

### Post by Nikos.Alexandris on 2008-11-22
I finally did another test with the Alsa script. Unfortunately... again I lost my "Input Sources" under the "Options" tab and sound is still right-y :-)

Grrr!! I want the lefty sound in to the game :-p

I have to re-install all again since skype (mic capturing does not work anymore) :-(

---

### Post by melqui on 2008-12-16
[FONT="Verdana"][SIZE="0"]Add another person to the list of people with only the right speaker emitting sound. If anyone solves this please post a solution. I hate showing off my new MacBook Pro and talking so heavily about how great Linux is with only one speaker working haha.[/SIZE][/FONT]

---

### Post by Profiler on 2009-01-02
> **melqui said:**
> [FONT="Verdana"][SIZE="0"]Add another person to the list of people with only the right speaker emitting sound.[/SIZE][/FONT]

and another..., still no solution for this odd problem ?

---

### Post by della on 2009-01-18
> **Profiler said:**
> and another..., still no solution for this odd problem ?

Me too... could someone with a working configuration post their /var/lib/alsa/asound.state?

---

### Post by ercoppa on 2009-01-27
Hi, I have enabled in my sources.list the intrepid-proposed repositary and now with 2.6.27-11-generic I don't need to manually install Alsa 1.0.18(a).

In alsamixer I again see the famous "three input sources" (but the mic don't work but maybe I don't test the correct settings for it) and amixer says:
```
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono                                    
  Limits: Playback 0 - 64                                    
  Mono: Playback 64 [100%] [0.00dB] [on]                     
Simple mixer control 'PCM',0                                 
  Capabilities: pvolume                                      
  Playback channels: Front Left - Front Right                
  Limits: Playback 0 - 255                                   
  Mono:                                                      
  Front Left: Playback 255 [100%] [0.00dB]                   
  Front Right: Playback 255 [100%] [0.00dB]                  
Simple mixer control 'Front',0                               
  Capabilities: pvolume pswitch                              
  Playback channels: Front Left - Front Right                
  Limits: Playback 0 - 64                                    
  Mono:                                                      
  Front Left: Playback 64 [100%] [0.00dB] [on]               
  Front Right: Playback 64 [100%] [0.00dB] [on]              
Simple mixer control 'Line',0                                
  Capabilities: pvolume pswitch                              
  Playback channels: Front Left - Front Right                
  Limits: Playback 0 - 31                                    
  Mono:                                                      
  Front Left: Playback 31 [100%] [12.00dB] [on]              
  Front Right: Playback 31 [100%] [12.00dB] [on]             
Simple mixer control 'Line Boost',0                          
  Capabilities: volume                                       
  Playback channels: Front Left - Front Right                
  Capture channels: Front Left - Front Right                 
  Limits: 0 - 3                                              
  Front Left: 3 [100%]                                       
  Front Right: 3 [100%]                                      
Simple mixer control 'Line-Out',0                            
  Capabilities: pvolume                                      
  Playback channels: Front Left - Front Right                
  Limits: Playback 0 - 64                                    
  Mono:                                                      
  Front Left: Playback 64 [100%] [0.00dB]                    
  Front Right: Playback 64 [100%] [0.00dB]                   
Simple mixer control 'Mic',0                                 
  Capabilities: pvolume pswitch                              
  Playback channels: Front Left - Front Right                
  Limits: Playback 0 - 31                                    
  Mono:                                                      
  Front Left: Playback 31 [100%] [12.00dB] [on]              
  Front Right: Playback 31 [100%] [12.00dB] [on]             
Simple mixer control 'Mic Boost',0                           
  Capabilities: volume                                       
  Playback channels: Front Left - Front Right                
  Capture channels: Front Left - Front Right                 
  Limits: 0 - 3                                              
  Front Left: 3 [100%]                                       
  Front Right: 3 [100%]                                      
Simple mixer control 'IEC958',0                              
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono                                    
  Capture channels: Mono                                     
  Mono: Playback [off] Capture [off]                         
Simple mixer control 'IEC958 Default PCM',0                  
  Capabilities: pswitch pswitch-joined                       
  Playback channels: Mono                                    
  Mono: Playback [off]                                       
Simple mixer control 'Capture',0                             
  Capabilities: cvolume cswitch                              
  Capture channels: Front Left - Front Right                 
  Limits: Capture 0 - 46                                     
  Front Left: Capture 46 [100%] [30.00dB] [on]               
  Front Right: Capture 46 [100%] [30.00dB] [on]              
Simple mixer control 'Capture',1                             
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 46 [100%] [30.00dB] [on]
  Front Right: Capture 46 [100%] [30.00dB] [on]
Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 46 [100%] [30.00dB] [on]
  Front Right: Capture 46 [100%] [30.00dB] [on]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '6ch'
  Item0: '6ch'
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 0 [0%] [-30.00dB]
  Front Right: Capture 0 [0%] [-30.00dB]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Front Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Front Mic'
Simple mixer control 'Input Source',2
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Front Mic'
Simple mixer control 'Speaker',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]

```

Greets, ercoppa.

---

### Post by della on 2009-01-28
> **ercoppa said:**
> Hi, I have enabled in my sources.list the intrepid-proposed repositary and now with 2.6.27-11-generic I don't need to manually install Alsa 1.0.18(a).

Can you hear sound from your left speaker?

---

### Post by Nikos.Alexandris on 2009-01-28
I don't know what has been changed exactly but "amixer" does NOT report "Mono" anymore. Yet, I don't hear any sound from the left speaker.

Maybe because the heat (on the left) has burned-down the left speaker.. :D;)

---

### Post by ercoppa on 2009-01-28
> Can you hear sound from your left speaker? 
Unfortunately no :( :( :(

Greets, ercoppa.

---

### Post by Nikos.Alexandris on 2009-01-29
Folks,

just test yourself the command speaker-test with various -c# settings (where # is a number of "channels"!).

For example:
```
speaker-test -c2
speaker-test -c3
speaker-test -c4
speaker-test -c5
speaker-test -c6
speaker-test -c7
```

...and listen. You can clearly distinguish between right speaker and center speaker... and some more? Only the left speaker does not "speak" :-)

Nikos

---

### Post by ercoppa on 2009-01-29
Hi, the microphone works (Sound record don't work under KDE4, but Audacity yes).
> ..and listen. You can clearly distinguish between right speaker and center speaker...
On MacBook I don't listen also the center speaker, only right speaker works. Maybe MacBook doesn't have the central speaker.

P.s. Nikos.Alexandris do you manually install alsa >=1.0.18 or update the kernel from intrepid-proposed repository (like me)?

Greets, ercoppa.

---

### Post by Nikos.Alexandris on 2009-01-29
> **ercoppa said:**
> 
[...]
On MacBook I don't listen also the center speaker, only right speaker works. Maybe MacBook doesn't have the central speaker.

P.s. Nikos.Alexandris do you manually install alsa >=1.0.18 or update the kernel from intrepid-proposed repository (like me)?

Greets, ercoppa.

Hi ercoppa. I did NOT install alsa on my own. Just what the updates brought to the machine :-)

I don't know if the MB has got NOT a center speaker. Perhaps looking at some specs or at [http://www.ifixit.com/Guide/First-Look/Mac/MacBook-Unibody](http://www.ifixit.com/Guide/First-Look/Mac/MacBook-Unibody) ?

Cheers, Nikos

---

### Post by ercoppa on 2009-01-29
Mmmmm, [this picture]("http://static3.ifixit.com/igi/MlhoVSZWEGDBJR1C.large") (see on the left) show 3 speakers or I am in wrong?

Greets, ercoppa.

---

### Post by buntuLo on 2009-02-01
> **Nikos.Alexandris said:**
> ...and listen. You can clearly distinguish between right speaker and center speaker... and some more? Only the left speaker does not "speak" :-)Nikos

hi Nikos, i installed the latest Alsa 1.0.19, switched to six channels and got sound through (both) headphones. then set max volume to the channel 'front' in HDAnvidia mixer and got the right speaker working. but when i test all channels with speaker-test -c5, i get sound just from the right one, the central speaker doesn't work. by the way, in the MacBook Pro this is supposed to be a tiny subwoofer. any possible hint about how you got it working? cheers, Lo.

ps: while restoring and reinstalling Alsa, i also happened to loose the input selectors for the microphone. in my case this was easily solved re-enabling them in the 'configure channels' menu of HDAnvidia mixer. i'm actually guessing that we have the same mixer gui in Gnome and KDE, as the link to launch the HDAnvidia mixer is here called KMix, the KDE mixer. does the Gnome mixer link open the same one for you?

---

### Post by ercoppa on 2009-02-16
Another bad news for me. When I go in suspend mode and resume, the audio is "dead", I must open the volume control an switch channels from 6ch to 2ch and from 2ch to 6ch. Do other persons have this problem?

Greets, ercoppa.

---

### Post by Nikos.Alexandris on 2009-02-16
> **ercoppa said:**
> Another bad news for me. When I go in suspend mode and resume, the audio is "dead", I must open the volume control an switch channels from 6ch to 2ch and from 2ch to 6ch. Do other persons have this problem?

Greets, ercoppa.

I _think_ that I also experienced this last week. I'll try to remember and try it out at some point.

Nikos

---

### Post by Nikos.Alexandris on 2009-02-18
> **buntuLo said:**
> hi Nikos, i installed the latest Alsa 1.0.19, switched to six channels and got sound through (both) headphones. then set max volume to the channel 'front' in HDAnvidia mixer and got the right speaker working. but when i test all channels with speaker-test -c5, i get sound just from the right one, the central speaker doesn't work. by the way, in the MacBook Pro this is supposed to be a tiny subwoofer. any possible hint about how you got it working? cheers, Lo.


Lo,

I missed this question. Apologies. I did not do anything specific. In fact I just ran the speaker-test -c# and I tried to listen carefully what's going on.

Sorry that I can't help you further.

---

### Post by acron on 2009-02-22
Hi there,

I understand solved as accomplished to get the best currently possible result: Sound on the right speaker. Is that correct?
Has anyone already submited a bug-report to [alsa]("https://bugtrack.alsa-project.org/alsa-bug/main_page.php")?
I searched the bug tracker but did not find a matching entrance...


Greets acron

---

### Post by ercoppa on 2009-02-23
> Has anyone already submited a bug-report to alsa?
I think not, can you open one?

Greets, ercoppa

---

### Post by della on 2009-03-03
> **ercoppa said:**
> I think not, can you open one?

Greets, ercoppa

I submitted the bug. See the report at

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4432](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4432)

---

### Post by cyberdork33 on 2009-03-03
> **della said:**
> I submitted the bug. See the report at

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4432](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4432)
I started a bug in launchpad pointing to this (I hope you don't mind, but I used your words from the alsa bug).
[https://bugs.edge.launchpad.net/mactel-support/+bug/337314](https://bugs.edge.launchpad.net/mactel-support/+bug/337314)

---

### Post by Nikos.Alexandris on 2009-03-04
della & cyberdork33, thank you for reporting the "bug".
Kindest regards, Nikos

---

### Post by Nikos.Alexandris on 2009-03-09
(Who?) Can somebody mark this thread as NON-solved?

Cheers, Nikos

---

### Post by cyberdork33 on 2009-03-09
> **Nikos.Alexandris said:**
> (Who?) Can somebody mark this thread as NON-solved?

Cheers, Nikos
report the thread to a mod.

---

### Post by Nikos.Alexandris on 2009-03-10
I've just posted a request to KiwiNZ.
Cheers, Nikos

---

### Post by Profiler on 2009-03-10
Great to hear that its reported, because this problem is the main reasen why i still use OSX every day.

---

### Post by cyberdork33 on 2009-03-11
> **Nikos.Alexandris said:**
> I've just posted a request to KiwiNZ.
Cheers, Nikos
and it appears to be repaired

---

### Post by jamesey on 2009-03-15
I think I might be one of the first to have this bug on the IMac 9,1. I have sound out of my headphone jack, but not from my speakers.

---

### Post by N_Nick on 2009-03-16
I don't have extensive experience on Linux/Ubuntu but you could try using Pulse.

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

---

### Post by jamesey on 2009-03-16
> **N_Nick said:**
> I don't have extensive experience on Linux/Ubuntu but you could try using Pulse.

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

what's the difference between PulseAudio and Alsamixer? Do they do the same thing?

---

### Post by cyberdork33 on 2009-03-16
> **jamesey said:**
> what's the difference between PulseAudio and Alsamixer? Do they do the same thing?
Ubuntu uses PulseAudio by default, but you still have to have ALSA working to activate your hardware properly.

---

### Post by jamesey on 2009-03-17
On another forum, someone suggested

> I've come up with a non-ideal fix for my problem. I found out that what is really going on is that ubuntu is mixing up my headphone jack and speaker outputs.

With "options snd-hda-intel model=auto" set in /etc/modprobe.d/alsa-base:
When I plug my headphones into the headphone jack, it believes it to be the speakers and is already outputting sound. Laptop speakers do not function even when switches in the volume control are toggled. <-----Thus headphone only sound

With "options snd-hda-intel model=arima" set in /etc/modprobe.d/alsa-base:
When I plug headphones into the headphone jack nothing happens. When I toggle Headphone switch to 'checked' in volume control, playback can be heard from laptop speakers! If I uncheck it, I can still get headphone sound from the "Front" output jack as this would always be on anyhow.
When I toggle the headphone switch, I can see in alsamixergui the mute toggles going on and off for the headphone channel. It is not possible to toggle the mute for the PCM channel. Volume is controlled by using the PCM, Front, or Master sliders; Headphone sliders are nonexistant.

My etc/modprobe.d/alsa-base file looks like this. Is this right for an imac?

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2

```

and is this right for the etc/modprobe.d/options file?
```
# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2

# Stop auto-association.
# LP: #264104
options ipw2200 associate=0

# XXX: Ignore HPA by default. Needs to be revisted in jaunty
options libata ignore_hpa=1
options snd_hda_intel model=imac24
```

---

### Post by cyberdork33 on 2009-03-17
> **jamesey said:**
> My etc/modprobe.d/alsa-base file looks like this. Is this right for an imac? hard to tell since nobody else has your same sound hardware.

> **jamesey said:**
> and is this right for the etc/modprobe.d/options file?
I am going to *guess* that the imac24 model is not correct for you (unless it gets updated), but there is likely not a correct model to put there yet either.

---

### Post by coiske on 2009-05-01
> **ercoppa said:**
> Another bad news for me. When I go in suspend mode and resume, the audio is "dead", I must open the volume control an switch channels from 6ch to 2ch and from 2ch to 6ch. Do other persons have this problem?

Greets, ercoppa.

I'm having this suspend/resume audio problem, too.  Any idea how I could reset it to 6ch from the command line?  If I could figure that out, I could put it in a script that would run each time I resume.

---

### Post by chadlewis on 2009-06-14
Why is this marked as solved? The Mactel support instructions do not work for some, myself included. 5,1.

---

### Post by luigi.viggiano on 2009-06-28
With 9.04 on mbp 5,1 sounds work fine, but it doesn't anymore after a resume, tested now.

---

### Post by superfly85 on 2009-08-28
Conexant CX20549 (Venice) 

sound is only comming out the left speaker.

---

### Post by amd-64 on 2009-08-28
> **luigi.viggiano said:**
> With 9.04 on mbp 5,1 sounds work fine, but it doesn't anymore after a resume, tested now.

This may help [http://ubuntuforums.org/showthread.php?t=1249885](http://ubuntuforums.org/showthread.php?t=1249885)

---

