---
title: "Problems executing newly installed packages."
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by ryan^2 on 2006-11-26
I've installed a couple of packages that will only run if I execute them as root from the command line.  How do I edit the permissions on these apps so that users, system wide, can use them?  

The specific apps are k3b and kpilot.  I'm running a Dapper Drake installation.

Thanks in advance.

-Ryan

---

### Post by taurus on 2006-11-26
You can run k3b as a regular user because I use it all the time when I need to burn something!  What happens when you run it from a terminal, Applications -> Accessories -> Terminal?

```
k3b
```

---

### Post by ryan^2 on 2006-11-26
This:

trying to create local folder /home/ryan/.kde/socket-Lowball1: Permission deniedtrying to create local folder /home/ryan/.kde/socket-Lowball1: Permission deniedkdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/ryan/.kde/socket-Lowball1/kdeinit__0'
ERROR: KUniqueApplication: Can't setup DCOP communication.

...and then it boots me back to command line.

---

### Post by turbojugend_gr on 2006-11-26
How did you installed those apps?

---

### Post by taurus on 2006-11-26
You don't even have permission to write to your own $HOME directory!!!  That's not normal...  What is the output of the last command from a terminal?

```
id
cd
ls -la
```

---

### Post by turbojugend_gr on 2006-11-26
> **ryan^2 said:**
> This:

trying to create local folder /home/ryan/.kde/socket-Lowball1: Permission deniedtrying to create local folder /home/ryan/.kde/socket-Lowball1: Permission deniedkdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/ryan/.kde/socket-Lowball1/kdeinit__0'
ERROR: KUniqueApplication: Can't setup DCOP communication.

...and then it boots me back to command line.

OOOoops, didn't see that. Are you the admin of your system? (other words: did you installed ubuntu on that machine?)

---

### Post by turbojugend_gr on 2006-11-26
Quote: "ls -la"

Wow, that's _sharp_! I wouldn't think of using it to check his rights. I 'ld go for the fstab and/or "id" to check the groups. Just pointing out I am very impressed.

---

### Post by ryan^2 on 2006-12-24
> **taurus said:**
> You don't even have permission to write to your own $HOME directory!!!  That's not normal...  What is the output of the last command from a terminal?

```
id
cd
ls -la
```

OK...that's it.  I ran the "ls -la" and noticed that my .kde directory is under "root" ownership.  I changed permissions with chmod and now I can use the apps in question.

Thanks for your help.

---

### Post by ryan^2 on 2006-12-24
I just changed ownership of the directory with the "chown" command and put the old "chmod" restrictions back on.  Everything seems to work OK.

---

