---
title: "How to setup root password?"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by georgman on 2006-03-12
I am quite new to the linux and ubuntu too. Just installed ubuntu on my laptop.
During installation it didnt ask for setting up root user or I didn't notice with the excitement of entering into a new world !!!

my primary login has got administrative privilages on my machine however this password doesn't authroize for the root.

How can I get my root password reset? Do I need to install it all again and carefully look for some option? pls advise..

---

### Post by bjweeks on 2006-03-12
to run a command as root put ```
sudo
``` in front of the command. eg ```
sudo apt-get update
```

---

### Post by kaamos on 2006-03-12
And if you want a root shell, just type
```
sudo su
```
and enter your user password. Note that only users in the "admin" group can use sudo.

---

### Post by AtinLango on 2006-03-12
The password you entered for your user account you setup during installation allows you access to root privileges. If you want to do what root does, precede every command with sudo e.g.

```
sudo rm -rf myfi*
```

Alternatively, once in a terminal (shell), you may type

```
sudo bash
```

so that you just issue commands without preceeding with sudo. This root privelege ceases when you close the terminal.

In either case, you will be prompted for your password referred to above.

---

### Post by Klaidas on 2006-03-12
Check my 4th link in the signature :)

---

### Post by Klejs on 2006-03-12
```
sudo passwd root
```

then it'll first ask for your password then the new root pass 2 times.

Have fun

---

### Post by georgman on 2006-03-12
Thanks all. could get it working ..

---

### Post by mlind on 2006-03-12
you should preferably avoid using root account, instead use sudo -command for
actions you need to do as root user. You should probably check out [RootSudo]("https://wiki.ubuntu.com/RootSudo")
documentation on the wiki like Klaidas said.

for temporary root terminal *sudo -i* or *sudo su*

---

### Post by Mr. Chaos on 2008-04-30
This is the error i get after my install of the server is

"john is not in the sudoers file.  This incident will be reported.
john@ubuntu-server:~$ sendmail: fatal: open /etc/postfix/main.cf: No such file or directory"

How do i fix it? So i can work on my server as root?

---

