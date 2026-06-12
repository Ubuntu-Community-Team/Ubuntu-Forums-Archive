---
title: "Trouble installing Java"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by enzeru on 2007-09-27
ok I installed java in my browser but it wasn't working to launch a web application, they directed me to a guide to installing it and stupidly i went right into the guide and did not delete the old install.  About halfway through the install it gives me an error about multiple repositories and tells me to run "apt-get update" to fix it.  But when i run apt and update I get the following error:

> 
me@computer:~$ sudo apt-get update
Password:
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory


Any help with this would be appreciated, I dunno if just pulling up my sources list and looking for new ones will work.  Wanted to check on here before I did anything else stupid.

---

### Post by mysticmatrix on 2007-09-28
Can you please post output of 

```
cat /etc/apt/sources.list
```

---

### Post by enzeru on 2007-10-01
Attached a copy of the file

---

### Post by Perfect Storm on 2007-10-01
Do you have synaptic or Add/remove open while doing this?

---

### Post by enzeru on 2007-10-01
No I don't,  i got this error and restarted to see if that would help but it still gives me the eroor even after a full restart and first thing I do try to update

---

### Post by Perfect Storm on 2007-10-01
Well, try make a new list then; [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

```
sudo nano /etc/apt/sources.list
```

When done. (You might want to check/reading about KEY in the new sourcelist and how to add them - mostly for unofficial sources).

```
sudo aptitude update && sudo aptitude upgrade
```

---

