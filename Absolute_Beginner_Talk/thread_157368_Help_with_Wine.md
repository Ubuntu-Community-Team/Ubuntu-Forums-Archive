---
title: "Help with Wine"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by slipk487 on 2006-04-09
Everything i install and run with wine lag what could cause that and when i hit the audio tab winecfg closes and i get this ```
slipk487@slipk487:~$ winecfg
ALSA lib seq_hw.c:455:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/slipk487/.kde/socket-slipk487.
can't create mcop directory
```

---

### Post by hollywoodb on 2006-04-09
try
```
lsmod | grep snd_seq
```

if snd_seq isn't loaded, try
```
sudo modprobe snd_seq
```

if your audio tab in winecfg works and you don't get that ALSA error, then add snd_seq to /etc/modules by doing:
```
sudo echo "snd_seq" >> /etc/modules
```

I'm not sure what the mcop stuff is about, however

---

### Post by slipk487 on 2006-04-09
i tried that and still get the same error

---

### Post by robglinka on 2006-05-02
Hey, I ran into this problem myself, and saw your post so here is how I fixed the problem.

```

mkdir  /home/slipk487/.kde/socket-slipk487

```

Another user solved it this way:
> 
The problem is the crash of artd during the automatic audio detection of wine.
to solve it just rename /usr/lib/wine/winearts.drv.so to something like renaming /usr/lib/wine/winearts.drv.so.old

---

