---
title: "Plesk and Ubuntu"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by redmond on 2006-08-16
I'm "playing" around with web servers at the moment.. this is just as a learning exercise, not as a going concern!

I have installed ISPconfig and set up a server via the very helpful "how to" guide on soundforge.. that is all working fine now..

But I want to try with Plesk as I have used it as a client before and am curious about setting it up (they have a trial version)..

so my question at the moment is.. and sorry of this seems basic.. if i'm using the plesk autoinstaller, do I need to have already installed apache, sendmail, ftp, mysql. php, ssl, etc before I install it.. or do I just intall the server version of 5.10 then install plesk?

---

### Post by siacs on 2006-08-17
It's generally a good idea to have all the services and apps on your system beforehand that an autoinstalled application would need to function correctly.

---

### Post by redmond on 2006-08-18
thanks.. will do

---

### Post by ZebCarnell on 2006-09-09
This is not nessicary with plesk.
Plesk runs apt-get and installs the packages needed. If you have any servers installed already itll remove and reinstall them.

---

### Post by wag2639 on 2007-03-06
Hi,

I have webadmin setup on my home ubuntu 6.06 server but I want to use plesk cause i'll need to use it for work. 

I tried installing Plesk before but I got a whole slew of errors about missing packages that weren't abel to be found. I went into the source.lst file and uncommented all the sources so it could use all repositories but I still got errors. 

At some point, i couldn't even use apt to get anything as it would point to plesk dependencies. 

I gave up and reinstalled ubuntu as there was nothing on it but I don't want to do that again.

Is there an easy to follow exact step by step guideline online somewhere?
Last time I looked, i came to the conclucsion that plesk and ubuntu 6.06 weren't ready for each other yet.

Thanks

---

