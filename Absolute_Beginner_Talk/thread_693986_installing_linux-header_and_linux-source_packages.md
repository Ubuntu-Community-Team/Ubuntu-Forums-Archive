---
title: "installing linux-header and linux-source packages"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by Buckleywood on 2008-02-11
Hi, this is my first post...new to Linux and Ubuntu. I have set up a dual boot with XP and Gutsy. I have a prooblem with my USB wifi adapter, which I have researched and found a possible solution  ( on the networking and wireless forum at "ndiswrapperless >= WUSB54GSv2/GCv2 / WL169gE / USR5421 / USR5420 / F5D7051"). 

I am going to give it a go, it's a fairly full guide to what to do. But I am confused about installing the correct linux-header and -source files. I think the header files are loaded (looking in Synaptic) but can't see the -source file. Have gone to the online archive, but am lost with all the dependencies - do I need to download all the dependency packages for the file ("linux-source_2.6.22.14.21_all.deb")?

Am I making this too complicated?!

I have a working internet connection through Windows XP, so can get what I need.

Help in understanding how this works would be much appreciated!

---

### Post by y-lee on 2008-02-11
I don't know about your wireless problem but in synaptic click settings and then repos and check all the ones with source you think you need and you should be able to download the source files.

If you want or need help with your my USB wifi adapter here you need to post more details and perhaps a link to the guide you are trying to use. I have like 0 experience with wifi issues but someone here may be able to help you

EDIT: BTW source files and headers may have dev added to the end for development

---

### Post by Buckleywood on 2008-02-11
Thanks. It's not the wifi problem I need help with (yet!) - and the forum thread I included has details, but here is the specific bit I am not sure about ..... 

" For the first step you will need internet access. You need the linux-headers and linux-source packages for your kernel.
You can use uname -r to find out what kernel version you have, and then get the corresponding packages. Also make
sure you have make and gcc (and all their dependencies) installed. You can download the .debs for all these from
packages.ubuntu.com and install them using dpkg -i <deb file>"

just not sure what packages I need, whether I need to download all the dependent packages as well....

Hope this helps

PS Can't download using Synaptic cos of the wifi issue - as I understand it, Synaptic would resolve the dependencies automatically...... so limited to picking up .deb files individually from the archive using my working Windows connection.

---

### Post by y-lee on 2008-02-11
I think make is part of build-essentials you can find it and gcc in synaptic package manager. Install them there and it will take care of all the dependencies for you. 


what is the output of 

```
uname -r
```

Sorry i missed the *Can't download using Synaptic* part.

---

### Post by Buckleywood on 2008-02-11
Thanks for the help so far!

Here is what I have:

uname -r returns the kernel as *2.6.22-14-generic*

According to Synaptic, I have the following header files installed:

[I]linux-headers-2.6.22-14
linux-headers-2.6.22-14-generic
linux-headers-generic[/I]

as well as:

[I]make (3.81-3build1)
gcc (4:4.4.1.2-9ubuntu2)[/I]

... which would seem to leave the linux-source file(s).

I have downloaded  a file called *"linux-source_2.6.22.14.21_all.deb*" from the gutsy archive, but it indicated that there was another dependent file; which in turn indicated three more..... at which point I thought I should ask what I needed to do!

Again, hope this helps.

---

### Post by y-lee on 2008-02-11
> ust not sure what packages I need, whether I need to download all the dependent packages as well....

Hope this helps

PS Can't download using Synaptic cos of the wifi issue - as I understand it, Synaptic would resolve the dependencies automatically...... so limited to picking up .deb files individually from the archive using my working Windows connection.

Yes you need all dependent packages! For gcc see [Package: gcc-4.2]("http://packages.ubuntu.com/gutsy/devel/gcc-4.2"), for build-essentials [Package: build-essential ]("http://packages.ubuntu.com/gutsy/devel/build-essential") for a list of all deps on Gusty.

---

### Post by y-lee on 2008-02-11
[Source package: linux-source-2.6.22 ]("http://packages.ubuntu.com/gutsy/source/linux-source-2.6.22") list deps there I think lol

PS download every think you think you need. you seem to be  doing ok researching it and if ya install more than you need no harm if ya have the HD space and that shouldn't be an issue.

---

### Post by Buckleywood on 2008-02-11
OK thanks I will check these out in the morning (!) although I assume that my installation will have taken care of the make and gcc dependencies anyway?

Back on it tomorrow.


Edit: thanks for the reference for the source package as well -will check it out tomorrow but I expect I will have more obvious questions as a result, LOL.

---

### Post by Buckleywood on 2008-02-16
Thanks for your help on this, I have downloaded the source file and all dependencies were satisfied so hopefully that is OK!

Now to see if it works....

Regards

---

