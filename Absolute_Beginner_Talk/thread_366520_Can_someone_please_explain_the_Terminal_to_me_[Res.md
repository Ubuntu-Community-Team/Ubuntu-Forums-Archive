---
title: "Can someone please explain the Terminal to me? [Resolved]"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by kamaboko on 2007-02-20
Hello,

I'm having difficult with the Terminal.  There is only one user account on this computer: me. It's the account I setup when installing Ubuntu.  Now I'm using the terminal to get info using hdparm.  I keep getting access denied messages.  It asks for a password and I input the same one I use to access Synaptic Package Manager.  How is that password different?  I don't get this. 

Thanks,
K

---

### Post by killaray on 2007-02-21
password should be the same

---

### Post by aysiu on 2007-02-21
Can you be more specific than > I'm using the terminal to get info using hdparm.? What *exact* commands are you typing in?

Have you read this?
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by kamaboko on 2007-02-21
for instance, i access the terminal and type in: hdpram -t /dev/hda2
after i select enter it wants a password.  i put in my only password and it says access denied.  but, if i were to access synaptic package mananger and put in the same password, i'm good to go.

---

### Post by 23meg on 2007-02-21
You are using hdparm with *sudo*, aren't you? As in ```
sudo hdparm -t /dev/hda2
```

---

### Post by kamaboko on 2007-02-21
no, i didn't b/c the guide for hdpram didn't say to.  am i to assume that all commands should include sudo?

---

### Post by aysiu on 2007-02-21
> **kamaboko said:**
> no, i didn't b/c the guide for hdpram didn't say to.  am i to assume that all commands should include sudo?
Only ones that require root permissions.

If some guide tells you to > su to root that means to use *sudo*

Here's an example:

**Traditional Linux Distro** ```
user@otherdistro:~$ su
password:
root@otherdistro:~$ cp /etc/apt/sources.list /etc/apt/sources.list.old
root@otherdistro:~$ nano /etc/apt/sources.list
root@otherdistro:~$ exit
user@otherdistro:~$ exit
``` **Ubuntu and Mac OS X** ```
user@ubuntu:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
password:
user@ubuntu:~$ sudo nano /etc/apt/sources.list
user@ubuntu:~$ exit
```

---

### Post by 23meg on 2007-02-21
Administrative commands need sudo as a prefix. Try using it with sudo and entering your user password when requested.

---

### Post by kamaboko on 2007-02-21
thanks.  this info will go into the "save this stuff" file.

---

### Post by gmutt on 2007-02-21
*[COLOR="Blue"][/COLOR]*Very good and informative articles "**_asyiu"_**, just spent the last 2 hrs reading through them all.  I myself might finally be giving up on Windows after purchasing a new PC for my wife and finding out the Vista disk that came with it could not update my old clunker without purchasing another license agreement.  So  I thought I would try Ubuntu out on this ***Not SO Old but Out Dated PC***.  So far I am rather impressed, and have had NO problems so far by reading all the threads and paying attention ... ***Keep up the good job*** ... us newbies appreciate it.

---

