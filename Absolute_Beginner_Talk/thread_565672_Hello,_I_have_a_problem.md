---
title: "Hello, I have a problem"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by Desert Storm on 2007-10-02
Well, I've always used WIndows, well, few times, Ubuntu too, Xubuntu
But, Now, as i installed, the Ubuntu, on my main computer, I wanted to install Beryl
(No, this topic isnt about Beryl)
I made this account as a administrator, but, when i try to edit something, in usr/bin, or something
(With other folders too), it gives me "Access denied"

---

### Post by eljalill on 2007-10-02
Even if your user is in the administrator group, you need to edit these system files as root.
So you need to type sudo nano /usr/bin/whatever or change who you are with sudo su in the terminal. (sudo means "superuser do") Then every commnad will be given as root. 

But be careful. You will not be asked for caution, if you do something as it is in windows. You can without big problems ruin your system as root!

---

### Post by benerivo on 2007-10-02
Even the administrator needs to supply a password for 'system changes'. What do you want to do in /usr/bin. To gain full access, type ```
sudo nautilus
```but remember that any changes you make from this new window may be dangerous.

---

### Post by Desert Storm on 2007-10-02
How could i login as root? I mean, as a normal user
I tryed at the login page, it told me, i cant login, from that page
And, thank you =D

---

### Post by benerivo on 2007-10-02
You can't (i don't think you can but there may be some clever workaround), but you can do anything you want in your own account, by knowing the password and using sudo in the terminal.

---

### Post by Desert Storm on 2007-10-02
Okay, thank you for your help :D

---

### Post by Incense on 2007-10-02
With great power comes great responsibility....near the bottom of the page is a section on how to enable the root account.

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Desert Storm on 2007-10-02
> **Incense said:**
> With great power comes great responsibility....near the bottom of the page is a section on how to enable the root account.

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

Yeah, so i will hold back, from endableing it, i dont want to mess up :D

---

### Post by steve.horsley on 2007-10-02
Very wise.

But whenever you want to launch a graphical application with root privilege, you should use:
**gksudo nautilus**
instead of:
**sudo nautilus**
I think nautilus is OK, but siome graphical apps can leave files in your home folder that prevent you from logging in again if you launch them with sudo rather than gksudo. It's complicated why (meaning I don't understand myself).

---

