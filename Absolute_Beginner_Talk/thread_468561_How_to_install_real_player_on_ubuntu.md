---
title: "How to install real player on ubuntu"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by yinglcs2 on 2007-06-09
Hi,

I am following the step here in order to install real player:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Player_.28RealPlayer_10.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Player_.28RealPlayer_10.29)

but I am getting the following error:

$ sudo aptitude install realplay
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package matching "realplay".  However, the following
packages contain "realplay" in their description:
  kmplayer-konq-plugins 
The following packages have been automatically kept back:
  gimp-data libfreetype6-dev libnspr-dev libnss-dev linux-image-generic 
  linux-restricted-modules-generic 
The following packages have been kept back:
  firefox firefox-dev firefox-gnome-support gimp gimp-python libfreetype6 
  libgimp2.0 libnspr4 libnss3 linux-generic linux-headers-generic 
0 packages upgraded, 0 newly installed, 0 to remove and 17 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.


Can you please tell me how to fix it?

---

### Post by jiminycricket on 2007-06-09
Try installing this deb package [http://archive.canonical.com/ubuntu/pool/main/r/realplay/](http://archive.canonical.com/ubuntu/pool/main/r/realplay/)

---

### Post by yinglcs2 on 2007-06-09
I tired, but I get this error now:

$ sudo apt-get install realplay_10.0.8-0ubuntu3_i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package realplay_10.0.8-0ubuntu3_i386

---

### Post by NeoLithium on 2007-06-09
Enable your extra repositories:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

And then see here:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Player_.28RealPlayer_10.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Player_.28RealPlayer_10.29)

You'll get all up in no time :)

---

### Post by yinglcs2 on 2007-06-09
I add this:/etc/apt/sources.list

```
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu feisty-commercial main
```

and then 

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

and then
```

sudo aptitude update
```

and finally
```
sudo aptitude install realplay
```

but I still get this:

```
$ sudo aptitude install realplay
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package matching "realplay".  However, the following
packages contain "realplay" in their description:
  kmplayer-konq-plugins 
The following packages have been automatically kept back:
  gimp-data libfreetype6-dev libnspr-dev libnss-dev linux-image-generic 
  linux-libc-dev linux-restricted-modules-generic 
The following packages have been kept back:
  firefox firefox-dev firefox-gnome-support gimp gimp-python libfreetype6 
  libgimp2.0 libnspr4 libnss3 linux-generic linux-headers-generic 
0 packages upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
```

---

### Post by dhtechs on 2007-06-09
no matter the "official announcements" use Automatix2 to install realplayer...it's painless   [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

It just works.

---

### Post by yinglcs2 on 2007-06-09
Can you please tell me how to fix my problem without install other application first? Thanks.

---

### Post by jiminycricket on 2007-06-10
> **yinglcs2 said:**
> I tired, but I get this error now:

$ sudo apt-get install realplay_10.0.8-0ubuntu3_i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package realplay_10.0.8-0ubuntu3_i386

Hmm did you double click on the downloaded .deb package?

or, installing from the command line is,
'sudo dpkg -i FILENAME.deb'

you can press the 'tab' button on your keyboard to autocomplete the file name.

---

