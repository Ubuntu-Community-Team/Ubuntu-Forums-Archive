---
title: "password problem"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by gavicus on 2007-04-23
I'm very new to Linux. I just installed Ubuntu and like the interface a lot.

I have been trying to install the latest Java RE, but am having problems with the "su" command. When I use sudo, I enter the password I used when installing Ubuntu, but su doesn't accept the password.

Now, I'm almost certain I'll have to reinstall, but where should I have entered the superuser password? My main confusion is this: why does sudo accept my password if su doesn't?

I'll appreciate any help you can offer.

---

### Post by Cypher on 2007-04-23
SUDO allows you to execute a command as ROOT using your own password.

SU allows you to become root with the root password and as you've noted there is no root password.

If you want to become root, use
```

sudo su

```

Regards

---

### Post by earobinson on 2007-04-23
```
sudo -s
``` will also work. Note the password to use is the same passowrd as your user password

Howerver if you just want to run one command as root try ```
sudo <command you want to run>
``` this is considered better practice.

---

### Post by jasonlfunk on 2007-04-23
Also, if you want to use su like normal you would need to set a password on your root account.

```
sudo passwd root
```

---

### Post by nickpaton on 2007-04-23
Welcome to Ubuntu and the forums.

The simple way to install such things as Java and multimedia plugins etc etc is to use either Automatix2 or Easy Ubuntu (BTW I have no preference)

Automatix2:

[http://www.getautomatix.com/wiki/index.php?title=Installation]("http://www.getautomatix.com/wiki/index.php?title=Installation")

Easy Ubuntu:

[http://ubuntuforums.org/showthread.php?t=190535]("http://ubuntuforums.org/showthread.php?t=190535")

An excellent site for general HOWTO's is the Psychocats site:

[http://www.psychocats.net/ubuntu/index.php]("http://www.psychocats.net/ubuntu/index.php")

Get back to us with any queries and good luck!

---

