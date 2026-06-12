---
title: "I am Root!"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by TuxIsCute on 2007-08-13
Quick question, when I set up Ubuntu, I set up a user "atd" with a password.  I didn't set up any other user.  When I need to do something as root, I give the password that I set up.  My question, is the "atd" user on my system then the root user?  If so, is my computer at risk?  Should I add another account and use that one instead?  Can I still add programs to my computer without haveing root?

I thought that as long as no one else had that password (which no one does) that I would be safe.  If I try to use sudo to install something, I still have to give that password.  I thought that running the command sudo su then giving the password made me root as that is the only time it says root@<location> in the terminal window.

I read this thing on the net, however, that said not to run linux as root user unless one wants to change the system.  I install something usually many times that I get on.  I use the add\remove and don't add in any other repositories except for the Wine one.  And even then I have to give that password.  If I am signed in as this account can I get a virus simply by loading a page on the net using firefox that loads it like in Windows?

I don't know.  What are your thoughts?

Tux is Cute.

---

### Post by aysiu on 2007-08-13
Here are my thoughts:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by koganinja89 on 2007-08-13
yes and no... you only have root (administrative powers) access for that one proccess. it is like 'sudo something' in the terminal you only get super user status for that one command.

---

### Post by Romanus81 on 2007-08-13
The only way you can log in as root is at the log-in screen to type root as your username (you might need to create a root password for this, not sure where, I never did and I'm not on my ubuntu pc so I can't check). 
Whenever you type in "sudo" in terminal it means you want to run whatever command as if you were root. You give in your password. Sudo su makes it so that everything you type in has the sudo understood (I think) so that you don't need to keep writing sudo. Sudo was made so that it is easier to edit files as root without logging in and out all the time.
You are correct that it is a security risk to be logged in as root and use root as your main user, but if you log in as "atd" then you are not root. The only way to log in as root, that I am aware of, is to log in at the main screen.

---

### Post by koganinja89 on 2007-08-13
Vista does the same thing every two seconds though... You are really never more at risk except by your own user error when you are changing settings like that.

---

### Post by TuxIsCute on 2007-08-13
> **Romanus81 said:**
> The only way you can log in as root is at the log-in screen to type root as your username (you might need to create a root password for this, not sure where, I never did and I'm not on my ubuntu pc so I can't check). 
Whenever you type in "sudo" in terminal it means you want to run whatever command as if you were root. You give in your password. Sudo su makes it so that everything you type in has the sudo understood (I think) so that you don't need to keep writing sudo. Sudo was made so that it is easier to edit files as root without logging in and out all the time.
You are correct that it is a security risk to be logged in as root and use root as your main user, but if you log in as "atd" then you are not root. The only way to log in as root, that I am aware of, is to log in at the main screen.

Thanks for the reply.  I was reading something on the net and it just got me thinking I was doing something wrong.  Now I'm not as worried.

BTW: That site from the guy that could have just as easily written an answer, was nearly exaclt like the site that sent me here to ask this question in the first place, but thanks anyway.

---

### Post by Paul133 on 2007-08-13
Aysiu's site explains the concept of root and security as it pertains to Ubuntu. No all distros are like this. Many other distros don't have "sudo"; you have to login as root and use the root password. With Ubuntu, you never see the root password. You just use 'sudo' and then your user password when you want temporary rot privileges. 'sudo su' allows you to change user, to root by default but 'sudo su adt' would let you change to your account.

---

