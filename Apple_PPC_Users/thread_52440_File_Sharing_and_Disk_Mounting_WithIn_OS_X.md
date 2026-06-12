---
title: "File Sharing and Disk Mounting With/In OS X"
date: 2005-07-27
forum: Apple PPC Users
---

### Post by MinutiaeMan on 2005-07-27
I'm having a problem (actually, two problems) with configuring Ubuntu to play nice with OS X on the same iBook.

(1) I've got Panther installed on one partition, and told the Apple Disk Utility to leave the rest of the drive as "free space". When I installed Ubuntu, I just let it do what it needed to with the remainder of the drive. But I'd assumed that OS X would be able to see/mount the Ubuntu partition -- but it can't. Is there any way that I can get OS X to see the partition, or would that require me to reformat the partition?

(2) Can someone point me in the direction of some decent instructions for enabling file sharing? I got as far as installing portmap, but couldn't figure out what the heck I was supposed to do with the rest of the instructions. (This is the kind of thing that keeps Linux from the real mainstream, unfortunately -- it's still rare to be able to push a button and have it "just work". :?) All I want to be able to do is have some basic file transfer ability so I can move stuff over the home wireless network from one of my Macs.

Thanks in advance!

---

### Post by craks on 2005-07-27
for your first question, if you use ext2/3 for your ubuntu, this will conform to your need:

