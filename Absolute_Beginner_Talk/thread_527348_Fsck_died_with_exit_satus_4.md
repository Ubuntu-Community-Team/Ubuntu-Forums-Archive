---
title: "Fsck died with exit satus 4"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by urk_nono on 2007-08-16
I've looked at the other threads with almost the same problem, and all I could get out from them that my UUID is wrong? I'm still quite new in using Ubuntu, so please be patient with me. I can't access ubuntu so I had to do it in command (if that's the name for the linux-command?) 

blkid:

[IMG]http://img522.imageshack.us/img522/5620/ubuntu1dc3.jpg[/IMG]


cat /etc/fstab:

[IMG]http://img167.imageshack.us/img167/7233/ubuntu2me5.jpg[/IMG]


Is it even possible for me to change the UUID now when I can't boot? I'm cow at sea here.. :confused:

---

### Post by philinux on 2007-08-16
Error 4 means 
 4    - File system errors left uncorrected

I'm pretty sure if you boot up to the point where it dies and leaves you with the command prompt.

Then you need to type in fsck -v this will then ask you if you want to correct the errors.

Answer yes. ( the switch -v means be verbose)

I've fixed mine twice this way. And I'm posting this from my linux box to prove it. :lolflag:

---

### Post by urk_nono on 2007-08-17
It worked! Some files were deleted, but seems most is OK! Thanks a lot! :)

---

