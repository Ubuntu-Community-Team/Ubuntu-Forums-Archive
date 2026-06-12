---
title: "Who can confirm the full potential of SATA being hot-swappable???"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by lentomies on 2007-10-01
Hello Ubuntu World!

I'm putting together a PC. I already have two 500 GB HDD. My intention is to mount each into a Mobile Rack. See [http://www.directron.com/kf812bk.html](http://www.directron.com/kf812bk.html) as an example.

On one HDD I will have XP. The other will have Ubuntu 7.04.

If SATA is hot-swappable meaning that devices can be added or removed while the computer is on depending, of course on OS features to detect new hardware after hot-swap, then at what stage during the XP and/or Ubuntu shut down can I manually TURN OFF (via rack key) the HDD of the O/S I'm shutting down and then TURN ON (via key) the HDD of the O/S I'm changing to?

I'm kinda under the impression that once it is confirmed that BIOS has taken over at start-up, during re-boot, I can then turn off one HDD and turn on the other? Is this right?

Or should I do an entire power shut down and then start up with the HDD I want ON with the appropriate O/S???

Thanks for any offered insight.

---

### Post by Scunizi on 2007-10-01
Why are you going to such pains to have 2 op systems  on your machine.  If you have both drives plugged in and operational with xp installed one and you then install Ubuntu on the other, Ubuntu will install GRUB which will allow you to choose the operating system of your choice when booting the system.  

As for turning the key off on the drive that's shutting down, you have to wait until it actually shuts down otherwise you risk loosing data on Ubuntu and screwing up you xp install.

---

### Post by lentomies on 2007-10-01
Actually that's exactly what I don't want! Both O/S's must operate independantly of each other for obvious reasons.

---

### Post by Scunizi on 2007-10-01
Ok.. I don't know what's so obvious about it, but there is another approach to do what you want.  Yank the xp HD, install Ubuntu on the other, put both into the system and choose which one to boot to via bios.  Otherwise, do the same thing and use your keys to turn one off before booting, making sure the two drives are one after the other in the bios so the system will "see" it and run.

---

### Post by lentomies on 2007-10-02
What do you mean:

"making sure the two drives are one after the other in the bios so the system will "see" it and run."???

Only one (1)  HDD with either Xp or Ubuntu will be running and TURNED ON. With that in mind, I'm lead to conclude that bios will always see that one drive, whether it has XP or Ubuntu on it as always being HDD "C:/". This is because the other HDD is turned off. 

I don't think the boot order needs to be played with at all. Am I wrong?

---

### Post by Scunizi on 2007-10-02
It really depends on your bios and may be nothing to worry about.  However, I've seen some bios's that once setup for 2 drives the boot order might be something like

cd/dvd
hd1
floppy
network card

After turning off HD1 and turning on HD2 the bios may not "automatically" switch the position of HD2 with HD1..  Experimentation will answer the question for you.  Either way .. you can have two seperate systems each on their own drive.

---

### Post by lentomies on 2007-10-02
But how would BIOS know, even detect for that matter, a HDD #2 if it is never even powered on at the same time as HDD#1?

---

### Post by Scunizi on 2007-10-03
The only thing left to do is try it your way and see what happens.. Bios's can be strange sometimes.

---

