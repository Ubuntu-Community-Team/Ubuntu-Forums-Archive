---
title: "Need help with xfire gaim plugin"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by HIGHLIFE on 2006-02-23
Ok so I have Gaim and I have the gaim-xfire-0.5.8.tar.gz plugin file sitting here on my desktop.  Can someone please show me how to install this?
Much thx in advance.:-D

---

### Post by HIGHLIFE on 2006-02-24
bump

---

### Post by pinkpanther01010 on 2006-02-24
You can probably either open it with GAIM, and if not, just save it in gaim's plugin dir and extract it if it need be.

---

### Post by Harleen on 2006-02-24
Incidentally I took just that plugin for my first attempt to create a proper deb file. So if you're courageous you can get it [here](http://people.freenet.de/harleen/pakete/gaim-xfire_0.5.8-0ubuntu1_i386.deb) and install that with:
```
sudo dpkg -i gaim-xfire_0.5.8-0ubuntu1_i386.deb
```

Or if you want to install it from source, you have to extract that tar.gz package into a directory and call inside that directory the following commands:
```
./configure -prefix=/usr
make
sudo checkinstall
```

After installing the Plugin you have to increase the Version number in the XFire account settings as shown in the attached screenshot.

---

### Post by Kurt` on 2006-02-24
Excellent, your .deb works perfectly. ;)

Thanks alot

---

### Post by HIGHLIFE on 2006-02-24
Yes much thx

---

### Post by VictorE on 2006-04-22
Thanks for making the deb.  I've been trying to install using the source files, and it wasn't working out for me.  BTW, I discovered two things:

1.  The current (as of 4/22/06) version of XFire is 1.55
2.  I had to enter my username as case sensitive.

---

### Post by daredevil on 2006-04-22
i installed that plugin but am not sure what exactly the plugin does. can u tell me wat it is ?

---

### Post by rippon on 2006-04-25
NM I got it working thanks!

---

### Post by MiniJames on 2006-05-06
[QUOTE=Harleen]Incidentally I took just that plugin for my first attempt to create a proper deb file. So if you're courageous you can get it [here](http://people.freenet.de/harleen/pakete/gaim-xfire_0.5.8-0ubuntu1_i386.deb) and install that with:
```
sudo dpkg -i gaim-xfire_0.5.8-0ubuntu1_i386.deb
```
[/QUOTE]

I love you! It works like a charm :) Send this deb to the project so they can publicise it :)

---

### Post by cville on 2006-05-14
The link does not work anymore :(

---

### Post by dux on 2006-06-04
I'm not having much luck with the x-fire plugin either. Any chance of the link going back up again?

---

### Post by Harleen on 2006-06-04
It is still up - at least in the rare occasions, when freenet.de decides to make its user pages reachable. :???: 
But be aware that this package is for breezy. I haven't tried to build it under dapper yet as the Xfire-for-Gaim project seemed to be abandoned. But there's been some life in it recently. So maybe there's hope for this project.

Edit: I just verified, that this .deb still works under dapper. Because dapper ships the same gaim version as breezy, no extra package is needed.

---

### Post by renis on 2006-06-13
i tried it, it installed but it says wrong version number, change version in account options

edit: i changed version to 100 and it worked

---

### Post by BoneyOne on 2006-06-13
I'm still having issues trying to download the deb file.

---

### Post by Harleen on 2006-06-13
I currently don't have any problems accessing that file. But you can get it also from here: [http://home.arcor.de/harleen/pakete/gaim-xfire_0.5.8-0ubuntu1_i386.deb](http://home.arcor.de/harleen/pakete/gaim-xfire_0.5.8-0ubuntu1_i386.deb)

---

### Post by adam.skinner on 2006-06-19
Does that deb work with Dapper?  I just installed it, restarted gaim, and no dice...

---

### Post by rippon on 2007-01-14
If anyone is still looking for this:

[https://sourceforge.net/project/showfiles.php?group_id=141362&package_id=155388](https://sourceforge.net/project/showfiles.php?group_id=141362&package_id=155388)

The author now has update .debs at the above link.

---

### Post by geoth on 2007-01-27
> **renis said:**
> i tried it, it installed but it says wrong version number, change version in account options

edit: i changed version to 100 and it worked

This also worked for me, thank you for posting about the 100 version number!

---

