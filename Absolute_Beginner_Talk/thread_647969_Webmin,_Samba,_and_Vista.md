---
title: "Webmin, Samba, and Vista"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by kjhud on 2007-12-23
I want to share my files, so i have downloaded Webmin and Samba but I have no clue how to set it up so that my Vista laptop can access it.

---

### Post by blueridgedog on 2007-12-23
There are a lot of great samba how-to's out there.  Here is a good one:

[http://samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/)

Here is one that involves webmin:

[http://www.webmin.com/samba-howto.html](http://www.webmin.com/samba-howto.html)

If you read up a bit on samba and webmin and then give it a try, you may encounter some specifics that others on the list can assist with.

---

### Post by kjhud on 2007-12-23
I did everything it said but it still doesn't work.

---

### Post by HermanAB on 2007-12-23
I suggest that you do something simpler first:
[http://filezilla-project.org/](http://filezilla-project.org/)

Samba is *the* most difficult file sharing system to set up and Ubuntu doesn't have proper wizards to do it for you.  So I recommend FTP and NFS first and Samba waaaaaay last and only for people that are committed to read the documentation.

Cheers,

Herman

---

### Post by kjhud on 2007-12-23
Do i need to install that on both of my PCs?

---

### Post by blueridgedog on 2007-12-23
Give me an overview of what you did other than "everything".

(what shares did you create, what were the permissions etc)

Give me an better understanding of what is not working, can the other PC's not see the Ubuntu box at all?  Can they not see the shares?  Can they not access the shares?  How are you testing it?

Also, are you willing to edit some test files by hand?

This is a simple process, but it must be done right and it is difficult to debug.

---

### Post by kjhud on 2007-12-24
Well I know my laptop can't detect Ubuntu on the network and i have tried mapping the drives by name and IP address. Is there anyone that can help me through skype, AIM, MSN, Xbox live?? Real time chat would be so much more helpful

---

### Post by blueridgedog on 2007-12-24
Why don't you post the out put of the following command:


cat /etc/samba/smb.conf


This will show how your samba setup is configured.

---

