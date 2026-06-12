---
title: "How to get out of Live CD"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by jfh on 2005-12-13
Before embarassing myself by asking this question, I looked through several threads in this forum, but nobady seems to have had this problem (or else they are ashamed to admit it).  I got the Ubuntu CDs from Shipit (thanks), and decided I would boot from the Live CD before installing it.  It booted fine, and I have tooled around in Ubuntu several times - and enjoyed it.  As soon as I figure out how to partition my hard drive, I'm sure I will install it (or try to).  In the meantime, however, I do have this small problem - after I have booted from the Live CD and expored Unbuntu, how do I then get out of it?  So far, the only way I have managed to exit the CD is to unplug my computer.  I hope somebody can help before I throw my back out crawling around to get to that plug.

---

### Post by 23meg on 2005-12-13
Can't you restart your computer with System / Log Out? If that doesn't work, try typing ```
sudo shutdown -r now
``` at the command line.

---

### Post by Gandalf on 2005-12-13
[QUOTE=23meg]Can't you restart your computer with System / Log Out? If that doesn't work, try typing ```
sudo shutdown -r now
``` at the command line.[/QUOTE]
i dont recommand -r option, i advise using -h one

```

sudo shutdown -h now

```

---

### Post by 23meg on 2005-12-13
[QUOTE=Gandalf]i dont recommand -r option, i advise using -h one

```

sudo shutdown -h now

```[/QUOTE]
Why not? -r will reboot, whereas -h will halt, that's the difference.

---

### Post by Gandalf on 2005-12-13
[QUOTE=23meg]Why not? -r will reboot, whereas -h will halt, that's the difference.[/QUOTE]
Oh my! oops i mixed up -r with -f :oops:

sorry yea youre right 23meg :oops: i donno why i thought of -f lol

---

### Post by jfh on 2005-12-14
Thanks, 23 meg and Gandalf. Only problem is - where do I find the "System Log Out" button or whatever.  And where do I type in the commands in the command line?  I assume you mean like the old DOS commands - but how do I bring up the box into which to type the commands? jfh

---

### Post by Mr. Electric Wizard on 2005-12-14
It is on the top Gnome Panel.
select:
System --> Log Out (at the bottom)

---

### Post by 23meg on 2005-12-14
> And where do I type in the commands in the command line? I assume you mean like the old DOS commands - but how do I bring up the box into which to type the commands?Hit Applications / Accessories / Terminal in the Gnome panel.

---

