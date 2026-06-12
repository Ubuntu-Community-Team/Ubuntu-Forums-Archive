---
title: "ownership"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by Vithant on 2008-02-28
How do I login as root?
How do I change the ownership of a file to root?


Thanks
Jim

---

### Post by Oldsoldier2003 on 2008-02-28
> **Vithant said:**
> How do I login as root?
How do I change the ownership of a file to root?


Thanks
Jim
sudo -i  to login as root with an interactive terminal

then chown the files/directories

man chown  or chown --help   if you need help with the options

---

### Post by aysiu on 2008-02-28
Please don't change ownership of root-owned files. That's a quick way to render your system useless. The ownership is there for a reason.

To modify root-owned files, however, read [this](http://www.psychocats.net/ubuntu/permissions).

By the way, what are you trying to do?

---

### Post by sayakb on 2008-02-28
> **Vithant said:**
> How do I login as root?
How do I change the ownership of a file to root?


Thanks
Jim

Open a terminal and type

```
sudo bash
```

This would log you in as root for that terminal. Also, adding "sudo" (w/o quotes) in front of any command will make it execute as root.

---

### Post by Oldsoldier2003 on 2008-02-28
> **LinuxIsInnovation said:**
> Open a terminal and type

```
sudo bash
```

This would log you in as root for that terminal. Also, adding "sudo" (w/o quotes) in front of any command will make it execute as root.

Grins, there's always more than one way to skin a cat in linux.  I prefer sudo -i since I've already opened the terminal, but you way ensures he'll get a bash session. Good catch.

---

### Post by Vithant on 2008-02-28
I am gllad you asked.

I downloaded the Java SE into Eris/public or Eris\public and it was loading into my machine when I decided to add another program concurrently which seemed to cause the Java instalation to crash. 

So now when I try to add or update I have to deal with the unfinished Java installation.

so when I run sudo dpkg --configuration -a 
I get you must login as root, root must own the file, and the file must be in tmp.
This is of course all from memory, I will get the exact message.

I am smart, have no life, do not relate to other humans, how do I get up to speed with ubuntu?

---

### Post by aysiu on 2008-02-28
> **Vithant said:**
> 
so when I run sudo dpkg --configuration -a 
I get you must login as root, root must own the file, and the file must be in tmp. It would make sense if you were running ```
dpkg --configure -a
``` that you'd get that message, but if you're running ```
**sudo** dpkg --configure -a
``` you shouldn't get a message saying you have to be root. That's the whole point of *sudo*--to give you the ability to run commands as root.

> This is of course all from memory, I will get the exact message. Please do post the exact message when you get the chance, and include exactly what you're typing, too, to get that error message.

If what you're saying is true, your *sudo* might be broken and [need to be fixed](http://www.psychocats.net/ubuntu/sudo).

---

### Post by Vithant on 2008-02-28
This from power on, directly to system, konsole

eris@Discordia:~$ sudo dpkg --configure -a
[sudo] password for eris:
Setting up sun-java6-doc (6-03-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

When I try to download again from sun I am told file already exists.

---

### Post by aysiu on 2008-02-28
One of these threads may help:
[jdk-6-doc.zip jdk-6-doc-ja.zip](http://ubuntuforums.org/showthread.php?t=485156)
[serious problem causing by unfinished download !!!](http://ubuntuforums.org/showthread.php?t=671167)

---

