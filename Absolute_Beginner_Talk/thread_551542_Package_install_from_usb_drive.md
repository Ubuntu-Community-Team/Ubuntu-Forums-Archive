---
title: "Package install from usb drive"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by SunshineSmile on 2007-09-15
Where do I find instructions for downloading programs (using windows) to an external usb drive, and installing the packages from that drive? What are the commands I have to use, do I need to operate in the terminal, or can I add something in a synaptic menu, or the repository list? I am talking bout installing seperate programs, not an entire system.

---

### Post by Daveth on 2007-09-15
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

is your first port of call

---

### Post by SunshineSmile on 2007-09-15
That link didn't help me out much. I don't want to experiment with installing my system on a usb drive. I want to use my usb drive for installing additional packages, when I have no internet connection up and going. It is rather unpractical to drag my old desktop around the house to get a cable connection in order to download build-essential, ndiswrapper, and whatever I need to get my WiFi card up and going. So when double booting windows and ubuntu, I want to download all packages I need to my external drive, or an internal drive visible by both OS, and then install the packages from there. 

So Q is: 
- Where to get the packages
- Can I download whole repositories?
- What do I need to type to install the packages from a drive?

---

### Post by benerivo on 2007-09-15
> So Q is:
- Where to get the packages
- Can I download whole repositories?
- What do I need to type to install the packages from a drive?

Packages from [here]("http://archive.ubuntu.com/ubuntu/pool/"), and [here]("http://packages.ubuntu.com/") and also individual ones all over the internet if they are not part of the current Ubuntu repositories.

You may be able to find a program on windows that downloads the contents of web sites, so you could try that on the above links.

You need the gdebi package installer, which is part of the standard Ubuntu installation. From Ubuntu, you can then right click on a .deb file and choose 'install' from the context menu.

If you put them on a CD, then you can use the option in Synaptic to add the CD as a repository. The Help file in Synaptic says you can add a hard drive location as a repository, but i've never worked out how.

---

### Post by SunshineSmile on 2007-09-15
Thanks a lot. 

Now when I download ndiswrapper.deb, all I have to do is to get into the folder with the downloaded file and  [sudo dpkg -i ndiswrapper.deb] to install it, right?

What do I do when I download a tar.gz file? Does that involve typing make in the folder with the makefile?  Have I got it right that I need build-essential to be able to use the command make, together with the kernel-headers?

---

### Post by Daveth on 2007-09-15
apologies- I misread your post

---

### Post by benerivo on 2007-09-15
> **SunshineSmile said:**
> Thanks a lot. 

Now when I download ndiswrapper.deb, all I have to do is to get into the folder with the downloaded file and  [sudo dpkg -i ndiswrapper.deb] to install it, right?

What do I do when I download a tar.gz file? Does that involve typing make in the folder with the makefile?  Have I got it right that I need build-essential to be able to use the command make, together with the kernel-headers?

Yes to both, although installing .tar.gz's using make, hasn't work every time for me in the past. From memory i'm sure you're right about needing both build-essential and the headers in order to compile one.

---

### Post by SunshineSmile on 2007-09-15
I need more help.

I wanted to download ndiswrapper to install my native windows drivers.

But ndiswrapper -i tells me that I need ndiswrapper-utils.

After some searching, I found a .deb file for ndiswrapper-utils. But the deb file won't install, coz I am missing libc6 !!!!! 

So then I try to find libc6.deb, but I can't find a deb file anywhere, and on packages.ubuntu.com, they only let me download tar.gz files. :confused:

This is where the problem begins, because I don't know how to install anything with tar.gz files.

I installed a version of build-essential.deb, but after a lot of tar -xvfz and -xvf I end up with a bunch of files from the libc6 tar.gz, and I have no god damn idea what I should do to get it installed. 

Searching for make only leads me to programming sites. 

What do I have to do? Getting an internet-connection is pretty much one of the first things a n00b gotta do, and this doesn't seem to get me anywhere...

---

### Post by chessercizes on 2007-09-15
hey

i don't know if this is actually libc6, but see if this is what you need:

[http://packages.ubuntu.com/feisty/libs/libapt-rpm-pkg-libc6.3-6-2]("http://packages.ubuntu.com/feisty/libs/libapt-rpm-pkg-libc6.3-6-2")

---

### Post by logos34 on 2007-09-15
Personally I'd download the [Ubuntu DVD]("http://www.ubuntu.com/getubuntu/downloadmirrors").  4 gigs.  Hopefully it'll have all or most of the dependencies you need.

---

