---
title: "display goes wonkey, need help"
date: 2005-10-25
forum: Absolute Beginner Talk
---

### Post by kevin_thome on 2005-10-25
I just installed ubuntu breezy, and I've been having issues with the display. 

A picture is worth a million words...

[IMG]http://members.shaw.ca/kevin_thome/screen.jpg[/IMG]

Up untill this kicks in, everything works fine. I'm stumpped as to what to do about this.

Please help!

 Pentium 4 3.2ghz 800mhz fsb
Asus P5AD2 Motherboard with I925x chipset
1 GB of ddrII ram
80GB maxtor sata drive
30GB maxtor ide drive
Asus N6600GT Video Card
M-Audio Delta 1010 Sound Card
Antec 550 PSU
Plextor PX-716a DVD RW

---

### Post by GrootBrak on 2005-10-25
I had a similair problem, it was my refresh synch rates that skewed things. I doubt if this is your problem cause the background looks okay. My screen looked like it was repeating itself horizontally about 50 times, but that was long ago, I have other issues now with Breezy!!!

---

### Post by kevin_thome on 2005-10-25
yeah this one is number one on the to figure out list, as when it happens there's nothing to do but reboot, which is not always easy due to not being able to really see what's going on.

---

### Post by Mustard on 2005-10-25
Have you tried reconfiguring your settings using...

```
sudo dpkg-reconfigure xserver-xorg
```

?

-edit-

I'll throw this link in, just in case it has something in it that you might find helpful.

[Fix Video Resolution HOW TO]("https://wiki.ubuntu.com//FixVideoResolutionHowto")

---

