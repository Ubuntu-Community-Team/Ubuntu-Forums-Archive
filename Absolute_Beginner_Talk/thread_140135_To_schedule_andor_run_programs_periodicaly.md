---
title: "To schedule and/or run programs periodicaly"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by Iesos on 2006-03-05
I have two programs that I want to run, but not when anyone in my local network or me are at their computer. That is how do I schedule a program to run at like 02:00 (24-hour time that is), and then terminate itself at like 06:00.
Got any sugesstions on commands or programs designed for this?

---

### Post by aggiechemist on 2006-03-05
Cron and anacron are exactly for that. I have no idea how to use them, but they are programs in ubuntu for scheduled operations.

---

### Post by christhemonkey on 2006-03-05
go into synaptic and search for ```
gcrontab
```
Which is a nice GUI program for cron, or if in KDE there is kcron.

---

### Post by Iesos on 2006-03-05
Thanks for the hint.
Read the manual, but manuals with no examples doesn't help me that much.
If anyone could give a little example I would be thankfull.

---

### Post by Xian on 2006-03-05
[QUOTE=Iesos]If anyone could give a little example I would be thankfull.[/QUOTE]

You could just have searched the wiki: [Crontab-HowTo](https://wiki.ubuntu.com/CronHowto).

---

### Post by Iesos on 2006-03-05
Thanks! gcrontab seems to be what I'm looking for. I'll be back in the morning if it doesnt work.

---

### Post by Iesos on 2006-03-06
I'm sorry, but this doesn't work.
I used cron (without the GUI), this is my crontab:
0 2-6 * * * /usr/bin/qtorrent
which should run qtorrent between 2 and 6 at night/morning, but it doesn't.
I tried changing it. Changed it at 10:03 to:
5 10 * * * /usr/bin/qtorrent
and then att 10:05 it did'nt run. (waited for a few minutes but it didn't work anyway.)
Have I messed up the syntax or what could be the problem?

---

### Post by Iesos on 2006-03-08
I've got it working now. To run a program using X you need to specify your display device, as such:

* 2-5 * * * DISPLAY=:0 program

But I still got a problem. 2-5 doesn't mean it starts at 2 and ends at 5. It just says that it starts 2 and continues to start in that intervall if it is closed.
What I would need is a command that closes the program, other than "kill". A command that ends the program in a normal way.

---

