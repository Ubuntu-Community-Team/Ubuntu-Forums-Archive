---
title: "Using Ubuntu as File Server... need some help..."
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by pnogoy on 2008-01-28
I'm currently using Ubuntu Linux as File server in the office... and I did a simple set-up where 4 Hard.disk come along together...

Its like this...

Linux Format
**160**Gb
**160**Gb

Windows Format
**120**Gb
**40**Gb

somehow I forgot what I did before since I lost my copy of the codes in Terminal...

I just want to ask... How can I check each and every hard drive that is in my File Server? What are the possible terminal codes that I can use?

Thank in advance...

---

### Post by brettg on 2008-01-28
Try; 

df -h

---

### Post by bodhi.zazen on 2008-01-28
you can use :

sudo fdisk -l

to list your HD

mount

to show what is mounted

and 

sudo less /etc/fstab

to see your config file

---

### Post by pnogoy on 2008-01-28
@ brettg and bodhi.zazen

Great Help... I'll try it now...

---

