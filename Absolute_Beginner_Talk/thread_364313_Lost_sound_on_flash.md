---
title: "Lost sound on flash"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by Jussi01 on 2007-02-18
Hei all, got a weird problem, I have lost sound on flash plugins in firefox. every other program plays sound perfectly. I have checked that alsamixer channels are all up and all my volume control settings seem to be fine. has someone heard of this/ knows how to fix it? 

Much appreciated

Jussi

---

### Post by r4ik on 2007-02-18
Open terminal, and enter:
Code:

sudo aptitude install alsa-oss

Wait for the install to complete, before typing:
Code:

gksudo gedit /etc/firefox/firefoxrc

A file will open, and in the file you will see:
Quote:
FIREFOX_DSP=”none”
Change this to:
Quote:
FIREFOX_DSP=”aoss”

Good luck !

---

### Post by Jussi01 on 2007-02-18
Thank you!!

---

### Post by r4ik on 2007-02-18
Glad it worked.
Thanks for the reply.

---

### Post by Jussi01 on 2007-02-20
No problems - I hate it when you help someone and they dont even bother to say thanks. BTW, Thanks again!! :D

---

### Post by Pugwash on 2007-02-21
I seemed to have lost sound on flash after an update today (I'm on opera btw). Unfortunately this is what I get:

```
~$ sudo aptitude install alsa-oss
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

```

Which repository should I enable?

Cheers

---

### Post by r4ik on 2007-02-21
Try reinstall.

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

Good luck !

---

### Post by Pugwash on 2007-02-21
Ah, that solved it. Many many thanks!!!!:) :) :)

---

### Post by r4ik on 2007-02-21
Glad i could help.

---

### Post by karhulitos on 2007-02-25
Great, this helped me with my [sound level problems]("http://ubuntuforums.org/showthread.php?t=367594") as well!

---

