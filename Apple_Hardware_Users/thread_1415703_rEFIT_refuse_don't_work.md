---
title: "rEFIT refuse don't work"
date: 2010-02-25
forum: Apple Hardware Users
---

### Post by SwedishWings on 2010-02-25
I had rEFIT working nice before. Then i uninstalled rEFIT (as described on the rEFIT homepage) and got back to normal boot. 

Now, when i need to install it again (to install Ubuntu), the installation completes successfully, but i get normal boot OSX. I have tried to manually install rEFIT, but without success. I always get to the normal boot of OSX. 

Any ideas?

Thanks,
Mike

---

### Post by linuxopjemac on 2010-02-25
> from within OSX:
Open Terminal and enter the following commands:

```
cd /efi/refit
./enable.sh
```

When prompted, enter the password for your user account.

If everything went well, you&#8217;ll see the rEFIt boot menu on the next restart. 


[http://refit.sourceforge.net/doc/c1s1_install.html](http://refit.sourceforge.net/doc/c1s1_install.html)

---

### Post by SwedishWings on 2010-02-25
> **linuxopjemac said:**
> [http://refit.sourceforge.net/doc/c1s1_install.html](http://refit.sourceforge.net/doc/c1s1_install.html)

Thanks for your reply.

Iv'e done exactly that a few times, but no change. However, after giving it up, and restarting a few times it suddenly start to work for no obvious reason.

---

### Post by linuxopjemac on 2010-02-25
Well great. I also don't understand but I'm glad it worked for you.

---

