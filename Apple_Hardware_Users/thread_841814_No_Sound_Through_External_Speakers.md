---
title: "No Sound Through External Speakers"
date: 2008-06-26
forum: Apple Hardware Users
---

### Post by infinitusagnitio on 2008-06-26
Hello all,

I have been having major problems with my sound.  I've been working on fixing it constantly since last week, and I still don't have it 100% working.  I'm running an Intel Macbook Pro Core Duo 2.0ghz with the snd hda intel card.  I was running everything off of Alsa and the PCM control as per the wiki, but that is not a correct solution.  Today I followed the guide for implementing pulse audio in hardy, and I'm currently using that.

I have already added options snd-hda-intel model=mbp3 to /etc/modprobe.d/options, and now the sound plays through the internal speakers.

As per now, here are the problems I am having:
-When headphones are plugged in, sound plays through both the headphones and the internal computer speakers.
-When the sound gets above 50%, it starts to crackle and I can hear some static (which pisses me off greatly because I'm an audiophile, and I have Shure e3c headphones) Also, I've never had this problem on my Mac side, even when volume is 100 percent it sounds perfect.
-When I plug my external speakers in through the headphone jack (Definitive 5.1 system :guitar:), the sound still only plays through the internal speakers.


If anyone has any ideas on any of these topics, I would greatly appreciate it.  Also, I'm running 8.04 currently.


If you need me to post any config files, just specify which ones and I'll upload them.



Thanks,
Bryan

---

