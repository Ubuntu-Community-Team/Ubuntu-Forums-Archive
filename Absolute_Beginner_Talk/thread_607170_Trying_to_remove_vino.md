---
title: "Trying to remove vino"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by thefunnyman on 2007-11-08
I'm trying to remove vino because I would like to use tight vnc.  I'm having a problem though.  Everytime I try to kill the process, it just restarts itself, and if I try to remove it 
```

sudo apt-get remove vino

```
the package manager says it's going to remove vino and ubuntu-desktop.  I don't want to get rid of ubuntu-desktop.  Is this just some piece of ubuntu-desktop that vino uses?  It's not going to uninstall the desktop is it?

Thanks in advance for your help.

---

### Post by bodhi.zazen on 2007-11-08
Well, the simple solution is not to remove vino.

You can use and alternate vnc server on 5901 (or higher)

Just ```
vncserver :1
```

See these links :

[uwiki]VNC[/uwiki]

[uwiki]VNCOverSSH[/uwiki]

---

### Post by thefunnyman on 2007-11-08
> **bodhi.zazen said:**
> Well, the simple solution is not to remove vino.

You can use and alternate vnc server on 5901 (or higher)

Just ```
vncserver :1
```

See these links :

[uwiki]VNC[/uwiki]

[uwiki]VNCOverSSH[/uwiki]

I'd prefer to not have processes running that I am not using, or have ports open that I am not using.  If I could just get some insight about how to remove vino ( or just turn it off ), that would be extremely helpful.

---

### Post by bodhi.zazen on 2007-11-08
With a default install the vino server is not enabled, see the links I gave for how to enable / disable it.

---

### Post by Kernel_Krunch on 2008-04-22
Ok, i would like to say something here.  I had some girl try to show me some gross video and she crashed my browser with some crazy script loop.  I ended up with vino running! :(  and who knows what else.

Why is a backdoor program part of a default install?  I consider remote desktoping a advanced network feature that should only be installed and used by people who know what they are doing.  I don't want it, and now i can't remove it because its imbeded in a package that doesn't even say its for remote desktop... it says its a upgrade helper and I shouldn't remove it.  

What??

---

### Post by Oldsoldier2003 on 2008-04-22
> **thefunnyman said:**
> I'm trying to remove vino because I would like to use tight vnc.  I'm having a problem though.  Everytime I try to kill the process, it just restarts itself, and if I try to remove it 
```

sudo apt-get remove vino

```
the package manager says it's going to remove vino and ubuntu-desktop.  I don't want to get rid of ubuntu-desktop.  Is this just some piece of ubuntu-desktop that vino uses?  It's not going to uninstall the desktop is it?

Thanks in advance for your help.

Removing ubuntu-desktop only removes the metapackage, it will not uninstall your desktop. Been there done that many times ;) you only need to remember to reinstall the meta package before you do a distro upgrade.

Actually the ubuntu-desktop metapackage gets removed by me early in the lifespan of my installations and never gets reinstalled. WHy? Because reinstalling the meta package causes a bunch of programs which i have painstakingly eradicated (such as vino and ekiga) to be reinstalled.

---

### Post by Kernel_Krunch on 2008-04-26
> **Oldsoldier2003 said:**
> Removing ubuntu-desktop only removes the metapackage, it will not uninstall your desktop. Been there done that many times ;) you only need to remember to reinstall the meta package before you do a distro upgrade.

Actually the ubuntu-desktop metapackage gets removed by me early in the lifespan of my installations and never gets reinstalled. WHy? Because reinstalling the meta package causes a bunch of programs which i have painstakingly eradicated (such as vino and ekiga) to be reinstalled.

removing ubuntu-desktop before updating the CD-base install of ubuntu caused werd update problems for me.  instead of the 250MB of updates I had 100MB, and an attempt to install flash player failed.  I am using ubuntu64 7.10. 

Again, why is the remote desktop "feature" a critical part of the OS?

---

