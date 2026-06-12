---
title: "password problems"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by nickmayfield on 2007-10-02
ok i'm about 3 days old using ubuntu feisty
i'm trying to make my nvidia card work and when i'm in the terminal screen i type su and hit enter for password. but my password doesn't work. i only use one password and it works for everything else. i also can't use sudo. i honestly don't understand all of this but this is the screen:

nick@NicksComputer:~$ su
Password: 
su: Authentication failure
Sorry.
nick@NicksComputer:~$


does it matter that i installed this off of a live cd?

---

### Post by dwhitney67 on 2007-10-02
When you attempt to perform an "su", you are essentially switching to the root user.  You need to enter the root password, not the password for your personal account.

Don't know the root password?  Then set it:

$ sudo passwd

Btw, when a "sudo" is performed, then you enter your personal password.  If you do not have sudo privileges, then you will not be able to run commands with the "sudo" prefix.  Sudo temporarily gives a regular user root-privileges.

---

### Post by nickmayfield on 2007-10-02
thanks a bunch.

---

### Post by bodhi.zazen on 2007-10-02
That works, but FYI Ubuntu uses sudo and disables the root password.

You can become root with:

```
sudo -i
```

you can re-lock your root account, is you so desire, with :

```
sudo passwd root -l
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by dwhitney67 on 2007-10-02
Teach Linux, not Ubuntu is my take on it.  A root account _does exist_ under Ubuntu; just because it is obfuscated by the Ubuntu creators doesn't mean it does not exist.

---

### Post by bodhi.zazen on 2007-10-02
> **dwhitney67 said:**
> Teach Linux, not Ubuntu is my take on it.  A root account _does exist_ under Ubuntu; just because it is obfuscated by the Ubuntu creators doesn't mean it does not exist.

LOL

I agree with you 100 % . There are reasons why Ubuntu is set up the way it is. The intent is not to "hide" or "obscure" root but rather to increase security by locking the root account.

There is nothing wrong with setting a root password, but please take the time to understand how and why Ubuntu is structured the way it is and understand the security implications of setting a root password on Ubuntu.

You will see this too is teaching Linux.

It it better ? This I do not know, but I have come to appreciate it. Please give advice and make changes to your system, Ubuntu or otherwise, with understanding, this is all I ask.

su or sudo, pick your poison.

EDIT: One parting tip, you may want to use su - rather then su

---

