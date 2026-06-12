---
title: "Where do installed packages go?"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by Pasty-Flawss on 2008-04-18
Hi,
I just installed a package. I was wondering how to access it's contents and where they are?
Btw, package name was linux-backports-modules-2.6.22-14-generic_2.6.22-14.10_i386

Thanks in advance :)

---

### Post by oedha on 2008-04-18
how did you install it ?
this wont show in the menu...since this file somekind of supporting package
if you ask for the *.deb location...it is on /var/cache/apt/archives/

---

### Post by Pasty-Flawss on 2008-04-18
I downloaded it off [www.packages.ubuntu.com](www.packages.ubuntu.com) and then i installed the package. But where are its contents?

---

### Post by Pasty-Flawss on 2008-04-18
come on guys its like a one word answer :/

---

### Post by kpkeerthi on 2008-04-18
[http://ubuntuforums.org/showpost.php?p=4738819&postcount=12](http://ubuntuforums.org/showpost.php?p=4738819&postcount=12)

---

### Post by frankos44 on 2008-04-18
> **Pasty-Flawss said:**
> I downloaded it off [www.packages.ubuntu.com](www.packages.ubuntu.com) and then i installed the package. But where are its contents?

The url you specified does not exist  when I clicked it. 

If you know the name of the package you can find it using "find". Type "man find"  for more info on how to use find. Here is an example: 

$ sudo find / -type f -name FILENAME

Once you have found the package make a note of its name and path. Type its name into the terminal and if that works create a "Document launcher" for it by right clicking the desktop and selecting "Create launcher"

Hope this helps.

---

### Post by frankos44 on 2008-04-18
> **kpkeerthi said:**
> [http://ubuntuforums.org/showpost.php?p=4738819&postcount=12](http://ubuntuforums.org/showpost.php?p=4738819&postcount=12)

That is a better solution but it only works with packages installed using the package manager..

---

### Post by Pasty-Flawss on 2008-04-18
it still doesn't say the directory..

---

### Post by hyper_ch on 2008-04-18
The individual files go where they belong to on the linux filesystem hierarchy

See this for more details:  [http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

---

### Post by george9233 on 2008-04-18
In the Synaptic Package Manager, just select an installed package, then right click and select "properties", then go to the "Installed Files" tab. I think this should be an easy way.

---

### Post by erginemr on 2008-04-18
> **Pasty-Flawss said:**
> Hi,
I just installed a package. I was wondering how to access it's contents and where they are?
Btw, package name was linux-backports-modules-2.6.22-14-generic_2.6.22-14.10_i386

Thanks in advance :)

This package is normally needed to solve the "Sound is gone all of a sudden" problem in Gutsy mostly with the HDA Intel audio cards. The package in question installs kernel modules as mentioned before and are activated automatically right away (or at next reboot). There is realy nothing for you to run there.

---

