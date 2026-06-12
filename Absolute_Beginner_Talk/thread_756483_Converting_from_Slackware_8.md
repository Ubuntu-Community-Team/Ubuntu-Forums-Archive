---
title: "Converting from Slackware 8"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by xyloweb on 2008-04-15
I have a friend with Slackware 8 (three or four years old) that wants to convert to Ubuntu, but she is worried that she will lose data in the process.
I told her that we just need to copy "some things" onto her external drive, then install Ubuntu on her main drive, then copy those things back over from the external drive.

QUESTION: What are the things she needs to copy, and what is the (safe) process to copy them back.  (I don't want to clobber Ubuntu when restoring her old stuff.)

I'm thinking she needs to copy /home/ and maybe /usr/.
Anything else?  Is that enough?  Too much?

---

### Post by bwang on 2008-04-15
I think you shouldn't replace /usr and /home with the backups. There are various configuration files that most likely will not work if they are several years old.

---

### Post by xyloweb on 2008-04-16
OK, our plan at this point is to copy /home/ and /usr/ to the external drive, and copy them back as needed, not necessarily overwriting the (possibly) existing files.

I looked at this more last night and booted with an Ubuntu LiveCD.  It recognized the external drive, but would not allow me to view the files, saying I did not have the authority to do so.  I am wondering if she copied some files over as root, and that is why I couldn't view them.

Assuming she knows all the appropriate passwords, how can I access this drive through Ubuntu?
FYI: The main drive is formatted with reiserfs, and I think the external drive is also.

---

