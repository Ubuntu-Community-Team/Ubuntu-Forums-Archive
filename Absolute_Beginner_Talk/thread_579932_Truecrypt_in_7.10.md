---
title: "Truecrypt in 7.10"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Kilarin on 2007-10-18
I just royally hosed myself.   Spent all morning downloading and installing Ubuntu 7.10.  Install went flawlessly.  EXCEPT!
I keep all of my user data on a truecrypt encrypted drive.  I booted into Ubuntu 7.10, attempted to mount my truecrypt drive, and, well, truecrypt runs fine when it asks for my password, but when it actually tries to mount the drive I get::

FATAL: Module truecrypt not found
Failed to load TrueCrypt kernal module.

YIKES!!!!   I should have considered that before I upgraded!   A bit of research shows that truecrypt is NOT available from the ubuntu downloads, and there isn't an ubuntu 7.10 version on truecrypt.org yet.    oh oh.   I tried uninstalling and re-installing the 7.04 version of truecrypt, just it case, but as I expected, that did nothing.

Obviously I should have waited until truecrypt had a 7.10 version out before upgrading, but its too late for that.  SO, how can I get truecrypt up and running under 7.10???

EDIT: I think I may have found a solution on the truecrypt forums:
[http://forums.truecrypt.org/viewtopic.php?t=7847](http://forums.truecrypt.org/viewtopic.php?t=7847)
This details how to compile truecrypt from the sources so that it will install on 7.10.

---

### Post by jagolis on 2007-10-18
When upgrading to 7.04 a while ago, I had to patch and compile from source too. I never did get around to uninstalling and then using the .deb. Same thing will probably happen this time heh. Thanks for the link.

---

### Post by timetunnel on 2007-10-18
You can compile truecrypt yourself. I just did that and it worked without any problems. Taken from  the German ubuntu wiki at [http://wiki.ubuntuusers.de/TrueCrypt/Installation](http://wiki.ubuntuusers.de/TrueCrypt/Installation) :

Install the following packages:
[LIST]
[*]linux-source
[*]dmsetup
[*]build-essential
[/LIST]

If you upgraded from Feisty, make sure to remove the older Truecrypt version!

Open a terminal and unpack the linux source (which is not done by the "linux-source" package, it just downloads a compressed tar.bz2 file of the sources):
```
cd /usr/src
sudo tar xvjf linux-source-2.6.22.tar.bz2 
sudo ln -s linux-source-2.6.22 linux
sudo cp /boot/config-$(uname -r) /usr/src/linux/.config

```

Then download the source code from the Truecrypt homepage, unzip the file and copy it to /usr/src. After that you should have a directory like "/usr/src/truecrypt4.3a-source-code" (or similar).

In a terminal, go into the "Linux" subdirectoy of the Truecrypt sources and compile it:
```
cd /usr/src/truecrypt-4.3-source-code/Linux
sudo ./build.sh
sudo ./install.sh
```

You will be asked about 2 or 3 questions. I had one asking me if something like a "dev/mapper" should be created. I said no. I answered the other questions by just pressing the RETURN key.

Compiling might take some time, so be patient.

That' it. It works for me (I did a fresh install of Gutsy and had used my truecrypt volumes on Feisty before). 

Remember that if you get a truecrypt deb file later on and want to install it you will have to remove the files of the self-compiled truecrypt beforehand.

Hope it helps
Jens

---

### Post by n3tfury on 2007-10-18
> **timetunnel said:**
> You can compile truecrypt yourself. I just did that and it worked without any problems. Taken from  the German ubuntu wiki at [http://wiki.ubuntuusers.de/TrueCrypt/Installation](http://wiki.ubuntuusers.de/TrueCrypt/Installation) :

Install the packages following packages:
[LIST]
[*]linux-source
[*]dmsetup
[*]build-essential
[/LIST]

If you upgraded from Feisty, make sure to remove the older Truecrypt version!

Open a terminal and unpack the linux source (which is not done by the "linux-source" package, it just download a compressed tar.bz2 file of the sources):
```
cd /usr/src
sudo tar xvjf linux-source-2.6.22.tar.bz2 
sudo ln -s linux-source-2.6.22 linux
sudo cp /boot/config-$(uname -r) /usr/src/linux/.config

```

Then download the source code from the Truecrypt homepage, unzip the file and copy it to /usr/src. After that you should have a directory like "/usr/src/truecrypt4.3a-source-code" (or similar).

In a terminal, go into the "Linux" subdirectoy of the Truecrypt sources and compile it:
```
cd /usr/src/truecrypt-4.3-source-code/Linux
sudo ./build.sh
sudo ./install.sh
```

You will be asked about 2 or 3 questions. I had one asking me if something like a "dev/mapper" should be created. I said no. I answered the other questions by just pressing the RETURN key.

Compiling might take some time, so be patient.

That' it. It works for me (I did a fresh install of Gutsy and had used my truecrypt volumes on Feisty before). 

Remember that if you get a truecrypt deb file later on and want to install it you will have to remove the files of the self-compiled truecrypt beforehand.

Hope it helps
Jens

awesome post, thank you.

---

### Post by Kilarin on 2007-10-18
Thanks everyone for the help, I FINALLY got it compiled.  
Would have been a LOT easier of Truecrypt had been included in the Ubuntu Universe.

Is there any particular reason why it is not?  I understand that the license Truecrypt uses is VERY close to GPL.

---

### Post by Hobo2021 on 2007-10-19
> **timetunnel said:**
> You can compile truecrypt yourself. I just did that and it worked without any problems. Taken from  the German ubuntu wiki at [http://wiki.ubuntuusers.de/TrueCrypt/Installation](http://wiki.ubuntuusers.de/TrueCrypt/Installation) :

Remember that if you get a truecrypt deb file later on and want to install it you will have to remove the files of the self-compiled truecrypt beforehand.

Hope it helps
Jens

Thank you for your guide, worked for me.

One deliciously succulent noobish question though, what is the preferred/graceful method of properly purging all the self-compiled truecrypt files later?

---

### Post by tmcmurph on 2007-10-28
slow firefox - IPv6 dns = fast firefox

truecrypt + compile = working TC

now on to getting my DVD working again.

Thanks a bunch. I use truecrypt a lot because it runs under windoze (at work they insist :( and I run ubuntu at home.

I will have to make a list of the stuff I've installed and check to see if it will work before I do the next upgrade. Good thing to keep an eye on.

Thanks again for the pointers in getting this one resolved.

---