[http://sourceforge.net/projects/macext2fs/](http://sourceforge.net/projects/macext2fs/)

second question, use smbfs or ftp

---

### Post by zxee on 2005-07-28
[QUOTE=craks]for your first question, if you use ext2/3 for your ubuntu, this will conform to your need:

[http://sourceforge.net/projects/macext2fs/](http://sourceforge.net/projects/macext2fs/)

second question, use smbfs or ftp[/QUOTE]

Am I missing something here? From the sourceforge page : 
"This Project Has Not Released Any Files" so ext3 fs for mac isn't!
So MinutiaeMan might be better served if he tries to create a hfs (NOT hfs+ also called mac extended) that both linux and OSX can read/write. 
I've heard this can be done by creating a dos partiton also but I haven't succeeded in doing it using dos.
MinutiaeMan if you don't want to re-partiton i.e wipe your entire drive again-and I don't blame you since pc users don't have to do that-then you might want to get prosofts drive genius
[http://eshop.macsales.com/item/Prosoft%20Engineering/23100/](http://eshop.macsales.com/item/Prosoft%20Engineering/23100/)
Hope this is helpful.
Added later: checking drive genius' specs it may not work to create an hfs partiton. Perhaps you can resize and create a partition for sharing between osx and ubuntu with parted [http://www.gnu.org/software/parted/manual/html_mono/parted.html](http://www.gnu.org/software/parted/manual/html_mono/parted.html)
Or you can use a usb thumb drive-not exactly a convient solution though.

---

### Post by autocrosser on 2005-07-31
OK--to "see" your linux partitions in OSX requires a small freeware program called Ext2FS--it installs as a control panel & allows mount of all your Linux drive(s)--you can unmount & remount them with a couple of mouse clicks--I found it on VersionTracker.com--The link is  

[http://www.versiontracker.com/dyn/moreinfo/macosx/18619](http://www.versiontracker.com/dyn/moreinfo/macosx/18619)

As for file sharing--I Set my "Shared" folder with full permission (everyone allowed)--Lastly--I edited my /etc/fstab to allow mounting my OSX drive(s)--this will create a /mnt directory in your / directory--make sure to mkdir /dev/whatever it is & mkdir /mnt/the name of whatever (done as su or sudo in a terminal)

This allows you to "swap" between your two OS's--I have mutiple drives, so my "extra" drives have had the permissions set to "no ownership"--so. the whole drive becomes a swap drive--

Any other questions---just ask-- I may not have the answers, but I'll try to point you the right way :wink:

---

### Post by zxee on 2005-08-01
[QUOTE=autocrosser]OK--to "see" your linux partitions in OSX requires a small freeware program called Ext2FS--it installs as a control panel & allows mount of all your Linux drive(s)--you can unmount & remount them with a couple of mouse clicks--I found it on VersionTracker.com--The link is  

[http://www.versiontracker.com/dyn/moreinfo/macosx/18619](http://www.versiontracker.com/dyn/moreinfo/macosx/18619)

As for file sharing--I Set my "Shared" folder with full permission (everyone allowed)--Lastly--I edited my /etc/fstab to allow mounting my OSX drive(s)--this will create a /mnt directory in your / directory--make sure to mkdir /dev/whatever it is & mkdir /mnt/the name of whatever (done as su or sudo in a terminal)

This allows you to "swap" between your two OS's--I have mutiple drives, so my "extra" drives have had the permissions set to "no ownership"--so. the whole drive becomes a swap drive--

Any other questions---just ask-- I may not have the answers, but I'll try to point you the right way :wink:[/QUOTE]

Thanks autocrosser, I will check out that freeware program. My problem is similar to the orginal post. When I partitioned to install hoary I created 4 partitons plus swap. One has OS9, OSX another, 6GB partition for ubuntu, and then a 13Gb fat32 partition that I mounted as dos. Ubuntu sees the dos partition but I don't know how to mount it in OSX. 
Here's my fstab in OSX 
# fs_spec                                    fs_file  fs_vfstype  fs_mntops
#
# UUID=DF000C7E-AE0C-3B15-B730-DFD2EF15CB91  /export  ufs         ro
# UUID=FAB060E9-79F7-33FF-BE85-E1D3ABD3EDEA  none     hfs         rw,noauto
# LABEL=This\040Is\040The\040Volume\040Name  none     msdos        ro

Is there a better way to do this and/or what should my fstab ( in OSX ) look like to get the dos partiton to auto mount? Thanks

---

### Post by autocrosser on 2005-08-02
I went to Apple tech support & it refered me to these articles--

[http://docs.info.apple.com/article.html?artnum=106471](http://docs.info.apple.com/article.html?artnum=106471)

[http://docs.info.apple.com/article.html?artnum=107483](http://docs.info.apple.com/article.html?artnum=107483)
(take a look at the bottom of this article)

[http://docs.info.apple.com/article.html?artnum=106660](http://docs.info.apple.com/article.html?artnum=106660)

[http://docs.info.apple.com/article.html?artnum=106568](http://docs.info.apple.com/article.html?artnum=106568)

[http://docs.info.apple.com/article.html?artnum=25344](http://docs.info.apple.com/article.html?artnum=25344)  
(take a look at the bottom of this article)

I would think these might give you a way into it--You can search Apple Tech yourself--the only problem is that they don't make it very "friendly" for non-tech support people to use it :-x 

If you have a problem with getting to these, I can send them via email---

Luck to you!!!

---

### Post by craks on 2005-08-02
[QUOTE=zxee]Am I missing something here? From the sourceforge page : 
"This Project Has Not Released Any Files" so ext3 fs for mac isn't!
So MinutiaeMan might be better served if he tries to create a hfs (NOT hfs+ also called mac extended) that both linux and OSX can read/write. 
I've heard this can be done by creating a dos partiton also but I haven't succeeded in doing it using dos.
MinutiaeMan if you don't want to re-partiton i.e wipe your entire drive again-and I don't blame you since pc users don't have to do that-then you might want to get prosofts drive genius
[http://eshop.macsales.com/item/Prosoft%20Engineering/23100/](http://eshop.macsales.com/item/Prosoft%20Engineering/23100/)
Hope this is helpful.
Added later: checking drive genius' specs it may not work to create an hfs partiton. Perhaps you can resize and create a partition for sharing between osx and ubuntu with parted [http://www.gnu.org/software/parted/manual/html_mono/parted.html](http://www.gnu.org/software/parted/manual/html_mono/parted.html)
Or you can use a usb thumb drive-not exactly a convient solution though.[/QUOTE]

so sorry for my mistake, it's:
[http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/)

i have used under 10.3 panther, it's ok for mounting ext2/3 of linux partitions, but not tested under 10.4 tiger, for i use reserfs under ubuntu

---

### Post by calum on 2005-08-02
[QUOTE=craks]so sorry for my mistake, it's:
[http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/)

i have used under 10.3 panther, it's ok for mounting ext2/3 of linux partitions, but not tested under 10.4 tiger, for i use reserfs under ubuntu[/QUOTE]

ext2fsx definitely doesn't work under Tiger, FWIW.
[http://sourceforge.net/forum/forum.php?forum_id=474630](http://sourceforge.net/forum/forum.php?forum_id=474630)

---

