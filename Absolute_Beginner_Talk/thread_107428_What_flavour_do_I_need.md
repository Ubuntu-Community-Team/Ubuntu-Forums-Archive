---
title: "What flavour do I need ?"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by oygle on 2005-12-23
I'm interested in Ubuntu, as a Windows (95b) 'replacement' ; please see my post [here]("http://ubuntuforums.org/showthread.php?t=63315&page=14")

If someone could advise me on some of those questions in the thread, I'd appreciate it.  :D

Now, just when I found the download page at [http://ubuntu-releases.optus.net/5.10/](http://ubuntu-releases.optus.net/5.10/) , and seeing that I need the [PC (Intel x86) install CD ISO]("http://ubuntu-releases.optus.net/5.10/ubuntu-5.10-install-i386.iso"), I have now noticed that there are 'flavours' of Ubuntu as follows:

Ubuntu Warty 4.10
Ubuntu Hoary 5.04
Ubuntu Breezy 5.10
Kubuntu Warty 4.10
Kubuntu Hoary 5.04
Kubuntu Breezy 5.10
Edubuntu Breezy 5.10
Xubuntu

Assuming that I need to get 5.10, will the above (linked) ISO be "Ubuntu Breezy 5.10" I guess ?

What are these used for, and how different are they, compared to Ubuntu ?

Kubuntu Breezy 5.10
Edubuntu Breezy 5.10
Xubuntu

I also see there are sub forums Ubuntu 5.10 (GNOME) and Ubuntu 5.10 (KDE) ; are these just different installs from the same ISO ?

As an overview, all I need to know is, will Ubuntu 5.10 fill my requirements, as outlined in the other post (my first), and do I have the correct link to the ISO.

I only have a 7Gb HDD to test this on, and noticed this

> 
I recommend to create four partitions: /boot (~100-200 MB), swap (double RAM size), /[root] (~4-7GB, depending on your needs) and /home (as big as you like it to be).

so, will 7 Gb not be enough room to install everything ?  I cannot find anything in the Wiki in regards to the actual installation. I assume you just boot up from the ISO, like I did when installing IPCOP. What about partitions, will the installation of Ubuntu reformat the HDD, and then ask me what size the partitions are to be ?

The HDD I'm going to use has IPCOP on it, no longer needed, so I shouldn't need to reformat the HDD, is that correct ?  Although I do want to 'wipe' everything though.

Thanks,   :)

Oygle

---

### Post by akniss on 2005-12-23
Ubuntu is on a 6 month release cycle, so the numbers correspond to the year and month they were released.  (5.10 = October, 2005)  The "Breezy"  and "Hoary" are just nicknames that the developers give each release (I think it must be a linux thing... ;) So Breezy 5.10 would be the most up to date and the one you want.

Ubuntu uses Gnome as the default desktop.  If you prefer KDE, then Kubuntu comes with KDE as the default desktop instead.  Edubuntu comes with special educational software, and finally Xubuntu comes with a third desktop called Xfce.  I would recommend Ubuntu or Kubuntu (I prefer Gnome, but many windows converts prefer KDE).

A 7 GB harddrive should be plenty.  During installation, you can choose to let Ubuntu  make its own partitions, or you can manually set them yourself.  Many people like to have separate partitions for /  (called root), /home, and sometimes you need a separate partition for /boot (but probably not you with a 7GB drive).  The install will give you the option to format the entire drive, so you will get everything 'wiped clean' as you desire.

---

### Post by TheCyrus on 2005-12-23
Kubuntu is Ubuntu in the KDE Enviro.
Edubutnu is designed for students and young people.
Xubuntu uses XFCE

---

### Post by towsonu2003 on 2005-12-23
you've got many questioons ;) 


[i]Ubuntu Warty 4.10
Ubuntu Hoary 5.04
Ubuntu Breezy 5.10
Kubuntu Warty 4.10
Kubuntu Hoary 5.04
Kubuntu Breezy 5.10
Edubuntu Breezy 5.10[/i]
numbers and names (breezy, warty, hoary) are versions (like win 95, 98, XP). Kubuntu Ubuntu etc are flavors. 

*Assuming that I need to get 5.10*
yes

*What are these used for, and how different are they, compared to Ubuntu ?*
ubuntu: linux + gnome
kubuntu: linux + kde
xubuntu: linux + xfce
edubuntu: linux for educational nstitutions (thin client supported etc)

