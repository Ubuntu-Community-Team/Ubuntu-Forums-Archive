---
title: "Safe to unplug unmounted but spinning drive?"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by Jittoku on 2007-11-01
I'm wrestling with that common problem of unmounting/ejecting external USB HDDs.  I've read a lot of posts about it, and I've got a few more things to try.  (Any tried & true fixes yet?)  For right now, I'd just like to know, if I umount the disk at the CL, and it's gone from /media, but it's still spinning, is it safe to unplug it?  
Thanks!

---

### Post by Pumalite on 2007-11-01
If you have unmounted it and have all windows closed, you are OK.

---

### Post by defrex on 2007-11-01
The short answer is no. If it's still spinning, there could still be a problem. Though you should note: a drive being read can be turned off with no issues, It's only writing that can cause a problem.

edit: I said no because spinning but unmounted is very suspicious, and there could be something out of the ordinary going on.

---

### Post by Jittoku on 2007-11-01
I've just been able to unmount the drive from the desktop for the very first time, so I'm feeling cautiously optimistic.   
I used the following fix given by evilc on another thread:

sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /usr/share/hal/fdi/policy/10osvendor/storage-policy.fdi.bak

I don't understand it, but it worked.  But the drive still spins for a few minutes after unmounting.  I guess I can afford to wait.  

Thanks for your replies!

---

### Post by defrex on 2007-11-01
For the sake of education: *sudo* gives the command root (administrator) privileges. *mv* stands for move: cut & paste, but in one command. And I'm not sure exactly what the file does, but it's taking a file and moving it to it's current location and name plus ".bak". Essentially deleting it, but leaving a backup in case you need it again later.

---

### Post by Sir_Sid on 2007-11-01
The drive wont turn off immeidatly after being unmounted. It will keep spinning for 5 minutes or whatever the default idle time is on the drive. All my external harddrives do that. As long as it is unmounted it should be alright to unplug. If you remove the power, the heads will automatically snap back into their docks so there is no need to worry about physically damaging the drives.

---

### Post by Jittoku on 2007-11-02
Thanks, Sir_Sid, that makes it a lot clearer.  

And thanks, defrex - the sudo and mv I understand, but if moving it to the new name must be hiding it, what must the file have been doing before?  Deliberately preventing unmounting from Gnome?

---

