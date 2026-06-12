---
title: "Laptop High Pitch Screen Whine"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by Elitegunslinger on 2007-11-27
Just another quick question.

I got a C712NR Compaq laptop, the one from black Friday.  I am not sure why but when the screens brightness changes there is a high pitched squeal for about 5 seconds.  It isn't super noticeable or loud I just would like to make sure the laptop isn't broken or in need of repair.

---

### Post by toupeiro on 2007-11-27
interesting..  

Normally, this is something you'd expect with a CRT (screen monitor).  As your CRT changes brightness and/or resolution, your flyback will readjust itself, and sometimes cause the noise you're talking about, but I would not expect this on a laptop...  Just to confirm, you are not using an external screen?  Make sure all your refresh rates, sync rates and whatnot are in range for your laptop.  If you are throwing a vertical/horizantal sync range out of your hardwares scope, this can cause some abnormal behavior.  Best thing to do is to google your laptop's model number followed by 'xorg.conf' and see what you come back with.  Then compare the video settings you find with the video settings specified in your /etc/X11/xorg.conf file.

I would also pull up alsa-mixer just to insure you don't have a SFX level up very high and the change is, for some unexplicable reason, affecting the sound. (a.k.a. this is more of a long shot, but I've seen weirder things.)

---

### Post by Elitegunslinger on 2007-11-27
Just a note, it doesn't make the noise with bios up.  Checking xorg now.

---

### Post by Elitegunslinger on 2007-11-27
wow.... the pcm was all the way up causing the noise.

---

### Post by Elitegunslinger on 2007-12-11
Actually I lied, tried changing refresh rates.  Didn't help.  Anyone know how to change the horizontal and vertical syncs?

I also emailed hp to see if it is possible that my LCD inverter is faulty.

---

