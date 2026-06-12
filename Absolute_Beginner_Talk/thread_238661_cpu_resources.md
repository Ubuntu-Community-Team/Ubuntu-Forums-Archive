---
title: "cpu resources"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by PBeck929 on 2006-08-18
Hello all,
   For some reason, my computer is running slow, so I went to system monitor and it said that my dual core cpu is running at 100% on both cpu's... can somebody tell me why it is doing this and how to fix it?  Thanks.

---

### Post by croak77 on 2006-08-18
Is your computer always slow? Or just this time? There might be a process going on in the background, beagle indexing, updating locate db, etc.

---

### Post by Frank Golden on 2006-08-18
> **PBeck929 said:**
> Hello all,
   For some reason, my computer is running slow, so I went to system monitor and it said that my dual core cpu is running at 100% on both cpu's... can somebody tell me why it is doing this and how to fix it?  Thanks.
Under processes in system monitor what process is listed as using100%?

---

### Post by PBeck929 on 2006-08-18
It's just this time and when I go into processes, there is no single process taking up 100% of the resources, but it's multiple processes with the same name, "gnash", that are running and the only processes taking up any percentage of resources...

---

### Post by croak77 on 2006-08-18
> **PBeck929 said:**
> It's just this time and when I go into processes, there is no single process taking up 100% of the resources, but it's multiple processes with the same name, "gnash", that are running and the only processes taking up any percentage of resources...

I would say if you don't need gnash, GNU flash player, kill it. Also check what 'top' says from a terminal.

---

### Post by PBeck929 on 2006-08-19
Ok, so I've narrowed it down to it being the process Gnash and it only affects my resources when I go to myspace.com... and I thought that there would only be one Gnash process running, but instead there are like 15 Gnash processes running at once... anymore info on this would be great...

---

### Post by croak77 on 2006-08-19
[http://savannah.gnu.org/bugs/?func=detailitem&item_id=16779](http://savannah.gnu.org/bugs/?func=detailitem&item_id=16779)

Loks like A Gnash bug.

---

