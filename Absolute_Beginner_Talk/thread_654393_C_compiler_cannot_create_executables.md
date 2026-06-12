---
title: "C compiler cannot create executables"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by venicia on 2007-12-31
Kubuntu Feisty Fawn dual-boot w/ WinXP on Compaq Presario 900.

And yes, I've tried sudo apt-get install build-essential
do I need to do a sudo apt-get update or something?

As far as I know, using the "add programs" (adept installer) works like a charm, but when I try to compile from source in the terminal I get the cannot create execs error message.

Total Ubuntu/Linux newbie here; I've grown up with Windows (ever since the 2.0 days) and just started using ubuntu a day ago, so any and all help is appreciated!

---

### Post by Perfect Storm on 2007-12-31
```
sudo aptitude update && sudo aptitude safe-upgrade
sudo aptitude install build-essential
```

Please post output. Also we need the output of when you're configure it + make.

---

### Post by venicia on 2007-12-31
./configure renders a XML::Parser perl module is required for intltool error.
Kubuntu is actually running on my other laptop right now (which has a busted touchpad) so I'll get you the output in a few minutes.
[edit] Nvm, once I got the hang of using Synaptic everything fell into place, thanks anyways!

---

