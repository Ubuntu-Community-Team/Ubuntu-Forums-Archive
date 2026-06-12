---
title: "Cant install programs"
date: 2005-09-21
forum: Absolute Beginner Talk
---

### Post by DoeRayMe on 2005-09-21
i have loads of trouble installing tar.gz files, can someone tell me how to install stuff please, as i dont know

thanks

if someone knows how to install peng, i would be very happy aswell

---

### Post by aysiu on 2005-09-21
[QUOTE=DoeRayMe]i have loads of trouble installing tar.gz files, can someone tell me how to install stuff please, as i dont know[/quote] You use .tar.gz files only if you want to install from source. Most software you'll install using Synaptic. For a graphical tutorial on Synaptic [go here](http://www.psychocats.net/essays/winuxinstall.php)

> 
if someone knows how to install peng, i would be very happy aswell You need extra repositories for that:

[http://www.frankandjacq.com/ubuntuguide/5.04/index.html#extrarepositories](http://www.frankandjacq.com/ubuntuguide/5.04/index.html#extrarepositories)

Are you using Hoary (5.04) or Breezy (5.10)? If you're using Breezy, you'll need to change some of those extra repositories to Breezy ones.

---

### Post by KingBahamut on 2005-09-21
gunzip nameoftarball.tar.gz

tar -xvf nameoftarball.tar

cd /directorycreatedbytarball

If it exists run 
./configure

satisfy any dependencies that fail in this process. 

Once this is done, 

Edit your makefile to make sure your paths are all correct. 

the run 

make 

then run

sudo make install 

or what you can do is let apt-get create a deb for you by -- apt-get checkinstall

---

### Post by DoeRayMe on 2005-09-21
[QUOTE=aysiu] You need extra repositories for that:

[http://www.frankandjacq.com/ubuntuguide/5.04/index.html#extrarepositories](http://www.frankandjacq.com/ubuntuguide/5.04/index.html#extrarepositories)

Are you using Hoary (5.04) or Breezy (5.10)? If you're using Breezy, you'll need to change some of those extra repositories to Breezy ones.[/QUOTE]
 how?

when i cant get on aol, because i need to install PengAOL before i can connect

btw 5.04

---

### Post by aysiu on 2005-09-21
[QUOTE=DoeRayMe]how?

when i cant get on aol, because i need to install PengAOL before i can connect

btw 5.04[/QUOTE] How did you get the .tar.gz? Did you download it off another computer? When you downloaded it, was there something available ending in a .deb or .rpm extension (as opposed to .tar.gz)?

---

### Post by DoeRayMe on 2005-09-21
[QUOTE=aysiu]How did you get the .tar.gz? Did you download it off another computer? When you downloaded it, was there something available ending in a .deb or .rpm extension (as opposed to .tar.gz)?[/QUOTE]
 Yeah im on my girlfriends computer getting the stuff needed, only .tar.gz files, no .deb or .rpm

what now?

---

### Post by aysiu on 2005-09-21
[QUOTE=DoeRayMe]Yeah im on my girlfriends computer getting the stuff needed, only .tar.gz files, no .deb or .rpm

what now?[/QUOTE] Okay. I found the .debs. Ordinarily, if you use Synaptic, it resolves dependencies for you, but you're going to have to install the dependencies first.

[This page](http://packages.ubuntu.com/hoary/net/penggy) lists all the dependencies and has links to their .debs and the penggy .deb.

Once you have a .deb, you should download it to your desktop.
Then, type in this code

```
cd Desktop
sudo dpkg -i debconf.deb

```

Of course, if you're installing another package, you'd change the code appropriately, to packagename.deb.

---

### Post by DoeRayMe on 2005-09-21
[QUOTE=aysiu]Okay. I found the .debs. Ordinarily, if you use Synaptic, it resolves dependencies for you, but you're going to have to install the dependencies first.

[This page](http://packages.ubuntu.com/hoary/net/penggy) lists all the dependencies and has links to their .debs and the penggy .deb.

Once you have a .deb, you should download it to your desktop.
Then, type in this code

```
cd Desktop
sudo dpkg -i debconf.deb

```

Of course, if you're installing another package, you'd change the code appropriately, to packagename.deb.[/QUOTE]
 thanks i have it all installed, i just need to find out where my modem is located

its not /dev/modem

where could i find that out?

---

