---
title: "New drive permissions"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by Wafdof on 2006-09-10
Hi, I've two ide HD's in the box, a new Ubuntu 6.06 install on hdb.  The second drive-- ironically hda--is formated fat32.  Initially I couldn't mount hda.

I modified the etc/fstab thus; 
/dev/hda1    /media/ralph   vfat  defaults   0   0  

additionally, I ran the following;  sudo chmod 777 /media/ralph

Now, using the ubuntu gui, ralph appears mounted, I can open it and look in it, but I can't copy a file TO it.  

Error message:  
Error while copying to "/media/ralph".
You do not have permissions to write to this folder.

I'm sure I'm missing something simple in setting the permissions, but short of doing a copy with a sudo command from the terminal, how do I get the permissions so I can copy to it in the gui?

Thanks a bunch,
John the Linux virgin...

---

### Post by jorn on 2006-09-10
The fstab-line about your fat-partition must look like this:
> /dev/hda1     /media/ralph     vfat     iocharset=utf8,umask=000     0       0
in order to make it work.
Try it and post back if it does't work.

---

### Post by Wafdof on 2006-09-10
Nope, that wasn't it.  It won't mount at all.  Again, I'm on the gui desktop:  /places/computer-file browser.

When I try to mount it from there I get this error message:

error: device /dev/hda1 is not removable
error: could not execute pmount

I'm wondering if  the chmod 777 I did orginally was in error?
Or, maybe, I need to reinstall making sure Ubuntu ends up on hda instead of hdb...

Thanx, john

---

### Post by Wafdof on 2006-09-10
Disrenevermind.  Pulled the fstab up again and somehow a bunch of stuff got knocked out o

---

### Post by Wafdof on 2006-09-10
Disrenevermind.  Pulled the fstab up again and somehow a bunch of stuff got knocked out of it.  (Everything but the swap disk, hdb5.)  Don't know how I did it but now I need to figure out how to rebuild it.  I'll check back in after I hack it back together....

Thanks, john

---

### Post by Wafdof on 2006-09-10
Okay.  Brain fart.  I left the darn CD in and it booted from that, so of courst the fstab was bolixed.  

Works fine with the mod you gave me, thanks a million.  

Thanks, John

---

### Post by Wafdof on 2006-09-10
And, what am I telling it with
iocharset=utf8,umask=000 0 0

If it's too complicated to explain, that's cool.  I'm sure I'll get to it eventually. 

Thanks again, John

---

