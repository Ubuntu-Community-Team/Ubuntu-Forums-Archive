---
title: "Netgear router problems...can't even see other windoze machine,"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by Znort_Ubern00b on 2008-03-03
Having problems...trying to set up samba but I can't even share between the two windoze machines.

1 x vista, 1 x XP
I can ping them from the router but not machine to machine.

Anyone able to offer some insight into this??

Cheers in advance
Znort

---

### Post by Znort_Ubern00b on 2008-03-03
bump .... :)

---

### Post by Vitamin-Carrot on 2008-03-03
check you windows firewall and system logs under admin tools in control panel

see if there are any alerts.

when trying to access windowz shares frpoom your ubuntu machine use
smb://

I think thats right.

---

### Post by zerhacke on 2008-03-03
Vista has two CIFS problems.. one, the firewall doesn't allow for it by default.  Two, it requires usernames and passwords by default for any share.

I'm sure the Windows forum will be glad to help you with your problems, as I cannot.

---

### Post by Znort_Ubern00b on 2008-03-04
> **zerhacke said:**
> Vista has two CIFS problems.. one, the firewall doesn't allow for it by default.  Two, it requires usernames and passwords by default for any share.

I'm sure the Windows forum will be glad to help you with your problems, as I cannot.


Thanks for that (sarcasm included on your part was noted) but this also affects my ubuntu machine as I cannot ping from that to the Windoze machine either even though they connect to same router and I'm wondering if this is why I have never been able to get samba to work on my network. I was more wondering if anyone else used netgear router or knew of anyone who may have experienced this problem.

---

### Post by zerhacke on 2008-03-04
What sarcasm?

---

### Post by Znort_Ubern00b on 2008-03-04
Because I am not sure how windows forum would be able to help me set up samba...which I did state in my original post.

My main problem is not even being able to ping any of the other pcs from anyone of them...ubuntu to winxp etc...but i can ping from router to each one.surely if they connect to same router they should be able to ping each other???

---

### Post by zerhacke on 2008-03-04
And like you said in your opening post you can't ping between Windows computers or from the Ubuntu one.  This is a Windows problem, not a Ubuntu problem.

Like *I* said in my first post, it has to do with the ultra restrictive Vista firewall.  And as such, you should seek help in a Windows forum.  Wouldn't you know it, this forum has a Windows section.  Go there.

---

