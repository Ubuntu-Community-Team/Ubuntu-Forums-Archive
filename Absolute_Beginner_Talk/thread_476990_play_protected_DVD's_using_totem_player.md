---
title: "play protected DVD's using totem player"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by hb0ss on 2007-06-17
Just new to Ubuntu and linux os..  Have installed latest version  7.04 and could play copy protected dvd's by installing the automatix css decoder/drivers.  I then install some additonal software including realplayer and crossover standard and now i can not play the protected dvd's. i have unistalled and re-installed the automatix drivers but still unable to play on the totem player.. get msg that libdvdcss is missing or not installed when attempting to run the dvd.   ??     Any help would be appreciated.

---

### Post by arnieboy on 2007-06-17
> **hb0ss said:**
> Just new to Ubuntu and linux os..  Have installed latest version  7.04 and could play copy protected dvd's by installing the automatix css decoder/drivers.  I then install some additonal software including realplayer and crossover standard and now i can not play the protected dvd's. i have unistalled and re-installed the automatix drivers but still unable to play on the totem player.. get msg that libdvdcss is missing or not installed when attempting to run the dvd.   ??     Any help would be appreciated.
you could have got an update from another repository which might have broken libdvdcss.
Please post the results of the following command:
```
cat /etc/apt/sources.list
```

---

### Post by steveneddy on 2007-06-17
Hey arnieboy - welcome back.

:)

---

### Post by arnieboy on 2007-06-17
> **steveneddy said:**
> Hey arnieboy - welcome back.

:)
hey steveneddy! Thanks :)

---

### Post by steveneddy on 2007-06-17
You're welcome.

