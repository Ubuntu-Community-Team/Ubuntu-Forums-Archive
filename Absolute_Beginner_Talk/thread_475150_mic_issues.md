---
title: "mic issues"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by shawndw on 2007-06-15
Hi i'm new to linux well not exactually new but i wouldn't count on me doing much technical on it here's my problem my mic doesn't work i'm useing an acer aspire with dual core athlon running ubuntu fiesty not sure if this is helpful but

```

shawn@shawn-ubuntu:~$ sudo tail -2 /proc/asound/oss/sndstat
Password:
Mixers:
0: Realtek ALC888
shawn@shawn-ubuntu:~$ 

```

*edit* also i notice that when i blow into my mic i can hear it on the speakers i'm just haveing trouble getting sound recorder or anything else working

---

### Post by pete83 on 2007-06-15
Have you run "alsamixer" from the terminal, then hit f4 to see the recording devices, and unmuted everything and turned up all volume? If so, did you try all the possible sources in Sound Recorder? (that is, where it says "record form input")

---

