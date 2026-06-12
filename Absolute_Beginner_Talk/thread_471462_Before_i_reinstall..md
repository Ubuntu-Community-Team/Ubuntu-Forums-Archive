---
title: "Before i reinstall."
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by jusmurph on 2007-06-12
So I’m looking at reinstalling Ubuntu in attempt to fix my sound that has slowly disappeared.

I just have a few questions:

How do I back up Azureus’ progress. (I have a separate /home partition so the files will be fine), I’m more curious about where are the torrents stored so I can back them up and how do I resume these torrents from there current progress level?

With regards to Firefox
Are plugins stored in /home directory?
Are Bookmarks stored in /home directory?

What is the easiest way to back up my Ubuntu install so if a problem presents itself I can roll it back? (Not that reinstall is hard).

---

### Post by Pragmatist on 2007-06-12
One good way to find files is with the "locate" command.  First update its database (this takes a few minutes):
```
sudo updatedb
```

Now you can search, for example:
```
locate firefox |grep plugins
```

In the future, if you make a separate partition for  /home, then backup of personal files is much easier.

What problem are you having with sound?  Maybe you don't have to do a reinstall at all.

---

### Post by jusmurph on 2007-06-12
Thanks

updatedb... what database is this? Excuse te silly question but i would rather learn what im doing than copy and paste my way through linux.

Regarding my sound issue, Full details[ here]("http://ubuntuforums.org/showthread.php?p=2823086").

---

### Post by Pragmatist on 2007-06-12
> **jusmurph said:**
> Thanks

updatedb... what database is this? Excuse te silly question but i would rather learn what im doing than copy and paste my way through linux.

The database is used by the "locate" command.  Every time you change the files on your system, you can run this to make "locate" more accurate.

It is an excellent idea to learn rather than just cut-and-paste.  To learn more abou locate and updatedb, see the man pages:
```
man locate
```
```
man updatedb
```

---

### Post by jusmurph on 2007-06-12
quick question:
Is there a nicer way to read the man pages other than in the terminal... The terminal is not ecatly the greatest setting for reading.

---

### Post by squee on 2007-06-13
Copy them to text editor and then print it off if you want.....

---

