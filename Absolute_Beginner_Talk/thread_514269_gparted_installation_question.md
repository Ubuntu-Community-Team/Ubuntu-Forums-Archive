---
title: "gparted installation question"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by themis on 2007-07-31
PLeaze pleaze help me with the gparted installation.

I've downloaded a .tar.bz2 file that has gparted,placed it in /home and been trying to install it.

Can you help me with this?

I've read this, [http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm) , but nothings comes out.

I am under prssure to do this,because I am obliged to make a partition and install windows on it,
and now I don;t even have an internet connection where the pc is!

thanks*!

---

### Post by ayenack on 2007-07-31
open terminal and type this.

sudo apt-get install gparted

My mistake I did not finish reading the post. No internet. Ok do this. Put the GParted tar on your desktop and double left click it this should open ded package installer and click install package that's it. Simple.

---

### Post by themis on 2007-07-31
I did it,and it tries to connect to gr.archive.ubuntu.com,
which is not available because I have no internet connection.

I have downloaded the fileso I want to install it manually.
Is this the only way?
thanks anyway

---

### Post by eggdeng on 2007-07-31
> I am obliged to make a partition and install windows on it

If you install windows after ubuntu, it will overwrite your MBR and you will not be able to get into ubuntu.So, before you do anything, download the Super Grub Disc ISO [http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")and burn it (as ISO) so as to be able to restore your MBR.

---

### Post by thefoolisme on 2007-07-31
Did you try this (from the link you posted)?

Download the file into the directory of choice. In this example we choose the /tmp directory. Then follow the instructions :

cd /tmp
#unpack the tarball:
tar -xjf gparted-x.y.tar.bz2
cd gparted-x.y/
./configure --prefix=/usr
make
su -
make install
# that's all. Problems may arise if you haven't the right dependencies

Following the build, change into the directory and run gparted from a terminal :

cd /tmp/gparted-x.y/src
./gparted
And now the fun begins 

Of course, you could have to change /tmp to home since that's where you stored it.  My only other concern is that there may be dependencies which would need to be installed.  Without an internet connection, I'm not sure how you would get those dependencies.

---

### Post by ugm6hr on 2007-07-31
Isn't the GParted .deb on the Ubuntu LiveCD?

If not: [http://packages.ubuntu.com/feisty/gnome/gparted](http://packages.ubuntu.com/feisty/gnome/gparted)

If you select the correct architecture - and download the .deb, you should be able to just double-click it.

---

### Post by Mwelsh on 2008-03-12
I am having a similar problem, mostly with dependencies. I downloaded probably 20 or so .deb files to try to cover all the dependencies, but one of them will not install because it would overwrite a previously installed one. I could uninstall it, but then I will lose many apps that require it.

Was a solution ever found for this?

Thanks

---

### Post by Oldsoldier2003 on 2008-03-12
> **Mwelsh said:**
> I am having a similar problem, mostly with dependencies. I downloaded probably 20 or so .deb files to try to cover all the dependencies, but one of them will not install because it would overwrite a previously installed one. I could uninstall it, but then I will lose many apps that require it.

Was a solution ever found for this?

Thanks

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install gparted
```

---

### Post by jan quark on 2008-03-12
it is only a partial solution to use the gparted live cd

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

