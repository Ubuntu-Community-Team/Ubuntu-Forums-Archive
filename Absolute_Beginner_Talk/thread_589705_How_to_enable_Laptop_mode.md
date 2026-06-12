---
title: "How to enable Laptop mode?"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Caezar on 2007-10-24
I am new to Linux and just installed Ubuntu 7.10 on my Thinkpad X60. The laptop is running hot, so I did some research and it seems I need to tweak the settings and notably enable the laptop mode.

I tried to go to /etc/default/acpi-support and set ENABLE_LAPTOP_MODE from false to true.

Unfortunately, I cannot seem to save the document even though I am logged into my main user, which has all privileges.

What to do? :confused:

---

### Post by aphirst on 2007-10-24
In linux, your 'main user' is not the one you set up in the installation process; it is a hidden user called 'root'. you cannot normally log in as root in linux from the login window. (think of root as the windows administrator account).

In order to invoke administrator privileges, one must use the terminal, and precede the command with sudo or gksudo. like this :

```
$ sudo gedit /etc/default/acpi-support
```

Once you type your root passwor (login password in the case of the 'main user' as you have prevuiously understood the term), you can save the file.

The whole root concept is essentially prevent major (potentially harmful) cahnges being done accidentally or withour users permission.

Hope that helps.
~ aphirst ~

---

### Post by Caezar on 2007-10-24
Thank you aphirst. But what is the default password for root? I installed Gutsy 1 hour ago and i swear I have not been asked to choose a password for the root login.

---

### Post by ThrobbingBrain66 on 2007-10-24
The password it's asking for is *your* password.  Root isn't actually enabled by default so doesn't have a password.

---

### Post by aphirst on 2007-10-24
If there is only one normal user account on your linux box, then the sudo password is the same as your login password. I thought I said that... :S . Never mind.

---

### Post by Dr Small on 2007-10-24
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Caezar on 2007-10-24
I know now. When I typed sudo gedit /etc/default/acpi-support in the Terminal, it prompts me for my user password. After I type the password, the file is opened. I can edit it and save the document.

This means that my user login does have full admin privileges, I guess. Indeed when I go to the user accounts management menu, the root login does not have any right, whereas my login has all rights, but one or two categories.

Thanks for your help!

---

### Post by ThrobbingBrain66 on 2007-10-24
That's not entirely true.  If your user had full privileges, you'd be able to edit and save system files without using sudo or gksudo.  Using sudo and gksudo allow you *temporarily* become root to edit files.

---

