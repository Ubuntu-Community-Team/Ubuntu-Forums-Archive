---
title: "Does synaptic make a log file?"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by aosmith on 2006-12-16
Hey guys (and Gals)--
I deleted a lib by mistake last night... At any rate i dont think my dns is working now so i need some help on this one.  Does synaptic make a log file of changes?  Can someone point me in the direction of what packages i should have?  Running edgy on i386

---

### Post by bodhi.zazen on 2006-12-16
Not that I know of

Try /var/log/dpkg.log

Should list all changes .....

In synaptic there is a

File -> History, but I do not know if it saves information between sessions.

Also there is an undo button, but again I do not know if it saves information between sessions.

---

### Post by aosmith on 2006-12-16
the problem actually appears to be with dhcp... In syslog im not getting any dhcp offers... i know other ocmputers on the network are working any ideas?

---

### Post by bodhi.zazen on 2006-12-16
> **aosmith said:**
> the problem actually appears to be with dhcp... In syslog im not getting any dhcp offers... i know other ocmputers on the network are working any ideas?

Are you getting any error messages? Type of internet connection?

What happens with:```
sudo ifdown eth0
sudo ifup eth0
sudo ifconfig
```

---

### Post by aosmith on 2006-12-16
scratch this whole thread... didn't check the simple things first.  The wireless router go unplugged (i'm sure everyone will blame the dog for it)

---

