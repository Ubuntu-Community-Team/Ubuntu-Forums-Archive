---
title: "Installing GIMP? [Resolved]"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by Jack the R on 2006-12-17
What package do I need to download from gimp.org?

---

### Post by yabbadabbadont on 2006-12-17
None.  Gimp is in the Ubuntu repositories.  You can install it in a terminal using "sudo apt-get install gimp" or through Synaptic.  It's dependencies will be installed automatically along with it.

---

### Post by aysiu on 2006-12-17
You don't.

Assuming you're using Kubuntu, just click on the KMenu and go to Add/Remove Programs and click to install it.

If you're using Ubuntu, it should already be installed.

---

### Post by Jack the R on 2006-12-17
I'm om Kubuntu, as aysiu guessed.  I tried add/remove programs but GIMP was not listed.

What are repositories?  Are they on the install cd?  The pc I put Kubuntu on doesn't have internet access.

---

### Post by macogw on 2006-12-17
Repositories are online servers for you to download/install from.

On gimp.org, download gimp-2.2.13.tar.gz and extract it to ~/src (or wherever you put your source files), then in the terminal type in:
```
cd ~/src/gimp-2.2.13
./configure
make
make install

```
If ./configure spits out any errors at you, you're going to have to go download the necessary dependencies from [http://packages.ubuntu.com/edgy/graphics/gimp](http://packages.ubuntu.com/edgy/graphics/gimp) there and install them before re-attempting ./configure

---

### Post by aysiu on 2006-12-17
> **Jack the R said:**
> I'm om Kubuntu, as aysiu guessed.  I tried add/remove programs but GIMP was not listed.

