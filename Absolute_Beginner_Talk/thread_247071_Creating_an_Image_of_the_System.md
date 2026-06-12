---
title: "Creating an Image of the System"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by hakre on 2006-08-30
Hi Folks, I have installed Debian on an Old Computer and I want to check out Ubuntulite on it now. But before I boot & install Ubuntu I'd like to create an Image of the existing system.

I have a shell on the box (x is not properly installed) and network (lan). Because there is not much space on the system it might be an option to store this image on a winxp box within the network.

Since I'm new with linux I know that all these cool tasks can be done with available software but I don't know how and I need help on doing so.

---

### Post by mejy on 2006-08-30
Edit:  Sorry, double post.

---

### Post by mejy on 2006-08-30
> **hakre said:**
> Hi Folks, I have installed Debian on an Old Computer and I want to check out Ubuntulite on it now. But before I boot & install Ubuntu I'd like to create an Image of the existing system.

I have a shell on the box (x is not properly installed) and network (lan). Because there is not much space on the system it might be an option to store this image on a winxp box within the network.

Since I'm new with linux I know that all these cool tasks can be done with available software but I don't know how and I need help on doing so.

Although it's not technically the same as an image (in that it's not at the file system level), you can simply archive the full contents of the file system, by using

tar -cvf backup.tar /

or if space is an issue, you can compress it:


tar -czvf backup.tgz /

But remember, untarring that would effectively replace your new Ubuntu system with Debian.  A better choice would be to archive your home directory, which will backup all your user preferences andfiles.  To do this, replace the '/' in the commands above with '/home/*username*/'.

To extract one of these files, replace the '-c' with '-x'.

---

### Post by hakre on 2006-08-30
I shoud have mention that the current debian system is the install only, I do not have any other files on it, so I will not apply the Image on the ubuntu system.

How do I tell tar to put the tar/tgz file onto a network location? Can I map a windows share easily?

