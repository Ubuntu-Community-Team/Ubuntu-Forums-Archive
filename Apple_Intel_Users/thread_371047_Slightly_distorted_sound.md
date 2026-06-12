---
title: "Slightly distorted sound"
date: 2007-02-26
forum: Apple Intel Users
---

### Post by hackeron on 2007-02-26
I'm on a macbook pro 15" 2.16ghz Core Duo (not core 2 duo) and listening to music on Ubuntu produces distorted sound - more noticeable in speech and higher frequencies but certainly enough to make listening to music not enjoyable.

This distortion isn't huge but sounds like as if you pushed all frequencies by 10db or so, not so or at all at times noticeable from the internal speakers but with quality external speakers or headphones, very noticeable.

Other than the distortion, both internal speakers and headphone socket work as expected, speakers are muted when inserting headphones, the volume control on the keyboard works after selecting PCM in volume control but this distortion is just stopping me from using linux, anyone had that problem and knows a solution?

---

### Post by cocoia on 2007-02-26
Did you try alsa-mixer and put some sliders a bit down? Sometimes the settings in the mixer can produce a bit sound that the speaker doesn't eat for breakfast.

---

### Post by hackeron on 2007-02-26
Yes, I've tried keeping PCM to minimum and the Side slider to max, then the other way around, then both to the same number - same bad sound :(

You can especially hear how terrible the sound is if you start gst-properties-manager and play a test tune, instead of a beep, you hear shhhhhrrrrrr with the beep.

The speakers and headphones in question are behringer 2031A - the big heavy ones and the Shure E5 headphones -- both can handle an incredible amount of decibels :)

---

### Post by cocoia on 2007-02-26
That's really awful. The problem doesn't manifest in OS X?

---

### Post by hackeron on 2007-02-26
> **cocoia said:**
> That's really awful. The problem doesn't manifest in OS X?

