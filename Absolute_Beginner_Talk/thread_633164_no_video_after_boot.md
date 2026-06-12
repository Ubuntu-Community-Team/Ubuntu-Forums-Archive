---
title: "no video after boot"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by md11driver on 2007-12-06
i've tried searching for this but may not know how to search properly.  please pardon me in advance if i'm boring everyone.

i have an old sony pcg-sr33 600mh, 256 mg.  the same video problem occurs with 7.04 and 7.10.

last night i thought i had the problem whipped.  after installing 7.10, after initial boot, the screen stopped at a blank screen, no information whatsoever.   i thought i was overwhelming my system possibly, so i installed 7.04 as a dual boot.  i booted to 7.04 and had normal video.  i thought, "hmmm", and tried to boot to 7.10.  normal video!!!  i updated the system, turned it off, and went to bed.

this morning i have no video after boot in either 7.04 or 7.10.  the recovery screen boots fine and i can get to a command prompt.  i have no idea what to enter to change video settings.

i'm assuming video driver problems, but why normal video once?  ubuntu worked wonderfully when i could see it.

please help!

---

### Post by Partyboi2 on 2007-12-06
To reconfigure 
```
sudo dpkg-reconfigure xserver-xorg
```
What video card are you using?

---

### Post by md11driver on 2007-12-06
thank you partyboi2.

i went through the reconfig.  the card is an S3 86c270-294 savage/ IX-MV.  when the machine boots i can see just a flicker after the splash screen then nothing.

---

### Post by md11driver on 2007-12-06
bump

---

