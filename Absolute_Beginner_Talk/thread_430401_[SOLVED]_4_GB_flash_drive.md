---
title: "[SOLVED] 4 GB flash drive????"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by john3347 on 2007-05-02
I want to get my feet wet with a linux OS (probably ubuntu).  I have several year's experience working with Windows all the way back to Windows 3.11, but I am only at some intermediate level of competency and may not have the general knowledge to learn and live with linux.  I am under the impression that it requires a skill level approximately equal to DOS prior to windows.  Can I install the entire system on a 4 GB USB Flash Drive and use the flash drive as a hard drive partition?  I just don't know what kind of learning curve I may be in for and don't want to risk everything on my hard drive by creating a partition and maybe screwing something up in doing so.

---

### Post by mikeyphi on 2007-05-02
Presumably you have windows at the moment......if you have the windows install CD there should be no risk to your current system if you also install Ubuntu on the same drive (given enough spare space).
The Ubuntu install will offer/take care of partitions and will overwrite the MBR with the Grub - giving you an option at power on to boot into either system.
If at a later stage you choose to remove Ubuntu you will only need to run your windows Cd in recovery mode and, at a command line, type 'fixmbr'

The above option will be the easier initial setup - you will then be able to explore/learn and change things if required.

---

### Post by darkrose on 2007-05-02
Installing to a usb flash drive is tricky, but it can be done. There is a howto for it at [http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar)

You will need to boot to the ubuntu live cd to follow the howto.

---

### Post by TheMono on 2007-05-02
In shot, you can do what you want to do, but it is not easy. 

The learning curve aint so bad at all though, nothing like using DOS!

Don't be afraid to learn new things, but it certainly isn't hard - AS LONG as your hardware plays nicely with it. If you want to post your hardware brands and models we'd be happy to let you know what the odds of a problem are.

---

### Post by Angry_Man on 2007-05-02
Should be possible, but 4GB is a little tight, particularly if you want to install some extra packages. The default installation requires at least 2GB. Also make sure that you're using a USB2.0 port, or it's going to be unbearably slow. Also, you can try a lot of features just by booting from the Ubuntu Live CD, something you're going to have to do to install anyway.

If you still want to go ahead, you should find this helpful:

[http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/](http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/)
(ingnore the fact that this was a hard drive, your flash drive is just a smaller USB Mass Storage device)

---

### Post by john3347 on 2008-01-31
Thanks to all of you who have responded to this post.  It was posted several months ago and I have made an effort a few times since to get a Linux OS installed in some form.  I have so far been unsuccessful.  My eventual goal is to assemble a totally no-cost software computer.  I still haven't even accomplished getting the OS installed.  I am currently attempting this on a computer with a Celeron D Processor, 1 GB ram, an unpartitioned 160 GB hard drive (containing Windows XP Pro), and a second 80 GB hard drive with 3 partitions onto which I now think I want to install Ubuntu 7.10 and, at some later date, remove Windows [and possibly the 160 GB hard drive] entirely from that computer.  [I have other computers for critical use while I experiment with this one.]

Any suggestions anyone?  

Thank you.
John

---

### Post by philinux on 2008-01-31
These are useful guides there are many others.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

[http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon](http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon)

---

### Post by lemon_duck on 2008-01-31
[SIZE="4"]A word of encouragement!

I installed Ubuntu last weekend. I also made the mistake of not reading the instructions thoroughly and deleted XP at the same time. Turned out to be a good thing. I can still use XP on the Tablet but I'm compelled to persevere with Ubuntu when using the Desktop.

A more helpful and friendly group of users cannot be believed. Problems you imagined you had turn out to be mostly that, imagination. 

And you get the most pleasant surprises. The printer I could never get to work on XP via USB was 'seen' and uprunning in moments. 

Don't worry about the learning curve either. Like yourself I've experienced most Windows emanations as well as Assembly Language and Basic and GEM since 1978. Ubuntu is certainly efficient and even with the little I've learned my appetite has been whetted for more. There are folk in the forums who will 'talk' you through solving the things you find  difficult at first.

Go for it!!!:guitar:[/SIZE]

---

### Post by john3347 on 2008-02-16
I would love to find these people that lemon_duck speaks of.  I did get very helpful responses to my first couple of posts, then it is as though I have terrible bad breath or something.  Is there some kind of unwritten limit of two questions or some such?

---

### Post by dansco on 2008-02-16
Another good resource for usb linux is

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

i found it very helpful

bad me missed the solved bit

---

### Post by skymera on 2008-02-16
i wouldnt install ubuntu.

it will be slow, very slow from a usb.

i installed Damn Small Linux on my flash drive and works great

---

### Post by An_Dynas on 2008-02-16
Puppy Linux also works extremely well from a flash drive.  It's a little too cutesy for some but it's a tremendously effective distro, particularly given its size.  Very accommodating for newbies, too.

---

### Post by MasterJS on 2008-02-16
I installed Xubuntu onto an external hard drive and have had it up and running nicely. I would recommend looking at the sites a few of the other posters have placed, especially the one from pendrivelinux. My blog listed in my signature at the bottom of my post includes how I installed Xubuntu.

---

### Post by john3347 on 2008-02-27
Decided against trying to do the USB drive thing and I installed an 80 GB second harddrive for the Ubuntu drive.  I got the OS installed, but I just had a bigger truckload of problems that I couldn't get figured out than the size truck I had, so I gave up and I'll have to live with Micro$oft for a while yet.  Maybe some developer will come along with an OS for the person who wants to use their computer FOR a project and not AS the project.:confused:

---

