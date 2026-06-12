---
title: "No sound from speakers, but phones work."
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by ipsisverbis on 2007-11-11
I have an LG S1, and i can't manage to have sound trough speakers, only on the phones,

Any ideas to solve this problem?

Thanks.

---

### Post by DutyDuty on 2007-11-11
Pardon me for not being familiar, but what is a LG S1? 
If it is a Toshiba, the link in my signature might help.
If not, sorry.

---

### Post by ipsisverbis on 2007-11-12
[It's this one.]("http://www.lge.com/products/model/detail/s1%20pro%20express%20dual.jhtml.")

I will try that, it might work.
Thx

---

### Post by ipsisverbis on 2007-11-12
I've done the steps that you have on the other thread...
Still, no sound from the speakers, but the phones works allright.
I can't understand what's the problem...
The laptop came with a program for win XP to manage the sound card definitions, the inputs and outputs are managed trough that program. I'm guessing that maybe I need something like that...

Does anyone has a clue in what's is the problem?

---

### Post by deadgobby on 2007-11-12
For the audio to work on the S1 you will need ALSA version 1.0.12rc1 or greater.
[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

Gobby

---

### Post by ipsisverbis on 2007-11-12
I've installed the ALSA version 1.0.15, and the problem remains...

More ideas? 
thx for the help

---

### Post by zabien1970 on 2007-11-12
Is this something that just happened or has it never worked with ubuntu, are you dual booting

---

### Post by ipsisverbis on 2007-11-13
It never worked on ubuntu.
I'm dual booting with win XP, and the sound works fine there.

thx

---

### Post by ipsisverbis on 2007-11-15
Hey, no more ideas on how to solve this problem?

---

### Post by DutyDuty on 2007-11-15
```
sudo apt-get install alsamixergui
```
Make sure it's not on mute. Run alsamixer and check volume levels. If there are any "MM" at the bottom of levels, move to them and press "m".

---

### Post by ipsisverbis on 2007-11-15
All MM's turned to 00, i rebooted and nothing. All the same, phones working, no sound from  speakers...

thx anyway.
what can i do more to try solving this problem?

---

### Post by ipsisverbis on 2007-11-21
anyone?

---

### Post by AvengingAngel718 on 2007-11-21
I actually had this problem when i first installed and the solution was pretty weird and simple..... try simply plugging your speakers into a different port. I don't know why it changed what port it used for me, but it did and this was my solution. if that doesnt work listen to what the other people are saying because I probably don't know what i'm talking about.

---

