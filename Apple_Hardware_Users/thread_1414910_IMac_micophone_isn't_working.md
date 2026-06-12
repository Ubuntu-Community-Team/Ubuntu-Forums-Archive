---
title: "IMac micophone isn't working"
date: 2010-02-24
forum: Apple Hardware Users
---

### Post by C.mind on 2010-02-24
Hi everybody. I just installed Ubuntu 9.10 64 bit on IMac few days ago.Every thing went fine except the microphone and the headphone,they wouldn't work for unknown reason.I have googled and searched the forum for related problem but no luck in finding such thing.The speaker sound is working very well and I can hear anyone talking to me through skype but they can't hear me.My iMac features are " Apple iMac model A1224; 20/2.4/1Gb/250Gb/SD/AP/BT. I would be really appreciative if someone helps me out.

---

### Post by linuxopjemac on 2010-02-24
you might want to unmute all channels with
```
alsamixer

```
if that doesn't work, I would install the alsa backports and then unmute all channels.

aptitude install linux-backports-modules-alsa-karmic-generic

PS in general it's good to read the wiki for your particular machine [here]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages").

---

### Post by C.mind on 2010-02-24
I unmuted all of them but no thing worked out. I also installed alsa but i didn't work.It's IMac 7.1.

---

### Post by linuxopjemac on 2010-02-24
[https://help.ubuntu.com/community/Intel_iMac#Sound](https://help.ubuntu.com/community/Intel_iMac#Sound)

> Klaus Doblmann: If your microphone doesn't work (no mic-boost switch), set the model to "mbp3" instead of "imac24". 

```
nano etc/modprobe.d/options.conf 
```

and edit the 
```
options snd-hda-intel model=imac24
```
to
```
options snd-hda-intel model=mbp3
```

reboot your machine and unmute all channels again...

---

### Post by C.mind on 2010-02-26
still the same problem.

---

### Post by linuxopjemac on 2010-02-26
Did you install the alsa backports ?

[http://idebian.wordpress.com/2008/06/23/24-imac-alsa-configuration/](http://idebian.wordpress.com/2008/06/23/24-imac-alsa-configuration/)

---

### Post by C.mind on 2010-03-03
I install Alsa driver and it's working now. thank you very much man

---

