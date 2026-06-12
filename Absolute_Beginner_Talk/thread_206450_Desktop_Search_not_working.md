---
title: "Desktop Search not working"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by hanzj on 2006-06-30
I can't seem to get Desktop Search (Places/Search) to work well. For example, in /hanzj/ (in my home directory), I've got a file named journal.txt. ONe word there is "kitchen." Yet when I try do a search for "kitchen", Desktop Search gives no hits. In File/Preferences, there is a checkbox on "Index my home directory". If you can help me fix Desktop search, I'd appreciate it.

edit: typo fixed.

---

### Post by ajgreeny on 2006-06-30
I presume you did the search on "kitchen" not "ktichen" as you typed; typo error?  Have a look in gnome system monitor to see if beagled is running.  It should be by default, but if it isn't that could affect what is (or rather isn't) happenning.

---

### Post by mozetti on 2006-06-30
Are you sure the Desktop Search is supposed to work like that now, or is it just supposed to be a filename search?

Here's a Wiki link that discusses it, but I'm not sure if it's implemented yet:

[https://wiki.ubuntu.com/IntegratedDesktopSearch?highlight=%28search%29](https://wiki.ubuntu.com/IntegratedDesktopSearch?highlight=%28search%29)

---

### Post by ajgreeny on 2006-06-30
Certainly beagle works superbly on my machine, and finds everything I expect it to when I search on an included word, not just on file names.  Have you checked that you have beagle installed?  I've looked for tracker but can't find it in synaptic so can't help with that package.

---

### Post by hanzj on 2006-06-30
AJGreeney,

Is it necessary to check system monitor to see if beagled is running, if i have the "Desktop Search" program running right in front of my face?

Anway, I did check system monitor. beagled and beagled-helper are running.

After reading your 2nd message, I doublechecked that beagle is installed. I did "sudo apt-get install beagle". "beagle is already the newest version."

---

### Post by ajgreeny on 2006-06-30
And is beagled running?  Look in gnome system monitor / Processes.  In ubuntu 5.10 beagle did not work as well as it does in 6.06, but if this is not helping I don't think I can go any further.

---

### Post by hanzj on 2006-06-30
yes, beagled is running.

---

