---
title: "Totem will not play DVD"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by olddave on 2006-01-28
As the title says, new install of ubuntu will not play DVDS do i need to install any plugins or anything.
Other than this very happy with the install so far.
olddave

---

### Post by bloodborne on 2006-01-28
The easiest way to get all that stuff up and running is with Automatix, which you can get here:

[http://ubuntuforums.org/showthread.php?t=80295](http://ubuntuforums.org/showthread.php?t=80295)

Just a warning, though, DVD codecs are non-free and illegal to use on Linux systems inside the United States.

---

### Post by hen3rz on 2006-01-28
> As the title says, new install of ubuntu will not play DVDS do i need to install any plugins or anything.
Other than this very happy with the install so far.

Hello,

If your not comfortable with automatix doing everything for you. You can do it all manually by having a read of this wiki:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by kingsidy on 2006-01-28
give automatix a shot before trying it our manually. I have used it in a system i installed recently, it is pretty good now compared to before. plus while using you should be able to install other applications that could be of use

---

### Post by mstlyevil on 2006-01-28
I can say that Automatix has never caused me a problem. You should try it first because it will save you a lot of time on getting your new Ubuntu install up and running. If you have a Nvidia graphics card, you can also get the drivers for it installed in Automatix.

---

### Post by olddave on 2006-01-28
Used automatix and then tried to play DVD and got this message,
There were no decoders found to handle the stream, you might need to install the corresponding plugins.
Automatix make using ubuntu so much easier to use for updating and installing software.
olddave

---

### Post by derspiess on 2006-01-28
Okay, stupid question.  I liked pretty much everything Automatix installs, but after typing the 3 commands listed in the link, nothing seems to have installed.  Is there something else I need to do?  Here is what I saw when I typed the commands; seemed to happen awfully quickly for all that to have installed:

shayne@linux:~$ sudo apt-get install xterm
Password:
Reading package lists... Done
Building dependency tree... Done
xterm is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
shayne@linux:~$ wget [http://beerorkid.com/automatix/automatix_5.0-2_i386.deb](http://beerorkid.com/automatix/automatix_5.0-2_i386.deb)
--21:08:45--  [http://beerorkid.com/automatix/automatix_5.0-2_i386.deb](http://beerorkid.com/automatix/automatix_5.0-2_i386.deb)
           => `automatix_5.0-2_i386.deb.1'
Resolving beerorkid.com... 205.196.218.206
Connecting to beerorkid.com|205.196.218.206|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 32,196 (31K) [text/plain]

100%[====================================>] 32,196        96.89K/s

21:08:46 (96.65 KB/s) - `automatix_5.0-2_i386.deb.1' saved [32196/32196]

shayne@linux:~$ sudo dpkg -i automatix_5.0-2_i386.deb
(Reading database ... 67198 files and directories currently installed.)
Preparing to replace automatix 5.0-2 (using automatix_5.0-2_i386.deb) ...
Unpacking replacement automatix ...
Setting up automatix (5.0-2) ...

---

### Post by olddave on 2006-01-28
As i am new to all things ubuntu but all looks ok did you look in system tools if it is in there it should be ok,
olddave

---

### Post by derspiess on 2006-01-28
[QUOTE=olddave]As i am new to all things ubuntu but all looks ok did you look in system tools if it is in there it should be ok,
olddave[/QUOTE]

Yep, it's there (didn't think to look there- duh!).  I thought it would install everything after typing those commands.    Looks like it's installing everything I selected as I type this. 

Very cool-- I didn't seem to have codecs to play *any* video files I wanted to watch.

---

### Post by philidox on 2008-02-26
Alright this is how to get totem to play dvd's!!!  You should mark this SOLVED after these instructions or just follow this link [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

RestrictedFormats/PlayingDVDs

Contents

   1. Starting Fresh with xine Based Players
   2. Installing libdvdcss2
   3. Setting DVD Region Codes
   4. Troubleshooting

Most commercial DVDs are encrypted with CSS (the Content Scrambling System), which attempts to restrict the software that can play a DVD.

By installing the libdvdcss2 package you can play encrypted DVDs with:

    *

      Kaffeine, the Kubuntu video player
    *

      MPlayer
    *

      xine
    *

      Totem-xine
    *

      VLC media player

Note : While Totem-gstreamer can play a DVD automatically when it is inserted into the DVD drive, it cannot navigate the DVD nor play it by selecting Movie &#8594; Play Disc 'DVD Name' (see [WWW] Bug #41335). If you use vlc media player you can navigate through the menu, forward in the movie and select subtitles. Just select open disc, probe Disc(s) and click ok.
Starting Fresh with xine Based Players

After doing a fresh install of any one of the Ubuntu-based Linux distributions, some packages needed for DVD playback are not installed by default because of Ubuntu's commitment to completely free multimedia formats. This section covers what packages are needed and how to acquire and install them onto your system.

    *

      Ubuntu 7.10 "Gutsy Gibbon"

In gutsy to get encrypted DVD playback to work i had to do the following:

sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
sudo /usr/share/doc/libdvdread3/install-css.sh

After that, running gxine from the Applications -> Sound and Video menu played the DVD perfectly. I found this tip at: [WWW] [http://yoten.blogspot.com/2007/10/play-encrypted-dvds-under-ubuntu-gutsy.html](http://yoten.blogspot.com/2007/10/play-encrypted-dvds-under-ubuntu-gutsy.html) cheers random website!

    *

      Ubuntu 7.04 "Feisty Fawn"

After doing a fresh install of Feisty, be it Ubuntu or Kubuntu, there are two packages not installed by default that need to be installed for DVD playback to work. There's a third package needed to play encrypted DVDs. They are:

    *

      libdvdread3
    *

      libxine1-ffmpeg (Also requires libmad0, therefore libmad0 will be installed automatically along with this package)
    *

      libdvdcss2 (Needed to play encrypted DVDs)

libdvdread3 and libxine1-ffmpeg are in the Ubuntu repository. To install them through the command line, type the following:

sudo apt-get install libdvdread3 libxine1-ffmpeg

libdvdcss2 is not part of the Ubuntu repository because of Ubuntu's commitment to completely free multimedia formats. The next section explains how to acquire libdvdcss2.
Installing libdvdcss2

If you are using Ubuntu 6.06 "Dapper Drake":

    *

      Install the libdvdread3 package from the universe repository.
    *

      Open a terminal and type

      sudo /usr/share/doc/libdvdread3/examples/install-css.sh

      and press the enter key. This will download and install libdvdcss2.

If you are using Ubuntu 6.10 "Edgy Eft":

    *

      Install the libdvdread3 package from the universe repository.
    *

      Open a terminal and type

      sudo /usr/share/doc/libdvdread3/install-css.sh

      and press the enter key. This will download and install libdvdcss2.

If you are using Ubuntu 7.04 or later:

    *

      Install the libdvdcss2 package after adding the unsupported third-party repository Medibuntu.

Your DVD player should now play back encrypted DVDs.
Setting DVD Region Codes

    *

      If your DVD player regularly locks up when you try to play back a DVD, your DVD player probably does not match the DVD's [WikiPedia]Region Code. Region Codes are a form of vendor lock-in. For example, you cannot play a DVD published in Japan (Region 2) on a DVD player in the United States (Region 1) without changing the Region Code of the DVD player (unless you own a region free DVD player). You can view or modify the Region Code of your DVD drive with the [WWW] regionset tool.

      warning.png
      [WWW] The author of regionset writes: "On delivery, most DVD drives have no region code set. The drive firmware allows you to change the region code, but on nearly all drives you are limited to five (5) changes. After the fifth change, the DVD drive will stay fixed on that code -- on some drives you can upgrade the drive firmware and have then additional five changes, on other drives you won't be able to change the region code any more."
    *

      Most players (eg mplayer/vlc) with most DVD drives are able to ignore the value of the region setting. However, it must have been set to something; if it hasn't been initialized, even non-region-restricted DVDs won't play. Also, if it is necessary to crack the CSS key, it can sometimes take up to a few minutes to do so.


    *

      To change the Region Code of your DVD player, insert a DVD from your region in the DVD player, and do the following:
          o

            Install the regionset package from the Universe repositories.
          o

            To launch regionset, issue the command

            regionset

          o

            See the Free Formats page for more information

Troubleshooting

    *

      Jerky Playback
          o

            If DVD playback is noticeably choppy or burning a CD/DVD is slower than it should be, then you may need to enable DMA transfer for the DVD drive. See the DMA (Direct Memory Access) page for details.

---

