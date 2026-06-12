---
title: "several newbie questions"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by markii on 2007-11-24
Hope there are some folks out there charitable and patient enough to help with the following:

1. How do I -  or can I - install fonts (TrueType) without screwing up my Firefox/Epiphany browsers?

2. How do I set up Ubuntu/Firefox for anonymous proxy?

3. How can I tell if Firestarter is running? (I know it's running when I see the little blue circular icon present, but when that disappears I'm not sure if Firestarter has shut down)

4. Should I rely on Firestarter or move to Lokkit or Guarddog (or another firewall)?

5. Are there any good online Ubuntu tutorials for newbies out there?

6. How can I tell which programs are running at any given time?

7. Do I need to defrag Ubuntu? If so, how?

Many thanks to the patient amongst you.

---

### Post by marco123 on 2007-11-24
3. Firestarter is just a frontend that sets ip tables. (The built in firewall.) Once you've set it you can just exit it.

4. Firestarter is fine.

5. [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

6. Open the System Monitor, Sessions or run the "top" command in a Terminal.

7. Nope.:)

---

### Post by Dark_X on 2007-11-24
3. Go to system > administration > system monitor and click processes.
5. There are good tutorials here.  Just use the search function.
6. Same as 3.
7. Never.

---

### Post by Malta paul on 2007-11-24
Welcome, a good online book that may help you is at:
[http://book.opensourceproject.org.cn/distrib/ubuntu/hacks/](http://book.opensourceproject.org.cn/distrib/ubuntu/hacks/)
Have fun :)

---

### Post by skyjacker on 2007-11-24
# 7 Read info on this link. Very Good!   [http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by Tyche on 2007-11-24
With regard to knowing what is running on your machine, I use system monitor, but in a way that I haven't seen mentioned in this thread.  In Gnome, if you go to the upper bar and right-click on it, and select +Add To Panel, a box will come up.  In that box are various main headings.  Under Systems and Hardware is an icon marked System Monitor.  Select that and click on the ADD button, or just drag it onto the upper bar.  This will place a graphic representation of what your CPU use is on the bar.  Then, when you want to know what's running, just click the graph.

When you click on the graph, a box will appear with 4 tabs in it.  The first tab, System, shows your computer name, distribution, hardware and system status in brief form.

The second tab, Processes, shows the running processes on the system.  ***_CAUTION: _*** The ability to end processes or KILL processes is available in this view.  Ending or Killing the wrong process can lock up or kill your system.  It will not destroy your distribution, but you could have to resort to a hard re-boot (power cycle) to restart your system.

The third tab shows the system Resources in graphical form.

The fourth tab shows your file systems.

Additionally, by right-clicking on the graph, you get a menu from which you can select Properties.  Additional graphs can be added, at your discretion, and the colors of the graphs can be changed to suit your aesthetics.

I hope this helps.

---

