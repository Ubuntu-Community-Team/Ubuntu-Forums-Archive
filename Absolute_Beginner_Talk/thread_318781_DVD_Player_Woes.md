---
title: "DVD Player Woes"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by chaplanger on 2006-12-14
When I attempt to start a DVD I get the following error message:
[I]Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it.
Please install the necessary plugins and restart Totem to be able to play this me[/I]dia.

I am running Edgy Eft -- I have downloaded "Easyubuntu" and installed all that I could but in the middle of installation I receive this message

[I][I]Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/free/binary-i386/Packages.gz:](http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/free/binary-i386/Packages.gz:) 404 Not Found
[http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/non-free/binary-i386/Packages.gz:](http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/non-free/binary-i386/Packages.gz:) 404 Not Found[/I]

Any help would be appreciated -- Remember -- brand new to LINUX and have very little knowledge about command line terminal etc.

---

### Post by Jussi01 on 2006-12-14
Get automatix2. It should have all the bits and peices you need.

---

### Post by chaplanger on 2006-12-14
I followed you instructions, downloaded and installed Automatix2 and added the multimedia players and codexes but when I attempt to play a DVD I still get

The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?

For whatever reason I do not have libdvdcss.

Libdvdcss -- seems to be the culprit.  How do I download this file and install on my Linux system (please recall that though I have heard of tar and untar -- I have no clue of what to do or how to write into the terminal)

Thanks

---

### Post by Azakus on 2006-12-17
Read this post (a somewhat shameless plug on my part) [http://ubuntuforums.org/showthread.php?t=320379#6](http://ubuntuforums.org/showthread.php?t=320379#6)

---

### Post by Bachstelze on 2006-12-17
You can get libdvdcss from [here](http://download.videolan.org/pub/libdvdcss/1.2.9/). Either get the DEB and install it with *sudo dpkg -i filename.deb* or get the source and build it yourself. I personnaly always build it from source, it's just three commands to run anyway.

---

### Post by Azakus on 2006-12-17
> **HymnToLife said:**
> You can get libdvdcss from [here](http://download.videolan.org/pub/libdvdcss/1.2.9/). Either get the DEB and install it with *sudo dpkg -i filename.deb* or get the source and build it yourself. I personnaly always build it from source, it's just three commands to run anyway.

If you build from source (as there are no AMD64 builds for this in the link listed) use this code ```
sudo aptitude install checkinstall build-essential
wget http://download.videolan.org/pub/libdvdcss/1.2.9/libdvdcss-1.2.9.tar.gz
tar -xzf libdvdcss-1.2.9.tar.gz
cd ./libdvdcss-1.2.9
./configure --prefix=/usr
make
sudo checkinstall
```
This will build the .deb and install it.

---

