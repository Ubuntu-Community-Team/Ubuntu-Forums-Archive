---
title: "bandwidth watcher"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Sushubh on 2007-06-15
i needed some application to see which applications are accessing the net and using how much bandwidth...

---

### Post by Golyadkin on 2007-06-15
For some basic info, you can use "System > Administration > System Monitor" and click on the "Resources" tab. It shows speed, bandwidth usage and a total of sent / received bytes.

---

### Post by Sushubh on 2007-06-15
well yeah but it does not show it application wise. i wanted to see what software is taking all the bandwidth i have! sometimes the net just crawls :)

---

### Post by Golyadkin on 2007-06-15
Well, the hardcore way to do it is using "netstat" in the console. Maybe there is a graphical front end for that?

---

### Post by dustigroove on 2007-06-15
[FONT=Arial][COLOR=Black][SIZE=2]I did a quick [FONT=Courier New]apt-cache search net | grep bandwidth[/FONT]. Looks like 'bandwidthd' or 'nethogs' may suite your need?

Also as Golyadkin said, [FONT=Courier New]netstat[/FONT] should also do the trick. Not sure if it will break down your usage is an easily digestable way. But a [FONT=Courier New]netstat -tpc[/FONT] should bring up something useful.

Cheers

[/SIZE][/COLOR][/FONT]

---

### Post by Sushubh on 2007-06-15
cool checking thanks!

---

### Post by Sushubh on 2007-06-15
bandwidthd does not seem to work for me but nethogs works fine! thx again.

---

