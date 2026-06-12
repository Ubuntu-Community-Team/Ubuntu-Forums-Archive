---
title: "Issues with Synaptic"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by The Reepr on 2007-05-13
Synaptic won't start I get an error:

[IMG]http://i84.photobucket.com/albums/k36/TheReepr/Screenshot-1.png[/IMG]

anyone knwo how to fix it?

I tried the command line they told me but it keeps saying I need to be a superuser?

---

### Post by taurus on 2007-05-13
Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --config -a
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by The Reepr on 2007-05-13
all cleared up, but I had to enter it in a new window and there was an extra space needed thanks fo the help

---

