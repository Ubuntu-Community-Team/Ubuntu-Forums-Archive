---
title: "Samba Password"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by mikeylikesit on 2008-02-12
Hi All, i am trying to set up an share using ubuntu 7.10, and samba. the host name is server. In windows i type //server, and it asks for a password. I type in my credentials with no luck the box just pops back up, I have tried the sudo smbpasswd -a mike and sudo smbpasswd -e mike. 

I am having a really hard time i would appreciate some help.

---

### Post by oedha on 2008-02-12
here's what i did
to shared my laptop linux folder.....
go to system - administration - shared folder
click add button
choose teh folder that i'd like to share
pay attention on read only box

then....open terminal
type :==> sudo smbpasswd -L -a username ( make a username and password can be different from login)

---

### Post by spiderbatdad on 2008-02-12
It's been a while since I tried samba, and I remember struggling with the credentials. I think I finally made the Ubuntu shares folder 0777.  I used the so called "comprehensive guide to samba" from the Ubuntu wiki...it had an error regarding credentials as well.

Hoping to see a good answer to this question.

---

### Post by dcstar on 2008-02-12
> **mikeylikesit said:**
> Hi All, i am trying to set up an share using ubuntu 7.10, and samba. the host name is server. In windows i type //server, and it asks for a password. I type in my credentials with no luck the box just pops back up, I have tried the sudo smbpasswd -a mike and sudo smbpasswd -e mike. 

I am having a really hard time i would appreciate some help.

And what folders have you shared?

If there are any permission issues whatsoever (like Samba doesn't have permission to read a folder etc.), then the authentication will fail and you will keep being prompted.

You should also check your /etc/samba/smb.conf file to ensure that all the right things have been enabled. There are various Samba HOWTOs you can search out for details.

---

### Post by mikeylikesit on 2008-02-12
i am trying to share out my slave HD, but i also tried it with my home folder, this is driving my crazy

---

### Post by munkyeetr on 2008-02-12
> **mikeylikesit said:**
> Hi All, i am trying to set up an share using ubuntu 7.10, and samba. the host name is server. In windows i type //server, and it asks for a password. I type in my credentials with no luck the box just pops back up, I have tried the sudo smbpasswd -a mike and sudo smbpasswd -e mike. 

I am having a really hard time i would appreciate some help.

Is your samba password the same as you Windows login password? I'm pretty sure you need to have a password on your Windows user account, and it has to be the same as your samba login password.

I just got mine set up yesterday, and after making the two passwords the same, i didn't even need to type a password to see my shared partitions. The Windows login handles it.

---