*I also see there are sub forums Ubuntu 5.10 (GNOME) and Ubuntu 5.10 (KDE) ; are these just different installs from the same ISO ?*
Ubuntu GNOME is to discuss ubuntu + gnome (= ubuntu) issues; ubuntu KDE is to discuss kubuntu issues. As mentioned above, kubuntu will install from kubuntu iso, ubuntu from ubuntu iso. **but** you can have all at once as well... Just install one, connect to internet, and download <flavor>-desktop using apt-get. See my example below with Xubuntu.

*As an overview, all I need to know is, will Ubuntu 5.10 fill my requirements, as outlined in the other post (my first), and do I have the correct link to the ISO.*
I do not see your specs there but I can guess... You would be better off with xubuntu (ubutu + xfce)
to get xubuntu, install ubuntu then connect to internet and from the terminal: ```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```
Then logout and login after choosing 'xfce' from the sessions menu. Make it your default as well (it will ask). 

*I only have a 7Gb HDD to test this on, and noticed this*
Try this scheme: 
4GB -   /
512MB -  swap
rest -     /home
And change (reformat - reinstall) if you're not happy. My first linux install got reinstalled about 8 times... 


*so, will 7 Gb not be enough room to install everything ?*

Yes, most probably. My / uses 2.7 GB and I've got some stuff installed (like couple of kernels and 3 different office suites). if not (very very unprobable), try a distro like "Damn Small Linux"

*I cannot find anything in the Wiki in regards to the actual installation.*
take a look at: 
[https://wiki.ubuntu.com/GettingUbuntu](https://wiki.ubuntu.com/GettingUbuntu)
[https://wiki.ubuntu.com/Installation/I386](https://wiki.ubuntu.com/Installation/I386)
keyword used was installation

** * _This will be useful after installation: [http://help.ubuntu.com/starterguide/C/faqguide-all.html](http://help.ubuntu.com/starterguide/C/faqguide-all.html) ** * _

*I assume you just boot up from the ISO*
yes

*What about partitions, will the installation of Ubuntu reformat the HDD, and then ask me what size the partitions are to be ?*
if you choose automatic partitioning, no it wont ask. If you choose expert partitioning, yes it will ask

*The HDD I'm going to use has IPCOP on it, no longer needed, so I shouldn't need to reformat the HDD, is that correct ?*
reformatting will erase **everything** on that computer. beware...

*Although I do want to 'wipe' everything though.*
reformatting (especially automatic partitioning) will **erase everything** However, you will need to reformat in order to install ubuntu because 7GB is not that big to hold two distros toghether (assuming you want /home in separate partition for later distro installations to try out them easier). Anyhow, how big is the IPCOP installation (go to IPCOP running computer and issue this command: df -h)? 

Welcome and enjoy linux :)

---

### Post by oygle on 2005-12-23
Thanks for the info on the release versions, and how Breezy and Hoary came about.

[QUOTE=akniss]Ubuntu uses Gnome as the default desktop.  If you prefer KDE, then Kubuntu comes with KDE as the default desktop instead. ..... I would recommend Ubuntu or Kubuntu (I prefer Gnome, but many windows converts prefer KDE).[/QUOTE]

I notice from the [help on Kubuntu]("http://help.ubuntu.com/kde/about-kubuntu/C/index.html"), that it is posible to switch between the two

> Thus, it is very easy to install GNOME from a Kubuntu distribution, and equally as easy to install KDE from an Ubuntu setup.

.. so, assuming I can 'switch' desktops, I may download both, and install Ubuntu, and if there are any (major) issues, then I can try the swap.

[QUOTE=akniss]A 7 GB harddrive should be plenty.  During installation, you can choose to let Ubuntu  make its own partitions, or you can manually set them yourself.  Many people like to have separate partitions for /  (called root), /home, and sometimes you need a separate partition for /boot (but probably not you with a 7GB drive).  The install will give you the option to format the entire drive, so you will get everything 'wiped clean' as you desire.[/QUOTE]

Okay, thanks. I do also have a 20Gb HDD that is on this XP box, and I would hope in a few months for that drive to be 'free' for the Linux box.  Considering adding that extra 20Gb later, I would then no doubt be wise to reorganise things, like putting the swap partition on the 7Gb, and place the other partitions on the 20Gb. I have used Norton PartitionMagic to reduce or increase partition sizes; can the same be done with Ubuntu, even if the (new) boot partition was going to the 20Gb HDD ?

Anyway, ..... that's months down the track, .... wooo neady !!!

For now, 7Gb will do, ....... can't wait to download it (both).

Thanks,

Oygle

---

### Post by oygle on 2005-12-23
Hi towsonu2003,

Thanks for answering all those questions, and supplying the info on the links,etc. Yes, I did have a few questions alright. I _may_ actually consider putting the Office 2000 on this XP box, then that will remove the need for any 'office' type needs on the Linux computer (the Win95 replacement).

[QUOTE=towsonu2003].... to get xubuntu, install ubuntu then connect to internet and from the terminal: ```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```
Then logout and login after choosing 'xfce' from the sessions menu. Make it your default as well (it will ask). [/quote]

If there any method to get it 'locally' at all ? Strange question I know, but my download limit is only 500Mb per mth, and I only have about 200 Mb left. If I go over the 500Mb, the speed is reduced, which doesn't worry me, so I leave big downloads until the end of the month, so I'm happy to download both Ubuntu and Kubuntu before the end of this month.

Can I get it over the LAN, just by IP address, although the 'get' would be to a Win computer.

Many thanks,

Oygle

---

### Post by towsonu2003 on 2005-12-23
[QUOTE=oygle]
Thanks for answering all those questions, and supplying the info on the links,etc. Yes, I did have a few questions alright. I _may_ actually consider putting the Office 2000 on this XP box, then that will remove the need for any 'office' type needs on the Linux computer (the Win95 replacement).[/quote] OpenOffice.org in Ubuntu might take care of your office needs. I have 3 office suites because, well, I am weird. Ubuntu comes with a nice office suite compatible with MS Office (unless the document is too complicated). 
[QUOTE=oygle]
If there any method to get it 'locally' at all ? [/QUOTE]
Hmm, I am not clear with this question (which desktop I mean).
But in any case, in my system, downloading xubuntu-desktop will take about 25-30MB. Downloading kubutu-desktop will take about 120MB. I am hoping these numbers will satisfy you. 

So basically, to install, just download one cd (ubuntu 5.10) and boot with it, install and apt-get xubuntu (or kubuntu, which ever you prefer) :)

If you don't like either gnome (ubuntu, comes with the CD) nor xfce (xubuntu) than you can apt-get kubuntu. 

Hopefully this will be helpful :) good luck (bed time for me, be back after that :P)

