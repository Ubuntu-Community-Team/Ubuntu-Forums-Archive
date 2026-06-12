---
title: "What is Ubuntu Linux for downloading Flash etc."
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by CuriousTeen on 2007-03-26
Hi all,

I just install ubuntu.

May I know what linux version of Ubuntu?

This is the part that I not sure what to download [Flash]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash") for Firefox 

Slowly I will need to download: 
1)Utorrent
2)DirectX
3)Adobe reader. (Any software that can convert Doc to Adobe?)
4)Can't remember what else at this moment.

Thanks

---

### Post by taurus on 2007-03-26
Here you go.

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by tgunner on 2007-03-26
> **CuriousTeen said:**
> Hi all,

I just install ubuntu.

May I know what linux version of Ubuntu?

This is the part that I not sure what to download [Flash]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash") for Firefox 

Slowly I will need to download: 
1)Utorrent
2)DirectX
3)Adobe reader. (Any software that can convert Doc to Adobe?)
4)Can't remember what else at this moment.

Thanks

If you go to a website requiring flash, firefox should prompt you to install it, and it will work as long as your using 32-bit (i386) ubuntu. 

Ubuntu has a built in torrent down loader, or you can run "sudo apt-get install azureus" to get the azureus client. uTorrent does run in WINE, as do some directX games, but you will have to do some quick digging in the forum here to find out how to install WINE. 

And OpenOffice.org Writer should let you export a .DOC as a .PDF.

---

### Post by jem7v on 2007-03-26
Abiword also lets you save text documents as .pdf files, and it will open .doc files as well.  It is not installed by default, but it is a lighter weight word processor if OpenOffice runs too slowly on your computer.

"evince" is the default Acrobat reader in Ubuntu - you probably won't need Adobe Acrobat.  If you do want it, I believe it's the **acroread** package in Synaptic.

DirectX is a Windows thing, really... getting that going might be a bit of work.

---

### Post by arochester on 2007-03-26
If you want to know which version you have see "Find which Ubuntu Linux Version you are running" at [http://www.ubuntugeek.com/find-which-ubuntu-linux-version-you-are-running.html](http://www.ubuntugeek.com/find-which-ubuntu-linux-version-you-are-running.html)

---

### Post by jem7v on 2007-03-26
Oh, also, if you are going to download the flash player from Adobe's site instead of doing it the normal easy way (as linked to by Taurus) you'd want the .tar.gz version, because .rpm files are for Redhat Linux systems.

---

### Post by CuriousTeen on 2007-03-26
> **taurus] 	Here you go.

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)[/QUOTE]

Thank you.
I just open Terminal and just cut & paste.
Run the step twice in Terminal and don't really know what happen.... 
thanks cos I'm can see video when I tested in a website. 

[QUOTE=tgunner said:**
> 
Ubuntu has a built in torrent down loader, or you can run "sudo apt-get install azureus" to get the azureus client. uTorrent does run in WINE, as do some directX games, but you will have to do some quick digging in the forum here to find out how to install WINE. 


I prefer Utorrent cos catonfiguration meant for basic user and is light weighted torrent program. 

I cut and paste 'sudo apt-get install azureus' into Teminal and hit enter but file not found?

Any beginner user learn this i.e 'sudo apt-get install azureus' command? I don't anything about command, you guys think I can learn it? (impossible right?)

What is wine?

[QUOTE=jem7v]"evince" is the default Acrobat reader in Ubuntu - you probably won't need Adobe Acrobat. If you do want it, I believe it's the acroread package in Synaptic.

DirectX is a Windows thing, really... getting that going might be a bit of work.
[/QUOTE]

I can't find evince running on Ubuntu.... 
Wow.... I find it hard to use linux know..... lol

Thank you guys for fast reply

---

### Post by macogw on 2007-03-26
Wine is a compatibility layer to make some simple Windows apps work on Linux.  Check out ubuntuguide.org for instructions to do all kinds of neat stuff, including install Wine. 

sudo = let me do administrative stuff, please
apt-get = run the software-management program
install = what it says
azureus = put whatever program you want to install in this spot, in this case Azureus

Evince just launches when you try to open a .pdf from the internet.  To make pdfs, use Open Office.

---

### Post by CuriousTeen on 2007-03-27
I can't view video file when browse a video site that full of WMV clip database, firefox do not have windows media player plugin for Linux user.

---

### Post by CuriousTeen on 2007-03-27
Hi,



Can any teach me how you guys watch WMV via internet?

---

### Post by jem7v on 2007-03-27
For the codecs, go here:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

In general, you should probably read this guide, because it might clear up a lot of your questions about using Ubuntu:
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html)

---

### Post by sushii. on 2007-03-27
> **CuriousTeen said:**
> Hi,



Can any teach me how you guys watch WMV via internet?