What are repositories?  Are they on the install cd?  The pc I put Kubuntu on doesn't have internet access.
It's not in Add/Remove? That's weird. Have you tried Adept Package Manager? That tends to list more packages. If you don't want to wade through packages, you can also just paste this command into the terminal in order to install it: ```
sudo aptitude update && sudo aptitude install gimp
``` Please don't follow macogw's instructions unless mine don't work. Installing from source isn't necessary and can be quite a headache.

---

### Post by Jack the R on 2006-12-17
I tried Linux back in the Mandrake 7.0 days, will avoid installing from source if at all possible ](*,) 

Do I need to install GTK?

---

### Post by Bachstelze on 2006-12-17
No, thanks to the magic of APT, installing GIMP will also install everything it needs to run. Just do *sudo apt-get install gimp* and you will be fine.

---

### Post by Jack the R on 2006-12-17
In Kubuntu "add/remove" programs starts "Adept Installer."

By choosing the "any suite" option in Adept I can find GIMP, BUT it is greyed out and can not be installed.

FWIW the suite options are KDE, Gnome, and Any Suite.

---

### Post by Bachstelze on 2006-12-17
That's the reason why we're telling you to use the command line ;)

Open a terminal (Alt+F2 > konsole) and type this :

```
sudo apt-get install gimp
```

---

### Post by bsell on 2006-12-17
> **Jack the R said:**
> In Kubuntu "add/remove" programs starts "Adept Installer."

By choosing the "any suite" option in Adept I can find GIMP, BUT it is greyed out and can not be installed.

FWIW the suite options are KDE, Gnome, and Any Suite.
 
You need to enable the repositories by uncommenting them. Then you can install the GIMP.

---

### Post by Jack the R on 2006-12-17
Tried the command line technique (both aysiu's and HymnToLife's).  Got different error messages but both to the effect that GIMP isn't there and nothing was done.

In case it needs to be mentioned again, the Kubuntu machine doesn't connect to the internet.  If GIMP didn't come on the (6.10) install cd, it isn't there.

---

### Post by aysiu on 2006-12-17
> **Jack the R said:**
> Tried the command line technique (both aysiu's and HymnToLife's).  Got different error messages but both to the effect that GIMP isn't there and nothing was done.

In case it needs to be mentioned again, the Kubuntu machine doesn't connect to the internet.  If GIMP didn't come on the (6.10) install cd, it isn't there.
Whoops--missed that major point! No internet.. that's going to hurt. Are you using Edgy Eft or Dapper Drake right now?

---

### Post by Bachstelze on 2006-12-17
Oh, sorry, I guess I missed that. Well, GIMP doen't come in the Kubuntu CD indeed. An easy way if you can have a connection from somewhere else would be to downloat an Ubuntu *Alternate* CD and install from it.

---

### Post by Jack the R on 2006-12-17
> **aysiu said:**
> Whoops--missed that major point! No internet.. that's going to hurt. Are you using Edgy Eft or Dapper Drake right now?

6.10 is Edgy Eft, right?

---

### Post by aysiu on 2006-12-17
Okay, I don't know where you live or what processor you have, but let's say, for this example, you live in Europe and are using i386 (instead of AMD64 or PowerPC)...

Using the computer you have that *is* connected to the internet, download these files to a flash drive or some other media (iPod, zip drive, etc.):
[http://fr.archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp_2.2.13-1ubuntu1_i386.deb](http://fr.archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp_2.2.13-1ubuntu1_i386.deb)
[http://fr.archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp-data_2.2.13-1ubuntu1_all.deb](http://fr.archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp-data_2.2.13-1ubuntu1_all.deb)
[http://fr.archive.ubuntu.com/ubuntu/pool/main/a/aalib/libaa1_1.4p5-30_i386.deb](http://fr.archive.ubuntu.com/ubuntu/pool/main/a/aalib/libaa1_1.4p5-30_i386.deb)
[http://fr.archive.ubuntu.com/ubuntu/pool/main/g/gimp/libgimp2.0_2.2.13-1ubuntu1_i386.deb](http://fr.archive.ubuntu.com/ubuntu/pool/main/g/gimp/libgimp2.0_2.2.13-1ubuntu1_i386.deb)
[http://fr.archive.ubuntu.com/ubuntu/pool/main/libw/libwmf/libwmf0.2-7_0.2.8.3-3.1ubuntu1_i386.deb](http://fr.archive.ubuntu.com/ubuntu/pool/main/libw/libwmf/libwmf0.2-7_0.2.8.3-3.1ubuntu1_i386.deb)

Then transfer them to your Kubuntu's desktop and paste these commands in the terminal: ```
cd ~/Desktop
sudo dpkg -i *.deb
``` That should get it installed. Installing software without internet on Kubuntu is a pain.

---

### Post by Jack the R on 2006-12-17
Thanks, but let's look at one more option before I go the "scenic" route.  There's nothing stopping me from hauling the Kubuntu PC over here and hooking it up to the internet temporarily.  I didn't want to connect it while running XP because I don't know XP well enough to de-worm it if it gets clogged with spyware.  A temporary connection while running Linux should be fine.

I'll see if I can get the net working under Linux.

---

### Post by aysiu on 2006-12-17
If you don't mind hauling it over to hook it up, that's cool--the command I gave you earlier might not work right away, though. When you install Kubuntu without an internet connection, it automatically comments out (for all practical purposes, removes) all the online repositories, so you'd have to uncomment those first before you could use *apt-get* or *aptitude* to install GIMP.

```
kdesu kwrite /etc/apt/sources.list
``` will allow you to edit your sources. You should notice a bunch of what look like web addresses. Any that have a # sign at the beginning of the line are commented out (i.e., deactivated). Delete the # sign from all of those lines and save. Then ```
sudo aptitude update
sudo aptitude install gimp
``` should do it.

Otherwise, it's not as scenic as you might think--just open up a web browser in your connected computer (which you already have open apparently), then click on the links I gave you--they should automatically download the files you need, transfer them to Kubuntu, and then paste in those two commands.

---

### Post by Jack the R on 2006-12-17
aysiu - What version of GIMP does that install?

When using Adept or the earlier console commands, how long does it take for the latest version of GIMP to become available when there's an update?

---

### Post by aysiu on 2006-12-17
Everything I've given you before (Adept, downloading the individual .deb files, using the Konsole) all are basically the same thing--using the online repositories to install prepackaged files needed to run GIMP.

The version of GIMP they install is 2.2.13.

Software in Ubuntu gets updated with every new release (every six months). So when Edgy Eft was released two months ago, 2.2.13 was the latest version of GIMP. When Feisty Fawn is released in April, it will use whatever the latest version of GIMP is at that time, and so on.

Occasionally, you do get updated versions between releases. Sometimes this happens because of security issues (the update to the application is a patch for a security hole). Sometimes it's what's called a "backport," when someone takes the trouble to package the newer version of an application for an older version of Ubuntu.

Most of the time, though, you just wait, and every six months, you get the most up-to-date software... until the next six months.

---

### Post by greenimacg3 on 2006-12-17
He said he didn't have web access.

---

### Post by Bachstelze on 2006-12-17
You should read more carefully...

> **Jack the R said:**
> There's nothing stopping me from hauling the Kubuntu PC over here and hooking it up to the internet temporarily.

---

### Post by greenimacg3 on 2006-12-17
Yes, I am sorry, I didn't realize that there is more than one page to the topic. My bad.

---

### Post by Jack the R on 2006-12-17
greenimacg3 - I've got two machines, an old one for web access and a new one for getting work done.  

aysiu - Hmm - latest stable version of GIMP appears to be 2.2.13, so your files should work for now, but I want the latest stable version of GIMP as soon as it comes out.  I'll cross that bridge when I come to it though.

I'm on a 3.4 ghz P4, but in U.S.  Will your links still work?

---

### Post by aysiu on 2006-12-17
Yeah, they'll work just fine.

---

### Post by Jack the R on 2006-12-17
O.K., I'll download everything and report back when it's done.

---

### Post by Jack the R on 2006-12-17
That was surprisingly easy.  

Now - how does one make the pressure sensitivity work on the Wacom?

---

### Post by aysiu on 2006-12-17
When you have an internet connection, software installation is a cinch.

Read more here:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

I've created a new thread for your Wacom tablet issue:
[ Need help with pressure sensitivity on WACOM](http://ubuntuforums.org/showthread.php?t=320760)

---

### Post by Jack the R on 2006-12-17
I installed via the links - might as well start learning the command line stuff for when the next GIMP comes out.   

Thanks for the how-to-install link!

---

