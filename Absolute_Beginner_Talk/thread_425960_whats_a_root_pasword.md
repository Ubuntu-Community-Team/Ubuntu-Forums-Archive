---
title: "whats a root pasword"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Big_Kiwi on 2007-04-28
I am trying to install java 'jre-6ui-linux-i586.bin'  have downloaded it to my Ubuntu desktop, then the install instrutions say to open terminal and typr su, then my root password, **But what is my root password and where do I find it and is it the same as my logon password:( **

---

### Post by lluisanunez on 2007-04-28
'su' means you want to become root or administrator. It then asks for your root password. 
In Ubuntu we don't usually use 'su' but 'sudo', wich goes with your normal password. You seem to be following instructions that are not for Ubuntu. I'd recommend installing Java wih Synaptic or apt-get

---

### Post by Big_Kiwi on 2007-04-28
Is threr any one site that I can go to to download compatable JAVA Wins, and other Ubuntu software

---

### Post by Najand on 2007-04-28
Open a terminal:
```

$ sudo apt-get install sun-java6-jre

```

---

### Post by Jose Consuervo on 2007-04-28
> **Big_Kiwi said:**
> Is threr any one site that I can go to to download compatable JAVA Wins, and other Ubuntu software

What exactly do you mean by java Wins. You can find a lot of programs, and install them using add/remove programs on your menu.

---

### Post by nemesisrobot on 2007-04-28
your password should be the one you chose when you set up your User Account during installation

---

### Post by Najand on 2007-04-28
> **nemesisrobot said:**
> your password should be the one you chose when you set up your User Account during installation

I am afraid it is not the root password... It is his/her account's password which is a member of adm group and a sudoer.

---

### Post by mesh_ok on 2007-04-28
AFAIK, commonly Ubuntu user does not need to know root password - everyone uses "sudo"
but if you still want to logon as root, you may use "sudo su" or set root's password by using "sudo passwd root"
I'd suggest you not to do anything with root password - you just don't need it :)

---

### Post by Big_Kiwi on 2007-04-28
thanks again guys another success story, You guys are great, now one more question will Photoshop work underUbuntu

---

### Post by mesh_ok on 2007-04-28
photoshop is promised to work under wine and cedega, but why don't you try GIMP? :)

---

### Post by Big_Kiwi on 2007-04-28
Yeah!  you are right again Gimp works fine, that will do, So far I have replaced quite a few progams with just one **[COLOR="Red"]FANTISTIC[/COLOR]** :guitar:

---

### Post by mesh_ok on 2007-04-28
Happy to help you :) Welcome to Ubuntu

---

