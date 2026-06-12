---
title: "[SOLVED] Xubuntu Abiword file save probelm"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by staib on 2007-10-21
Hi all,

Just had a call for help from my son, who is up in Leeds, running Xubuntu on his laptop for the first time.  He has written his first essay using Abiword, but now finds that he can't 'save as' anywhere - either on his desktop or in his work folder. He gets an error message to the effect that whichever directory he chooses is 'write protected'.

I suspect this is more of a permissions thing than something specific to Abiword or Xubuntu or Xfce.

If anyone can give us some ideas to either save this piece of work or change his folder so he can save to it we would be **very **appreciative.

Cheers,

Nick

---

### Post by spin2cool on 2007-10-21
1) make sure that he owns the directory that he's trying to save it into.  If his username is 'asdf', then do

> ls -l /home
and make sure that the 'asdf' directory is owned by asdf. It'll look something like this, with the first two instances of 'asdf' being the owner and the group.

drwxr-xr-x 83 asdf asdf 4096 2007-10-21 13:32 asdf

if the first two are not his username, use this command to own the directory

>chown asdf:asdf /home/asdf

also make sure that the directory is properly readable/writable

>chmod u+rwx /home/asdf

---

### Post by staib on 2007-10-21
Thanks spin2cool - that sounds like it will do the trick.  I'll let my son know in the morning and if it works mark this thread as solved.  I really appreciate your help!    Nick

---

### Post by staib on 2007-10-24
Thanks again.  Finally had confirmation from my son that he can save his documents after he ran the:

chmod u+rwx /home/asdf 

Thread has now been marked as solved :)

---

