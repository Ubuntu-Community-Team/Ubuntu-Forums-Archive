---
title: "Logging in as root"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by peterhf on 2007-03-26
Ubuntu Desktop 6.10

The machine is started as the non-root user. I open the terminal window. At the prompt I enter "login root". The following message appears: "No utmp entry. You must exec "login" from the lowest level "sh".

I am unfamiliar with this procedure as  I am able to execute this procedure in Mac OS X.

Peter -

---

### Post by fakie_flip on 2007-03-26
The root account in Ubuntu is disabled by default for security reasons. To enable it, you must give the root account a password with this command.

sudo passwd root

Otherwise you can get a root shell by doing one of these.

sudo -i
sudo su -

You don't need to do any of these commands. Most people just type sudo before a command to have it executed with root priveledges.

"login root" is not the command to login as the root user in Linux. If you have enabled the root account using the first command I gave you, then you can login as root by doing this.

su -

---

### Post by aysiu on 2007-03-26
As fakie_flip notes, there's absolutely no need to use or enable the root account in Ubuntu.

More info in these two links:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by peterhf on 2007-03-26
Thanks for the info, guys. Not only did you answer my question but have pointed me to resources that I haden't yet discovered but sorely need!

Peter -

---

