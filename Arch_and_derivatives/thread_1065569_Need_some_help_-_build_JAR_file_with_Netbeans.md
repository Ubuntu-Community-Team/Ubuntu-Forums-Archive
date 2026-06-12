---
title: "Need some help - build JAR file with Netbeans?"
date: 2009-02-10
forum: Arch and derivatives
---

### Post by Open-SuSe-A-Me on 2009-02-10
Hello everyone, i am having a problem getting iplist/ipblock to work properly.  iplist is a program similar to peerguardian on windows.  For Ubuntu a .deb file is provided from sourceforge which works fine, but on Arch i have to compile from source, which i know how to do but i'm not so sure how to do Java stuff.

Basically the program itself "iplist" compiled without errors and i can start it from the terminal, but the GUI "ipblock" needs to be built with Netbeans according to the readme.  The gui used to be in java on ubuntu, but newer versions have a GTK interface at least in the ubuntu deb.  

What i have achieved so far is executing the .jar file in the terminal and the GUI does appear, but all of the drop-down menus which normally have the list URL's to select are blank.

Does anyone know what "build with Netbeans" means?  Sorry i dropped computer science as a major within 1 month of trying to learn java, too confusing.

Thanks! Arch rules.

----------------
Now playing: [Arch Enemy - Enemy Within](http://www.foxytunes.com/artist/arch+enemy/track/enemy+within)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by uljanow on 2009-02-10
iplist seems to be in [AUR]("http://aur.archlinux.org/packages.php?ID=14871&detail=0"). But I haven't tested those packages.

The source tarball comes with the pre-build ipblockUI.jar. Due to the nature of java there's no need to recompile it. 

Once the GUI starts it expects two config files in /etc: ipblock.conf and ipblock.lists, respectively.

---

### Post by Open-SuSe-A-Me on 2009-02-11
Thanks uljanow, i got it working from the AUR with the GTK interface.

The only problem is I am using KDE3 and i can't seem to theme ipblock because it is a root application.  I know in gnome i just put the theme in /usr/share/themes/ and it will theme, but its not working.  I know it is working for firefox and other gtk apps because they are gtk-themed properly.

I even tried "kdesu kcontrol" and setting the gtk theme but it doesnt work.

Any ideas?

thanks

---

### Post by Open-SuSe-A-Me on 2009-02-11
Ok, nevermind, the theme is working now, BUT after i choose my lists and update everything is fine until i "enable" ipblock and it gives me this error:

error: can't get status of iplist

also after i get this error it seems to be working in the background, because half of my tabs in firefox would not connect, one was google which i know should be blocked by ipblock.

i'd really like to get this working, thanks

---

### Post by uljanow on 2009-02-11
What does "DEBUG=1 sudo ipblock -sl" show ?

---

### Post by uljanow on 2009-02-11
I've found the reason for the error message. The GUI expects awk to be in /usr/bin but in Arch it's in /bin. The following shoud fix it until I find a better solution:
```
ln -s /bin/awk /usr/bin/awk
```

---

### Post by Open-SuSe-A-Me on 2009-02-11
Thanks Uljanow, that fixed it.

*Note to admins* - I would like to mark this as solved and give uljanow a "thanks" but i cannot do either.

---

### Post by smartboyathome on 2009-02-12
> **Open-SuSe-A-Me said:**
> *Note to admins* - I would like to mark this as solved and give uljanow a "thanks" but i cannot do either.

[http://ubuntuforums.org/showthread.php?t=1044714](http://ubuntuforums.org/showthread.php?t=1044714)

---

### Post by Open-SuSe-A-Me on 2009-02-12
Thanks for that

---

