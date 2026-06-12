---
title: "questions about Ubuntu install"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by leoliver on 2007-05-06
I'm a beginner with Linux. I have a Ubuntu 7.04 desktop CD, which I have been booting to , to learn about Linux.
 I have two questions to ask : 1st, is there any "learning exercises" I can use ( to further my Linux education) , while I'm booted to the CD, prior to installing Linux on my hard drive?
  2nd, I have one small Dell diagnostic partition, and the rest of my 80 gb. HD is all Windows. So during the Linux install, can the Dell partition be removed , by the Linux installer?
 And it looks like I have another question also, i have never created or deleted partitions. So what does reformatting a partition mean? If my Windows partition was re-formatted, would it be damaged or erased?
Or does re-formatting apply to "resizing" the free space before creating new partitions for Linux?
Feedback will be appreciated.

---

### Post by bobplano on 2007-05-06
i don't know about any exercises you can do to help you learn more about linux other than reading up on it. (like[http://www.psychocats.net/]("http://www.psychocats.net/")) all hard drives that are being used are in some kind of format. ext3 is the format used by linux, compared to ntfs by windows. fat32 is a less effiecent format, but both operating systems can read from it. reformatting a partition changes the format it is in (or you can just change it back to what is was before i.e. ext3 to ext3). this causes ALL information on the partitions to be erased. for ubuntu to be installed you don't have to reformat anything. when you get to the partition part of the install choose manual. then you can delete the smaller partition and resize the windows one, then make a /(root) swap and /home partitions, formatted to ext3. make sure your windows is defragged before doing that though, and you might want to backup your data.

---

### Post by Nekiruhs on 2007-05-06
For #2:
First let me define re-format. When you reformat a partition or hard-drive you are recreating the filesystem (Be it NTFS for windows or EXT3 for linux).  When you reformat a partition or Hard-Drive everything on that partition or hard-drive is lost. But, you can resize a partition (to make a long story short only the end can move not the beginning) with out harming it. So if you install Ubuntu to the diagnostic partition, All the data one the diagnostic partition will be lost.
<Edit>Darn you bobplano, you beat me to it. Lol</Edit>

---

### Post by Lucifiel on 2007-05-06
Here're some suggested pointers on what type of filesystem format to use for Linux. 

Either ext3 or fat32. 

A Fat32 partition can be recognised by both Windows and Linux. However, you might run into certain permission errors. 

When you want to first install Linux, you need to create:

- a swap partition. Recommended size is 200% of your RAM. Filesystem format: linux-swap

- root directory 
Filesystem format: ext3 

- it is also recommended to create a separate partition for your "home" directory. 
Filesystem format: ext3

---

### Post by notwen on 2007-05-06
> 1st, is there any "learning exercises" I can use ( to further my Linux education) , while I'm booted to the CD, prior to installing Linux on my hard drive?

Just keep exploring using the LiveCD, try to think of things you'll be using on a day-to-day basis web browsing, word processing, etc, this way you'll have an idea of of whats not working or behaving the way you're accustomed to.  I strongly recommend using the forums here for any issues you may run into, it just helps alot when you have an idea of what's going wrong or what's behaving differently.   If possible try to do some things using the terminal/command-line, sometime sin Linux you may find yourself in a situation where you'll have to use the command line to do something that's not possible using a GUI.  Small tasks such as copying, renaming, moving files in the terminal will help. Browsing all of your folders using the terminal.  Everything you can learn will help you tell us what's not working for you should you run into a problem.

> 2nd, I have one small Dell diagnostic partition, and the rest of my 80 gb. HD is all Windows. So during the Linux install, can the Dell partition be removed , by the Linux installer?
More than likely you'll end up just resizing your windows partition during your linux install, when you're ready, and Ubuntu will also install a boot-loader(GRUB) which will recognize your Windows partition and once all is done GRUB will give you the choice of booting Windows or Ubuntu at every startup.   Read over some other threads regarding dual-booting to get idea of what may be in store for you when you do decide to go ahead w/ the Ubuntu install.  

Don't rush yourself in installing as exploring the LiveCD can be very helpful in learning the whereabouts of assorted apps/utilities you'll need to know.  You could also browse the forums for threads that may be asking questions similar to issues/situations you may run into during your install.  I still browse the forums everyday for random things I may encounter somewhere down the road.  ubuntuforums.org make the saying "You learn something new everyday' very true to me at least. =p

---

### Post by mb01915 on 2007-05-06
I had an old e-Machine desktop that was misbehaving running XP Home.  Since it was an extra computer, I just blew windows off and installed Ubuntu.  Doing the same with a very old laptop.  So far so good.  I am afraid working with it is the only way to learn.

---

### Post by hyper_ch on 2007-05-06
And besides the forum here you also get excellent support in the irc channels :)

Server:
irc.freenode.org

Channels:
#ubuntu
#kubuntu
#xubuntu

---

