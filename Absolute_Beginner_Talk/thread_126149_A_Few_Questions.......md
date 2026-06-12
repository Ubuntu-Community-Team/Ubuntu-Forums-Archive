---
title: "A Few Questions......"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by xXx 0wn3d xXx on 2006-02-05
1. How can I disable update notifier from starting with the system and running all the time. It uses 25.6 MB of memory and it already checks for updates every 3 days.

2. Why does the trash applet use over 20 mb of memory ? There is nothing in it.

3 what is wnck-applet ?

4. How can I remove unessary things that are in gnome ?

5. How can I increase my swap. I only have 128 of ram so I might get better proformance with more.

Thanks

---

### Post by xXx 0wn3d xXx on 2006-02-05
does anyone know ?

---

### Post by aysiu on 2006-02-05
128 MB of RAM?
Don't use Gnome. Or KDE, for that matter.

To increase swap, you'd have to resize one of your existing partitions. For that, you need a live CD. I'd recommend PCLinuxOS or Knoppix.

Other than that, use XFCE.
1. See the first link of my signature.
2. ```
sudo apt-get update
sudo apt-get install xubuntu
```
3. Log out.
4. Sessions > XFCE
5. Log in.

---

### Post by paulmilliken on 2006-02-05
Regarding question 5, the following link might be useful: [http://enterprise.linux.com/enterprise/05/03/02/2250257.shtml?tid=129&tid=42](http://enterprise.linux.com/enterprise/05/03/02/2250257.shtml?tid=129&tid=42)

Not sure about your other questions sorry.

Paul

---

### Post by xXx 0wn3d xXx on 2006-02-06
can anyone answer my questions about the processes and it says that xubuntu can't be found. I think it's xbuntu anyway.......

---

### Post by Perfect Storm on 2006-02-06
[QUOTE=MasterChief1234]

2. Why does the trash applet use over 20 mb of memory ? There is nothing in it.
[/QUOTE]

[http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html](http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html)
Someone posted this in the community forum, good read for understanding :)

---

### Post by aysiu on 2006-02-06
[QUOTE=MasterChief1234]can anyone answer my questions about the processes and it says that xubuntu can't be found. I think it's xbuntu anyway.......[/QUOTE] You have to enable extra repositories--that was step #1, seeing the first link of my signature.

---

### Post by paulmilliken on 2006-02-07
[QUOTE=MasterChief1234]1. How can I disable update notifier from starting with the system and running all the time. It uses 25.6 MB of memory and it already checks for updates every 3 days.
[/QUOTE]
Regarding programs that run at startup, I recently discovered a program called BUM (Boot-Up-Manager) which might be useful for you: [http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html) 
I haven't used it myself yet but it looks promising.  Otherwise, you might want to try a program called "update-rc.d" - see the man page for details.

Paul

---

