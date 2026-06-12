---
title: "Help with libdvdcss2"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by Danyl on 2006-06-16
Hi all

First of all, I am an EXTREME newbie when it comes to Linux and Ubuntu. While I can use the terminal if someone shows me what to type, I have no REAL understanding of it. So please keep that in mind....

I've just installed Ubuntu for my Athlon64 (love this distribution by the way, I really can't wait to get everything installed and cranking!) and have followed the directions here **[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)** to install DVD capability for totem-xine.

But I'm having problems still playing encrypted DVD's.

I've used the Synaptic Package Manager to install debhelper, build-essential and fakeroot (the Package Manager shows these in green so I'm assuming they're installed?) and then typed this into the terminal:

**sudo /usr/share/doc/libdvdread3/examples/install-css.sh**

I get a message from the terminal saying:

[B]"No binary deb available.  Will try to build and install it.
You need to have debhelper, dpkg-dev and fakeroot installed.
If not, interrupt now, install them and rerun this script.

This is higly experimental, look out for what happens below.
If you want to stop, interrupt now (control-c), else press
return to proceed"[/B]

I hit return and it  seems to go off and install the libdvdcss2.

But then I open up totem-xine to test it out and it still says:

**"The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?"**

What am I doing wrong?!

Please help me out! Thanks everyone!

---

### Post by jeroen2 on 2006-06-16
There are alternate methods for getting libdvdcss2, although I don't know if they're effective for amd64..... Try at your own risk (it won't screw up your system though so don't worry).

You can use automatix to install libdvdcss. Look for installation guide at:

[http://ubuntuforums.org/forumdisplay.php?f=77](http://ubuntuforums.org/forumdisplay.php?f=77)


Furthermore, Christian Marrilat offers it in his repository. Add the following line to your sources.list:

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main


You might also want to check out the w32codecs package at the above.

I hope this helps. Let me know if I need to clarify things or if you run into additional problems.


~Jeroen

---

### Post by briguy on 2006-06-16
The marillat repositories is probably the easiest solution - but it is important to remove or comment it out of your sources.list before you start installing other programs or upgrading - some of the other binaries from this repo may not play well with Ubuntu.

---

### Post by givré on 2006-06-16
If you are still afraid by all that, there is an easyer solution:
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)
It's a bit like automatix (less possibility), but it is made for really newby.

---

### Post by Danyl on 2006-06-16
Sorry to sound like a dumb newb but when you say add Marrilat to my soures list, do I do that in the Synaptic Package Manager? If so how?

---

### Post by Danyl on 2006-06-16
givre thanks for that! That is very handy. I downloaded it and tried to run it. But I get an error message when I try and update saying:

**The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences**.

This happens for all the boxes I tick too.:-( 

?????

---

### Post by jeroen2 on 2006-06-16
[QUOTE=Danyl]Sorry to sound like a dumb newb but when you say add Marrilat to my soures list, do I do that in the Synaptic Package Manager? If so how?[/QUOTE]

I don't know how to add Marillat with Synaptic, because I use Kubuntu and thus the adept package manager...


However, I'm pretty sure you can edit your sources.list directly under ubuntu with the following command:

sudo gedit /etc/apt/source.list

Mine looks like this (don't be confused by al the Kubuntu stuff, just think ubuntu instead ;) :


------------------------------------------------------------------------
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main 
deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted 


deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) breezy main restricted 
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) breezy main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) breezy-updates main restricted 
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) breezy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) breezy universe 
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) breezy universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse 
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe 
------------------------------------------------------------------------


~J

---

### Post by jeroen2 on 2006-06-16
After you install libdvdcss and maybe w32codecs, comment the marillat line like this:

## deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main

To disable it. Like briguy mentioned, you don't want to update with Marillat enabled.


~J

---

### Post by Danyl on 2006-06-16
Thanks Jeroen2, updated the sources list as directed with the ftp address for Marillat but I get the following error:

[B]E: Type 'ftp://ftp.nerim.net/debian-marillat/' is not known on line 34 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.[/B]

