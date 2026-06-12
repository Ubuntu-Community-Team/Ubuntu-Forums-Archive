---
title: "enable flash and java in Gutsy 64?"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by limberlegs on 2007-10-14
OK, so maybe this is a stupid question, and for that I apologize.  How do I install flash and java plugins for my Gutsy 64 bit install?  In reading through some old posts, it appears that this wasn't possible a few months ago, but perhaps things have changed?

Thanks!

---

### Post by scwinn on 2007-10-14
Say I guess I am not as much a newbie as I used to be....

Start Synaptic (package manager) and do a search on the word "restricted". One package will be "ubuntu-restricted-extras". This will download Java, Flash, the MP3 and video codecs.

Enjoy!

---

### Post by limberlegs on 2007-10-14
Ooops!  I should have been more specific.  I have those packages installed.  What I meant was, how do I get the firefox plugins for those?

Sorry for the confusion.

---

### Post by williamwade on 2007-10-14
Open terminal

```
sudo apt-get install flashplugin-nonfree
```

this installs flash. You may have to agree to an EULE

> sudo apt-get install sun-java5-plugin

this installs java. as before,  You may have to agree to an EULE

---

### Post by limberlegs on 2007-10-14
Hey, thanks!  I have the flash plugin working just fine.  Java didn't work, unfortunately.  Here's the response I got when I typed the above code into terminal:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java5-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java5-plugin has no installation candidate

---

### Post by ruibernardo on 2007-10-15
I was going to say to you to enable the multiverse repository to install it and to install the latest version of it (sun-java6-plugin), but then I saw that the Java plugin is only available for i386 (it seems that Sun doesn't make them for 64 bits), so it isn't available in your Ubuntu version.

To install Java plugin for FireFox and other 32 bit plugins in amd64, take a look here: [https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins)

I don't have a 64 bit CPU, so I just hope it helps you somehow.

Cheers.

EDIT: That link should work for you (it's the official documentation), but you can find more tips, questions and answers about your specific version of Ubuntu here on this forum: [Ubuntu Forums]("http://ubuntuforums.org/index.php")  	> [The Ubuntu Forum Community]("http://ubuntuforums.org/forumdisplay.php?f=130")   	> [Main Support Categories]("http://ubuntuforums.org/forumdisplay.php?f=173") > [x86 64-bit Users]("http://ubuntuforums.org/forumdisplay.php?f=134")

---

### Post by FredB on 2007-10-15
There is no Sun Java plugin in 64 bits for now.

Flash ? sudo apt-get install flashplugin-nonfree.

This is the only thing I miss with ubuntu AMD64. And I am using AMD64 version since Edgy Eft...

---

