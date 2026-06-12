---
title: "Home directory does not exist after changing username"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by cmac1602 on 2007-10-06
I'm a newbie and in the process of configuring 6.10 the way I want it.  I changed my user name and password and thought that I would change the name of my home directory to reflect the new user name.   

So far so good, but at log in, my new user name and password are accepted but access is denied and the dialogue box says that the listed home directory does not exist.  Having tried a few thing it seems the only thing I can do is correct the error through Terminal in failsafe mode but I've no idea what to tell it!

Any ideas?

---

### Post by Happy_Man on 2007-10-06
Well, you could always enter the command ```
mkdir /home/<username>
```

---

### Post by taurus on 2007-10-06
Boot into recovery mode from GRUB menu and change your old $HOME directory to the new login name.  _Assuming_ your old login name is **john** and the new one that you just changed is **jack**, do

```
mv /home/**john** /home/**jack**
chown -R **jack**:**jack** /home/**jack**
ls -la /home
```
Also, look in /etc/passwd to make sure it is pointing to /home/jack.

```
more /etc/passwd
```
Reboot and see if you can log in as jack now.

```
shutdown -r now
```

---

### Post by cmac1602 on 2007-10-06
Thanks Happy Man - tried it but the command line is saying that it 'cannot create directory' and 'permission denied'

---

### Post by cmac1602 on 2007-10-06
Taurus - you the man! Worked a treat.
Many Scottish thanks - have a whisky on me!

---

### Post by taurus on 2007-10-06
Glad to hear it's working now.  I see that you're Scotsman.  I have a friend in Montrose, mate.

---

