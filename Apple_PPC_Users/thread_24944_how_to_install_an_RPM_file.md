---
title: "how to install an RPM file???"
date: 2005-04-08
forum: Apple PPC Users
---

### Post by areitze on 2005-04-08
i've tried 
rpm install FILE.rpm
rpm -i FILE.rpm

and nothing...  I'm tring to install Limewire...  plus I belive I need to install Java...  how to do that???

Thx for any help...
Andrés.-

---

### Post by Leif on 2005-04-08
Ubuntu does not use rpm. what you need to do is :

alien -i FILE.rpm
dpkg -i FILE.deb

you can find instructions on how to install java by pressing the button that says ubuntu guide.

---

### Post by bored2k on 2005-04-08
rpm to deb :
alien -d file.rpm
You can get a better .tgz in limewire.org
If its the Pro and you payed for it, you can also get its .tgz.

java : 
After learning [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) , add this  to /etc/apt/sources.list
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

Then do apt-get update and finally,
sudo apt-get install sun-j2re1.5

---

### Post by CowPie on 2005-04-08
From what I know (which may be incorrect :)):

Limewire needs java SDK (not just JRE), maybe this can help: [http://ubuntuforums.org/showthread.php?t=22860&highlight=howto+installation](http://ubuntuforums.org/showthread.php?t=22860&highlight=howto+installation)

RPM needs to be converted to DEB in the terminal by "alien", check its man page for that (man alien)

---

### Post by bored2k on 2005-04-08
[QUOTE=CowPie]From what I know (which may be incorrect :)):

Limewire needs java SDK (not just JRE), maybe this can help: [http://ubuntuforums.org/showthread.php?t=22860&highlight=howto+installation](http://ubuntuforums.org/showthread.php?t=22860&highlight=howto+installation)

RPM needs to be converted to DEB in the terminal by "alien", check its man page for that (man alien)[/QUOTE]
 I have JRE installed and I run Java, Azureus and every other shizznit.

---

### Post by CowPie on 2005-04-08
[QUOTE=bored2k]I have JRE installed and I run Java, Azureus and every other shizznit.[/QUOTE]
 Oh yes, the thing is that I read Limewire exclusively requires the SDK for seom reason.

---

### Post by zab on 2005-04-08
[QUOTE=CowPie]Oh yes, the thing is that I read Limewire exclusively requires the SDK for seom reason.[/QUOTE]

You only need the SDK if you intend to build limewire from source.  ([instructions](http://www.limewire.org))

---

### Post by areitze on 2005-04-10
[QUOTE=bored2k]rpm to deb :
alien -d file.rpm
You can get a better .tgz in limewire.org
If its the Pro and you payed for it, you can also get its .tgz.

java : 
After learning [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) , add this  to /etc/apt/sources.list
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

Then do apt-get update and finally,
sudo apt-get install sun-j2re1.5[/QUOTE]


Didn't work...    hmmm  maybe I need to do a clean install and download the new version instead of trying to upgrade from the preview version I have installed...

---

