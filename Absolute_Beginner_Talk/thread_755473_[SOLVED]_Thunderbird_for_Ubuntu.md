---
title: "[SOLVED] Thunderbird for Ubuntu"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by raffeyg on 2008-04-14
I am so completely new to Linux/Unix/Ubuntu, so I need a little hand holding.  I just want to install Thunderbird on the machine.  I have downloaded from mozilla and unzipped into a folder, now what do I do to install?  I must confess that I am so used to Windows and just clicking on an exe or installer file and having it work that I have become lazy.  Any help would be appreciated. :)

---

### Post by munkyeetr on 2008-04-14
The easiest way to install Thunderbird is to do the following:

1) Open a Terminal window (**Applications** -> **Accessories** -> **Terminal**)
2) Type the following in the Terminal window:
```

sudo apt-get install thunderbird

```

Enter your password, and when it's done you should be able to launch TB from the **Applications** menu.

---

### Post by konungursvia on 2008-04-14
> **raffeyg said:**
> I am so completely new to Linux/Unix/Ubuntu, so I need a little hand holding.  I just want to install Thunderbird on the machine.  I have downloaded from mozilla and unzipped into a folder, now what do I do to install?  I must confess that I am so used to Windows and just clicking on an exe or installer file and having it work that I have become lazy.  Any help would be appreciated. :)

Or, you could just move the installer package to "/home/yourname/" and then open a terminal and type "sudo tar xvf thunderbird*" and then your password. Don't type thunderbird* unless that's the exact beginning of your package name, I forget if it starts with mozilla or not. Then it should install fine. Or, just do what the other guy says. Delete your package and install from the repositories (repos) using aptitude or apt-get on the command line in the terminal window, also called a shell.

---

### Post by laffinet on 2008-04-14
Or you go to System -> Administration -> Synaptic Package Manager

Search for Thunderbird. Right click the right entry, select 'mark for installation'. Click apply. 

That's how you can find and install heaps of software.

---

### Post by raffeyg on 2008-04-15
Thanks everyone, got it.  I appreciate all the help.

---

