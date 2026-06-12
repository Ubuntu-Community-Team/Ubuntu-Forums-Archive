---
title: "I can't get any audio to work with audio editors..."
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by discmaster on 2007-06-05
I have tried goldwave/audacity/GNUSound, even sound recorder, & I simply can't get any audio to record or playback. I am guessing it must be a driver issue, but I have tried every setting imaginable.

...device cannot be found/no supported plugin, etc...several errors along those lines...


OSS/Alsa/device settings & different settings in the editors as well. I am at my wits end here, & seriously considering just going back to windows where everything pretty much works. 

Can anyone give me some assistance here & give me a reason to stay with ubuntu?!? :(

---

### Post by Daishiman on 2007-06-05
Specify the sound card that you're using. Have you checked to see if the microphone input is enabled? Have you checked if any of these applications use JACK?

---

### Post by Crafty Kisses on 2007-06-05
> **discmaster said:**
> I have tried goldwave/audacity/GNUSound, even sound recorder, & I simply can't get any audio to record or playback. I am guessing it must be a driver issue, but I have tried every setting imaginable.

...device cannot be found/no supported plugin, etc...several errors along those lines...


OSS/Alsa/device settings & different settings in the editors as well. I am at my wits end here, & seriously considering just going back to windows where everything pretty much works. 

Can anyone give me some assistance here & give me a reason to stay with ubuntu?!? :(

It seems like your frustrated, I was too when I first started. :p
First you try installing your codecs that possibly could work. What are your system specs?

---

### Post by frolle on 2007-06-05
Click twice on your volume control -> Switches and see if jack is enabled or not. That was how i fixed mine..

---

### Post by discmaster on 2007-06-05
> It seems like your frustrated, I was too when I first started.ya' think?!? :lolflag:

> First you try installing your codecs that possibly could work. What are your system specs?
Codecs; such as lame mp3? I am not sure I understand completely...

system;
A8V-VN SE mainboard
onboard sound - Realtek  ALC660 6 ch. (in the mobo manual)

double click on the vol. icon, I have; 
ALC861 (OSS Mixer)
or
HDA VIA VT82xx (ALSA Mixer)

---

### Post by bpdsmyth on 2007-06-06
Sound recording worked fine in Edgy but is broken in Feisty.  I have tried every suggestion in this forum with no luck.  Neither Sound Recorder or Audacity will let me record.  When I plug into the line-in and or microphone jack and set the volume control to the appropriate recording device I can hear the music I just can't record it. Switching between ALSA and OSS doesn't help.

Extremely Frustrated,

Brian

---

### Post by discmaster on 2007-06-06
>  	Sound recording worked fine in Edgy but is broken in Feisty. I have tried every suggestion in this forum with no luck. Neither Sound Recorder or Audacity will let me record. When I plug into the line-in and or microphone jack and set the volume control to the appropriate recording device I can hear the music I just can't record it. Switching between ALSA and OSS doesn't help.

Extremely Frustrated,

Brian I can't speak for edgy, but I know it isn't working here, & there seems to be no solutions; doesn't anyone else use their pc's for audio recording?

---

### Post by discmaster on 2007-06-12
Any more suggestions on this? I need to do streaming audio recording/edition, & I cannot get any audio editor to pick up the audio from the sound card/mixer.

What can I do to solve this? :confused:

---

### Post by discmaster on 2007-06-20
I am still trying...](*,)

Anyone have any other ideas??? I cannot get any audio editor/recorder to pick up the sound from my sound card... :(
I want to record streaming audio - I can listen to the stream, but no recording will take place...

---

### Post by skipkent on 2007-07-09
Interestingly I'm in a similar boat, only I find that I can record with Ardour just fine, but Audacity and many other jack and non-jack audio devices fail to play.

Is there a way to 'jack-enable' everything?  I'm just using the built-in soundcard which for me is fine.  I have an Alesis mixer going into that and the sound is superb.  I'll be re-installing with Ubuntu Studio soon, which I'm sure will fix things, but I'd like to know what's going on as well.

Could it be that we need to update some of these apps after moving to feisty?

That aspect of Ubuntu sort of confuses me as my Synaptic still seems to be stuck in '6.04' mode or whatever it was that I originally installed, and I see only older versions of programs.  I finally put in the UStudio repository, which let me get Ardour 2.0 instead of .99 which is great, but I'm wondering how others deal with Synaptic.  Where do people learn of what repositories to connect to for new software?

frolle - could you attach a screenshot of the jack switch you're talking about?  I've looked at my volume control but I don't think I've ever seen that.  jack apps always seem to be separate.

Thanks,

-skent

---

### Post by skipkent on 2007-07-09
Somone mentioned this in another thread and I think they might be on (to) something:

      sudo chmod 666 /dev/snd/*

It could be that the upgrade changed the ownership of all/some audio devices so that only root can use them.  This might be worth a try before pulling out any more fistfulls of hair, or re-installing or whatever.  ; )  I'm not home now so I can't try this for a while...

---

### Post by Logical Dream on 2007-07-09
In this moment I'm trying to install gstream for audio, but He needs the installation disk in some point. I install 7.04 at with my frend and now I dont have disk and I need 3-4 hours to download installation. Is there any option to disable that disc source?

---

### Post by Logical Dream on 2007-07-09
OK I found It :) 
So maybe somebody will just need it.  

System->Administration->Synaptic Package Manager->Settings->Repositories-> on bottom you will see Installable from CD/DVD ->just unmark it  and It will work without CD.

I already like this OS , awsome ;)

---

### Post by discmaster on 2007-08-27
Well, I've tried just about everything at this point; An experienced user had me recompile the kernel in hopes that it would work, but it still doesn't. (The streaming audio recording). The answer always seems to be that my hardware is not compatible with linux...Don't know what else to do, other than wait for the next release in October & hope that it works then... ](*,)

---

### Post by donespo on 2007-08-27
I started having this problem yesterday.  Haven't figured out how to fix it yet but I thought that my input might lead to some ideas from more experienced users than I.

I loaded Audacity on a new install of Feisty about a week ago and everything worked great.  I could record with no worries and play back everything except MP3 (a codec issue I hadn't yet gotten around to as yet).  Then I installed Compiz-Fusion on Saturday, just to see what all the fuss was about.  It's cool but certainly not essential.  

Anyway, I went to record something yesterday and discovered that the playback didn't work anymore.  It looks like Compiz changed something in my sound card setup but I have no clue what it could be.  I removed Compiz but it didn't restore the settings.  I'm going to try removing Audacity tonight and reinstalling it to see what happens.  

BTW, I installed Gnusound last night before I removed Compiz and it also couldn't playback but after removing Compiz and rebooting it worked fine.

---

### Post by donespo on 2007-08-28
[I]Somone mentioned this in another thread and I think they might be on (to) something:

sudo chmod 666 /dev/snd/*

It could be that the upgrade changed the ownership of all/some audio devices so that only root can use them. This might be worth a try before pulling out any more fistfulls of hair, or re-installing or whatever. ; ) I'm not home now so I can't try this for a while...

skipkent
[/I]


Thanks.  This solved my problem.  

Before doing chmod Audacity only showed one option under Edit/Preferences/Playback device.  After chmod it shows 4 options.  Selected OSS: /dev/dsp and life is good.

Thanks for sharing.

---

### Post by discmaster on 2007-09-06
> Before doing chmod Audacity only showed one option under Edit/Preferences/Playback device. After chmod it shows 4 options. Selected OSS: /dev/dsp and life is good. Unfortunately that doesn't solve my issue :(

I have all those listed too, & no matter which one I select, the end result is the same - no recording...

---

