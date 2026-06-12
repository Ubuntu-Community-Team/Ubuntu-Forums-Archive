---
title: "Networkless &quot;build-essential&quot;"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by djhworld on 2006-08-15
I've just downloaded the debian package to the 'build-essential' (my network is wireless, I can't use it until I've built the driver) package.

But upon doing a "dpkg -i <build essential>" I just get a load of dependancy errors (i.e. it wanting packages such as GCC, G++ etc)

Does this mean I have to individually download each one and install them?

---

### Post by Klaidas on 2006-08-15
Yes, that's true.
If you are not able to > sudo apt-get install build-essential you will have to install dependencies manually
[http://packages.ubuntu.com/dapper/devel/build-essential](http://packages.ubuntu.com/dapper/devel/build-essential)

---

### Post by mlind on 2006-08-15
> **djhworld said:**
> I've just downloaded the debian package to the 'build-essential' (my network is wireless, I can't use it until I've built the driver) package.

But upon doing a "dpkg -i <build essential>" I just get a load of dependancy errors (i.e. it wanting packages such as GCC, G++ etc)

Does this mean I have to individually download each one and install them?

Yes, build-essential is just a meta package. If you have ubuntu cd, you can use **apt-cdrom** to add cd as a repository and install dependencies from there.

---

### Post by az on 2006-08-15
Build-essential and all of the dependencies are on the Desktop cd.  They are on a repo apart from the live session.  

Boot into your Ubuntu install and when at the desktop instert the desktop cd.  You will be brought to the package manager and you will be able to install build-essential and some other stuff from the cd.

---

### Post by djhworld on 2006-08-15
You can install dependancies from the CD?! Jesus christ!

How do you add a CD as a repository?

---

### Post by Kobalt on 2006-08-15
I believe "build-essential" can be installed from synaptic, from the CDrom of Ubuntu version installed on your computer.
Did you download the package "build-essential" from another computer then transfered it to your computer, then installed it ? 
Build-essential is actually a lot of packages used to compile apps and etc, grouped under the name of one package. It has a lot of dependencies then... You could check this out at [http://packages.ubuntu.com](http://packages.ubuntu.com) and download it from here. Can't you access the internet at all from the computer you try to install build-essential on ?

---

### Post by mlind on 2006-08-15
> **djhworld said:**
> You can install dependancies from the CD?! Jesus christ!

How do you add a CD as a repository?

Open a terminal an try
```

sudo apt-cdrom add
sudo aptitude update
sudo aptitude reinstall build-essential

```

---

### Post by syedn on 2006-08-15
if i understand the description of build-essential correctly it's really just a list right?  it lists all the packages needed for building/compiling etc, and then has them all as dependencies, so when you try to install build-essential it actually downloads all the diff. packages you would need, correct?

---

### Post by djhworld on 2006-08-15
Okay thanks guys, this has worked brilliantly, had a few problems with binutils/linux-headers, but everything is working fine now. 

Just got to carry on trying to get this damn wireless working now...

---