Nope, sounds great in OSX :( -- Currently booted in OSX to watch scrubs, very good sound for a laptop.

---

### Post by hackeron on 2007-02-26
In the above post I meant gstreamer-properties -- under the audio tab, click Test, is it only heavily distorted for me?  -- If not, is that a pro core duo or core 2 duo?

---

### Post by cocoia on 2007-02-26
What version of alsa do you have? Did you apply the patches / install drivers recommended in Howto's? If so, which ones?

---

### Post by madcow222 on 2007-02-26
I've had what I think to be the exact same problem that you're having on my 15" CD MBP.  A workaround I've discovered is to restart alsa via the command:

```
sudo /etc/init.d/alsasound restart
```

What's weird about it is that sometimes upon startup the sound is fine and I don't need to restart alsa, and other times it has the same distortion that you're describing.

A bit OT, but I was wondering how you got internal speakers and headphone detection to work properly?

---

### Post by hackeron on 2007-02-27
> **madcow222 said:**
> I've had what I think to be the exact same problem that you're having on my 15" CD MBP.  A workaround I've discovered is to restart alsa via the command:

```
sudo /etc/init.d/alsasound restart
```

What's weird about it is that sometimes upon startup the sound is fine and I don't need to restart alsa, and other times it has the same distortion that you're describing.

A bit OT, but I was wondering how you got internal speakers and headphone detection to work properly?

I'll give that a try but I think you're right, my first boot didn't experience sound problems but all boot ups after had distortion, I'll try the alsa restart tip.

As for the speakers and headphones, I'm using ubuntu feisty 3 (well, dist-upgraded to 4 now) and the 2.6.20 kernel's alsa version fixed the problem of speakers and headphones but you still need to open volume control (double click on the speaker icon) > Settings > Enable "Side" and "Line in as ouput" Close the settings-wndow Activate "Line in as output" on the switches-tab and adjust the volume with the "Side-slider" -- but after that everything works as expected. It doesn't remember your speaker volume and headphones volume like in OSX but that's not too bad.

---

### Post by Gen2ly on 2007-03-01
Strange.  I was looking at this topic because sometimes my MacBook (actually with certain programs) has a crackling sound.  So, I tried:
> sudo /etc/init.d/alsasound restart

I don't even has this run time program.  Weird.  Can anyone else confirm this?

---

### Post by jonj on 2007-03-12
sudo /etc/init.d/alsa-utils restart 

should do it

Incidentally, alsa-utils was not selected in the list of services on my box, so I've selected it to see if this improves things (with skype)

services-admin is the command to bring up the service list, or you'll find 'Services' under System/Administration

---
[http://know.homelinux.com/](http://know.homelinux.com/)

---

### Post by mealz on 2007-03-13
I'm having the same sound issues with Suse 10.2 on my macbook and restarting alsa does resolve them!

---

### Post by russellc on 2007-03-27
I can confirm this behaviour. Sometimes on boot, sound is perfectly fine, but sometimes it is crackly. Reloading alsa fixes it, but it would be nice to never have this problem :p

---

### Post by Lotharsson on 2007-04-23
I can partly confirm and partly dis-confirm this behaviour.  

I have a MythTV box on KUbuntu connected to my newly acquired hi-fi speakers and amp using SPDIF (PCM over a coaxial cable).  The sound card is on-board Intel HDA.  I use Amarok as well for playing FLACs ripped from my CDs.

I've spent a fair bit of time trying to figure out the high frequency crackling that creeps into the sound.  Sometimes it's there and sometimes it is not.  (This is after figuring out that something was resampling 44.1kHz FLACs to 48kHz - and doing a very poor and noisy job.  I turned off the KDE sound system and switched explicitly to ALSA to stop this happening.  I haven't created a .asoundrc or asound.conf file - so far Ubuntu seems to be happy producing audio without it, except for the crackle.)

I thought I'd fixed it recently by configuring Amarok to use OSS which was emulated by ALSA).  That seemed to good to be true - direct use of ALSA crackled but using the ALSA-provided OSS emulation layer did not?!  However, a couple of reboots later and the crackle is back even using OSS emulation.  Repeated restarts of ALSA did not fix it :( Any further ideas?

I've seen other posts saying some sound cards need to keep the PCM slider <75% in the mixer, but the PCM slider doesn't affect the volume at all when using SPDIF (nor does it affect the volume using HDA analog line out).  The ONLY slider that has an effect when using SPDIF is IEC958.

Any help would be appreciated :-)  It's a little bit annoying to have decent hi-fi gear suffering from mysterious intermittent crackling...

---

### Post by Lotharsson on 2007-04-23
I also see PCM/SPDIF output stopping at times when Amarok goes from one song to the next.  Reconfiguring the Engine (oss or ALSA, default or /dev/dsp or ALSA's spdif device) doesn't seem to make any difference.  Analog output still works unless I explicitly select a digital-only output.  ](*,)

---

### Post by bsantos on 2007-04-24
I'm having sound issues on Feisty, distorted on one side, and restarting alsa doesn't solve it. Is the driver buggy or something? The main and front could be merged also. :)

This happens after a while but is ok on boot. Also I get huge loads of xrun erros if I try to use jackd... :(

---

### Post by ronocdh on 2007-04-24
> **bsantos said:**
> I'm having sound issues on Feisty, distorted on one side, and restarting alsa doesn't solve it. Is the driver buggy or something? The main and front could be merged also. :)

This happens after a while but is ok on boot. Also I get huge loads of xrun erros if I try to use jackd... :(
Heh, odd: I had this problem in Edgy, I don't in Feisty! You're on a MB CD, yes? Perhaps we should all conform to the scriptkiddy protocol of explicitly detailing our hardware in our sigs; it would eliminate a lot of confusion! ;)

Seriously, please keep us updated on this. Have you asked around at the multimedia forum? It's possible a lot of new users looking for fixes went straight there instead of stopping by the Apple Intel ones.

---

### Post by bsantos on 2007-04-24
Core 2 Duo. :| It isn't frequent, but it happens. Can you use jackd?

---

### Post by ronocdh on 2007-04-24
> **bsantos said:**
> Core 2 Duo. :| It isn't frequent, but it happens. Can you use jackd?
Haven't tried yet, actually. I was hoping for an early release of Ubuntu Studio to really go nuts with that, but I suppose they have a ways to go yet, and we can maybe provide some input by testing audio on our Macs! I'll give it a go this week and let you know.

---

### Post by bsantos on 2007-04-24
Cool! Good luck! :)

---

### Post by roadcone on 2007-04-25
I have some news... Good or bad is up to you. Now, I'm a complete n00b, so I can't give you any detailed tech info, but I have Ubuntu running on an IBM Thinkpad T60, and I have had and still have high-level distortion. Mid-level and bass is fine. I have read through and tried restarting alsa, and this does nothing. I've tried running audio straight from CD in case it was a problem with my OGGs, running it from rhythmbox and from VLC. They all have high-level distortion.

---

