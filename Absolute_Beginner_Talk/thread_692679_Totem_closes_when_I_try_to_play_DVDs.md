---
title: "Totem closes when I try to play DVDs"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by Famicommander on 2008-02-10
I'm trying to watch a DVD, and Totem closes upon startup. Any ideas as to why this is happening? 

This is what I get when I run Totem in terminal:
```
jason@jason-desktop:~$ totem
libdvdnav: Using dvdnav version 1.1.7 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Attempting to use device /dev/scd0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/jason/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f60000. Regions: 1 4
libdvdnav: Suspected RCE Region Protection!!!

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0006dfd2
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x0006dfd2)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0007a0c8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00372091
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
AFD changed from -2 to -1
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 113 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

---

### Post by spiderbatdad on 2008-02-10
[http://ubuntuforums.org/showthread.php?t=661833&highlight=howto+multimedia](http://ubuntuforums.org/showthread.php?t=661833&highlight=howto+multimedia)

---

### Post by LookTJ on 2008-02-10
Why not try to use vlc?
```
sudo apt-get install vlc
```

Open vlc, File->Open Disc(assuming it is a dvd disc.

Note: You need to install dvd playback codecs I believe.

---

### Post by Famicommander on 2008-02-10
> **spiderbatdad said:**
> [http://ubuntuforums.org/showthread.php?t=661833&highlight=howto+multimedia](http://ubuntuforums.org/showthread.php?t=661833&highlight=howto+multimedia)

VLC just closes too.

---

### Post by Famicommander on 2008-02-10
This is what I get when I run VLC through terminal:
```
jason@jason-desktop:~$ vlc
VLC media player 0.8.6c Janus
[00000287] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:384000
ALSA lib setup.c:555:(add_elem) Cannot obtain info for CTL elem (MIXER,'IEC958 Playback Default',0,0,0): No such file or directory
No accelerated IMDCT transform found
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82
```

---

### Post by LookTJ on 2008-02-10
Install these:

```
 **sudo apt-get install libdvdcss2 libdvdread3  build-essential debhelper fakeroot**
```

then
```
**sudo /usr/share/doc/libdvdread3/install-css.sh
```**

---

### Post by Famicommander on 2008-02-10
They both say "insufficient resources", but my specs are better than my other computers running Ubuntu, and they all play DVDs just fine.

Here are my specs:
2.0ghz Pentium 4 processor
512MB RAM
ATi RAGE 128 graphics card

My other Ubuntu rigs are running on Celerons with ~256MB RAM and integrated video, but they all play DVDs fine.

---

### Post by Famicommander on 2008-02-10
> **Taylor said:**
> Install these:

```
 **sudo apt-get install libdvdcss2 libdvdread3  build-essential debhelper fakeroot**
```

then
```
**sudo /usr/share/doc/libdvdread3/install-css.sh
```**

Doesn't help. It still closes when I start the DVD.

---

### Post by LookTJ on 2008-02-10
> **Famicommander said:**
> They both say "insufficient resources", but my specs are better than my other computers running Ubuntu, and they all play DVDs just fine.

Here are my specs:
2.0ghz Pentium 4 processor
512MB RAM
ATi RAGE 128 graphics card

My other Ubuntu rigs are running on Celerons with ~256MB RAM and integrated video, but they all play DVDs fine.
Just wondering, what kind of media do you have? CD-RW/DVD or CD ROM? I would like the brand name, it may help.

---

### Post by Famicommander on 2008-02-10
Xine doesn't work either....

---

### Post by Famicommander on 2008-02-10
> **Taylor said:**
> Just wondering, what kind of media do you have? CD-RW/DVD or CD ROM? I would like the brand name, it may help.

CD/DVD-ROM.

EDIT: I'm not sure about the brand, but this is a Dell Optiplex GX240

---

### Post by spiderbatdad on 2008-02-10
To get encrypted DVDs playing properly (some newer ones still won't work for now), paste these commands into the Terminal;

sudo apt-get install libdvdcss2 libdvdread3 build-essential debhelper fakeroot

then;

sudo /usr/share/doc/libdvdread3/install-css.sh

To set VLC as your default DVD player (I strongly advise you do) type the following command into the Terminal;

gksudo gconf-editor

Now expand "desktop" and then "gnome", scroll down to "volume manager" but don't expand it, just click on it and look over at the right pane. Scroll down and look for "autoplay_dvd_command" and change the command to "/usr/bin/vlc dvd://" (without quotes of course) by right clicking on it and selecting "Edit", then click on "Set as Default". Do the same for the "autoplay_vcd_command" as well.

Note: If you wish to change the region of a DVD drive so you can play foreign discs, you will need to install the following terminal based application;

sudo apt-get install regionset

Please be aware that most drives limit you to about 5 changes (regionset should tell you how many you have left). So maybe it's best to have a secondary external DVD drive and have it set to a different region to the one in your machine. To make the change, put any disc into your drive and type "sudo regionset" into the Terminal and change the region. Here is the list of region codes and what countries they cover;

RC1 = North America (USA and Canada)
RC2 = Europe, Middle East, South Africa and Japan
RC3 = Southeast Asia, Taiwan, Korea
RC4 = Latin America, Australia, New Zealand
RC5 = Former Soviet Union (Russia, Ukraine, etc.), rest of Africa, India
RC6 = China


FROM: reassuringlyoffensive's Complete Streaming, Mutltimedia & Video How-to.

---

### Post by tyggna1 on 2008-02-10
Well, if X is sending you the error--then chances are that this computer just doesn't have enough "bang" to play this movie.  Try getting a really low resolution-peice-of-junk movie and running it.  I have a gx270, and the bus speed on that thing is barely capable of playing low-quality movies.

I vote for a hardware issue.

---

### Post by Famicommander on 2008-02-10
That doesn't help.

---

### Post by Famicommander on 2008-02-10
> **tyggna1 said:**
> Well, if X is sending you the error--then chances are that this computer just doesn't have enough "bang" to play this movie.  Try getting a really low resolution-peice-of-junk movie and running it.  I have a gx270, and the bus speed on that thing is barely capable of playing low-quality movies.

I vote for a hardware issue.

I swear, people don't even read my posts. This is a Pentium 4 2 ghz PC with 512MB of RAM, as I've already posted. I have Ubuntu running on three other machines, all of them with lower specs than this one, and all of them can play DVDs.

---

### Post by Famicommander on 2008-02-10
Update: it will play video files from my hard drive just fine. Just not DVDs.

---

### Post by zabien1970 on 2008-02-10
I couldn't get dvd's to play on my computer after installing compiz, totem kept crashing, never figured out why but turning compiz off helped   'metacity --replace'

---

### Post by Famicommander on 2008-02-10
> **zabien1970 said:**
> I couldn't get dvd's to play on my computer after installing compiz, totem kept crashing, never figured out why but turning compiz off helped   'metacity --replace'
How do I turn off Compiz?

---

### Post by zabien1970 on 2008-02-10
> **Famicommander said:**
> How do I turn off Compiz?

Hit Alt + f2 and type in metacity --replace then hit run

Edit: that's 2 minus signs before replace

---

