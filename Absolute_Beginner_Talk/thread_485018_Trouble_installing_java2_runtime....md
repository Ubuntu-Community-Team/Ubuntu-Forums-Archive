---
title: "Trouble installing java2 runtime..."
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by clinton_labombard on 2007-06-26
I downloaded the RPM package from this address:

[http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com:80](http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com:80)

And followed the installation directions given at that site.  However, I'm denied access to root.  I looked around and discovered the command format (or whatever it's called) of 'gksudo [command] [file]' and it looked like it attempted to execute/install the RPM package, but nothing happened.  I've also attempted to switch user to root, but apparently I don't have the password... and I'm the one who installed this.  I saw no prompt for a root user password or user name during installation.  Can you help me?

---

### Post by testube_babies on 2007-06-26
Is there a reason you're installing Java from an RPM?

This is the recommended method:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Java_.26_Non-Media_Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Java_.26_Non-Media_Browser_Plug-ins)

---

### Post by bobplano on 2007-06-26
ubuntu's based on debian meaning that the packages for it are .deb. to install rpm packages you need alien
```
sudo aptitude update
sudo aptitude install alien
sudo alien -i /where/the/file/is.rpm
```

---

### Post by clinton_labombard on 2007-06-26
Thanks, Testube.  That did it.

---

