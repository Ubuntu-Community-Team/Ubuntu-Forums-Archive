---
title: "problem using apt-get dist-upgrade to upgrade from 5.10 &gt; 6.0.6"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by specialst on 2006-10-21
Hey guys,

I have ubuntu 5.10 installed, and want to upgrade to 6.0.6. I heard you can use the apt-get dist-upgrade command, but i can't seem to get that to work.... does anyone know of any tutorials or how to get this breezy upgraded to edgy?

thanks,

al

---

### Post by Sef on 2006-10-21
Did you use the two commands?

Applications > Accessories > Terminal

sudo apt-get update

sudo apt-get dist-upgrade

Also did you change your sources list?

You need to change Breezy to Dapper.

sudo gedit /etc/apt/sources.list

---

### Post by specialst on 2006-10-21
thanks for the quick reply. i'm still having some problems though...

i tried the first two commands (sudo apt-get update; sudo apt-get dist-upgrade) before changing the sources.list and that didn't work...i then opened the sources.list and replaced all occurances of "Breezy" with "Dapper" and ran the commands again, but no luck.

Do you want me to paste all the errors that i get?

thanks again,

al

---

### Post by blendmaster on 2006-10-21
Shouldn't you be using 

```
sudo aptitude update

sudo aptitude dist-upgrade
```

I might be wrong though.

---

### Post by Engnome on 2006-10-21
> **blendmaster said:**
> Shouldn't you be using 

```
sudo aptitude update

sudo aptitude dist-upgrade
```

I might be wrong though.

Apt and aptitude does the same thing. Some prefer aptitude because it keeps track of what u don't need and uninstalls it if no other package needs it. I use apt because I had some issues with aptitude. Using deborphan to remove unneeded packages.

What error output are you getting specialist?

---

### Post by specialst on 2006-10-22
These are the errors I get when i do sudo apt-get update (this is with the sources.list file changed where all "breezy" words were changed to "dapper")
```
dex@ubuntu:~$ sudo apt-get update
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) Dapper Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) Dapper Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) Dapper/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) Dapper/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) Dapper/universe Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) Dapper Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) Dapper/multiverse Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) Dapper/main Packages
  404 Not Found [IP: 146.137.96.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) Dapper/restricted Packages
  404 Not Found [IP: 146.137.96.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) Dapper/universe Packages
  404 Not Found [IP: 146.137.96.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) Dapper/multiverse Packages
  404 Not Found [IP: 146.137.96.15 80]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) Dapper Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) Dapper/free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) Dapper/non-free Packages
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) Dapper/free Packages
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) Dapper/non-free Packages
  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/Dapper/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/Dapper/main/binary-i386/Packages.gz)  404 Not Found [IP: 146.137.96.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/Dapper/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/Dapper/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 146.137.96.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/Dapper/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/Dapper/universe/binary-i386/Packages.gz)  404 Not Found [IP: 146.137.96.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/Dapper/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/Dapper/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 146.137.96.15 80]
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/Dapper/free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/Dapper/free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/Dapper/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/Dapper/non-free/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) Dapper/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_Dapper_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) Dapper/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_Dapper_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) Dapper/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_Dapper_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) Dapper/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_Dapper_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) Dapper/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_Dapper_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) Dapper/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_Dapper_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
```and this is what i get when i try to do sudo apt-get dist-upgrade```
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) Dapper/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_Dapper_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) Dapper/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_Dapper_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) Dapper/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_Dapper_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) Dapper/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_Dapper_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) Dapper/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_Dapper_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) Dapper/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_Dapper_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
```Thanks guys!

---

### Post by specialst on 2006-10-26
any luck on this guys? I think the main problem is my sources.list file - because i can't seem to be able to download "anything" else using apt-get....

does anyone know where i can get a new copy of sources.list for my 5.10 or should i get the new breezy sources.list?

thanks

---

### Post by PriceChild on 2006-10-26
I think the us.archive servers have been overloaded this afternoon with edgy's release.

If i were you, i'd try a different mirror or try again later.

---

