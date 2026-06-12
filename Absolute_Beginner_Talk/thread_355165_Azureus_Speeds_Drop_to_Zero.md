---
title: "Azureus Speeds Drop to Zero"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by cam2009 on 2007-02-06
I've been using Ubuntu for a month or so, and have been having a problem with azureus since the beginning. i have a laptop, so I port-forwarded just like I did before in windows, and everything seemed to work ok. download speeds are good. but after about 5-10 minutes, the speeds drop to 0. the torrents have plenty of seeders and have perfect health. and, if i close completely out of azureus and open it again, it works for another 5 minutes. i can get them to finish, but only if i open and close 5 or so times in the process. i searched around, but I didn't really understand what the problem was. sounds like it has to do with java? thanks.

---

### Post by Quintin Riis on 2007-02-07
rtorrent

---

### Post by Marcos W on 2007-02-15
I had the same problem with azureus... What i did was to uninstall azureus, install the latest Java JRE and then install latest version of azureus from their site: [http://azureus.sourceforge.net/](http://azureus.sourceforge.net/)

---

### Post by lukew on 2007-02-15
> **cam2009 said:**
> I've been using Ubuntu for a month or so, and have been having a problem with azureus since the beginning. i have a laptop, so I port-forwarded just like I did before in windows, and everything seemed to work ok. download speeds are good. but after about 5-10 minutes, the speeds drop to 0. the torrents have plenty of seeders and have perfect health. and, if i close completely out of azureus and open it again, it works for another 5 minutes. i can get them to finish, but only if i open and close 5 or so times in the process. i searched around, but I didn't really understand what the problem was. sounds like it has to do with java? thanks.

Sounds like you might need to check the portforwarding on your router!!

Luke

---

### Post by volksman on 2007-02-15
Your problem is the Java version in use by default.

```
 sudo update-alternatives --config java
```

If you don't see something like:

```
There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*+        2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java


```

Then that is your problem.  Use Automatix to un-install Azureus and install Sun-JRE....Then re-install Azureus and make sure the command above defaults to the Sun JRE...Everything will work great after that!

---

### Post by stueyboy on 2007-02-18
@ Volksman: Thanks for that information. Azureus has been driving me nuts recently after a re-install of Ubuntu. Because I didn't use Automatix to install, the Java bits and pieces weren't added. I followed your instructions and all is well.

Ta

---

### Post by klepto on 2007-03-06
I had the same problem too.. 

gij-4 was at 99% cpu and azureus would stop downloading. 
I was pulling my hair out trying to fix this problem because I couldn't uninstall gij-4 without removing a bunch of programs including ubuntu desktop.

---

