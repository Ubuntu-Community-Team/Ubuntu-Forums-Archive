---
title: "C Compiler...just hear me out?"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by rivera82falcon on 2006-08-02
I've been reading the same thing over about using the apt-get for build essentials and also using the synaptic package manger also. This is my situation...I have a laptop that does NOT have internet access at this time. What, or where, can I download a file for the build essentials (thru another pc of course) so I can have the compilier on the laptop?

---

### Post by fourchannel on 2006-08-02
At [this]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=build-essential&searchon=names&subword=1&version=all&release=all") website you can download the build essential that goes to your version of ubuntu. Once it brings up the page you need to download each package separately. Reason being that "build-essential" is not actually a package, but a list of packages to make a complete compiling system.

once you have download all the packages it lists use this command to install them.

```
sudo dpkg -i package.deb
``` 
infact you could download all the packages to one directory and then run this instead.

```
sudo dpkg -i *.deb
```

---

### Post by rivera82falcon on 2006-08-02
Wow, That's exactly what I need! Thank you VERY much fourchannel. It's a pain because to install one package, you need another package, and so on so forth, but it's okay, I'll continue doing so til I have all the required downloads. Thanks! =)

---

### Post by IYY on 2006-08-02
I was under the impression that the build tools were on the CD, just not installed by default. So, just finding them in Synaptic or using apt-get should work without an internet connection.

---

### Post by catlett on 2006-08-02
> **IYY said:**
> I was under the impression that the build tools were on the CD, just not installed by default. So, just finding them in Synaptic or using apt-get should work without an internet connection.

This is correct. If you put the installation cd in the computer and install from synaptic or if you apt-get, the package will be retrieved from the cd.
You can get the repositories on cd 2 ways. 1 cost $35 and the other requires access to the internet and a dvd burner. [http://www.ubuntuforums.org/showthread.php?t=224956&highlight=ubuntu+dvd](http://www.ubuntuforums.org/showthread.php?t=224956&highlight=ubuntu+dvd)
Then you can add the packages without an internet connection. You just install from the dvds.

---

### Post by fourchannel on 2006-08-03
> **catlett said:**
> This is correct. If you put the installation cd in the computer and install from synaptic or if you apt-get, the package will be retrieved from the cd.
You can get the repositories on cd 2 ways. 1 cost $35 and the other requires access to the internet and a dvd burner. [http://www.ubuntuforums.org/showthread.php?t=224956&highlight=ubuntu+dvd](http://www.ubuntuforums.org/showthread.php?t=224956&highlight=ubuntu+dvd)
Then you can add the packages without an internet connection. You just install from the dvds.


Even better. It happens time after time... A problem comes along that I think I know exactly how to fix, and I end up learning even more. LOL. I love these forums. =D

---

