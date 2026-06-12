---
title: "Setting root password"
date: 2005-05-13
forum: Absolute Beginner Talk
---

### Post by brice on 2005-05-13
Being new to Ubuntu I find that the account management in the install process is not quite so intuitive. The first couple of times I installed the distro I noticed it never asked to establish a root password--it only asked to add a user other than root. On the third install I added root as a user and supplied a password. Then I added an additional user and proceeded with the install. 

Success! Upon login I could now su as root where before I could not. However, somehow it broke the update-manager....which I could run previously as a normal user (this was strange also as normally that is only a function allowed by root).

Finally my question: Am I missing something that is distro specific here? Normally I deal with Red Hat and it's install process always specifically asks for the root account password. And why would the update manager now be broken?

Any insight would be greatly appreciated.

---

### Post by ubuntu_demon on 2005-05-13
[QUOTE=brice]Being new to Ubuntu I find that the account management in the install process is not quite so intuitive. The first couple of times I installed the distro I noticed it never asked to establish a root password--it only asked to add a user other than root. On the third install I added root as a user and supplied a password. Then I added an additional user and proceeded with the install. 

Success! Upon login I could now su as root where before I could not. However, somehow it broke the update-manager....which I could run previously as a normal user (this was strange also as normally that is only a function allowed by root).

Finally my question: Am I missing something that is distro specific here? Normally I deal with Red Hat and it's install process always specifically asks for the root account password. And why would the update manager now be broken?

Any insight would be greatly appreciated.[/QUOTE]
 the root account is disabled by default. If you want to do something with root permission on the console you have to type sudo before the command.

"sudo" means superuser do. "sudo" will prompt for "Password:". Please specify user password

Your way of enabling the root account is wrong. The correct way to enable the root account (which is not advised to do) is : 

sudo passwd root

In order to try to repair the mess you created I suggest this :

first create a new user named username with :

sudo adduser accountname

Then do this :
sudo pico /etc/sudoers
or
sudo gedit /etc/sudoers


the file probably will be empty.  add this line :
```

username     ALL=(ALL)       ALL

```

After this remove the root account do this :
sudo passwd -l root

A good website to begin learning about Ubuntu is [www.ubuntuguide.org](www.ubuntuguide.org)

---

### Post by bored2k on 2005-05-13
[QUOTE=demon666_nl]the root account is disabled by default. If you want to do something with root permission on the console you have to type sudo before the command.

"sudo" means superuser do. "sudo" will prompt for "Password:". Please specify user password

Your way of enabling the root account is wrong. The correct way to enable the root account (which is not advised to do) is : 

sudo passwd root

In order to try to repair the mess you created I suggest this :

first create a new user named username with :

sudo adduser accountname

Then do this :
sudo pico /etc/sudoers
or
sudo gedit /etc/sudoers


the file probably will be empty.  add this line :
```

username     ALL=(ALL)       ALL

```

After this remove the root account do this :
sudo passwd -l root

A good website to begin learning about Ubuntu is [www.ubuntuguide.org](www.ubuntuguide.org)[/QUOTE]
 [http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)

demon just so you know, to avoid conflicts, sudoers MUST be edited through  the visudo command. If you still want to use gedit, do 
```
export EDITOR=gedit && sudo visudo
```.

---

### Post by ubuntu_demon on 2005-05-13
[QUOTE=bored2k][http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)

demon just so you know, to avoid conflicts, sudoers MUST be edited through  the visudo command. If you still want to use gedit, do 
```
export EDITOR=gedit && sudo visudo
```.[/QUOTE]

thnx I didn't know. I have never had any problems btw.

---

### Post by bored2k on 2005-05-13
[QUOTE=demon666_nl]thnx I didn't know. I have never had any problems btw.[/QUOTE]
 > DESCRIPTION
 visudo edits the sudoers file in a **safe fashion**, analogous to vipw(8).  visudo locks the sudoers file against
 multiple simultaneous edits, provides basic sanity checks, and checks for parse errors.  If the sudoers file is currently being edited you will receive a message to try again later.

No probs.

---

### Post by brice on 2005-05-13
[QUOTE=bored2k][http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)

demon just so you know, to avoid conflicts, sudoers MUST be edited through  the visudo command. If you still want to use gedit, do 
```
export EDITOR=gedit && sudo visudo
```.[/QUOTE]
 Thanks everyone for the input. I wasn't aware that Ubuntu utilized sudo for root tasks. Red Hat, Mandrake, Sun JDS, etc all allow you to su as root and login as root at the login screen.

I figured it was just something stupid that I was doing as a result of not being familiar with this distribution. Again, thanks for the speedy and informative replies.

---

### Post by bored2k on 2005-05-13
[QUOTE=brice]Thanks everyone for the input. I wasn't aware that Ubuntu utilized sudo for root tasks. Red Hat, Mandrake, Sun JDS, etc all allow you to su as root and login as root at the login screen.

I figured it was just something stupid that I was doing as a result of not being familiar with this distribution. Again, thanks for the speedy and informative replies.[/QUOTE]
 Sudo is supposedly safer than su, but we'll let you be the judge of that. Even if you make a root password, the menu will continue using sudo unless told otherwise.

---

