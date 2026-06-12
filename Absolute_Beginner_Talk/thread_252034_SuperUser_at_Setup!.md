---
title: "SuperUser at Setup!"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by hollym on 2006-09-06
Hi, I am trying to install Ubuntu but there is no option for for setting up a superuser password during password. I need to edit files to configure the machine.

---

### Post by Tomosaur on 2006-09-06
You do not need to create a super-user account. The account you set up during the installation has the ability to gain super-user priveleges as and when they are needed by executing the 'sudo' command via the terminal (although some GUI system applications will ask for your password too when you need to gain higher priveleges). The password it will ask for is the same password as you use to log on.

---

### Post by pyros on 2006-09-06
The first user that you setup will be the admin/root account. to do something as the superuser, just use sudo or gksudo and use the password for your first account.

---

### Post by meng on 2006-09-06
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
for more info.

---

### Post by hollym on 2006-09-06
so at the terminal prompt i type:

sudo ?what? and then the password?

---

### Post by Tomosaur on 2006-09-06
Let's say you wanted to nano with super priveleges:
```

sudo nano ./myFile.ext

```
You will then be prompted to type your password. It won't show up on screen, but it is being typed so don't worry about that. Just be careful not to misspell it :D

---

### Post by crane on 2006-09-06
If you run a command the requires root access it will promt you for your password. 
Like the example in previous post. Or just start synaptic or any administrative tasks.
 When prompted for a the password use your password. (assuming you are running as the user you created during set up)

---

### Post by pyros on 2006-09-06
But, if you get a message about not having permission, start the program with gksudo (for graphical programs) or sudo (for command line programs) to run it as the superuser.

---

### Post by anaconda on 2006-09-06
yep, and you can also type
```
sudo su
```
in terminal, and you will have root rights until you type exit..

gksudo nautilus is also a good command to know,,

And if you come from some other linux distro, then you might want to enable root user, you can do that by:
sudo passwd
and after you give a password to root you can login as user root.. (not recommended)

---

