---
title: "how do I make the media player work"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by khris on 2007-07-25
The rythmbox music player keeps telling me I need to download some kind of plugin before I can play music!:(

---

### Post by srt4play on 2007-07-25
Probably a plugin for mp3 playback.  The quickest way is to double-click an mp3 file in your file browser.  It will open with the totem media player by default and prompt you to let it download the codec to play mp3 files.  Then you can re-open rythmbox and the files will play.

---

### Post by linuxwizard on 2007-07-25
Have you installed the multimedia codecs ? If not follow my post here to install them
[http://ubuntuforums.org/showthread.php?t=508693](http://ubuntuforums.org/showthread.php?t=508693)



[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by khris on 2007-07-25
I can't get internet on that computer yet.

Is there some way I could download the packages on to a different computer and then transfer them to my ubuntu computer?

---

### Post by srt4play on 2007-07-26
Sure, go to [http://packages.ubuntu.com](http://packages.ubuntu.com).  Do a search for libmad0.  There will be two results you only need the first one.  Click on the word feisty underneath where it says Package:libmad0, then click on i386 underneath where it says Download libmad0.  Then choose a mirror to download from to get the .deb file.  Once you transfer the .deb to your computer just double-click it to install.

---

### Post by khris on 2007-07-26
After I installed the package, some of the files played, but most of them did not.  Is this because they are protected?

---

### Post by RomeReactor on 2007-07-27
Hi. Are the problematic files in a format other than MP3?

---

### Post by khris on 2007-07-27
Yes, most of them are not mp3.  but the mp3's won't even play.  It will only play WAV files.

---

### Post by RomeReactor on 2007-07-27
Most likely you haven't installed **gstreamer0.10-plugins-ugly** and **gstreamer0.10-plugins-ugly-multiverse**. The first one is required for Rhythmbox to play MP3 files; the other one is its multiverse variant. Doesn't hurt to install both, though you only really need the first:
```
sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```
It is always useful, when searching and finding an application in Synaptic, to right-click on the program and see what it lists under **Mark Recommended for Installation** and **Mark Suggested for Installation**, as usually installing those packages give the program much more functionality and prevent future headaches, like in this case.

---

### Post by khris on 2007-07-29
Could you tell me how to do this on a different computer and then transfer it to my linux computer?

---

### Post by RomeReactor on 2007-07-29
Is there a way you can get a wired internet connection for your Ubuntu system? It would probably be very problematic to download the packages from **packages.ubuntu.com** since you need to satisfy the dependencies for these libraries, and those dependencies might have dependencies themselves.

If you can't get a wired connection, then download the packages [here]("http://packages.ubuntu.com/feisty/libs/gstreamer0.10-plugins-ugly") and [here]("http://packages.ubuntu.com/feisty/libs/gstreamer0.10-plugins-ugly-multiverse"). 

Once you move them to your Ubuntu system, you install them by double-clicking on them. They probably won't be able to install due to not having certain dependencies installed, so take note of the missing ones and search for them [here]("http://packages.ubuntu.com/").

Also, in what format are the other files Rhythmbox can't play?

---

### Post by nmcvicar on 2007-07-30
I ran the line of code posted by RomeReactor. I got the foutput below (notice the errors at the end). 
ONe of the error messages - "`perl-modules' is missing final newline" - has popped up when I've tried (unsuccessfully) to install other applications.  Does this mean I need to reinstall Ubuntu? 

Thank you,
Neil

nmcvicar@nmcvicar-desktop:~$ 
nmcvicar@nmcvicar-desktop:~$ sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  liba52-0.7.4 libdvdread3 libid3tag0 liblame0 libmad0 libmpeg2-4 libsidplay1
Suggested packages:
  libdvdcss2 debhelper fakeroot sidplay-base xsidplay
The following NEW packages will be installed:
  gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
  liba52-0.7.4 libdvdread3 libid3tag0 liblame0 libmad0 libmpeg2-4 libsidplay1
0 upgraded, 9 newly installed, 0 to remove and 112 not upgraded.
Need to get 763kB of archives.
After unpacking, 2232kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe liba52-0.7.4 0.7.4-7 [26.4kB]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe libdvdread3 0.9.7-2ubuntu1 [57.7kB]
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libid3tag0 0.15.1b-8 [34.9kB]
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libmad0 0.15.1b-2.1 [76.9kB]
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe libmpeg2-4 0.4.1-1 [64.1kB]
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe libsidplay1 1.36.59-4 [65.9kB]
Get:7 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe gstreamer0.10-plugins-ugly 0.10.5-0ubuntu2 [207kB]
Get:8 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse liblame0 3.96.1-2ubuntu1 [190kB]
Get:9 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse gstreamer0.10-plugins-ugly-multiverse 0.10.5-2 [40.0kB]
Fetched 763kB in 7s (95.4kB/s)                                                 
Selecting previously deselected package liba52-0.7.4.
(Reading database ... dpkg: error processing /var/cache/apt/archives/liba52-0.7.4_0.7.4-7_i386.deb (--unpack):
 files list file for package `perl-modules' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/liba52-0.7.4_0.7.4-7_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
nmcvicar@nmcvicar-desktop:~$

---

### Post by RomeReactor on 2007-07-30
Hi **nmcvicar**. There's a line missing in **/var/lib/dpkg/info/perl-modules.list**. To fix that, you need to open a root terminal, so press ALT+F2 and enter:
```
gksu /usr/bin/x-terminal-emulator
```
Once it pops up, enter the following:
```
echo -en '\n' | sudo tee -a /var/lib/dpkg/info/perl-modules.list
```
close the root terminal, open a 'normal' terminal and enter:
```
sudo apt-get update
```
and then try installing the Gstreamer packages again.

Thanks to [bapoumba and blightc]("http://ubuntuforums.org/showthread.php?t=494321") for finding the bug and the fix.

---

### Post by nmcvicar on 2007-07-30
thanks RomeReactor but.....

I can't even get a root terminal to open (Alt + F2 did nothing). I suppose my keyboard is not set up correctly. 

I have another thread [http://ubuntuforums.org/showthread.php?t=511780](http://ubuntuforums.org/showthread.php?t=511780) in which Forestpixie was trying to guide me through some other errors I keep getting (related to perl-modules not being installed correctly). I think I should work on getting that issue resolved before worring too much about codecs.

Thank you again,

Neil

---

### Post by forestpixie on 2007-07-30
no no it's the same issue :)

Edit - and the link RomeReactor is pointing you at is the same one I was pointing you at the other night

---

### Post by forestpixie on 2007-07-30
if you can't open it with Alt + F2 - you can get a root terminal in system tools - but I would get rid of it afterwards - you could cause serious damage using it.

Right click menu bar and edit menus - go to system tools and tick root terminal. I tshould appear in your system tools menu. 

Then you should be able to follow RomeReactors post - don't try to type it though make sure you copy and paste it.

And remember that root terminal can be dangerous.

---

### Post by sailor2001 on 2007-07-30
it's not dangerous because he isn't even on line............Installing anything on linux without being on-line is a bug-a-boo

---

### Post by nmcvicar on 2007-07-30
I tried RomeReactor's suggestion in root terminal. It didn't work. I got another error message regarding the perl-modules. What in the world am I doing wrong?

I also tried the command for multimedia at 
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs)
and I got the following: 

nmcvicar@nmcvicar-desktop:~$ sudo apt-get install ubuntu-restricted-extras libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll
Password:
Sorry, try again.
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-plugins-base is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
The following extra packages will be installed:
  cabextract flashplugin-nonfree gstreamer0.10-plugins-ugly
  gstreamer0.10-plugins-ugly-multiverse java-common liba52-0.7.4 libcdaudio1
  libdvdread3 libfreebob0 libgsm1 libid3tag0 libjack0.100.0-0 liblame0
  libltdl3 libmad0 libmms0 libmodplug0c2 libmpcdec3 libmpeg2-4 libpulse0
  libsidplay1 libsoundtouch1c2 libswfdec0.3 libwavpack1 libxine1
  libxine1-ffmpeg libxvmc1 msttcorefonts odbcinst1debian1 sun-java6-bin
  sun-java6-jre sun-java6-plugin unixodbc
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs equivs libdvdcss2 debhelper
  fakeroot pulseaudio sidplay-base xsidplay libxine1-plugins xine-ui gxine
  sun-java6-fonts ttf-sazanami-gothic ttf-sazanami-mincho libmyodbc
  odbc-postgresql libct1
Recommended packages:
  w32codecs jackd gsfonts-x11
The following NEW packages will be installed:
  cabextract flashplugin-nonfree gstreamer0.10-pitfdll
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
  gstreamer0.10-plugins-ugly-multiverse java-common liba52-0.7.4 libcdaudio1
  libdvdread3 libfreebob0 libgsm1 libid3tag0 libjack0.100.0-0 liblame0
  libltdl3 libmad0 libmms0 libmodplug0c2 libmpcdec3 libmpeg2-4 libpulse0
  libsidplay1 libsoundtouch1c2 libswfdec0.3 libwavpack1 libxine-extracodecs
  libxine1 libxine1-ffmpeg libxvmc1 msttcorefonts odbcinst1debian1
  sun-java6-bin sun-java6-jre sun-java6-plugin ubuntu-restricted-extras
  unixodbc
0 upgraded, 37 newly installed, 0 to remove and 112 not upgraded.
Need to get 37.5MB/39.6MB of archives.
After unpacking, 111MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main java-common 0.25ubuntu2 [76.9kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libpulse0 0.9.5-5ubuntu4.1 [100kB]
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libltdl3 1.5.22-4 [168kB]
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main odbcinst1debian1 2.2.11-13 [64.1kB]
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main unixodbc 2.2.11-13 [269kB]
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse sun-java6-bin 6-00-2ubuntu2 [26.2MB]
Get:7 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse sun-java6-jre 6-00-2ubuntu2 [6324kB]
Get:8 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe cabextract 1.2-2 [53.9kB]   
Get:9 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse flashplugin-nonfree 9.0.31.0.2ubuntu1 [15.4kB]
Get:10 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libmodplug0c2 1:0.7-5.2build1 [120kB]
Get:11 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libxvmc1 2:1.0.2-0ubuntu2 [12.1kB]
Get:12 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libxine1 1.1.4-2ubuntu3 [2473kB]
Get:13 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe libxine1-ffmpeg 1.1.4-2ubuntu3 [1571kB]
Get:14 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse libxine-extracodecs 1.1.4-2ubuntu3 [39.4kB]
Get:15 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse msttcorefonts 1.8ubuntu1 [35.0kB]
Get:16 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse sun-java6-plugin 6-00-2ubuntu2 [1392B]
Get:17 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse ubuntu-restricted-extras 2.2 [1920B]
Fetched 37.5MB in 7m51s (79.7kB/s)                                             
Extracting templates from packages: 100%
Preconfiguring packages ...
Selecting previously deselected package java-common.
(Reading database ... dpkg: error processing /var/cache/apt/archives/java-common_0.25ubuntu2_all.deb (--unpack):
 files list file for package `perl-modules' contains empty filename
Errors were encountered while processing:
 /var/cache/apt/archives/java-common_0.25ubuntu2_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
nmcvicar@nmcvicar-desktop:~$

---

### Post by RomeReactor on 2007-07-30
From the [bug report]("https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/108189"):
> The error shown will be either:
files list file for package `*' is missing final newline
Or:
files list file for package `*' contains an empty filename

Where * start is a random but steady "per install" package name.

**Adding a newline char to the file changes the message form the first to the seccond error noting about the empty filename**.

Since all these files seem to contain only a string of @^@^@^@^@^@^@^@^@^@^@^@^
it seems they are redundant, **and i ventured on moving them from the folder, this solved the problem**.

So you can try to move the file to your home folder (so you keep it safe in the meantime) and try to update again. From the terminal:
```
sudo mv /var/lib/dpkg/info/perl-modules.list ~
```
to move the file to your home folder; and
```
sudo apt-get update
```
then try the installation again. If it still complains, you can move the **perl-modules.list** file back:
```
sudo mv ~/perl-modules.list /var/lib/dpkg/info
```
while you wait for someone to post another fix. Also:
> **sailor2001 said:**
> it's not dangerous because he isn't even on line............Installing anything on linux without being on-line is a bug-a-boo
There is an abundance of ways you can break your installation from a root terminal that have nothing to do with being online or installing packages. Just the fact that entering an incorrect command while having administrator privileges can delete entire system folders, or move system libraries around can be disastrous.

---

