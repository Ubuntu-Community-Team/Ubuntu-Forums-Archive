---
title: "Users, Passwords"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by Nrbelex on 2006-04-19
When I first set up the OS, I used a name and password which I assume became the "root". I later read that its stupid to constantly use this user for basic everyday tasks so I created another. Using this new user-name, I'm restricted in what I can do in terms of installing programs, etc. (which I guess is the point so as to prevent access to potentially dangerous areas of the OS accidentally). However, if I want to run an update or use Synaptic package manager as the restricted user, is there any way I can without logging out and then back in as the root user? Also, can I easily transfer things like menu settings and Firefox bookmarks between the two? Thanks!

~ Brett

---

### Post by mostwanted on 2006-04-19
Ubuntu has never made a root user, it doesn't use root users. Just use your old user account or add your new user to the admin group.

The fact that you to type in passwords all the time is a safety measure (you temporarily allow root access). It's not something that's on all the time, otherwise it woule be pointless to type in those passwords.

Good link:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by krusbjorn on 2006-04-19
The user and password you set during the installation process was just a regular user. By default, there is no root user in Ubuntu - when you need to do something that requires root access you do it with "sudo" (like "sudo apt-get install firefox"). When using sudo, the password required is the user's password, not the root's.

---

### Post by Nrbelex on 2006-04-19
So both users have identical privelages? Why can I not install programs with the newly created user then? Does (from the site you gave me) "the installer will setup sudo to allow the user that is created during install to run all administrative commands" mean that only that first user has privelages to administrative tasks like installing programs? If so is there any reason for the newly created user to exist? Thanks again!

~ Brett

---

### Post by krusbjorn on 2006-04-19
[QUOTE=Nrbelex]So both users have identical privelages? Why can I not install programs with the newly created user then? Does (from the site you gave me) "the installer will setup sudo to allow the user that is created during install to run all administrative commands" mean that only that first user has privelages to administrative tasks like installing programs? If so is there any reason for the newly created user to exist? Thanks again!

~ Brett[/QUOTE]

Yeah, the user you created afterwards doesnt have sudo rights. You can add your new user in the /etc/sudoers file using the command "sudo visudo" or make the user a member of the admin group (in System->Administration->Users and Groups) to grant those rights. But I dont see any reason to keep your new user. You could just delete it (after backing up any files in its home directory you want to keep) and go back to your good old user ;)

---

### Post by mostwanted on 2006-04-19
[QUOTE=Nrbelex]So both users have identical privelages? Why can I not install programs with the newly created user then? Does (from the site you gave me) "the installer will setup sudo to allow the user that is created during install to run all administrative commands" mean that only that first user has privelages to administrative tasks like installing programs? If so is there any reason for the newly created user to exist? Thanks again!

~ Brett[/QUOTE]

As I said in my previous post: add the new user to the admin group. You can do that the way krusbjørn describes.

---

### Post by Nrbelex on 2006-04-19
I got rid of the new user - I had read an article on Linux in general which had recommended the practice of creating the second user for securty without realizing that Ubunti takes care of it. Thanks!

---

### Post by mostwanted on 2006-04-19
[QUOTE=Nrbelex]I got rid of the new user - I had read an article on Linux in general which had recommended the practice of creating the second user for securty without realizing that Ubunti takes care of it. Thanks![/QUOTE]

Yeah. Ubuntu is a special distro in that sense. It's the same approach as Mac OS X; no root there either, you use sudo when you need root privileges.

---

### Post by Coruba67 on 2006-04-20
anyone know what the command in terminal is for deleting a user?

---

### Post by codejunkie on 2006-04-20
[QUOTE=Coruba67]anyone know what the command in terminal is for deleting a user?[/QUOTE]
```
deluser
```should do it.

---

### Post by angkor on 2006-04-20
From man deluser:

deluser, delgroup - remove a user or group from the system

Edit: Ha, Codejunkie beat me to it...that's probably why they call you codejunkie.:) ;)

---

### Post by Coruba67 on 2006-04-20
hummmmm....  I type in deluser and it says that the command is not found.  Mind you it is a Fedora box..  wouldn't have thought it would have been different though.

---

### Post by codejunkie on 2006-04-20
[QUOTE=Coruba67]hummmmm....  I type in deluser and it says that the command is not found.  Mind you it is a Fedora box..  wouldn't have thought it would have been different though.[/QUOTE]
if your using fedora you need to run ```
su -
```then run the```
deluser
```command.

---

### Post by Coruba67 on 2006-04-20
I am already logged in as root though...  It just says the command is not found...  :(

---

### Post by codejunkie on 2006-04-20
[QUOTE=Coruba67]I am already logged in as root though...  It just says the command is not found...  :([/QUOTE]
if i login as root with```
su
```on my fedora install, the command is not listed either, i have to run ```
su -
```to gain root access then run ```
deluser
```

---

