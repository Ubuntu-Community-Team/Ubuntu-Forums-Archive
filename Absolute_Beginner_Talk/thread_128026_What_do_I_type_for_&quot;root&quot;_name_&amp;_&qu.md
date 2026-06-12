---
title: "What do I type for &quot;root&quot; name &amp; &quot;root&quot; password"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-02-10
I tried to Log Out & Lag In with ROOT priviledges, but I do not know what are my ROOT:

1. name &
2. password

When I installed Ubuntu, I was only asked for "MY" username & password.

I was never asked to enter a "ROOT" username & password.

What do I type in, as "ROOT" username & password to Log in as ROOT?

Many Thanks.

---

### Post by Davyp on 2006-02-10
Yeah ubuntu encourages the use of sudo for accessing root priveliges. This is for security reasons and probably for useability reasons too.

Check out this wiki for a bit more info:

[https://wiki.ubuntu.com/RootSudo?action=show&redirect=UsingSudo](https://wiki.ubuntu.com/RootSudo?action=show&redirect=UsingSudo)

---

### Post by TrendyDark on 2006-02-10
There isn't really a ROOT account, it's just a security messure. The root password is your password, if your account was the one created on startup.

---

### Post by dvarsam on 2006-02-10
I know how to do it from the Terminal:

1. From menu select:                   "Applications\Accessories\Terminal"

2. Type:                                         "sudo -i" 

3. Enter my user:                          "my_password"


What I can not figure out, is:
How to do it from the Log In Screen?

1. From the Menu, I select:            "System\Log Out"

2. Then, in the Log-in srceen:

    a. For user name, I enter:           "root"

    b. For password, I enter:             "my_password"


But Ubuntu does not let me Log-in...

What do I have to type in the user name area, instead of root?

Is it "admin"?

---

### Post by Iowan on 2006-02-10
> 
What I can not figure out, is:
How to do it from the Log In Screen?
The short answer is:
You don't.
There are ways to activate the root account, but you don't really want to.  If you have experience on other Linux systems, you know that most administrative jobs are done logged is as "root".  Ubuntu (by default) has no active "root" account - that function (as mentioned by others) is carried out bu the **sudo** command and the user password.

---

### Post by dvarsam on 2006-02-10
Ok, then I have a question:

How can I copy & paste Files (& Folders) from one Hard Drive to another without having to go through the "tons of commands" typed at the command prompt?

Cause I keep typing:

mount, unmount, sudo, password, ls, cd, fdisk -l, cp, rm, e.t.c, e.t.c. ....

I want to keep things simple & thought that by logging-in as root (superuser), I can avoid all this hassle....

There MUST be some other way, ...

Is there is some other way, to do copy & paste easier & faster?

Cause if I drag & drop, I get the "This is only permitted to the root user"....

I am really stuck here guys & I am forced to memorise TONS of commands....

I like learning the commands & I am really happy & excited that I am learning Linux, but it is frustrating to do EVERYTHING in command prompt!

Please Help!!!

---

### Post by aysiu on 2006-02-10
If you're using Gnome, create a launcher for the command ```
gksudo nautilus
```

If you're using KDE, create a launcher for the command ```
kdesu konqueror
```

---

### Post by Davyp on 2006-02-11
Another option might be to have the hard drives automatically mounted in the boot process, when you turn your computer on.

To enable this open up /etc/fstab in a text editor and add the word 'auto' (or if there is the existing word 'noauto' change it to 'auto') under the options column in the row of the appropriate hard drive. If you've not done this before I would make a backup of the file before making any changes.

After doing this next time and everytime you turn your computer on you can just open your window manager and the hard drives will be accessible.

---

