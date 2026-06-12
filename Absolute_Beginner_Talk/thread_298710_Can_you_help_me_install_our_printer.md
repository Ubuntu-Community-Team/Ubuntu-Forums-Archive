---
title: "Can you help me install our printer?"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by I_have_seen_the_light on 2006-11-13
I am completely new in Linux and I have a bit of a problem.
we have 4 boxes in a network, 3 of them are installed with Windows and can print fine.  I just installed Xubuntu on one PC and was trying to print.  I tried folloing the instructions in the help file and the CUPS Web interface, but it is all too confusing.  need help

its set up like this.
Printer: Canon MP120
is connected to P4 2.3 GHz Win XP

My PC:
P3 600 mhz Xubuntu 6.06

Thanks in adavance!

---

### Post by an.echte.trilingue on 2006-11-13
You life is going to be easier if you use samba to print to a windows print server.

It involves some config file editing, but I think this is the best way you can do it.

[read this link]("http://www.faqs.org/docs/Linux-mini/Debian-and-Windows-Shared-Printing.html#printing_to_windows")

---

### Post by seshomaru samma on 2006-11-13
is the printer connected to a windows box or the xubuntu?
i personaly find that for these kind of things ubuntu is much friendlier than xubuntu. 
I am not sure if it will help you but try this GUI tool :
```
sudo apt-get install xffm4
```

---

