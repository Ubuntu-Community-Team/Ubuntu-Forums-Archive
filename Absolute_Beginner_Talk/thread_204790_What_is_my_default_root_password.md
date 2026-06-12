---
title: "What is my default root password"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by SmackyFan on 2006-06-27
Hello i cant understand how i can get my root pswd i need it to configure my internet connection but ... Pls tell me a way to change it or a way to see it .... :(

---

### Post by T700 on 2006-06-27
It is the password for your user account that you created when you first installed Ubuntu.  That is the password you use when you log on after a reboot.  By default, there is not a root account as such in Ubuntu (although one can be created).  

When using a command in a terminal that requires root, you preface it with sudo or gksudo (for graphical applications).  After you press enter, you will be prompted for the password.

Paul

---

### Post by aysiu on 2006-06-27
There is no root password:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Maggot on 2006-06-27
If you want to make it so as to use root, just type:

sudo su (then enter your user password)

then:

passwd (enter new root password twice)

---

### Post by SmackyFan on 2006-06-27
Well i think you didnt understand me i just installed the kubuntu and i got my login and pasword but they are not the same as that one that are required to nano the fstab for example i need root permition to do that but i dont know my pasword it is not the same as my login ones for sure ;(

---

### Post by Brunellus on 2006-06-27
[QUOTE=SmackyFan]Well i think you didnt understand me i just installed the kubuntu and i got my login and pasword but they are not the same as that one that are required to nano the fstab for example i need root permition to do that but i dont know my pasword it is not the same as my login ones for sure ;([/QUOTE]
Ubuntu does not enable the 'root' account by default, opting instead to add the first 'regular' user to the 'sudoers' list.

What this means is that whenever you need to execute a command with root permissions, you must preface it with "sudo".  For example, bringing a network interface up:

$ sudo ifup eth0

The shell will prompt you for a password.  type your USER password and hit enter.  The program will execute with root permissions.  

advantages to such a system can be found by reading

[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

### Post by aysiu on 2006-06-27
Let me make sure I understand you.

You did a normal installation (not an expert one).

You're currently logged in as the first user you created during installation.

As this first user, when you type ```
sudo nano /etc/fstab
``` you're asked for a password. You enter your user password, and the password gets rejected and you see this message? ```
Sorry, wrong password
``` Is that what you're saying?

---

### Post by Kilz on 2006-06-27
[QUOTE=SmackyFan]Well i think you didnt understand me i just installed the kubuntu and i got my login and pasword but they are not the same as that one that are required to nano the fstab for example i need root permition to do that but i dont know my pasword it is not the same as my login ones for sure ;([/QUOTE]
If you want a gui to move around in as root, try ```
ksudo konqueror
``` Im not sure there is a qtsudo like gksudo in gnome.

EDIT: Corrected command

---

### Post by bruce89 on 2006-06-27
[QUOTE=Kilz]If you want a gui to move around in as root, try ```
sudo konqueror
``` Im not sure there is a qtsudo like gksudo in gnome.[/QUOTE]
It is called *kdesu* AFAIK.  Using sudo messes everything up in this situation.

---

### Post by aysiu on 2006-06-27
Yes, please read this:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Kilz on 2006-06-27
[QUOTE=bruce89]It is called *kdesu* AFAIK.  Using sudo messes everything up in this situation.[/QUOTE]
Thanks for the info, ill edit the command above. Ill keep it in mind when giving advice. I dont use kde myself, tho I do use a few kde programs in gnome.

---

### Post by bruce89 on 2006-06-27
[QUOTE=Kilz]I dont use kde myself...[/QUOTE]
Neither do I!  I just know the command.

---

