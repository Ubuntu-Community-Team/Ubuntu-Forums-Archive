---
title: "[SOLVED] mplayer not playing dvds"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by rouge568 on 2007-07-23
I am trying to use mplayer to watch dvds on Feisty, but everytime that I try to open one, I get the following error message:
> Error opening/initializing the selected video out (-vo) device.
I have tried all the possible drivers, and for every other one, I get :
> FATAL: Could not initialize video filters (-vf) or video output (-vo).
Could someone please help?

---

### Post by asmoore82 on 2007-07-23
do you have the DVD Decryption packages installed?

---

### Post by rouge568 on 2007-07-23
Which is that? I went into synaptic and installed all packages to do with reading/playing dvds and mplayer. Nothing is different. Thanks for answering, though.

---

### Post by Majorix on 2007-07-23
Ah yes I remember that error. You have to fix it by going to .mplayer and finding your gui.conf file. I am not sure what it was named. So can you please post the result of
```
ls ~/.mplayer/
```

And we can help :)

---

### Post by asmoore82 on 2007-07-23
you will need a **CSS** (Content Scrambling System) decryption library to play back commercial DVDs.
you will not find such a thing in the official packages lists...
I would recommend following the Installing DVD Support section [here]("http://linuxondesktop.blogspot.com/2007/05/13-must-do-things-on-new-ubuntu-704.html").

:P ::move along: nothing to see here:: :P

---

### Post by rouge568 on 2007-07-23
```

scott@scott-laptop:~$ ls ~/.mplayer/
config  gui.conf  gui.history  gui.pl  gui.url

```

---

### Post by subaru on 2007-07-23
best solution  . . . try getting Sabayon linux dude . . . its another distro . . . plays dvds out of the box

---

### Post by rouge568 on 2007-07-23
I followed the link and installed libdvdcss. It works now! Only problem is I wonder if it's legal...
Thank you!

---

