---
title: "How Do I Install Something I've Downloaded?"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by Kernel Sanders on 2006-04-21
Hi everyone, 

I'm just playing with the Kubuntu Live CD (To learn more about it) and I have downloaded Firefox to my Desktop (Is it called a desktop?) 

Now my only problem is installing the thing :)

I have no clue what to do next! :cry:

If I double click it, up comes a program called "ark" and there are lots of files in it?

Help! :cry:

Sorry for being a Linux Idiot :cry:

John :)

---

### Post by gingermark on 2006-04-21
[This page](http://www.psychocats.net/ubuntu/installingsoftware.php) highlights the various ways of installing software in Kubuntu.

I haven't used the LiveCD myself, but assuming you have a partition the disc can write to, I would assume it's much the same. The file you've downloaded contains the code needed to compile the program yourself I would think. The page I linked to explains the nice and easy way to install binary packages in Kubuntu.

---

### Post by mostwanted on 2006-04-21
What kind of package is it. That is *pretty* important if you want to know how to install it.... =/

---

### Post by gingermark on 2006-04-21
What I'm saying is that I'd install firefox via apt-get/Adept.

You've downloaded the source packages I think, which is what you'd use if you wanted to compile the program yourself.

On a Kubuntu system installed on a hard drive you would open up Konsole and type:

sudo apt-get update
sudo apt-get install firefox

and that would be it.

As I said though, not too sure how this would work with the Live CD.

EDIT: Sorry, mostwanted, thought you were the OP there.... :)

---

### Post by Kernel Sanders on 2006-04-21
[QUOTE=mostwanted]What kind of package is it. That is *pretty* important if you want to know how to install it.... =/[/QUOTE]

Hey, I have downloaded firefox-1.5.0.2.tar.gz and I want to know how to install that.

I think I have extracted it to the home folder..........

So I have a folder called firefox in the home folder, with a bunch of files and folders in it.

How do I install that?

Thanks for your help!

John :)

---

### Post by mostwanted on 2006-04-21
[QUOTE=*John*]Hey, I have downloaded firefox-1.5.0.2.tar.gz and I want to know how to install that.

I think I have extracted it to the home folder..........

So I have a folder called firefox in the home folder, with a bunch of files and folders in it.

How do I install that?

Thanks for your help!

John :)[/QUOTE]

usually a tar.gz is a source package so you'd go to the correct folder you've untared it to and run

```
./configure
```

if there is such a script and then

```
sudo make install
```

But Firefox is a bit different, it's already compiled. If you go to the correct folder there is a file named "firefox" or similar. You just run that.

---

### Post by towsonu2003 on 2006-04-21
Are you running Kubuntu 6.06 (Dapper) or 5.10 (Breezy)? 6.06 is for testing, 5.10 is the one for normal use. I am asking you this bc left to your message, it says you're using "Dapper". Following are two probabilities: either you have 6.06 or you have 5.10:

if you have 6.06 LiveCD (or install CD for that matter), you don't need firefox from mozilla. Its new version is already there in 6.06. I believe its icon is on the desktop? 

There is a chance firefox isn't installed on a **K**ubuntu 6.06 (they use "Konqueror" instead?). Open a terminal (under Applications>Accessories) and type 
```

sudo apt-get install firefox

```any errors: please copy and paste here. 

if you have 5.10, its firefox is old. If this is a LiveCD (reboot, and all changes will be lost, so no need to do boring stuff), go to this page [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) to the section called "Installing Firefox Quick and Dirty". 

If you decide to install Ubuntu 5.10 and want to install firefox there, go to the same page and use the section "Installing firefox from mozilla.org". Don't use "Installing Firefox Quick and Dirty" in your installed Kubuntu.

---

### Post by clemm on 2006-05-14
This is great link, Thanks for the info. This stuff is hard to find when your new and dont really know where to look. Thanks

---

