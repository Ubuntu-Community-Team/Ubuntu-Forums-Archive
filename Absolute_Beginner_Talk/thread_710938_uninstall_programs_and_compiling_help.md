---
title: "uninstall programs and compiling help"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by onthefence on 2008-02-29
So, this question is more general than I would like but I would like to know if there is a general way to uninstall a program that you manually install. Is it just a matter of deleting the folders that were unzipped from the tarball. Specifically I'm dealing with MySQL.

Also, I tried to follow a guide for installing some software, but it involved compiling and even with the instruction it was over my head. Are there any good guides to understanding what compiling really is? I mean I kind of understand the concept, but it seems that there are some standard steps involved and commands involved that are part of any compiling that if you don't understand/know, then guides can be somewhat nebulous. Specifically I am dealing with PHP here.

FYI, I understand these can be installed via Synaptic, but to modify them for my needs, they need to be modified and recompiled. 

Any help is appreciated...

---

### Post by talsemgeest on 2008-02-29
Ok I will put it in the easiest way I can.

When you compile, you change the human-readable code into computer-readable code.

To do this, you need to cd into the directory where the source code is.
E.g. If you extarcted the tar.gz to your desktop, you would type ```
cd ~/Desktop/(folder-name-here)
``` Obviously replacing (folder-name-here) with the name of the folder.

Then you have to configure the software by typing: ```
./configure
```
Then to compile the software you type ```
make
```

Then to install it to your system, type ```
sudo make install
```
Type your password and you are done!

But as for uninstalling it, I have never really looked into it, but deleting the folders should do the trick

Hope this is what you were after :)

---

### Post by talsemgeest on 2008-02-29
Oh, and there is also a pretty good guide on compiling in the latest full circle magazine (ubuntu, kubuntu, xubuntu...) You can download it from here: [http://fullcirclemagazine.org/issue-10/](http://fullcirclemagazine.org/issue-10/)

---

### Post by HermanAB on 2008-02-29
make uninstall

---

### Post by onthefence on 2008-03-02
make uninstall, geez, why does Ubuntu have to be so logical,

ok, so those steps make sense, except for the ./configure part, how do you know how to configure the program? Is it different for each program? Are there notes with the download that explain the configuration options for the program?

---

### Post by spiderbatdad on 2008-03-02
Using checkinstall to add the program to your package manager is often preferred to "sudo make uninstall," which may not always work.[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) Though it can have issue to; it's good to have choices.

---

### Post by talsemgeest on 2008-03-03
> **onthefence said:**
> make uninstall, geez, why does Ubuntu have to be so logical,

ok, so those steps make sense, except for the ./configure part, how do you know how to configure the program? Is it different for each program? Are there notes with the download that explain the configuration options for the program?
You don't. It does it all for you. Just type that command, let it do its stuff, and then continue...

---

### Post by onthefence on 2008-03-04
Thanks, a lot of good information, I think i got it, let me try it out...

---

### Post by talsemgeest on 2008-03-04
Cool, I hope it goes well

---

### Post by hyper_ch on 2008-03-04
why do you want to compile mysql and php from the source?

---

### Post by onthefence on 2008-03-05
following a guide, 
according to the guide(book written circa 2006) this was necessary to get certain functionality that was inserted into .conf and .ini files in the guide and/or security. 
although i tried following a different guide calling it LAMP installation which worked fine, everything is up and running, now i'm just looking for a good mysql frontend to work with.

i think the guide was just outdated. it seems almost a rule in the software business that anything you read in print is already outdated by the time it hits the shelves.

but the root of the thread was how does one compile because I'm sure I'm going to run into other situations where I might have to.

---

