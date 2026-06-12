---
title: "No network manager in Squeeze"
date: 2011-08-13
forum: Any Other OS
---

### Post by kmsalex on 2011-08-13
So i did a new install a little while ago along side my 10.04 and win 7. Everything when't fine, boot up try out empithy, can't load.
ok try to ping Google nothing. 
try sudo apt-get update, there is no sudo.
try <ctrl><alt>f2 login as root apt-get apt-get update, only reads cd. try apt-get install gimp, "network can not be reached"


Now before all this of course i looked for the network manager applet in the panel but its not in there, and i can't install it with out Internet. looking around in the menues they realy don't give you much in the default cd 10.04 came with network manager... i think.

So any advice?

---

### Post by NightwishFan on 2011-08-13
If you used the Debian cd1 it does not have enough space to include network manager. If you are on a dhcp ready ethernet connection just open a root terminal and run:
> dhclient eth0

Then set up your software sources in synaptic (if its installed from cd1, not sure). All you need is the debian main repository, it looks something like the below. It might already be set up.
```
deb http://ftp.us.debian.org/debian squeeze main
```

If your sources are set up fine just install network-manager-gnome in synaptic.

**Now if you dont have synaptic**, you need to edit the /etc/apt/sources.list file. From root terminal.
```
nano /etc/apt/sources.list
```

Add the line I mentioned above (deb [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) squeeze main). Then save the file with CTRL+X. Then run this to reload the sources:
```
sudo apt-get update
```

Then run this to install synaptic and network-manager:
```
apt-get install synaptic network-manager-gnome
```

---

