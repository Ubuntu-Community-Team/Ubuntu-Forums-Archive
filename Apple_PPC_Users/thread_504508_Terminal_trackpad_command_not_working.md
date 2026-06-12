---
title: "Terminal trackpad command not working?"
date: 2007-07-19
forum: Apple PPC Users
---

### Post by utn on 2007-07-19
Greetings all!

I've been trying to find a solution to my trackpad settings not working but have yet to find anyone with the same problems.

I have a Powerbook G4 (aluminum) 1.67ghz with Ubuntu 7.04 Feisty Fawn installed and so far its great. I was very surprised that I did not have to fool around with XGL/ATI junk to get Beryl working properly.

Anyway, when I try to disable the tap click feature on my trackpad I get this return in my terminal.

```
g4:~$ sudo trackpad notap
Password:
writing /dev/adb: No such device or address

```

Am I doing something wrong? I would really like to disable the tap clicking as its quite irritating.

And one  other quick question, is there a way to speed up my 2D/3D rendering for Beryl and the system in general? All of the Beryl effects work properly but they dont seem too smooth and it seems to me that my system should have no problem giving me ample frame rates for these kind of processes. I only get about 700-900fps in glxgears.

Help is very appreciated!
Thanks,
utn

---

### Post by gtcoffee on 2007-07-19
read this powerpc FAQ, it should be helpful.

[https://wiki.ubuntu.com/PowerPCFAQ#head-341b2526a7463780f67059c7bc7ec0a4635f2eab]("https://wiki.ubuntu.com/PowerPCFAQ#head-341b2526a7463780f67059c7bc7ec0a4635f2eab")

However, even i enable notap, but tap is still on, ppl said that is a bug,
so i dun noe........

---

### Post by ajmctaggart on 2007-07-19
Did you think of just uninstalling those powerpc-utils, it specifies the exact name in the PPC FAQ...if you uninstall those utilities, which I believe just control the trackpad, you shouldn't have any tap feature.

Just a thought, 

Good Luck,
ajm

---

