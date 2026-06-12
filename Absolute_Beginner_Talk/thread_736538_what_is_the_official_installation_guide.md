---
title: "what is the official installation guide?"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by foolish one on 2008-03-26
What is the basic formula for installing a package manually?

---

### Post by SunnyRabbiera on 2008-03-26
well even though its not official there is this:
[here]("http://monkeyblog.org/ubuntu/installing/")
It is a great guide for beginners.

---

### Post by Laser Dude on 2008-03-26
From a .deb file?  I think just double clicking it should work.

---

### Post by iansane on 2008-03-26
by manually do you mean from a source tar.gz ?

If so, right click and extract here, then open terminal and cd to the new extracted directory.

There should be a readme file with directions.

Some have a config file, some have a make file, some have .sh scripts that have to be made executable before running them. They are all different depending on how they were made, so a good one will have a good understandable readme file with directions

For .deb files just click and let the fileroller do it for you

You will probably need to install build-essentials from synaptic and maybe some other packages for it to compile correctly. If the readme is not there or you can't understand it cause it sucks, ask for specific directions for a specific package here on the forums

That's my official guide

---

### Post by SunnyRabbiera on 2008-03-26
> **Laser Dude said:**
> From a .deb file?  I think just double clicking it should work.

normally, depending if it needs other files.

---

### Post by spiderbatdad on 2008-03-26
Your best option is using "sudo apt-get install package" or opening synaptic package manager and selecting the package by name. If the package is not in the repositories, first make sure you have universe and mutilverse repos enabled. If downloading the package is your only option, look for a .deb package. These will install (with needed dependencies) by clicking on the package from your desktop. You can then trash the package if you want. Such packages are also easily removed by the Gdebi installer. If you must install a tar package, right click on the package, and select "extract here," the read any documentation included ie, Read Me and Install files. 

Follow this guide, and use "sudo checkinstall" OR "checkinstall--install=no" (this last example will create a .deb you can click to install, and possibly help to avoid a permissions error in your root directory)  instead of "sudo make install," if possible. The reason is that checkinstall will add the package to synaptic as a .deb, and give you an easy means of removal. Checkinstall does not always work, and some programs come with uninstallers included.
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by foolish one on 2008-03-26
thanks guys that helps a ton. I was worried about the tar.gz packages because it doesn't always work.

---

### Post by SunnyRabbiera on 2008-03-26
yeh the tar packages are usually for compiling, most of what you need is in the repositories though.
Is there anything in particular you wanted to know about?

---

### Post by foolish one on 2008-03-27
thanks that's all.

---

