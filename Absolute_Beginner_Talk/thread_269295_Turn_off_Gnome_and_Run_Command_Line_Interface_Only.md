---
title: "Turn off Gnome and Run Command Line Interface Only"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by kimvall on 2006-10-01
Hello, I have a little machine that I only run SSH/FTP on. Therefor I don't need Gnome and I wanna turn it off so that I can save system resources.

I.e. when I press the power button, I want Linux to start but not start Gnome, only a command prompt.

Thanks in advance.

---

### Post by skymt on 2006-10-01
You can do that by downloading and installing the server version of Ubuntu.

Go to one of the Ubuntu [download sites](http://www.ubuntu.com/download). Download and burn a "Server install CD".

You could also take a regular install of Ubuntu and remove anything to do with Gnome/X, but that's a lot of trouble if it's a fresh install.

If you want to leave Gnome on it, then install sysv-rc-conf, run it with sudo, and uncheck every box on the gdm line.

---

### Post by kimvall on 2006-10-01
Thanks for the quick reply. I think I'll go with the server installation.

One thing though; won't the server installation install a whole heap of stuff per default that'll eat more system resources than I saved in the first place?

---

### Post by skymt on 2006-10-01
No, the server install is much lighter than the default Gnome desktop.

---

### Post by steve.horsley on 2006-10-01
You can prevent the GUi from starting with this command:
**sudo mv /etc/rc2.d/S13gdm /etc/rc2.d/s13gdm**
This changed the first character of the file name from S to s, thus preventing it from being started at boot. 

Alternatively, install the package bum (boot up manager) and use that to disable the gdm service.

---

### Post by kimvall on 2006-10-01
Thank you both for the help. I used the server installation of Ubuntu and it works perfectly.

Now I just gotta figure out how to control the cd autorun function via the command line.

---

