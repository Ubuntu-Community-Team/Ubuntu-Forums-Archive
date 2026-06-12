---
title: "An idiotic question about installing apps"
date: 2005-06-25
forum: Absolute Beginner Talk
---

### Post by H_Roark on 2005-06-25
I've been trying to install an update to Firefox for over an hour now, and none of the "instructions" I've found are coherent or work.  Is there someplace I can find a step-by-step, I-am-idiot explanation of how to install applications on this OS?

---

### Post by TristanMike on 2005-06-26
Hi, what update are you trying to install and what exactly is not happening?
TristanMike

---

### Post by Xian on 2005-06-26
_How-To's_

1. [Apt-Get How-To](https://wiki.ubuntu.com//AptGetHowTo)
2. [Synaptic How-To](https://wiki.ubuntu.com//SynapticHowto)
2. [Managing Packages](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-install)

Enable the [Extra Repos](http://ubuntuguide.org/#extrarepositories).
Then update any package (if update is available) in either a terminal or in Synaptic.
Use the methods listed in the How-To's.

---

### Post by H_Roark on 2005-06-26
I'm trying to install Firefox 1.0.4.  I've downloaded and extracted it, but once I run the extractor, it seems to vanish.  Clicking on the 'open' button in the archive window (where the extractor opens) brings up a list of files, none of which do anything.  In a terminal window, typing the commands provided in FF's relase notes gets me a message that the directory does not exist.  Using the tar command provided in the same place also gets me the same result.  I finally tracked down some of the files in the tmp directory, but running firefox install from /tmp brings up the webpage for some company that writes installation scripts.  No help there, and it's certainly not installing anything.

I was warned that software installs were the great bugaboo with Linux, but I had no idea...  This reminds me of learning to use CP/M back in the early days, where you needed some sort of Codex to find the commands to run the machine.

---

### Post by SGC on 2005-06-26
Installing software using synaptic is even easier than install them using windows, but first you need to do this first, open this file **/etc/apt/sources.list** and replace it's contents with the following:
```

deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe
deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted
deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe
deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

Then open synaptic from **System -> Adminstration -> synaptic package manager** and hit the **reload** button. After that you can search for any program you want and synaptic will download it and install it for you.

---

### Post by Xian on 2005-06-26
[QUOTE=H_Roark]I'm trying to install Firefox 1.0.4.  I've downloaded and extracted it, but once I run the extractor, it seems to vanish.[/QUOTE]
That FF version is available and ready for use in Synaptic or Apt if you will as instructed enable the extra repos. The How-To's that were posted will assist you in installing packages and maintaining your system.

---

### Post by H_Roark on 2005-06-26
[QUOTE=SGC]Installing software using synaptic is even easier than install them using windows, but first you need to do this first, open this file **/etc/apt/sources.list** and replace it's contents with the following:
```

deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe
deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted
deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe
deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

Then open synaptic from **System -> Adminstration -> synaptic package manager** and hit the **reload** button. After that you can search for any program you want and synaptic will download it and install it for you.[/QUOTE]


Fair enough, but how do I get to that file?  In the root terminal, it tells me either 'permission denied' or claims that the file doesn't exist.  Sorry for my idiocy, btw.

---

### Post by TristanMike on 2005-06-26
Hi, I had this problem and poofyhairguy helped me step by step, check it out,

[http://www.ubuntuforums.org/showthread.php?t=41806](http://www.ubuntuforums.org/showthread.php?t=41806)

Hope this helps
TristanMike
PS, it starts at comment #5

---

### Post by H_Roark on 2005-06-26
I've got it figured out now.  For anyone else having this issue, I used the code above by using nautilus to navigate to the folder listed, and doing a cut and paste.

Thanks to all.

---

