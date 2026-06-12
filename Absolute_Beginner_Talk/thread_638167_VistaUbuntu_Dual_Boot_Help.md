---
title: "Vista/Ubuntu Dual Boot Help"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by RobotoWorks on 2007-12-11
So I want to dual boot Ubuntu with my current Vista, I made the partitions, and have the Live CD, now theres only one problem, when I go to install Ubuntu, everything starts out fine, I choose "Manual" to install it, that way I can be in charge of everything. So anyway that goes well too, it shopws both partitions and the amount of space on each of them. But when I click "Install" it gives me an error prompting "No root file specified" or something along thos  lines(Im sorry I forgot exactly what it said. What is the error, and how can I fix it?

---

### Post by overdrank on 2007-12-11
> **RobotoWorks said:**
> So I want to dual boot Ubuntu with my current Vista, I made the partitions, and have the Live CD, now theres only one problem, when I go to install Ubuntu, everything starts out fine, I choose "Manual" to install it, that way I can be in charge of everything. So anyway that goes well too, it shopws both partitions and the amount of space on each of them. But when I click "Install" it gives me an error prompting "No root file specified" or something along thos  lines(Im sorry I forgot exactly what it said. What is the error, and how can I fix it?

Hi and when you create the ubuntu partition you will need to set it as / like in this screen shot
[http://img216.imageshack.us/my.php?image=feistydual12tj0.png](http://img216.imageshack.us/my.php?image=feistydual12tj0.png)
And this link may help
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Presto123 on 2007-12-11
> **RobotoWorks said:**
> So I want to dual boot Ubuntu with my current Vista, I made the partitions, and have the Live CD, now theres only one problem, when I go to install Ubuntu, everything starts out fine, I choose "Manual" to install it, that way I can be in charge of everything. So anyway that goes well too, it shopws both partitions and the amount of space on each of them. But when I click "Install" it gives me an error prompting "No root file specified" or something along thos  lines(Im sorry I forgot exactly what it said. What is the error, and how can I fix it?

First off, I would suggest that you make sure to have a swap file...it helps in speed. Also, when you go into your partitioning menu as "manual" you can fix this problem by clicking on the partition, then clicking "edit partition" and set the one you want to install Ubuntu at the bottom as "\". This will show up when you click on the drop-down box. Set up the other swap file space as a "Linux Swap".

**Edit**Yeah. Like the picture he has above. :) Another one beats me to it!**

---

### Post by RobotoWorks on 2007-12-11
Wow, you guys were right on, now that you told me, I remember that I didnt have that set, btw is it "/" or "\"?

---

### Post by overdrank on 2007-12-11
> **RobotoWorks said:**
> Wow, you guys were right on, now that you told me, I remember that I didnt have that set, btw is it "/" or "\"?

Yea I believe it is /

---

### Post by davidc502 on 2007-12-11
What you want to do is format the hard drive, and install Ubuntu on its own. This eliminates the problem of dual boot, and you get the best OS to boot!

I know, not terribly helpful. If anything, dual boot with XP. I recommend staying away from mista ole problematic vista.

---

### Post by RobotoWorks on 2007-12-11
Okay well heres what I did, I installed Ubuntu about 1 month ago, well last Sunday, I decided to format my drive using my recovery disk, that gave me Win XP, I have Vista on a Live CD so I installed it, now I want to dual boot Ubuntu. I need Vista because I use ALOT of Wndows apps, but at the same time I love Ubuntu!

---

