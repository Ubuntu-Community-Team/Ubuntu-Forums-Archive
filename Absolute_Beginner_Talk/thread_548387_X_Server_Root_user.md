---
title: "X Server? Root user?"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by owainbills on 2007-09-11
Noob here,

I'm trying to install my nVidia graphics drivers. If I click them and tell them to run in terminal they say i need to be logged in as root. I finally managed to login as root from within the terminal (su command) and now when I try to run them itsays I'm running an X Server and could I please exit it.

I read briefly in a tutorial that you don't NEED to use the terminal, but it's useful. Has anyone got any idea how I can install the drivers/login as root/quit the x server from the gui?

Thanks, Owain

---

### Post by 505 on 2007-09-11
You can't install them from a gui. But to install them, press Ctrl+Alt+F1, this will give you a console. Log in using your normal username and password. Then type:
```
sudo /etc/init.d/gdm stop
```
This will stop X.
Go to the directory where the installer is saved and type:
```
sudo ./installer.run
```
(or whatever the name of the file is, just remember to prefix it with sudo (for root) and ./ (to execute).
After the installation you can start X again by typing
```
sudo /etc/init.d/gdm start
```

Edit: every command with sudo asks for a password. This is *your* password, not some root user account password.

---