### Post by ronocdh on 2007-04-25
> **roadcone said:**
> I have some news... Good or bad is up to you. Now, I'm a complete n00b, so I can't give you any detailed tech info, but I have Ubuntu running on an IBM Thinkpad T60, and I have had and still have high-level distortion. Mid-level and bass is fine. I have read through and tried restarting alsa, and this does nothing. I've tried running audio straight from CD in case it was a problem with my OGGs, running it from rhythmbox and from VLC. They all have high-level distortion.
Have you tried this? [http://ubuntuforums.org/showthread.php?t=418681&page=2](http://ubuntuforums.org/showthread.php?t=418681&page=2) Please post back with your experience on it.

---

### Post by Valinski on 2007-04-27
Hi people. Ive had the same issue with my version of ubuntu. This is how i solve the problem. 

The line in fader seems to be the one distorting things for some strange reason. 

Try muting it.

I did and my sound is now perfectly clear!

---

### Post by rdwtux on 2007-05-18
I also have this problem on a Macbook Core Duo running Fiesty.   Sound is slightly distorted on the left speaker (or left earphone with headphones plugged in). 

Restarting also doesn't help. 

I'm not sure what you mean by muting the 'line in fader', however I've tried muting and unmuting all inputs without any luck. 

Has anyone else found a solution to this?  I'm guessing it's a bug in alsa.

---

### Post by bsantos on 2007-05-19
> **rdwtux said:**
> I also have this problem on a Macbook Core Duo running Fiesty.   Sound is slightly distorted on the left speaker (or left earphone with headphones plugged in). 

Restarting also doesn't help. 

I'm not sure what you mean by muting the 'line in fader', however I've tried muting and unmuting all inputs without any luck. 

Has anyone else found a solution to this?  I'm guessing it's a bug in alsa.

No. I notice it is a mater of luck, in some boots it is ok, in other it isn't. It must be something with alsa, yes. Have you tried ekiga's sound test? Here it sounds awful. 

There's also two mics in the configuration options when there's only one available and a line-in.


jackd is unusable, also.

Is anyone on gutsy that may see if there's any difference?

---

### Post by rdwtux on 2007-05-21
I hadn't noticed that some reboots do fix the sound - your right.  My current boot is working fine, no sound distortion.  I guess I won't reboot for a while :)   

I see there are a few bugs mentioning sound distortion on launchpad, generally for laptops.

---

### Post by Lovely Baby on 2007-05-21
Spam.

---

### Post by DucentiVigintiDuo on 2007-05-23
> **ronocdh said:**
>  I was hoping for an early release of Ubuntu Studio to really go nuts with that, but I suppose they have a ways to go yet, and we can maybe provide some input by testing audio on our Macs! I'll give it a go this week and let you know.

I'm a relative noob to Linux, and quite a big one at Ubuntu. Used to have Fedora Core 4 before that.

I now decided to make Ubuntu Feisty Fawn 7.04 my only OS, and I'm really happy with my choice, except for a few really annoying problems like this one.

Like someone mentioned before, I have a crackling sound, but only on the left channel.
At first I thought it was my output jack but after a reboot I realized it's software based.

I updated to Ubuntu Studio from Feisty using the repo and following the directions on the site, but the problem still isn't fixed. I was kinda hoping for a magical solution but I guess that's not an option. :p

If someone could give some specific details as to how I can control ALSA sliders, install any necessary plugins/drivers/whatever, I'd be really, REALLY greatful. 

Listening to and composing music are two things I like to do very, very frequently so you can understand how annoying this is to me.

Thanks in advance to anyone that replies with a useful tip or two.

Hardware:

Macbook Core Duo 1.83, 512MB RAM, 60GB HDD.

---

### Post by ronocdh on 2007-05-23
> **DucentiVigintiDuo said:**
> If someone could give some specific details as to how I can control ALSA sliders, install any necessary plugins/drivers/whatever, I'd be really, REALLY greatful.
Type **alsamixer** in the terminal, mate! Sorry I can't help out more; my sound has never been crackly. =/

Welcome aboard!

---

### Post by Gen2ly on 2007-05-24
> **DucentiVigintiDuo said:**
> Like someone mentioned before, I have a crackling sound, but only on the left channel.
At first I thought it was my output jack but after a reboot I realized it's software based.

I updated to Ubuntu Studio from Feisty using the repo and following the directions on the site, but the problem still isn't fixed. I was kinda hoping for a magical solution but I guess that's not an option. :p

If someone could give some specific details as to how I can control ALSA sliders, install any necessary plugins/drivers/whatever, I'd be really, REALLY greatful. 