### Post by aysiu on 2006-05-14
[This script](http://www.psychocats.net/ubuntu/firefox) automates the Wiki instructions.

---

### Post by towsonu2003 on 2006-05-14
[QUOTE=clemm]This is great link, Thanks for the info. This stuff is hard to find when your new and dont really know where to look. Thanks[/QUOTE]
yea, I experience the same thing everytime I try out a new distro...

---

### Post by jtibau on 2006-05-14
Every (I think) tarball with an installable program has an INSTALL file. It is a simple text file, pretty much the same for all programs. I should guide you through compiling and installing the program you want.

The steps generally are: (in CLI by the way)
*untar the file
*cd to the folder
./configure
*become root
make
make install

however apt-get makes your life much easier, you just say what you want installed on your system by typing:
sudo apt-get install package
It will donwload, unpack, configure and install the desired program, no hassel to you. Plus it keeps record of what it installs so you can easily remove it later.

---

### Post by user1397 on 2006-05-14
[quote=aysiu][This script]("http://www.psychocats.net/ubuntu/firefox") automates the Wiki instructions.[/quote]
aysiu:
does that script install all of the plugins for firefox or are you supposed to already have gotten those?

---

### Post by aysiu on 2006-05-14
[QUOTE=erik1397]aysiu:
does that script install all of the plugins for firefox or are you supposed to already have gotten those?[/QUOTE] It does what the Wiki instructions do: install the newest version of Firefox (1.5.0.3). Both the script and the Wiki will link to whatever plugins you've already installed.

If you want a script that does more, try [Automatix](http://www.ubuntuforums.org/showthread.php?t=138405). I believe Automatix installs 1.5.0.1, but you can probably check for updates once you launch Firefox.

---

### Post by towsonu2003 on 2006-05-14
[QUOTE=jtibau]Every (I think) tarball with an installable program has an INSTALL file. It is a simple text file, pretty much the same for all programs. I should guide you through compiling and installing the program you want.

The steps generally are: (in CLI by the way)
*untar the file
*cd to the folder
./configure
*become root
make
make install

however apt-get makes your life much easier, you just say what you want installed on your system by typing:
sudo apt-get install package
It will donwload, unpack, configure and install the desired program, no hassel to you. Plus it keeps record of what it installs so you can easily remove it later.[/QUOTE]
Contrary to my expectations, I found that compiling isn't as hard as ubuntu makes it look like... The problem with compiling in ubuntu is that it doesn't ship most of the libraries, tools, and headers you need to compile. 

I was trying Zenwalk (based on Slackware, 1CD), and to my surprise, I compiled wvstreams (needed to google a bit), wvdial (needed to google a bit), liferea, and firestarter in about 20 minutes (most of it being spent by cpu). Maybe gentoo isn't as hard as I think either :PpP

Weird stuff :)

---

### Post by user1397 on 2006-05-14
[quote=aysiu]It does what the Wiki instructions do: install the newest version of Firefox (1.5.0.3). Both the script and the Wiki will link to whatever plugins you've already installed.

If you want a script that does more, try [Automatix]("http://www.ubuntuforums.org/showthread.php?t=138405"). I believe Automatix installs 1.5.0.1, but you can probably check for updates once you launch Firefox.[/quote]
oh ok thanks:)
and btw, automatix installs 1.5.0.3 now

---

### Post by Perfect Storm on 2006-05-14
[QUOTE=towsonu2003]Contrary to my expectations, I found that compiling isn't as hard as ubuntu makes it look like... The problem with compiling in ubuntu is that it doesn't ship most of the libraries, tools, and headers you need to compile. 

I was trying Zenwalk (based on Slackware, 1CD), and to my surprise, I compiled wvstreams (needed to google a bit), wvdial (needed to google a bit), liferea, and firestarter in about 20 minutes (most of it being spent by cpu). Maybe gentoo isn't as hard as I think either :PpP

Weird stuff :)[/QUOTE]

Well, if you have internet connection and it works when you turn ubuntu on, there's no problem compiling stuff in ubuntu. Done that a billion times now.

---

### Post by nalmeth on 2006-05-14
install and use [checkinstall]("http://asic-linux.com.mx/%7Eizto/checkinstall/") for when compiling apps

it's "better" ( :) ) than merely 'make install'


sudo apt-get install checkinstall

check website for instructions, it's simple, will allow you to properly uninstall the program if you need to.

---

