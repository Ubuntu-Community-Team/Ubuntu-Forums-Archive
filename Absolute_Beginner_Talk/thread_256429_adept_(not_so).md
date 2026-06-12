---
title: "adept (not so)"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by spur on 2006-09-13
I have been trying to get adept to work and I receive this message
You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.
I get this all the time. As far as I can detrmine no other program or process is using the packaging system.
I tried looking at the process running to see if something was, no luck.
does any one have any sugestions. 
I'm running Dapper 6.06 Kubuntu 32 bit on a 64 bit board with an AMD 64 dual core 4200+ and 3GB RAM and 110GB hdd.](*,)

---

### Post by jordanmthomas on 2006-09-13
Are you running it as root?
Press Alt + F2
type
```
kdesu adept
```

If this doesn't work, log off and then back on and see if it'll work then.

---

### Post by spur on 2006-09-13
I had tried that but I did it agian to be sure and no change. I still can't use adept. What would be locking the data base?:confused:

---

### Post by Jucato on 2006-09-13
A failed or interrupted installation could also lock the database. Try running this command to fix it:

```
sudo dpkg --configure -a
```

---

### Post by spur on 2006-09-13
Thanks. Errors were reported.
meliore@meliore-desktop:~$ sudo dpkg --configure -a
Password:
Setting up libxfont1 (1.0.0-0ubuntu3.2) ...
Setting up libtunepimp-bin (0.4.2-3ubuntu3~dapper1) ...
Setting up libtheora0 (0.0.0.alpha7-1ubuntu1~dapper1) ...

Setting up ktorrent (2.0.1-0ubuntu1~dapper1) ...

Setting up liblog4j1.2-java-doc (1.2.12-1ubuntu2) ...
cannot create dhelp file '/usr/share/doc/liblog4j1.2-java-doc/docs/.dhelp': No such file or directory
dpkg: error processing liblog4j1.2-java-doc (--configure):
 subprocess post-installation script returned error exit status 2
Setting up amarok-xine (1.4.2-0ubuntu2~dapper1) ...
Setting up amarok (1.4.2-0ubuntu2~dapper1) ...

Errors were encountered while processing:
 liblog4j1.2-java-doc
meliore@meliore-desktop:~$

---

### Post by spur on 2006-09-13
I ran adept from the command and got he same result. I coud paste the whole output to the comand line here but it is long. If some one thinks it could be useful I can post it or send it too them.

---

### Post by spur on 2006-09-13
I solved it. I looked at the output above nad noticed the dificulr ty with 
liblog4j1.2-java-doc. I used kdesu konqueror to go to the file address mentioned above in the line starting "cannot creat..." I then found that the final docs directory did not exist. I created it then ran the configure command again and it finished. I then run adept and it ran ok. Thanks Jucato, much appreciated.

---

