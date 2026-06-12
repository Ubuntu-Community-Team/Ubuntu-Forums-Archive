---
title: "password"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by fyrstorm on 2008-04-16
Hi ,
 Huge newbie... Not very computer knowledgeable .. Just learning. B/f was working all ubuntu for me .. HE is out of the picture now so i need to learn I first need to change my adminstrator password. Could someone please help.. I am sure this is very easy but I have looked and have no clue what to do .. Thank you in advance for your help and time.. 

R:confused:

---

### Post by nathanael on 2008-04-16
click "system", click "preferences", then click "about me" then click change password in upper right hand corner.

---

### Post by Dazed_75 on 2008-04-16
Easiest if you are able to log in as the "administrator" whatever that user name is.  If you are able to do that then either open a terminal and enter "passwd" or use the System/Administration/Users and Groups gui interface to change your password.

If you cannot log in as that account, but have sudo priviledge, then open a terminal and enter "sudo passwd administrator" (substituting the administrator user name of course).

---

### Post by munkyeetr on 2008-04-16
To change your password, which is what you need to use sudo to make administrative changes use:

1) Open a Terminal window (**Applications** -> **Accessories** -> **Terminal**)
2) Then type the following:
```

passwd

```

You'll have to enter your current password, then your new one twice.

In case your B/F changed the root password to something he knows do the following:

1) **System** -> **Administration** ->** Users and Groups**
2) Enter your password
3) Click on the **root** user and choose **Properties**
4) At the very bottom of the dialog select **Generate random password** option, then press **OK**

Now root is set to a random password, and you can use **sudo** to make administrative changes using your own password.

---

### Post by bodhi.zazen on 2008-04-16
I suggest you consider :

1. If there is a concern re: trust -> re-install. It is just easier that way.

2. If you just want to change passwords, open a terminal

```
passwd
``` to change your password.

```
sudo passwd root -l
``` to make sure the root account is locked.
[indent]* That is a small "L" and not the number 1.[/indent]

Delete any other user accounts.

Make sure you are not running any kind of server, like ssh, ftp, samba, nfs or otherwise. If you are you will need to review the security of those services.

---

### Post by aysiu on 2008-04-16
Or try this:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

