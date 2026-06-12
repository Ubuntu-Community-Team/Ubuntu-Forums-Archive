---
title: "&quot;dpkg was interrupted&quot; on using Automatix"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by FariAzz on 2006-07-31
Hi, 

I installed Automatix in Kubuntu, and when I try to download some software I got an error message all the time:
[I]
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem[/I]

I tryed to uninstall Automatix because I can't enter Adept anymore even when Automatix is closed, but I got the same message about dpkg and it wouldn't work.

I'm totally new to Linux so I hope someone can give me a hand:confused:

---

### Post by Dr. Nick on 2006-07-31
automatix,adept,synaptic are all guis to the apt-get / dpgk program.

So what you need to do to fix all them (adept,automatix,...) is open a konsole and run 

sudo [I]dpkg --configure -a

[/I]Something must have interrupted automatix while it was running, the above command will finish what has already been started and rstore functionality to adept

---

### Post by catlett on 2006-07-31
Open up the konsole and enter this command 
```
sudo dpkg --configure -a
```If it isn't major then dpkg will fix itself.

---

