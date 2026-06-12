---
title: "How much spaced used on hard drive?"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by dwiedenfeld on 2007-11-01
I'm sorry, I'm a noob, and I HAVE searched in the forums here, but I can't find it. So here goes:

How do I find out how much of my hard drive / partition is used, and how much free space is there? 

I've looked all over nautilus, but I can't seem to find anything. I know the answer is going to be easy and obvious once one of you points it out, but right now I'm stumped with this simple little task.

---

### Post by nick_h on 2007-11-01
Type:```
df -h
```

---

### Post by sloe on 2007-11-01
I haven't found it in the GUI, either, but to be fair, I haven't really looked.  I use a terminal and the command **df**.  df gives you the info for the complete file system, so if you want to look at a particular partition you should name it to remove all extra info.  Also, you should add a size modifier - default is displayed in 1k blocks.  You can use -m to get 1 megabyte blocks, or -h to get human readable format.  If you have everything on one partition (/dev/sda1 or/dev/hda1), just use this:

df -h /

If you've got more than one partition, I haven't figured out how to get just the hard drives without using grep, so you could just issue df -h and see everything.

-sloe

---

### Post by steve.horsley on 2007-11-01
For the GUI, go System->Administration->System Monitor and click the File Systems tab.

---

### Post by Paqman on 2007-11-01
You can put the Gnome System Monitor on a panel and you'll have all that information and more available with a single click.

---

### Post by dwiedenfeld on 2007-11-01
Great--this was what I needed. 

For us noobs, the GUI version (via System Monitor) is easy to understand. (And somehow I never found it while looking around in there.) But I do appreciate df -h too--lots of good information in that one.

Thanks, guys.

---

### Post by nick_h on 2007-11-01
If you want to look at the usage in more detail then Applications->Accessories->Disk Usage Analyser is very good.

---

### Post by rudeboyskunk on 2007-11-01
You can also go to Applications>Accessories>Disk Usage Analyzer (or something like that) and it will tell you.

---

