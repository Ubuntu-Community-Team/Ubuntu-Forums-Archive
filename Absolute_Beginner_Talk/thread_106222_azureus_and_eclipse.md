---
title: "azureus and eclipse"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by o_owd on 2005-12-20
hello,
i installed azureus from here ([https://wiki.ubuntu.com/AzureusHowTo?highlight=%28azureus%29)](https://wiki.ubuntu.com/AzureusHowTo?highlight=%28azureus%29)).
among other packages it installed "libswt-gtk-3.1-java" and "libswt-gtk-3.1-jni".
now i want to install eclipse sdk. the synaptic package manager tells me that azureus and the two packages specified above must be uninstalled because it must install the following two "libswt3.1-gtk-java" and "libswt3.1-gtk-jni".
how to install both of them (azureus and eclipse) ?

and btw are these packages the same thing ?

"libswt-gtk-3.1-java"  and  "libswt3.1-gtk-java"
"libswt-gtk-3.1-jni" and "libswt3.1-gtk-jni"

thanks.

---

### Post by Perfect Storm on 2005-12-20
I have no expertise on these two programs, but I'll give it a shot.


Get rid of your java (uninstall it). Then:

```

sudo gedit /etc/apt/sources.list

```
add:

> ## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

```
sudo apt-get update
sudo apt-get install sun-j2re1.5

```

Now download Azureus here: [http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php) Pick Linux version 2.3.0.6.

```

cd /to/the/folder/where/you/saved/azureus
sudo tar jxvf Azureus_2.3.0.6_linux.tar.bz2 -C /opt/
sudo chown -R root:root /opt/azureus/
smeg

```

Pick **Internet** and click **New Entry**

Name: Azureus
Command: /opt/azureus/azureus
Icon: /opt/azureus/Azureus.png

press ok.


That should do the trick.

---

### Post by o_owd on 2005-12-21
it works. thanks.

---

### Post by WelterPelter on 2006-02-03
That got me going too. Thanks!

:mrgreen: I just want to say that these ubuntu forums rule! You can actually get answers here. Other distro forums I've been on are like endless stone-cold waiting halls, echoing with noise.

One note: If you've already got java 5 installed, you shouldn't bother uninstalling it.

---

### Post by darth_vector on 2006-02-03
thank you, that was a very helpfull post AI!

---

### Post by Perfect Storm on 2006-02-04
[QUOTE=WelterPelter]
One note: If you've already got java 5 installed, you shouldn't bother uninstalling it.[/QUOTE]

Correct.

---

### Post by Seeker on 2006-02-04
Thanks! That worked perfectly.

---

### Post by sciurus on 2006-02-05
You may need to eidt /opt/azureus/azureus and set PROGRAM_DIR="/opt/azureus"

---

