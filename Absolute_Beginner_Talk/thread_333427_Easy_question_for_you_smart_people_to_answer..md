---
title: "Easy question for you smart people to answer."
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by smitty5533 on 2007-01-07
i just installed ubuntu last night and i have a few quick questions.

I have a tablet pc and i found a website which outlined some changes to make, the only problem is that i do not know what to type into the terminal to be able to edit these things.

I am not sure what to put into the terminal to be able to edit xorg.conf 


the website i looked at was [http://aleph-null.tv/go.php?doc=20050625-0102-56.xml]("http://aleph-null.tv/go.php?doc=20050625-0102-56.xml")

i'm working on learning ubuntu and i appreciate any help that you all can give me.

---

### Post by Ocxic on 2007-01-07
sudo nano /etc/X11/xorg.conf   to edit in a terminal
gksu gedit /etc/X11/xorg.conf   to edit in gedit.


both nano and gedit are text editors. sudo and gksu give you temporary root access so you can mopdify the files. sudo for just the terminal gksu if your goin to use a grphical proggram.

---

### Post by aysiu on 2007-01-07
That guide uses 5.10. I'm not sure if that makes a difference or not, but you're probably using 6.06 or 6.10 (more recent versions of Ubuntu).

The commands you're looking for are: ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by smitty5533 on 2007-01-07
thanks, what is the difference between sudo and gksudo?

---

### Post by aysiu on 2007-01-07
> **smitty5533 said:**
> thanks, what is the difference between sudo and gksudo?
The former is for terminal applications, the latter for graphical applications. More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by smitty5533 on 2007-01-07
okay, well i put in everything that he had in there and i'm still not working.

When I put it in it looked a little bit different, it wasn't as linear as what he posted, i suppose i'll try later, but i probably will just scratch it for now and start working on my wireless.

---

