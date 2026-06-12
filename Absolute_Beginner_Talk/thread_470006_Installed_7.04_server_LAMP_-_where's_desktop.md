---
title: "Installed 7.04 server LAMP - where's desktop"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by edasich on 2007-06-10
After installing 7.04 server I now have a command line after I log in. 

I have no idea on how to start a desktop.  

How do I see a directory of files etc?

The ubuntu help seems to think I already know how to start the desktop.
thanks

---

### Post by zeveck on 2007-06-10
If I remember correctly, LAMP server does not include a desktop. It's meant to be run on a server.

You can add the desktop though, with <b>apt-get install ubuntu-desktop</b>, which will install a *lot* of stuff, but then you should be on your way to the desktop.

What do you mean by a directory of files? To list files in the current directory use <b>ls</b>.

---

### Post by madmetal on 2007-06-10
> **edasich said:**
> After installing 7.04 server I now have a command line after I log in. 

I have no idea on how to start a desktop.  

How do I see a directory of files etc?

The ubuntu help seems to think I already know how to start the desktop.
thanks


server version doesnt have GUI but you can install it with
```
sudo aptitude install ubuntu-desktop
```

---

### Post by edasich on 2007-06-10
Thanks.  I have no experience with linux and I'm jumping right in.  

that 'apt-get' command is working (after adding sudo command). thanks

---

### Post by tompickles on 2007-06-10
> **edasich said:**
> Thanks.  I have no experience with linux and I'm jumping right in.  

that 'apt-get' command is working (after adding sudo command). thanks
try [http://linuxcommand.org]("http://linuxcommand.org") to give you a head start into learing about Bash - the command line (aka CLI) I found this really really usefull and has helped me understand all about Linux in general. If your new to linux, try using the Desktop version of Ubuntu to just give you a flavour of what a Linux workstation can do for you.

---

### Post by amgeex on 2007-06-10
This will help you: [http://tuxoblog.blogspot.com/2007/06/ubuntu-light.html](http://tuxoblog.blogspot.com/2007/06/ubuntu-light.html)

---

### Post by p_quarles on 2007-06-10
[COLOR=Black]In a server installation, your home/user directory starts out empty. To see what's on the disk, do this:
```
 cd ..
sudo ls

```

The second command forces it to display all hidden files/directories. 
[/COLOR]

---

