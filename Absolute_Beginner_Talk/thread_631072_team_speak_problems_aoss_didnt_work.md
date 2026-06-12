---
title: "team speak problems aoss didnt work"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by yowshi on 2007-12-04
my teamspeak2 is muted nd i cant unmute mysel i have tried aoss and esdd things it doesnt work

and i did test my mic in sound recorder and it works i have tried alsamixer and unmuted everything and stuff

---

### Post by frodon on 2007-12-04
Make sure that all apps using the sound card are closed before using teamspeak, you can also run a "killall esd" command to make sure that no apps are locking the sound device.

The main problem is that teamspeak is poorly designed and still use the OSS sound drivers which is only able to handle the sound of one apps at the same time.

---

### Post by yowshi on 2007-12-04
actually the first time it failed to work i rebooted to make sure nothing was using the drivers

still didnt work even after the killall

---

### Post by frodon on 2007-12-05
i already had this problem but don't remember well how i solved it, i believe in my case it was mainly that my mic was muted somewhere in the sound control window.

I always run it with aoss.

---

### Post by yowshi on 2007-12-06
i checked everywhere i can think of an it isnt muted and i also run it with aoss it doesnt work. but not just the mic i get no speaker or headphone sound either

---

### Post by frodon on 2007-12-06
Check the output of the "lsof /dev/dsp" command, if something is locking your sound card you will get it as output.

---

### Post by yowshi on 2007-12-06
that command didnt give any output

oddly enough even when teamspeak is active it gives no output

oh aoss teamspeak gives me this ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.

i dont know if thats relevant

---

### Post by yowshi on 2007-12-12
bump

---

### Post by mnml on 2007-12-20
> **frodon said:**
> Check the output of the "lsof /dev/dsp" command, if something is locking your sound card you will get it as output.

lsof: WARNING: can't stat() ext3 file system /dev/.static/dev
      Output information may be incomplete.

---

