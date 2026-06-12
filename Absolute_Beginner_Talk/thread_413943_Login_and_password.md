---
title: "Login and password"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by ADP on 2007-04-19
I installed ubuntu Breezy Badger on a new hard drive but lost my login name and password and can't get back in . I also want to install Dapper. Can anyone tell me how to reset the access?

---

### Post by taurus on 2007-04-19
Do you remember your login name?  Boot into recovery mode from GRUB menu and look at the output of this command to see what's your login name is.

```
ls -la /home
```
Assuming it's **adp**, change the password with

```
passwd **adp**
```
Reboot and see if you can log in as **adp** with the new password.

```
shutdown -r now
```

---

### Post by aysiu on 2007-04-19
Boot into recovery mode.

Then type ```
cd /home
ls
``` That should remind you what you username was. Let's just say, for this example, that it's *adp*. You reset the password by typing ```
passwd adp
``` Then reboot: ```
reboot
```

If you don't know how to boot into recovery mode, this link will help you:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

Don't install Dapper. Install Feisty Fawn. It just came out today!

---

