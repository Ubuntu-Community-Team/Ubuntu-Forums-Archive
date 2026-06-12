---
title: "Again, sound problems. Please help."
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Dysan on 2007-05-21
I've noticed something with the sound. When the little speaker icon in the top-right is "x"ed, the sound works, but when it's not "x"ed, my sound doesn't work. That's exactly what happened last time which lead me to ruining my GUI while trying to fix it. I, of course, reformatted with Ubuntu again.

Just to cut to the point, what the hell? How do I fix it?

---

### Post by encompass on 2007-05-22
Ok tell us about your computer first... exspecially your sound card... what model and brand is it?  Do you know?

---

### Post by Dysan on 2007-05-22
> **encompass said:**
> Ok tell us about your computer first... exspecially your sound card... what model and brand is it?  Do you know?

My computer is a Gateway 835GM with 1024MB RAM, an Radeon X1900 GT graphics card, and a Creative Sound Blaster Audigy SE sound card. The video and sound cards aren't installed, so I don't know if those are the problems. I've been running off the software stuff thus far.

I just started up my computer today and the sound wasn't working.

---

### Post by johnny4north on 2007-05-22
i believe that your motherboard has a sound card that is conflicting with your Audigy soundcard.  you may need to disable the on board soundcard in the bios.  do be careful, might be best to have a friend or one of the forum guys help you with a walk though.

---

### Post by Dysan on 2007-05-22
I don't know anyone here that can help me. That aside, how was my sound able to work for a week if there was a confliction? I didn't mess with any sound options, so it should still work.

---

### Post by STREETURCHINE on 2007-05-22
just out of interest what version of ubuntu are you using.
i have edgy 6.10 and it fails to load the sound every other boot,bit of a piss off but there seems to be no fix for it yet.
i have fiesty installed but havnt tried it yet,hope it works with my sound better.
pain in the butt having to switch to windows when i want to listen to some music or watch a vidio

---

### Post by Dysan on 2007-05-22
Feisty Fawn. This is the second time it's done it.

---

### Post by STREETURCHINE on 2007-05-22
hmmm  maybe they have not fixed that bug yet.wont know till i start using feisty fawn.

thanks

---

### Post by Dysan on 2007-05-22
Well, I don't want to have to reinstall Ubuntu *again*. Can anyone help me?

---

### Post by dbott67 on 2007-05-22
After upgrading through Edgy & Feisty, I noticed that I was having some weird sound problems:

1. At the GDM login screen I would hear the "drum roll" sound.
2. After logging in, I would not hear the **startup.wav** file, although I could hear it if I played it in "Beep" or other music program.
3. In **SYSTEM > PREFERENCES > SOUND > SOUND tab**, the sounds would **not** play.
4. In **SYSTEM > PREFERENCES > SOUND > DEVICES tab**, the **TEST SOUND** worked.
5. Most applications with sound worked (Beep, Totem, Flash video, etc.)
6. No sound in the games "Cube" or "Sauerbraten".
7. All applications worked previously.

After fiddling with the sound settings trying various suggestions in the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") thread, I totally buggered up my sound.  Oh well, a fresh install of Feisty never hurt anyone and I had my **/home** directory on a separate partition.

After the new install, I still had the 6 symptoms described above.

Thinking that it might be some sort of **.config** file remnant, I created a new user and everythng worked properly. A-HA! Comparing the user home directories, I noticed the presence of a **.asoundrc** file and another similarly named file.  After doing some research here about [what the file is for]("http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php") (and it's safe removal), I deleted it, logged out and returned to a system with full working sound.

My suggestion is this:

1. Create a new user account
2. Login using new user account
3. Check to see if sound works properly
4. If it does, then the issue is likely some sort of config file.  Look for the .asoundrc file in your original home directory and move it to a backup folder (just in case)
5. Log back in as your original user and test.
6. If it fails to cure the problem, try the Comprehensive Guide above.

-Dave

---

### Post by Dysan on 2007-05-25
I've tried what that guide suggests, but it doesn't help. " aplay -l" shows my sound card, but I just can't get it to work. I don't get sound in a different account either.

---

