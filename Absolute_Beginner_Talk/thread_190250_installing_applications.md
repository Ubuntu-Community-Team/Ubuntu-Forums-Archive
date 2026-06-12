---
title: "installing applications"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by benner on 2006-06-06
I have been reading all kinds of different posts about installing new apps and to be honest, still  don't really get it.  I think I understand how to download using the package manager but I am downloading things myself.  I downloaded a couple of applications from sourceforge and haven't gotten the commands right to install.  One of them is called VCDmount and it is sitting on my desktop.  The other is skype and i got the .deb file.  It is also on my desktop.  Can someone walk me through it or drop me a link to a very simple good user guide?  The last two questions I posted got very quick and helpful responses that solved my problems.  Your kindness and understanding is appreciated...

---

### Post by aysiu on 2006-06-06
[QUOTE=benner]Can someone walk me through it or drop me a link to a very simple good user guide?[/QUOTE] [http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by Kilz on 2006-06-06
[QUOTE=benner]I have been reading all kinds of different posts about installing new apps and to be honest, still  don't really get it.  I think I understand how to download using the package manager but I am downloading things myself.  I downloaded a couple of applications from sourceforge and haven't gotten the commands right to install.  One of them is called VCDmount and it is sitting on my desktop.  The other is skype and i got the .deb file.  It is also on my desktop.  Can someone walk me through it or drop me a link to a very simple good user guide?  The last two questions I posted got very quick and helpful responses that solved my problems.  Your kindness and understanding is appreciated...[/QUOTE]

If you have a .deb file on your desktop right click on the file and chose "Open with GDebi Package Installer" Debi will start up , then click Install package. 

Edit: Darn I type to slow, nice link aysiu.

---

### Post by dmizer on 2006-06-06
here's a good one ... skype specific direct link, but if you scroll to the top, there's lots of other pointers there: [http://easylinux.info/wiki/Ubuntu#How_to_install_Messenger_.28Skype.29](http://easylinux.info/wiki/Ubuntu#How_to_install_Messenger_.28Skype.29)

---

### Post by tonyr on 2006-06-06
[QUOTE=aysiu][http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)[/QUOTE]

WHAT!! You're not plugging your own???
[http://www.psychocats.net/ubuntu/installingsoftware.php]("http://www.psychocats.net/ubuntu/installingsoftware.php")

---

### Post by aysiu on 2006-06-06
[QUOTE=tonyr]WHAT!! You're not plugging your own???
[http://www.psychocats.net/ubuntu/installingsoftware.php]("http://www.psychocats.net/ubuntu/installingsoftware.php")[/QUOTE] Guides with screenshots tend to be more welcome by newcomers.

When people are using Kubuntu, I direct them to my guide, as the Monkeyblog one seems quite Gnome focused at the moment.

---

### Post by tonyr on 2006-06-06
**benner**:

If you downloaded **vcdmount** from sourceforge.net, I believe you got a tar file or a
compressed tar file, one of these:
[B]vcdmount-1.0.tar.gz
vcdmount-1.0.tar
vcdmount-1.0.tar.bz2[/B]

To install any one of these, you first need to extract it with one of these commands in a
**terminal** (see **aysiu**'s signature for **the terminal**):
```

tar xzf vcdmount-1.0.tar.gz
tar xf vcdmount-1.0.tar
tar --bzip2 -xf vcdmount-1.0.tar.bz2

```

(OTHER WATCHERS: Does this happen automatically in **nautilus** with a
double-click?  I'm a cli guy from way back...)

[COLOR="Red"]EDIT1:  In Kubuntu(KDE), double-clicking the tar file icon opens it with **Ark**, and from there
you can extract it to a directory of your choice.  I assume the same thing happens
in Ubuntu(Gnome).[/COLOR]

A directory named **vcdmount-1.0** will be created.  In a terminal,  go to that directory and
type the command
```

sudo make

```

The executable **vcdmount** will be installed in **/usr/bin**, and a man page
will also be installed.  The file INSTALL in the **vcdmount-1.0** directory says essentially the same
thing as I am saying here, but does not include the **sudo**.  It sort of assumes
that you will be user **root** when you are installing; Ubuntu encourages the 
use of **sudo** for commands requiring root privileges.

---