Install MPlayer ([http://mplayerhq.hu](http://mplayerhq.hu)). Download the tarball from the site, extract, start up a terminal, cd to the new directory, "./configure", "make", "make install". Via internet? I don't know if that will work. Try it out though. And for DirectX, thats a total M$ thing. Cedaga and WINE can play some Windoez games. Google them, I'm to lazy to go get the link ;).

---

### Post by jem7v on 2007-03-27
You don't need to download and compile MPlayer because it's already in the official software repositories. You can just install it from the Applications -> Add/Remove dialogue... go to Sound & Video and scroll down until you reach MPlayer Movie Player and the MPlayer Plugin for Mozilla, check those two off, and click the Apply button.

You'll still need to install the proper media codecs, though. (The link in my last post says how to do that.)

---

### Post by houstonbofh on 2007-03-27
To start out, you should not ask questions in the way that you did.  You asked "How do I do a Windows thing."  This is not Windows...  If you asked "How do I get torrents like I did with utorrent?" I would have told you to install bittorrent-gui from the Universe repositories.  Very simple program, that is fast and easy.  Also it is half installed already.

For codecs (and a bunch of other stiuff) I run this script I made after endbling all the stock repositories. (and turning off the CD)
```

#!/bin/sh
# Ubuntu Update Script (Edgy)
#
# This is a script to update a default install to 
# a fully functional system. Most things are automated,
# but a few things still need to be done by hand.
#
# Enable the Universe, Multiverse, and Restricted 
# repsoitories.  Uncheck the CD repository.
#
# DHCP Client
# /etc/dchp3/dhclient.conf
# Unhash 'send host-name' and put in system hostname.
#
# NTP Config
# Set the clock to update automatically from
# us.pool.ntp.org
#
# Note: Sudo must be enabled for this to work.
# (Type 'sudo ls' and the passowrd before running
# this script)
#

# Add extra repositories

# Medibuntu
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
sudo wget http://medibuntu.sos-sts.com/sources.list.d/edgy.list -O /etc/apt/sources.list.d/medibuntu.list

# Wine HQ
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list -O /etc/apt/sources.list.d/winehq.list

# Refresh repositories
sudo apt-get update

# Install everything

sudo apt-get install ssh traceroute p7zip unace rar xfonts-intl-european flashplugin-nonfree sun-java5-plugin faad ffmpeg gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse lame liba52-0.7.4 libartsc0 libdc1394-13 libdvdread3 libfaac0 libfaad2-0 libgsm1 libid3tag0 libimlib2 liblame0 libmad0 libmjpegtools0c2a libmms0 libmodplug0c2 libmp4v2-0 libmpcdec3 libmpeg2-4 liboggflac3 libquicktime0 libsidplay1 libswfdec0.3 libungif4g libwavpack0 libxine-extracodecs libxine-main1 libxvidcore4 libxvmc1 mjpegtools ntp ntp-simple sox vorbis-tools libdvdcss2 w32codecs msttcorefonts ogle-mmx ogle-gui streamtuner streamripper

```

That should get you going, and still be very close to stock.

---

### Post by digital_sabotage on 2007-03-27
I'm a newbie too but i had luck playing most videos in firefox by installing mplayer from synaptics and then installed a firefox addon called MediaPlayerConnectivity which has a simple wizard to make mplayer the default player in firefox ...you will also need to download win32 codecs from mplayerhq and follow the instructions to put them in the correct directory ...hope this helps

---

### Post by CuriousTeen on 2007-03-28
> **jem7v said:**
> You don't need to download and compile MPlayer because it's already in the official software repositories. You can just install it from the Applications -> Add/Remove dialogue... go to Sound & Video and scroll down until you reach MPlayer Movie Player and the MPlayer Plugin for Mozilla, check those two off, and click the Apply button.

You'll still need to install the proper media codecs, though. (The link in my last post says how to do that.)

Thank you,

 I finally get it done.

I followed, 

1)add/remove 2 category of 'Mplayer'.
2)[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) 
3)installed 'w32codecs package'
4)Still don't work
5)I go 'If you still cannot play WMV files after installing w32codecs, try [WWW] the method suggested here.'
6)add/remove 2 category of 'gstreamer'
7)thank you, finally solve this problem. 

                                                   [QUOTE=houstonbofh]To start out, you should not          ask  questions in the way that you did. You asked "How do I do a Windows thing." This is not Windows... If you asked "How do I get torrents like I did with utorrent?" I would have told you to install bittorrent-gui from the Universe repositories. Very simple program, that is fast and easy. Also it is half installed already.[/QUOTE]

