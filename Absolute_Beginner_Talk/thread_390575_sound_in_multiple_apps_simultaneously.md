---
title: "sound in multiple apps simultaneously"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by lerio on 2007-03-22
Hi,

I'm stuck with this problem: how do I make Edgy play sounds from different apps simultaneously?

I'm using an external USB audio card (e-Dio USB card)

I followed this guide ([http://www.laliluna.de/blog/2007/03/02/ubuntu_debian_linux_sound_problem.html](http://www.laliluna.de/blog/2007/03/02/ubuntu_debian_linux_sound_problem.html)) but didn't help me very much

PLEASE HELP

---

### Post by Gannin on 2007-03-22
Are all the apps using ALSA for their sound output?

---

### Post by lerio on 2007-03-22
well, I think I tried everything. I've tried setting everything to OSS, ESD, ALSA, Auotdetect with no luck: the first app just takes control of the sound channel

---

### Post by lerio on 2007-03-22
anyway, if you (or anybody else) kindly posted a list of steps to check if everything is set correctly, I'll try it as soon as I get back home from work.

Thanks a lot

---

### Post by Gannin on 2007-03-22
Can you give some examples of the programs you're trying to get to work?

---

### Post by garbage792 on 2007-04-29
> **lerio said:**
> well, I think I tried everything. I've tried setting everything to OSS, ESD, ALSA, Auotdetect with no luck: the first app just takes control of the sound channel

Greetings,

I have the same problem and I too have an external sound card. I have tried various tutorials and despite the claims, ALSA just does not work. I have gone back to xp after giving up.

If you ever get to fix the problem, please do post back. 

Cheers.

---

### Post by LuisGMarine on 2007-04-29
I'm also experiencing the same problem, although I don't know if I should start a new thread because I don't want to hijack this one.

Pretty much I've followed most tutorials on here to get software mixing working, but nothing seems to work.  By examples lets say I'm playing a video on YouTube, and at that same time I want to play a song, I launch lets say banshee to play that song and hit the play button but no sound comes out.  Seems like only one app can control the sound card.  As soon as I shutdown the YouTube video I get sound from banshee, and vice versa.

In a nutshell you can only hear one sound at a time, you can't have multiple applications running different sounds at the first time, usually the first one is the one that has the control of the sound, and just cuts all the others off.

I just have standard onboard sound, if that makes any difference.

-LuisGMarine

---

### Post by garbage792 on 2007-04-30
> **LuisGMarine said:**
> I'm also experiencing the same problem, although I don't know if I should start a new thread because I don't want to hijack this one.

Pretty much I've followed most tutorials on here to get software mixing working, but nothing seems to work.  By examples lets say I'm playing a video on YouTube, and at that same time I want to play a song, I launch lets say banshee to play that song and hit the play button but no sound comes out.  Seems like only one app can control the sound card.  As soon as I shutdown the YouTube video I get sound from banshee, and vice versa.

In a nutshell you can only hear one sound at a time, you can't have multiple applications running different sounds at the first time, usually the first one is the one that has the control of the sound, and just cuts all the others off.

I just have standard onboard sound, if that makes any difference.

-LuisGMarine

I have exactly the same problem. I have configured alsa as the basic sound system and also have "aoss" setup in my firefox and am using alsa in all the video/audio players.
I have the latest version of alsa BTW.

I tried creating another thread but apparently no one answered. Guess no one really knows whats wrong. I am glad that I am no the only one though.

What amazes me is that a decade old system like windows 98 does this without a hiccup.On the other hand, in Ubuntu you have to go through hoops to enable this feature which should have just been there by default in the first place. And no its not the drivers problem because I get perfect sound otherwise, except that multiple devices cannot mix sounds.

If the ever "incompetent" Microsoft can do it painlessly that why can't it be done in Ubuntu? Why is it so hard and frustrating?

I demand a better unified sound solution for gnome!! :(

---

### Post by SergeiFranco on 2007-05-01
I was wandering why Ubuntu cannot do software mixing by default (or maybe at all)?
it is much of a hassle to launch programs with oss option enable to be able have 2 sounds at a time.
If there is a way to enable system wide software/hardware mix, some one please post a HOW-TO.
I am currently struggling to make the bloody thing work. Actually when I have amarok playing some of the apps (like Kaffeine for example) fail to launch at all.
This is really annoying.
And what is the point of application named *mix (alsamixer, kmix etc.) if it does not mix at all...
Oh btw, I did search on that issue and it seems to me than a lot of people have this issue, and no-one found a proper solution 
who cares about Beryl or other interface fancy, if simple thing like that does not work.

---

### Post by SergeiFranco on 2007-05-01
Right, I am sorry about rant.
I have fixed issue (somewhat).
I just had to add to .asoundrc file a few lines from this site:
[http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php?module=usb-audio](http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php?module=usb-audio)
BTW I have USB Extigy sound card. Remote control and buttons and knobs still not work on it.

---

### Post by 3rdalbum on 2007-05-01
Ah-ha.

If it's happening between programs that use ALSA, then it's got to be a drivers issue.

As for the complaint that "Windows 98 mixes sounds perfectly", then that's actually not true. Just as Linux has some programs that use OSS and grab control of the sound card, so does Windows. The difference is, you can often tell Linux systems to redirect the OSS sound through ALSA; whereas you can't do anything similar on Windows.

Try playing the game Elastomania on Windows while playing an MP3; it can't be done. However, play the same game on Linux through Wine and you can enjoy your choons at the same time.

---

### Post by garbage792 on 2007-05-01
> **3rdalbum said:**
> Ah-ha.

If it's happening between programs that use ALSA, then it's got to be a drivers issue.

As for the complaint that "Windows 98 mixes sounds perfectly", then that's actually not true. Just as Linux has some programs that use OSS and grab control of the sound card, so does Windows. The difference is, you can often tell Linux systems to redirect the OSS sound through ALSA; whereas you can't do anything similar on Windows.

Try playing the game Elastomania on Windows while playing an MP3; it can't be done. However, play the same game on Linux through Wine and you can enjoy your choons at the same time.

How can it be the drives issue? :confused: 
The soundcard either supports hardwire mixing or it does not. If my sound card does not support hardware mixing than alsa should do the software mixing. Where do drivers come into play?

Is there someway that I could debug and go to the bottom of this? How can I tell whether software mixing is being used or not? Are their any log files?

I really cannot comment about Elastomania. I have personally never run into any programs in windows that take over the sound card. I swear. I am not arguing that there aren't any such programs  but they are probably very rare unlike linux where every multimedia application takes over ](*,) 

Leaving windows aside I need to fix it desperately. Its so irritating that I am using windows and I am having Ubuntu withdrawal. Please help :*(

---

### Post by LuisGMarine on 2007-05-03
I will look into it when I get home from work.  This is one of those minor issues, but when you discover that its there its quite annoying.  I have found HOW-TO's for every problem that I have encountered on Linux, and yet this one is just about the only one where I can't find anything about it.

-LuisGmarine

---

