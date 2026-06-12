---
title: "Unable to log into console"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by RBaker on 2007-04-05
Hello all,
I have installed Ubuntu 6.10,but I am unable to log into the console"ctrl Alt F1,F2..."
I receive the following message 
Module is unknown
Then I am back at the login prompt.
 I am a new user so please be gentle
any help would be appreciated,
Thanks,
Rob

---

### Post by vruum on 2007-04-05
are you able to login from the graphical login manager? if you are, can you launch a terminal from there (applications->accesories->terminal (i think)
also, can you give a little more information, like when exactly does the "module is unknown" error appear, after you've typed your password or before? and how did you install (live cd or alternate) did you get any errors doing install.

---

### Post by RBaker on 2007-04-05
Hi,
Yes I am able to login into the graphical login, I can run all apps in the graphical including the terminal. I get the error message after the password is entered. I installed using the LiveCD.
Thanks,

---

### Post by vruum on 2007-04-05
okay, well, I might be a little out of my depth here. so this might go nowhere but, anyway. try opening a terminal and type xterm, does the first terminal spit out any error messages? then try, from the newly opened xterm, to run ```
 sudo apt-get update
``` and type in your password and see if it is accepted.

---

### Post by RBaker on 2007-04-06
I ran xterm the sudo apt and I received warning messages about signatures could not be verified. Thats the only warnings that I received

---

