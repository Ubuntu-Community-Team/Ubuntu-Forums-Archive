---
title: "Having sound issues with iMac 2013"
date: 2015-02-02
forum: Apple Hardware Users
---

### Post by Tu1J4kXk8NUhMz on 2015-02-02
Okay, so full disclosure: I'm asking about Linux Mint. However, it's my understanding that Mint is built on top of Ubuntu, so the answer should be transferable. Also, I've seen other folks have similar issues with Ubuntu (though their solutions didn't seem to help me). Additionally, I was an Ubuntu fella for quite some time, and I'm very comfortable with this community - and I know the Mac/Ubuntu knowledgeable folks here are quite good at what they do.

That out of the way, here's my question:

I recently installed Linux Mint 17.1 (Cinnamon) on my iMac 2013 27". It works great, but the one thing I'm having issues with is my sound.

I didn't notice at first because the system sounds are fine. However, music from VLC (.mp3) and sound tracks on YouTube and Spotify sound very quiet and kind of scratchy. I have no idea where the sound comes from on the iMac (the speakers are INVISABLE =-o), but it seems like the sound in Mint is coming from tiny speakers in the back of the unit.

I've read and tried some solutions to problems that sound vaguely like mine. I've added an entry to alsa-base.conf (options snd-hda-intel model=imac27), I've tried adjusting the front speakers in Alsamixer (there doesn't seem to be a slider for that)...I'm not sure where to look to fix the issue. I've not gotten far in fixing the problem with any of these researched solutions.

The headphone jack also doesn't seem to work, but that might be a completely different issue - one that I'm hoping will be resolved by fixing the poor sound quality.

I'm a bit familiar with Ubuntu (though it's been a while) and I'm pretty new to Linux Mint - if you need any logs or anything, please let me know how to fetch them. Thank you!

By the way, I thought it might be useful to know that many of the solutions I tried are from here: [https://help.ubuntu.com/community/Intel_iMac#Sound](https://help.ubuntu.com/community/Intel_iMac#Sound)

---

### Post by Tu1J4kXk8NUhMz on 2015-02-04
This has been bugging me so I decided to do some more research. It's starting to occur to me that maybe that's just how they sound, and maybe Mac OSX is doing some kind of black magic to make them seem better? I've come across the phrase "virtual surround sound" a few times, and Apple's specs about this model says "Stereo speakers" (though, they don't actually say where they are).

I actually chatted with an Apple support person, and they showed me the speakers and what they look like, and they are just stereo speakers. 
[https://www.ifixit.com/Guide/iMac+Intel+27-Inch+EMC+2639+Left+Speaker+Replacement/19649](https://www.ifixit.com/Guide/iMac+Intel+27-Inch+EMC+2639+Left+Speaker+Replacement/19649)
[https://www.ifixit.com/Guide/iMac+Intel+27-Inch+EMC+2639+Right+Speaker+Replacement/20251](https://www.ifixit.com/Guide/iMac+Intel+27-Inch+EMC+2639+Right+Speaker+Replacement/20251)

I think the issue must be an equalizer one, and I just don't have the settings worked out. I'll have to play with that. I'll close this topic out.

---

