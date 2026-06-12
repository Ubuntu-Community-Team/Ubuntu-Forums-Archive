---
title: "no user account"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by Doobiedo on 2005-11-14
i just installed ubuntu and thanks to some help from people on these forums got x working after a troubled install but now i have another problem.

during installation when i entered a username and password it got stuck in a loop forcing me to enter my real name then username then password then password again then back to asking me for my real name.  

i couldn't find a way for it to accept my user account so i skiped this step.  i am now staring at the login screen as i have no regular account, can't login as root and don't know how to get back to the command prompt to add a new user (or the syntax for adding a new user).

can sombody please help me?

---

### Post by invalid on 2005-11-14
It sounds like there may have been an illegal character somewhere in either a name or password. How did you work on your X problems if you were not logged in as a user?

Cb

---

### Post by Doobiedo on 2005-11-14
when x failed to load it dumped me at a command prompt so i logged in as root.

there was no illegal character either as i went through the loop 20+ times trying different name/password combinations

---

### Post by earobinson on 2005-11-14
This link might help you, to find this i searched for: passwrd revovery

[http://www.ubuntuforums.org/showthread.php?t=86277&highlight=password+recovery](http://www.ubuntuforums.org/showthread.php?t=86277&highlight=password+recovery)

---

### Post by codejunkie on 2005-11-14
[quote=Doobiedo]i just installed ubuntu and thanks to some help from people on these forums got x working after a troubled install but now i have another problem.

during installation when i entered a username and password it got stuck in a loop forcing me to enter my real name then username then password then password again then back to asking me for my real name.  

i couldn't find a way for it to accept my user account so i skiped this step.  i am now staring at the login screen as i have no regular account, can't login as root and don't know how to get back to the command prompt to add a new user (or the syntax for adding a new user).

can sombody please help me?[/quote] you have to be root to add a new user, by default the root user is disabled in ubuntu for security so what you have do is first enable the root account to do that reboot your computer and at the grub menu you'll see some choices for example if you dual boot ubuntu & windows you'll see something like this
```

Ubuntu, kernel 2.6.12-9-k7
Ubuntu, kernel 2.6.12-9-k7 (recovery mode)
Ubuntu, memtest86+
Microsoft windows

``` choose the recovery mode this will enable root acess temporarly when you reach the command line as root you run this command 
```
passwd root
``` this will let you set the password and enable the root account now you can add a new user with this command ```
adduser
```and fill in the user information, when your done reboot like you normaly do and login with your new user if you have any more questions let me know and i'll be happy to help you.

---

### Post by Doobiedo on 2005-11-14
Thanks.

i ran adduser and got

"adding user 'username' . . . 
adding a new group 'username' (1000).
Adding new user 'username' (1000) with group 'username'.
Creating home directory '/home/username'.
chown 1000:1000 /home/username: Operation not permitted
Cleaning up.
Removing directory '/home/username'
Removing user 'username'.
Removing group 'username'.
groupdel: group username does not exist

?

---

### Post by codejunkie on 2005-11-14
[quote=Doobiedo]Thanks.

ive rebooted into recovery mode and logged in as root again but the passwd command only allows you to change the password of an existing user account.  as there are no accounts set up i cant change a password so still can't login.

anyone know how to create a new account?[/quote]no the ```
passwd root
``` command enables the root account, you'll need that enabled later most likely, if your user account settings are as messed up as the seem to be. because you'll have to add your user account that you create with the ```
adduser
``` command to the sudoers file to use administration applications like synaptic, networking etc  the adduser one will let you create the new user account.

---

### Post by Doobiedo on 2005-11-14
Ive been searching for answers and found a way to enable logging in as root using gdmsetup. but this needs x running to work so i've manually edited the config file in /etc/X11/gdm/gdm.conf

Thanks for the help people.

---

### Post by Doobiedo on 2005-11-14
more problems.

i can now log in using my root account and have tried to create a new user but when i try and log in using this i get the message 

"Your $HOME/.dmrc file has incorrect permissions and is being ignored. This prevents the default session and language from being saved. File sould [sic] be owned by user and have 644 permissions"

then it logs me out again.
with this error

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /varlog/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h " " -l ":0" "username"
/etc/gdm/Xsession: Beginning session setup . . .

(gnome - session : 9037): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: Permission denied
Could not create per-user gnome configuration directory '/home/username/.gnome2/': Permission denied

---

