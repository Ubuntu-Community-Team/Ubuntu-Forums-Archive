---
title: "Trying to do stuff and cant???"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by will71110 on 2006-09-06
Getting very frustrated.  I installed the GproFTP server and I cant get it to work.  I get an error saying cant not some file and when I try and use the default settings it says "cannot write to a file."  The file it is looking for is proftpd.conf .  It tells me to run program as root.  I'm very confused because I didnt think you could run as root?  Anyone know what I should I do.

---

### Post by empcrono on 2006-09-06
> **will71110 said:**
> Getting very frustrated.  I installed the GproFTP server and I cant get it to work.  I get an error saying cant not some file and when I try and use the default settings it says "cannot write to a file."  The file it is looking for is proftpd.conf .  It tells me to run program as root.  I'm very confused because I didnt think you could run as root?  Anyone know what I should I do.

Sure, Go to System / prefernces / login screen 

then under the sacruity tab click alow admin login

then go to system / Administraction / Users and Groups 

click on "root" then click on properties then give it a password logout then login. under username type root (in the login screen) then the password is what you just gave "root" if you need more help post but see if that works for you.

---

### Post by will71110 on 2006-09-06
Cool...thanks that worked fine...Now if I can only get the FTP server working right?!?!?!?

---

### Post by empcrono on 2006-09-06
woops once you login as root login to the FTP server under root if you didnt do so already and that should fix it?

---

### Post by will71110 on 2006-09-07
Well I got the FTP server up but now I cannot get it to go online.

---

### Post by empcrono on 2006-09-07
I have never used GproFTP hower i have used GFTP and it works nice. have you tried it out. any way  it sounds like you are having a problem with understaning the FTP its self. im a not sure. explain how it works maybe i might be able to help with it.

---

### Post by will71110 on 2006-09-08
I got it working.:)  I needed to change the group setting.  by default it sets the group for nobody.  There was no group nobody so I created one. ( or I just could of assigend it to a group listed).  After I did that it worked like a charm. thanks for the help.  Now I just need to play with it more so I can mess with the advance stuff ;)

---

