---
title: "Who has occupied the soundcard"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by mellibra on 2006-06-19
When I start xmms, it says "Couldn't open audio" and I need to check no other program is blocking the soundcard. How to fix this problem?

---

### Post by uzi09 on 2006-06-19
i really doubt that it's some other program using it. especially if that's currently the only program you're running and it gives you that message.

i think it might be some driver issue. can you give us some info on your system?
do you have a factory soundcard or something else u added?
what version of ubuntu are you using?
what version of the kernel are you using?
to find out what kernel, copy paste what comes up when you enter the following into the terminal:
```
uname -a
```

EDIT: also, you may want to give this a try:
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_configure_sound_to_work_properly_in_GNOME](http://easylinux.info/wiki/Ubuntu_dapper#How_to_configure_sound_to_work_properly_in_GNOME)

---

### Post by mellibra on 2006-06-20
My PC is TOSHIBA PORTEGE A100, a laptop. Ubuntu is Dapper Drake 6.06.

Linux ubuntu 2.6.15-25-386 #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006 i686 GNU/Linux

---

### Post by uzi09 on 2006-06-20
hmm, sounds like you have the latest stuff, too bad the sound didn't work out of the box for ya =\.

Did you happen to give that site a try?

---

### Post by ubuntuuser on 2006-06-20
Just out of curiosity: Do you have an ATI card and do you use fglrx? Because I have the same problem when I start X with the fglrx module: xmms says that my sound device is busy.

---

### Post by mellibra on 2006-06-25
I'm gonna crazy, still cannot fix this problem

---

