---
title: "Windows XP in Ubuntu Dapper"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by arijarot on 2006-09-07
Is it possible to run windows which is installed on one partition of the hard drive while using Ubuntu which is installed on another partition of the same hard drive? 
if i want to run a program which is on the windows partition (the program won't work in wine so it needs the entire xp os) i want to be keep using ubuntu with access to the app on xp.

does this make sense?

---

### Post by bluefrog on 2006-09-08
not possible. basically, you are asking (to rephrase it and show you the flaw) to run win98 _while_ running XP. It's one or the other not both at the same time.

Now you can overtake the problem by using vmware-player inside Ubuntu to run a winXP image.

James

---

### Post by arijarot on 2006-09-08
> **bluefrog said:**
> not possible. basically, you are asking (to rephrase it and show you the flaw) to run win98 _while_ running XP. It's one or the other not both at the same time.

Now you can overtake the problem by using vmware-player inside Ubuntu to run a winXP image.

James

oh ... does that mean from a cd and you can't save settings and data then?

---

### Post by aeiah on 2006-09-08
you can save the data yea. vmware works like a virtual pc, with its own virtual harddrive. however, if you're wanting to use this data within ubuntu or within your normal win xp partition you'd be best saving it in a partition that both windows and linux can read. because your vmware winxp is a virtual machine, you have to connect to that partition using samba. it'd be treated like it's a harddrive on a network.

there are good clear howtos for that sorta thing on the forum. i got it running with no problems.

but first things first, are you sure you cant use a linux alternative program?

---

### Post by arijarot on 2006-09-08
> **aeiah said:**
> you can save the data yea. vmware works like a virtual pc, with its own virtual harddrive. however, if you're wanting to use this data within ubuntu or within your normal win xp partition you'd be best saving it in a partition that both windows and linux can read. because your vmware winxp is a virtual machine, you have to connect to that partition using samba. it'd be treated like it's a harddrive on a network.

there are good clear howtos for that sorta thing on the forum. i got it running with no problems.

but first things first, are you sure you cant use a linux alternative program?

yeah i just came across a vmware howto ([http://ubuntuforums.org/showthread.php?t=183209&highlight=run+windows+ubuntu](http://ubuntuforums.org/showthread.php?t=183209&highlight=run+windows+ubuntu))

i wish i could use a linux alt, but sadly i can't :-| 

thanks for the advice guys:)

---

