---
title: "dont have permissions to change.."
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by noob_saioke45601 on 2007-03-13
hello again, i been trying to move a source file to src folder in usr folder but it gives me a strange error saying i do not have permission to move or change my file into the src folder. any help?

---

### Post by Jussi01 on 2007-03-13
Type

```
sudo nautilus 
```

into terminal, then copy in that.

---

### Post by taurus on 2007-03-13
> **Jussi01 said:**
> Type

```
sudo nautilus 
```

into terminal, then copy in that.

Should use gksudo instead.

```
gksudo nautilus
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by noob_saioke45601 on 2007-03-13
typed in gksudo nautilus and got this error..


gksudo nautilus
(nautilus:8349): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(nautilus:8349): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.

---

### Post by taurus on 2007-03-13
What is the name of the directory what you want to move and where do you want to move it?  You can do that from a terminal like

Applications -> Accessories -> Terminal
```
sudo cp **directory** **destination**
```

---

### Post by noob_saioke45601 on 2007-03-13
ah i see

thanks for te info.

---

