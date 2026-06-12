---
title: "Root owns my desktop"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by sacedric on 2008-01-03
I think I messed up. As per the instructions under the Feisty section of this post, ([http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)), I ran the following command...
sudo rm -rfd ~/Desktop/usr

What have I done wrong? Since it now appears that root owns my desktop. Ho do I get control back?
Thanks
SACedric

---

### Post by mikewhatever on 2008-01-03
That command deletes a previously created directory from your desktop. Nothing's wrong with that. It is normal that root is the owner of the system. This is how it works in Linux. Read for more info [http://psychocats.net/ubuntu/permissions](http://psychocats.net/ubuntu/permissions)

---

### Post by chips24 on 2008-01-03
dont run any code with RM in it.

---

### Post by Xavieran on 2008-01-03
Run this command:
```
gksu nautilus /home
```
Go to your users home folder.Right click on Desktop and select properties then Permissions and change the owner to yourself

---

### Post by Xavieran on 2008-01-03
> **chips24 said:**
> dont run any code with RM in it.

You can run code with rm in it,as long as you know what it will be deleting...
Check this out for more info[http://http://ubuntuforums.org/announcement.php?f=73]("http://http://ubuntuforums.org/announcement.php?f=73")

---

### Post by sacedric on 2008-01-03
Thanks so much. Knowledge is a powerful thing...
Seems to be back to normal.

---

### Post by Xavieran on 2008-01-03
No problem.:)

That's what I'm here for.:)

---

### Post by Kzin on 2008-01-03
I am root!  Thats my desktop!  Ship it to me immediately. ;-) :lolflag:

---

### Post by Xavieran on 2008-01-03
Who's paying for postage? ;)

---

### Post by Kzin on 2008-01-03
> **Xavieran said:**
> Who's paying for postage? ;)

I suppose it would depend whats on the desktop... Or in this case, what the desktop is on.  I'll pay.  No facsimiles accepted. =D

---

