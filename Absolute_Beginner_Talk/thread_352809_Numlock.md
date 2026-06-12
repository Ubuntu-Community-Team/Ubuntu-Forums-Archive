---
title: "Numlock"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by nlow04 on 2007-02-03
When I boot up, my numlock is off.  Is there a way to keep this from happening again?

Please respond.  Thanks.

---

### Post by meng on 2007-02-03
Install the package numlockx
sudo apt-get install numlockx

---

### Post by aysiu on 2007-02-03
Or use KDE.

---

### Post by nlow04 on 2007-02-03
How do I get the package package numlockx
sudo apt-get install numlockx which will keep my numlock on when my pc boots?

Please respond.  Thanks.

---

### Post by dalee on 2007-02-03
Hi,

Open a terminal, and copy/paste or type the sudo apt-get install numlockx. Hit the enter key, it will ask you for your password. Type that in, (it won't show as you type password). Hit enter, and wait and watch!

When done, log out and re-log in. It should be working.

dalee

---

### Post by meng on 2007-02-03
You will need universe repositories enabled.

---

### Post by aysiu on 2007-02-03
**Step 1**: Enable extra repositories (as meng says, you need the Universe repositories, which are not enabled by default):
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) will help you with this

**Step 2**: Install *numlockx* (as dalee says, the command ```
sudo apt-get update && sudo apt-get install numlockx
``` will install *numlockx* for you... after you've completed *Step 1*.

To read more about installing software in Ubuntu, read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by nlow04 on 2007-02-04
How do I open a terminal?  I'm sorry I don't understand since I'm a newbie with Ubuntu 6.10.

Please respond.

---

### Post by meng on 2007-02-04
It's funny, specifically asking for a respond is quite superfluous!
Applications > Accessories > Terminal.

---

### Post by aysiu on 2007-02-04
> **nlow04 said:**
> How do I open a terminal?  I'm sorry I don't understand since I'm a newbie with Ubuntu 6.10.

Please respond.
If you need screenshots and/or aren't using Gnome, this will help:
[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

---

