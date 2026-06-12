---
title: "Root password"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by Ink on 2006-08-01
Im a bit new to linux and all... I just installede xubuntu, but i never entered a root password.. dont remember if it asked for it:P

It asked for my name, made a normal account and i gave it a password..

I have tryed my password for the normal account as root password, and I have tryed to leave it blank. That didnt work..

How do i get the root password?

---

### Post by Tomosaur on 2006-08-01
You shouldn't ever need to login properly as root. Ubuntu uses a command called 'sudo' to grant your root privileges when you need them. To use it, just put 'sudo' in front of whichever command you're trying to run, for example:
```

sudo apt-get install blah-blah-blah

```

The password it will ask you for is just your normal password.

Note that sudo should only be used for command line programs. If you want to run a GUI program using sudo, change it to 'gksudo' instead.

---

### Post by timetunnel on 2006-08-01
It's explained here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by AndyCooll on 2006-08-01
Ubuntu doesn't use root as such. It automatically gives the first created user special administrative powers.

Therefore your "adminstrative" password is password you use when you logon.

:cool:

---

### Post by SeanHodges on 2006-08-01
Sudo is a much better way of managing root access. It's also convenient because you always know when you're doing something risky - gksudo also makes running GUI apps as root more simple (dont have to su in a terminal and run the app from there, just add gksudo at the beginning of a shortcut).

Some people still prefer to use su, mainly ones that use their machine as a server and want to do a number of privileged things in one go. Although **I strongly recommend you don't do this** unless you have a good reason, you can reinstate the root account by typing:

```
sudo passwd root
```

And set a password. You should disable the account as soon as you dont need it by typing:

```
sudo passwd -l root
```

---

### Post by Ink on 2006-08-01
ok! thx:D

but why cant i apt-get amsn?

---

### Post by T700 on 2006-08-01
> **Ink said:**
> ok! thx:D

but why cant i apt-get amsn?

Because you have to type: ```
sudo apt-get amsn
```

The "sudo" will invoke root authority.

Paul

---

### Post by moma on 2006-08-01
Sudo vs su.
o--> [http://ubuntuforums.org/showthread.php?p=1283789#post1283789]("http://ubuntuforums.org/showthread.php?p=1283789#post1283789")

---

