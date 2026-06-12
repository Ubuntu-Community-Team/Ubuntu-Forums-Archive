---
title: "nfs/webmin accident : can't access home folder"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by spynotebook on 2007-06-07
This morning, I was trying to set up a NFS export so that my MythTV could acess my iTunes library which is stored on my 7.04 fiesty box. I was doing this through webmin. I set one up and didn't like the way it looked so I checked it and chose to delete it. There were 3 or 4 items in my exports list which looked to be ones that were set up automatically. It didn't delete so I tried it again.

Around this point, I realized that webmin was not deleting the item I checked but rather some of the other ones. I think one was associated with the home directories.

I then noticed I could not open my home folder through nautilus.  I did a ctrl-alt-backspace and logged in using failsafe terminal and all my stuff is still there, but when I login as normal, my desktop items never come up.

It is as if I deleted my systems ability to see the home directories.

What did I do? Might I have erased something ELSE important? How do I fix it?

Any help appreciated.

---

### Post by sandwitch on 2007-06-07
do a ls -l /home/
does it look like this?
drwxr-xr-x 106 sandwitch   sandwitch   4096 2007-06-07 13:06 sandwitch 
watch the first colon
the "x"  makes it accessible

---

### Post by spynotebook on 2007-06-07
I have
drwxr-xr-x

That does not seem to be the problem. Is there something in NFS Exports that I could have messed up?

I have a 7.04 CD. Good idea or bad idea to attempt a reinstall?

---

### Post by sandwitch on 2007-06-08
Local access to a directory has nothing to do with nfs. So there must be another reason

---

