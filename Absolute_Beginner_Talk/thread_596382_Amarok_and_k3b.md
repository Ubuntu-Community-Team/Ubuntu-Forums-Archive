---
title: "Amarok and k3b"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by poision_heart on 2007-10-29
Hi i just installed ubuntu 7.10 .Well everything is working very well.Now i wish to install amarok and k3b.But these two packages are kde based so probably they ll install kde applications too which i dont want.Can any one guide me how to install amarok and k3b without installing unwanted kde packages?Thanks in advance

---

### Post by skyjacker on 2007-10-29
Use the Add/Remove list and only install these 2 packages. You will only install what is needed to run these 2 applications.

---

### Post by Maestro23 on 2007-10-29
For Gnome, you can take a look at Banshee also.

[http://banshee-project.org/Main_Page](http://banshee-project.org/Main_Page)

---

### Post by tdrusk on 2007-10-29
```
sudo apt-get install amarok k3b
```

---

### Post by zvacet on 2007-10-29
You can not install them without kde packages.amarok will pull lot of packages,so you can try something else.I use Mplayer and it is O.K. but you can try Banshee,VLC...
For second  K3b will not pull so many libs and it is good tool.More transparent and intuitive than Gnomebaker wich is also good.

---

### Post by Inxsible on 2007-10-29
Me for one can't live without k3b. Once I downloaded it, it had pretty much downloaded all the required kde packages that it needs. So when i downloaded amarok, it hardly downloaded 4-5 additional packages which were all amarok related.

Meaning : If you download any 1 kde app (please give leeway here - i mean a major kde app not some small game) it will pretty much download all the basic kde packages and if you install any other kde app, it wont have to download any additional packages for kde.

I hope that makes sense

---

### Post by poision_heart on 2007-10-30
> **Inxsible said:**
> Me for one can't live without k3b. Once I downloaded it, it had pretty much downloaded all the required kde packages that it needs. So when i downloaded amarok, it hardly downloaded 4-5 additional packages which were all amarok related.

Meaning : If you download any 1 kde app (please give leeway here - i mean a major kde app not some small game) it will pretty much download all the basic kde packages and if you install any other kde app, it wont have to download any additional packages for kde.

I hope that makes sense


well buddy can u tell me which packages are really needful for amarok n k3b?that ll be nice n easy for installing for me..

---

### Post by Maestro23 on 2007-10-30
> **poision_heart said:**
> well buddy can u tell me which packages are really needful for amarok n k3b?that ll be nice n easy for installing for me..

You can go into Synaptic, look each program up.  Click on Properties and it will tell you all the dependencies of the program needs.  When you go to install it, it will tell you what is being installed.

---

### Post by Inxsible on 2007-10-30
> **poision_heart said:**
> well buddy can u tell me which packages are really needful for amarok n k3b?that ll be nice n easy for installing for me..
Simply do a ```
sudo aptitude install k3b amarok
```and it will download everything that is needed.

---

