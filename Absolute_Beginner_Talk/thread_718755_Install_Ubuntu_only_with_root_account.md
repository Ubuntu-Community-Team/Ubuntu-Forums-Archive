---
title: "Install Ubuntu only with root account"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by andy_blah on 2008-03-08
Is it possible to install Ubuntu without an other account than root and to pre-set it`s password? I was wondering since there is no person other than me using this computer and I don`t really need the second account with fewer possibilities and permissions.

Thank-you in advance,
>-Andy-<

---

### Post by boeing777 on 2008-03-08
it's not recommeded to use root all the time.  just setup an account just for safety reason.  if you need root permission, it will ask for password anyways.

add sudo in front of commands if you need to run it as root

---

### Post by taurus on 2008-03-08
Maybe you need to read this link first before you decide you don't need the account, logging in as root all the time.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jken146 on 2008-03-08
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

There is no need to runa as root all the time.  In fact, it is a very stupid thing to do.

---

### Post by SloYerRoll on 2008-03-08
Not to mention sudo reminds you that your doing something at the root level. 

Even Ubuntu and Linux GURU's don't stay logged in as root unless they have a specific reason to. 

those four letters you type may save your machines butt one day:)

---

### Post by finferflu on 2008-03-08
What I did on my system was disabling the password for sudo. My logic is that if somebody broke into your system s/he already knows your password in order to use it with sudo. The only problem is when somebody has physical access to your machine. I have no such problems, so I'm fine with that. 
This is the howto I have followed: [http://wiki.archlinux.org/index.php/Disable_root_password_and_gain_su_sudo_with_no_password](http://wiki.archlinux.org/index.php/Disable_root_password_and_gain_su_sudo_with_no_password)

I'm not a security expert though, so be warned that you might be risking in following my advice.

---

### Post by andy_blah on 2008-03-08
I know the possible dangers of using a root session and the existence of the sudo prefix in the terminal command, I want to do this because every folder from any partition does not permit me to read and write with a normal account.

I suppose I should not use a root account and find an alternative.
Thank-you all for assistance ^_^

---

### Post by jken146 on 2008-03-08
You can use sudo commands to do that.  Anything can be done in a normal account in Ubuntu, provided that the user is a member of the admin group (the first user on the machine always is).

If your problem is that you need to enter your password when mounting partitions, you need to *** fstab entries for them.  See [www.psychocats.net/ubuntu/mountlinux](www.psychocats.net/ubuntu/mountlinux) and [www.psychocats.net/ubuntu/mountwindows](www.psychocats.net/ubuntu/mountwindows)

If you were referring to using the file manager, use the command ```
gksu nautilus
``` to get a file manager with root priviledges.

---

### Post by taurus on 2008-03-08
In Unix/Linux, you can only write to your own $HOME due to security reasons.  So, if you need to write something outside of your $HOME, use sudo/gksudo.

And if you insist on logging in as root for your everyday use, you will screw up your machine so fast that you don't know what hits it!  Then, you will be mad because it breaks and nobody can fix it.

---

### Post by andy_blah on 2008-03-08
> **jken146 said:**
> You can use sudo commands to do that.  Anything can be done in a normal account in Ubuntu, provided that the user is a member of the admin group (the first user on the machine always is).

If your problem is that you need to enter your password when mounting partitions, you need to *** fstab entries for them.  See [www.psychocats.net/ubuntu/mountlinux](www.psychocats.net/ubuntu/mountlinux) and [www.psychocats.net/ubuntu/mountwindows](www.psychocats.net/ubuntu/mountwindows)

If you were referring to using the file manager, use the command ```
gksu nautilus
``` to get a file manager with root priviledges.

I was referring at file manager.

I want to thank-you all for your assistance again and sorry for my "midless" attitude :-D

---

