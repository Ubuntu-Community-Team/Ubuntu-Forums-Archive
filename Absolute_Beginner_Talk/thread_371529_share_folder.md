---
title: "share folder"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by Patrickvv on 2007-02-27
ok so im sharing a folder for windows users to access. i've installed the samba thingy which says need to be installed. when i go to a windows box and run my IP it asks for name and password.

i put my normal login name which is patrick and **** which is my login password. but i cant get access. not even as when i put root as username..anyways can someone give me a good instructions on sharing for ubuntu !!

---

### Post by chuckyp on 2007-02-27
[www.ubuntuguide.org](www.ubuntuguide.org) has excellent isntructions on various samba set ups.  You can make a share so that any user can read/write to it with out authentication.

---

### Post by Sidster on 2007-02-27
Hi There

You're on the right track. :)  All you need to do is create a samba user and you're on your way. It's very easy, here's how:

Open a terminal window and copy and paste the following code:

```
sudo smbpasswd -a *user*
```

Replace "user" with a username that you choose. I usually make this the same as my Ubuntu login name but you can use any user name you like.

Once you've done that it'll prompt you to enter your desired password for this user and re-enter it to confirm.

Now when you connect to that share you put in the username and password you've just chosen

---

### Post by SqRt7744 on 2007-02-27
This link might help you:

[http://easylinux.info/wiki/Ubuntu_Edgy#Samba_Server](http://easylinux.info/wiki/Ubuntu_Edgy#Samba_Server)

easylinux is a great guide, lost of quick setup info.  another one is 

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

If it still doesn't work after following the instructions at easylinux, post here again.

Good luck!

---

### Post by Patrickvv on 2007-02-27
will do and post update.thanks

---

### Post by Patrickvv on 2007-02-27
nah, not working. after following this [www.ubuntuguide.org](www.ubuntuguide.org)  i cnt even see my friends on the workgroup.Nor can they access me.
each time i go on the windows box and run my Ip i get the 'network path not found'error..

this is very confusing.

---

### Post by Sidster on 2007-02-27
> when i go to a windows box and run my IP it asks for name and password


If you got that far before, you should just be able to enter your newly created samba username and password. The only other problem could be the domain name. That is usually "MSHOME" but you can check this in "Administration" > "Shared folders" under "General Properties"

---

