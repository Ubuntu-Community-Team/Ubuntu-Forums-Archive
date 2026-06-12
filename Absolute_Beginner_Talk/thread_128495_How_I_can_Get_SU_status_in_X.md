---
title: "How I can Get SU status in X"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by wint on 2006-02-11
When i try to login in X as root I see message that this is imposible.
So i log in as user with my nick. Then I try to run Add Aplication meneger(or anower system utilit) I must input root password to run it, but then I type them (110% correctly) i'll see message: "Wrong paasword"...
P.S. in console I can login as SU... Thy I can' do it in X.(I use KDE, but in Gnome  i have same problem)

p.p.s Sorry for my English:rolleyes:

---

### Post by whiter on 2006-02-11
you can't as far as i know... however, to issue root commands you can just use "sudo" like "sudo gedit /etc/fstab" or something like that, works just like su.

---

### Post by wint on 2006-02-11
I only want run Aplication that demands privilieges of root in  GRAFFIC mode (in X). 
Can i do it in Ubuntu? I think it's simply...

---

### Post by patrick295767 on 2006-02-12
After installing, you may type:

```
sudo su
```
  
enter ur password
  
then ```
passwd 
```
to define ur new password for root
  
 =====
If you wanna get ur password via /etc/shadow...
[http://ubuntuforums.org/showthread.php?t=64557&page=6](http://ubuntuforums.org/showthread.php?t=64557&page=6)


====

Welcome to a very powerful & great os : linux 

Greetings

Patrick

---

### Post by mcduck on 2006-02-12
I'd rather use 'gksudo nautilus' to get root acces to my machine. And if some application needs to be run as root you can modify it's launcher to use gksudo too, so it asks for your password when you try to run it.

Logging in to X as root is not a good idea, and usually there is no need for doing that. Honestly, I don't ever even need root, I find using sudo much faster and easier ;)

Here's a nice link about Ubuntu&root/sudo: [https://wiki.ubuntu.com/RootSudo?highlight=%28rootsudo%29]("https://wiki.ubuntu.com/RootSudo?highlight=%28rootsudo%29")

---

### Post by newuser111 on 2006-02-12
sudo -i or sudo -s -H will give you a working root shell environment

typing xhost + before entering the root shell will let you run X apps from root,

---

### Post by codejunkie on 2006-02-12
you have several different options to run gui apps as root in ubuntu
i'll use "synaptic" the packagemanager for an example:

if you use gnome you use the following commands

alt+F2 and enter
```
gksudo synaptic
```
this command will also work when run through a terminal

open a terminal and use
```
sudo synaptic
```
if you use the "sudo" command in front of an app it must be run in a terminal in order for you to enter your password.

if you use kde you use the following commands

alt+F2 and enter
```
kdesu synaptic
```
you can still use
```
sudo synaptic
``` through the terminal in kde also.

NOTE: i've noticed in kde if you use commands with the prefix **kdesu** might not work sometimes loging out and logging back in might fix the issue, also trying the ```
sudo -K
``` command to kill any process hanging up kdesu.
if your using kde your best bet at running apps as root is through the terminal with the "sudo" option.

if you wan't full root access to your system via gui press ctrl+alt+F1 
login with your username and password and switch to root with
```
sudo su
``` enter ```
/etc/init.d/gdm stop
```if you use gnome
if you using kde enter ```
/etc/init.d/kdm stop
```
after the display manager stops type ```
startx
``` and you'll be logged in as root to restart the display manager when your done and you wan't to log back in to your normal user account logout then type ```
/etc/init.d/gdm restart
```if you use gnome 
```
/etc/init.d/kdm restart
```if you use kde.

---

### Post by USA1 on 2006-02-14
[QUOTE=patrick295767]After installing, you may type:

```
sudo su
```
  
enter ur password
  
then ```
passwd 
```
to define ur new password for root
  
 =====
If you wanna get ur password via /etc/shadow...
[http://ubuntuforums.org/showthread.php?t=64557&page=6](http://ubuntuforums.org/showthread.php?t=64557&page=6)


====

Welcome to a very powerful & great os : linux 

Greetings

Patrick[/QUOTE]
Excellent reply.  It helped me too, thank you very much.

---

