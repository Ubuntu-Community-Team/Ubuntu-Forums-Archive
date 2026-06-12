---
title: "Total noob can't get sound to work!"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Lordcoca on 2007-04-23
This is a rough OS to use if you're not too tech savvy...

Here's what aplay -l does:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Anyone have any advice?

---

### Post by annda on 2007-04-23
well, first try with alsamixer from the terminal to see if master and PCM are not per chance muted. if so, unmute BOTH by hitting 'm'

also, what happens when you test your device from system > preferences > sound?

---

### Post by Albi on 2007-04-23
A noob mistake I made was that "Headphone Jack Sense" was checked under switches

---

### Post by Lordcoca on 2007-04-23
> **annda said:**
> well, first try with alsamixer from the terminal to see if master and PCM are not per chance muted. if so, unmute BOTH by hitting 'm'

also, what happens when you test your device from system > preferences > sound?

alsamixer shows:

Headphone - unmuted
PCM -unmuted
Front - unmuted
Front mic - unmuted
Mic - unmuted
Caller I - muted
Input So (above it says Mic but no unmuting option)
Off-hook - muted

My laptop is a Toshiba a135-s4427 and it has the volume slider on the side of the computer which I can turn up and down. When I do so the volume speaker comes up and I can change the volume just fine. When I play anything through amarok, youtube etc they play fine there is just no sound.



Under sound preferences everything is set to auto detect, but when I click test the box saying testing pipeline comes up and starts off 1/5 of the way full but never goes higher and I never hear any sound :confused:

---

### Post by Lordcoca on 2007-04-23
> **Albi said:**
> A noob mistake I made was that "Headphone Jack Sense" was checked under switches

Where can I turn this off?

---

### Post by annda on 2007-04-23
this is tricky, because every soundcard has different options. try right clicking on the sound applet in the panel, opening the volume control and enabling everything in preferences. then experiment with the various switches.

---

### Post by imon9 on 2007-04-23
don't worry, u will get pass this stage pretty soon, coz the forum members will always offer their hands...

i am not sure if u can do much help..but let start trouble shooting a bit:
(1) open a terminal and type in the commnad: speaker-test
if it play some sound, u got ur sound card correctly configured

