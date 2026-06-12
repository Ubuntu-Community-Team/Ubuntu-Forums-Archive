---
title: "Headphones do not mute Speakers"
date: 2011-10-17
forum: Asus Ubuntu Support (CLOSED)
---

### Post by kharaku on 2011-10-17
Hi, I have an ASUS P150IJ.

When I use my head phones they do not mute the external speakers (kind of defeating the point of headphones...)

Is there anyway to force them to do so?  I have played with various settings in Audio preferences to little avail.

Thanks!

---

### Post by Shazbot89 on 2011-10-18
I have the same issue on an K60IJ, from what I understand it's one of those "and it will still be like that" issues.

However, PulseAudio crashed at some point and when the headphones were plugged in they played while the speakers were muted. Not sure how that works. One of those "The car is broken because there is a car". Not sure what the relationship between the PulseAudio server and the raw output was though, not even sure how that would work :[.

---

### Post by kharaku on 2011-10-19
> **Shazbot89 said:**
> I have the same issue on an K60IJ, from what I understand it's one of those "and it will still be like that" issues.

However, PulseAudio crashed at some point and when the headphones were plugged in they played while the speakers were muted. Not sure how that works. One of those "The car is broken because there is a car". Not sure what the relationship between the PulseAudio server and the raw output was though, not even sure how that would work :[.

I just don't understand with all the 'Linux does everything Windows does better' folks why Windows (XP even not 7) mutes the audio fine, and Linux completely drops the ball.

It's not like ASUS uses rare parts...

---

### Post by rightanglecse78 on 2011-10-20
I have ASUS k40ie .
I have the same problem that the guys discussed. Whats the problem...??

---

### Post by kharaku on 2011-10-23
> **rightanglecse78 said:**
> I have ASUS k40ie .
I have the same problem that the guys discussed. Whats the problem...??
Was hoping upgrading on Ocelot would help but I can't do that because it keeps saying some index files didn't download (incidentally no there is not a network problem, all networking features seem to work fine)

---

### Post by ryurage on 2012-03-27
I'm somehow guessing that for all of us with this generation of Asus laptops, there ain't no fix coming for this hardware-specific problem anytime soon.  But who to blame?  So irritating...

---

### Post by mörgæs on 2012-03-27
Have you tried 12.04 to see if the problem is fixed or are you just guessing?

---

### Post by ojcme on 2012-03-29
I have an Asus UL20 and I don't know if this will fix it for you, but it did for me.

I had to add a line to the end of my alsa-base.conf and it worked for me.

So you would sudo gedit /etc/modprobe.d/alsa-base.conf
At the end I added options snd-hda-intel model=auto and then saved it.

Headphone output now works properly to me. Hopefully it works for you guys.

---

### Post by mörgæs on 2012-03-29
Thanks!

---

### Post by ojcme on 2012-03-30
Fixed your problem?
I dunno why but I've bought 2 asus laptops in the last 4 years and both of them needed to have this line added to make it work.

---

