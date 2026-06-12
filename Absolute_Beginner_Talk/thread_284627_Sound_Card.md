---
title: "Sound Card"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by nhandler on 2006-10-25
I recently installed Ubuntu on my Dell Inspiron 6000 laptop. When I first installed it, it wouldn't play various codecs. I followed various tutorials and threads to try and fix that. Now, when I launch gtkpod and try and play an mp3 song, I get this error:
Pleae check that:

Your soundcard is configured properly
You have the correct output plugin selected
No other program is blocking the soundcard

Sound was working when I first installed Ubuntu. I have no other programs that play audio running (as far as I know), so that should mean that nothing is blocking the soundcard.

If someone could help me out, I would really appreciate it. I am totally new to linux. Thanks.

Well, I feel dumb. I guess the problem had to do with a site I was viewing in firefox (my.yahoo.com). The minute I closed firefox, the sound started working in my programs. Now, even with that site open in firefox, the sound works.

---

### Post by woedend on 2006-10-25
I get this error if there is more than one device that has capability to play sound(dual cards, webcams, etc).
try this for a moment..
double click the sound icon by the time.
go to file -> change device
how many are listed?  Your soundcard should be 0, is it?

---

