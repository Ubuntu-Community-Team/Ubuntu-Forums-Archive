---
title: "Can't enable restricted driver: ATI Radeon XPress 200m"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by jmusso on 2007-07-17
Okay so I'm running a fairly fresh install of Feisty Fawn on my Compaq Pressario V5000 with the ATI Radeon Xpress 200m card. When I go to System > Administration > Restricted Drivers and try to enable the ATI driver or whatever, i click on it, it comes up with a message saying do you want to enable it? I click yes, and then it does nothing. The words go gray for a second or two, and then it is unchecked. I can't enable it. Why?

---

### Post by hamburglar6 on 2007-07-17
You might want to try using tseliots envy script to install the binary ATI drivers automatically.  If you're interested download the script from his homepage here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) 

and just follow the instructions there.

---

### Post by swisscow on 2007-07-17
Short answer - because it's an ATI card. I have an X300 and the restricted drivers do the same. You do have choices though.

You can visit the ati website nad download the official drivers
You canuse synaptic to install the fglrx drives supplied with Ubuntu (search for fglrx)
You can do nothing.

If everything works fine - do nothing. Some applications such as googlee arth won't work though so use the official or the ubuntu drivers. But then this causes problems if you want to use beryl/compiz - there are a million threads on this.

Whatever you do, research first.

---

### Post by Rocket2DMn on 2007-07-17
You will first need to enable the restricted repositories in /etc/apt/sources.list and remove the # from in front of the restricted lines, they should be near the top.
```
gksudo gedit /etc/apt/sources.list
```
Then you can install the fglrx drivers
```
sudo apt-get install xorg-driver-fglrx
```
You can then reconfigure your xserver, selecting fgrlx as your driver
```
sudo dpkg-reconfigure xserver-xorg
```
Please take your time in the configuration so you get it right.  You can select the correct resolutions for your monitor while you're at it using TAB to move around and SPACEBAR to select.
Good luck.

---

### Post by jmusso on 2007-07-17
Okay, I tried the last advice. This is what happened...
```
joe@joe:~$ gksudo gedit /etc/apt/sources.list
(gedit:12805): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```

When sources.list opened up, it was completely empty. Nothing in it.

---

### Post by stchman on 2007-07-17
> **jmusso said:**
> Okay so I'm running a fairly fresh install of Feisty Fawn on my Compaq Pressario V5000 with the ATI Radeon Xpress 200m card. When I go to System > Administration > Restricted Drivers and try to enable the ATI driver or whatever, i click on it, it comes up with a message saying do you want to enable it? I click yes, and then it does nothing. The words go gray for a second or two, and then it is unchecked. I can't enable it. Why?

My laptop did the same thing.  I have hte same card.  Try it again a few times.  The restricted driver does work.

---

### Post by Rocket2DMn on 2007-07-17
Apparently it is a [bug]("https://launchpad.net/ubuntu/+source/gksu/+bug/23917")
You can read about gksudo [here]("http://www.psychocats.net/ubuntu/graphicalsudo")

The file was empty eh?  In terminal type
```
cat /etc/apt/sources.list
``` and post the ouput here.

---

### Post by jmusso on 2007-07-17
```

joe@joe:~$ cat etc/apt/sources.list
cat: etc/apt/sources.list: No such file or directory

```

---

### Post by Rocket2DMn on 2007-07-17
Shoot my bad, you need a / before etc (the / is the root of the filesystem).  That was a mistype.
```
cat /etc/apt/sources.list
```
Sorry.

---

### Post by jmusso on 2007-07-17
it didn't make much of a difference...
```
joe@joe:~$ cat /etc/apt/sources.list
cat: /etc/apt/sources.list: No such file or directory

```

what the hell? i feel like such a noob...

---

### Post by Rocket2DMn on 2007-07-17
Well that's rather funny.  I would give you my sources.list file except I'm not in front of my Ubuntu computer.  Let's give this a try:
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
You should be able to just accept the default settings - it will give you a minimal sources.list file.  Copy and paste what it gives you into the blank sources.list file in /etc/apt/ using the gksudo command above.
Then set the correct permissions on it:
```
sudo chmod 644 /etc/apt/sources.list
```

---

### Post by jmusso on 2007-07-17
ok... so i'm just a bit confused at one part. i copied the sources.list from where you said and saved it, but when you say to remove the #s from in front of the restricted parts, where exactly do you mean? once again sorry for my extreme noobishness...
```

# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu feisty main restricted 
deb http://us.archive.ubuntu.com/ubuntu feisty-updates main restricted
deb http://security.ubuntu.com/ubuntu feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu feisty universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse

```

---

### Post by jmusso on 2007-07-17
When i try to install fglx this is what happened... thats why i'm asking the question above...
```
joe@joe:~$ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xorg-driver-fglrx
joe@joe:~$ 

```

---

### Post by Rocket2DMn on 2007-07-17
I was having you removing the # in front of
> deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty main restricted 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
but they are already removed.  Don't worry about that now, it's good.

Now, for the driver install, give this a go: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
You may need to follow the directions for Edgy if the ones for Feisty don't work.
I'm going on lunch now, I'll be back in an hour or so, let me know how it goes.
Good luck!

---

### Post by jmusso on 2007-07-18
I think I got it to work... we'll see when I get Beryl running, if I get it running... Thanks for all the help. I had Feisty running great on this laptop about a week ago, with Beryl running awesome and everything, no problems (except some dumb things with the wireless internet, but forget that) and then I left the install cd in the drive, and some of my friends tried to use my computer, accidentally reformatting it... so now I have to go through all of this again. It's really quite a pain. Once again, thanks!

---

