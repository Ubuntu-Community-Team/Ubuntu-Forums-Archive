---
title: "How to choose where programs are installed"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by dwally89 on 2008-04-09
Hi,

How can I choose where programs are installed when I install them, as my main partition is getting full, but I have other partitions that have plenty of free space, so how can I install programs onto those partitions instead of the main/default one?


Thanks

---

### Post by billgoldberg on 2008-04-09
I would also like to know how you could tell apt-get (and synaptic) to tell where to download files to.

I suppose just coping their folders to another partition wouldn't work?

---

### Post by dwally89 on 2008-04-09
But surely that'd break shortcuts etc?

---

### Post by philinux on 2008-04-09
First thing to try is to cleanup apt-get. sudo apt-get any from below. From man apt-get.

      clean
           clean clears out the local repository of retrieved package files.
           It removes everything but the lock file from
           /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When
           APT is used as a dselect(8) method, clean is run automatically.
           Those who do not use dselect will likely want to run apt-get clean
           from time to time to free up disk space.

       autoclean
           Like clean, autoclean clears out the local repository of retrieved
           package files. The difference is that it only removes package files
           that can no longer be downloaded, and are largely useless. This
           allows a cache to be maintained over a long period without it
           growing out of control. The configuration option
           APT::Clean-Installed will prevent installed packages from being
           erased if it is set to off.

       autoremove
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for some package and that are no
           more needed.

The other would be to empty /root/.Trash

Finally resize your partitions.

---

### Post by dwally89 on 2008-04-09
Thanks :-)

---

### Post by prshah on 2008-04-09
> **dwally89 said:**
> Hi,
How can I choose where programs are installed when I install them, as my main partition is getting full, but I have other partitions that have plenty of free space, so how can I install programs onto those partitions instead of the main/default one?


Why not just resize your partitions to make better use of available space?

---

### Post by dwally89 on 2008-04-09
Is it not dangerous to resize partitions though? Can't data be lost when doing so?

---

### Post by lackofcreativity on 2008-04-09
> **dwally89 said:**
> Is it not dangerous to resize partitions though? Can't data be lost when doing so?

I've heard stories of people killing Ubuntu doing this, but even with a 75% full hard drive, I've never actually had trouble with it.

---

### Post by dwally89 on 2008-04-09
K Thanks.

I'll leave it for the mo.

---

### Post by stchman on 2008-04-09
> **dwally89 said:**
> Hi,

How can I choose where programs are installed when I install them, as my main partition is getting full, but I have other partitions that have plenty of free space, so how can I install programs onto those partitions instead of the main/default one?


Thanks

How big is your Ubuntu partition?  I have mine set to 20GB and I have used maybe 4GB at most.  Ubuntu is a very streamlined OS and therefore does not take up a lot of room.

I do however not use /home for storage of my personal data.  I recommend a partition for Ubuntu and have another partition for your personal stuff.

---

### Post by dwally89 on 2008-04-09
My Ubuntu partition is 10GB, and i have a 60GB Data partition, however by default programs are installed on the Ubuntu partition which is getting full (am currently using 8.12GB).

So is it possible for me to install programs on the Data partition?

Thanks

---

### Post by stchman on 2008-04-09
> **dwally89 said:**
> My Ubuntu partition is 10GB, and i have a 60GB Data partition, however by default programs are installed on the Ubuntu partition which is getting full (am currently using 8.12GB).

So is it possible for me to install programs on the Data partition?

Thanks

I don't believe you can have Synaptic install the programs to a different location.

You can use the LiveCD to resize your Ubuntu partition and decrease the data partition size.

Are you using a lot of space in your /home folder?  As I said I have a ton of programs installed and I use up about 4GB.  You may also need to clean your Ubuntu installation.  You may have a lot of packages cached.

