---
title: "Mounting NTFS partation"
date: 2006-09-18
forum: Assistive Technology &amp; Accessibility
---

### Post by Sharath on 2006-09-18
I am using Live CD Version 5.10.

I am able to mount c: which is NTFS partition, I can access any data on c:, but the Problem is Ubuntu mounts C: with only Read permissions.

Is there any way I can mount c: with write permission...:confused: 

I have tried to mount c: with '-w' options but of no use...:frown: 

can someone help me on this...

---

### Post by madmetal on 2006-09-18
linux doesn't still have full and reliable suppport for ntfs disks..
there are ways to read and write at a ntfs partition but it is not safe for your data and not recommended.

---

### Post by Sharath on 2006-09-18
Can u let me know of these ways...???

---

### Post by madmetal on 2006-09-18
try this one 
[http://www.ubuntuforums.org/showthread.php?t=217009&highlight=write+ntfs+support](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=write+ntfs+support)
but still under some risk..
i hope it works great with no problems!

---

### Post by Sharath on 2006-09-18
Thax, I will try it out....

---

### Post by niteblind on 2006-09-19
I am having the same issue with a USB external hard drice. This thing I cannot get my head around is that I can share to the C:\ on both my windows XP machine but not to the external hard drive.

This seems odd to me being that i can do it to the other NTFS shares on the network. Any one got any ideas why this would be?

niteblind

---

### Post by ecksit on 2006-09-22
Thanks. I was having the same problem with my external harddrive. I could read it, but couldn't write to it. Now it all works. I think i should still back up and convert to vfat just to be safe.

---

