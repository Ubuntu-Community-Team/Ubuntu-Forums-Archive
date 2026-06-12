---
title: "How to install applications without internet access."
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by Addison13248 on 2006-05-11
I am running Ubuntu on a old laptop, I blew the modem awhile back, and don't really want to spend the money for a new one. How do I install applications if I can't access the internet?

Thanks,

Addison

---

### Post by aysiu on 2006-05-11
It's going to be difficult.
Do you have *any* internet access (say, on another computer)?

I realize you must have *some* internet access (as you are posting on an online forum), but do you have access to a machine on which you can boot a Ubuntu live CD?

---

### Post by Addison13248 on 2006-05-11
I have access on my windows laptop.

Yes, I do.

Addison

---

### Post by Clay85 on 2006-05-12
Hmm I'm trying to teach myself how to install stuff and someone gave me this link:

[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

Scroll down to "Using CDs as offline package repositories". I have no idea what it's talking about, but maybe you do. Hope this helps.

---

### Post by aysiu on 2006-05-12
[QUOTE=Addison13248]I have access on my windows laptop.

Yes, I do.

Addison[/QUOTE] Does a Ubuntu live CD recognize that laptop's internet connection? If so, we're in business. If not, it'll be painful--extremely painful.

Pop in a Ubuntu live CD on the laptop. The live CD has to be the same version as the Ubuntu you have on your other computer (Breezy/Breezy or Dapper/Dapper).

Go to the terminal and type ```
sudo rm -rf /var/cache/apt/archives/*.deb
``` Then go to System > Administration > Synaptic Package Manager and "install" (these programs won't really be installed, they'll just be pretend installed to your laptop's RAM) the programs you want. Then copy all the .deb files from /var/cache/apt/archives to some other device (an iPod, a USB stick, etc.).

Finally, copy those .deb files from the device to your old laptop's Ubuntu desktop and type this in a terminal: ```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

### Post by darf681 on 2006-05-12
As a side note...

If you can get access to a broadband connection and a burner.  Download the automatix cd.  You can search for it here in the forums. :)  It can load a lot of good applications/plugins/etc  to get you started.

---

### Post by aysiu on 2006-05-12
More info on the Automatix CD [here](http://www.ubuntuforums.org/showthread.php?t=145889).

---

### Post by Addison13248 on 2006-05-12
I am afriad, my attemp to connect has failed. I am not that good with using Ubuntu, I have been using it for a couple of weeks now. I still have to use my windows computer because I can't figure out how to connect. I have a dial up connection. I went into System > Administration > Networking and enabled the modem. I filled the number, username and password in. I don't know what port I would hook my modem up too. Microsoft makes it easy by already asigning it. I am not sure what the dialing prefix is either. 

Thanks 

Addison

---

### Post by EdThaSlayer on 2006-05-13
[QUOTE=Addison13248]I am running Ubuntu on a old laptop, I blew the modem awhile back, and don't really want to spend the money for a new one. How do I install applications if I can't access the internet?

Thanks,

Addison[/QUOTE]

You can always visit the ineternet cafe's and download the .tar,.rpm, or any of the other file extensions associated with Linux. Then all you have to do is compile/install everything on your laptop(with USB flashdrives nowadays moving information from computer to computer is easy):-k

---

### Post by Addison13248 on 2006-05-14
[QUOTE=EdThaSlayer]You can always visit the ineternet cafe's and download the .tar,.rpm, or any of the other file extensions associated with Linux. Then all you have to do is compile/install everything on your laptop(with USB flashdrives nowadays moving information from computer to computer is easy):-k[/QUOTE]

Yeah, I have several that I want to install. How do I compile them without a compiler. I have several on my windows computer but none that I know of on my Ubuntu computer.

Addison

---

### Post by jtibau on 2006-05-14
[QUOTE=Addison13248]Yeah, I have several that I want to install. How do I compile them without a compiler. I have several on my windows computer but none that I know of on my Ubuntu computer.

Addison[/QUOTE]

By default ubuntu doesn't install any compiler. But gcc and all the compiling stuff are available from the install cd.
Type "sudo apt-get install build-essentials" in a terminal. That should get you all that you need to compile/install stuff in linux

Compiling ain't that hard :) you just unpack the tarball in some folder. Then follow instructions on the INSTALL file. It basically means doing:
./configure
make
make install
That's pretty much it. mmm You have to be root or do the last two ones with sudo.

---

### Post by Addison13248 on 2006-05-14
Every time I time type "sudo apt-get install build essentials" into terminal it gives me "W: couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breazy/univers Packages" and so on and on. I know how to compile, just never done it on Ubuntu.

---

### Post by ComplexNumber on 2006-05-14
[quote=Addison13248]I am running Ubuntu on a old laptop, I blew the modem awhile back, and don't really want to spend the money for a new one. How do I install applications if I can't access the internet?

Thanks,

Addison[/quote] do exactly the same as me. manually doanload them and then burn the applications to cd/dvd, then go back and to back and to, fetching the necessary dependencies :D. there isn't really any shortcuts.
without an internet connection, ubuntu/kubuntu aren't much good. try something like fedora core 5 or suse 10.1 because they provide far more packages by default. i have no internet connection to my linux box either, thats why i have fedora core 5 installed instead. seriously, don't bother with ubuntu if you have no internet connection - if you really want to use ubuntu, wait until you have an internet connection

---

### Post by Addison13248 on 2006-05-14
I have them downloaded, and on my desktop, I just don't have the permision to open the files to install them.  Every time I type "apt-get install basic-essentials" it  tells me "E: Could not open lock file /var/lib/apt/lists/lock - open (13 permissions denied)
E:  Unable to lock the list directory" 
I thought I was the administrator, I am not the owner also when I go to the file and right click and hit properties. Everything under System>Administration>Users and Groups is enable for my user. There are no other users on the computer that I know of. Next weekend I am going to my mom's office, to use the network so I will beable to download them. I find Ubuntu much like windows in the menus and stuff and like OS X when you insert the media into the computer. I would recomend it for beginners or people with internet access.

---

### Post by Addison13248 on 2006-05-14
[QUOTE=ComplexNumber]do exactly the same as me. manually doanload them and then burn the applications to cd/dvd, then go back and to back and to, fetching the necessary dependencies :D. there isn't really any shortcuts.
without an internet connection, ubuntu/kubuntu aren't much good. try something like fedora core 5 or suse 10.1 because they provide far more packages by default. i have no internet connection to my linux box either, thats why i have fedora core 5 installed instead. seriously, don't bother with ubuntu if you have no internet connection - if you really want to use ubuntu, wait until you have an internet connection[/QUOTE]

I have done that, when I type "apt-get install build-essentials" it tells me that it can't open the lock files. /var/lib/apt/lists/lock. I am taking it to my mom's office  next weekend, there she has a fast network where i can download things. I think Ubuntu is good for people that are just getting used to Linux, after using Windows, or OS X. (if they have internet access).

---

### Post by JNowka on 2006-05-14
make sure you use "sudo" in front of the command and put your password in when it asks.  Its a security feature linux has so people you don't want doing stuff to your comp can't. So type.

sudo apt-get install basic-essentials

---

### Post by jtibau on 2006-05-15
[QUOTE=Addison13248]Every time I time type "sudo apt-get install build essentials" into terminal it gives me "W: couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breazy/univers Packages" and so on and on. I know how to compile, just never done it on Ubuntu.[/QUOTE]
The problem here is that it is trying to install the build-essentials package that is supposed to be at that address. However since you have no internet connection it can't reach it.
What you can do is remove all the repositories, besides the one in the installation CD. To do this (in a simple way), open Synaptic, go to Settings>>Repositories. Then remove everyone besides the one that says cdrom something.
Afterwards you can install build-essentials using synaptics.

---

### Post by jtibau on 2006-05-15
By the way, what exactly is it you donwloaded, tar files or deb files?

---

### Post by Addison13248 on 2006-05-16
I downloaded .deb files

---

