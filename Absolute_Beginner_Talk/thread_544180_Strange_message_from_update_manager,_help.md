---
title: "Strange message from update manager, help?"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by JBrehm on 2007-09-06
I got this message after downloading some updates. What's wrong? How do I fix it?

[[IMG]http://img467.imageshack.us/img467/4086/screenshotsynapticpc7.th.png[/IMG]](http://img467.imageshack.us/my.php?image=screenshotsynapticpc7.png)

---

### Post by alienexplorers on 2007-09-06
You could try running;
> sudo apt-get update
and
sudo apt-get upgrade

---

### Post by afonic on 2007-09-06
You have added some 3rd party repositories which doesn't seem to be available.

Just edit your /etc/apt/sources.list file and remove the ones showing in the error message,

---

### Post by mocoloco on 2007-09-06
It means what it says.  It couldn't contact those two repositories, so it will ignore them until it can.  No big deal.  If it continues for a while maybe remove them, or go to their sites to see if they've changed the URLs.
Otherwise just hit "reload" every so often in your Update Manager, or in Syanptic (or terminal commands like alienexplorers posted) and it will probably just clear up on it's own.

---

