---
title: "[SOLVED] ssh onto ubuntu server from windows"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by keymoo on 2007-09-05
Hi there,

I have just installed a feisty ubuntu server and i want to connect to a shell from my windows machine, is that possible? If so, what do I need to do on the server and client ends?

Thanks!
keymoo

---

### Post by jvc26 on 2007-09-05
You need to have ssh installed on the server, and enable logging in of your username from the sshd_config file.

```

sudo apt-get install ssh

```
Then:
```

sudo nano /etc/ssh/sshd_config 

```
And, at the bottom of the file add:
```

AllowUsers username

```
Also change the line:
```

PermitRootLogin yes

```
to
```

PermitRootLogin no

```

Once you have made the changes to the sshd_config, you need to restart the service:
```

sudo /etc/init.d/ssh restart

```

Then on the windows machine you need to install Putty, and then log in via that.

Il

---

### Post by keymoo on 2007-09-05
Cool, that worked - I'm using it already! Thanks.

One question: when I installed ssh, ubuntu asked me for the server CD rather than getting the packages from the internet. Can I configure apt-get to install from internet by default instead of the CD?

Thanks.

---

### Post by jvc26 on 2007-09-05
Yes you can, I'd probably do it via:
```

sudo nano /etc/apt/sources.list

```
Then either comment out (put a # in front of the line) or delete the lines at the top of the file talking about the cd.
Then:
```

sudo apt-get update

```
And you're sorted.
Il

---

### Post by keymoo on 2007-09-05
Thanks, worked fine.

---

