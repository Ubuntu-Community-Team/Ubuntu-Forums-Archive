---
title: "HOWTO: Uninstall in Dapper"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by maxM on 2006-05-06
Hi, I'm verry new to Ubuntu, and I wonder what command to use when I wish to uninstall programs? Like Opera, what command do I use to uninstall it?

---

### Post by eirc on 2006-05-06
the easiest way is to run the synaptic package manager in "System -> Administration -> Synaptic Package Manager" and search for what you want to install-uninstall

---

### Post by Sef on 2006-05-06
> the easiest way is to run the synaptic package manager in "System -> Administration -> Synaptic Package Manager" and search for what you want to install-uninstall

That works only for packages in the repositories.

---

### Post by ncappel1 on 2006-05-06
the command line way
```
sudo apt-get remove [name of program/package]
```

further question: will the above command work for locally installed programs or is it only for ones installed through synaptic?

---

### Post by mostwanted on 2006-05-06
It will work for all commands installed in APT. This means apps installed from debs, rpms (if alien was used) and source (if checkinstall was used), as well as from the repos.

But use Synaptic instead for installation and removal, it's gives a much better overlook when installing and removing packages.

---

### Post by tuxcantfly on 2006-05-06
sudo dpkg -r programname

will also work

---

### Post by Rinzwind on 2006-05-06
A lot of programs installed by hand (so not apt-get) also come with an 'uninstall'.
Check the directory where the program is for it.

---

### Post by barbarian on 2006-05-06
*sudo aptitude remove name_of_the_program*

---

### Post by ncappel1 on 2006-05-06
[QUOTE=Rinzwind]A lot of programs installed by hand (so not apt-get) also come with an 'uninstall'.
Check the directory where the program is for it.[/QUOTE]

just for reference, what is the directory that files are installed to? When the install script does its thing, doesn't it put files all over the system? I've read some articles about the organization of the linux file system, but I can't seem to understand where the "main" directory they are installed to is. meaning, pardon the windows reference ;), similar to the c:/program files/[program name]?

---

### Post by maxM on 2006-05-07
> **ncappel1]just for reference, what is the directory that files are installed to? When the install script does its thing, doesn't it put files all over the system? I've read some articles about the organization of the linux file system, but I can't seem to understand where the "main" directory they are installed to is. meaning, pardon the windows reference  said:**
> ?

This would help me to. I tried to install Opera, but I did it the wrong way. When I tried to do it the right way I got the message (something like): The package already excist, it's installed.
So I'm still stuck since none of the commands so far have done the job. 
PS: The commands was at help at every other program I wanted to uninstall :)

---

