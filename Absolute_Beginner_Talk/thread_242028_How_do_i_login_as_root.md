---
title: "How do i login as root"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by ic3man on 2006-08-23
hi i have an nvidia installer for drivers that is telling me to login as root. How can i do this?
I tried but with no success

---

### Post by drtvasudevan on 2006-08-23
in terminal one uses the commands preceded by sudo to do most of the root access work.

---

### Post by ic3man on 2006-08-23
so that is the only way to run the installer?
No GUI?

---

### Post by Druidor on 2006-08-23
if you want to use a gui the command is 

```

gksudo nautilus

```

This will open up the explorer style folder browser which you can navigate through using hte mouse & drag/drop files into relevent places & edit text files.

It is best to install via the command line though

Also Automatix does Nvidia driver installs if you are feeling lazy lol

see the forum thread on it

[http://www.ubuntuforums.org/showthread.php?t=80295](http://www.ubuntuforums.org/showthread.php?t=80295)

 To install automatix do the following (3 steps):
Open up terminal and paste the following 3 commands one after the other:
```


wget http://www.getautomatix.com/files/automatix-installer

```
```


chmod 755 ~/automatix-installer

```
```


./automatix-installer

```

When the installer finishes successfully (without any errors) and you get back to command prompt, run Automatix from Applications --> System Tools in Ubuntu, Main Menu --> System in Kubuntu/Xubuntu Dapper

The above installer checks the version of Ubuntu installed on your computer and your desktop environment (Gnome/KDE/XFCE) and adds the suitable repository to your sources.list, updates it and installs automatix.

After you have used this installer once, you do not need to use it again because automatix will get updated automatically (through update manager) every time a new version is released.

---

### Post by derred on 2006-08-23
There's no X based gui available for the drivers as far a I know but as long as you read the text on the screen;) you should be ok

If you don't want to put sudo in front of every command you can try "$sudo su" it will ask for your password and then switch users so that you become root.(this is to be done in a x terminal emulator or tty1..6)

---

### Post by ic3man on 2006-08-23
Thnx...
also from the controll panel i changed the root password while trying to login...
I made a mistake?

---

### Post by drtvasudevan on 2006-08-24
as long as you remember it,  it is not.;-)

---

### Post by hraposo on 2006-08-24
to login as root:
sudo passwrd root
enter the neew root password
then type: su
root password and you are login as root

---

### Post by hraposo on 2006-08-24
Sorry, the line command is
sudo passwd root

---

### Post by soutSA on 2006-08-24
That will only change the password for root.

To logon as root you only have to type the following:

# su

after that it will ask you for a password. Type in the password you just added to your root account.

bam....you will see the following:

root@******#

This means you are now logged on as root.

---

### Post by macogw on 2006-08-24
> **soutSA said:**
> That will only change the password for root.

To logon as root you only have to type the following:

# su

after that it will ask you for a password. Type in the password you just added to your root account.

bam....you will see the following:

root@******#

This means you are now logged on as root.

i thought it was sudo -s to stay logged in and that su was for all non-debian-based distros

---

### Post by FuriousLettuce on 2006-08-24
You can use either, although sudo -s is the easier method. Setting up a root user account and using it is a habit generally carried over from other distro's (or just looking around on the 'net). Whilst it is possible to su, or just simply login as root, I would say that generally sudo -s is the preferred method.

---

