---
title: "How to install bittorrent"
date: 2005-09-30
forum: Absolute Beginner Talk
---

### Post by Goffy on 2005-09-30
Hi.

As a total beginner with Linux alltogether I have some difficulties when it comes to installing new software. So far I gave figured out the package manager and installed most of the stuff I need from there. I also installed the bittorrent filesharing software, but for some reason it didn't install the GUI as well. I had to go to a website to get it, wich I have done. So now I am the proud owner of something that looks like a packed file wich I have no clue what to do with.??

I tried to search the bittorrent website for installing tips, but it seems such information is strictly confidential.

Anyone here able to help? Please take into consideration that I am an old infantryman who is used to be fed information with a teaspoon. ;-)

---

### Post by Qrk on 2005-09-30
Ubuntu comes with a bittorrent installed by default... did this one not work?

Its Applications --> Internet --> Gnome Bittorrent

---

### Post by Goffy on 2005-09-30
Not really.. It tells me to open the location of the bittorrent meta file whatever that might be??


Yes, yes.. Dumbass.. I know.. :lol:

---

### Post by Qrk on 2005-09-30
OK... So when you click on a bittorrent to download through firefox, it should ask you how you want to open it. "open with" dialog box. The default should be "Gnome Bittorrent" choose that and it will download the meta file then automatically start the bittorrent client.

---

### Post by poofyhairguy on 2005-09-30
[QUOTE=Goffy]Not really.. It tells me to open the location of the bittorrent meta file whatever that might be??
[/QUOTE]

Thats the .torrent file you get from sites. For all the sites I go to, clicking on the "get torrent" link give me the option to open with Gnome-bittorrent!

---

### Post by Goffy on 2005-09-30
So bittorrent isn't a filesharing system like limewire, edonkey, kazaa and others?

Where do I find one of those that will run on ubuntu, and how do I install them?

---

### Post by Qrk on 2005-09-30
There are a lot of options
Amule is the Linux version of emule.
Get it by 
1) enableing the extra repositories, see [www.ubuntuguide.org](www.ubuntuguide.org)
2) typing 
sudo apt-get install amule 
into a terminal
Gtk-Gnutella is like Limewire or Kazaa
1) do 1 above
2) type
sudo apt-get install gtk-gnutella
into a terminal

---

### Post by Goffy on 2005-09-30
I did the enabeling of the extra repositories but the sudo-apt get didn't work. Couldn't find package it said??

Here is the entire message:

> W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 Ingen slik fil eller filkatalog)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 Ingen slik fil eller filkatalog)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 Ingen slik fil eller filkatalog)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 Ingen slik fil eller filkatalog)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 Ingen slik fil eller filkatalog)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 Ingen slik fil eller filkatalog)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 Ingen slik fil eller filkatalog)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 Ingen slik fil eller filkatalog)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 Ingen slik fil eller filkatalog)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 Ingen slik fil eller filkatalog)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 Ingen slik fil eller filkatalog)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_main_binary-i386_Packages) - stat (2 Ingen slik fil eller filkatalog)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 Ingen slik fil eller filkatalog)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 Ingen slik fil eller filkatalog)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 Ingen slik fil eller filkatalog)
W: You may want to run apt-get update to correct these problems
E: Kunne ikke finne pakken gtk-gnutella


type this command:

sudo apt-get update

then type the other command above to get gtk-gnutella!

---

### Post by xequence on 2005-09-30
This is where I can accually help - Bittorent ;) Heres an explanation of it...

It is the most widly used network for large files. You get a .torrent file from a website that tells the client (Bittorent, Azureus, etc) what to download. It will download the file, while uploading. They have a share ratio, how much you share to what you download. It is normally good to share 20% more then you downloaded... If you downloaded a 10GB file, share 12 GB back. Thats a ratio of 1.2 ;) The site that you downloaded the .torrent file from, the tracker, tracks your stats. Many private sites you have an account and if you get a low share ratio, you get banned. The most popular public sites are torrentspy and thepiratebay. I am on a site called demonoid that is REALLY good. They rarly open the registration, but they have an invite system. I want an invite to two sites I heard were great for music - Oink and Audiofarm :P And another thing. Bittorent will hold up good legally because it is used very much for legal purposes. Nasa uses it to distribute its WorldWind program, and most linux distros use it.

There you go, a hopefully good explanation of bittorent. The only P2P system where people trade 8 GB DVD quality seasons of TV shows, and some share terabytes of files :)

---

