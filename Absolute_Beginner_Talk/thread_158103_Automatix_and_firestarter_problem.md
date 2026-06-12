---
title: "Automatix and firestarter problem"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2006-04-10
Having used automatix to install 'Firestarter' it seemed to download and install, on restart of PC I am asked for password to run 'Firestarter' in  /user/sbin/firestarter. I supply the password then nothing happens .It is not installed! If I try to uninstall as the automatix post, I get 'Firestarter' not installed. I have looked at 'Files', /usr/sbin/ firestarter and there is no entry, yet I am stll asked for password to run it on bootup. Any ideas anyone?:confused:

---

### Post by r4ik on 2006-04-10
Well it is a litlle bit of a read but this might work,

[http://www.ubuntuforums.org/showthread.php?t=23081&highlight=remove+firestarter](http://www.ubuntuforums.org/showthread.php?t=23081&highlight=remove+firestarter)

Good luck.

---

### Post by confused57 on 2006-04-10
Try this:

Now go to system --> preferences --> sessions -->startup programs and remove
"gksudo firestarter"

I had the same problem using Automatix to install firestarter, this will remove
the login to firestarter at startup.   You'll still be able to start firestarter in the normal way and login manually at the prompt rather than at startup.

---

### Post by Sbarton on 2006-04-10
Thanks. I restarted the pc twice and it is now up and running. Weird though.

---

### Post by Sbarton on 2006-04-10
Thanks. I restarted the pc twice and it is now up and running. Weird though.

---

