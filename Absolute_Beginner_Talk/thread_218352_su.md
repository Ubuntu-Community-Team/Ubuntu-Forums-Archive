---
title: "su?"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by sjoppery on 2006-07-18
Ive used a few distros of linux and decided to try ubuntu. I am having trouble loging in as su using a terminal. I am using the administrator password I have set up which works for everything else but it says
[I]    su: Authentication failure
    Sorry.[/I]
Can anyone help me please. ](*,)

---

### Post by T700 on 2006-07-18
Please check the Where's Root link in my sig.  Short answer:  Ubuntu uses a different way of accessing root permissions that does not use a traditional root account.  To use a command as root, you preface it with either "sudo" for non-graphical apps or "gksudo" for non-graphical apps.  
For example: ```
sudo apt-get install xyz
```

Paul

---

### Post by taurus on 2006-07-18
What password are you talking about?  The root account is locked as default so you need to create a password before you can "su -" to it.  Log in as the user that you have created and open a terminal and type

```

sudo passwd root
(enter your own password)
(enter new root password)
(re-enter new root password)

```
Then

```

su -

```

---

### Post by Bloch on 2006-07-18
ubuntu does not have su enabled by default. The default is to use the sudo command.
sudo <command>
e.g.
sudo nautilus
to run the file browser as root
and press enter. Your password will be requested. If you perform another sudo commandline within a couple of minutes it will not request your password a second time.

You can use 
sudu su
to become root user. I've never had to.


using sudo by the way is the way things are done on OS X.

---

