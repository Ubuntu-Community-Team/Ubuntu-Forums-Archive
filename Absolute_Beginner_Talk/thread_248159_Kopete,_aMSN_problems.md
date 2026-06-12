---
title: "Kopete, aMSN problems"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by Jeeks on 2006-08-31
Ok, here's the deal. I have installed Ubuntu Dapper on my laptop after a struggle with my CDRom but finally it was installed and it is working as good as it can be.

As a beginner, problems are there. Thanks for friends I have, they are helping me solve these. Now I got stuck with a problem that no one is able to guess what it is.

On Kopete and on aMSN, I can receive webcam but I cannot send my webcam. My webcam is working fine and it has been tested, but I can't seem to be able to send image to my contacts. It just hangs there without anything happening.

On both clients I face the same problem but with file sending and receiving. I seem to be able to receive files without any hassle but when it comes to sending, it just hangs there saying transfer established but without sending any bit.

How can one fix this problem?

Any help is appreciated :D

---

### Post by PPAAUULL on 2006-08-31
Well MSN has just updated to Windows Live messenger which could have an effect on the way these proccesses work. I don't know for sure but I would guess that maybe Windows live messenger (if indeed that is what the other person has) does not like it and hangs it. That would be my best guess.

---

### Post by Dinerty on 2006-08-31
> **Jeeks said:**
> Ok, here's the deal. I have installed Ubuntu Dapper on my laptop after a struggle with my CDRom but finally it was installed and it is working as good as it can be.

As a beginner, problems are there. Thanks for friends I have, they are helping me solve these. Now I got stuck with a problem that no one is able to guess what it is.

On Kopete and on aMSN, I can receive webcam but I cannot send my webcam. My webcam is working fine and it has been tested, but I can't seem to be able to send image to my contacts. It just hangs there without anything happening.

On both clients I face the same problem but with file sending and receiving. I seem to be able to receive files without any hassle but when it comes to sending, it just hangs there saying transfer established but without sending any bit.

How can one fix this problem?

Any help is appreciated :D

Bare with me on this, I had the same problem myself on kopete (I Don't use aMSN), I found I had to install one of the plugins called "NetMetting", once this was succesfully installed my Webcam could be sent to others.

This may not and probaly isnt the main cause for your problem not working on aMSN as well, but I found it works now on Kopete for doing this

---

### Post by Jeeks on 2006-08-31
> **Dinerty said:**
> Bare with me on this, I had the same problem myself on kopete (I Don't use aMSN), I found I had to install one of the plugins called "NetMetting", once this was succesfully installed my Webcam could be sent to others.

This may not and probaly isnt the main cause for your problem not working on aMSN as well, but I found it works now on Kopete for doing this


I am willing to give it a try, where and how can i install this plugin.

@PPAAUULL, I am trying to send and receive with people on Linux.

---

### Post by Dinerty on 2006-08-31
> **Jeeks said:**
> I am willing to give it a try, where and how can i install this plugin.

@PPAAUULL, I am trying to send and receive with people on Linux.

In kopete do this:

Settings > Configure Plugins > Netmeeting

Tick "Netmeeting" hit "Apply" then"ok" download the plugin from [http://www.kde-apps.org/content/show.php?content=10395](http://www.kde-apps.org/content/show.php?content=10395)

Then right click the file and say "Extract here"

Now fire up the terminal and head to where you download the file to (e.g desktop for me)

```
cd Desktop
```

then

```
cd konference-0.1
```

then

```
./configure
```

then

```
make
```

then

```
make install
```

then kopete webcam worked for me

---

### Post by toipot on 2006-08-31
Sorry to hijack this thread a little ;) 

Just wondering which webcams you use?
Ive been after one for a while, id like one thats (k)ubuntu compatible.

---

### Post by Dinerty on 2006-09-01
> **toipot said:**
> Sorry to hijack this thread a little ;) 

Just wondering which webcams you use?
Ive been after one for a while, id like one thats (k)ubuntu compatible.

A £6 labtec one [http://www.labtec.com/index.cfm/gear/details/EUR/EN,crid=30,contentid=731](http://www.labtec.com/index.cfm/gear/details/EUR/EN,crid=30,contentid=731)

---

### Post by Jeeks on 2006-09-02
Dinerty, your last two commands don't make anything :S

I think I have a bug also, in Kopete I seem to send each message with a different colour.

---

### Post by Dinerty on 2006-09-03
> **Jeeks said:**
> Dinerty, your last two commands don't make anything :S

I think I have a bug also, in Kopete I seem to send each message with a different colour.

did you recieve any errors when installing "like permission denied"?, sometimes you need use sudo before the command "sudo make install".

---

### Post by Jeeks on 2006-09-03
> **Dinerty said:**
> did you recieve any errors when installing "like permission denied"?, sometimes you need use sudo before the command "sudo make install".

No, I got command not found.

---

### Post by Dinerty on 2006-09-03
> **Jeeks said:**
> No, I got command not found.

```
sudo apt-get install build-essential
```

or if you wish to go Synaptic Package Manager and install it from there

---

### Post by Jeeks on 2006-09-11
My webcam worked for a couple of days, I was so happy and I thanked you (Dinerty) a lot but then one day it stopped working.

The same day it stopped working my Skyoe stopped working as well.

---

### Post by keyo on 2006-10-26
I got this
```
configure: WARNING: libjpeg not found. disable JPEG support.
checking for perl... /usr/bin/perl
checking for Qt... configure: error: Qt (>= Qt 3.2) (headers and libraries) not found. Please check your installation!
```

---

### Post by Azzco on 2006-12-05
Sorry to bump in here.
But I'm having the same problem when doing ./configure

I gave up on webcam and forgot about it months ago but when I saw this post I had to try.

Could the problem have anything to do with running Edgy?

---

### Post by javierfh on 2007-01-26
Hello,
i saw this post and seems to be quite interesting, but when following it no much progress, see below.

> **Dinerty said:**
> In kopete do this:

Settings > Configure Plugins > Netmeeting

Tick "Netmeeting" hit "Apply" then"ok" download the plugin from [http://www.kde-apps.org/content/show.php?content=10395](http://www.kde-apps.org/content/show.php?content=10395)

Then right click the file and say "Extract here"

Now fire up the terminal and head to where you download the file to (e.g desktop for me)

```
cd Desktop
```

then

```
cd konference-0.1
```

then

```
./configure
```

then

```
make
```

then

```
make install
```

then kopete webcam worked for me


is this working at all? I mean when i try to run ./configure i get the following error 

> 
javi@javi-desktop:~/Desktop/konference-0.1$ sudo ./configure 
Password:
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
javi@javi-desktop:~/Desktop/konference-0.1$ sudo make
make: *** No targets specified and no makefile found.  Stop.




Any idea how to progress one more step? that sounded promissing the installation of that plugin but..well...seems that i cant install it.

Any help would be more than welcomed.

Javi

---

