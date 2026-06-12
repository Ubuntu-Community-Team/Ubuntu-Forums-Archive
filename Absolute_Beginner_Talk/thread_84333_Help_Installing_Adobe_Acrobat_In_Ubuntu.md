---
title: "Help Installing Adobe Acrobat In Ubuntu"
date: 2005-10-30
forum: Absolute Beginner Talk
---

### Post by foska on 2005-10-30
I need some help installing Adobe Acrobat Reader. I have downloaded a 'tar' archive from Adobe's website (AdbeRdr701_linux_enu.tar.gz) and have extracted all the files to another folder.  I tried running the install script but I have had no success.  Can soemone help me with this?

Thanks

Foska

---

### Post by aysiu on 2005-10-30
Sure.

1. Delete the .tar.gz you downloaded.
2. Follow the instructions [here](http://www.psychocats.net/linux/sources.php)
3. Then open up a terminal and type in ```
sudo apt-get update
sudo apt-get install acroread
```

You're done. If you don't understand what just happened, read this:
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by thinhlegolas on 2005-10-30
[QUOTE=foska]I need some help installing Adobe Acrobat Reader. I have downloaded a 'tar' archive from Adobe's website (AdbeRdr701_linux_enu.tar.gz) and have extracted all the files to another folder.  I tried running the install script but I have had no success.  Can soemone help me with this?

Thanks

Foska[/QUOTE]

I had exactly the same problem... what I did  was to delete Adobe in /usr/local... then

sudo apt-get update
sudo apt-get install acroread

This will install Acrobat Reader 5. However during the installation process, it installed some other packages needed to run Reader 5

Now uninstall acroread in Synaptic, and install Acrobat Reader 7 again... it should run :)

---

### Post by aysiu on 2005-10-30
[QUOTE=thinhlegolas]I had exactly the same problem... what I did  was to delete Adobe in /usr/local... then

sudo apt-get update
sudo apt-get install acroread

This will install Acrobat Reader 5.[/QUOTE] My Synaptic's showing Acrobeat Reader 7, not 5.

---

### Post by foska on 2005-10-31
This is the what I get

waynep@ubuntu:~$ sudo apt-get update
Reading package lists... Done
waynep@ubuntu:~$ sudo apt-get install acroread
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package acroread
waynep@ubuntu:~$

What's wrong?

---

### Post by linbetwin on 2005-10-31
Click "Add Applications" in "Applications" menu. In the "More programs" subcategory of the "Office" category you will find Adobe Acrobat. Check it and click "Apply". It worked for me.

---

### Post by foska on 2005-10-31
OK,

I went back over all the steps and it seems to be working now. But what if I wanted to install it from the files that I downloaded.  Maybe it is not everytime that I will be able to install via an update.

Foska

---

### Post by gerbman on 2005-10-31
[QUOTE=foska]This is the what I get

waynep@ubuntu:~$ sudo apt-get update
Reading package lists... Done
waynep@ubuntu:~$ sudo apt-get install acroread
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package acroread
waynep@ubuntu:~$

What's wrong?[/QUOTE]

Make sure you have the needed repositories enabled, as aysiu points out.  Follow  [this]("http://www.psychocats.net/linux/sources.php") if you're not sure.  After running ```
sudo apt-get update
``` you should be able to find the package with ```
apt-cache search acroread
```You can also use Synaptic to do all this, but I like the command line. :)

Edit:  we posted at the same time, heh...good to see you got it

---

