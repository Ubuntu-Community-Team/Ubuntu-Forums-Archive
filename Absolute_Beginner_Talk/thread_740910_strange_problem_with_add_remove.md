---
title: "strange problem with add remove"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by shredfitz on 2008-03-31
I just did a fresh install on a Thinkpad t40 of 7.10. I want to use add/remove applications. When I select an application to be added, I get the message that pops up to tell me that 'the list of applications is not available,  Click on reload to reload it. You need a working internet connection'. So I hit refresh and then it goes throught he process very quickly but nothing happens in the end. I then try again and I get the same message. Just an endless loop. Anyone know what could be the problem here ?

---

### Post by shredfitz on 2008-03-31
never mind I got it. Sorry to bug you! :)

---

### Post by joechua1996 on 2008-04-01
I also have that problem. How do you fix it?

---

### Post by obsidiaani on 2008-04-04
I also have a similar problem. I already managed to update the list but it won't download anything.... 
...so..... wtf?

---

### Post by oedha on 2008-04-04
first....go to system - administration - software sources
mark on all 4 boxes
close it....click reload
go to add/remove again
search your program on all available applications...
maybe this can help...:)

---

### Post by obsidiaani on 2008-04-04
> **oedha said:**
> first....go to system - administration - software sources
mark on all 4 boxes
close it....click reload
go to add/remove again
search your program on all available applications...
maybe this can help...:)

did that already. now it updates the list of available applications just fine. now when I select something (gFTP) and press Apply Changes->Apply it says: W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gftp/gftp-common_2.0.18-16ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gftp/gftp-common_2.0.18-16ubuntu3_i386.deb)
403 Forbidden

---

### Post by oedha on 2008-04-04
change the server of source code........
or
the repo is not available for this time....

:)

---

### Post by obsidiaani on 2008-04-04
> **oedha said:**
> change the server of source code........
or
the repo is not available for this time....

:)

changed the server. same thing happens. what do you mean with "the repo is not available for this time...."??

also... I did this: sudo apt-get install ubuntu-restricted-extras

but it says that the package was not found, or something. my ubuntu is finnish so sorry about the translation...

---

