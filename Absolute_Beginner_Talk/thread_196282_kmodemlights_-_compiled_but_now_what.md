---
title: "kmodemlights - compiled but now what?"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by xoros on 2006-06-14
From another post: "You can install kdebase+kdebase-dev, then install kmodemlights (KDE equivalent of the gnome 2.8 modem lights applet) from [www.kde-apps.org](www.kde-apps.org) and finally set the kde panel (kicker) to run at startup so that he have modem lights in his box. (Or just install KDE)"

I got this compiled and did make and make install.  

But now what? I try to add applet to kicker panel but I don't see kmodemlights anywhere.  How do I get this to run or where do I find it?

---

### Post by xoros on 2006-06-14
I can't believe this would be a difficult thing,  probably something really simple.... does anyone have any ideas?  

Thanks in advance for any help !

---

### Post by xoros on 2006-06-14
I see "kmodemlights.desktop" in /usr/local/kde/share/apps/kicker/applets

So... ?  why don't i see it in the kicker panel?  I have to put this somewhere else?

---

### Post by xoros on 2006-06-14
Well I made it show up in the add applets menu with this: 
sudo ln -s /usr/local/kde/share/apps/kicker/applets/kmodemlightsapplet.desktop /usr/share/apps/kicker/applets/kmodemlightsapplet.desktop

Now when I click on Modemlight it to add it... it says "Modemlight applet could not be loaded. Please check your installation."
:(
Maybe I needed a --prefix when doing ./configure?  What would it be?

---

### Post by xoros on 2006-06-14
I needed to do this also: 
sudo ln -s /usr/local/kde/lib/kde3/kmodemlights_panelapplet.so /usr/lib/kde3/kmodemlights_panelapplet.so
sudo ln -s /usr/local/kde/lib/kde3/kmodemlights_panelapplet.la /usr/lib/kde3/kmodemlights_panelapplet.la

The question remains.... why did I have to do this, was there a way around it?

---

### Post by xoros on 2006-06-14
Well now when I test it,  it connects me fine but the lights don't blink and no graph! plus no way to disconnect without doing poff.

---

### Post by Harleen on 2006-06-14
You could try to install this to /usr instead of /usr/local. For KDE application this can usually be done by running configure with the option --prefix=/usr

---

### Post by xoros on 2006-06-14
Yes that worked better,  I did 'make distclean' then './configure --prefix=/usr' 
I didn't have to set up links now.  

It connects fine - but still no lights/graph !! :(

---

### Post by xoros on 2006-06-14
There was some errors during ./configure and make install,  maybe I am missing some needed packages?

Here is what happened near the end of ./configure
configure: creating ./config.status
Can't open perl script "admin/conf.change.pl": No such file or directory
mv: cannot stat `./config.status.bak': No such file or directory
config.status: creating Makefile
config.status: creating kmodemlights/Makefile
config.status: creating po/Makefile
config.status: creating config.h
config.status: executing depfiles commands

Good - your configure finished. Start make now

Edit: nevermind with 'make install';  I forgot to do sudo.  'make install' went good - no errors.  

Still no lights though :(

---

### Post by xoros on 2006-06-14
Any other ideas?  Should I try to ask the author of this program?

Thanks.

---

### Post by xoros on 2006-06-18
I had to do this quote from kmodemlight author
> a) do 

     ls /var/lock
     /sbin/ifconfig | grep "^[^ ]" 

   go online

     ls /var/lock
     /sbin/ifconfig | grep "^[^ ]" 

   There should be one file more at the second "ls": this is the
   lockfile

   There should be one device more at the output of the second
   "ifconfig" starting with "ppp": this is the device. Enter them in
   the kmodemlights preferences device-tab and try again.

	MfG
	bmg

Now it works....  Thank you !!!!!!!!!!!!!!!!!!!!!

---