(2) try upgrade to ALSA 1.0.14rc3 at [http://www.alsa-project.org/](http://www.alsa-project.org/) 
(u will need to download a few tar. file and un-compress then compile them...err ask me if u not sure how to do it)

(3) try running "sudo alsaconf" to reconfigure your soundcard;

(4) try restarting alsasound by the command "sudo /etc/init./alsasound restart

(5) try adjusting the volume by command "alsamixer"

if all else fail...please report back
(actually there is a helpful community at freenode IRC channel #alsa, so u could try find help there..they are more expert...but i suggest u try the above first)

---

### Post by Lordcoca on 2007-04-23
> **imon9 said:**
> don't worry, u will get pass this stage pretty soon, coz the forum members will always offer their hands...

i am not sure if u can do much help..but let start trouble shooting a bit:
(1) open a terminal and type in the commnad: speaker-test
if it play some sound, u got ur sound card correctly configured

(2) try upgrade to ALSA 1.0.14rc3 at [http://www.alsa-project.org/](http://www.alsa-project.org/) 
(u will need to download a few tar. file and un-compress then compile them...err ask me if u not sure how to do it)

(3) try running "sudo alsaconf" to reconfigure your soundcard;

(4) try restarting alsasound by the command "sudo /etc/init./alsasound restart

(5) try adjusting the volume by command "alsamixer"

if all else fail...please report back
(actually there is a helpful community at freenode IRC channel #alsa, so u could try find help there..they are more expert...but i suggest u try the above first)

Step 1 produced no sound.

I'm stuck at step 2, how do I uncompress and compile this stuff?

---

### Post by imon9 on 2007-04-23
erm..i suppose u have the program like archiver, xarchiver, erm 7zip? uncomprass like it is a zip file to a folder (please check "extract with full path) ....eg: to /home/temp/alsa

there is ways to do this in commandline too...but i cant recalled it now)

next: open up terminal and go to that folder by:
/home/temp/alsa
(note: sometimes ur archiver program might uncompress extra folder)
so, it maybe something like this /home/temp/alsa/alsa1.10.14rc3/

next command: ./configure
next command: make
next command: sudo make install

---

### Post by Lordcoca on 2007-04-23
> **imon9 said:**
> erm..i suppose u have the program like archiver, xarchiver, erm 7zip? uncomprass like it is a zip file to a folder (please check "extract with full path) ....eg: to /home/temp/alsa

there is ways to do this in commandline too...but i cant recalled it now)

next: open up terminal and go to that folder by:
/home/temp/alsa
(note: sometimes ur archiver program might uncompress extra folder)
so, it maybe something like this /home/temp/alsa/alsa1.10.14rc3/

next command: ./configure
next command: make
next command: sudo make install

when I open up terminal and try to go to that folder it says bash: home/temp etc. is a directory

and that's it? :confused:

---

### Post by Lordcoca on 2007-04-23
Man, I can totally see how this os hasn't caught on, it's ridiculously difficult for the average user to get a hold of...

---

### Post by imon9 on 2007-04-23
sorry: i forgot to mention, the command to go to a folder is:
cd /home/temp/alsa

or cd /home/temp/alsa/alsa1.10.14rc3 (maybe)
try use the command "dir" to see the files in the folder /home/temp/alsa

---

### Post by Lordcoca on 2007-04-23
> **imon9 said:**
> erm..i suppose u have the program like archiver, xarchiver, erm 7zip? uncomprass like it is a zip file to a folder (please check "extract with full path) ....eg: to /home/temp/alsa

there is ways to do this in commandline too...but i cant recalled it now)

next: open up terminal and go to that folder by:
/home/temp/alsa
(note: sometimes ur archiver program might uncompress extra folder)
so, it maybe something like this /home/temp/alsa/alsa1.10.14rc3/

next command: ./configure
next command: make
next command: sudo make install

OK, so I got this all done and at the end it said: 


WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.

How do I fix this?

---

### Post by annda on 2007-04-23
alsamixer again.

---

### Post by Lordcoca on 2007-04-23
> **annda said:**
> alsamixer again.

when I go to alsamixer nothing is muted except for what I mentioned on page 1, and whenever I try to unmute then and go back to alsamixer it just mutes them again?

---

### Post by imon9 on 2007-04-23
no...that is just a warning messgae...it desnt nessasarily means u had ur mixer muted....

anyway, try the "sudo alsaconf" and "test-speaker" after that...and report back..i will be here all nite..trying to finish some reports

---

### Post by annda on 2007-04-23
it shouldn't really be necessary but try sudo alsamixer. raise the levels to 80% or something. that way sound should be audible but not damage your speakers.

try enabling everything in preferences (applet) and check the switches again. i have no more ideas, sorry.

p.s. and congratulations on your first compilation!

---

### Post by Lordcoca on 2007-04-23
> **imon9 said:**
> no...that is just a warning messgae...it desnt nessasarily means u had ur mixer muted....

anyway, try the "sudo alsaconf" and "test-speaker" after that...and report back..i will be here all nite..trying to finish some reports

I get this: sudo: alsaconf: command not found

---

### Post by Lordcoca on 2007-04-24
So...anyone else got any advice? I still can't get anything to work.

---

### Post by Lordcoca on 2007-04-24
Should I try reinstalling Ubuntu? Is there any chance that will yield any positive results?

---

### Post by Lordcoca on 2007-04-24
I've been trying to run alsaconf to see what that can do. Whenever I try sudo alsaconf I get "command not found"

if I type whereis alsaconf I get:
alsaconf:

I'm at a loss here.

---

### Post by Snowmayne on 2007-04-24
One thing I noticed is that when edgy eft first came out, it seemed the video drivers were an issue with 80% of people doing the upgrade. This time it seems to be sound that's the issue.

I've been trolling the forum since feisty was 'officially' released last week trying to fix my sound problem. I've tried just about every suggestion from reinstalling to OS, reconfiguring alsa, deleting and then reinstalling gstream and anything else dealing with sound.

I can't speak for anyone else with sound issues, but the only thing I've found is that when I was trying to reinstall gstream, I noticed that the error I was getting was that 'the file/directory doesn't exist. So, looking at the path that was provided by the error (can't recall now since I'm on my windows partition to write this) is that, true enough, there were no files in the gstream folders. Using apt-get or synaptic to uninstall gstream and then reinstall produced the same result. System says it was updated, but no files were added.

So, at least I was able to track down the problem (I think), but now it's still a question of 'how the <bleep> do I get those files?'

<sigh> everytime I get ubuntu tweaked just right and get all the apps I need up and running, something seems to break that requires a brand new install

---

### Post by imon9 on 2007-04-24
no, please do not try reinstall ubuntu... there aren't going to be much difference with that...

I strongly suggest you to go to IRC channel #alsa at freenode and ask in the chatroom... they have made a script to help you troubleshoot... and most probably they can get it right for you

---

### Post by Snowmayne on 2007-04-25
> **imon9 said:**
> no, please do not try reinstall ubuntu... there aren't going to be much difference with that...

That's just what I did and it actually fixed the problem. I ***think*** the problem was my original upgrade was done through synaptic while the reinstall this morning was from a LiveCD

---

