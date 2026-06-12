---
title: "clamAV Unable to view ClamAv's information file"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by OldNewb on 2008-02-26
I installed clamAV from synaptic and at first it gave me a hard time updating [needed to run as root to update] After I learned how to do that I ran the program and found this error message waiting for me 

Unable to view clamAV's information file 

I tried to do the update but was told unable to retrive updates try again later.

Please help I am floundering.

---

### Post by OldNewb on 2008-02-26
...bump...

---

### Post by julian67 on 2008-02-26
> **OldNewb said:**
> I installed clamAV from synaptic and at first it gave me a hard time updating [needed to run as root to update] After I learned how to do that I ran the program and found this error message waiting for me 

Unable to view clamAV's information file 

I tried to do the update but was told unable to retrive updates try again later.

Please help I am floundering.

Possibly you need to run clamAV with root privileges, sounds like the information file is readable only by root and you're launching clamAV as user.  

But unless you're running a mail server or cleaning up drives you share with *unprotected* Windows PCs on your network the easiest solution is simply to uninstall clamAV, it serves no purpose on Linux desktops (unless placebo effect counts as a benefit).

---

### Post by OldNewb on 2008-02-26
I received that error running it both as a normal user and root, and yes I have been told it is pretty much unneeded but hey aren't there like 4 viruses out there for Linux?

---

### Post by Oldsoldier2003 on 2008-02-26
> **OldNewb said:**
> I received that error running it both as a normal user and root, and yes I have been told it is pretty much unneeded but hey aren't there like 4 viruses out there for Linux?

The thing is that for the most part in order for a virus to do anything more than trash your user it would have to be executed as Root. ClamAv is mostly there to protect your windows users from an infected file through email,ftp samba share whatever. Granted there are cases where you could possibly get a linux based virus, but safe computing practices will cage it to the local users profile. Unlike in windows where most everything operates as a privileged user process.

---

