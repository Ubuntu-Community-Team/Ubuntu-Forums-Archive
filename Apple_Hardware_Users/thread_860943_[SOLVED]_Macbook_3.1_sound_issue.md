---
title: "[SOLVED] Macbook 3.1 sound issue"
date: 2008-07-16
forum: Apple Hardware Users
---

### Post by mattcossel29 on 2008-07-16
First off I would like to say hi! This is my first post, I have been reading quite a bit on the site though to help me set up and run Hardy on my Macbook.

Anyways, I am trying to get the sound to work, I read and tried to follow the instructions here:
[http://zepsling.wordpress.com/2008/05/03/enable-macbook-sound-in-hardy/](http://zepsling.wordpress.com/2008/05/03/enable-macbook-sound-in-hardy/)

I get to where I am entering the option in

I enter it(as pictured here)
[IMG]http://i145.photobucket.com/albums/r227/mattcossel29/Screenshot-mattmatt-laptop.png[/IMG]

My question is, Is this correct? If so, do I/how do I save this setting?(have tried just exiting and that did not work)

Any help on this situation would be much appreciated! Any suggestions, other ideas or constructive criticism is welcome as well!

Thanks!

---

### Post by mattcossel29 on 2008-07-16
Bump


I know atleast one of you knows how to do this :)

---

### Post by cyberdork33 on 2008-07-16
you should only bump after 24 hrs...

Try using a simpler editor like nano or gedit.

```
sudo nano /etc/modprobe.d/options
```

---

### Post by mattcossel29 on 2008-07-17
> **cyberdork33 said:**
> you should only bump after 24 hrs...

Try using a simpler editor like nano or gedit.

```
sudo nano /etc/modprobe.d/options
```


Sorry about that, I will remember that next time.

Thank you for the information! I will try that when I get home.

---

### Post by mattcossel29 on 2008-07-17
Thank you cyberdork33! That did it!

:guitar:

---

### Post by mattcossel29 on 2008-07-17
Well, I thought it did.. It works for the audio player(only app I have tried it on) but it does not work for anything online

*edit nvm a reboot fixed that issue!

---

### Post by cyberdork33 on 2008-07-17
if you could, please mark this thread as solved from the thread tools menu. Glad you got it working.

---

### Post by mattcossel29 on 2008-07-20
> **cyberdork33 said:**
> if you could, please mark this thread as solved from the thread tools menu. Glad you got it working.

Done. Thanks again for the help!

---