Sorry, I really don't know anything about linux so that why I trying out. 
I'm sorry that I mention 'windows' cos I can't explain clearly to member what are the help/solution I need.
Infect, my computer not perfectly solve cos all my LED light not up, keyboard go crazy( haven't finish typing a sentence and it auto jump to other field). so I have to post one by one.

Ubuntu default bittorrent was in my system, but is not workable cos I'm running Router and connect thru built-in wireless pci.
I can't find bittorrent program nor settings, so I tested by download torrent file. bittorrent only pop up when I attempt to download a file but fail cos the program can't connect to clients and idle for 15mins then later prompt me fail.
When I was windows, I can configure port/fire etc. 
Now.... I got no idea. 
Truly sorry for asking so much simple question yet is difficult for me.

Should I quit using linux?
Or any sites that is easy for beginner to understand how linux work before touching on Ubuntu knowledge guide. ( I can't cope all the links guide cos I don't understand the jaggon) 

I really don't know where is the beginning to learn Ubuntu... :( :( :( 
I'm trying, I desperate for an answer without resting, I being browsing for like 16 hrs.


[QUOTE=houstonbofh]For codecs (and a bunch of other stiuff) I run this script I made after endbling all the stock repositories. (and turning off the CD)
```
Code:

#!/bin/sh
# Ubuntu Update Script (Edgy)
#
# This is a script to update a default install to 
# a fully functional system. Most things are automated,
# but a few things still need to be done by hand.
#
# Enable the Universe, Multiverse, and Restricted 
# repsoitories.  Uncheck the CD repository.
#
# DHCP Client
# /etc/dchp3/dhclient.conf
# Unhash 'send host-name' and put in system hostname.
#
# NTP Config
# Set the clock to update automatically from
# us.pool.ntp.org
#
# Note: Sudo must be enabled for this to work.
# (Type 'sudo ls' and the passowrd before running
# this script)
#

# Add extra repositories

# Medibuntu
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
sudo wget http://medibuntu.sos-sts.com/sources.list.d/edgy.list -O /etc/apt/sources.list.d/medibuntu.list

# Wine HQ
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list -O /etc/apt/sources.list.d/winehq.list

# Refresh repositories
sudo apt-get update

# Install everything

sudo apt-get install ssh traceroute p7zip unace rar xfonts-intl-european flashplugin-nonfree sun-java5-plugin faad ffmpeg gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse lame liba52-0.7.4 libartsc0 libdc1394-13 libdvdread3 libfaac0 libfaad2-0 libgsm1 libid3tag0 libimlib2 liblame0 libmad0 libmjpegtools0c2a libmms0 libmodplug0c2 libmp4v2-0 libmpcdec3 libmpeg2-4 liboggflac3 libquicktime0 libsidplay1 libswfdec0.3 libungif4g libwavpack0 libxine-extracodecs libxine-main1 libxvidcore4 libxvmc1 mjpegtools ntp ntp-simple sox vorbis-tools libdvdcss2 w32codecs msttcorefonts ogle-mmx ogle-gui streamtuner streamripper
```

That should get you going, and still be very close to stock.[/QUOTE]

Do I need to follow this since I'm able to see video?

---

### Post by houstonbofh on 2007-03-29
> **CuriousTeen said:**
> 
Sorry, I really don't know anything about linux so that why I trying out. 
I'm sorry that I mention 'windows' cos I can't explain clearly to member what are the help/solution I need.
Infect, my computer not perfectly solve cos all my LED light not up, keyboard go crazy( haven't finish typing a sentence and it auto jump to other field). so I have to post one by one.
This is a common issue.  Remember that your *goal* is to download torrents.  How you do this is the *method.*  Let us sugest the method. :)
> **CuriousTeen said:**
> 
Ubuntu default bittorrent was in my system, but is not workable cos I'm running Router and connect thru built-in wireless pci.
I can't find bittorrent program nor settings, so I tested by download torrent file. bittorrent only pop up when I attempt to download a file but fail cos the program can't connect to clients and idle for 15mins then later prompt me fail.
When I was windows, I can configure port/fire etc. 
Now.... I got no idea. 
Truly sorry for asking so much simple question yet is difficult for me.

Do not be sorry.  You are now asking much better questions.  You are also learning quite a bit.  The beginning is always the hardest part.  It will get easier.  As to bit torrent clients,  The bittorrent-gui is fast, but has no real configuration.  The bittornado-gui has much more configuration, but is still quite simple and easy.  Azureus is the last one in the repositories that is frequently recommended.  If none of these work, we will have to try more difficult things.  Don't worry.  We will not give up if you don't.
> **CuriousTeen said:**
> 
Should I quit using linux?
Or any sites that is easy for beginner to understand how linux work before touching on Ubuntu knowledge guide. ( I can't cope all the links guide cos I don't understand the jaggon) 

I really don't know where is the beginning to learn Ubuntu... :( :( :( 
I'm trying, I desperate for an answer without resting, I being browsing for like 16 hrs.

Do I need to follow this since I'm able to see video?
Don't quit, but do rest.  Sometimes just taking a break from a problem makes it easier to find a solution.  You do not need to do this in one day.  Take your time.  This is what a duel boot system is for! ;)
As to sites, I think [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) is one of the best starting places.

---

### Post by stchman on 2007-04-05
> **CuriousTeen said:**
> Hi all,

I just install ubuntu.

May I know what linux version of Ubuntu?

This is the part that I not sure what to download [Flash]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash") for Firefox 

Slowly I will need to download: 
1)Utorrent
2)DirectX
3)Adobe reader. (Any software that can convert Doc to Adobe?)
4)Can't remember what else at this moment.

Thanks

Firefox will install Adobe flash automatically.

You will substitute ktorrent for utorrent.  utorrent would need to run under WINE and ktorrent can do the same as utorrent.

There is no DirectX in Linux.  You can play some DX games through WINE.

Adobe Reader will not convert .doc to .pdf.  OpenOffice has an import to .pdf so that will work.

---

