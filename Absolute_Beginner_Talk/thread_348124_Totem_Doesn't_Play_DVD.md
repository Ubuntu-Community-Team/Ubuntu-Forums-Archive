---
title: "Totem Doesn't Play DVD"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by mengd2002 on 2007-01-28
Totem won't play DVD movies.  When I insert a DVD movie into my DVD drive, after a few seconds Totem comes up and displays the following message "Totem could not play 'dvd:///media/cdrom0'.  No URL header implemented for "dvd" ".

How do I watch DVD movies in Ubuntu?  This is a DVD I rented from Blockbuster and it plays just fine in my DVD player.  Thanks for any help you can give.

Don

---

### Post by taurus on 2007-01-28
I would recommend vlc for that.  It's in the repos.  Here's a link for you to read over.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

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

### Post by bred on 2008-02-27
thank you guys!

---

### Post by philidox on 2008-02-27
post it as solved, that way people know where to go to or bookmark this page

---

