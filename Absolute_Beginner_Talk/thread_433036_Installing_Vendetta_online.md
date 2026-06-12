---
title: "Installing Vendetta online"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by Talon-Skave on 2007-05-04
Hey, I'm very new to Linux/ubuntu. (3days lol) so I apologize if this is an obvious answer.

Firstly I'm using ubuntu 7.04, and im trying to install Vendetta online
 
[http://www.vendetta-online.com/x/download?platform=linux&accept=y](http://www.vendetta-online.com/x/download?platform=linux&accept=y)

I have downloaded to client and the website says

"To install Vendetta, type sh ./vendetta-linux-x-installer.sh. You do not need to be root; install it under your usual account."

So I have typed this into the terminal and get the following error "sh: Can't open ./vendetta-linux-x-installer.sh"

I downloaded the client to my desktop. So how can I get it to install? again sorry if its obvious but I'm very new to Linux.

Thanks in advance.

---

### Post by Slackpacker on 2007-05-04
you probably need to navigate to the download directory first, i.e. ```
cd Desktop
```

---

### Post by Coffeemike on 2007-05-18
I had to do this to make it work.  Type in from the terminal:

mkdir bin
sh ./vendetta-linux-ia32-installer.sh

The first line is to create the "bin" subdirectory that the installer will need.  The second line is the line that the Vendetta should have shown because that is the actual file that is downloaded.

Mike

---

### Post by b3n0 on 2007-06-12
Hey I i cant get it going either. That coding doesn't seem to work for me.

---

### Post by nelcon24 on 2007-11-27
this is how to install vendetta

save it to your home dir (/home/username)
where username is your username
then open a terminal and type

mkdir bin
chmod +x vendetta*
./vendetta*

the first line makes the directory needed by the installer
chmod +x vendetta* changes the file you downloaded permissions to allow it to be executed (ran, like a program should be)
and the third line starts the installer, good luck ;-)

---

### Post by MechWarrior001 on 2008-06-07
I'm trying to install VO as well, but when I type that in Terminal I get:

```
bash: ./vendetta-linux-ia32-installer.sh: /bin/sh: bad interpreter: Text file busy

```

Now what?

---

