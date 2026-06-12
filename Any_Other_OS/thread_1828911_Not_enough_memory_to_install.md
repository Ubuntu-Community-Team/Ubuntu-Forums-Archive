---
title: "Not enough memory to install"
date: 2011-08-19
forum: Any Other OS
---

### Post by Linux_junkie on 2011-08-19
I have an old Dell Optiplex 170L mini tower pc with 256MB of RAM and 40GB hard disk.  A while ago I downloaded Fedora 15 LXDE to install on this machine.

Yesterday decided to start installing Fedora 15 on to this machine.  I booted the computer up from the live CD that I created and whilst displaying the boot menu was a bit disappointed that there wasn't an option to boot from the menu.  I had to load the OS from the CD then once loaded had to click the 'Install to Hard Disk' icon to install it on the computer.

Considering that this distribution was using LXDE and the desktop is designed for computers with low resources (i.e. not enough memory to run Gnome / KDE) I thought it would fit nicely on to the Dell computer.  How wrong I was, no sooner had I ran the installation app from the desktop than a warning message popped up telling me that I needed a minimum memory of 640MB to install it.  So I gave up.

I also had a copy of Lubuntu 11.04 and Mint 10 (LXDE) and tried both of these disks only to find that on both occasions during the installation process both had crashed and therefore I was unable to complete the installation.

I was getting desperate at this stage so I inserted a DVD I got with a magazine and began to install Debian 6 choosing the text based option from the boot menu.  After going through the various options Debian was installed on the computer.  However, upon logging in to it discovered that it has only installed a basic system.  I would need to get access to the internet from this machine to download and install other apps that I would like to use.  There is a problem connecting to the internet because it hasn't installed Network Manager and I've been using this app to set up my mobile broadband device so that I can connect to the internet but without it I cannot connect.

I am now deciding whether I can download an alternative copy of Fedora for text based installation or simply download the Debian packages I want through my Ubuntu laptop and install them from a USB memory stick.  

I'd like some opinions on what I should do please?

---

### Post by MG&amp;TL on 2011-08-19
Lubuntu (an Ubuntu variant with LXDE) works fine on my 256Mb Dell. So does X- and U- buntu, actually. The Debian install is a nightmare. If you're going to install package files from USB, be aware that it won't mount them automatically. you'll probably need to edit /etc/fstab.

Mint LXDE also works-is the memory installed and workking correctly on your computer?

---

### Post by Linux_junkie on 2011-08-19
As far as I know the memory is working fine.  I had the same problem with Lubuntu 10.10 in that during the installation it crashed and at that time I also had Ubuntu and Xubuntu 10.10 and installed Xubuntu 10.10 with no issues.

Looks like I'll be going back to Xubuntu but using 11.04.

---

### Post by wojox on 2011-08-19
[Fedora 15 Net Install]("http://ftp.jaist.ac.jp/pub/Linux/Fedora/releases/15/Fedora/i386/iso/")

---

### Post by Linux_junkie on 2011-08-19
> **wojox said:**
> [Fedora 15 Net Install]("http://ftp.jaist.ac.jp/pub/Linux/Fedora/releases/15/Fedora/i386/iso/")

Won't I need access to internet to download other apps?  Unless I can setup mobile broadband device during installation won't be able to do it this way.

---

### Post by mikewhatever on 2011-08-19
Debian installation CD/DVD should have an option to install Gnome Desktop, including the Network Manager.
The original problem was caused by you trying to use a Live CD. Live CDs run entirely from RAM + the installer need some to work, and 256MB is not enough for any Live CD with a full Desktop Environment.

---

### Post by drawkcab on 2011-08-19
Yeah, I would give up on the graphic installation and you might have more success.  Install Lubuntu or crunchbang w/out the graphical installer and you'll probably off to the races.

---

### Post by wojox on 2011-08-19
> **Linux_junkie said:**
> Won't I need access to internet to download other apps?  Unless I can setup mobile broadband device during installation won't be able to do it this way.

