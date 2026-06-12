---
title: "Question About gparted"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by Dispatch on 2008-03-02
I'm at friends house right now who is also trying to install ubuntu so if you've been helping me out don't be confused by this :)

Last night he made a a 30GB partition and then he had to go to sleep.  When he came back in the morning the 30GB partition that was his G: drive seemed to have disappeared.  I brought over my gparted live cd and it recognized the partition he made as an "extended filesystem" and then there were 30GB of unallocated space.  I changed the that space into an ext3 partition and saved it and when I went to shut down it's been sitting at "Remounting remaining filesystems read only" for a long time now (15 minutes).  Is this normal?  Will ctrl+alt+backspace shut it down or is that not a good idea.

P.S. Sorry for the long-ish story.:(

---

### Post by Mazza558 on 2008-03-02
It sounds like when he created the 30GB partition, something went wrong somewhere. I'm also wondering why it'd try and remount a drive whilst shutting down.

---

### Post by Dispatch on 2008-03-02
Yeah, he said he thought he might have done something wrong when he made the partition.  Should I go ahead and try CTRL+ALT-Backspace?  Will that shut it down?

---

### Post by Mazza558 on 2008-03-02
> **Dispatch said:**
> Yeah, he said he thought he might have done something wrong when he made the partition.  Should I go ahead and try CTRL+ALT-Backspace?  Will that shut it down?

I wouldn't risk it yet. Give it a few more minutes and if nothing else is happening, give it a go.

---

### Post by glennric on 2008-03-02
Remounting the drives read-only when shuting down is standard procedure.  The drives are synced and unmounted, and then remounted read-only so that linux can still access shutdown functions on the drive, but modifications can not be made.  This would cause errors on the disk upon reboot.  

To get your computer to shut down you could try the magic system requests.  Ctrl-Alt-Backspace won't work at this point as the x-server has already been shut down.

---

### Post by Dispatch on 2008-03-02
Okay, but Magic System Requests? :confused:  We're both pretty new to Linux.

---

### Post by justleen on 2008-03-02
> **Dispatch said:**
> Okay, but Magic System Requests? :confused:  We're both pretty new to Linux.

System Request are a " backdoor"  to you system.

have a look at this [link]("http://http://www.cyberciti.biz/tips/reboot-or-halt-linux-system-in-emergency.html")

Raising Skinny Elephants Is Utterly Boring ;)

---

### Post by Dispatch on 2008-03-02
Okay, I'm just gonna man up and go with the flow and see what happens.  :)

---