Thanks for letting us know of your problem DucentiViginitDruo.  I too have the exact same problem that you do.  I originally thought that I had blown my left speaker but after trying OS X I had no problems.  The last little bit I've eliminated sound cracklin', here's what I did:

First I set alsasound to the levels below, then I turned off ESD sound.  Not sure which one fixed it but after rebooting all is fine.  I suspect it's the later as System Sounds uses an archaic standard, thats overly complex and doesn't work well for many people.  Could you tell me if this fixed your problems as well?

---

### Post by DucentiVigintiDuo on 2007-05-24
> **Dirk.R.Gently said:**
> Thanks for letting us know of your problem DucentiViginitDruo.  I too have the exact same problem that you do.  I originally thought that I had blown my left speaker but after trying OS X I had no problems.  The last little bit I've eliminated sound cracklin', here's what I did:

First I set alsasound to the levels below, then I turned off ESD sound.  Not sure which one fixed it but after rebooting all is fine.  I suspect it's the later as System Sounds uses an archaic standard, thats overly complex and doesn't work well for many people.  Could you tell me if this fixed your problems as well?

First of all, **ronocdh**, thanks for the terminal command and the welcome! :)

Secondly,** Dirk.R.Gently**, thank you so much for your instructions! They seem to have fixed the problem!
It feels really good to have clean sound again! :D

I realized I had ESD turned off before, so *it's probably the ALSA levels that made the difference*.
Mine were too high. Once again, thank you so much for the instructions!

Maybe we should make this a sticky? I don't know if it's that important but it seems a lot of people are having trouble with this. If anyone could try these steps as well and tell us if it works that'd help a lot of people out.

---

### Post by FreedomFromWindows on 2007-05-24
In case non-Mac Intel users come across this thread, I was having a similar problem with a AMD64 X2 (not exactly Intel, is it?) Asus with Soundblaster Audigy soundcard - the whole sound system worked fine with no distortion, until I did a brand new install of Ubuntu Studio (first release version).  

From that point on, at odd and unpredictable times, a clipping-like distortion would appear, generally starting slowly at first, and not correlated with starting or stopping other sounds (but only audible when playing something, usually midi keyboard or Rosegarden midi playback or audio track playback).  Sometimes it was so subtle that it just sounded like something wasn't quite clear, but often it got absolutely terrible like an overdriven guitar (all this without changing any levels or inputs).  It might last a minute or two in its annoying phase.  Then it would suddenly and abruptly disappear without stopping or restarting any applications, never mind the computer, only to reappear perhaps five or ten minutes later again.  The only apparent correlation with any other activity was that it seemed to often start toward the end of long and otherwise successful audio recording takes - but that may be just my paranoid imagination.

I tried disabling lots of things, and trying things like changing mixer configurations or time sources in Rosegarden, but there didn't appear to be any effect.  However, when I disabled the ESD by unchecking the 'Enable software sound mixing (ESD)' checkbox through system->preferences->sound->sound tab, I thought it went away, but it came back again.  Since I had not rebooted after clearing the checkbox (as it has been suggested is required - is there some Windows code in here somewhere?), I tried that.

Since that time about twenty minutes ago, it has not gone into 'overdrive' mode again... so perhaps this may be a solution on platforms other than Apple?  Thanks to those that creatively tracked it down!

---

### Post by DucentiVigintiDuo on 2007-05-30
I guess I was too enthusiastic...the distortion problem striked back, more than once.
I tried the ALSA settings and then I tried another solution posted somewhere in the forum where you place a script on boot that kills and restarts the server, but none of these seem to work, and now when I boot into Ubuntu all sound levels are 100% and muted.

How can I save my ALSA settings and have them restored on boot-time?


All these problems and a few more I've had with mySQL are making me seriously consider a fresh install of Ubuntu Studio from the installation DVD, even though it'll be a pain to set everything up again. :-?

---

### Post by Valinski on 2007-06-01
Havent had time to read the whole thread but i fixed mine by just changing the Devices menu in Preference>Sound from autodetect to ALSA. Im sure you have probably tried this but i thought it might still be worth posting...

Hope you sort it mukka :D

---

### Post by ivesjd on 2007-06-02
I just realized that my sound was crackling, and all I did was System>Administration>Services and then checked audio settings management. Sound is better at least on my laptop speakers. (the baby is asleep or else I would try through my stereo)

---

