---
title: "Broken depenancies help"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by Phosphoric on 2007-11-07
Long story, trying to get kdenlive to capture.  Apparently I need a later version of dvgrab.  Tried to download that and it asked for libc6.  Downloaded that and it said I had broken dependencies.

In synaptic I finally found the broken dependancies libc6-dev and libc6-i686.

To repair these Synaptic wants to remove loads of my basic packages like gnucash etc.

What do I do?  I don't want to trash my system.

Help please.

---

### Post by markharding557 on 2007-11-07
reckon you have to remove the packeges you manualy installed

---

### Post by Phosphoric on 2007-11-08
Well, I'm really stuffed now.

Removed libc6 as instructed by Synaptic and it took out a whole lot of other stuff.  It didn't seem to have the intelligence to reinstall anything so now I have packages that no longer work.

Tried to reinstall gnucash.  Now I'm in a dependency loop.  Synaptic keeps saying that the package needs g-wrap but I'm not going to install it!  Try to install g-wrap and it says it needs libgwrap-runtime0-dev.....but is not going to install it.

Seems to boil down to the missing libc6 package.  When I try to install that, it stops with this error:  libc6(=2.5Oubuntu14) but 2.6.1-lubuntu9 is to be installed.

Then won't go any further.  Now I'm stuck.

Help please.

---

### Post by zvacet on 2007-11-08
```
cd /var/cache/apt/archives
```

```
sudo dpkg -i libc6_2.5-0ubuntu14_i386.deb
```

and after that 

```
sudo aptitude install g-wrap  libgwrap-runtime0-dev
```

---

### Post by Phosphoric on 2007-11-08
Thanks for the reply zvacet.
Could you explain what this does?  

The example of g-wrap was one of many.  Do I have to carry out the same command line work for each package that got removed.....I'll be at it forever.

I'm at work at the moment so can't try out your suggestion but I'll give it a go later.

Thanks.

---

### Post by Phosphoric on 2007-11-08
Hmm. tried the suggestion and got:

```
ray@ray-desktop:~$ cd /var/cache/apt/archives
ray@ray-desktop:/var/cache/apt/archives$ sudo dpkg -i libc6_2.5-0ubuntu14_i386.deb
dpkg: error processing libc6_2.5-0ubuntu14_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libc6_2.5-0ubuntu14_i386.deb
ray@ray-desktop:/var/cache/apt/archives$ 
```

What next?

---

### Post by Maestro23 on 2007-11-08
> **Phosphoric said:**
> Hmm. tried the suggestion and got:

```
ray@ray-desktop:~$ cd /var/cache/apt/archives
ray@ray-desktop:/var/cache/apt/archives$ sudo dpkg -i libc6_2.5-0ubuntu14_i386.deb
dpkg: error processing libc6_2.5-0ubuntu14_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libc6_2.5-0ubuntu14_i386.deb
ray@ray-desktop:/var/cache/apt/archives$ 
```

What next?

See exactly what is in the archived directory.
 
> cd /var/cache/apt/archives

then

ls (list contents of directory)


Can also try the "Fix Broken Packages" option in Synaptic. Under Edit.  

Can also search for Broken stuff under the Filters option: Settings>>Filters

---

### Post by Phosphoric on 2007-11-08
Seems to me that I don't have libc6 2.5-Oubuntu installed hence not in the archive.

This is a search in Synaptic

---

### Post by Phosphoric on 2007-11-08
Sorry Maestro23, didn't catch your post before putting up my Synaptic list.

