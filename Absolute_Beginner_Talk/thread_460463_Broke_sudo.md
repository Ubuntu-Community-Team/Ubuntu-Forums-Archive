---
title: "Broke sudo"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by jonward0690 on 2007-05-31
Now when I run a sudo command it says "jon@jon-desktop:~$ sudo
>>> sudoers file: syntax error, line 13 <<<
sudo: parse error in /etc/sudoers near line 13
jon@jon-desktop:~$"

---

### Post by annda on 2007-05-31
hmm, more details, please. what does your sudoers file look like?

---

### Post by aysiu on 2007-05-31
> **jonward0690 said:**
> Now when I run a sudo command it says "jon@jon-desktop:~$ sudo
>>> sudoers file: syntax error, line 13 <<<
sudo: parse error in /etc/sudoers near line 13
jon@jon-desktop:~$" This should help: [http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by jonward0690 on 2007-05-31
I wish i could tell you but anything to do with sudo i get a error

---

### Post by digitalbenji on 2007-05-31
if you can post your /etc/sudoers file, we can identify the problem.  sudo reads the sudoers file for configuration information, you probably just have some bad syntax in there that is confusing it.  To edit the file, you're going to need to use one of the tty terminals (ctrl+alt+f1 - f6) and login as root.  First, post the output of cat /etc/sudoers so that we can identify the problem for you, that way when you log in to the tty you'll know exactly what you need to do.  

Thanks,

---

### Post by Bachstelze on 2007-05-31
He cannot view the sudoers file if he doesn't have sudo rights since the file is chmodded 440. Recovery mode is the only option.

---

### Post by aysiu on 2007-05-31
> **HymnToLife said:**
> He cannot view the sudoers file if he doesn't have sudo rights since the file is chmodded 440. Recovery mode is the only option.
More details in the link I posted earlier (how to boot into recovery mode, what the /etc/sudoers file *should* look like)

---

### Post by digitalbenji on 2007-06-01
That's a good point, I had forgotten that.  The only way he can view it then is by logging in as root, or booting into recovery mode.

---

### Post by jonward0690 on 2007-06-01
Yea I spent hours tring to fix it and I just ended up reinstalling Ubuntu

---

