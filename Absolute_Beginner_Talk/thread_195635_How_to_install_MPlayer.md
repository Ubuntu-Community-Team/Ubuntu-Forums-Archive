---
title: "How to install MPlayer"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by drix on 2006-06-13
I just downloaded MPlayer at Ubuntu Linux all files are written like c++, guys plz help  me up.... just a beginner here... thanks

---

### Post by Hanj on 2006-06-13
Sounds like you downloaded the source code. Don't do this unless you really need to. Intead, when installing applications, open Synaptic package manager, search for the program and select install. Then click apply. Simple as that.

---

### Post by johso on 2006-06-13
You can do it with Synaptic/apt-get, but you probably need to enable the backports/universe repos.
Check if it is there first though, then this procedure is unnecessary (but adds a lot of programs to synaptic, though, so it wouldn't hurt).
```

sudo gedit /etc/apt/sources.list

```
Uncomment both deb and deb-src for both backports and universe.
Save it, open a terminal (Alt+F2, xterm) and do a:
```

sudo apt-get update

```

Now you can either go to Synaptic and find MPlayer, or, from the terminal, type:
```

sudo apt-get install mplayer

```

---

### Post by frodon on 2006-06-13
You should read that to understand how works ubuntu : 
[http://ubuntuforums.org/showthread.php?t=153118](http://ubuntuforums.org/showthread.php?t=153118)

---

### Post by ivangotoy on 2006-06-13
i have a nice howto for mplayer - tested on breezy badger and dapper drake .

i have installed mplayer 2 ties on each distro (after reinstall) each time mplayer appear to be 

as good as you cannot imagine now i will quote the howto

i want to stress : I HAVE NOT WRITTEN THE HOWTO FOR MPLAYER - i am just trying 

to help you guys :)

so here i go - the next lines are just quoted from txt document on my hard drive:
******************************************************************************************** 
** UPDATED **
 Per post: [http://ubuntuforums.org/showpost.php...6&postcount=48](http://ubuntuforums.org/showpost.php...6&postcount=48)
 
 // Ubuntu Multimedia HOWTO
 //
 // by Disposable
 //
 // [http://www.oldskoolphreak.com](http://www.oldskoolphreak.com)
 
 
 Introduction
 ------------
 "Will Warty Warthog / Ubuntu include complete multimedia support?"
 
 Ubuntu Linux [1] is a Debian-based, desktop Linux distribution whose name
 means "humanity to others." The philosophy behind this GNU/Linux
 distribution and the great selection of packages make you feel good that
 you're using it. The lack of multimedia support, however, leaves your
 digital media desires unsated.
 
 "We're still working out some of the difficult legal / policy issues
 involved with multimedia support. Warty Warthog will include some
 multimedia support, we just need to find out what we can safely and freely
 do."
 
 This HOWTO details the installation and configuration of applications
 essential to your media enjoyment on Ubuntu.
 
 
 Update It
 ---------
 If you've installed Ubuntu, and you should have a fresh install for this
 HOWTO, then you're already familiar with its default use of sudo. You'll
 be using sudo a lot.
 
 The first step towards an Ubuntu multimedia powerhouse is to make sure your
 box is up-to-date [2].
 
 $ sudo apt-get update
 $ sudo apt-get upgrade
 $ sudo apt-get dist-upgrade
 
 
 MPlayer
 -------
 It's time to grab all of the packages needed to install MPlayer. MPlayer
 is the most versatile media player available for GNU/Linux - video, audio,
 X, no X - it very well may be the only player you'll need. Let's start with
 gcc/g++ and other dependencies, and then grab the MPlayer source.
 
 $ sudo apt-get install manpages-dev
 $ sudo apt-get install autoconf
 $ sudo apt-get install automake
 $ sudo apt-get install libtool
 $ sudo apt-get install flex
 $ sudo apt-get install bison
 $ sudo apt-get install gcc-doc
 $ sudo apt-get install g++
 $ sudo apt-get install x-window-system-dev
 $ sudo apt-get install libgtk1.2-dev
 $ sudo apt-get install libpng-dev
 
 Have your Warty Warthog CD handy and accept any extra packages, e.g. the
 libtool install will also install gcc. We'll use a US mirror for (most of)
 the MPlayer packages and assume you're working in your home directory.
 Download MPlayer, codecs, English fonts and the default blue skin.
 Internationalization and slick graphics are up to you.
 
 $ wget [http://ftp5.mplayerhq.hu/mplayer/rel....0pre5.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/rel....0pre5.tar.bz2)
 $ wget [http://ftp5.mplayerhq.hu/mplayer/rel...040922.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/rel...040922.tar.bz2)
 $ wget [http://ftp5.mplayerhq.hu/mplayer/rel...8859-1.tar.bz2](http://ftp5.mplayerhq.hu/mplayer/rel...8859-1.tar.bz2)
 $ wget [http://www1.mplayerhq.hu/MPlayer/Skin/Blue-1.4.tar.bz2](http://www1.mplayerhq.hu/MPlayer/Skin/Blue-1.4.tar.bz2)
 
 Using the README from mplayerhq.hu [3] as a baseline, install the codecs
 with the following commands.
 
 $ tar -xjf essential-20040922.tar.bz2
 $ sudo mkdir -p /usr/local/lib/codecs
 $ sudo cp essential-20040922/* /usr/local/lib/codecs/
 
 Time to compile MPlayer. Issue these commands.
 
 $ tar -xjf MPlayer-1.0pre5.tar.bz2
 $ cd MPlayer-1.0pre5
 $ ./configure --enable-gui
 $ make
 $ sudo make install
 
 Now install the fonts and skin.
 
 $ cd
 $ tar -xjf font-arial-iso-8859-1.tar.bz2
 $ sudo cp font-arial-iso-8859-1/font-arial-14-iso-8859-1/* /usr/local/share/mplayer/font/
 $ tar -xjf Blue-1.4.tar.bz2
 $ sudo mkdir -p /usr/local/share/mplayer/Skin/default
 $ sudo cp -r Blue/* /usr/local/share/mplayer/Skin/default/
 
 Finally, copy over the included conf files.
 
 $ sudo cp MPlayer-1.0pre5/etc/* /usr/local/etc/mplayer/
 
 Test your install by launching the graphical version of MPlayer.
 
 $ gmplayer
 
 QuickTime, WindowsMedia, MPEG, avi - you should be able to play just about
 anything. Give yourself quick access to MPlayer by adding a launcher to
 the top GNOME panel. Right click on the panel and click Add to Panel...
 Select Custom Application Launcher and click Add. Use the following
 information and click OK.
 
 Name: MPlayer
 Command: /usr/local/bin/gmplayer
 Icon: /usr/local/share/mplayer/Skin/default/icons/32x32.png
 
 
 Playing DVDs
 ------------
 The Ubuntu Wiki discusses restricted formats [4], which include CSS and
 DVD playback. To add DVD playback capability to Ubuntu, use your favorite
 text editor and add the following line to your /etc/apt/sources.list file.
 
 deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
 
 Then sync your package index and grab the infamous DeCSS.
 
 $ sudo apt-get update
 $ sudo apt-get install libdvdcss2
 
 Add a dvd link and enjoy DVDs with MPlayer and Ubuntu.
 
 $ sudo ln -s /media/cdrom0 /dev/dvd
 
 
 XMMS
 ----
 With your video needs taken care of, we can move on the audio portion of
 our show by installing XMMS.
 
 $ sudo apt-get install libmikmod2
 $ sudo apt-get install xmms
 
 Logging out and logging back in will find XMMS already in the Applications/
 Multimedia menu. And there it is - instant Ogg/mp3/jukebox/streaming audio
 goodness.
 
 
 A Little Perl
 -------------
 For streaming internet radio, you can of course use XMMS. Set your
 preference in Firefox and you're good to go. I listen to a few stations
 regularly, and I always have a gnome-term open. With those things in mind,
 I've found it much more convenient to write a Perl script that uses MPlayer
 to stream my favorite music.
 
 
Code:
#!/usr/bin/perl -w
 
        # mplay.pl -
        # command line streaming of your fav stations
        # usage: mplay <channel>
 
        use strict;
 
        help() unless defined(my $chan = shift);
 
        if ($chan =~ /bass/) {
                system("mplayer http://us-dc1.streams.bassdrive.com:8012");
        }
        elsif ($chan =~ /cryo/) {
                system("mplayer http://207.200.96.225:8022");
        }
        elsif ($chan =~ /di/) {
                system("mplayer http://64.235.239.5:8006");
        }
        elsif ($chan =~ /ind/) {
                system("mplayer http://130.240.207.88:9090");
        }
        elsif ($chan =~ /talk/) {
                system("mplayer http://broadcast.rantradio.com:9010");
        }
        else { help(); }
 
        sub help {
 
        print <<EOF;
 
        Usage: mplay <channel>
 
        Channels:
        bass - BassDrive
        cryo - Cryosleep
        di   - Digitally Imported
        ind  - RantRadio Industrial
        talk - RantRadio Talk
 
        EOF
 
        exit;
        }

 "mplay ind" plays RantRadio's 128-bit industrial stream quickly and
 without a browser. If you need your terminal, "q" stops the stream, do
 your deed, and up arrow gets the stream right back (or of course Ctrl+
 Shift+T for a new tab in gnome-terminal).
 
 
 Conclusion
 ----------
 Ubuntu Linux is an impressive distribution. Even more impressive is the
 conviction of the developers. "The most important thing about Ubuntu is
 not that it is available free of charge, but that it confers rights of
 software freedom on the people who install and use it." They put their
 money where their apt is. So as a GNU/Linux user, the tasks detailed
 above are trivial compared to the decisions made not to include such
 support.
 
 Please support free software developers. Continue to use Ubuntu.
 Contribute to the Ubuntu Linux community. And watch Batman: Dead End
 while you're doing it [5].
 
 
 References
 ----------
 [1] [http://www.ubuntulinux.org/](http://www.ubuntulinux.org/)
 
 [2] I could not intuitively get Rhythmbox to play one simple Ogg file. So
 my first step in setting up multimedia on Ubuntu is to sudo apt-get
 remove rhythmbox.
 
 [3] [http://www.mplayerhq.hu/DOCS/README](http://www.mplayerhq.hu/DOCS/README)
 
 [4] [http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats)
 
 [5] [http://www.theforce.net/theater/shor...atman_deadend/](http://www.theforce.net/theater/shor...atman_deadend/)
 Last edited by ubuntu-geek : October 29th, 2004 at 12:57 PM. 





i hope you enjoy watching all the staff of different media formats

just a simple piece of advice - install all codecs pack in the mentionted dir before 

compiling , skin and subtitles could be fixed either before or after installation

enjoy :)

---

