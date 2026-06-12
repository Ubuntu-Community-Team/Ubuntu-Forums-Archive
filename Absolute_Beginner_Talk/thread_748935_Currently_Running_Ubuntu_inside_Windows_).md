---
title: "Currently Running Ubuntu inside Windows :)"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by dreamerz679 on 2008-04-07
Hey everyone!

Let me start off by saying that I am generally pretty new to linux. I work with linux at work, but thats mainly just running scripts and doing some basic editing of config files through VI. I was talking with some people at work about running VMware and virtualization. I had also just put my new PC together and after figuring out that XP didn't like my raid 5 and having my dvdrw on Sata as well, I decided to go with Vista x64 just to get things running and to see how 64-bit development and support is going. (Just for everyone else's info. I haven't had a single problem as of yet, been running for 46 hours so far.) I started googling VMware and running Linux inside of windows and came upon this article that gives you step by step instructions on how to run a linux install from windows and run linux inside windows using free software. It was a LOT easier than I expected. This can be extremely handy, especially since right now I am running Ubuntu 8.04x64 inside Vista x64. Beta testing on a mass scale could become much easier. :)

Heres the link - 
[http://johnbokma.com/mexit/2005/11/07/vmware-player-ubuntu-installation.html](http://johnbokma.com/mexit/2005/11/07/vmware-player-ubuntu-installation.html)

The instructions I thought were pretty straight-forward, but there are a few things that I thought I should clarify....

1. Where the instructions tell you to create a virtual partition, Its actually a "virtual partition". IE. its a file. You don't need to format anything or create an actual partition. To Windows, it looks like a "File" and thats it.

2. Where it states to run this  command - c:\program files\qemu\qemu-img.exe create -f vmdk Ubuntu.vmdk 2G ---- The "2G" portion is the "virtual partition" size. I did mine as 15G to have room for other applications.

3. The file it tells you to make in notepad, the line --- ide:0.fileName = "ubuntu-5.10-install-i386.iso" --- you need to change that to whatever the ISO image name is that you downloaded. mine was ---  ide:0.fileName = "ubuntu-8.04-beta-desktop-amd64.iso" ---.

And as a last note, make sure everything is in the same folder, the ISO image and the two files you created. If you just follow the instructions its very easy. The install was flawless and without any problems at all. Kudos to the Ubuntu.

Hopefully this will help someone else as well.  ::cheers::

---

### Post by marine63 on 2008-04-07
:l everyone knows about this

---

### Post by Crafty Kisses on 2008-04-07
> **marine63 said:**
> :l everyone knows about this

Be nice, he's just trying to help. Thanks for the info man! Here at the Ubuntu Forums a lot of people know about this, so you may want to use the search option and see if anyone has posted a similar thread next time. :)

---

### Post by bodhi.zazen on 2008-04-08
dreamerz679: Welcome to the Ubuntu forums. Virtualization is exciting, thank you for your observations.

If you like qemu you might also enjoy VMWare or VirtualBox.

Let us know if we can be of further assistance.

---

### Post by keypox on 2008-04-08
i found it to run really slow though.... i have c2d at 3ghz used vmwares, vmplayer

---

### Post by marine63 on 2008-04-08
i know but i don't know how else to put it without insulting him :(
virtualbox works just as well and have a nicer interface

---

