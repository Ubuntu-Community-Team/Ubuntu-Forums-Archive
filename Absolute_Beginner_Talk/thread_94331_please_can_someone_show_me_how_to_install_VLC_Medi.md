---
title: "please can someone show me how to install VLC Media"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by Danielle on 2005-11-23
hi, i really want to listen to an MP3 stream. with windows i never download mp3's but tell VLC to play the URL live. i have tried to install VLC and tried to edit the source list but it was write protected :( can someone show me how to install it please? once it's installed can i listen to an mp3? or do i have to do something with codecs? thanks.

[http://www.videolan.org/vlc/download-debian.html](http://www.videolan.org/vlc/download-debian.html)

---

### Post by Grimoire on 2005-11-23
Hi there

In a terminal type:

```
sudo gedit /etc/apt/sources.list
```

Then you can add sources to it. My sources list for example:

```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sarge main
     
deb-src [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sarge main

```

I added the last two for vlc to work.

Then simply

```
sudo apt-get install vlc
```

That should install VLC and it should all be working. It shouldn't require any extra codecs to listen to a streamed mp3.

Hope that all works!

---

### Post by Danielle on 2005-11-23
[QUOTE=Grimoire]

Hope that all works![/QUOTE]
i hope so too :D i'll try it out in a few minutes, thanks for the help, Grimoire

---

### Post by Grimoire on 2005-11-23
Don't worry about it - I only got Ubuntu about 2 weeks ago and I remember how useful these forums were for me! (and still are when I manage to break things... :p  )

---

### Post by Danielle on 2005-11-23
[QUOTE=Grimoire]Don't worry about it - I only got Ubuntu about 2 weeks ago and I remember how useful these forums were for me! (and still are when I manage to break things... :p  )[/QUOTE]
yes, it's very good here. 

thanks again, but it wouldn't install, it says there maybe a bug. here's part of the error:

The following packages have unmet dependencies:
  vlc: Depends: liba52-0.7.4 but it is not installable
       Depends: libid3tag0 (>= 0.15.1b) but it is not installable
       Depends: libmad0 (>= 0.15.1b) but it is not installable
       Depends: libmodplug0c2 (>= 1:0.7-4.1) but it is not installable
       Depends: libmpeg2-4 but it is not installable
       Depends: wxvlc but it is not going to be installed
E: Broken packages

do you think i should try this mirror:
[http://www.fr.videolan.org/vlc/download-debian.html](http://www.fr.videolan.org/vlc/download-debian.html)

---

### Post by Ruso on 2005-11-23
Danielle try install it using the synaptic

sudo synaptic

then just use "search"  to find the VLC and install it. At least it worked for me doing it this way!.

---

### Post by Grimoire on 2005-11-23
I just removed and reinstalled VLC using those sources and it worked fine. Also - in Synaptic on my installation all of the dependencies are already installed.

Try this:

```
sudo apt-get install liba52-0.7.4 libid3tag0 libmad0 libmodplug0c2 libmpeg2-4
```

Then try to reinstall VLC and see what happens.

---

### Post by Danielle on 2005-11-23
[QUOTE=Ruso]Danielle try install it using the synaptic

sudo synaptic

then just use "search"  to find the VLC and install it. At least it worked for me doing it this way!.[/QUOTE]
i just got the same error, maybe it's something i did eariler. there are afew search results and i double-clicked on VLC. maybe i should try MPlayer. oh, when i did the search i searched in "name" where should i search? there are other options

---

### Post by Danielle on 2005-11-23
[QUOTE=Grimoire]I just removed and reinstalled VLC using those sources and it worked fine. Also - in Synaptic on my installation all of the dependencies are already installed.

Try this:

```
sudo apt-get install liba52-0.7.4 libid3tag0 libmad0 libmodplug0c2 libmpeg2-4
```

Then try to reinstall VLC and see what happens.[/QUOTE]
this is what happened when i ran the code:

Reading package lists... Done
Building dependency tree... Done
Package liba52-0.7.4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [http://download.videolan.org](http://download.videolan.org) sarge/main Packages (/var/lib/apt/lists/download.videolan.org_pub_videolan_debian_dists_sarge_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package liba52-0.7.4 has no installation candidate

i'll try the install now

---

### Post by Danielle on 2005-11-23
this is the error i get when i start: sudo synaptic

W: Couldn't stat source package list [http://download.videolan.org](http://download.videolan.org) sarge/main Packages (/var/lib/apt/lists/download.videolan.org_pub_videolan_debian_dists_sarge_main_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by Xian on 2005-11-23
[QUOTE=Danielle]i just got the same error, maybe it's something i did eariler. [/QUOTE]
I don't see where it has been established that your source list is properly set-up. Can we do that before going on to some other steps? If you are using Breezy your /etc/apt/sources.list needs to look similar to the example below. If it does not, then please edit the file on your system so they are similar. Afterwards, do an 'apt-get update' session from a terminal and then try to install vlc.

```
## Breezy Primary Repositories
deb http://archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

```

```
$ sudo gedit /etc/apt/sources.list
$ sudo apt-get update
$ sudo apt-get install vlc
```

---

### Post by Danielle on 2005-11-23
Wow, that was brilliant. i got 36 updates next to my clock too. and VLC is in with all the other media stuff now. 

i cut and pasted the whole of your list. the first time i just copied the last two lines. 

is this how i get updates for my system?
sudo apt-get update

thanks for the help :)

---

### Post by Grimoire on 2005-11-23
I apologise - I just realised now that I forgot to include the update command for apt-get!

---

### Post by Xian on 2005-11-23
[QUOTE=Danielle]is this how i get updates for my system?
sudo apt-get update

thanks for the help :)[/QUOTE]
That is how you update the cache of available packages. In Synaptic the same function is accomplised by clicking the 'Reload' button. You can do an upgrade via the update-notifier, Synaptic, or the command line.

---

### Post by Danielle on 2005-11-23
no problem, Grimoire. i'm happy to get some help. i can help anyone with windows security if you're interested :D :D

thanks, Xian too. can i ask one more thing? i have BitDefender-Console-Antivirus-7.1-3.linux-gcc3x.i386.deb
on my desktop to install. is there a different command for .deb archives? thanks

so i should update all those 36 updates, they're not Xian's updates that i just pasted into the list? thanks for the help :)

---

### Post by Grimoire on 2005-11-24
> i have BitDefender-Console-Antivirus-7.1-3.linux-gcc3x.i386.deb
on my desktop to install. is there a different command for .deb archives?

In a terminal do:

```
cd <path of the deb package
sudo dpkg -i <name of the deb package>.deb
```

That will install the .deb package for you!

---

### Post by Danielle on 2005-11-24
thanks, Grimoire. it installed. i hate asking all these questions, but where is it? i looked through the Applications on the panel, but it's not there. thanks

---

### Post by Grimoire on 2005-11-24
Try restarting. If that doesn't work then you could always launch from terminal! I'm not sure of the command but it's probably just

```
bitdefender
```

If you want a more elegant solution, you could always add an application launcher to your panel:

1. Right click on where you wish to place the launcher on your panel.

2. Choose "Add to panel"

3. Choose "Custom application launcher"

4. Choose an icon, name, etc.

5. Where it says "Command" simply type the same command that launches from terminal, again a guess but probably

```
bitdefender
```

6. Click ok and use the launcher to run the software!

I hope that works for you!

---

