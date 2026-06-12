---
title: "Stopping apps from changing the refresh rate..."
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by some_random_noob on 2006-12-13
[http://www.ubuntuforums.org/showthread.php?t=292528&highlight=apps+changing+refresh+rate](http://www.ubuntuforums.org/showthread.php?t=292528&highlight=apps+changing+refresh+rate)
^ Other thread

"sudo dpkg-reconfigure xserver-xorg"
^ Command that confuses me.

That above command brings up a ton of stuff I don't understand. Could someone please guide me because this looks crazy :-k ...My graphics card is an "integrated intel extreme graphics2".

---

### Post by drphilngood on 2006-12-13
> **some_random_noob said:**
> [http://www.ubuntuforums.org/showthread.php?t=292528&highlight=apps+changing+refresh+rate](http://www.ubuntuforums.org/showthread.php?t=292528&highlight=apps+changing+refresh+rate)
^ Other thread

"sudo dpkg-reconfigure xserver-xorg"
^ Command that confuses me.

That above command brings up a ton of stuff I don't understand. Could someone please guide me because this looks crazy :-k ...My graphics card is an "integrated intel extreme graphics2".

See here:

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

and post back if you still need help.

---

### Post by some_random_noob on 2006-12-13
Errr... is that page what I'm meant to look at? I just want the refresh rate stuck on 60hertz and stop other programs from overriding it. Whats with all that video card stuff? The first few commands on that page go to what I've already seen too... misinterpretation? My refresh rate is fine, just when I open something like a game I've made does it screw up and go to 75hertz.

edit: this is also dapper drake btw.

---

### Post by drphilngood on 2006-12-13
> **some_random_noob said:**
> Errr... is that page what I'm meant to look at? I just want the refresh rate stuck on 60hertz and stop other programs from overriding it. Whats with all that video card stuff? The first few commands on that page go to what I've already seen too... misinterpretation? My refresh rate is fine, just when I open something like a game I've made does it screw up and go to 75hertz.

edit: this is also dapper drake btw.

I'm sorry; from your post, I thought that a program had reset your refresh rate and you didn´t now how to set it back.  I have no clue how to stop a program that you´ve allowed rights to change your refresh rate from doing so.

Good luck!

---

### Post by some_random_noob on 2006-12-13
Look at the link in my first post, some other guy tried it. The graphics card configuration part confuses me. Only one person other than me seems to have tried this so we're a little short on information :(

---

### Post by drphilngood on 2006-12-13
When it changes it, can you change it back by going to **System** -> **Preferences** -> **Screen Resolution**?

---

### Post by some_random_noob on 2006-12-13
With a full screen program I don't think so. My game does say to run at 60hertz but ubuntu overrides it :( Maybe I could edit that or xorg.conf, but doing that every time I open my game wouldn't be fun. I think I'm ready to give up on this, I don't use ubuntu for that much and I'm in no hurry to play my game, I'd rather have other people play it :D

However help is always appreciated and I'm having enough fun looking at my 1000 word tutorial on internet security that I've been writing today... and its only 2:35pm :cool: 

I doubt theres any harm done running at 75hertz for a limited time, this was mainly so I could beat the os and use the knowledge in the future, I'm not really disadvantaged right now from not being able to fix it.

- Cheers :D

---

