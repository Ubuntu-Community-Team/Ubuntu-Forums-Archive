---
title: "Restricting ssh login my user name"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by echo $USER on 2006-03-30
Correction: Thread name should be "restricting ssh login BY user name"

Is this possible?

Say if I had user abc, which is the system admin with sudo passwd, and user xzy, that does not have sudo privilages.  Can I deny user abc from logging in ssh, but allow user zxy to log in?

I disabled root login in the sshd.conf, but since there is no real root account this is not working.  I can still log in with user abc with the password that is the sudo password.

Thanks for the help!

---

### Post by benguin on 2006-03-30
Sure you can do that.

Edit the openssh daemon config file under /etc/ssh/sshd_config, and add two lines like this:
```

DenyUsers abc
AllowUsers xyz

```
I'm guessing the DenyUsers entry may not be necessary, but I am a little paranoid about security! heh.

Oh and don't forget to restart the sshd daemon
```
sudo /etc/init.d/ssh restart.

For my own home box, I allow only one user to remotely login, and I have this setting:

 [code]
DenyUsers all
AllowUsers my_user

```

Only my_user can login via ssh in this case.

Hope that helps.

-J-

---

### Post by opus on 2006-03-30
One step further in security is to disable password based authentication and enable only key based authentication.  Then you generate a private and public key pair, copy your public key to the ssh keys file and you will be authenticated based on that.  

Sorry I don't have the details on that, but most of it can be found in the sshd config file.

Aaron

---

### Post by echo $USER on 2006-03-30
Thanks for the help guys.  Just the info I needed.  Key authentication is something I know nothing about.  Sounds like a future project.  Thanks again.

---

