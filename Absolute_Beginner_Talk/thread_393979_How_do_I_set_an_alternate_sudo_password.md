---
title: "How do I set an alternate sudo password?"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by donkyhotay on 2007-03-26
I don't like having SUDO use the same password I use to login. I do like how I can use it to prevent logging on to my system with username root though. Is there any way to configure sudo to only grant access with a different password besides a users login password? I've been reading the documentation on sudo but haven't seen anyway of doing this. Now I'm not trying to simply set up a root password (I know how to do that) and that would allow logging in directly as root which is something I am trying to avoid. I want sudo to use a different password then the one I use for logging in when it grants permissions.

---

### Post by compmodder26 on 2007-03-26
As far as I know, sudo isn't set up to do that.  It would probably require modifying the source code.

---

### Post by juantovarm on 2007-03-26
I do not think that is possible.

---

### Post by igknighted on 2007-03-26
Not sudo, but you can enable the root account and give that a separate password.  You would then have to use "su -" to get root privileges and then your command instead of "sudo command".  This is how most of the rest of the linux world does it.  Ubuntu is the odd bird using sudo for everything.

---

### Post by Bachstelze on 2007-03-26
It's a bit complicated but you *can* enable the root accound but disable the login (i.e. you can _only_ use su to become root) :

```
sudo -i
passwd
*set the password here*
chsh -s /bin/false
echo "/bin/false" >> /etc/shells
visudo
*comment the %admin line out to disable sudo*
exit

```

Now you can become root with :

```
su -s /bin/bash
```

---

### Post by igknighted on 2007-03-26
Since su -s /bin/bash is an awkward thing to type any time you need root, I would recommend aliasing that to something easier to type.

---

### Post by Bachstelze on 2007-03-26
By the way, the fact that you cannot login as root by default has nothing to do with sudo. It is very possible to install sudo on other systems that allow root logins (sudo existed way before Ubuntu) and it is also possible to disable root logins - the way I told you for example - when you don't have sudo installed.

Also, I just realized that what I told you will work fine in a terminal but might cause problems if you want to do GUI stuff as root, since Ubuntu expects gksudo to be there and usable...

---

### Post by igknighted on 2007-03-26
> **HymnToLife said:**
> By the way, the fact that you cannot login as root by default has nothing to do with sudo. It is very possible to install sudo on other systems that allow root logins (sudo existed way before Ubuntu) and it is also possible to disable root logins - the way I told you for example - when you don't have sudo installed.

Also, I just realized that what I told you will work fine in a terminal but might cause problems if you want to do GUI stuff as root, since Ubuntu expects gksudo to be there and usable...

You can use gksudo when logged into a terminal as root to do this.  At least kdesu works like that in Kubuntu, I assume gksudo works the same.

---

