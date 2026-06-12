---
title: "No Internet"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by shoot2kill on 2006-06-27
i have been using kbuntu for a few weeks now, and works fine....

today i loaded kbuntu and the internet would not work... also, none of the network was working, i tried connecting to my router at 192.168.1.1 and it wouldnt load...

i do not know anything about ubuntu and networking as when i first loaded ubuntu it worked from out of the box, and i have not modified anything.. 

my NIC and Cable is fine, as i am on same box now but in XP.... (dual boot)

---

### Post by shoot2kill on 2006-06-27
[QUOTE=shoot2kill]i have been using kbuntu for a few weeks now, and works fine....

today i loaded kbuntu and the internet would not work... also, none of the network was working, i tried connecting to my router at 192.168.1.1 and it wouldnt load...

i do not know anything about ubuntu and networking as when i first loaded ubuntu it worked from out of the box, and i have not modified anything.. 

my NIC and Cable is fine, as i am on same box now but in XP.... (dual boot)[/QUOTE]

any help.. PLEASE

---

### Post by Brunellus on 2006-06-27
execute teh following:

sudo ifdown eth0

sudo ifup eth0

---

### Post by Apple 101 on 2006-06-27
If that deactivation, activation process works, then the problem is definitely is a bug.  You'll be one of many users to come across it.

---

### Post by wych77 on 2006-06-27
I'm having something of the same issue.  I did what you wrote for terminal procedures, however, I still can't connect to any site other than the ubuntu forums.  I  can hit the net just fine on my XP side though.  Any help?

---

### Post by dmizer on 2006-06-27
[QUOTE=wych77]I'm having something of the same issue.  I did what you wrote for terminal procedures, however, I still can't connect to any site other than the ubuntu forums.  I  can hit the net just fine on my XP side though.  Any help?[/QUOTE]
you can browse around the ubuntu forums with no problem, but nowhere else?

if that's the case, you should probably post a new thread of your own, because that's a different issue than here in this thread.

---

