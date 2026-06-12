---
title: "Programme and Package Installation methods"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by jbor7755 on 2007-04-19
I am at a loss as to how to install any packages in Ubuntu.  Al the books I read tell me to use Synaptic but  I have no way to connect to the internet.  My modem is a winmodem for which I have to get a driver and I have no network to connect to.
My only internet acces is via wireless and VPN at my university but from what I understand, I cannot access a network in Ubuntu without network manager.... and I can't get network manager without an internet connection!

I would be very happy if someone could prove me wrong here becasue as yet I cannot connect to anything.

As far as I am aware there are basic drivers for my Intel wireless card and Broadcom network card already installed with ubuntu (and running dmesg shows this to be true) so I should be able to get a physical connection but for this little problem.

Also is it possible to install a program/package/driver using "traditional windows methods" (bringing it to the computer in a external drive and then installing by double clicking)?  If so then I could at least install some up-to-date drivers and some non-package programs. 

Seems to be a good setup otherwise.

---

### Post by bobplano on 2007-04-19
you can download what you need at packages.ubuntu.com, then put them on a usb stick or something and install them

---

### Post by KIAaze on 2007-04-19
[edit]see post further below for an even better solution. ;)[/edit]

[re-edit]And also: [http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")[/re-edit]

Just download .deb packages or tar.gz (after having installed "alien", you can also download .rpm packages), put them on an external support and then install them as follows:

1)Installation of .deb packages:
```
sudo dpkg --install name.deb
```

2)Installation of tar.gz files (installation from source):
```
tar -xzvf name.tar.gz
``` (or right-click->"extract here" with the mouse)
```
./configure
make
sudo make install
```

_Warning:_
You might have to download a lot of files to get some programs working.
When you have an internet connection the package manager automatically gets the dependencies.
Without internet connection, you'll have to make sure that you have all the dependencies all by yourself :( :
-Method 1:
```
apt-cache show *program_name*
```
This will list a lot of info about the package, among which the dependencies.
-Method 2: Check the dependencies on [packages.ubuntu.com]("packages.ubuntu.com") (or [http://www.debian.org/distrib/packages]("http://www.debian.org/distrib/packages") if it's Debian exclusive)
Go there and search for the package you want to install.
You can then access a page about it, listing all its dependencies.
-Method 3: Try to install and if something is missing, get it...

None of those methods are recursive, which means that you will have to also look out for the dependencies of the dependencies... :/
I already did that once and it's no fun...

---

### Post by jbor7755 on 2007-04-20
Are there any DVD or CD images of the package repositories avaiable? Or is it possible to purchase repository DVDs?

---

### Post by KIAaze on 2007-04-20
I just discovered something very interesting in [this thread]("http://ubuntuforums.org/showthread.php?t=414728"):
> [QUOTE]9) Lastly Offline Suppport - I do not have a working internet connection. If you are saying that ubuntu is for all the people who can't afford Vista. Then they cannot afford a high speed internet connection. Lets take a scenario - If you want to install a new program. start clicking on the synaptic packet manager. The manager is going to make you a file. Including the dependancies and everything. Quote you how much downloading it will take. All you have to do is put the file on the flash disk. Go to a cybercafe, or your friend's house which has an internet connection. double click the file, and bang. a progress bar appears, showing how much downloading has been done. when its finished. its already made up a bigger file.
go back to ubuntu, and double click the file, all you needed is installed seamlessly, giving you peace of mind.
Download the .deb files, double click and install. Have you every seen the 'make package script' in the synaptic package manager? Makes you a script to download all the dependencies, you go to a connection run it, the dependencies are downloaded and woah - a double click on the .deb file installs them (FYI - go to synaptic package manager, select the files you want, and allow the dependencies, then I think it is -> File -> Make Package Download Script (Or words to that effect) and then it will ask you where you want the script saved to. Select the desktop for instance, then take it to a connected pc and run the script and so on...[/QUOTE]

I can't try it right now since I am at work, but if it works as described, it will make offline installation a whole lot easier. :)

> Are there any DVD or CD images of the package repositories avaiable? Or is it possible to purchase repository DVDs?
Look here: [http://howtoforge.com/dvd_images_of_ubuntu_repositories]("http://howtoforge.com/dvd_images_of_ubuntu_repositories")

---

