---
title: "Can't run gedit when su'd as another user?"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by JimTDI on 2006-11-23
Hi Everyone!  Can someone help me please?

I want to be able to edit one of my Postgres config files - it's owned by user "postgres".  If I try gedit as myself, and try to open the file, I get "permission denied" (or something similar) (so gedit fires up quite nicely!).

so...  I'm assuming I need to su as user postgres, and then gedit the file, but when I do, I get the following message.  I am able to VI and VIM the file though (as user postgres).

sudo su postgres
Password:
gedit
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

cannot open display: (null)
Run 'gedit --help' to see a full list of available command line options.

---

### Post by taurus on 2006-11-23
```
gksudo gedit <name of the file>
-or-
sudo nano -Bw <name of the file>
```

---

### Post by JimTDI on 2006-11-23
Thanks!  That helped alot!!

Should I su as user postgres first to edit the file, or just fire up gedit the way you said, as the default user?

I tried as default user, it appears it worked just fine.  I did get another copy of my config file with a ~ after it's filename (a backup copy?).  That file with the ~ makes me a little nervous though... :???:

---

### Post by taurus on 2006-11-23
I recommend you use "gksudo gedit" and yes, the one with ~ at the end is the backup file created by gedit.  If you don't need it, just remove it.

---

### Post by qamelian on 2006-11-23
> **JimTDI said:**
> Thanks!  That helped alot!!

Should I su as user postgres first to edit the file, or just fire up gedit the way you said, as the default user?

I tried as default user, it appears it worked just fine.  I did get another copy of my config file with a ~ after it's filename (a backup copy?).  That file with the ~ makes me a little nervous though... :???:

Just use the command as provided by Taurus. Using sudo will temporarily give you admin rights for any similar task.

---

### Post by JimTDI on 2006-11-23
sorry... don't mean to be a PITA (pain in the a..)  :-)

I follow as far as the gksudo gedit <<filename>>.

Just still not sure if I should su as postgres first since postgres owns the file.  Or if I should run gksudo as myself (user jim).

Or does gksudo allow me to edit user "postgres" (and other user's files), since it executes as root?

I don't want to screw up any file ownership/permissions by doing it the wrong way.  

Sometimes Ubuntu scares me - it has so much power!!

Really appreciate the replies/help - these forums, and people here are wonderful!

---

### Post by NiklasV on 2006-11-23
root has access to all files, regardless of ownership.

---

### Post by JimTDI on 2006-11-23
OK - got it - thanks!!

---

