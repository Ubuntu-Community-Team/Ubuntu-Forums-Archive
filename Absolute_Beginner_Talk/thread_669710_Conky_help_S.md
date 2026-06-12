---
title: "Conky help :S"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by Fraser from Scotland on 2008-01-16
I installed conky using sudo apt-get install conky  but i don't know how to start it or set it up. Can some help?

---

### Post by SOULRiDER on 2008-01-16
You need a configuration file (.conkyrc) and ance you have it you gotta press alt + f2 and type conky to run it.

Here are different config files from people in the forums:
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by mandrill on 2008-01-16
Best I can do is the sourceforge page with a link to the man page

[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

---

### Post by Fraser from Scotland on 2008-01-16
how do i get the .conkyrc file? Is there a guide you could point me towards? 
Thanks/.

---

### Post by SOULRiDER on 2008-01-16
Check out the link i Posted, lots of people posted theirs there.
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

You could modify them to make a config that suits your needs.

---

### Post by Fraser from Scotland on 2008-01-16
Ok, I found the .conkyrc I want but how do I configure conky to run that .conkyrc instead of the default one?

---

### Post by SOULRiDER on 2008-01-16
Place it in your home overwriting the old one and restart conky. Kill it first with
```
 killall conky
```
and then open it again as you did it before.

---

### Post by Fraser from Scotland on 2008-01-16
Ok, I don't think i did it right at all, I pasted it into a text file and put it into my home folder. That didn't work and it doesn't seem right to be honest. Sorry, I'm totally new to Ubuntu.

---

### Post by voteforpedro36 on 2008-01-16
Is the text file named .conkyrc in your home folder?

---

### Post by Fraser from Scotland on 2008-01-16
no its not, there isn't a .conkyrc file already there which is weird i think. Isn't there meant to be one?

---

### Post by p_quarles on 2008-01-16
Running this command will get you the example configuration included with conky:
```
$ zcat /usr/share/doc/conky/examples/conkyrc.sample.gz > ~/.conkyrc
```
It's a good place to start.

---

### Post by Fraser from Scotland on 2008-01-16
I just figured out the .conkyrc file is hidden, so i tried putting pastig it in but when i ran conky it was messed up. I'll try again.

---

