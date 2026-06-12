---
title: "Synaptic says its installed"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by kingpoiuy on 2007-05-01
Why is it that every time I try to install something via other means than Synaptic it tells me I have a dependency issue then when I go to Synaptic to check for that dependency it tells me that it IS installed!?

This has really been driving me nuts since the day I installed Ubuntu.  

But I still love Ubuntu sofar :)

---

### Post by taurus on 2007-05-01
What happens if you run these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by mac.ryan on 2007-05-01
What do you mean by "via other means than Synaptic"? Do you mean by "apt-get" or "aptitude" or do you mean by mean of some .bin or .deb packages? If it is the latter, you have to give specs of what you are trying to install, as each case is different. Also, in some cases is essential to know if you are running 32 or 64 bits version of the system...

---

### Post by zvacet on 2007-05-01
You have program installed but not able to run it,because it depends on packages named dependencies(obvious isn´ it).Find out wich dependencies you need and install them.You can find that information in **read me** file.But,best way to install(if your program is in the repos)is to use **aptitude**.With aptitude you will install program and all dependencies.

```
sudo aptitude install program_name
```

---

### Post by jmendez2 on 2007-05-01
Will the sudo command install .bin oand .deb programs?

---

### Post by NilsE on 2007-05-01
SUDO does not install anything. SUDO just allows the command to temporarily act as root which is needed to install.  

The apt-get or aptitude does the install.

---

### Post by jmendez2 on 2007-05-01
I see, I see.  That's why it prompts for a password when executed right?
Also, if it temporarily acts as root, the same password that is entered when prompted is the same whenever you execute the su command right? 

I aks because everytime I need to change to root it asks for my password but it says 'Authentication Failure'

---

### Post by taurus on 2007-05-01
You need to enter the same password that you log in with.  However, you need to belong to both groups adm and admin before you can use sudo.  What's the output of this command from a terminal?

```
id
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Pobega on 2007-05-01
Sudo = Lets a user act as a superuser (root). Is short for "superuser do". It only takes the user's pass though, not the root pass.

Su = Logs the user in as another user (Default: root). By typing su you're literally logging into another account, rather than just doing something as a superuser.

In Ubuntu your best bet is "sudo -i" for a root console.

---

### Post by jmendez2 on 2007-05-01
I get this:

jmendez@jmendez-laptop:~$ id
uid=1000(jmendez) gid=1000(jmendez) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),106(lpadmin),110(scanner),112(admin),1000(jmendez)

---

### Post by teddybairs1 on 2007-05-01
Maybe I just like the simple path, but if you right click on a .deb file on the desktop or in the home folder and select Gdebi Package Installer it will do the rest for you, including install the dependencies if it knows of them and can find them.

In general, if Synaptic says the dependency is installed, it is installed. Gdebi should be able to find the dependency as well.

---

