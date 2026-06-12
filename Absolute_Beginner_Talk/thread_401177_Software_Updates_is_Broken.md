---
title: "Software Updates is Broken"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by chaplanger on 2007-04-04
Using Add/Remove today I attempted to add the Java plug-in for firefox.  This failed to properly install and came back with error messages.  However, I cannot uninstall the Java plug-in from Add/Remove.  When I go here it will allow me to highlight the Java plug-in, but will not pull up the right click menu to remove.

Since this occurred I cannot use the update function (Software Updates) it returns the following message: 
```
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
```

When I  use
```
sudo apt-get install -f
```

I come to messages of failed to install.  
The latest wrinkle is that  the terminal and  sudo apt-get install -f  returns the following information:

```
david@david-desktop:~$ sudo apt-get install -f
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
david@david-desktop:~$ 
```

This error screen has also come up.

```
W: Duplicate sources.list entry http://us.archive.ubuntu.com edgy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com edgy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-i386_Packages)
```

Any ideas on a solution.

---

### Post by dca on 2007-04-04
Hmmm, got nothing....   Either another instance of synaptic is running or somehow either using easyubuntu/automatix or 'system -> admin -> synaptic -> repos' duplicate repos or whatever are active...???

---

### Post by chaplanger on 2007-04-04
Now as I logged out of Firefox and closed everything down in Ubuntu, I received this message:

```
You have 1 broken package on your system!

Use the "Broken" filter to locate it.
```

OK -- Where is the "broken filter" and once located, how is it fixed?

---

### Post by xopher on 2007-04-04
> The latest wrinkle is that the terminal and sudo apt-get install -f returns the following information:

Make sure any other apt-process is terminated before running this. Eg. synaptic, update-manager, add-remove etc.

---

### Post by xopher on 2007-04-04
> **chaplanger said:**
> Now as I logged out of Firefox and closed everything down in Ubuntu, I received this message:

```
You have 1 broken package on your system!

Use the "Broken" filter to locate it.
```

OK -- Where is the "broken filter" and once located, how is it fixed?

Lower left corner of Synaptic, Custom Filter -> Select Broken in the list to the left.

---

### Post by Maestro23 on 2007-04-04
> **chaplanger said:**
> Now as I logged out of Firefox and closed everything down in Ubuntu, I received this message:

```
You have 1 broken package on your system!

Use the "Broken" filter to locate it.
```

OK -- Where is the "broken filter" and once located, how is it fixed?

Beat me to it. (Synaptic>>Edit>>Fix broken pkg)

---

### Post by compmodder26 on 2007-04-04
To fix your package index, make sure you don't have Synaptic or Add/Remove programs open.  Then, in a terminal, do the "sudo apt-get install -f" command.

edit: or do what Maestro23 said above

---

### Post by BarfBag on 2007-04-04
What changes did you make to your sources.list?  Did you make a back-up?

The problem with your second error is that you had Software Update running as you tried to use apt-get.  If you haven't already done so, restart your computer.  When it boots back up, do NOT open any package manager (Synaptic, Add/Remove or Software Update).

Open up terminal and edit your sources list.

> gksudo gedit /etc/apt/sources.list

Skim through it and look for duplicate entries.  If you can't find any, comment out (add # in front of it) the changes you made before this started.  This is assuming that you made changes in the first place.

Now, run apt-get update and install -f.

> sudo apt-get update
> sudo apt-get install -f

---

### Post by chaplanger on 2007-04-04
xopher & maestro23,
Thanks for the help -- using your synaptic advise  fixed the problem.  Situation corrected and everything is running smoothly now.

Again, thanks!

---