I'm still confused....sorry.....:-(

---

### Post by Danyl on 2006-06-16
[QUOTE=jeroen2]After you install libdvdcss and maybe w32codecs, comment the marillat line like this:

## deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main

To disable it. Like briguy mentioned, you don't want to update with Marillat enabled.


~J[/QUOTE]

Sorry I don't understand this. 

I like the idea of using EasyUbuntu as it appears nice and easy. It just doesn't want to work. :(

---

### Post by givré on 2006-06-16
which pakage did you try to install?

---

### Post by givré on 2006-06-16
also to have a good source.lst, select in system, repository list

---

### Post by jeroen2 on 2006-06-16
[QUOTE=Danyl]Thanks Jeroen2, updated the sources list as directed with the ftp address for Marillat but I get the following error:

[B]E: Type 'ftp://ftp.nerim.net/debian-marillat/' is not known on line 34 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.[/B]

I'm still confused....sorry.....:-([/QUOTE]


Did you add the entire line to sources.list?:

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main


The errorcode looks like you forgot to add the word deb. Don't just type the ftp adres, type the entire line I show above.


Also, I don't want to start an automatix <-> easybuntu warthread, but if easybuntu doesn't work for you, try automatix, it never failed me....


~Jeroen

---

### Post by givré on 2006-06-16
Okay, after trying to understand what could be your problem, it seems that your source.lst is totaly broken.
Put here the result of ```
gedit /etc/apt/source.lst
```
so we can fix your poblem

---

### Post by jeroen2 on 2006-06-16
Danyl

If you want me to walk you through the problem in a chat: I'm in #ubuntu on freenode irc, or you can send me a private message and I'll give you my msn...


~Jeroen

---

### Post by Danyl on 2006-06-16
[QUOTE=jeroen2]Did you add the entire line to sources.list?:

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main


The errorcode looks like you forgot to add the word deb. Don't just type the ftp adres, type the entire line I show above.


Also, I don't want to start an automatix <-> easybuntu warthread, but if easybuntu doesn't work for you, try automatix, it never failed me....


~Jeroen[/QUOTE]

Yep, definitely have the word 'deb' in there. Will have to get back to you guys soon. Stay tuned!

---

### Post by TwistesdTexan on 2006-06-16
If you start easyubuntu again and only check the first 3 boxes on the first page it will load the codecs you need.

---

### Post by racecat on 2006-06-16
Does anyone know of a good reason not to download and install the deb file from freshmeat.net? It's easy and it worked fine on my new Dapper install.

Bill

---

### Post by aysiu on 2006-06-16
Paste these two commands and you're good: ```
wget -c http://packages.freecontrib.org/ubuntu/plf/pool/dapper/i386/free/libdvdcss2/libdvdcss2_1.2.9-1plf3_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-1plf3_i386.deb
```

---

### Post by Danyl on 2006-06-18
Success!!!

I don't know which one of the solutions you all provided, but I shut down the machine last night and turned it on again today and oi-la! It works! I'm now able to watch an encoded DVD!!!!

Thanks for all your help guys/gals! No doubt I'll be on here again soon looking to get everything set up to my ideal setup (ie to completely replace my windows OS).

I'm so happy! Thanks everyone!

---

### Post by Danyl on 2006-06-18
Ooops.

How do I now fix my sources.list file?

When I try and use my Synaptic Package Manager now, it says:

[B]E: Type 'ftp://ftp.nerim.net/debian-marillat/' is not known on line 34 in source list /etc/apt/sources.list
E: Unable to lock the list directory[/B]

How do I fix this??!!!

---

### Post by aysiu on 2006-06-18
Close Synaptic.

In the terminal, paste these commands: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo nano /etc/apt/sources.list
``` Delete the nerim lines. Add these two lines instead: ```
deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
``` Then save (control-x), confirm (y), and exit (Enter).

Launch Synaptic again. After you click Reload in Synaptic, you should see *libdvdcss2* in there.

---

### Post by Danyl on 2006-06-18
Hey hey! It worked! Great, thanks aysiu!!!!

---

