---
title: "Log in as Root"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by bellaterror on 2006-06-24
how do I log in as root?:confused:

---

### Post by raptros-v76 on 2006-06-24
ok. in ubuntu, you use sudo to run programs as root. you do
sudo <program>
then enter in your password

---

### Post by Kilz on 2006-06-24
[QUOTE=bellaterror]how do I log in as root?:confused:[/QUOTE]
Ubuntu disables the root login. Commands are done with sudo and your password. If you need a gui for root type ```
gksudo nautilus
``` into the terminal. But beware, there is a good reason root is disabled , you can mess your system up very easy.

---

### Post by tonyr on 2006-06-24
NOT something you ordinarily want to do, unless you REALLY know what you are doing.
In the Ubuntu world, you can execute any command as root by putting **sudo** first.
So I would edit **/etc/fstab** a file owned by **root** with this:
```

sudo vi /etc/vi

```

since I'm a vi kind o' guy.

You can start a root shell in a terminal with **sudo su**.   If you REALLY REALLY
REALLY want **login** as root from the login window,  in a terminal do
```

sudo passwd root

```
and supply a root password.  And just in case I was not clear berfore, THIS IS NOT
A RECCOMMENDED PRACTICE, what with security issues and dangers and all those other risks
that you already know about.

---

### Post by bellaterror on 2006-06-24
kay I knew those two before, so there is no way to login (username) as root???

---

### Post by raptros-v76 on 2006-06-24
oh. do sudo -s

---

### Post by tonyr on 2006-06-24
Yeah, **sudo passwd root**.  And to reverse it, **sudo passwd -d root**.
Note that when you do this, it will ask you for YOUR password first, before it will
ask you to provide a **root** password.

---

### Post by bellaterror on 2006-06-24
Thanks a whole lot one more question for you is there a way to do it when it starts up and you enter username and the PW?

---

### Post by raptros-v76 on 2006-06-24
... thats not advised. there;s a reason why the root account is disabled, but its complicated

---

### Post by bellaterror on 2006-06-24
okay then nvm thanks Alot again

---

### Post by anaconda on 2006-06-24
I think, (not sure) that if you create a password for root (like tonyr suggested), then you can also login as root..

Recovery mode is also with root rights...

---

### Post by raptros-v76 on 2006-06-24
also, in order to log in graphically, you need to enable it for gdm, theres a configuring frontend in gnome somewhere

---

### Post by tonyr on 2006-06-24
[QUOTE=anaconda]I think, (not sure) that if you create a password for root (like tonyr suggested), then you can also login as root..

Recovery mode is also with root rights...[/QUOTE]

Do the **sudo passwd root** thing. Then go to **System->Administration->Login Window**
and under the **Security** tab check **Allow local system administrator login**.  At the next
**GDM** login window, you should be able to log in as root with the password you provided
in **sudo passwd root**.

---

