---
title: "root privileges to my user"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by srg84 on 2007-05-15
Hi, how to have root privileges in my user, I mean like being a root and not to have to type a password anymore ?

---

### Post by wormser on 2007-05-15
If you did that you would be breaking the number one security rule.  Never log in as root except as needed.  It is not a good idea to do what you want.  I do not see the big deal with entering your password.  You are only prompted when making system changes.

---

### Post by aysiu on 2007-05-15
Why would you want that?

---

### Post by eentonig on 2007-05-15
Sorry for the OP, but this question is quickly getting annoying.

Linux is secure because off several good reasons. One of them, you don't get system right as a normal user. And normal users shouldn't have those right anyhow.

Define 'normal' user? Any user who logs in to the system to do some day to day processing. I.e. (but not limited to) reading mail, working on images, writting documents, browsing the web, .... I have NEVER been asked to enter my sudo/root password when doing one of these things.

IF you want to change your system behavior/configuration, it is wise to be aware of this. And to make sure you intend AND know these changes to happen. This only happens a lot after initial install (when I usually work during an extended sudo session, hence I only have to type my sudo password once for a whole bunch of programs. 

If you want to read more about the good sense in using Sudo
[http://www.psychocats.net/ubuntu/security#sudomakessense](http://www.psychocats.net/ubuntu/security#sudomakessense)

---

### Post by srg84 on 2007-05-15
Thanks but i want to be a superuser with my account, tell me how please, that computer is not connected.

---

### Post by ruscoe on 2007-05-15
> **srg84 said:**
> Thanks but i want to be a superuser with my account, tell me how please, that computer is not connected.
sudo passwd root

The posters above me have already made clear why this is a bad idea, and I hope you've listened, but your system is your responsibility. Do what you want with it.

---

### Post by srg84 on 2007-05-15
thanks but i want to make my account root privileges, not to access with a root account

---

### Post by drowner on 2007-05-15
srg84: what is the difference?

---

### Post by srg84 on 2007-05-15
that i have all the programs configured in my account, root account is crap with brown icons xD

---

### Post by drowner on 2007-05-15
srg84: There is a very good reason why experienced linux users DONT log in with an account with root priviliges.

Seriously, i use a sudo or gksudo like, once a day, and im ALWAYS on my computer. You dont need to use it that often. 

Excuse me for being nosey, but what is it exactly that you are doing that requires you to use sudo so much?

---

### Post by scrooge_74 on 2007-05-15
> **srg84 said:**
> thanks but i want to make my account root privileges, not to access with a root account

By default the first account of the system has administratives priviliges, you only need to type sudo "commands" on a terminal or give your password when doing admin task inside your GUI of choice

---

### Post by srg84 on 2007-05-15
i'm tired of putting my root password every time i want to do something, that's the main reason

30 times a day or so

---

### Post by drowner on 2007-05-15
> **srg84 said:**
> i'm tired of putting my root password every time i want to do something, that's the main reason

seriously, how often do you sudo?

What are you doing that requires so much sudoing?

---

### Post by srg84 on 2007-05-15
> **drowner said:**
> seriously, how often do you sudo?

What are you doing that requires so much sudoing?

trying to configure lirc xDDD

---

### Post by ruscoe on 2007-05-15
> **srg84 said:**
> thanks but i want to make my account root privileges, not to access with a root account
I believe you can use "sudo visudo" in the terminal to give root privileges to your user account but I haven't looked far into it and cannot offer any more advise than that.

---

### Post by drowner on 2007-05-15
> **srg84 said:**
> trying to configure lirc xDDD

And, so thats once.

Well, its your system.

I've typed sda once, instead of sdb.

I wasnt sudoing. Thank god.

---