[http://www.stchman.com/cleanup.html](http://www.stchman.com/cleanup.html)

---

### Post by dwally89 on 2008-04-09
Am using 2.1GB in my home folder, 1.5GB of which is WINE.

---

### Post by wawadave on 2008-04-09
how and where would be the best way to resize partitions?(newby)

---

### Post by dwally89 on 2008-04-09
Get gparted, really good program.

---

### Post by Tatty on 2008-04-09
> **wawadave said:**
> how and where would be the best way to resize partitions?(newby)

Gparted is in the repos.  But if you alter the partitions on a drive, then that drive has to be unmounted.  So if you want to edit the partitions on the drive you boot from, then you will need to boot to a live CD first

The Ubuntu livecd has gparted installed by default - i think its System->Administration->Gnome Partition Manager, or something like that.

---

### Post by bodhi.zazen on 2008-04-09
Partitions should be managed via a live CD. Resizing a partition can lead to data loss, but it is rare. You should back up your data first.

Hmm 10 Gb is a lot of applications, are you sure the space is not taken by data or files in Trash ?

Lasy, you can install into an alternate location with chroot. This is fairly standard and for example you can install a 32 bit chroot on a 64 bit os ...

[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

Run X apps :

[http://www.gelato.unsw.edu.au/IA64wiki/XinChroot](http://www.gelato.unsw.edu.au/IA64wiki/XinChroot)

[http://wiki.mandriva.com/en/Development/Howto/Chroot](http://wiki.mandriva.com/en/Development/Howto/Chroot)

---

### Post by dwally89 on 2008-04-09
> 
Partitions should be managed via a live CD. Resizing a partition can lead to data loss, but it is rare. You should back up your data first.

Hmm 10 Gb is a lot of applications, are you sure the space is not taken by data or files in Trash ?

Lasy, you can install into an alternate location with chroot. This is fairly standard and for example you can install a 32 bit chroot on a 64 bit os ...

[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

Run X apps :

[http://www.gelato.unsw.edu.au/IA64wiki/XinChroot](http://www.gelato.unsw.edu.au/IA64wiki/XinChroot)

[http://wiki.mandriva.com/en/Development/Howto/Chroot](http://wiki.mandriva.com/en/Development/Howto/Chroot)


I've just had a look at those four links and I don't really understand them.

Is there not an easy way to choose where the program is installed when installing it?

---

### Post by bodhi.zazen on 2008-04-09
> **dwally89 said:**
> I've just had a look at those four links and I don't really understand them.

Is there not an easy way to choose where the program is installed when installing it?

No there is no "easy way". But chroot is not all that hard either ...

---

### Post by dwally89 on 2008-04-09
Could someone please give me a brief explanation of what chroot is?

Thanks

---

### Post by wawadave on 2008-04-09
thx for the advice on gpart!

---

### Post by scragar on 2008-04-09
It **ch**anges the **root** (root as in folder, not user) temperarily(usualy for a single command). This means another folder may be used to install things into without messing with shortcuts. The problem as I see it is the lack of required directory structure on the partition you want to install things to(although I should think apt-get would fix that).

---

### Post by dwally89 on 2008-04-09
Thanks

I'll read it into it

---

### Post by bodhi.zazen on 2008-04-09
chroot is an alternate root or /

If you follow the link I gave you for the ubuntu wiki you will would install a MINIMAL ubuntu system in to an alternate location.

You then

sudo chroot /new/location /bin/bash

You are now in the chroot and can install applications from the command line

apt-get install foo

installs foo

The other link explains how to run graphical apps.

If you multiboot, you can say run Fedora application within Ubuntu without having to reboot. Sorry, Microsoft does not support chroot.

OpenVZ is one method of expanding on a chroot to achive virtualization

[http://openvz.org/](http://openvz.org/)

---

### Post by dwally89 on 2008-04-09
Thanks :-)

---

### Post by bodhi.zazen on 2008-04-09
> **scragar said:**
> It **ch**anges the **root** (root as in folder, not user) temperarily(usualy for a single command). This means another folder may be used to install things into without messing with shortcuts. The problem as I see it is the lack of required directory structure on the partition you want to install things to(although I should think apt-get would fix that).

If you are interested, look at the first two links I gave ...

---

### Post by philinux on 2008-04-10
From what I've read on here, most peoples root is about 4 gig. 

How come you got 8 gigs worth in there? Worth investigating this.

---

