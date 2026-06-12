---
title: "sound ubuntu help"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by exneo002 on 2008-01-14
I use hp pavilion a819n with fiesty and wubi installer and sound doesnt work I try tarballs but the bash script wont exicute and I cant use sound also I need disicntion between pulse audio oss and alsa plz help me my ability to be able to use ubuntu as a full windows replacment depends on

---

### Post by ajmorris on 2008-01-14
Hi there,
could you please post the output of ```
sudo lspci
```

Also, PulseAudio = a sound Daemon
Alsa = Sound System (stands for Advanced Linux Sound Architecture)
OSS = Sound System (stands for Open Sound System) OSS is somewhat deprecated these days in linux, you are better of with ALSA.

---

