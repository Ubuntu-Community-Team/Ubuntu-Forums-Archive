---
title: "Running progs from terminal"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by Shmook on 2007-05-11
I'm having some trouble finding what to type in the terminal to utilize gksudo, which many programs seem to require to fully operate. 

How do I find what to type to load??

---

### Post by aysiu on 2007-05-11
Just *gksudo* and the application name.

For example, if it's Firestarter, the command would be ```
gksudo firestarter
``` Are you running into applications that haven't automatically created menu entries?

---

### Post by Bachstelze on 2007-05-11
It depends on what program you are trying to launch. If you know the name of the package you used to install your app, you can find all the executables that package installs with

```
dpkg -L PACKAGE_NAME | grep /usr/bin
```

For example, if I don't remember the command to run apt, I do

```
$ dpkg -L apt | grep bin
/usr/bin
/usr/bin/apt-cache
/usr/bin/apt-cdrom
/usr/bin/apt-config
/usr/bin/apt-get
/usr/bin/apt-key

```

That lists all the "commands" provided by that package.

---

### Post by pizzutz on 2007-05-11
Just prefix the command for any graphical program you want to run as root with gksu or gksudo, it will pop up a box and ask you for your password. Please remember that using gksu is not recommended unless absolutly necessary.  if you run gksu nautilus, for example, you would have a file browser that lets you access every file on your computer, and you could easily delete or otherwise mess up important system files.

---

### Post by Shmook on 2007-05-11
well for example, I installed AVG antivirus from a .deb, and was upset to see that "gksudo avg" didn't work...

thanks a bunch, all

---

### Post by aysiu on 2007-05-11
*avg* may not be the command to launch AVG Anti-virus.

---

### Post by Bachstelze on 2007-05-11
I guess I posted in the wind once again...

---

### Post by Shmook on 2007-05-12
My apologies; I tried your suggested dpkg technique, but it didn't return any results, and aysiu's comment comes down to the simplicity of my problem -- I just don't know how to find what to type to run a program from the terminal so I can use gksudo with it  -- as AVG sends a permission denied message when I try to update the definitions when launching it from the Apps menu.

---

### Post by Bachstelze on 2007-05-12
What if you told us a bit more precisely what you want to do/know ?

---

### Post by Shmook on 2007-05-12
> **HymnToLife said:**
> What if you told us a bit more precisely what you want to do/know ?

I'd like to know how to find what to type in the terminal to run programs I usually run from the apps menu, so I can preface it with gksudo so I can use all the features of the program. For example, how it was mentioned that "avg" isn't the command to run AVG antivirus from the terminal -- how do I find what is? Or is there another way to run a program as root that I don't know about?

---

### Post by drs305 on 2007-05-12
If I could tag on a related question while you help Shmook...

Is there a /switch or command you can use when you open a program in terminal to close or free the terminal window once the actual app is running?  

Thanks.

---

### Post by Bachstelze on 2007-05-12
Yep, just add an ampersand (&) at the end of the command :

```
gedit /foo/bar &
```

---

### Post by mikewhatever on 2007-05-15
> **Shmook said:**
> I'd like to know how to find what to type in the terminal to run programs I usually run from the apps menu, so I can preface it with gksudo so I can use all the features of the program. For example, how it was mentioned that "avg" isn't the command to run AVG antivirus from the terminal -- how do I find what is? Or is there another way to run a program as root that I don't know about?

It works if you type > sudo avgupdate -o

---

