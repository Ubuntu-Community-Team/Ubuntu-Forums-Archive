---
title: "Removing deps"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by kart3r on 2006-05-31
There is any command line to remove all deps relative to some package?

---

### Post by Dr. Nick on 2006-05-31
[quote=kart3r]There is any command line to remove all deps relative to some package?[/quote] 
Im sure their is, I just dont know it. If not to remove them it should atleast give all dependencies. I have heard that using aptitude insead of apt is better for removing packages and their dependencies, but it doenst work unless you use aptitude to install it..

 You could look into deborphan or gtkorphan which is a gui to deborphan. It will list all packages not being used and let you remove them, If that doesnt help then more details about what you want to accomplish may be helpfull.

---

### Post by ComplexNumber on 2006-05-31
[quote=kart3r]There is any command line to remove all deps relative to some package?[/quote] you mean orphan packages?

EDIT: oops. too late.

---

### Post by kart3r on 2006-05-31
For example, I install apache and all its dependencies.But i'm sick of it and want to remove.I remove it but the dependencies that were installed when I've installed apache still in my computer and I want to remove them.I'm using apt to do this kind of work

---

### Post by ComplexNumber on 2006-05-31
[quote=kart3r]For example, I install apache and all its dependencies.But i'm sick of it and want to remove.I remove it but the dependencies that were installed when I've installed apache still in my computer and I want to remove them.I'm using apt to do this kind of work[/quote] use a GUI instead such as Smart or synaptic. if you take a look at [this]("http://www.nongnu.org/synaptic/images/0.53-filters.png") screenshot of synaptic, it shows the orphaed packages and gives the user the option to uninstall them.

---

### Post by Dr. Nick on 2006-05-31
[quote=kart3r]For example, I install apache and all its dependencies.But i'm sick of it and want to remove.I remove it but the dependencies that were installed when I've installed apache still in my computer and I want to remove them.I'm using apt to do this kind of work[/quote]

In that case from a terminal type 

sudo aptitude install apache

that will intall it, dont use apt-get but instead just aptitude.

Then to remove it type 
sudo aptitude remove apache

Which should remove apache and any thing installed with it initally. The deborphan comes in handy if you use apt-get to install/remove and want to clean it later

---

### Post by yarlson on 2006-05-31
Try [deborphan]("http://packages.ubuntulinux.org/dapper/admin/deborphan")

> deborphan finds "orphaned" packages on your system. It determines which packages have no other packages depending on their installation, and shows you a list of these packages. It is most useful when finding libraries, but it can be used on packages in all sections.

---

### Post by aysiu on 2006-05-31
It won't help unless you install it with *aptitude* in the first place.

Always install with *aptitude* if you are ever considering getting rid of the dependencies that came with a package.

If you're using Dapper, there's a graphical version of *deborphan* called *gtkorphan*.

---

### Post by patrick295767 on 2006-05-31
To remove installed stuffs, you can also type : 
```
dpkg -l | less
```
to list ur installed packages
  
You wanna remove : 
```
apt-get remove packagename
```
  
Greetz

---