---

### Post by elemental666 on 2005-12-23
I would highly recommend, just based on your internet access, downloading only Kubuntu and ordering the Ubuntu install media from the [ubuntu website]("https://shipit.ubuntu.com/").  Also, before you get all partitions crazy you should take the time to read up on the [Linux File Hierarchy]("http://www.pathname.com/fhs/") and [Partioning]("http://www.tldp.org/HOWTO/Partition/").

Read the partitioning howto first, then the File Hierarchy.  You can probably read them while Kubuntu downloads ;)  I mentioned the file hierarchy simply because it helped me understand why, for example, /home and /opt are really good candidates for having their very own partition, as it helps explain what the standards directories are for.  Too often I see people talk about their favorite partition schemes but they don't help anyone understand WHY they went that way.  This will get you started UNDERSTANDING what you are doing and why, instead of just blindly following the advise of others.

As a matter of fact, [The Linux Documentation Project]("http://tldp.org/") should be in your bookmarks and referenced often.  While just about anything is possible in linux, its sometimes best to get a broad view of the subject, then specialize it to your specific environment.

Good Luck


[QUOTE=oygle]Hi towsonu2003,

Thanks for answering all those questions, and supplying the info on the links,etc. Yes, I did have a few questions alright. I _may_ actually consider putting the Office 2000 on this XP box, then that will remove the need for any 'office' type needs on the Linux computer (the Win95 replacement).



If there any method to get it 'locally' at all ? Strange question I know, but my download limit is only 500Mb per mth, and I only have about 200 Mb left. If I go over the 500Mb, the speed is reduced, which doesn't worry me, so I leave big downloads until the end of the month, so I'm happy to download both Ubuntu and Kubuntu before the end of this month.

Can I get it over the LAN, just by IP address, although the 'get' would be to a Win computer.

Many thanks,

Peter[/QUOTE]

---

