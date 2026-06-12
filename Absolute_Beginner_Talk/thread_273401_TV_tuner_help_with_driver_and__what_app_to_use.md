---
title: "TV tuner help with driver and  what app to use"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by midnight27 on 2006-10-08
I have a Kworld / V-stream Xpert TV-pvr 883 pci card hooked up to cable tv.  I have use synaptic and download the 2 tv apps there, "Zapping Tv Viewer" which gives error popups all over the place and "Tv Time television veiewer" which blinks on screen and closes. I used another on a differnt install forget the name and it showed 4 diferent inputs, the first one came up with a screen that looked like tv fuzz.  There was no options to tune channel frequencies, or to even change channels at all.  This runs great in windows and even has a infrared remote. And it has an fm tuner as well and video capture.  

What should I use?
I entered these commands:
dmesg|grep tuner
dmesg|grep tv
and got the following on the terminal:

midnight27@midnight27-desktop:~$ dmesg|grep tuner
[17179588.804000] TV tuner -1 at 0x1fe, Radio tuner -1 at 0x1fe
[17179588.964000] tuner 2-0060: All bytes are equal. It is not a TEA5767
[17179588.964000] tuner 2-0060: chip found @ 0xc0 (cx88[0])
[17179588.996000] tuner 2-0060: tuner type not set
midnight27@midnight27-desktop:~$ dmesg|grep tv
[17179588.928000] tveeprom 2-0050: Huh, no eeprom present (err=-121)?
midnight27@midnight27-desktop:~$

According to this it looks like it is beeing recongnized but not set with a driver? I could be wrong.
I would appreciate any help with this and help reguarding an application to use it. Thanks

---

### Post by midnight27 on 2006-10-08
Is there anybody out there? anyone?

---

### Post by crispy_420 on 2006-10-08
try here

[http://ubuntuforums.org/showthread.php?t=90032](http://ubuntuforums.org/showthread.php?t=90032)

---

