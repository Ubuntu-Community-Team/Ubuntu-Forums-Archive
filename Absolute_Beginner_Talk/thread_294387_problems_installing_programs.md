---
title: "problems installing programs"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by omf on 2006-11-06
Hello

I am pretty(very( new to linux, and i have installed a clean ubuntu 6.06 on my laptop (works fine).


I am having some problems when i tried to install a vpn client. I've followed the guidelines given to me, but i am having some problems.

When i try to install the program.

I get the message: Sorry, You need super-user access to run this script.

Even if i am on the only account created so far (the admin one).

I have just downloaded the program to my "home/desktop" directory, does this have anything to do with it?

---

### Post by ReaderRat on 2006-11-06
Are you using 'sudo'?

[How **sudo** Works](http://www.ubuntuforums.org/showthread.php?t=275605)

---

### Post by omf on 2006-11-06
no, i have no idea what sudo is...

i was told to use the terminal, download and then unpakc the problem using:
tar -xzf vpnclient-linux-3.7.Rel-k9.tar.gz

when i try to use the installation file
./vpn_install

i get that error message, regarding super-user...

---

### Post by taurus on 2006-11-06
You need to put "sudo" in front of that line...

```
sudo ./vpn_install
```
May want to read up on these two links!!!

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by omf on 2006-11-06
good tricks using that suo function, i think it did it... now i just need to write the conf file, thanks for the help.

---

### Post by lyceum on 2006-11-06
> **omf said:**
> no, i have no idea what sudo is...

i was told to use the terminal, download and then unpakc the problem using:
tar -xzf vpnclient-linux-3.7.Rel-k9.tar.gz

when i try to use the installation file
./vpn_install

i get that error message, regarding super-user...

sudo is SUper user 

Just type sudo first, ex:

sudo ./vpn_install

---

### Post by taurus on 2006-11-06
Again, if you need to install or modify something outside of your $HOME directory, you need to use sudo...

---