```
ray@ray-desktop:~$ cd /var/cache/apt/archives
ray@ray-desktop:/var/cache/apt/archives$ ls
audacity_1.2.6-0ubuntu1_i386.deb
autotools-dev_20060920.1_all.deb
bsdutils_1%3a2.12r-17ubuntu2.1_i386.deb
cupsys_1.2.8-0ubuntu8.1_i386.deb
cupsys-bsd_1.2.8-0ubuntu8.1_i386.deb
cupsys-client_1.2.8-0ubuntu8.1_i386.deb
cupsys-common_1.2.8-0ubuntu8.1_all.deb
digikam_2%3a0.9.1-1ubuntu4_i386.deb
digikamimageplugins_2%3a0.9.1-0ubuntu2_i386.deb
firefox_2.0.0.8+1nobinonly-0ubuntu1_i386.deb
firefox-gnome-support_2.0.0.8+1nobinonly-0ubuntu1_i386.deb
hpijs_2.7.2+1.7.3-0ubuntu1.1_i386.deb
hplip_1.7.3-0ubuntu1.1_i386.deb
hplip-data_1.7.3-0ubuntu1.1_all.deb
kdebase-bin_4%3a3.5.6-0ubuntu20.7_i386.deb
kdebase-kio-plugins_4%3a3.5.6-0ubuntu20.7_i386.deb
kdesktop_4%3a3.5.6-0ubuntu20.7_i386.deb
libcupsimage2_1.2.8-0ubuntu8.1_i386.deb
libcupsys2_1.2.8-0ubuntu8.1_i386.deb
libcupsys2-dev_1.2.8-0ubuntu8_i386.deb
libexiv2-0.12_0.12-0ubuntu2_i386.deb
libgcrypt11-dev_1.2.3-2build1_i386.deb
libgnutls-dev_1.4.4-3build1_i386.deb
libgpg-error-dev_1.4-2build1_i386.deb
libieee1284-3-dev_0.2.10-4build1_i386.deb
libjpeg62-dev_6b-13_i386.deb
libkexiv2-0_0.1.1-0ubuntu1_i386.deb
libkipi0_0.1.5-1_i386.deb
libkonq4_4%3a3.5.6-0ubuntu20.7_i386.deb
liblzo-dev_1.08-3_i386.deb
libnspr4_2%3a1.firefox2.0.0.8+1nobinonly-0ubuntu1_i386.deb
libnss3_2%3a1.firefox2.0.0.8+1nobinonly-0ubuntu1_i386.deb
libopencdk8-dev_0.5.9-2build1_i386.deb
libpng12-0_1.2.15~beta5-1ubuntu1.1_i386.deb
libpopt-dev_1.10-3build1_i386.deb
libportaudio2_19+svn20060825-1_i386.deb
libsane-dev_1.0.18-3ubuntu1_i386.deb
libsensors-dev_1%3a2.10.1-2ubuntu2_i386.deb
libsnmp9-dev_5.2.3-4ubuntu1_i386.deb
libsnmp-perl_5.2.3-4ubuntu1_i386.deb
libsoundtouch1c2_1.3.0-2.1_i386.deb
libssl0.9.8_0.9.8c-4ubuntu0.2_i386.deb
libssl-dev_0.9.8c-4ubuntu0.2_i386.deb
libtasn1-3-dev_0.3.6-2build1_i386.deb
libtiff4-dev_3.8.2-6_i386.deb
libtiffxx0c2_3.8.2-6_i386.deb
libtool_1.5.22-4_i386.deb
libusb-dev_2%3a0.1.12-2_i386.deb
libwrap0-dev_7.6.dbs-11ubuntu0.1_i386.deb
libwxgtk2.4-1_2.4.5.1ubuntu2_i386.deb
lock
mount_2.12r-17ubuntu2.1_i386.deb
mozilla-thunderbird_1.5.0.13+1.5.0.14b-0ubuntu0.7.04_i386.deb
openssl_0.9.8c-4ubuntu0.2_i386.deb
partial
python2.5-dev_2.5.1-0ubuntu1_i386.deb
python-imaging_1.1.6-0ubuntu3_i386.deb
python-qt3_3.17-0ubuntu3_i386.deb
python-reportlab_2.0dfsg-1_all.deb
python-sip4_4.5-0ubuntu2_i386.deb
sound-recorder_0.06-7_i386.deb
tzdata_2007h-0ubuntu0.7.04_all.deb
util-linux_2.12r-17ubuntu2.1_i386.deb
util-linux-locales_2.12r-17ubuntu2.1_all.deb
zlib1g-dev_1%3a1.2.3-13ubuntu4_i386.deb
ray@ray-desktop:/var/cache/apt/archives$ 

```

I did the "fix broken packages"  thing and that's why I'm in this state, it took out loads of other package dependencies.

---

### Post by Phosphoric on 2007-11-08
OK, latest plan.....I've made a new /home partition and copied my home folder to it.

I've now made a fresh install of Gutsy Gibbon.

Can I now make Gutsy use all or some of my old bits and pieces.  The howtos that I have found so far tell me how to copy my old home folder in to the new Gutsy home folder but I want to do the reverse.  I want the new installation to use the separate /home partition with all my old stuff in it.

Thanks. :)

---

### Post by Phosphoric on 2007-11-09
Any takers on restoring my old /home partition?

---

### Post by zvacet on 2007-11-09
You just need libc6_2.5-0ubuntu14_i386.deb package.it is not in var/cache/apt/archives.So what.Download it from 

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libc6&searchon=names&subword=1&version=feisty&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libc6&searchon=names&subword=1&version=feisty&release=all")

and install it with command I give you in previous post.That way you will downgrade it and that is what you need to do.To your question about other packages it is command to install them at the same time.That way you will get out of dependency hell.

---

### Post by Phosphoric on 2007-11-09
Thanks for your considered reply zvacet.

Unfortunately I carried on in my own way and have stuffed completely my OS and have now installed Gutsy.  I now have another set of problems which will appear in other threads.

So we keep learning.:)

Thanks for taking the time to help.:KS

---

