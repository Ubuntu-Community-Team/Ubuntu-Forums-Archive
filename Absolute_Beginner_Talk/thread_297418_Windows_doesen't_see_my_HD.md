---
title: "Windows doesen't see my HD"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by Meysys on 2006-11-11
I've had a ubuntu dedicated laptop for about a week or two, but theres some programs that I need that don't work very well (or at at all) under wine. So I just departitioned 20gb of space from my ubuntu partition, but now when I boot from my windows disk, it'll load all its files, and then tell me I don't have a hard drive ](*,) ](*,) ](*,) ](*,) ](*,) 

Anybody know how to fix this?
I'm using Dapper if it makes any difference.

---

### Post by 3rdalbum on 2006-11-11
Is the new "departitioned" space formatted? It must be formatted as Fat32 or NTFS in order for the Windows installer to see it.

---

### Post by Meysys on 2006-11-11
Ah nuts, Yeah thats probrably why. It gave me the option to format it, but I was silly and didn't.
 I guess i'll do it tomorrow, for now sleep.

---

### Post by Meysys on 2006-11-11
So windows is installed now, I ended up reformating my entire HD, but it worked. However whenever I restarted windows it would try to run the scandisk on me. So I let it run, it restarted and now whenever I try to boot windows the screen blanks out on me while windows is loading. :neutral:  

This is making me a sad panda.

---

### Post by drtvasudevan on 2006-11-12
do you mean you reformatted, installed windows and it wont work now? teh linux is there or not?
you can dual boot. windows installed in a fat -32 partition and linux in a suitable -like reiserfs- partition.
if you have only installation of windows and it is not running the install has not gone on smoothly.

---

