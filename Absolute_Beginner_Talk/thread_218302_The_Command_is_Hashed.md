---
title: "The Command is Hashed"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by mumebuhi on 2006-07-18
I am trying to change a command to point to a different program.

Currently,
$ type jmeter
jmeter is hashed (/usr/local/jmeter/bin/jmeter)

#1 What does "is hashed" mean?
#2 I did not set this in the .bashrc file. How does Ubuntu create this "link"?
#3 How do I change the 'jmeter' command to point to a different location, e.g. /opt/jmeter/bin/jmeter?

Thank you beforehand


Buhi

---

### Post by taurus on 2006-07-18
Do you happen to have /usr/local/jmeter/bin/ in your path?  Change it to /opt/jmeter/bin/ then!!!

---

### Post by Ragazzo on 2006-07-18
> **mumebuhi said:**
> 
#1 What does "is hashed" mean?


When a command is executed, the shell must usually search through different places to find it. To speed up things the command's path can be saved (hashed) so that you don't need to go through the search process again. Here's an example:

```

~> type gedit
gedit is /usr/bin/gedit
~> gedit
~> type gedit
gedit is hashed (/usr/bin/gedit)
~>

```

When I first called gedit (can be any program), it wasn't hashed but if I call it second time, it will be hashed.

---

### Post by mumebuhi on 2006-07-18
Thank you, Ragazzo. It is clear now.

---

### Post by mumebuhi on 2006-07-18
$ echo $PATH
[contains /usr/local/jmeter/bin]

You are right, taurus!

The thing that I don't understand is that I did not set it in ~/.bashrc file. Where should I make the change?

---

### Post by taurus on 2006-07-18
Could be in /etc/bash, /etc/profile, or even /etc/environment!!!

---

### Post by mumebuhi on 2006-07-18
Oh yes, it is defined in /etc/bash.bashrc.

Thank you very much, taurus!

My /etc/environment contains
LANGUAGE="en"
LANG=en_US.UTF-8

What is this file for? Another place to define user's environment variables?

---

### Post by taurus on 2006-07-18
> **mumebuhi said:**
> Oh yes, it is defined in /etc/bash.bashrc.

Thank you very much, taurus!
You're welcome.

> 
My /etc/environment contains
LANGUAGE="en"
LANG=en_US.UTF-8

What is this file for? Another place to define user's environment variables?
Yip.  That's for the whole system.

---

### Post by mumebuhi on 2006-07-18
Woohoo! Now, it makes a perfect sense!
bash and profile are for individual users; whereas, environment is for the system.

---

### Post by taurus on 2006-07-18
Actually, for individual setting, you do it in ~/.bashrc.  For the whole system, you set it in /etc/bash, /etc/bash.bashrc, /etc/profile, or /etc/environment.

---

