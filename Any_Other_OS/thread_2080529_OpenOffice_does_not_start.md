---
title: "OpenOffice does not start"
date: 2012-11-04
forum: Any Other OS
---

### Post by aabed91 on 2012-11-04
Hi all,

I install Unix Mint 13 in my laptop.
and i install openoffice

but when i start it nothing happened.
in terminal i type:

```
openoffice.org
```

the result is:

javaldx: Could not find a Java Runtime Environment! 
no suitable windowing system found, exiting.


Any help?

Thanks

---

### Post by Peter Maunder on 2012-11-04
Linux Mint 13 already has LibreOffice installed, which is the preferred alternative (upgrade) to OpenOffice. It is not recommended to install OpenOffice alongside Libreoffice due to conflicts.

---

### Post by howefield on 2012-11-04
Thread moved to "*Other OS/Distro Talk*" forum.

---

### Post by aabed91 on 2012-11-04
> **Peter Maunder said:**
> Linux Mint 13 already has LibreOffice installed, which is the preferred alternative (upgrade) to OpenOffice. It is not recommended to install OpenOffice alongside Libreoffice due to conflicts.

LibreOffice removed and OpenOffice Installed.
But this problem appear.

---

### Post by vasa1 on 2012-11-04
There's a forum for Linux Mint users over here: [http://forums.linuxmint.com/](http://forums.linuxmint.com/)

Maybe you'll find other people with the same OS who have solved your problem.

---

### Post by Hagar Delest on 2012-11-15
You may find some hints with [this query on the AOO forum]("http://forum.openoffice.org/en/forum/search.php?st=0&sk=t&sd=d&sr=topics&keywords=Java+Runtime+Environment&fid%5B%5D=16").

---

### Post by Peter Maunder on 2012-11-15
On Ubuntu and Libux Mint LibreOffice and OpenOffice are usually installed to the /opt folder. for example 
      /opt/libreoffice3.6/program/soffice  
The root application is actually called soffice. Individual applications swriter, scalc, sbase, smath, simpress. 

If you wish to start OpenOffice from the terminal you should invoke the appropriate module directly not OpenOffice.org.

On my Ubuntu 12.04 and Mint 13 systems  I have both LibreOffice 3.5 and 3.6 installed. The OpenOffice is equivalent to 3.4 and there are known problems trying to mix 3.4 with later systems.

Unless you have overriding reasons for using OpenOffice.org, I would suggest you remove it and re-install LibreOffice. After all Ubuntu (Mint) were tested with LibreOffice not OpenOffice.

---

### Post by MadmanRB on 2012-11-16
Personally I dont understand why you wanted openoffice instead of libreoffice, both are the exact same thing.
The only difference is the numbers game which currently openoffice is behind on and improvements to the system will appear in libreoffice long before they hit openoffice.

---

### Post by Hagar Delest on 2012-11-17
Personally, LibO is a show stopper because of the Navigator that is not expanded by default. I need to see the whole outline structure of my files as soon as I load them. So LibO is definitively not the solution.
The lack of page borders too is not something I like too (may be reactivated somewhere in the preferences I hope).

Moreover, LibO QA is not that good. Even on their mailing list they say that the X.Y.0 and even X.Y.1 versions are not fit for production work. This is just not acceptable. I won't risk my daily job to beta test an application. If the release doesn't meet the quality standards or if you're not sure you've checked the whole thing, then don't release it. I know there is limited manpower on QA but well, once a version is released, bugs are reported. So instead, make RC and wait longer before going final.

Finally, I think that Apache license will be proved more dynamic and may attract more devs or more money from big players. They also seem to be more concerned by quality and stability, especially if it's more oriented toward corporate use. BTW, I've heard that LibO was thinking of changing their license to... Apache license too.

---