/edit:
I just learned about [Partimage](http://www.partimage.org/) and it's said it supports network. I try to install it now.

---

### Post by mejy on 2006-08-30
> **hakre said:**
> I shoud have mention that the current debian system is the install only, I do not have any other files on it, so I will not apply the Image on the ubuntu system.

How do I tell tar to put the tar/tgz file onto a network location? Can I map a windows share easily?

First off, I cannot guarentee that simply overwriting your Ubuntu system with the archive would result in a Debian install.  If there are any files on the Ubuntu install that are not included in the archive, they will remain there and could break the system, and if the partition layout changes at all it almolst definately will.

I'd personally recommend just doing a fresh Debian install if you have no important personal files, but if you want to try this first I'll go into a little more detail.  The tar/tgz file will be created in the directory you executed the command, by default your home directory.  To move it onto the network, you can simply use a graphical method to drag it across from your home folder to the network folder (assuming you can mount the network share, which is a different issue entirely).

Also, when untaring the archive you'll have to put 'sudo' infront of the tar command (so long as your untarring on Ubuntu, anyway).

---

### Post by hakre on 2006-08-30
hi mejy, thanks for your efforts, but i have not made my point clear enough, sothat you point to the wrong direction:

First off: I have a Debian install and want to create an Image of it. Then the box will be erased. Then Ubuntu will be installed (fresh). The Setup of Ubuntu is totally unrelated to the setup of Debian. Debian was a test. Ubuntu will be a test.
Second off: The Image will be created from the current Debian System and because I do not have much space on the machine, I need to put the Image somewhere to another Computer _while_ creating the image.

---

### Post by mejy on 2006-08-30
> **hakre said:**
> hi mejy, thanks for your efforts, but i have not made my point clear enough, sothat you point to the wrong direction:

First off: I have a Debian install and want to create an Image of it. Then the box will be erased. Then Ubuntu will be installed (fresh). The Setup of Ubuntu is totally unrelated to the setup of Debian. Debian was a test. Ubuntu will be a test.
Second off: The Image will be created from the current Debian System and because I do not have much space on the machine, I need to put the Image somewhere to another Computer _while_ creating the image.

If you don't have space on the machine, the best option would be to look into NFS - if you have another linux box, you can create an NFS share and mount it like a normal directory, and then cd to that directory before starting the tar.  If you can't use NFS, things get tricky if you want to mount a samba (windows) share to a directory, which is something I've never done before.

---

### Post by hakre on 2006-08-30
> **mejy said:**
> If you don't have space on the machine, the best option would be to look into NFS - if you have another linux box, you can create an NFS share and mount it like a normal directory, and then cd to that directory before starting the tar.  If you can't use NFS, things get tricky if you want to mount a samba (windows) share to a directory, which is something I've never done before.
Indeed this all looks quite tricky. I created myself the Linux System Rescue CD which contains Partimage, but it looks like that this nice thingy is not compatible with a 32MB system. Anyway I think I figure that out by a install on the running system.

Your Idea with an NFS share is really cool, since I've got no additional Linux Box (next to the wlan router) I checkout if there is an Option to have NFS on Windows as well - hehe.

Setting up a Samba something to Mount a samba share is another Idea I came across, I think this is well documented in the net.

---

### Post by Marsolin on 2006-08-30
Did Partimage work for you? If not, some other options are [Mondo]("http://linuxappfinder.com/package/mondo"), [Ghost for Linux]("http://linuxappfinder.com/package/g4l"), and [g4u]("http://linuxappfinder.com/package/g4u").

---

### Post by hakre on 2006-08-30
> **Marsolin said:**
> Did Partimage work for you? If not, some other options are [Mondo]("http://linuxappfinder.com/package/mondo"), [Ghost for Linux]("http://linuxappfinder.com/package/g4l"), and [g4u]("http://linuxappfinder.com/package/g4u").

Thanks for pointing out, unfourtionatly until now I was not able to start partimage physically. as I wrote the rescue boot cd did not work out, so I currently try to install partimage by hand. So far I was not able to handle an installation with apt-get and wonder why:

1.) a package called partimage exists with debian, even if it's unstable:
[http://packages.debian.org/unstable/admin/partimage](http://packages.debian.org/unstable/admin/partimage)

2.) apt-get can install unstable packages, I learned that the following command should do the job:
apt-get install -t unstable partimage
source: [http://www.newsforge.com/article.pl?sid=04/12/02/1710208](http://www.newsforge.com/article.pl?sid=04/12/02/1710208)
It did not

3.) I was trying around with aptitude (I finally found the name of the proggy!) , but I'm not able to let aptitude display unstable packages.

So I'm a little stuck here. Compiling the source of partimage might be an option finally, the website is quite well I hope, it lists all the dependencies hopefully. That would be my first compile anyway ;)

EDIT:
4.) a little *vi /etc/apt/sources.list* and adding unstabel behind an active source.
5.) starting aptitude again and updating sources then (the message box even displays an hint for doing so)
6.) searching for partimage does now work quite properly and I am able to install it.

I'll check partimage now...
(and then I'll check your ghost suggestions...)

EDIT:
the installation of partimage takes its time and is making progress (it's a computer labled "speedline 586" :-D ), while I was taking a walk, the complete C-Library or sort of is updated (maybe this is why it is in the unstable section), but seems to work as intended. I'm just hit how well this is all working out.

EDIT:
Yeah! I could start partimage. But hehe, there is a message displayed an I can only cancel:
> Warning: You have devfs enabled but not mounted. You have to do it to continue. You can also boot with non-devfs kernel if you have one.
well, hmm, I have an Idea what this message is trying to tell me but I have no Idea where to get a non-devfs kernel or how to deactivate that. Looks like checking for the linux ghost now.... (anyway in that time (day#2 is nearby over), I could have just installed ubuntulite ;) )

---

