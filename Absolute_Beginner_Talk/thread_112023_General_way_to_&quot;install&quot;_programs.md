---
title: "General way to &quot;install&quot; programs"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by alsolo on 2006-01-03
hello everybody,
i installed ubuntu on my computer and now i'm trying to have some programs working on it. I was trying to install bittorrent and i downloaded it, but, coming from windows i dunno how to install it. there are no readmes and nothing else but .py or .pyc files. i dunno what to do with those. Please help me 
thanx in advance 
Silvio

PS
Generally speaking, in which form linux programs come? i mean, it is a self extracting file or it is a compressed archive and you just ungzip it and it's fine or you have to ungzip and compile it, or...whatever?
thx

---

### Post by phido on 2006-01-03
[quote=alsolo]hello everybody,
i installed ubuntu on my computer and now i'm trying to have some programs working on it. I was trying to install bittorrent and i downloaded it, but, coming from windows i dunno how to install it. there are no readmes and nothing else but .py or .pyc files. i dunno what to do with those. Please help me [/quote] bittorrent is as deb package available, run Synaptic (package manager) and search for it or install it with [I]sudo apt-get install bittorrent
[/I][quote=alsolo]
Generally speaking, in which form linux programs come? i mean, it is a self extracting file or it is a compressed archive and you just ungzip it and it's fine or you have to ungzip and compile it, or...whatever?
thx[/quote] Most programs are available as *.deb packages (for ubuntu) in an official or unofficial repository, the other way is to compile it from source to an debian-package and then install it.

h2h

---

### Post by Peter76 on 2006-01-03
Hello, to install software in Ubuntu, the best way is to see if u can find it in Synaptic ( It's in the System menu in the title bar on top of your screen) Go through the manual, it's pretty simple and here you can find most of the software you want. Softwar for linux comes in different flavours; as Ubuntu is Debian ( another distro ) based, the easiest way to install software is through .deb files, but this is most of the times handled by Synaptic. You can also do it through the command line, but I don't think you're looking for that now. Another packaging format is .rpm which is used by RedHat and others. There is a commandline tool to convert from .rpm to .deb: alien, but you have to install this. The last resort is to compile yourself; you download the sources and the compile them, look through the forums how to do this if you want this. It reqquire a bit of tweaking most of the time. Good luck

---

### Post by 23meg on 2006-01-03
Take a look at [this]("http://www.psychocats.net/linux/installingsoftware.php").

---

### Post by phido on 2006-01-03
Compiling from source should be done like this for debian/ubuntu:
*apt-get install dh-make fakeroot build-essential*
then 
* tar -xvzf obscure-1.0.tar.gz*
*cd obscure-1.0*
if theres no debian folder in there
*dh_make*
and now u can make a deb package with
[I]fakeroot debian/rules binary
[/I]and install it with
[I]dpkg -i ../obscure-1.0.deb

justmy2cents
[/I]

---

### Post by Aphorism on 2006-01-03
Until you are fully aware of the implications of installing software and the security issues therein, I *strongly* recommend that you use the package manager built into Ubuntu.  It is very feature rich and robust.  Further, the software that plays by the best rules is all in there...  Try to work within it until you can't.

---

