---
title: "Help setting up a files erver"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by banditv1 on 2007-03-30
Hello,
Over the years I have gathered a large amount of data I would like to keep. I am tired of burning DVDs so I decided to setup a linux file server. However I am fairly new to linux. I have decided to try Ubuntu 6.10 for the file server. Many people have told me Ubuntu has one the best communities on the Internet, so that is why I chose Ubuntu. This will be the largest linux undertaking for me. So here is what I am trying to find, a well detailed how too on setting up a file server. Something that will explain things like how to partition the hard drives correctly ( I will have three installed )  on up to the more complex settings. I am currently at step 1 downloading the ISO. 

Thank you in advance for your time and any help you may provide.

---

### Post by rich.bradshaw on 2007-03-30
What exactly do you want it to do?

There are different protocols for sharing files over the internet such as ftp, ssh, nfs, samba etc. You should probably give a quick wikipedia trip for each of those.

I tend to use ssh as it is secure and can be used from any computer on the internet.

Are you planning to share with Windows computers, or just Linux? Are you just worried about sharing on a LAN, or over the internet in general?

How often are you going to use it? Do you need different areas to be password protected etc?

If you are worried about partitioning I would do it like this:

1st drive

3-6 GB for ubuntu install. ext3
around 1-2 times the amount of Ram you have. Linux-swap
rest of drive ext3

2nd/3rd drives completely ext3.

This is assuming that you don't have anything on them already. Fat32 will do on drives 2 and 3 if you have been using them with Windows already and don't want to erase everything. Ubuntu shouldn't be installed itself onto fat32 though.

Once it Ubuntu is installed, check you can access the drives using the Computer link in the menus. If you need to format them from Ubuntu, use gparted.

Then look at using ftp/samba/ssh etc. Samba is best for sharing with Windows PCs on a Lan. Ftp is good for anonymous access over the interner. SSH/sftp is best for secure access.

Read up on webmin, I hear that it is good for setting the file sharing stuff up.

Good Luck! post here if you have any immediate questions!

---

### Post by banditv1 on 2007-03-30
Thank you for you reply.  FTP would likely be the simplest thing to do I think. Yes I will have windows pcs on the network. I would like to be able to use ssh to log in and send files with the windows ssh program putty. Lastly I would like to be able to share over the internet as well as lan

Thanks for your time and help

---

### Post by rich.bradshaw on 2007-03-30
I have just had a look at webmin, a package designed to set all this up and make it simple, it seems pretty good and has lots of options.

Once you have got everything installed do

sudo aptitude install webmin

then from any computer on your network (including the Ubuntu one you just installed it on) type

[https://ipofthatcomputer:10000](https://ipofthatcomputer:10000)

into the address bar in Firefox/IE etc.

(if you need to know the IP of the computer, type ifconfig in a terminal and look for the ip address)

Log in with your username on that computer and there are ots of things to set up.

Samba for inside LAN

Putty and WinSCP + SSH for over the internet.

Remember that if you want to access over the internet you need to forward ports from your router to your PC. SSH is port 22.

---

### Post by rich.bradshaw on 2007-03-30
How far have you got by the way?

---

### Post by banditv1 on 2007-03-30
Currently I have finished installing Ubuntu and am trying to figure out why my extra hard drives are not listed in computer but are listed in the device manager window.

---

### Post by Zuuswa on 2007-03-30
can you display the contents of /etc/fstab ??  we might be able to help you more with that info.

---

### Post by banditv1 on 2007-03-30
My fstab file

My extra hard drive names are hdb and hdd

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=db67fcbc-5f59-4059-83a6-1321effb80ab /               ext3   
defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=ba010dd0-b2b3-4db6-8a7a-9172ce671634 none            swap    sw      
       0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by banditv1 on 2007-03-30
I am also having a problem installing the webmin. When I run the command I get and error message saying that a package of the name could not be found.

---

### Post by dca on 2007-03-30
I think it's in one of the repos not active by default:

edit the /etc/apt/sources.lst file or use:  System -> Synaptic -> Settings -> Repositories
 
 
If I remember correctly I think I got it from here:
[http://www.webmin.com/download.html](http://www.webmin.com/download.html)

---

### Post by banditv1 on 2007-03-30
I went to the website and downloaded the webmin_1.330_all.deb which is the one recommended for Ubuntu. I get this error when I try to install it. Error Dependency is not satisfiable: libauthen-pam-perl

Thanks for the reply

---

### Post by Origin415 on 2007-03-31
If you aren't using apt's repositories, you must get all dependencies beforehand manually.

sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl

will take care of them for webmin.

---

