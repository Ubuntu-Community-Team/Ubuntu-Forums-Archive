---
title: "Help installing Java"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by dethredic on 2007-12-03
Ok, I have been through a mess installing Java so far.

First I used Synaptic, and installed j2re1.4. I then found out I needed Java 1.5, not 1.4

So then I did this:
sudo apt-get update
sudo apt-get install sun-java5-jre
I didn't get any errors, but my program still didn't run. So then I did java -version and I got 1.4.2 :(

I then checked add remove programs and bot Java 4 / 5 were installed, 

I then installed Java 6 from add remove programs, but when I go terminal java -version I still get 1.4.2 :(

Any ideas?

---

### Post by daimaru on 2007-12-03
you have to change the default jave u use
```
sudo update-alternatives --config java
```
select the right one and your good to go.

---

### Post by dethredic on 2007-12-03
Great! Works well. Thanks a lot.

---

### Post by daimaru on 2007-12-03
@[dethredic]("http://ubuntuforums.org/member.php?u=230338")
great it works please mark thread as "solved" from menu "tread tools"

---

