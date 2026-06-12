---
title: "Multiple applications using ALSA"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by ocho on 2007-04-15
I realize this has probably been brought up a multitude of times, but after doing some searching of google and these forums, I have come up empty handed. 

I am trying to fix my ALSA setup so I can hear sound from multiple applications, specifically Counter-Strike and Rythmbox. I've tried using aoss as one of the wiki's I read suggested, but it did not work.

My sound card, according to sysinfo, is Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02).

Could anyone point me in the right direction? Thanks.

---

### Post by Seisen on 2007-04-15
Have you tried this 

[http://ubuntuforums.org/showthread.php?t=101125]("http://ubuntuforums.org/showthread.php?t=101125")

---

### Post by click4851 on 2007-04-15
this is one of those "problems " that I think doesn't get enough attention by the devs. I really wish this would "just work". I can't be the only other person who has had to fiddle with my audio settings.

---

### Post by ocho on 2007-04-15
Nope, I tried using both the ALSA setup and the ESD setup. Now I can't hear system sounds...even after changing my configuration back to ESD.  

Any suggestions?

EDIT: Okay, I now have system sounds working using ESD and I have multiple applications playing sound, the two I tested were Rythmbox and Gaim. My problem now is that Counter-Strike does not have sound when Rythmbox is open. I think this may be because Crossover is not defaulting to ESD but rather to ALSA. I'll see if I can figure out how to make it use ESD.

SECOND EDIT: Well, I successfully forced Crossover to use ESD by merely changing the "Sound Driver Load Order." Now I'm having a worse problem...rather than no sound in Counter-Strike the sound loops and the game lags horribly because of it. Maybe I need to set up ALSA for more than one sound...ESD doesn't seem to work so well.

---

