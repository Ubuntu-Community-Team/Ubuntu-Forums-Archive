---
title: "HFS+ volume troubles"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by mcphilip on 2007-02-09
I am currently having trouble installing the latest version of the Ubuntu OS I think because the hard drive is formatted as one partition as an Apple HFS+ volume.
How can I install Ubuntu *without* removing everything from the hard drive? I have a lot of proprietary software that I will continue to need.

Matt

---

### Post by mikewhatever on 2007-02-09
Hi,
I am not familiar with Apple PCs, and perhaps that's why I don't understand what the problem is. You are saying that you're having troubles installing. What kind of troubles? Are there any error messages? Does the process stop, if so, at what stage? Tell us anything you can think of. Perhaps you will find [This Guide](https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/index.html) useful.

---

### Post by rccharles on 2007-02-09
> **mcphilip said:**
> 
How can I install Ubuntu *without* removing everything from the hard drive? I have a lot of proprietary software that I will continue to need.

I'd suggest you backup anything you want.  A few people make mistakes.

You need some unallocated partition space.  If you have an intel mac, you can use bootcamp to resize your mac partition.  


For use to see what your harddrive looks like...
In the Mac OS terminal, ( applications > utilities > terminal ) run the command:

sudo pdisk -l

enter your logon password here.

copy and past the output here.

To place the output in a file do:

cd ~

sudo pdisk -l >seepdisk


Robert

---

### Post by mcphilip on 2007-02-10
The exact problem I am having is that this pre-intel PowerBook G4's hard drive is formatted as HFS+ rather than Unix, why I am not really sure, I inherited this computer. The problem I am begins at the point in the installation where the installer gives you 3 options to choose from when setting up partitions on the disk: use available free space, manual partitioning, and the first option, the first option to me begins with the words "Erase Disk..." and therefore I went with the second option. After exiting that part of the installer to begin the actual installation of the OS, then an error message comes up telling me that partitions were not allocated properly. From what I have heard from those who have slightly more experience with Ubuntu and Unix systems on the whole tell me that probably it is the HFS+ partitioning that is causing this. I tried that
sudo pdisk -| thing and it didn't work for me, but I presume that it will not tell me THAT much more than disk utility. Perhaps if I restart from the Mac OS Tiger and repartition the disk apporpriately I will not have to reformat and erase (I simply hope that repartitioning will not erase my data, though Apple's stuff usually has quite a few warning messages in big friendly letters telling me before I do).

---

### Post by mcphilip on 2007-02-10
wait, got that seepdisk thingy to work, thanks. 
Partition map (with 512 byte blocks) on '/dev/rdisk0'
 #:                type name        length   base      ( size )
 1: Apple_partition_map Apple           63 @ 1        
 2:          Apple_Free Extra       262144 @ 64        (128.0M)
 3:           Apple_HFS Untitled 156039270 @ 262208    ( 74.4G)
 4:          Apple_Free Extra           10 @ 156301478

Device block size=512, Number of Blocks=156301488 (74.5G)
DeviceType=0x0, DeviceId=0x0

---

### Post by rccharles on 2007-02-10
> **mcphilip said:**
> 

 3:           Apple_HFS Untitled 156039270 @ 262208    ( 74.4G)
 
Device block size=512, Number of Blocks=156301488 (74.5G)


Ok, you have a 74.5g disk ( probably sold as a 80g disk ).  You have 74.4gig allocated to Mac OS X.  You need to resize the disk or backup and restore to a smaller partition.  

Here is a thread on resizing a Mac OS partition.  I recommend backing up your data.


---------------------


The Fink project wants to bring the full world of Unix Open Source software to Darwin and Mac OS X. We modify Unix software so that it compiles and runs on Mac OS X ("port" it) and make it available for download as a coherent distribution. Fink uses Debian tools like dpkg and apt-get to provide powerful binary package management. You can choose whether you want to download precompiled binary packages or build everything from source.

"The database was last updated at 00:09 GMT on Tuesday, January 23 and currently lists 7575 packages in 24 sections. See:
[http://fink.sourceforge.net/](http://fink.sourceforge.net/)
[http://pdb.finkproject.org/pdb/index.php?phpLang=en](http://pdb.finkproject.org/pdb/index.php?phpLang=en)


Robert

---

