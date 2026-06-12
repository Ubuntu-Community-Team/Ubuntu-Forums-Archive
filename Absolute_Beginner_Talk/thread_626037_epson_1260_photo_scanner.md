---
title: "epson 1260 photo scanner"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by montydonsheaddoctor on 2007-11-28
Hi i was wondering if anyone out there could help me with a little problem. I am new to ubuntu  and I am trying to get my epson 1260 scanner working. I have xsane installed and it recognises the scanner but if I try to preview or scan any documents the scanner just makes a noise as though it were jammed and nothing else?:confused:

---

### Post by master_kernel on 2007-11-28
First, try running this in a terminal:
```
sudo rmmod ppdev
```
If this solved it, it is related to these bug reports:
[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/102285](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/102285)
**[https://bugs.launchpad.net/ubuntu/+source/sane-backends-extras/+bug/88672](https://bugs.launchpad.net/ubuntu/+source/sane-backends-extras/+bug/88672)**
Blacklist this driver if it worked.

If that didn't work...

Did you check if it was compatible with Linux?

I googled and found the following:

This was solved, but it's in Polish or something: [http://forum.ubuntu.pl/showthread.php?p=370741](http://forum.ubuntu.pl/showthread.php?p=370741)

[http://ubuntuforums.org/showthread.php?t=431868](http://ubuntuforums.org/showthread.php?t=431868)

[http://ubuntuforums.org/showthread.php?t=108027](http://ubuntuforums.org/showthread.php?t=108027)


Hope this helps,
master_kernel

---

### Post by backflip on 2007-11-28
I've got the epson 1250 and xsane installed. Once I pointed xsane at my printer it worked ok. All I had to do was type the name of the printer, not the path or anything. In my case HP_Laserjet_1100 was sufficient.

---

### Post by montydonsheaddoctor on 2007-11-29
Thanks for the info. Removed the module but still no joy I guess I just have to keep searching

---

