---
title: "ubuntu and gnome don't work any more, please help"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by idrinkwhisky on 2007-02-02
Hi,

My ubuntu is messed up. I can't log in anymore using normal session. Only "failsave gnome" works. Whenever I log in using failsave mode i get 2 error messages:

```

"user's $home/.dmrc file is being ignored. this prevents the default session from being saved. File should be owned by user and have 644 permissions. 
user's $home dir must be owned by user and not writable by other user's." 
```
the second problem is:

```

"there was error starting gnome settings deamon. Error message was: 
unable to determine the address of the message bus (try man dbus-launch and man dbus-deamon for help). gnome will try to restart the settings deamon next time" 
```

I hope you guys can help me. Thanks

---

### Post by bodhi.zazen on 2007-02-02
> **idrinkwhisky said:**
> Hi,

My ubuntu is messed up. I can't log in anymore using normal session. Only "failsave gnome" works. Whenever I log in using failsave mode i get 2 error messages:

```

"user's $home/.dmrc file is being ignored. this prevents the default session from being saved. File should be owned by user and have 644 permissions. 
user's $home dir must be owned by user and not writable by other user's." 
```

For the first one you will not need sudo if you are root (boot to recovery mode), 

.drmc file permissions, in a terminal: (use first set)

> 	sudo chmod 644 .dmrc
	sudo chown user_name .dmrc
	sudo chmod 755 /home/user_name
	sudo chown user_name /home/user_name

	OR, if that fails:

> 	sudo chown  user_name /home/user_name 
	sudo chmod 755 /home/user_name
	sudo rm -rf /home/user_name/.dmrc

Where  user_name = your log-in name :p

> the second problem is:

```

"there was error starting gnome settings deamon. Error message was: 
unable to determine the address of the message bus (try man dbus-launch and man dbus-deamon for help). gnome will try to restart the settings deamon next time" 
```

I hope you guys can help me. Thanks

Not sure about the second one ...

---

### Post by x64Jimbo on 2007-02-02
You need to be sure to use the recursive flag when changing ownership of a directory rather than a file. So for instance, when you're changing ownership of your home directory, you need to do it this way:
sudo chown -R <username> /home/username

That "-R" is extremely important, because it follows the directory structure all the way down and changes the permissions on all sub directories and files.

---

### Post by idrinkwhisky on 2007-02-02
I did what you guys suggested and everything is OK now :) 
So thanks a lot

---