Your probably going to have problems with any window manager/desktop environment. 

I have the Optiplex 150 with 256mb of ram. I use it as a web/torrent server. Command line only is the way to go. Net installs have always worked. I've run Ubuntu, Debian, Fedora, and currently have decided to stay with CentOS.

I don't know why you would be having problems with your network card :confused:.
I just plugin an Ethernet cable to the back of the tower and connect it to one of the open router ports and it will usually scan and find eth0 for me.

---

### Post by NightwishFan on 2011-08-20
I think you will need Debian CD1 and CD2 to get the network manager. I know it is not on CD1 (even though most of Gnome is).

---

### Post by mikewhatever on 2011-08-20
The OP has used a magazine supplied DVD. I wonder, should the NM be there?

---

### Post by NightwishFan on 2011-08-20
Should be there on both Debian dvd1 and Fedora dvd. It isnt on the multiarch for gnome though i think wicd is. (i am not sure why, too many server packages crammed in there for the networkmanager libs i guess?)

---

### Post by Sef on 2011-08-20
> Lubuntu (an Ubuntu variant with LXDE) works fine on my 256Mb Dell. So  does X- and U- buntu, actually. The Debian install is a nightmare.

Have an old compaq with 384 mb ram of which 128 is used for the video, and I installed Debian from a cd and it worked just fine.

---

### Post by Linux_junkie on 2011-08-20
Thanks for all your advice, there's some useful ideas that I'll try out.

---

### Post by Linux_junkie on 2011-08-20
I'd managed to find an old Ubuntu DVD that I got from a magazine backend of last year which has all the *buntu's of 10.10 version.  I tried again to install Lubuntu 10.10 but during installation it crashed and did not get details from the logs so still no idea why it crashes on this Dell machine.  I did install Xubuntu 10.10 and everything went without a problem,now all I've got to do is update it!

---

### Post by aeronutt on 2011-08-20
> **mikewhatever said:**
> Debian installation CD/DVD should have an option to install Gnome Desktop, including the Network Manager.
The original problem was caused by you trying to use a Live CD. Live CDs run entirely from RAM + the installer need some to work, and 256MB is not enough for any Live CD with a full Desktop Environment.

Hmmm...I'm pretty sure I've loaded ubuntu from liveCD onto a computer with 256MB before.

---

### Post by Linux_junkie on 2011-08-20
Just in case anyone is interested, after installing and updating Xubuntu 10.10 I then downloaded and installed LXDE.  As mentioned in my previous posts, even though I've failed to install two LXDE based distro's by installing an XFCE distro then installing LXDE along with it you could say I now have Lubuntu 10.10.

All the apps that I want are available to me and the computer is now running a lot more smoothly.

Thank you and good night.

---

### Post by amjjawad on 2011-09-10
[http://docs.fedoraproject.org/en-US/Fedora/15/html/Release_Notes/sect-Release_Notes-Welcome_to_Fedora_15.html](http://docs.fedoraproject.org/en-US/Fedora/15/html/Release_Notes/sect-Release_Notes-Welcome_to_Fedora_15.html)

Fedora probably has the best documentation I have ever seen so far.
I  remember first time I wanted to use Fedora, I start reading their  installation guide and it was almost 100% enough for me but had one or  two questions.

I can confirm that I managed to get the GUI in Lubuntu 10.04 and 11.04 on P4 with LESS than 512MB of RAM.

I can change the shared memory and I think I can drop it to 256MB. I'll do that and test Lubuntu 11.04 or Lubuntu 10.04 and see if I still can get the GUI or not :)

---

### Post by amjjawad on 2011-09-10
[IMG]http://ubuntuforums.org/picture.php?albumid=2428&pictureid=8190[/IMG]

Who said that requires 512MB or more? ;)

I think I need to post the same on Fedora's Forum :D

---

