---
title: "The Application &quot;gedit&quot; has quit unexpectedly."
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by pikeblodd on 2006-09-01
hey all, ive just loaded up my ubuntu two days ago, and other than some minor trouble (see title) im having a blast.  i was wondering if anyone else has seen or has heard of gedit failing all over the place and if anyone knows a fix for it.  i had to use nano to update, and havent been able to do much without this error popping up.

any advice would be greatly appreciated, and talk slow, im still learning.

thanks!

---

### Post by jISh on 2006-09-01
Haven't heard of that one, really. Try updating your system with the terminal:

sudo apt-get update
sudo apt-get dist-upgrade

And if you need an alternative while finding a solution, feel free to
sudo apt-get install leafpad

Replica of the almighty Windows notepad, best software by Microsoft! :D

---

### Post by jordanmthomas on 2006-09-01
Also, try running gedit from a terminal and see what it spits out on there when it dies.

---

### Post by pikeblodd on 2006-09-01
thanks for the suggestion for leafpad.  

ive done both update and dist-upgrade with no change, and gedit still fails even when launched in terminal.  i even tried to apt-get remove and then apt-get install gedit, with no change either.

i was wondering, since i havent really done too much, if i might be better off reinstalling?  could my live-cd i burned have an error on it?  im just curious to know whats up since from all my google searches i havent turned up anyone else who has had this problem.

---

### Post by jordanmthomas on 2006-09-01
What does come up if you run gedit from a terminal?  Most programs will tell you what kills them if you do this.

---

