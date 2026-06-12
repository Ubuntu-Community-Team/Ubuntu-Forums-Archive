---
title: "Automatic Login at a Specific Time"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by mindalchemist on 2008-01-27
Is there any way to have it login at a specific time?  I can make it boot up at a certain time, shut down at another, but not the login.  I don't want a straight forward auto login because that makes me feel really insecure.  Any suggestions?

---

### Post by bodhi.zazen on 2008-01-27
I was going to suggest the auto log in feature.

Well, you can disable GDM at boot 

```
sudo mv /etc/rc2.d/S20gdm /etc/rc2.d/s20gdm
```

*Linux is case sensitive.

Your system will boot to a log in screen (not the graphical gdm screen).

Now, set a cron job to start or stop GDM at the times when you want to auto log in / log out.

```
# Start GDM
/etc/init.d/GDM start

#stop GDM
/etc/init.d/GDM stop
```

Run those command (cron) as root.

If you want something more complex, look at expect. This will allow you to use cron to run an expect script (which allows you to input your passwords), keep the script on a removable device, so when the device is NOT present, no auto - login 

[http://www.linuxjournal.com/article/3065](http://www.linuxjournal.com/article/3065)

	[http://www.linux.com/articles/56066](http://www.linux.com/articles/56066)

---

