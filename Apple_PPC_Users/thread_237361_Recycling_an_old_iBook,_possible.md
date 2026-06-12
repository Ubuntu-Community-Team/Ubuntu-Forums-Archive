---
title: "Recycling an old iBook, possible ?"
date: 2006-08-16
forum: Apple PPC Users
---

### Post by olofgaga on 2006-08-16
Hi all,

I have an old iBook G3 500MHz. On OS X, it begin to be very slow...

So I think about installing another OS, if possible light ! I find xUbuntu, but before trying it, I have some questions :

I use this laptop for one thing, earing mp3. Nothing else.

All my mp3 are on an external firewire drive formatted for Mac OS (HFS+ ???). I can't copy theses files to the iBook, not enough space.

So, is it possible to use this harddrive ???

And do you know nice mp3 player who run on xUbuntu ? Or, why not, a text based player -> no X-Windows but with a nice way to browse mp3 and make playlist ?!?!?



Thank you !

---

### Post by daniel of sarnia on 2006-08-16
As I know HFS/HFS+ can not be read from any os other then a mac os, be it linux windows or bsd. A good mp3 player that will work with xubuntu is an ipod, you will have to format it with fat32 though.

---

### Post by APU on 2006-08-16
Of course HFS and HFS+ can be read by Linux. Just plug in the Firewire harddrive and it will show up on the Dapper Desktop (at least with Ubuntu, but it should be the same with Xubuntu too).

The only limitation is that you should turn off Journaling on the external drive (Can be done from the Disk Utility in MacOS X). There are still problems with journaled HFS+ drives in Linux.

Sorry but I don´t really know about an mp3 Player but a good Command Line player would be interesting for me too!

APU

---

### Post by olofgaga on 2006-08-16
Thank you ! I think that my external drive isn't jouralised, so I will test that.

I found a text mp3 player : [http://mp3blaster.sourceforge.net/]("http://mp3blaster.sourceforge.net/")

---

### Post by stmiller on 2006-08-16
HFS/HFS+ read has been built in the Linux kernel for awhile. There is recent write support, but it is experimental. It works fine for me though (writing) as long as journaling is turned off on the drive.

As far as a command line mp3 player, the classic program is mpg123 (or mpg321).

[http://en.wikipedia.org/wiki/Mpg123](http://en.wikipedia.org/wiki/Mpg123)

[http://mpg321.sourceforge.net/](http://mpg321.sourceforge.net/)

---

### Post by olofgaga on 2006-08-18
I have installed xUbuntu. But when I plug my Firewire harddrive, nothing happends. No informations on dmesg.

I boot on Ubuntu CD. I plus my drive, it mounts on the desktop. Read-only but for me it's ok. I see that the mount partition is /dev/sda9. I return in xUbuntu, but I don't have /dev/sdaX !!! No sd... at all !

Is it normal ?

Thank you !

---

### Post by avtolle on 2006-08-18
Try booting with the Firewire drive plugged in; don't know if this is the answer, but back in my past (CP/M days), sometimes this was the way to get peripherals to be recognized/set up to operate correctly.

---

### Post by olofgaga on 2006-08-18
> **avtolle said:**
> Try booting with the Firewire drive plugged in; don't know if this is the answer, but back in my past (CP/M days), sometimes this was the way to get peripherals to be recognized/set up to operate correctly.
Oh yes, it works ! I boot with the hard drive plugged. I have to mount it manually but it works !

I'm not a Linux guru, so I would like to know why /dev/sdxn doesnt exists when I boot without the hard drive plugged and when I boot with the hard drive, they are there !!!!

---

### Post by avtolle on 2006-08-18
I'm no guru, either, just an "old" hand at dealing with OS (other than Windows), so I have no idea why it works. I'm just glad it does.

---

### Post by songo on 2006-08-18
> **olofgaga said:**
> 
And do you know nice mp3 player who run on xUbuntu ? Or, why not, a text based player -> no X-Windows but with a nice way to browse mp3 and make playlist ?!?!?


music management apps:

listen [http://listengnome.free.fr/]("http://listengnome.free.fr/")
exaile [http://www.exaile.org/]("http://www.exaile.org/")
rhythmbox [http://rhythmbox.sourceforge.net/]("http://rhythmbox.sourceforge.net/")

> I use this laptop for one thing, earing mp3. Nothing else.
amarok [http://amarok.kde.org/]("http://amarok.kde.org/")
it will install some kde stuff, but it is by far the best.  I personally use exaile, which is amarok-like.

---

### Post by olofgaga on 2006-08-19
Now, I can mount my external hard-drive. So I try some mp3 players.

mp3blaster : work fine I move files in my home directory. Directly from the external hard drive I have a segmentation fault...

mpg123 : show me on screen that it is working, but no sound

xmms : works fine on my home directory but freeze if I try to open file on external hard drive

Others propositions spoke about kde or gnome apps. I don't have kde or gnome. I use xUbuntu. So if I'm correct, I can't install kde or gnome apps, right ?

Any other idea ?

---

### Post by songo on 2006-08-19
> **olofgaga said:**
> 
Others propositions spoke about kde or gnome apps. I don't have kde or gnome. I use xUbuntu. So if I'm correct, I can't install kde or gnome apps, right ?

wrong!
u can install anything you want!
exaile is GTK, so it will work fine in xubuntu.
amarok is KDE but it should (will) run on xubuntu. but it will install some KDE libraries that amarok needs to run properly. so your xubuntu will be a little bit hybrid. it's no big deal unless you DON'T want an heterogeneous environnement.

---

### Post by olofgaga on 2006-08-20
Yes, I found Rhythmbox in Synaptic and it works.

Just some very little stop when I do others things. Any way to "allocate more processor time" ?

---

### Post by Xappe on 2006-08-27
for textbased mp3-playing maybe you could try Music Player Daemon (MPD) with a text based client like MPC. With MPD running you can also connect to the computer over a network or the internet to manage your playlists and so on. There are some clients available for windows and osx too I think...

For more info: [http://www.musicpd.org/]("http://www.musicpd.org/")

---

### Post by Xappe on 2006-09-18
or try out orpheus, an ncurses based mp3-player (looks a bit like centericq)

---

