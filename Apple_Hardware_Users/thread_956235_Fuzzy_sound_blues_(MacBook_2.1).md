---
title: "Fuzzy sound blues (MacBook 2.1)"
date: 2008-10-23
forum: Apple Hardware Users
---

### Post by ninjaaron on 2008-10-23
Hey. I'm a relatively new ubuntu user (two weeks), and I am experiencing what is apparently a common problem: static in my sound. It is particularly noticeable from the headphone jack, but also when 'surround' is mixed into the speaker output. (I am using a MacbBook 2.1, so I have to use the 'surround' trick).

I've gone through the FAQ's and done all the things they said to do. These things did not help.

I know something about sound because I am a musician. The kind of static I'm hearing is digital distortion that comes from pushing the front-end of a digital pre-amp. I guess this means that the driver is giving too much juice to the sound card when 'surround' is engaged.

Unfortunately, I don't know enough about Linux, or programming, or hardware, or whatever I need to know to fix it. Nonetheless, the static is driving me crazy.

---

### Post by bsantos on 2008-10-28
> **ninjaaron said:**
> Hey. I'm a relatively new ubuntu user (two weeks), and I am experiencing what is apparently a common problem: static in my sound. It is particularly noticeable from the headphone jack, but also when 'surround' is mixed into the speaker output. (I am using a MacbBook 2.1, so I have to use the 'surround' trick).

I've gone through the FAQ's and done all the things they said to do. These things did not help.

I know something about sound because I am a musician. The kind of static I'm hearing is digital distortion that comes from pushing the front-end of a digital pre-amp. I guess this means that the driver is giving too much juice to the sound card when 'surround' is engaged.

Unfortunately, I don't know enough about Linux, or programming, or hardware, or whatever I need to know to fix it. Nonetheless, the static is driving me crazy.

Is it coming from the left channel? I read somewhere that there was a fix on the development kernel, but no patch was pulled to fix this on the current Intrepid kernel (assuming you're using the beta).

I get it to stop the static by suspending and resuming. It's the only thing missing for Intrepid being perfect on this machine, even wireless (ath9k) has been working well (apart from the weaker signal than I got with madwifi).

---

### Post by Bakon Jarser on 2008-10-28
Double click on the volume control in the upper right corner and make sure pcm is not at 100%.  Since I have turned that down I haven't gotten any distortion.  If that doesn't help maybe you can find your answer here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

