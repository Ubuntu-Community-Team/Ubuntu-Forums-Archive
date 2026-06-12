---
title: "KANOTIX on usb stick"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by microsoft92sucks on 2007-08-18
This may not be an Ubuntu problem but it is debain Linux based os problem.
I'm trying to put KANTOIX on a usb stick to boot off of and I'm using this how to.
[http://biohackery.com/node/4#start](http://biohackery.com/node/4#start)
but on part 6 of it I cant get sda1 to mount in /dev/ it keeps mounting in /media/.
So when I try to make a home dir it only lets me choose /dev/hdb1 /dev/hda1 /dev/sda1 /dev/sda2 and I choose /dev/sda1 becouse thats where I want it to go it says theres 0 room left But there 100mb there It's just not mounted right.
So my question is how do I mount it in /dev/
By the way its showing up on the desktop as "800M Removable Media"
And yes Im a Ubuntu user but thought KANOTIX would be better for this.
Thanks for any help

---

### Post by microsoft92sucks on 2007-08-18
Any Help Please!!!

---

### Post by sourjax on 2007-08-18
I'd suggest using:

/media/sd**

It appears that's what he meant when he wrote it. I could be wring, its happened before... Once. :lolflag:

---

### Post by microsoft92sucks on 2007-08-19
The proggram to make the home dir wont let me choose /media/sda1

---

### Post by llamakc on 2007-08-19
You don't mount in /dev/. The how-to is not telling you to do that.

Is the stick full? What's the output of 

fdisk -l /dev/sda

and

df -h

---

