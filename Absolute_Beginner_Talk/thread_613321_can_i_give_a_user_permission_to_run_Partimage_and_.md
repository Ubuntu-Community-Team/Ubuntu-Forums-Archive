---
title: "can i give a user permission to run Partimage and mount/umount drives?"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by ijason on 2007-11-14
i'm trying to give a normal user permissions to umount/mount drives, and to run Partimage so that i can run a script to do these things automatically without requiring them to enter the root password. is there a way to give a normal user permission to access these programs?

---

### Post by overdrank on 2007-11-14
> **ijason said:**
> i'm trying to give a normal user permissions to umount/mount drives, and to run Partimage so that i can run a script to do these things automatically without requiring them to enter the root password. is there a way to give a normal user permission to access these programs?

Hi your normal user uses sudo. :KS

---

### Post by Inxsible on 2007-11-14
you will have to run partimage when the drives are not mounted. So you would need to run from the LiveCD. none of your users exist in the LiveCD so you don't really need to do this.

unless I am completely off on what you are implying.

---

### Post by ijason on 2007-11-14
i need to be able to have my user run both the u/mount commands and Partimage without having to SU or SUDO. i'm trying to set up a sort of automated rescue option for someone who is computer illiterate. i'm running things through a script, and the script fails upon password prompting. 

unless there is a way to enter a password in a script?

---

### Post by Dr Small on 2007-11-14
This may be completely in left field, as to what you are trying to do, but here is my guide on how to allow certain commands to be run as "sudo" without having to type a password for sudo.

[http://php.8ez.com/drsmall/blog/?p=157](http://php.8ez.com/drsmall/blog/?p=157)

---

### Post by overdrank on 2007-11-14
> **Dr Small said:**
> This may be completely in left field, as to what you are trying to do, but here is my guide on how to allow certain commands to be run as "sudo" without having to type a password for sudo.

[http://php.8ez.com/drsmall/blog/?p=157](http://php.8ez.com/drsmall/blog/?p=157)

nice Dr small blog  :KS

---

### Post by Dr Small on 2007-11-14
> **overdrank said:**
> nice Dr small blog  :KS
Thanks, overdrank ;)
We seem to be all the time meeting up :p

---

### Post by ijason on 2007-11-14
i figured it out. a way to add user permissions for specific programs in the sudoers file. :)

thanks for the help!

---

