---
title: "Macbook keyboard not working"
date: 2008-11-09
forum: Apple Hardware Users
---

### Post by rahoagla on 2008-11-09
In order to get the caplock and numlock lights working I removed the mouseemu package per instructions I read in another thread.  However, after doing this, my keyboard ceases to work (except for brightness control). My keyboard resumed working as before upon reinstalling mouseemu. I am running Ubuntu 8.10 on a Macbook 2,1.  Also my function keys (F1-F8) seem to be mapped to volume, brightness, etc, instead of regular functions.

---

### Post by Rog-Mahal on 2008-11-10
I had a similar problem upon removing mouseemu, however when I rebooted my keyboard functioned normally. Your function keys are mapped the way they are by the pommed package. It controls your function keys and special keys like eject. If you want them to behave like normal function keys you just need to hold the fn button and press them. You can change this behavior by editing the /etc/pommed.conf file. A quick online search should tell you how to switch things around.

There are plenty of posts about how to set up your touchpad without mouseemu and get things like right/middle click.

---

### Post by rahoagla on 2008-11-11
Thanks so much.  Too think all this time I just had to reboot.  I feel a little sheepish, but now I'm running 100% smoothly.

---

### Post by Rog-Mahal on 2008-11-11
Glad to hear it, would you mark this thread as solved? It's under the Thread Tools link at the top of the post.

---

