---
title: "Please Report"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by andy_6590 on 2007-08-09
I tried to install a program and it said to stop an application called update manager or synaptic package manager. when I tried opening these programs I got this error message:

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

How do I fix this, to be honest I don't know how I have caused it either so if anybody knows how to stop this from happening again please post. 

Thanks

---

### Post by Inxsible on 2007-08-09
you cannot have Add/remove or Synaptic open when you are installing stuff from the CLI or vice-a-versa. Simply close the apps that you are not using and try again.

---

### Post by Dr Small on 2007-08-09
Did you try running 'dpkg --configure -a' ?

---

### Post by andy_6590 on 2007-08-09
In the Terminal you mean? Yes I have tried but I get this as well.

andrew@andrew-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
andrew@andrew-desktop:~$ 

Which I also don't know how to get "Superuser Privileges".

Thanks for the reply.

---

### Post by splintercellguy on 2007-08-09
Put the word sudo before dpkg ... and when it asks for password enter your account password.

---

### Post by Dr Small on 2007-08-09
If you need to run something as a super user, place 'sudo' in front of it.
Example: 'sudo dpkg --configure -a'

Dr Small

---

### Post by andy_6590 on 2007-08-09
It asks for a password but it wont let me type, any reason for this?

---

### Post by Dr Small on 2007-08-09
The terminal doesn't output what you type on the screen, but it still is typing.
Just type your password, and hit enter. You won't be able to see it, but the system will read it.

Dr Small

---

### Post by Yes on 2007-08-09
It does let you type, it just doesn't show what you're typing.  Type in your password and press enter, and it should work.

---

### Post by st33med on 2007-08-09
No, no. It's typing and receiving your password, even if it's empty. Just input the password.

---

### Post by andy_6590 on 2007-08-09
Yes got it to work thanks for all your help I'm new to Linux if you can't tell.

One more question I opened Synaptic Package Manager and it said:

"You have 1 broken package on your system!

Use the "Broken" filter to locate it."

Whats the broken filter? and how do I access it?. Thanks again for all your help.

---

### Post by forestpixie on 2007-08-09
in syanptic manager - Edit > Fix Broken Packages

---

### Post by andy_6590 on 2007-08-09
All is fixed now. Only 1 more problem to solve if you would care to look. I have posted a thread in the forum here is a link.

[http://ubuntuforums.org/showthread.php?t=521226](http://ubuntuforums.org/showthread.php?t=521226)

If any addition information is needed just ask and I will post it immediately. Thank you all for your help it is much appreciated.

---

