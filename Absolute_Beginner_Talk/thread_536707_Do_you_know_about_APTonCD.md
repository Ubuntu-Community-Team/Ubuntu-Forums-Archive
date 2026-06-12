---
title: "Do you know about APTonCD?"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by antharr on 2007-08-28
APTonCD is a ultilty that allows you to back up all your apps. If you have to reinstall Ubuntu, all of your apps will be stored on a CD. All you have to do is a restore with the APTonCD app and all of your apps are installed without all of the headache of installing all of them individually.  Made this thread just to make people aware of a backup option for Ubuntu.

---

### Post by rahimveron on 2007-08-28
Thabk you for the info. It is a life saver if you wanna re-install Ubuntu and also for those who dont have internet connection, right?

---

### Post by Zootropo on 2007-08-28
You can also get the list of installed packages with dpkg --get-selections > packages or you can copy the deb files from /var/cache/apt/archives, but this is way much more confortable.

I talked about these three methods some time ago at my blog (spanish):
[Copia de seguridad de los programas instalados en Ubuntu](http://mundogeek.net/archivos/2007/06/11/copia-de-seguridad-de-los-programas-instalados-en-linux/)

---

### Post by antharr on 2007-08-28
> **rahimveron said:**
> Thabk you for the info. It is a life saver if you wanna re-install Ubuntu and also for those who dont have internet connection, right?

Yes. It places your packages on a CD or DVD so that you don't have to download them all over again.

---

### Post by antharr on 2007-08-28
> **Zootropo said:**
> You can also get the list of installed packages with dpkg --get-selections > packages or you can copy the deb files from /var/cache/apt/archives, but this is way much more confortable.

I talked about these three methods some time ago at my blog (spanish):
[Copia de seguridad de los programas instalados en Ubuntu](http://mundogeek.net/archivos/2007/06/11/copia-de-seguridad-de-los-programas-instalados-en-linux/)

Cool. I searched it a bit last night on this site and didn't come up with much. I just thought I would get it out there for everyone to see. I was about to get another PC and was looking for options that would let me back up my software. Installs are going to be much less painful now, not saying they were that bad to begin with. Installs are much easier for me now that I have moved over to Ubuntu (well about 90%). I still use the evil OS for a couple things and it's there when I have company that's not comfortable with Linux.

---

### Post by s26c.sayan on 2007-08-28
AptonCD is a cool app!

I had to reinstall Ubuntu very often after breaking everything (I do that quite often!) and since my ISP charges me per mb of download, aptonCD saved me quite a few bucks! :)

---

### Post by bodhi.zazen on 2007-08-28
Here is an English link :

home page :
	how to : [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by Rick Z on 2007-08-29
instead of transfer package into cd/dvd, could I transfer it into usb stick and deploy it to another pc?  is there a tutorial somewhere?  Please guide me.  thanks.,

---

### Post by s26c.sayan on 2007-08-29
> **Rick Z said:**
> instead of transfer package into cd/dvd, could I transfer it into usb stick and deploy it to another pc?  is there a tutorial somewhere?  Please guide me.  thanks.,

I guess you can!

Just create an iso as usual but instead of burning the image on some CD/DVD, just copy the iso onto the usb stick. 
Now carry the stick to the other machine (aptoncd should be installed in that) and choose the option 'restore iso' from aptoncd on the iso in the stick.

---

### Post by Rick Z on 2007-08-31
nice, I did it to my usb stick.  How do I use the saved .iso package to another pc?  I guess the other pc also need to install aptoncd as well right?

---

### Post by s26c.sayan on 2007-08-31
> **Rick Z said:**
> nice, I did it to my usb stick.  How do I use the saved .iso package to another pc?  I guess the other pc also need to install aptoncd as well right?

Right, the other PC will need aptonCD as well so that you can use the 'Restore iso Image' option on it!!

---

### Post by Rick Z on 2007-09-01
I did install aptoncd on other box, but even when I do the restore.  I didn't see any other package been 'install.'  I guess  the option was to  restore the packages, but not acutally install the package.  How could I run the installation?  Where are the restore packages reside by aptoncd application?  What command should I use to see all the aptoncd restore packages.  Please help...

---

### Post by s26c.sayan on 2007-09-02
AptonCD only restores the packages, doesn't install them automatically!

Actually, when you install something on your box via apt-get (or synaptic, same thing!), a copy of the corresponding deb package(s) , including all the dependencies are stored under **/var/cache/apt/archives**. You can copy all of them and carry them to a new machine and put them in the same directory of the new  machine. This would (in most cases) allow you to install these packages in the new machine w/o downloading anything! 
This entire process is kinda automated by AptonCD, but you still have to install them explicitly!

To do so, simply do 'sudo apt-get install <packagename>' as you normally do! But in this case, apt-get won't download packages from the online repos, but from the cached packages!

BTW, all about aptonCD is there in the [Documentation]("http://aptoncd.sourceforge.net/doc-manual.html")!

---

### Post by Rick Z on 2007-09-05
I found the aptoncd documentation as below. 

“The packages selected are copied from the APTonCD media to /var/cache/apt/archives/ directory. This way the packages are available and you can install them using apt-get, aptitude or synaptic without need to download them.”

How can I or should I change the apt-get, aptitude or synaptic to directly see the package is listed in /var/cache/apt/archives?  For example, I have partimage as one of the package, but when I use apt-get install partimage.  It will give me the error because the pc I am testing for aptoncd doesn’t have any internet connection.  

Please help…

---

### Post by Majorix on 2007-09-05
Hi, here is an idea on how to install the packages saved by APTonCD.

Unpack the iso to a directory. Then cd to that directory using terminal and finally type in this:
```
sudo dpkg -i *.deb
```

---

### Post by por100pre1 on 2007-09-05
Maybe not related, but a fellow poster told me about a tool called apt-mirror, a tool for backing up the whole repos. The poster gave me this [link]("http://www.linux.com/feature/115226") to a how-to. I haven't tried it yet. :-k

---

### Post by chrome307 on 2007-09-05
Thanks for the info especially on Apt-Mirror

Just to clarify, do we simply add the additional sources to the text file 'mirror.list'  

eg


```


## Example sources
##

# sarge's section
deb http://ftp.fi.debian.org/debian sarge main contrib non-free
deb-src http://ftp.fi.debian.org/debian sarge main contrib non-free

deb http://security.debian.org/debian-security sarge/updates main contrib non-free
deb-src http://security.debian.org/debian-security sarge/updates main contrib non-free

deb http://ftp.fi.debian.org/debian sarge main/debian-installer

# MY PERSONAL LIST TAKEN FROM THE SCREENSHOT
deb http://medibuntu.sos-sts.com ( just made up !!)



```

[IMG]http://1pix.org/out.php/i1969_1.jpg[/IMG]

But would do you do about packages that need authorisation ???

[IMG]http://1pix.org/out.php/i1970_2.jpg[/IMG]

---

### Post by por100pre1 on 2007-09-05
I got a question here: What are those Debian repositories for? They need a # before them.

---

### Post by s26c.sayan on 2007-09-06
> **Rick Z said:**
> I found the aptoncd documentation as below. 

“The packages selected are copied from the APTonCD media to /var/cache/apt/archives/ directory. This way the packages are available and you can install them using apt-get, aptitude or synaptic without need to download them.”

How can I or should I change the apt-get, aptitude or synaptic to directly see the package is listed in /var/cache/apt/archives?  For example, I have partimage as one of the package, but when I use apt-get install partimage.  It will give me the error because the pc I am testing for aptoncd doesn’t have any internet connection.  

Please help…

Just a tip: Make sure the /etc/apt/sources.list file is same in both the host and target machines!!
Maybe you shld also try a 'sudo apt-get update' before trying to install ( it will give errors due to internet unavailabilty...but still try it)

Otherwise, you can install packages individually ( along with dependencies) using 'sudo dpkg --install /var/cache/apt/archives/<package>.deb'

---

### Post by s26c.sayan on 2007-09-06
> **por100pre1 said:**
> I got a question here: What are those Debian repositories for? They need a # before them.

If you mean the 'deb' word in the beginning of the lines, it implies that the  corresponding line refers to a repository which contains debian BINARY files. Ubuntu uses deb package format. It will have 'deb-src' at beginning, if the repository contains debian source code files.

If a line starts with '#' that means it is commented out. If it comes in front of a repository line, it means that repository is disabled!!

More info : [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by kelvin spratt on 2007-09-06
People If you read apt help it explains how to reinstall from the disc you created using Synaptic, you add the disc to synaptic using aptoncd and you will find the entries in synaptic under aptoncd in the left hand pane and you can just tick and that's it or you can restore them into the catch in var and again use synaptic to reinstall its all in the help, thats how i found out how to do use it and its superb piece of kit,

---

### Post by chrome307 on 2007-09-06
[IMG]http://i6.tinypic.com/4cdinva.jpg[/IMG]

---

### Post by por100pre1 on 2007-09-06
The **Installable from CD-ROM/DVD** section works with Ubuntu CDs and DVDs. I think it works with APTonCD disks too, but I'm not sure. Insert the CD and the system will ask for confirmation.

---

### Post by por100pre1 on 2007-09-06
> **s26c.sayan said:**
> If you mean the 'deb' word in the beginning of the lines, it implies that the  corresponding line refers to a repository which contains debian BINARY files. Ubuntu uses deb package format. It will have 'deb-src' at beginning, if the repository contains debian source code files.

If a line starts with '#' that means it is commented out. If it comes in front of a repository line, it means that repository is disabled!!

More info : [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

That's *exactly* what I mean. I would disable those Debian repositories if it were my system. Ubuntu and Debian repos don't mix quite well. :)

---

