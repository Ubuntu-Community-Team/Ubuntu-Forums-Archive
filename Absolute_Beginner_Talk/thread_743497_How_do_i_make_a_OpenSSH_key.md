---
title: "How do i make a OpenSSH key"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by LiNuXxToOthEMaX on 2008-04-02
i wanted a generated one, but i cant figure it out, any help thank!

---

### Post by Crafty Kisses on 2008-04-02
> **LiNuXxToOthEMaX said:**
> i wanted a generated one, but i cant figure it out, any help thank!

First, you'd have to login as root, and do the following:
```
ssh-keygen -t rsa
```
That should generate a ssh-key for you.

---

### Post by Kingsley on 2008-04-02
```
sudo ssh-keygen -t rsa
```

---

### Post by bodhi.zazen on 2008-04-02
here is a nice intro

[http://alblue.blogspot.com/2005/08/howto-ssh-logins-using-keys.html](http://alblue.blogspot.com/2005/08/howto-ssh-logins-using-keys.html)

Also, you do not need to be root to make keys.

---

### Post by Crafty Kisses on 2008-04-02
> **bodhi.zazen said:**
> here is a nice intro

[http://alblue.blogspot.com/2005/08/howto-ssh-logins-using-keys.html](http://alblue.blogspot.com/2005/08/howto-ssh-logins-using-keys.html)

Also, you do not need to be root to make keys.

Yeah, my bad. Just make sure to type sudo.

---

### Post by bodhi.zazen on 2008-04-02
> **Codename said:**
> Yeah, my bad. Just make sure to type sudo.

LOL, you can make a key as a regular user, no need or sudo or su.

> test@VirtualUbuntu:~$ ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/home/test/.ssh/id_rsa):
Created directory '/home/test/.ssh'.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/test/.ssh/id_rsa.
Your public key has been saved in /home/test/.ssh/id_rsa.pub.
The key fingerprint is:
4f:0d:42:17:60:76:e8:1b:93:0a:3e:5a:18:97:ec:bc test@VirtualUbuntu
test@VirtualUbuntu:~$

test@VirtualUbuntu:~$ ls .ssh/
id_rsa  id_rsa.pub

---

### Post by kevdog on 2008-04-02
As Ive stated before, its proabably better to make 2048 bit keys or even 4096 bit keys beyond the 1024 bit default length.  To do this it would be:

ssh-keygen -t rsa -b 2048 
ssh-keygen -t rsa -b 4096

Choose one of the following above.  The maximum key size currently is 4096 so you cant eclipse this.  2048 should be sufficient.

---

