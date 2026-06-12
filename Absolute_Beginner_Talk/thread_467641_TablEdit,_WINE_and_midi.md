---
title: "TablEdit, WINE and midi"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Howlin' Hobbit on 2007-06-07
I installed the TablEdit reader (TefView)  under WINE. TablEdit is a program for creating music tablature. I opened a TablEdit file. Everything shows well but when I play it I get no sound. Checking the midi setup I see only one option, "WINE midi mapper."

When I searched the forums I found an entry where it was suggested that one checks to make sure one actually *has* sound with WINE by running winecfg and clicking on the Audio tab. I ran it, clicked the audio tab and it quit, leaving this error message:

howlin@pingu:~$ winecfg
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Link points to "/tmp/ksocket-howlin"
can't create mcop directory

I tried again and got *this* variant on the error message:

howlin@pingu:~$ winecfg
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/howlin/.kde/socket-pingu.
can't create mcop directory

I'm completely at sea here. Does anyone know how I can get the midi working via WINE?

I'm running Dapper Drake on a Dell Inspiron 5000.

Thanks for any clues!

---

### Post by trak87 on 2007-06-07
Someone claims to have solved the problem in this thread:

[http://ubuntuforums.org/showthread.php?t=196033](http://ubuntuforums.org/showthread.php?t=196033)

---