### Post by vh1 on 2007-06-04
they list [a fix on the debian wiki](http://wiki.debian.org/MacBook#head-d374bb9e1b7183c133759a8c6877a34c50c4ba7d). I've got it applied but will give it a few days of testing

---

### Post by hanjet on 2007-06-06
For the longest time I had the glitchy sound in the left channel as well ( it was random, some boots it worked, some it didn't). It was very annoying and I searched for a fix for days....

Well, all you have to do is follow this guide: [HDA-Intel Sound Howto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

Basically, you just recompile (manually) alsa and it's library... Sort of an update.

It fixed the problem for me, and I'm pretty sure it should work for you.

Good Luck!
(and let me know how it goes)

---

### Post by crabapple on 2007-06-09
I'm running a Macbook core2duo with Feisty.

I too get crackles in the left earphone usually but not invariably on boot.
I updated to the latest version of ALSA but the problem was still there.
Stopping esd, altering preferences in Multimedia Systems Selector -- all no help.
It goes away for the rest of the session if I restart ALSA with

sudo /etc/init.d/alsasound restart

and then reload the driver:

sudo modprobe snd_hda_intel

I didn't try this before updating ALSA so I don't know if restarting alsa and reloading the driver alone would have done the trick.

---

### Post by DucentiVigintiDuo on 2007-06-13
For the first command it says it can't find the command "/etc/init.d/alsasound".
I tried reversing it and putting restart first but it didn't find that command either.
Are you sure this is the write command to restart the ALSA mixer?

---

### Post by bsantos on 2007-06-13
> **DucentiVigintiDuo said:**
> For the first command it says it can't find the command "/etc/init.d/alsasound".
I tried reversing it and putting restart first but it didn't find that command either.
Are you sure this is the write command to restart the ALSA mixer?


The initscript is alsa-utils, you can do

sudo /etc/init.d/alsa-utils restart

or

sudo invoke-rc.d alsa-utils restart

---

### Post by crabapple on 2007-06-13
The alsasound script came from the updated alsa-driver package.
Restarting with alsa-utils restart doesn't solve the problem on my system.

I'll poke around to see if I can find out what

/etc/init.d/alsasound restart 
.
is doing that

/etc/init.d/alsa-utils restart

doesn't.

One thing that is immediately evident is that the alsasound script unloads the driver and then doesn't reload it.
(Why not?)

I can't just do 
sudo modprobe -r snd_hda_intel
because modprobe objects that the module is in use

Could it be the reloading of snd_hda_intel that's the key?

---

### Post by Ilove2023 on 2007-06-13
When I reload the snd_hda_intel module, the sound becomes good on mine. To reload it, you just have to close all "sound application", like pommed and the gnome-volume-manager in your gnome-panel and other things like that.

---

### Post by crabapple on 2007-06-13
I just checked this, snarfing the relevant parts of the alsasound script to shut down sound services, and then reloading snd_hda_intel; it's definitely reloading the driver that solves the problem for me.

Does reloading the driver solve the problem even if you haven't upgraded ALSA?

Why does reloading the driver make any difference?

---

### Post by crabapple on 2007-08-28
Honey, I killed the thread ...

FWIW if anybody is still reading this thread, you may like to know that adding

rmmod snd_hda_intel
modprobe snd_hda_intel

to /etc/rc.local

seems to fix the problem (by reloading the driver at boot).
I'm still not clear why this works; I also don't know if it would work without first updating ALSA.

---

### Post by cyberdork33 on 2007-08-28
> **crabapple said:**
> Honey, I killed the thread ...

FWIW if anybody is still reading this thread, you may like to know that adding

rmmod snd_hda_intel
modprobe snd_hda_intel

to /etc/rc.local

seems to fix the problem (by reloading the driver at boot).
I'm still not clear why this works; I also don't know if it would work without first updating ALSA.

Maybe it is currently loading prematurely, and needs another module loaded first? I know there was similar issues with applesmc and appletouch.

---

### Post by volanin on 2007-11-13
I don't know if it will work for you, but may also try this: (Read Post #9)
[http://ubuntuforums.org/showthread.php?t=611345](http://ubuntuforums.org/showthread.php?t=611345)
:)

---

### Post by inferno1005 on 2008-06-21
> **crabapple said:**
> Honey, I killed the thread ...

FWIW if anybody is still reading this thread, you may like to know that adding

rmmod snd_hda_intel
modprobe snd_hda_intel

to /etc/rc.local

seems to fix the problem (by reloading the driver at boot).
I'm still not clear why this works; I also don't know if it would work without first updating ALSA.

Thank you so much! This is the only thing that worked for me, and I have tried EVERYTHING else. Works after multiple boots :popcorn:

---

