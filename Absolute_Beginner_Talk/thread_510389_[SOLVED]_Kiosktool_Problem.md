---
title: "[SOLVED] Kiosktool Problem"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by vegipowrd on 2007-07-26
I'm trying to set up about 6 computers with very limited accounts.  I've been banging my head against the wall with Kiosktool.  My goal is to get everything set up on one machine first and then do the others with g4u or some other program.  

I can't seem to get Kiosktool to do **anything** (configure admin tool, add profile, etc).  The error I get says that kiosk is unable to connect to host localhost.  I get the same error if I supply the correct or incorrect root password.  

I'm still new to Linux, so I'm having some trouble figuring out if my entire approach is messed up.  

Any ideas?

---

### Post by phr0ze on 2007-07-26
I don't know Kiosktool but maybe we can find another way to solve your problem. I realise you are trying to setup limited accounts, but what are your trying to actually prevent?

---

### Post by vegipowrd on 2007-07-26
I'm setting up a few computers in a university lab.  They need to access a batch file on the desktop that runs a DOS program (yuck!) using DosBox.  They also must be able to take quizes on a web site.  

I would like to prevent the things that tend to happen in public places (changing desktop, moving files, changing settings) as well as preventing any security problems (accessing a terminal, accessing root directories, installing modules I don't want, etc.).  

Of course most of the most major problems are taken care of with a good root password, but that seems like painfully little protection.

Kiosktool seems well suited to this task, but I'm having problems getting it off the ground.  Is it possible to set it up and have it run on the same computer?  Must I configure it from a server?  Can I configure it from an admin account on the same machine?

---

### Post by dreamersbrow on 2007-07-27
Hello,

I would like to use the Kiosk Admin Tool also, but I have been running into the exact same problem.  I am not all that familiar with KDE but it looked like it was trying to connect to a local server with the fish protocol.  So I installed openssh server but that did not help either.  

Hope someone knows the answer to this.

Thanks.

---

### Post by vegipowrd on 2007-07-27
I think I've been working under the same assumption as you; that I'm missing another package.  The errors I'm getting only point me to where you just looked as well.

---

### Post by dreamersbrow on 2007-07-27
Ok I think I've got it figured out.  This app needs to be run with admin privileges.
Try typing

```
sudo kiosktool
```in a terminal, enter your password, and you should be golden.

Laters.

---

### Post by vegipowrd on 2007-07-27
Dude, you're savin' my day here.  You may be savin' the wall that my head's been banging on.  

I assumed that providing a root password was enough, rather than starting the program with a root level command.  

thanks

---

