---
title: "Is it possible to run a daemon/process as another user/group?"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-02-02
Eg. when I do a 'ps aux', I see 'root' as the USER for the '/usr/sbin/apache2 -k start -DSSL' process. Is it possible to run a daemon/process as another user/group instead of root in the example above?

Thanks

---

### Post by sas on 2006-02-02
[QUOTE=Akhran]Eg. when I do a 'ps aux', I see 'root' as the USER for the '/usr/sbin/apache2 -k start -DSSL' process. Is it possible to run a daemon/process as another user/group instead of root in the example above?

Thanks[/QUOTE]

Generally yes. However only root may use network ports below a certain number - 1024 I believe.

The quickest way to make a daemon run as another user then you have to setuid the executable file, you'll need to do this at a command prompt:
sudo chmod u+s /sbin/apache2

Running a program is setuid is dangerous though, and shouldn't be done

The other way to do it is to use su <username> then run the daemon.

If you're wanting to do this because of security concerns then as far as I know the apache process that deals with web requests is spawned from the original apache user as a unprivileged user.

---

### Post by Akhran on 2006-02-02
Suppose I have a script or daemon to run as runlevel 2 upon booting up, how do I configure the daemon to run as userA (assuming userA is not the owner of the file)? Or do I need to su as userA and restart the daemon / script each time after the system reboot so that it will run as userA?

Thanks for the help !

[QUOTE=sas]Generally yes. However only root may use network ports below a certain number - 1024 I believe.

The quickest way to make a daemon run as another user then you have to setuid the executable file, you'll need to do this at a command prompt:
sudo chmod u+s /sbin/apache2

Running a program is setuid is dangerous though, and shouldn't be done

The other way to do it is to use su <username> then run the daemon.

If you're wanting to do this because of security concerns then as far as I know the apache process that deals with web requests is spawned from the original apache user as a unprivileged user.[/QUOTE]

---

### Post by steve.horsley on 2006-02-03
The starter script for the daemon will be in /etc/init.d. Since the init script runs as root, adding an su command before launching the daemon should be simple, but of course you need to ensure that the new user has access to all the resources that the daemon needs. Be careful with backups etc when editing these scripts.

---

### Post by Akhran on 2006-02-04
From reading the man file for update-rc.d, I gather that I can get a script to run with sequence number 20 at runlevel 2, 3, 4, 5 with ```
update-rc.d script start 20 2 3 4 5
```

However, where to I add in the 'su command' for the script to run as a user besides root?

Thanks.



[QUOTE=steve.horsley]The starter script for the daemon will be in /etc/init.d. Since the init script runs as root, adding an su command before launching the daemon should be simple, but of course you need to ensure that the new user has access to all the resources that the daemon needs. Be careful with backups etc when editing these scripts.[/QUOTE]

---

