---
title: "Slow response time when using USB devices"
date: 2011-10-05
forum: Any Other OS
---

### Post by MonctonJohn on 2011-10-05
I thought this was just because of my old motherboard with bulging capacitors which I changed with a brand new board, but the behavior remains. I plugged in to USB external hard drives and copied my games from one to the other, but this behavior also happens if I plug in my camera to copy pictures and movies over.

Behavior: The system responds very slowly to mouse or keyboard. If I move my mouse it may take a second or two before the cursor moves. I've tried this with Graphics effects disabled with no help.

I'm using Mint 9 KDE version.

---

### Post by matt_symes on 2011-10-05
Hi

As an absolute minimum people here will need the specs for your system.

Are the keyboard and mouse USB devices ?
What type of devices are the hard drives ? Are they also USB devices ?
I assume the camera is also a USB device.
Are there any patterns you observe when you get this behaviour ?

My point is there could be a whole host of reasons for this behaviour, both hardware and software. Tracking something like this down on a forum may be very hard indeed.

Much more information is needed before an attempt at even guessing what the problem may be.

Do you still get the same behaviour from a liveCD ?

Kind regards

---

### Post by MonctonJohn on 2011-10-05
My apologies for the lack of info... I was hoping someone had experienced the same issue and could tell me what it was.

System:
[INDENT]Motherboard: Asus A8N-SLI SE[/INDENT]
[INDENT]CPU: AMD Athlon 64 X2 3800+[/INDENT]
[INDENT]Video: GeForce 6600 GT 256 MB[/INDENT]
[INDENT]Kbd and mouse are PS/2 hooked to a KVM[/INDENT]
[INDENT]Internal HDD is sata[/INDENT]
[INDENT]Memory: 2GB dual channel[/INDENT]

the external devices I was referring to were Hard drives and camera and I am usually copying to and from them. I can say that this behavior only occurs when I am trying to copy alot of information 2GB+

I have not tried a live CD but I will now that you mention it and post the results.

Thanks for your suggestions.

---

### Post by matt_symes on 2011-10-05
Hi

> I was hoping someone had experienced the same issue and could tell me what it was.

Unfortunately i have not.

However if we investigate then it's quite possible that someone will read this thread who has had this issue and will comment on it.

> Kbd and mouse are PS/2 hooked to a KVM

Do you still have the problem if they are hooked directly into the PC and not through the KVM ? I would definitely test that after the LiveCD test.

Kind regards

---

### Post by Perfect Storm on 2011-10-05
Moved to Other OS/Distro talk.

---

### Post by MonctonJohn on 2011-11-28
If anyone ends up searching and finding this thread I posted on stackexchange.com and one of the responses pointed out this:
[http://lwn.net/SubscriberLink/467328/c449ef7a003b272f]("http://lwn.net/SubscriberLink/467328/c449ef7a003b272f")
which is exactly the problem I was having.

---