### Post by oygle on 2005-12-23
[QUOTE=towsonu2003]Hmm, I am not clear with this question (which desktop I mean). But in any case, in my system, downloading xubuntu-desktop will take about 25-30MB. Downloading kubutu-desktop will take about 120MB. I am hoping these numbers will satisfy you. [/quote]

Yes, those numbers are small, but I can download both the Ubuntu and the Kubunta install ISO's before the end of the month. (about 640 Mb each)

My thinking there is that I'd be better to have both the (full) ISO's here, from [http://mirrors.uwa.edu.au/ubuntu-releases/kubuntu/5.10/kubuntu-5.10-install-i386.list](http://mirrors.uwa.edu.au/ubuntu-releases/kubuntu/5.10/kubuntu-5.10-install-i386.list) , I can see:

/pool/main/k/kubuntu-meta/kubuntu-desktop_0.55_i386.deb

so I have to assume both the GNOME and the KDE (desktops) are in each full ISO. There must be a way to update from a source either on the same computer, or even on the LAN.

Oygle

---

### Post by oygle on 2005-12-23
[QUOTE=elemental666].... Also, before you get all partitions crazy you should take the time to read up on the [Linux File Hierarchy]("http://www.pathname.com/fhs/") and [Partioning]("http://www.tldp.org/HOWTO/Partition/").[/quote]

Okay, thanks for those links, I will try and read up on partitioning,etc.

Oygle

---

### Post by akniss on 2005-12-23
[QUOTE=oygle]
I _may_ actually consider putting the Office 2000 on this XP box, then that will remove the need for any 'office' type needs on the Linux computer (the Win95 replacement).
[/QUOTE]

You could also put OpenOffice.org on your XP box (if the ubuntu resources are a little tight for Office apps).  It has a Windows or Linux version.  The default Ubuntu install will put OpenOffice on your Ubuntu box as well.

---

### Post by akniss on 2005-12-23
[QUOTE=oygle]
.. so, assuming I can 'switch' desktops, I may download both, and install Ubuntu, and if there are any (major) issues, then I can try the swap.
[/QUOTE]

It would save you time and bandwidth to only download one iso, then use apt-get or synaptic to get the other.

```
sudo apt-get install kubuntu-desktop
```
or
```
sudo apt-get install ubuntu-desktop
```
or 
```
sudo apt-get install xubuntu-desktop
```

---

### Post by oygle on 2005-12-23
[QUOTE=akniss]You could also put OpenOffice.org on your XP box (if the ubuntu resources are a little tight for Office apps).  It has a Windows or Linux version.  The default Ubuntu install will put OpenOffice on your Ubuntu box as well.[/QUOTE]

There may be some 'tricky' file conversions to do in the future, with "M$ Office" type files, and my thinking is that OpenOffice _may_ be wanting in some areas, simply by not being able to (fully) convert PPT and DOC formats to HTML for a website. I know M$ html files are full of bloatware, but I do have some tools to strip most of it out. I just feel I'd better stick with M$ Office for now, I'll move it to the XP box. That said, if Ubuntu installs OpenOffice, I can also convert those same docs, and see how well OpenOffice has converted them.

Thanks,

Oygle

---

### Post by oygle on 2005-12-23
[QUOTE=akniss]It would save you time and bandwidth to only download one iso, then use apt-get or synaptic to get the other.[/QUOTE]

If I downloaded (say) the Ubuntu ISO, can I download just the 'kubuntu-desktop' , so that, after I install Ubuntu, I can then use synaptic (or whatever) to install the kubuntu-desktop 'locally'.

Just that the kubuntu-desktop is about 120MB, so I'd rather grab it before the end of the month, if it possible to install from a local source (CD, other computer,etc).

Thanks,

Oygle

---

### Post by akniss on 2005-12-23
There is a way to just download and not install using apt-get -d, then use the burned cdrom as a repository, but I didn't have any luck when I tried to do that with xubuntu-desktop...  You sound more computer savvy then I am, though, so you may have more luck.  Below is a thread on how to do that. 

[http://ubuntuforums.org/showthread.php?t=101790](http://ubuntuforums.org/showthread.php?t=101790)

---

### Post by oygle on 2005-12-23
[QUOTE=akniss]..  You sound more computer savvy then I am, though[/QUOTE]

... I know nothing.  :D

Thanks for the link, I'll check it out.

Oygle

---

