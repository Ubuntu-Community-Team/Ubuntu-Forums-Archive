---
title: "samba"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by mstrap123 on 2007-11-20
i test ubuntu 6.10 server on ms virtual pc 2007, i configured samba(should be no problem) then i try to access from xp but i cannot access the server. i found out that i need to set the access for the machine as well as the user, i dont know how to set all this. can any1 give out a FULL TUTORIAL on how to setup ubuntu for samba file and printer sharing?

---

### Post by fatfranko on 2007-11-20
here's a howto i found for you.  post if it worked or not.
[http://ubuntuforums.org/showthread.php?t=76647](http://ubuntuforums.org/showthread.php?t=76647)

---

### Post by fatfranko on 2007-11-20
this is what you're probably talking about:
> 
Finally, create a SMB user, make sure this account exists on your Ubuntu Linux.
Code:

sudo smbpasswd -a `whoami`

and set your password

---

### Post by mstrap123 on 2007-11-21
thanks for the post, i download the latest ubuntu 7.10 and it work perfectly well. maybe the ubuntu 6.10 have problem with virtual pc 2007

---

