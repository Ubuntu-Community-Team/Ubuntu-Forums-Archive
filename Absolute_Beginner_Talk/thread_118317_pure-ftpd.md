---
title: "pure-ftpd"
date: 2006-01-16
forum: Absolute Beginner Talk
---

### Post by thanaous on 2006-01-16
hello,

I have installed pure-ftpd using synaptic install, but now im at a lost to run it.
ive tried typing pure-ftp & in terminal and various other things.  Also with sudo in frount of it.  I would love to know how to run it and maybe add it to the start up sequence,
Thanks

---

### Post by thanaous on 2006-01-16
[http://ubuntuforums.org/showthread.php?t=76302](http://ubuntuforums.org/showthread.php?t=76302)

i have found this thead which seems to describe my probem, however i can't edit the file no matter what i type

---

### Post by thanaous on 2006-01-16
i have used gedit to edit the file according the above link.  Then i try to run pure-ftpd either in the file browser or the terminal, and it returns nothing and runs nothing

---

### Post by nvez on 2006-01-16
You sure it runs nothing?  Check if your config is bad and/or it's maybe loading? ("ps -A" after running pureftpd).  Or you aren't starting the service?  "pureftpd -help" and figure out how to start it?

---

### Post by thanaous on 2006-01-16
thankyou for a reply
I checked using ps -A and i have got the service running.  I spose i thought it would pop up a gui so i could set addresses and things.  Was i mistaken?

---

### Post by hen3rz on 2006-01-17
I think u can get a gui for pure-ftpd somewhere...

check out this site: [http://www.debianhelp.co.uk/pureftpweb.htm]("http://www.debianhelp.co.uk/pureftpweb.htm")

---

### Post by thanaous on 2006-01-17
thanks ill have a look

---

### Post by Rumor on 2006-01-17
[QUOTE=thanaous]hello,

I have installed pure-ftpd using synaptic install, but now im at a lost to run it.
ive tried typing pure-ftp & in terminal and various other things.  Also with sudo in frount of it.  I would love to know how to run it and maybe add it to the start up sequence,
Thanks[/QUOTE]


Thanaous,
I run a pure-ftpd server on my machine. I have followed the HOWTO in [this thread]("http://www.ubuntuforums.org/showthread.php?t=91052&highlight=howto+pureftpd") and it works flawlessly for me.

Good luck!

---

