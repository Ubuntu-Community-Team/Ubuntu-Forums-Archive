---
title: "Login name and password problem"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by drifternel on 2006-06-23
I finally managed to get dapper installed (well nearly) using the alternate cd and good advice off these forums.
Problem, the final login stage of the installation is saying my username/password unrecognised.
Really cant believe how I managed to be this stupid as I always use the same combination with Linux (but obviously mistyped and didnt notice, the football was on!).
Any way round this folks without reinstalling?

---

### Post by x64Jimbo on 2006-06-23
If you can reboot and start in GRUB and select the recovery mode, it will log you in as root, and you can change your user's password from there by running this:
passwd <username>
it will ask you to confirm twice.

---

### Post by Apple 101 on 2006-06-23
Did you run an OEM installation?  I did that at first, and the same problem happened to me.  Here's how I fixed it:
In the GRUB menu, select the boot option that allows for emergency access.  When you get to the prompt, type:
passwd [username] and change your password that way.  You may need to create your username and password.

If you did do an OEM installation, you will find that hardly any programmes are installed by default.  This made me reinstall as a normal installation.

---

### Post by drifternel on 2006-06-23
great
only thing is, I'm not sure if its my username *or* password thats wrong!
If its the username it will be a bigger problem I suspect?

---

### Post by Apple 101 on 2006-06-23
I found that it was both.  It doesn't matter though.  In the recovery mode, you can (re)create both the username and password using the *useradd* and *passwd* commands.

---

### Post by drifternel on 2006-06-23
ok thats even better news - these forums are excellent!
I'm brand new to Linux so when I start recovery mode, what commands (if any) do I need to type to even get to the password part?
Or is it self explanatory as it goes along?

---

### Post by Apple 101 on 2006-06-23
Firstly, try:
passwd <your username here>

If that is not recognised, use
useradd (or adduser) <your username here>

Then you can set a password when prompted.

---

### Post by drifternel on 2006-06-23
sorry, didnt really understand what exactly I need to type apple...
Is 'passwd' a command to type in before typing in my username?
The next instruction - do I type 'useradd' then hit return then add my username?
Apologies for the extremely basic questions but this is so new to me!

---

### Post by Stolie on 2006-06-23
I believe that the syntax would be to use the "passwd <username>" command, to see if the username exists.. If it does, it will ask you to change your password. If the username doesn't exist, then it will tell you that. 

At which point you would use "useradd <username>" I believe, then set the password accordingly.

Hope this clarifies things!

---

### Post by Apple 101 on 2006-06-23
[QUOTE=drifternel]sorry, didnt really understand what exactly I need to type apple...
Is 'passwd' a command to type in before typing in my username?
The next instruction - do I type 'useradd' then hit return then add my username?
Apologies for the extremely basic questions but this is so new to me![/QUOTE]Sorry, if I didn't make the instructions clear enough.  I've fixed it now.

Stolie:  Thanks for clearing up my previous post into something easily understandable.:D

---

### Post by drifternel on 2006-06-23
I think now I understand the logic of whats going on now.
Thanks to you all in this thread...that has clarified things.
Much appreciated.

---

