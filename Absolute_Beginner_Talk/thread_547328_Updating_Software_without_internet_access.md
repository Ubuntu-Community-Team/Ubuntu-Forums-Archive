---
title: "Updating Software without internet access?"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by rookworm on 2007-09-09
OK, this  is gonna sound like i'm living in the stone age, but my comp at home does not have internet access. I have installed Ubuntu, but I would like to add some more software packages. I have access to some internet connected Windows machines (on which I can d/l stuff) elsewhere, and I have a USB flash key. I could just d/l some of the packages, but some of them (like TeX, compiling tools, etc.) have lots of dependencies, so it would be a preferable to have an automated solution.

I was wondering if anybody has a good solution for installing new software in this way.

Thanks!!

---

### Post by compiledkernel on 2007-09-09
One day I asked Chuck Norris this question and he bestowed upon me this link. 

[https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto)

Should help.

---

### Post by chrome307 on 2007-09-10
Maybe this could work?

On the Windows PC you could run VMWare and install Ubuntu. 

As this has internet access, download/install AptOnCD. 

In this instance save it as a DEB file which you can copy over to your Flash memory stick.  Just run the DEB file to install on your Ubuntu OS.

Once the program is installed download all the updates that you need and any new packages that you required.

Then start up AptOnCD and select the option 'Create AptOnCD' this will allow you to download the packages onto an ISO that you can burn. When you select the packages - choose the option 'Metapackage' this simply means that any application that you copy will have all the necessary files that might be needed from other packages.

At the end of the program it will allow you to burn this as an ISO or simply copy it over to your flash memory stick.

Now on the Ubuntu PC at home, transfer over AptOnCD (deb file) and then install it.

Once installed you can then start the program up and choose where to download/install all the packages eg

[IMG]http://i16.tinypic.com/6akf90n.jpg[/IMG]

To install the packages you need to go to Synaptic Package Manager and then type in the name of the package, this will then install the application that has been transferred over.

Goodluck :)

---

### Post by rookworm on 2007-09-12
Awesome. Thanks guys!

---

