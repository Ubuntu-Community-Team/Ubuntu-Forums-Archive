---
title: "real problem"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by yacinux on 2007-05-24
How to solve the problem of installation of a deb file that i downloaded manually in Ubuntu 7.04.i get this msg: could not open...?

the package might be corrupted or you are not allowed...
i have problem with synaptic too. please help.
by the way i tried some codes like: sudo dpkg --configure -a and similar but didn t work

---

### Post by benanzo on 2007-05-24
If you double-click the file does it ask for a password in order to run gdebi (package installer)?

Try this in terminal:
```
sudo dpkg -i (path to .deb file)
```

That should give you some output if it can't install.

---

### Post by starcraft.man on 2007-05-24
> **yacinux said:**
>  could not open...? the package might be corrupted or you are not allowed...


Ummm, I assume what I quoted is the message you got, maybe its just a bad download/version of the deb? This is the link where I got my copy of [real,]("http://archive.canonical.com/ubuntu/pool/main/r/realplay/realplay_10.0.8-0ubuntu3_i386.deb") I hope they get it in the repos soon. It is the edgy version btw, nothing wrong with it running on Feisty though. Do remember to do the small modifications as prescribed [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Player_.28RealPlayer_10.29") so ya get it working optimally.

That should be it, methinks. :)

Edit: Aye, try benanzo suggestion first, if that fails then redownload from my link, should work.

---

