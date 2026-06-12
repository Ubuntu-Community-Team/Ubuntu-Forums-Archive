---
title: "can't do sudo, 3 password out"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by clark0820 on 2007-01-28
Hi all,

         I try to log in as root user eariler to fix sth, but I don't know why, I never set up a root password and they ask for one, and then I fail give it the password within 3 times.

         Right now I can still use my normal user password to log in, but I can't do "sudo su"
when I typed "sudo su", it said "sudo: must be setuid root".

         Can anyone please help me wiht this suituation? thanks a lot.

Clark

---

### Post by MkfIbK7a on 2007-01-28
there is no root password by default in ubuntu instead we use sudo see here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ewankho on 2007-01-28
what exactly are you trying to do with "sudo su"? use your user password when it asks for the root password.

---

### Post by clark0820 on 2007-01-28
right now, my ubuntu couldn't have internet access, I don't know y, but it happened after the root password 3 times out thing. I want to do "sudo su" and do sth about the network, but now it return the msg "sudo: must be setuid root", Do anyone know any comment that I can type to fix my ubuntu??

thanks

---

### Post by aysiu on 2007-01-28
> **clark0820 said:**
> right now, my ubuntu couldn't have internet access, I don't know y, but it happened after the root password 3 times out thing. I want to do "sudo su" and do sth about the network, but now it return the msg "sudo: must be setuid root", Do anyone know any comment that I can type to fix my ubuntu??

thanks
[This thread](http://ubuntuforums.org/showthread.php?t=35130) might help.

---

### Post by clark0820 on 2007-01-28
I look at the thread and seems like have the idea to fix it.

How can I get to add lines in the "sudoers" file??
I can't use sudo to change the file and the file now is read only.

Thanks

---

### Post by aysiu on 2007-01-28
Boot into recovery mode. That will make you root.

More details here:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by clark0820 on 2007-01-29
hi

I tried 2 of the things that the thread said, I tried change the sudoers file and click the tick, but my ubuntu still can't do sudo su, just give me a msg, "sudo: must be setuid root"

can anyone help??

thanks

---

### Post by aysiu on 2007-01-29
And you already tried ```
chmod 0440 /etc/sudoers
``` when you were in recovery mode?

---

### Post by clark0820 on 2007-01-29
I tried it
but ubuntu still give me that
"sudo: must be setuid root"

---

### Post by rajan on 2007-01-29
it seems to me that

```

sudo su

```

is redundant, isn't it?

---

### Post by compmodder26 on 2007-01-29
> **rajan said:**
> it seems to me that

```

sudo su

```

is redundant, isn't it?

No, not really.  That allows you to work as root from the command line without having to prepend sudo to every command you type.  Some find that trivial.  I on the other hand find it quite convenient to not have to type sudo with every command.

---

### Post by OBnascar on 2007-01-29
Try using the file manager "Krusader Root" if you have that installed. Look for /etc/.sudoers.tmp. If this file exist, then you need to delete it using Krusader root, then try again and see if that fixes your problem.

If it doesn't, then post back and we will try something else.

If you do not have Krusader installed, do so using Adept.

good luck !

---

### Post by jkeyes0 on 2007-01-29
I'm not sure about the sudo su command, but I seem to recall using something like "sudo -i" to hold the "sudo" session. Someone please correct me if I'm wrong.

---

### Post by OBnascar on 2007-01-29
Wait a minute....does "sudo su" not work or does "sudo" not work either ????????

---

### Post by rajan on 2007-01-29
> **compmodder26 said:**
> No, not really.  That allows you to work as root from the command line without having to prepend sudo to every command you type.  Some find that trivial.  I on the other hand find it quite convenient to not have to type sudo with every command.

right .... so doesn't "su" do the same thing? i.e., switch to root user? i'm sure i'm wrong, but how?

---

### Post by steve.horsley on 2007-01-29
The obvious one to me is to make sure /usr/bin/sudo is setuid root. This is what mine looks like:
> steve@StevesPC:~$ ls -l /usr/bin/sudo
-rwsr-xr-x 2 root root 91508 2006-10-09 12:37 /usr/bin/sudo
If it's not setuid (notice the 's'), boot into recovery mode and do:
**chmod +s /usr/bin/sudo**

---

