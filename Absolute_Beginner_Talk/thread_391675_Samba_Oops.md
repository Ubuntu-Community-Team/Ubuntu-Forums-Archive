---
title: "Samba Oops"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by djearwig on 2007-03-23
Greetings Everyone,

I am hoping that someone will be able to help me with a small problem.  While installing and configuring LDAP, I accidentally rm-ed my samba.schema file.  Does anyone have a fresh one that they could post here so I could just copy and paste it?  It would be very much appreciated.

Thank you...

---

### Post by dhtseany on 2007-03-23
Are you referring to the "samba.conf" file?

---

### Post by djearwig on 2007-03-23
Yes, it is called samba.schema.  It comes compressed as samba.schema.gz in the initial install.  Is there a samba.conf file?  According to the LDAP readme file I need to copy the samba.schema file into the LDAP folder.  That is when I accidentally rm-ed the file.

---

### Post by djearwig on 2007-03-23
The file that I am looking for is contained in: /usr/share/doc/samba-doc/examples/LDAP/samba.schema.gz  
If you have samba installed.

---

### Post by djearwig on 2007-03-26
Nobody can help me out here?  

Please ...

---

### Post by dhtseany on 2007-03-26
This may sound dumb, but why don't you just uninstall LDPA and reninstall it?

---

### Post by djearwig on 2007-03-27
Yeah, I thought about that, but it would just be sooooo much easier to be able to restore that one file.  I'll probably just end up uninstalling and reinstalling Samba just to get that one file back.  Oh well, it was my mistake...

---

### Post by djearwig on 2007-03-27
Oh yeah - thanks for replying to my post.  I appreciate it.

---

### Post by mpokrywka on 2007-03-27
You don't need "uninstall" samba, this will probably do the trick:
```

sudo apt-get --reinstall install samba-doc

```

You can also browse inside deb packages using **mc** - go to /var/cache/apt/archives directory

---

### Post by djearwig on 2007-03-27
Brilliant!
'mpokrywka' you did it!
I'll have to remember that reinstall command...

Thank you

---