[[IMG]http://img520.imageshack.us/img520/1544/postiig9bm6.gif[/IMG]](http://imageshack.us)

---

### Post by hb0ss on 2007-06-18
Hi Arnieboy, hope this is what you wanted, sorry for the delay..

hugo@hugo-laptop:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
hugo@hugo-laptop:~$

---

### Post by RomeReactor on 2007-06-18
Hi. **hb0ss**, do you have totem-gstreamer installed instead of totem-xine? If you do, try changing it; also, try this from the command line just to make sure ou have everything you need installed:
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3
```

---

### Post by Tomylee on 2007-06-18
Hi!

I just entered that command and I have everything installed. I have searched the posts here to get my dvdrw to read (it reads and rips cds however). I have downloaded about six players that people don't have problems with, codecs, and tried minor fiddles with fstab but to no avail.

I was going to start another post, but hey, two birds are better than one. 

(Don't mean to butt in hb0ss)

T

---

### Post by aberadam on 2007-06-18
The easy way:

1) Get rid of Totem Player using add/remove (I could never get it to work properly -- no menus).

2) Get VLC player using add/remove (play around with the settings to get it working properly, some of them are worded strangely and not explained too well). 

3) Go to Synaptic Package Manager in System > Administration

4) Select 'search', search for 'libdvd' -- install everything that's non-development and has 'libdvd' in the title.  You need to have all repositories enabled for this.

---

### Post by aberadam on 2007-06-18
To enable the correct resources go to System>Administration>Software Sources.  Tick all the boxes apart from the bottom one "source code".  

You don't even need to use the terminal. 

I'm a newbie myself and am impressed by the support on these forums -- but they always tell you to do it the "complicated way" using terminal commands.

---

### Post by RomeReactor on 2007-06-18
**Tomylee**, do you dual-boot into windows? if so, check there that it correctly reads the DVDs. I suspect it's hardware failure (I had one that did the exact opposite: I could read and burn DVDs, but not CDs).

**aberadam**, uninstalling the main media player in Ubuntu just because you "could never get it to work properly -- no menus" (I imagine you're referring to DVD menus here) seems a little bit unnecessary to me. Most likely you had that issue by having totem-gstreamer (no DVD menu, no subtitles) installed, instead of totem-xine (which correctly displays menus and subtitles, though you can't change their font and size due to a bug in xine). Just my opinion. And I agree that using the terminal (for the vast majority of beginners) *is* complicated, but most people here give you command-line instructions because they are a **much faster** way to solve problems than giving a step-by-step verbal guide for using a graphical interface. And as you become more experienced, you'll find that it's a *very* powerful tool. I also agree that, as a new user, you should **never have to** even *see* the terminal; but also take into account that posts featuring instructions on how to solve a particular problem using the GUI tend to become rather convoluted and difficult to understand (maybe it's just me, but I've had several instances of that).

As for **Tomylee**'s problem, he already stated that he has the required packages installed (check out the list of packages I asked **hb0ss** to install), and that he's "downloaded about six players that people don't have problems with, codecs, and tried minor fiddles with fstab but to no avail".
Sorry for the rant; I haven't had my morning coffee, and that in itself makes me crankier than usual. I apologize.

---

### Post by hb0ss on 2007-06-18
Finally got the protected DVD's to play:
Went to  [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_DVD_playback_capability](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_DVD_playback_capability)
and copied the following:

sudo apt-get install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
sudo apt-get install totem-xine

As others have said this player is little basic, but at least its usable. When i get a bit more confident i may consider load/ trying another.     thanks everyone.    :)

---

### Post by aberadam on 2007-06-18
RomeReactor, 

I think that if Ubuntu is ever going to go mainstream, to seriously challenge Windows, it has to get fresh users and not just consolidate from within the current Linux user base.  To do that means the end of the command line.  One has to be able to do everything graphically point 'n' click style because that's what the basic user wants and needs regardless of whether it's less efficient or not.  

The graphical way is the future.  Microsoft realised that years ago.

---

### Post by RomeReactor on 2007-06-18
**hb0ss**, glad to hear you got it working!

**aberadam**, I agree that most new users would be more than a little intimidated by the command line, and rightly so: it's a completely different environment from the graphical desktops they plan on leaving behind. A new user **must be able** to do whatever configuration he/she wants to do to the system from a graphical application. However, let's remember that Linux in general is developed by volunteers, in their own time; and development, in most instances, isn't as fast as could be afforded by a multi-billion dollar corporation. And I disagree that for Linux to be adopted by the mainstream user, the command line must die. Like I said, a new user *must* be able to do everything from a graphical environment, but that doesn't mean that more advanced users won't choose to do some--if not most--things using the command line: it *is* faster for many operations...

> The graphical way is the future. Microsoft realised that years ago.

Actually, that was microsoft taking that idea from [apple]("http://en.wikipedia.org/wiki/Apple_Macintosh#Litigation"), who had previously taken it from [xerox]("http://en.wikipedia.org/wiki/Graphical_user_interface#Precursors_to_graphical_user_interfaces"). Check out [Pirates of Silicon Valley]("http://www.imdb.com/title/tt0168122/") for a very entertaining (in my opinion) look at that particular era in personal computing.

---

### Post by waiverider on 2007-06-19
> **aberadam said:**
> The easy way:

1) Get rid of Totem Player using add/remove (I could never get it to work properly -- no menus).

2) Get VLC player using add/remove (play around with the settings to get it working properly, some of them are worded strangely and not explained too well). 

3) Go to Synaptic Package Manager in System > Administration

4) Select 'search', search for 'libdvd' -- install everything that's non-development and has 'libdvd' in the title.  You need to have all repositories enabled for this.

Thank you sooooo much aberadam! This worked perfectly I can now play dvds in both Totem and VLC!!!  I am new to Linux and Ubuntu and quite frankly wish it was more end-user friendly but this at least was not difficult. Too bad this is not included in the docs!..Anyway, thanks again for the great instructions!:D

---

### Post by Tomylee on 2007-06-21
Hi - thanks for the reply. Sorry it took me a while to respond, I just finished exams today!

Rome reactor, I'm pretty sure the DVD drive is working as I just installed Ubuntu over the top of XP and it was working fine.

Would you mind checking my fstab?


> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ea61d1a6-7213-4bb2-bd1f-41eb4254c6e9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=de491d15-69cd-40f3-8886-d12536e4a129 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   auto    rw,user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Tomylee on 2007-06-25
Should I start a new thread?

---

### Post by RomeReactor on 2007-06-28
Sorry for the late reply! I don't know much about fstab, but the entries for my DVD reader and writer look somewhat different than your DVD and floppy:
> # /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda1 :
UUID=b8f72a5d-8844-4bc2-a2d2-9320dc86810f / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=cf4ed609-0f12-489b-8ce0-470c2e2075a7 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
Again, I don't know anything useful to help you there. If you get to read this, try with a new thread or ask in the IRC forums (**#ubuntu** in **irc.freeenode.net**).

---

### Post by Tomylee on 2007-07-07
Thanks RomeReactor,

I don't really know much about fstab either. I'll take your advice and start another post.

Thanks for getting back! :D

Tomylee

---