### Post by kmsalex on 2011-08-13
I'm on wireless would i try  
```
dhclient (my wireless name)                      
```(I'll need to reboot to try it) Come to think of it the install tried to configure it but it failed, i think saying something about dhc.

---

### Post by NightwishFan on 2011-08-13
It is odd that the networkmanager is not on the CD however the cd is not intended to be 'wireless only' and has to be very space conscious. You should install with the dvd or live dvd (slightly too big for a cd @ 1.1gb) instead.

Is the package wireless tools installed? If you run this command and it shows up as an "i" it is.
```
aptitude search wireless-tools
```

If so do:
```
ifconfig wlan0 up
```
```
iwconfig wlan0 essid nameofnetwork
```
```
dhclient wlan0
```

If the network is encrypted I have no idea how to set it up.

If 1.1gb live dvd or 4gb dvd installer is too much to download, you could try downloading the packages for network-manager from another machine and installing them manually. You likely do not need all the dependencies just a few but this is an annoying way to install it. >_<
[http://packages.debian.org/squeeze/network-manager-gnome](http://packages.debian.org/squeeze/network-manager-gnome)

To install them do (as root):
```
dpkg -i /path/to/package.deb
```

It should explain what else it needs to install.

---

### Post by kmsalex on 2011-08-13
It is encrypted, considering the sparsity of the cd install maby i'll just go grab the dvd image. you know this isn't meant to be a knock on debian, but ubuntu seams to do just fine getting twice the apps in the cd version, whats there on the back end thats eatting all the space on debain? hopefully i have a dvd lieing around somewhere. thanks though night.

---

### Post by kerry_s on 2011-08-13
thats why i only use the net installer when it comes to debian.
if your wifi is linux compatible, you'll setup during install & it will be ready when you get to the desktop.

---

### Post by kmsalex on 2011-08-13
you know i actully tryed the tiny web install after it did my second post, and i gave me an error about the dhc sever being down, or talking to long to respond. I'm going to hold of on marking this solved until i try the dvd.

---

### Post by NightwishFan on 2011-08-13
Server packages as well. 600mb is not a lot for a general purpose distribution. Ubuntu live cd is intended as desktop one, and yes I agree the team that chooses what goes in the live cd does a good job even if people complain when applications are removed all the time.

The Debian live image for Gnome is 1.1gb and includes the whole kitchen sink. I normally install using this.

The DVD1 should have a great selection of software.


I might file a bug to make sure nwm-gnome is included in the cd1 image as it seems like a problem a lot of folks encounter.

---

### Post by kmsalex on 2011-08-13
downloaded installed dvd version, install keep giving me an error twords the end of the the pakage install section, after second time i went back an totaly erased the partion i was trying to right it to, then the partioner gave me an error and right there i nearly threw the hole thing out my window (its only 2 feet away i was tempted).

I had a fedora 15 cd sitting near by, and since my ubuntu was unbootable now i went with that, this thing is a real bit** to get codcs for, i love how there's a point where the fedora wiki tells you to go google it :x:shock::evil:[-X](*,)](*,)](*,)](*,)

---

### Post by NightwishFan on 2011-08-14
You got an error because you probably burned the CD at full speed and it is corrupted. Have a nice day.

---

### Post by kmsalex on 2011-08-14
oh well thank you for your help ser (sarcastic voice) i burned it at 6x (8x is max) speed with it as the only thing running.

to anyone else, any tip's for fedora? i my or may not keep it depending on my experances with it over the next few hours, either way i need a way to make ubuntu bootable again, all fedoras grub gives me is fedora or other (leads to win 7....which i might just get rid of while i'm at it) the ubuntu partion is still there, i've mountaed it to get at some of my files.

the core resone for all this is i want to try gnome 3 outside virtual box, anyone esle running it one 11.10/opensuce/arch etc?

---

### Post by ilovelinux33467 on 2011-08-14
> **kmsalex said:**
> 
to anyone else, any tip for fedora?

One thing I usually do after installing Fedora is install the codecs required to play things like mp3's from the rpmfusion repo like so:
```

su -c 'yum localinstall --nogpgcheck http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-stable.noarch.rpm http://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-stable.noarch.rpm'
su -c 'yum install gstreamer-plugins-{bad,ugly} gstreamer-ffmpeg'

```

I think you can install other codecs off rpmfusion as well, but these are the ones I use.

Sorry, I can't help on making ubuntu bootable again due to the fact I just single boot my computers with Fedora.

---

### Post by kmsalex on 2011-08-14
> **ilovelinux33467 said:**
> One thing I usually do after installing Fedora is install the codecs required to play things like mp3's from the rpmfusion repo like so:
```

su -c 'yum localinstall --nogpgcheck http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-stable.noarch.rpm http://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-stable.noarch.rpm'
su -c 'yum install gstreamer-plugins-{bad,ugly} gstreamer-ffmpeg'

```I think you can install other codecs off rpmfusion as well, but these are the ones I use.

Sorry, I can't help on making ubuntu bootable again due to the fact I just single boot my computers with Fedora.

THANK YOU!:D

That is about the 4th time i've pasted somthing into a terminal in the past hour and it finly worked:D. may be a bit more complicated then apt-geting the restriced extras but i guess if i want to use fedora i'm going to have to get used to ziper and yum.:( i was just starting to realy get the apt- stuff down by heart. so i've got flash and mp3 down, what else is left dvd?

---

### Post by ilovelinux33467 on 2011-08-14
> **kmsalex said:**
> THANK YOU!:D

That is about the 4th time i've pasted somthing into a terminal in the past hour and it finly worked:D. may be a bit more complicated then apt-geting the restriced extras but i guess if i want to use fedora i'm going to have to get used to ziper and yum.:( i was just starting to realy get the apt- stuff down by heart. so i've got flash and mp3 down, what else is left dvd?

Have a look at autoplus which allows you to easily install codecs in Fedora:
[http://www.dnmouse.org/autoten/]("http://www.dnmouse.org/autoten/")

---

### Post by kmsalex on 2011-08-14
Thank you! i'm starting to get the felling more and more installing anykind of proparity softwar is going to be a chore in fedora.:popcorn:

---

### Post by ilovelinux33467 on 2011-08-14
> **kmsalex said:**
> Thank you! i'm starting to get the felling more and more installing anykind of proparity softwar is going to be a chore in fedora.:popcorn:

Yes it is a bit unfortunate. Have a look at this page which will give you a bit of information on why this is:
[http://fedoraproject.org/wiki/Forbidden_items]("http://fedoraproject.org/wiki/Forbidden_items")

---

### Post by garvinrick4 on 2011-08-14
Wrong thread: sorry.

---

### Post by kmsalex on 2011-08-14
> **garvinrick4 said:**
> Wrong thread: sorry.

no i didn't, but i wasn't in with the other 10-15 applets to add to pannel. and i did try 
```
network-manager
```normally and as root. and if you haven't noticed yet I've kind of moved on to something else :P 

what i could use help with now is restoring my 10.04 to a bookable state. the partions can still mount the partions, but ubuntu doesn't show up in grub. it doesn't even call windows windows just "other"

EDIT: oh well never mind then i guess.

---

### Post by NightwishFan on 2011-08-14
[http://lmddgtfy.com/?q=restore+ubuntu+grub](http://lmddgtfy.com/?q=restore+ubuntu+grub)

---

### Post by kmsalex on 2011-08-14
well actully i was about to try this 

[http://forums.fedoraforum.org/showthread.php?t=254080](http://forums.fedoraforum.org/showthread.php?t=254080)

so you want me to google it? starting to sound the the fedora wiki XD



_**EDIT:**_ well considering how far the topic has wonderd, i think its time to mark it solved. 

P.S. i wound up using this to get ubuntu booting again.
[http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html](http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html)

---

