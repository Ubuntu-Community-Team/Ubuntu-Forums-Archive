---
title: "user accounts with limited access"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by napi on 2008-03-14
Hey all.

Apologies if the title of the thread is mis-leading or simply wrong - still getting used to the terminology!

Just got Ubuntu Server up and running last night (yay).

I've setup all the LAMP stuff (brilliant tutorials on here, thankye) and FTP.

Now the next bit I'm stuck on; I want to be able to setup user accounts for friends so they get a limited amount of space, limited bandwidth (if possible?), shell access, ftp, and a directory for a website. Beyond that will be giving access to MySQL but figured I'd start with the basics first.

Not entirely sure how to get started on this or what to search for so any tutorials/documentation that will point me in the right direction would be greatly appreciated.

Edit- am well aware that diving into a multi-user system is not particularly smart for a linux beginner, but this is what the server will be used for eventually (won't be public/reselling, just for small circle of friends who are interested in this stuff)

---

### Post by marufaberlin on 2008-03-14
What do you want a bandwidth limit for? That's probably gonna be hard.

 You'd want to set up an SSH server for the shell access (see link bolow). Add the users locally using useradd and have their home directories some place Apatchy :-D can see (/var/www/username would be a good choice). Then, when they log in to their ssh shell, they get to the right dir. A good ftp server I'd recommend is vsftpd. Install it using
```

sudo apt-get install vsftpd

```

see [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html) for a complete tutorial to install ftp.

see [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#SSH](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#SSH) for a tutorial to install ssh.

Setting up mysql access is pretty much easier.
Install phpyadmin using
```

sudo apt-get install phpmyadmin

```

and add the users when going to [http://yourdomain/phpmyadmin](http://yourdomain/phpmyadmin)
Your users can go to that URL and log in there too.

Hope that answers your question.

---

### Post by diegosouza on 2008-03-14
Hey man, do a search about "quota2"  and "htaccess"... you can have a good control using both.
The only english link I have right now is it: [https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles](https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles)

Good luck.

---

### Post by napi on 2008-03-14
Cool. Plenty there to get me started. Thanks for the help :)

---

