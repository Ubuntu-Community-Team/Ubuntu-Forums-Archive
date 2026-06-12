---
title: "External HD sharing issue"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by lionround on 2007-10-08
First of all, thanks to all of the people on this forum who have helped me thus far.  I have actually managed to get an unsupported PCMCIA wireless card working with NDISwrapper working.  Hurray!!

My current issue is as follows:  

I have an external USB 2.0 HD that auto mounts at /media/LACIE (it is a Lacie HD.)  It is fat32 FS, 250 gig.  I have it shared SMB as Lacie and can SEE it through my WinXP machines.  However, whenever I try to ACCESS it through one of my XP machines, I  get the error message that \\Ubuntu\LACIE is not accessible. 

I want to be able to share media to/from that drive with my XP/98 machines.

Any suggestions??

---

### Post by lionround on 2007-10-08
bump bump

---

### Post by lionround on 2007-10-08
bump again.  Any help out there?

---

### Post by om1 on 2007-10-08
can you see the Ubuntu machine in mynetwork places from your XP machine??
also have you set up Ubuntu to be on the same workgroup as your XP/98 machines?

---

### Post by freesitebuilder on 2007-10-08
I used Linux Reader [http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/) in XP to read my Ubuntu hard drive. Haven't tried to read an external HDD with it though.

---

### Post by lionround on 2007-10-08
> **om1 said:**
> can you see the Ubuntu machine in mynetwork places from your XP machine??
also have you set up Ubuntu to be on the same workgroup as your XP/98 machines?

Yes, I can see the Ubuntu machine and I can see the Lacie HD, but when I click on it, it tells me that it is inaccessible.

Yes, they are all set to MSHOME.

---

### Post by om1 on 2007-10-08
have you set the permissions on the hard drive to be read by anyone?

---

### Post by lionround on 2007-10-08
When I right click on Properties, I am the owner with all permissions.  It is in the root group.  However, I CANNOT allow other users either write or read permissions.

When I click on one of the other options, it resets to None.

---

### Post by lionround on 2007-10-08
bump again

---

### Post by om1 on 2007-10-08
ok to be able to change permissions you will need to run this command in terminal
```
gksudo nautilus
```
that will give you the file browser with root privileges
then set read to everyone..... you might want to give write to everyone... all though it will not be secure but i'm not to familiar with how to do that any other way at this time

---

### Post by lionround on 2007-10-08
I pasted that into terminal and it opened up the files window.  When I went to /media/LACIE it did the same thing.  I tried to give permissions to others and it resets back to NONE when I close.

So I logged in as root sudo -s -H and tried it again.  Same result.

---

### Post by lionround on 2007-10-08
bump

---

### Post by om1 on 2007-10-08
im at a loss... sorry i couldnt help... if your not in a big hurry somebody here should be able to help you

---

### Post by Mr.Beast on 2007-10-08
Can't help you directly, but perhaps it's the in built firewall blocking the SMB ports.
I don't know that much about the firewall operations or if it's intelligent (or dumb!, depending on how paranoid you are) enough to open up the ports required for allowing your XP workstations access to the lacie device you have shared.

Hope this helps and this may help steer someone to a more meaningful post.

---

