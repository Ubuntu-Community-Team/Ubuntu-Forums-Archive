---
title: "Dependency Loop"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by Skifire on 2007-11-30
Greetings all,
                 I have been using Ubuntu 7.04 for about a month now and greatly prefer it over "Other Operating Systems" that I have used.  However I have an odd dependency problem.  

The computer I have Ubuntu on I can not plug into the internet so I simply move files over with my thumb drive (patients is a virtue).  Now I am trying to install *coriander* and as usual it says I need another dependency, well here is how the tree goes.

"Coriander" needs "libgnome32" > "llibgnome32" needs "gnome-libs-data" > "gnome-libs-data" needs "gnome-bin" > (now for the kicker) "gnome-bin" needs "libegnome32"

So I am stuck with a dependency needing another one that is higher up on the branch, is there a way around this?

Any help out be very much appreciated!

Mark

---

### Post by Anicka on 2007-11-30
Could you try copying all the .deb-files into /var/cache/apt/archives/ and thereafter you run "sudo apt-get install libgnome32"? It should work

Good luck!

---

### Post by mcduck on 2007-11-30
Just install them all at the same time. Put all .deb packages in same directory and then run 'sudo dpkg -i *.deb' to install them all at the same time.

(Or of course you could just use names of all the packages, like 'sudo dpkg -i coriander.deb libgnome32.deb gnome-libs-data.deb gnome-bin.deb' if you have other .deb packages in the same directory and you don't want to install them all)

---

### Post by TheWizzard on 2007-11-30
sudo aptitude install coriander

---

### Post by ruibernardo on 2007-11-30
To install coriander on a fresh installed gutsy without any upgrades and with a i386 architecture (generic kernel), download this packages and install them as mcduck said.

[http://archive.ubuntu.com/ubuntu/pool/universe/i/imlib/imlib-base_1.9.15-3ubuntu3_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/i/imlib/imlib-base_1.9.15-3ubuntu3_all.deb)
[http://archive.ubuntu.com/ubuntu/pool/universe/g/gtk+1.2/libgtk1.2-common_1.2.10-18_all.deb ]("http://archive.ubuntu.com/ubuntu/pool/universe/g/gtk+1.2/libgtk1.2-common_1.2.10-18_all.deb")[http://archive.ubuntu.com/ubuntu/pool/universe/g/glib1.2/libglib1.2_1.2.10-17build1_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/universe/g/glib1.2/libglib1.2_1.2.10-17build1_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/universe/g/gtk+1.2/libgtk1.2_1.2.10-18_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/g/gtk+1.2/libgtk1.2_1.2.10-18_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/universe/f/ftplib/ftplib3_3.1-1-6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/f/ftplib/ftplib3_3.1-1-6_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/libu/libungif4/libungif4g_4.1.4-5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libu/libungif4/libungif4g_4.1.4-5_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/universe/i/imlib/gdk-imlib11_1.9.15-3ubuntu3_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/universe/i/imlib/gdk-imlib11_1.9.15-3ubuntu3_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/universe/g/gnome-libs/libart2_1.4.2-36_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/g/gnome-libs/libart2_1.4.2-36_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/universe/g/gnome-libs/gnome-libs-data_1.4.2-36_all.deb ]("http://archive.ubuntu.com/ubuntu/pool/universe/g/gnome-libs/gnome-libs-data_1.4.2-36_all.deb")[http://archive.ubuntu.com/ubuntu/pool/universe/g/gnome-libs/libgnome32_1.4.2-36_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/g/gnome-libs/libgnome32_1.4.2-36_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/universe/g/gnome-libs/libgnomesupport0_1.4.2-36_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/universe/g/gnome-libs/libgnomesupport0_1.4.2-36_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/universe/g/gnome-libs/libgnomeui32_1.4.2-36_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/g/gnome-libs/libgnomeui32_1.4.2-36_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/universe/o/orbit/liborbit0_0.5.17-11.1ubuntu3_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/universe/o/orbit/liborbit0_0.5.17-11.1ubuntu3_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/universe/g/gnome-libs/libgnorba27_1.4.2-36_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/g/gnome-libs/libgnorba27_1.4.2-36_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/universe/g/gnome-libs/libgnorbagtk0_1.4.2-36_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/universe/g/gnome-libs/libgnorbagtk0_1.4.2-36_i386.deb")
[http://archive.ubuntu.com/ubuntu/pool/universe/g/gnome-libs/gnome-bin_1.4.2-36_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/universe/g/gnome-libs/gnome-bin_1.4.2-36_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/universe/d/db3/libdb3_3.2.9+dfsg-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/d/db3/libdb3_3.2.9+dfsg-1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/universe/g/gdk-pixbuf/libgdk-pixbuf2_0.22.0-11_i386.deb ]("http://archive.ubuntu.com/ubuntu/pool/universe/g/gdk-pixbuf/libgdk-pixbuf2_0.22.0-11_i386.deb")[http://archive.ubuntu.com/ubuntu/pool/main/libd/libdc1394/libdc1394-13_1.1.0-3ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libd/libdc1394/libdc1394-13_1.1.0-3ubuntu3_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/universe/c/coriander/coriander_1.0.1-3.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/c/coriander/coriander_1.0.1-3.1_i386.deb)

---

### Post by TheWizzard on 2007-12-01
> **epimeteo said:**
> To install coriander on a fresh installed gutsy without any upgrades and with a i386 architecture (generic kernel), download this packages and install them as mcduck said.


NO. don't install coriander this way!
this is the windows way. 

use aptitude, apt-get or the package manager. 
read:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by ruibernardo on 2007-12-01
Hi TheWizzard,

the OP said the following on his first post:
> **Skifire said:**
> 
The computer **I have Ubuntu on I can not plug into the internet** so I simply move files over with my thumb drive (patients is a virtue). Now I am trying to install *coriander*...
I was just helping him to install the package he wanted and all their dependencies based on a fresh install of Gutsy generic kernel.

---

### Post by TheWizzard on 2007-12-02
> **epimeteo said:**
> Hi TheWizzard,

the OP said the following on his first post:


oops, missed that. sorry!

---

