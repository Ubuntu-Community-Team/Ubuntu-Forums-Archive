---
title: "Grub: Error 22"
date: 2005-10-10
forum: Absolute Beginner Talk
---

### Post by PlayWithFire on 2005-10-10
I'll start of by admiting that i am idiot :???: 

I really want to learn linux, and that's why i installed Ubuntu. It worked really well, and i've used it a few times, but never really got into is much as i want because of school

I was running out of space on my HD so i decided to get rid of ubuntu until i can get a second HD. Well, the way i chose to do it, was really stupid. I just used partition magic and deleted the partition ubuntu was sitting on. Well, it worked, i merged the unpartitoned space on my Win XP partition, and continued using the PC. Well, time came, and i rebooted it, and i am getting an error 22 when grub is loading. 

Now, i know that's happening because grub is looking for a partition that doesn't exist, and i have no idea how to fix it. 

A good thing is that i have a live CD, so i can still use the web (that's how this post is being made). I would really appreciate any help you can provide me. I just want to get XP working again. 

Again, pardon my newbishness

---

### Post by SilentCacophony on 2005-10-10
Hello. If I gather the facts correctly, you now only have Windows XP on the drive, and you've orphaned grub stage 1 (in the MBR) by deleting the linux partition which held the /boot/grub/menu.lst. Not an uncommon occurance, really. ;)

If that's the case, you probably want to install the standard Windows MBR. I just ran across a good post for doing that, though there are other ways as well. Look for the reply by **Lord Illidan** in this thread:

[http://ubuntuforums.org/showthread.php?t=73921](http://ubuntuforums.org/showthread.php?t=73921)

---

### Post by PlayWithFire on 2005-10-10
thank you! :p 
this post is being made on XP

i'll be more careful next time :rolleyes:

---

### Post by SilentCacophony on 2005-10-10
No problem. :) Just remember that grub will generally try to load it's stage 2 from the last linux partition installed.

---

### Post by albertoramirez on 2005-10-11
No one's an idiot...

The one who doesn't know, and does know that he/she doesn't know, is an ignorant (just like me), and must be helped.

The one who doesn't know, and doesn't know that he/she doesn't know, usually  is a disaster maker, so keep him/her away from computers...

---

