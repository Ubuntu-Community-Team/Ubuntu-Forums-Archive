---
title: "Various questions"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by Handle123 on 2006-06-07
Hi

I just started using Ubuntu about a week ago. I've been very impressed (I always used Windows before this) but I've got some issues that I'm not sure how to solve.

1. My number pad doesn't work. Pressing numlock doesn't do anything, its as if numlock is always off.

2. Sound doesn't work - though it used to, and I can't think of any reason why it isn't working now.

I'm using the soundcard on my Nforce2 motherboard, and the keyboard is just a standard generic.

Thanks

---

### Post by jvictor on 2006-06-07
Numpad:: is there any bios setting that disables numpad ?

---

### Post by _simon_ on 2006-06-07
not sure what could be wrong with the numpad/numlock :-k 

As for sound, go into Terminal and type alsamixer and just check the settings in there, it could be something has become muted or something silly?

---

### Post by Handle123 on 2006-06-07
](*,) 

I had one of the speaker options muted! Hehe, dunno how that happened. Now I'm trying to figure out how to make sound come out of all 4 speakers instead of just the front 2.

As for the numpad thing, I don't think its a BIOS thing, since when I dual boot into Windows it works fine.

Thanks for the responses

---

### Post by _simon_ on 2006-06-07
ok back into alsamixer... do you have anything that says surround, centre, wave centre, wave LFE, wave sur, etc? if so whack the volume up on them whilst listening to an mp3 and that should sort you out!

apparently this *might* solve your numbpad problem:

```

sudo apt-get install numlockx

```

---

### Post by Handle123 on 2006-06-07
Unfortunately that didn't fix it. Edit : in regards to the numpad that is

I tried the sound thing, and I've increased every option that can be modified (some can't be increased from 0) and theres still no rear speaker sound.

:confused:

---

### Post by Handle123 on 2006-06-08
Anyone else have this problem?

---

### Post by dvarsam on 2006-06-08
To help you fix your sound problems, read the following article:

[http://ubuntuforums.org/showthread.php?t=154233](http://ubuntuforums.org/showthread.php?t=154233)

Good Luck!

P.S.1> Be Patient & read it down to the bottom!!!

P.S.2> Read the whole thing man!!!!

---

