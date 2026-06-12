---
title: "NFS Help"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by nonpareilpearl on 2008-02-15
I am currently using Feisty on my desktop, which is also the computer I am using for a Linux class I am taking. The professor told me I wouldn't have to reformat/repartition everything so long as I could complete the Red Hat/Fedora assignments on Ubuntu. So far I have been able to do all of this without difficulty, but we are currently supposed to configure our home directories as an exported NFS filesystem and set it up to be accessible from our main machine (i.e. the computer that the home directory is located on). I sent him an email that I was receiving a blank when I tried running "showmount", but he recommended that I check my exports file and I can see nothing wrong with it. So I include the results below, note that I am behind a router if that matters.

In /etc/exports (only one line modification):
/home/myusername 192.168.1.100(rw,async)

In /etc/hosts.allow:
portmap : 127.0.0.1
portmap : 127.0.1.1
portmap : 192.168.1.100

In /etc/hosts.deny:
ALL: PARANOID
portmap: ALL


Also, I tried using the instructions on the following post but to no avail:
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

Help?

---

### Post by Sam Lars on 2008-02-15
What do you get when you try to access it?  What's not working?

---

### Post by nonpareilpearl on 2008-02-15
When I enter "showmount", all it outputs is:
me@Phoenix:~$ showmount
Hosts on Phoenix:


(basically it is just blank - I am assuming this is incorrect, as my prof. did ask me to check the exports files as mentioned)

---

### Post by Sam Lars on 2008-02-15
I think that shows who is connected/mounted to your shares.  If no one is accessing them, then shouldn't it be blank?

---

### Post by nonpareilpearl on 2008-02-15
That makes sense, but the fact he told me to check my exports file made me think that something is missing. That's why I posted the contents of the file(s), to see if someone else could see something wrong. If it looks ok to you, I'll just fly with it I suppose :)

---

### Post by kaginken on 2008-02-15
I believe the command to show your exported shares is:

showmount -e

Does that show your share?  Seems like everything else looks okay...

---

### Post by nonpareilpearl on 2008-02-15
It does show the share, and the fact that I'm retarded, ha. Thank you :)

---

