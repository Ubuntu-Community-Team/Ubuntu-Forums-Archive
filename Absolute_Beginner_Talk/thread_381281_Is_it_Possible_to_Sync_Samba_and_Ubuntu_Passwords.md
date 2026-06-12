---
title: "Is it Possible to Sync Samba and Ubuntu Passwords?"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by robinlennox on 2007-03-10
Sorry to be a bother...

Just wondering if it's possible to sync these passwords?

Kind Regards

Robin

---

### Post by dstew on 2007-03-10
I don't think you can do that. You can, of course, use the same passwords, and you can automatically mount a samba share at boot time, but I don't know how you can grab the Ubuntu password and insert it into your Samba mount command automatically. Maybe by writing a script...?

---

### Post by robinlennox on 2007-03-10
Write a Script! I've been using windows for over 10 years.. How do I Point and Click to that! :lolflag:

---

### Post by gradedcheese on 2007-03-10
Lets take a look at /etc/samba/smb.conf, namely the lines:

```

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

```

So, remove the ';' and set password sync to 'yes', I suppose?

---

### Post by robinlennox on 2007-03-10
Thats what I thought as well, but no luck! I thought "Another Easy Option!":)

But it wasn't to be.... even restart samba just incase.

---

### Post by gradedcheese on 2007-03-10
For me, it seems to do exactly what's stated: if you smbpasswd to change a password, the other's passwd is also changed.  With the option disabled, it is not.  Obviously going the other direction won't have the same effect, since samba isn't involved when you use passwd on Linux accounts.

---

