---
title: "Samba Ubuntu 10.04LTS and Mac OS X 10.5.8 Question"
date: 2010-09-16
forum: Apple Hardware Users
---

### Post by ca_20gti on 2010-09-16
I would like to go to Places->Network and double click on my mac computer and a login window appears, once logging in it will grant me access to my shared drives.

If I go to connect to sever I can login and all is well because I can login, however certain people do not want to do this which makes my job harder lol... 

In the past I have had very good luck in searching and finding the answers to this question. But I can't seem to find the solution for this issue so i am breaking down and asking, adding 

browseable = no
writeable = no

to the mac's  /etc/smb.conf as previously suggested is not working for me now, I have no idea what could have changed. But it does look like the smb.conf file has changed somewhat.

It has been awhile since I looked at this file. Any help or links is greatly appreciated

Using 

Mac OS X 10.5.8
Ubuntu 10.04 LTS

Thanks :)

---

### Post by ca_20gti on 2010-09-16
I guess I should add, I can browse/copy files to my Ubuntu box just fine from my Macintosh, but when I go to connect to my Mac using my Ubuntu box, I can see the shared drives just fine. But my home dir will allow me to get 1 level in then say I do not have permissions, it won't ask me to login, so I cannot make changes.

---

### Post by ca_20gti on 2010-09-16
Bah, I just noticed I posted this in the incorrect place, my bad. I was super tired last night? can it be moved to a more appropriate place?

---

