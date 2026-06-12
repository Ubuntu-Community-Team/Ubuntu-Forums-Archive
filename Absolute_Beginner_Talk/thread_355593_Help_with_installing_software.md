---
title: "Help with installing software"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by Bright Carver on 2007-02-07
Hello

I have a laptop that won't connect to the internet.  Is there a way I can access the repositories on my Windows PC, download software, burn to CD and install on my laptop?

I've seen a site to help you burn to DVD, but my laptop doesn't have a DVD player

Thanks

Karl

---

### Post by compiledkernel on 2007-02-07
This is probably your best bet , IMHO 

[http://doc.gwos.org/index.php/ISO_image_source](http://doc.gwos.org/index.php/ISO_image_source)

---

### Post by Bright Carver on 2007-02-07
What I want to do is install WINE, Ardour and Rosegarden, and install an MP3 codec for the music player.  I have no internet connection on my lappy, but a CD drive.  My desktop Windows PC connects to the internet, and can burn CD's.

Could somebody help me through this?

---

### Post by compiledkernel on 2007-02-07
Ahhh, ok then. 

You just need Deb packages for those accompanying files. 

You may run into issues with dependencies , this is commonly refered to as Dependency Hell. (this is often felt by users of RPM based distros, as with such is Fedora)  

Hmmmm lets see now 
Wine - [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Others - (not sure if they have rosegarden in there or not) - [http://www.getdeb.net/](http://www.getdeb.net/)

Youll need to download the accompanying deb files, dependin on depedency though.

---

### Post by Bright Carver on 2007-02-07
Ok then, I'll try that.  I'm not very good at this yet, so I'll probably be back when I start tearing my hair out again :)

Thanks

Karl

---

### Post by eric71 on 2007-02-08
One thing to look at is Ubuntu's web pages for the various packages like this for rosegarden:

[http://packages.ubuntulinux.org/edgy/sound/rosegarden](http://packages.ubuntulinux.org/edgy/sound/rosegarden)

You can download the packages through there. They will list all of the dependencies you need.  You can cross reference this with what you've already got installed in Synaptic. That way you can get everything you need without having to boot back and forth between Windows and Ubuntu everytime apt tells you you have missing dependencies. Still tricky because something needed by one package will require other things, and without an internet connection to let apt do it all automatically, it rerally becomes dependency hell. Rosegarden will be tough, because it is a KDE app.  If your starting with Gnome, there will be a ton of KDE dependencies to get.

---

