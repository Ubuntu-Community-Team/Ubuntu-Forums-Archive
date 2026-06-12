---
title: "Command macros"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by k1001001 on 2007-08-25
Hi all. The server in my apartment complex doesn't seem to like my computer much and it kicks me offline after sitting idle for a few hours. To fix this, I type in "sudo ifdown eth0" followed by "sudo ifup eth0," which resets my connection and gives me a new DHCP lease. I'm wondering if it is possible to make a macro for these commands though, since it is sort of a pain to type out all of that twice a day every day. Thanks for any help!

---

### Post by Spook27 on 2007-08-25
You could write those commands into a simple text file starting with the line #!/bin/sh and chmod +x the file - that would save you a few keystrokes.  If you're feeling really up to it, you could also set up a cron job to handle all of that at regular intervals.

---

### Post by jordanmthomas on 2007-08-25
You could put this in your .bashrc
```
alias netfix='sudo ifdown eth0 && sudo ifup eth0'
```
Then, you would be able to just type netfix and put in your password.

---

### Post by Majorix on 2007-08-25
Since you don't know exactly when you will get disconnected, I don't think it would be good to make a cron task for this. But adding an alias for it -like jordan suggested- is a really good idea.

Good luck.

---

### Post by k1001001 on 2007-08-27
How would I edit my .bashsrc?

---

### Post by bodhi.zazen on 2007-08-27
to edit .bashrc :

you can either open gedit or in a terminal type :

```
gedit ~/.bashrc
```

+1 to the advice re: cron :twisted: cron will run those commands automatically two or three times a day as needed (automation is always good if possible for sys admin).

---

### Post by Acglaphotis on 2007-08-27
$gedit .bashrc

---

