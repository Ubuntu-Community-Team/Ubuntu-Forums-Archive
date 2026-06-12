---
title: "Windows screwed up and won't boot. How do I restore it without reinstalling Ubuntu?"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by Amablue on 2006-07-06
That's my problem in a nutshell. I was running a disk cleanup utility and at the end it had me reboot, and then Windows just wouldn't start. 

I don't mind doing a full reinstallataion of Windows, but I've always heard that Windows should be installed first and Ubuntu second. I'm assuming that's because Windows will take over the boot-up and so GRUB won't get a chance to let me choose what to boot.

Is there a way to get GRUB on a disk or install it from windows so that I don't have to reinstall Ubuntu? Or if that's not the solution, is there anything else I can do?

---

### Post by nameiwantistaken on 2006-07-06
You are correct about the boot setup.  Windows will just install it self and not play well and it will re-install its own boot program.  You'll have to find a way to reinstall GRUB afterwards.  I'm sure someone on here can help but your suspicions are correct.

---

### Post by shoot2kill on 2006-07-06
yes, i did this...

i had to re-install GRUB using the live cd... if you decide to do this, i will find the notes i used and post them here

---

### Post by MaximB on 2006-07-06
no problem...reinstall winxp - if there is no other way for you (like restore or if you have backups)
then run the ubuntu live cd - there is an option there to reinstall GRUB...

---

### Post by ajgreeny on 2006-07-06
You can also follow this note I put together a while ago

---

### Post by Katryx on 2006-07-06
Try [this](http://en.opensuse.org/SDB:Uninstalling_the_Boot_Manager_GRUB_from_the_MBR)?  I'm not completely sure if it relates to your problem, but I once had a problem with Windows being unable to boot after the drive containing Linux died.  That link helped me to fix it.

EDIT: Upon re-reading your post several times, I'm pretty sure my reply is entirely unhelpful... :???:

---

