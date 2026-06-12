---
title: "monitor problems with Ubuntu 7.04"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by MPAD on 2007-11-11
I recently installed flightgear which was very jerky.I exited and got a message about display drivers which I agreed to insall as I thought this was the problem. After this my monitor wont display and keeps displaying "No Support" when booted. I posted a thread which got back some responses which I tried but to no avail. I have since discovered that it is only   MY  monitor that will not function, also the monitor works fine with windows and live Ubuntu CD. I can only conclude that something on my monitor settings on the installed version is corrupted and will not work. Can anybody shed light on my problem? Looking forward to hearing from "Anybody". Alternately can you tell me how to back-up my e-mails, as I can get in in recovery mode. What file do they live in, so that I can copy to memory stick and re-install from scratch.Then copy back the info I dont want to loose.

                                        Mike

---

### Post by Pumalite on 2007-11-11
Check /var/lib/dpkg/status, find the drivers that you installed and un-install them.

---

