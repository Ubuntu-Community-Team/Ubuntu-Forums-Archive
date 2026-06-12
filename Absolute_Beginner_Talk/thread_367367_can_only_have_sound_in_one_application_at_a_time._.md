---
title: "can only have sound in one application at a time. help!"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by darkeale on 2007-02-22
hi im new to ubuntu (6.06) so go easy. i can only have sound in one appication at a time. tried a few things in other forums but nothings worked. im using a onboard cmi9738 sound device. the programs im trying are Gtick and audacity. anyone have any ideas. thanks

---

### Post by daster on 2007-02-22
tell us what you have done about it!

---

### Post by darkeale on 2007-02-22
i followed all the various sets of instructions in this forum ([http://bbs.archlinux.org/viewtopic.php?t=10350)](http://bbs.archlinux.org/viewtopic.php?t=10350)). nothing ive tried has appeared to change anything so far

---

### Post by RichJacot on 2007-02-22
I'm having the same issue.  If I have firefox open with say a youtube screen up (even if its not playing) I can get no other sound from other apps (i.e. mplayer, UT, VLC, etc.).  The other apps run just fine but they just don't have sound.  If I close firefox and open one of the others they play fine.  Say I have a movie playing in mplayer or VLC then open firefox, firefox doesn't have sound.  Basically, whatever app. is using the sound card first gets it and  no other app. can use it until the first app is closed.

Hope my symptoms help...

Rich

---

### Post by darkeale on 2007-02-22
i also tried all the methods in this guide aswell. still nothing. 

[http://ubuntuforums.org/archive/index.php/t-32063.html](http://ubuntuforums.org/archive/index.php/t-32063.html)

rich maybe you should try these?

---

### Post by darkeale on 2007-02-22
anyone?

---

### Post by neji on 2007-02-22
have you tried running alsamixer and turning up the volume on all the sound channels?

$ alsamixer

---

### Post by darkeale on 2007-02-22
tried it but no difference. anymore ideas?

---

### Post by kelbizzle on 2007-02-22
I know exactly what he's talking about. I can't play TCE and use TeamSpeak RC2 at the same time.

---

### Post by kelbizzle on 2007-02-22
EDIT: You may want to check this out. 
[http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php#softmix](http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php#softmix)

---

### Post by darkeale on 2007-02-22
what should i replace !default with in that code? is it my user name ie alex?

---

### Post by darkeale on 2007-02-22
anyone know?

---

### Post by darkeale on 2007-02-22
if i upgrade to ubuntu 6.10 will that make any odds?

---

