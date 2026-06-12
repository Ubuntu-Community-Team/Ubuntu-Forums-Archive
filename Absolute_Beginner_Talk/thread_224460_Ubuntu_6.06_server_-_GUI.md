---
title: "Ubuntu 6.06 server - GUI"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by samare on 2006-07-28
Hi,

I just installed Ubuntu 6.06 server on VMWare. How do I get the GUI(Gnome)? I set the run level to 5 in /etc/inittab file. But still it doesn't load the GUI. Please advice.

samare

---

### Post by FizDev on 2006-07-28
Hmmm... try :
```
sudo apt-get install ubuntu-desktop
```

---

### Post by samare on 2006-07-28
Hi,

I just entered the command but getting a message as follows.
"E: Couldn't find the package ubuntu-desktop".

Do I have to download the about package seperatly? Doen't it come with the Ubuntu 6.06 Server CD?

samare

---

### Post by samare on 2006-07-28
> **FizDev said:**
> Hmmm... try :
```
sudo apt-get install ubuntu-desktop
```



Hi,

I just entered the command but getting a message as follows.
"E: Couldn't find the package ubuntu-desktop".

Do I have to download the about package seperatly? Doesn't it come with the Ubuntu 6.06 Server CD? Please advice

samare

---

### Post by kinematic on 2006-07-28
try:sudo aptitude update,sudo aptitude install ubuntu-desktop.
the ubuntu-desktop package should be in the standard repo you're connected to.

---

### Post by samare on 2006-07-28
I tried aptitude but failed. Then I downloaded ubuntu-desktop package and tried with a command dpkg -i ubuntu-desktop_0.119_i386.deb. Then it says to install lots of dependencies.

Is there any way to install all the packages (or complete desktop package)once instead of installing one by one? I'm very much new to Ubuntu. Please help.

samare

---

### Post by ubuntuuser on 2006-07-28
The package ubuntu-desktop is a so-called meta-package. That means that the package itself only contains information on which packages should be installed to have a full ubuntu desktop. So if you want to have the Gnome desktop, just install ubuntu-desktop and all dependencies. 
Have you tried```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by samare on 2006-07-28
> **ubuntuuser said:**
> The package ubuntu-desktop is a so-called meta-package. That means that the package itself only contains information on which packages should be installed to have a full ubuntu desktop. So if you want to have the Gnome desktop, just install ubuntu-desktop and all dependencies. 
Have you tried```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

Yes, I tried those commands. And I tried "apt-get -f install" but none of them worked. Today is my very first day in Ubuntu. I should have started with the Desktop version of Ubuntu or Kubuntu. Thanks for all the support. But still I think that it would be great if there is one desktop package including all the dependencies.

samare

---

### Post by ubuntuuser on 2006-07-28
One package including every dependency wouldn't make much sense. All dependecies are available, so why build another package that includes things that are already there? It wouldn't make much of a difference. Instead of downloading 10 packages with one command you would download one package with one command, but the ammount of data would still be the same. IMHO, the fact that the whole package-system is very modular is definitely a huge advantage to the approach you propose.

---

### Post by Indras on 2006-07-28
Please let us know what output you get from the following commands:
sudo apt-get update
sudo apt-get install ubuntu-desktop

I'm guessing it's just a matter of putting the right repositories in your /etc/apt/sources.list file.  An output from the two above commands will tell for sure.

---

### Post by 3rdalbum on 2006-07-28
The "server" CD is for headless servers i.e. ones which are just going to sit in a corner and serve page requests; that's why there is no GUI included.

I suggest you download the full Ubuntu ISO, burn it to disk and install it. It will probably end off being easier on your internet connection than apt-getting the whole ubuntu-desktop metapackage.

Just checking: Do you have internet access on Ubuntu? To check, type:

```
ping -c 3 www.ubuntu.com
```

If it tells you that it can't find [www.ubuntu.com](www.ubuntu.com), or if it doesn't seem to be doing anything, your internet connection has not been configured, and that explains why you can't apt-get the ubuntu-desktop metapackage.

---

### Post by samare on 2006-08-01
Hi All,

It's done:D . It was my mistake. I have entered a wrong command as "sudo apt-get -f insatall ubuntu-desktop". This may be a common mistake of linux noobs. But the problem was that it didn't say that the command was wrong. Instead it was giving errors such as Unmet dependencies. Anyway Thanks a lot for all the support.

The correct command is:

sudo apt get -f install

---

### Post by samare on 2006-08-01
> **3rdalbum said:**
> The "server" CD is for headless servers i.e. ones which are just going to sit in a corner and serve page requests; that's why there is no GUI included.

I suggest you download the full Ubuntu ISO, burn it to disk and install it. It will probably end off being easier on your internet connection than apt-getting the whole ubuntu-desktop metapackage.

Just checking: Do you have internet access on Ubuntu? To check, type:

```
ping -c 3 www.ubuntu.com
```

If it tells you that it can't find [www.ubuntu.com](www.ubuntu.com), or if it doesn't seem to be doing anything, your internet connection has not been configured, and that explains why you can't apt-get the ubuntu-desktop metapackage.

Hi,

You are dead right. It took around 12 hours to download all the dependency packages from the Internet. This way is not good for those who experience slow internet connection.

---

