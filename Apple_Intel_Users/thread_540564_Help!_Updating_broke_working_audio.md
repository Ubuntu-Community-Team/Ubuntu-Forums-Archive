---
title: "Help! Updating broke working audio"
date: 2007-09-01
forum: Apple Intel Users
---

### Post by phonky on 2007-09-01
Can somebody help please?

I didn't have an internet connection for some time (Intel Macbook Pro). So today, when reconnecting,the update manager obviously reported a lot of available updates. I did these.

Now sound stopped working!!! Must have something to do with the updates! It was a big update....(see attached last-update.txt file)

me@laptop: $ cat /proc/asound/cards
--- no soundcards --- 

dmesg output: see attached snd_problems.txt

It drives me crazy! I need audio cause I need to call home, as I am abroad.It used to work fine so far... I'm thinking of disabling notification of updates: never change a winning team (or never update a running system...)

I greatly appreciate any help on this.

---

### Post by towanda on 2007-09-02
I'm in the same boat.  Installed Feisty on a Gateway MX6448 with AMD Turion 64 processor and sound worked fine.  Ran an update a couple days ago and sound quit working.  Can't seem to get any of the ALSA commands to work, either.

---

### Post by phonky on 2007-09-02
Folks,

I don't know what caused the problem, which is in my opinion serious.
If an "automatic" update damages a running system this way, something is really bad.
At least there should be warnings on relevant system updates that some critical stuff is being changed.

In fact, also my previously working camera on my mac book pro is not working anymore. My beryl installation, which was running without a glitch, was broken as well. And I think the fan is running in a different way it did. I guess, **all the configurations I did to tweak my macbook pro are just gone!!!!** 

For the audio: I downloaded the latest alsa-driver from alsa-project.org, compiled and installed it. Audio works again.

For the camera: Need to follow again the procedure in the forum. Should work then again, I hope.

bye

---

### Post by joselin on 2007-09-02
Hi,

Same problem here, with sound and isight. 

The sound does not work since the upgrade to gutsy. Compiling the latest alsa drivers didn't help for me on my iMac 24".

About the isight seems that there is a problem in uvcvideo that will be solved. There is a bug filled on launchpad, but I can't locate it now.

Regards

---

