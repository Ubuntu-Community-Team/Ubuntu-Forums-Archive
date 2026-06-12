---
title: "hard disk ticking sound?"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2007-02-12
My hard disk makes very very faint but steady and rhythmic ticking sounds, about once a minute or so. Anyone else experience this? (Even when idle)

---

### Post by an.echte.trilingue on 2007-02-12
I have an Asus A6, too, and it does the same thing.  I have no idea what causes it, but I don't think that it is abnormal.

Take care,
-mat

---

### Post by kpatz on 2007-02-12
Most likely it's thermal recalibration.  Basically the drive adjusting its heads to compensate for temperature drift.  This is normal on many drives.

Either that or there's a once-per-minute task running that writes to the drive.   Maybe a filesystem sync or something.  Does the HDD light flash when you hear the tick?

---

### Post by PartisanEntity on 2007-02-12
No lights when the ticking occurs. It didnt do this under windows. *This* ticking sound is much much quieter than the ticking sound you would hear during read/write. It doesnt seem to affect the stability or use in anyway, just thought it a bit weird.

---

### Post by phenest on 2007-08-10
I have the exact same ticking sound. I have a Dell Precision M90. The hard drive is a Seagate Momentus 7200rpm ST9160823AS. This laptop is brand new and I've never run Windows on it (for obvious reasons) to know whether it happens in Windows or not. There is no activity when the ticking occurs. Is it normal? Will it damage the drive?

---

### Post by Rocket2DMn on 2007-08-10
I've never noticed this problem on my laptop hard drive, but I've never been listening for it.  I'm always skeptical of hard drives that make unexplained noises, so as usual, I would suggest keeping good backups.  However, since it seems that you are all experiencing it, I wouldn't worry.  If it starts making scratching, loud clicking, or whining noises, that should throw up some red flags for sure.

---

### Post by SeanTater on 2007-08-10
Not that I'm any expert, but I would try to mount the drive with noatime.
If that has no effect, then maybe it's DMA?

---

### Post by logos34 on 2007-08-10
same here.  every 2-3 secs, light flashes on hard drive.  What is accessing the drive?  I've changed lm-sensors to 10 sec inverval, so that's not it.  Didn't do this in edgy or dapper.

---

### Post by asmoore82 on 2007-08-10
sounds like dying drives to me.

back up important data somewheres else.

---

### Post by logos34 on 2007-08-10
> **asmoore82 said:**
> sounds like dying drives to me.

back up important data somewheres else.

 It's a relatively new disk and I've run smartctl on it --it checks out perfectly.

---

### Post by floke on 2007-08-10
I wouldn't call in the priest yet. My drive occasionally starts making huge 'ker-klunk'-ing noises, that sound like its trying to break free. About nine months ago I thought it was going to crap out on me - but its still going strong!

---

### Post by kavon89 on 2007-08-10
My iBook does this all the time. It makes a very faint "scratching" noise when it idles every once and a while. I take it as a sign that it is still alive. Sometimes it makes a louder sound, meaning it actually did some loading.

I unfortunatly don't have a hard drive or even status light, so I can't tell ya if it flashes too, but I can tell the diffrence in the sounds. What brand and model do you have? It could be a bad laptop/quality and it is dying sooner than it should have. I know my Sony would restart itself if i moved it too quickly, and it had overheating problems.

(I'm on OS X, not Ubuntu. So it shouldn't be just an Ubuntu thing.)

---

### Post by phenest on 2007-08-10
My hard drive is brand new (so is the laptop it's in). I've heard this sound before in previous laptops running Windows.

I'm going to ignore it.

And on the subject of hard drive sounds: did anyone here know that if you remove a laptop hard drive and shake it a bit, it rattles. Perfectly normal. If it doesn't rattle, then there's something wrong.

---

### Post by mustafaahmedhussien on 2008-03-23
I have the same problem here. I just bought my laptop. Also the ticking stops when I am running windows. It only exists when I am running ubuntu

---

### Post by ghost_ryder35 on 2008-03-23
> **phenest said:**
> My hard drive is brand new (so is the laptop it's in). I've heard this sound before in previous laptops running Windows.

I'm going to ignore it.

**And on the subject of hard drive sounds: did anyone here know that if you remove a laptop hard drive and shake it a bit, it rattles. Perfectly normal. If it doesn't rattle, then there's something wrong.**
Depends on how loud the rattle is ;)  If its like KLUNK KLUNK you got a problem :guitar:

---

### Post by oettinger on 2008-03-23
I thunk WD drives come with the "THUNK_THUNK" from the factory... it is also a sign of them dying, and you need wd diags to give an error 04 for them to give you an RMA# for it (Hint Hint) otherwise they will tell you it is normal:lolflag:

---

### Post by Igniteflow on 2008-03-26
you might want to take a look at this [http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear](http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear)

---

### Post by waspbr on 2008-03-26
this too [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14")

---

### Post by wieman01 on 2008-03-26
Possible solution is posted here:

[http://ubuntuforums.org/showthread.php?t=531866]("http://ubuntuforums.org/showthread.php?t=531866")

---

