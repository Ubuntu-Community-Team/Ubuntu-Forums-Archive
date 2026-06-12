---
title: "dvds"
date: 2005-01-02
forum: Apple PPC Users
---

### Post by tiiim on 2005-01-02
how do you get dvds working? i have problems through Totem playing them do i need to download plugins for it or do you know another player in which case where do i get it?

Tim :o

---

### Post by danderso on 2005-01-02
I'm not sure if this works on powerpc (though I believe it does)...  Try running the following script to install libdvdcss2, the component that decodes the dvd (it should be preinstalled):

/usr/share/doc/libdvdread3/examples/install-css.sh

Make sure that you have installed the developer tools and the package 'fakeroot' before running the above script:
sudo aptitude install build-essential
sudo apt-get install fakeroot

Then once libdvdcss2 is installed, install totem-xine:
sudo apt-get install totem-xine

Hopefully that works, sometimes I have to load totem twice before I can get a dvd to play (not sure why that is).  I've also heard that mplayer works well, though I haven't tried it yet.

---

### Post by tiiim on 2005-01-03
inst all the script you said.

But when i went to download totem-xine it said

pagage totem-xine is not available, but is referred to by another package. That may mean that the package is missing, has been obsoleted, or is available from another source.

e: package totem-xine has no installation candidate



any ideas? do i need include the debian tree? if so how? or is that dangerous?

---

### Post by wallijonn on 2005-01-03
Either install Ogle or Xine through SPM or
```
sudo apt-get install ogle-gui
```
or
```
sudo apt-get install xine-ui
``` 

```
wget http://www.las.ic.unicamp.br/pub/debian-marillat/dists/unstable/main/binary-i386/libdvdcss2_1.2.8-0.0_i386.deb
```

```
dpkg -i libdvdcss2_1.2.8-0.0_i386.deb
``` 

Start Ogle or Xine.

---

### Post by tiiim on 2005-01-03
but ogle or xine dont exist on SPM it says they are not there .....

do i need to be on the Debian source instead of Ubuntu? remember im using PPC so not sure if i have all packages through the main area... or how fast the Ubuntu team compile for other platforms.... i know Debian themselves have a massive database for all formats....im assuming Ubuntu do also...

---

### Post by tiiim on 2005-01-03
[QUOTE=tiiim]but ogle or xine dont exist on SPM it says they are not there .....

do i need to be on the Debian source instead of Ubuntu? remember im using PPC so not sure if i have all packages through the main area... or how fast the Ubuntu team compile for other platforms.... i know Debian themselves have a massive database for all formats....im assuming Ubuntu do also...[/QUOTE]
 done!

sorry i went to my /etc/apt/sources.list and enable the 2 other sources that Ubuntu put in and now its made my collection big... but i managed to get the software to run! cheers.

---

### Post by wallijonn on 2005-01-03
How big is your /var/cache/apt/archives?

You might recover a lot of space by clearing it out from time to time, or make sure that when you are in SPM you clear it after an install or update.

---

### Post by danderso on 2005-01-03
Yeah, you had to uncomment those lines from the repository list.  Sorry about forgetting to mention that.  Hope it works alright now.

---

### Post by tiiim on 2005-01-03
[QUOTE=wallijonn]How big is your /var/cache/apt/archives?

You might recover a lot of space by clearing it out from time to time, or make sure that when you are in SPM you clear it after an install or update.[/QUOTE]


cheers for telling me set so it clears out when i installed.

[QUOTE=danderso]
 	Yeah, you had to uncomment those lines from the repository list. Sorry about forgetting to mention that. Hope it works alright now. [/QUOTE]

No problem yeah given me access to lots more files this was the reason i wanted a Debian distro... now got the full power of it in Ubuntu...

---

### Post by wallijonn on 2005-01-04
The other thing you want to do is look at all your /var/log files. You can try to fix any problems detected so that it doesn't grow too big. View as list. I wouldn't worry about files unless they go over 100MB. Some people won't worry about it until it hits 10% of their disk drive.

---

### Post by chascon on 2005-01-09
Concerning "/usr/share/doc/libdvdread3/examples/install-css.sh", yes that does work on ppc, for debian.  You say this installs libdvdcss2?  You can get libdvdcss3 from universe, so why bother with 2?  I'm not an expert but it seems to me that this could lead to conflicts.

AS for needing fakeroot on debian, I never went out to install it on debian, maybe it was default.  I did have dev tools though.

Chascon

UPDATE: I just tried the script for debian and debian-ppc on ubuntu-ppc.  It works with xine and ogle.  The standard totem (I think it comes with gstreamer as default) doesn't benefit.  On an iMac 400 mhz G3 I get less dropping of frames in debian (movies are still viewable in debian), but then again I'm running my own hacked ubuntu-ppc.  And no, I didn't have to install fakeroot or anything else as suggested in the posting added below.

How does one make the people who are in control of the wiki on restricted formats to add this info for ppc.  Their comments consider only intel and perhaps AMD as the mirror mentioned does not contain ppc binaries or source.  I think we should formulate an irc to take care of ppc specific problems such as this.  How does one 
go about this?

Chascon



danderso
Ubuntu Newbie
 
danderso is Offline:
Join Date: Nov 2004
Posts: 7
Style:
	
Default Re: dvds
I'm not sure if this works on powerpc (though I believe it does)... Try running the following script to install libdvdcss2, the component that decodes the dvd (it should be preinstalled):

/usr/share/doc/libdvdread3/examples/install-css.sh

Make sure that you have installed the developer tools and the package 'fakeroot' before running the above script:
sudo aptitude install build-essential
sudo apt-get install fakeroot

Then once libdvdcss2 is installed, install totem-xine:
sudo apt-get install totem-xine

Hopefully that works, sometimes I have to load totem twice before I can get a dvd to play (not sure why that is). I've also heard that mplayer works well, though I haven't tried it yet.

---

