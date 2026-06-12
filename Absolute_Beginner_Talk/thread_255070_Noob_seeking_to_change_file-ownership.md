---
title: "Noob seeking to change file-ownership"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-09-10
Checking the Title: above, returned:

vBulletin Message

    Sorry - no matches. Please try some different terms. 

                     ************************ 

I need to change the ownership of 3 files in /etc/ppp. They are:

-rw------- 1 root root   128 2006-09-10 15:23 chap-secrets
-rw------- 1 root root  1709 2006-09-10 15:57 pap-secrets
drwxr-s--- 2 root dip   4096 2006-09-10 15:57 peers

I am the only person using this computer. It's in my home. I want to have me (the user) known to the system as: **mark** to be the owner of these files. Or alternatively, I need WvDial and PPPD to be able to read/write to them. Especially WvDial.

Please show me, by example, how to do this, I've spent 2 hours trying to figure out how to sudo chmod, etc. and am no closer now than 2 hours ago.

I thought it was to go:

mark@lexington: chmod o+x etc/ppp/chap-secrets
mark@lexington: chmod o+x etc/ppp/pap-secrets
mark@lexington: chmod o+x etc/ppp/peers

if I understand "man chmod" et alia, this should change the ownership, but to whom? I don't see where I (user: mark) become the owner?

If I issue these commands, what will change in their printouts from: ls -l /etc/ppp?

---

### Post by zekopeko on 2006-09-10
chown is for CHange OWNership. try that.

---

### Post by mscman on 2006-09-10
> **zekopeko said:**
> chown is for CHange OWNership. try that.

More specifically for your info, the command uses the form:
```
sudo chown <username> <filename>
``` 
For example, for your files you would issue the commands:
```
sudo chown mark /etc/ppp/chap-secrets
sudo chown mark /etc/ppp/pap-secrets
sudo chown mark /etc/ppp/peers
``` 
Furthermore, you can merge this to one line with the command:
```
sudo chown mark /etc/ppp/chap-secrets /etc/ppp/pap-secrets /etc/ppp/peers
``` 
***NOTE*** When specifying absolute paths, you need to make sure you have the preceding '/' or else the path will be wrong.

---

### Post by Mark_in_Hollywood on 2006-09-10
That's not enough information. I'm unsure of how to make the "right" "user" the owner. Thanks otherwise.

---

### Post by mscman on 2006-09-10
> **Mark_in_Hollywood said:**
> That's not enough information. I'm unsure of how to make the "right" "user" the owner. Thanks otherwise.

Umm... I sure hope you're referring to the post above mine, because I basically spelled the entire procedure out.

If you are needing more info, let me know.

---

### Post by Mark_in_Hollywood on 2006-09-11
Yes sir, the post above yours. How the forum/computer put it "out of order" is a mystery to me.

---

### Post by Mark_in_Hollywood on 2006-09-11
SUCCESS.

user: mark 

is now the owner of the files. 

Thanks one-and-all.

---

