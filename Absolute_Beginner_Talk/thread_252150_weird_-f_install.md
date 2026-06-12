---
title: "weird -f install"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by Anonii on 2006-09-06
Greetings, never really had any problems with APT. I actually love it. But well, by reading some threads I've decided to start using aptitude.
After some installs and removes (I have installed/removed emacs like 5 times) when I try "sudo aptitude -f install" I get this:

```
$ sudo aptitude -f install
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are BROKEN:
  checkgmail emacs21 ffmpeg fglrx-kernel-2.6.15-26-386 firestarter gksu
  libcrypt-simple-perl libimlib2 libxml-parser-perl mjpegtools totem-xine
The following packages have been kept back:
  imagemagick libmagick9 libmysqlclient15off libssl0.9.8 mysql-common
  openssl vim
The following packages will be REMOVED:
  alsa-oss cabextract fglrx-control fglrx-kernel-source flashplugin-nonfree
  gnome-keyring gsfonts-other gsfonts-x11 gstreamer0.10-ffmpeg
  gstreamer0.10-fluendo-mp3 gstreamer0.10-fluendo-mpegdemux
  gstreamer0.10-gl gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-base
  gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly
  gstreamer0.10-plugins-ugly-multiverse lame libavc1394-0 libbonoboui2-0
  libbonoboui2-common libcompress-zlib-perl libcrypt-blowfish-perl
  libcrypt-ssleay-perl libdv4 libemail-mime-encodings-perl
  libfreezethaw-perl libggi2 libgii0 libgii0-target-x libglib-perl
  libgnome-desktop-2 libgnome-keyring0 libgnomeui-0 libgnomeui-common
  libgtk2-perl libgtk2-trayicon-perl libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl liblame0 liblog4j1.2-java libltdl3
  libmd5-perl libmjpegtools0c2a libmms0 libnautilus-extension1 liboil0.3
  libpostproc0 libquicktime0 libshout3 libsidplay1 libswfdec0.3
  libtotem-plparser1 libungif4g liburi-perl libwavpack0 libwww-perl
  libxml-libxml-common-perl libxml-libxml-perl libxml-namespacesupport-perl
  libxml-sax-perl libxml-simple-perl linux-headers-2.6.15-26
  linux-headers-2.6.15-26-386 memtester mencoder mencoder-386
  mozilla-mplayer mpg321 mplayer mplayer-386 mplayer-fonts mplayer-skins
  msttcorefonts odbcinst1debian1 procinfo sox sun-java5-bin sun-java5-jre
  sun-java5-plugin sysutils t1-xfree86-nonfree tofrodos ttf-dustin ttf-f500
  ttf-isabella ttf-larabie-deco ttf-larabie-straight ttf-larabie-uncommon
  ttf-staypuft ttf-summersby ttf-ubuntu-title ttf-xfree86-nonfree unixodbc
  xfonts-artwiz xfonts-intl-european xorg-driver-fglrx
0 packages upgraded, 0 newly installed, 99 to remove and 8 not upgraded.
Need to get 0B of archives. After unpacking 288MB will be freed.
The following packages have unmet dependencies:
  firestarter: Depends: libbonoboui2-0 (>= 2.5.4) but it is not installable
               Depends: libgnome-keyring0 (>= 0.4.3) but it is not installable
               Depends: libgnomeui-0 (>= 2.13.0) but it is not installable
  libcrypt-simple-perl: Depends: libcompress-zlib-perl but it is not installable
                        Depends: libcrypt-blowfish-perl but it is not installable
                        Depends: libemail-mime-encodings-perl but it is not installable
                        Depends: libmd5-perl but it is not installable
                        Depends: libfreezethaw-perl but it is not installable
  libxml-parser-perl: Depends: liburi-perl but it is not installable
                      Depends: libwww-perl but it is not installable
  fglrx-kernel-2.6.15-26-386: Depends: xorg-driver-fglrx (= 8.27.10-1) but it is not installable
  checkgmail: Depends: libgtk2-perl but it is not installable
              Depends: libgtk2-trayicon-perl but it is not installable
              Depends: libwww-perl but it is not installable
              Depends: libcrypt-ssleay-perl but it is not installable
              Depends: libxml-simple-perl but it is not installable
              Depends: libcrypt-blowfish-perl but it is not installable
              Depends: libfreezethaw-perl but it is not installable
              Depends: libcompress-zlib-perl but it is not installable
  ffmpeg: Depends: liblame0 (>= 3.96.1-1) but it is not installable
  gksu: Depends: libgnome-keyring0 (>= 0.4.3) but it is not installable
  emacs21: Depends: libungif4g (>= 4.1.3) but it is not installable
  mjpegtools: Depends: libdv4 but it is not installable
              Depends: libmjpegtools0c2a (>= 1:1.8.0-0.0ubuntu1) but it is not installable
              Depends: libquicktime0 but it is not installable
  totem-xine: Depends: libbonoboui2-0 (>= 2.5.4) but it is not installable
              Depends: libgnome-desktop-2 (>= 2.11.1) but it is not installable
              Depends: libgnome-keyring0 (>= 0.4.3) but it is not installable
              Depends: libgnomeui-0 (>= 2.13.0) but it is not installable
              Depends: libnautilus-extension1 (>= 2.13.1) but it is not installable
              Depends: libtotem-plparser1 but it is not installable
              Depends: libtotem-plparser1 but it is not installable
  libimlib2: Depends: libungif4g (>= 4.1.3) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
checkgmail
libparse-debianchangelog-perl
libxml-parser-perl
lintian
totem-xine

Keep the following packages at their current version:
gnome-keyring [0.4.9-1ubuntu1 (dapper, now)]
libavc1394-0 [0.5.1-1 (dapper, now)]
libbonoboui2-0 [2.14.0-0ubuntu1 (dapper, now)]
libbonoboui2-common [2.14.0-0ubuntu1 (dapper, now)]
libcompress-zlib-perl [1.41-1 (dapper, now)]
libcrypt-blowfish-perl [2.09-5 (dapper, now)]
libdv4 [0.104-1ubuntu2 (dapper, now)]
libemail-mime-encodings-perl [1.3-1 (dapper, now)]
libfreezethaw-perl [0.43-2 (dapper, now)]
libgnome-keyring0 [0.4.9-1ubuntu1 (dapper, now)]
libgnomeui-0 [2.14.1-0ubuntu3 (dapper-updates, now)]
libgnomeui-common [2.14.1-0ubuntu3 (dapper-updates, now)]
liblame0 [3.96.1-1 (dapper, now)]
libmd5-perl [2.03-1 (dapper, now)]
libmjpegtools0c2a [1:1.8.0-0.0ubuntu1 (dapper, now)]
libquicktime0 [1:0.9.7-0.4ubuntu1 (dapper, now)]
libungif4g [4.1.4-1 (dapper, now)]
xorg-driver-fglrx [8.27.10-1 (now)]

Leave the following dependencies unresolved:
tetex-bin recommends libxml-parser-perl
Score is -2071

Accept this solution? [Y/n/q/?] Y
The following packages are unused and will be REMOVED:
  diffstat libclass-accessor-perl libhtml-template-perl libio-string-perl
  libtimedate-perl
The following packages will be automatically REMOVED:
  checkgmail libparse-debianchangelog-perl libxml-parser-perl lintian
  totem-xine
The following packages have been kept back:
  imagemagick libmagick9 libmysqlclient15off libssl0.9.8 mjpegtools
  mysql-common openssl vim
The following packages will be REMOVED:
  alsa-oss cabextract checkgmail fglrx-control fglrx-kernel-source
  flashplugin-nonfree gsfonts-other gsfonts-x11 gstreamer0.10-ffmpeg
  gstreamer0.10-fluendo-mp3 gstreamer0.10-fluendo-mpegdemux
  gstreamer0.10-gl gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-base
  gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly
  gstreamer0.10-plugins-ugly-multiverse lame libcrypt-ssleay-perl libggi2
  libgii0 libgii0-target-x libglib-perl libgnome-desktop-2 libgtk2-perl
  libgtk2-trayicon-perl libhtml-parser-perl libhtml-tagset-perl
  libhtml-tree-perl liblog4j1.2-java libltdl3 libmms0
  libnautilus-extension1 liboil0.3 libparse-debianchangelog-perl
  libpostproc0 libshout3 libsidplay1 libswfdec0.3 libtotem-plparser1
  liburi-perl libwavpack0 libwww-perl libxml-libxml-common-perl
  libxml-libxml-perl libxml-namespacesupport-perl libxml-parser-perl
  libxml-sax-perl libxml-simple-perl lintian linux-headers-2.6.15-26
  linux-headers-2.6.15-26-386 memtester mencoder mencoder-386
  mozilla-mplayer mpg321 mplayer mplayer-386 mplayer-fonts mplayer-skins
  msttcorefonts odbcinst1debian1 procinfo sox sun-java5-bin sun-java5-jre
  sun-java5-plugin sysutils t1-xfree86-nonfree tofrodos totem-xine
  ttf-dustin ttf-f500 ttf-isabella ttf-larabie-deco ttf-larabie-straight
  ttf-larabie-uncommon ttf-staypuft ttf-summersby ttf-ubuntu-title
  ttf-xfree86-nonfree unixodbc xfonts-artwiz xfonts-intl-european
0 packages upgraded, 0 newly installed, 91 to remove and 8 not upgraded.
Need to get 0B of archives. After unpacking 255MB will be freed.
Do you want to continue? [Y/n/?]             
```

Isnt it great? :P
What could I do, to fix this? I see some really important things in the remove list and I dont think I want to remove them :]

---

### Post by dannyboy79 on 2006-09-06
YEP, I did the same thing. You should have never said yes when you say "the following packages will be removed"!!!!! Oh well, I posted a question for help about 2 weeks ago and no one responded with anything helpful. they basically told me the obvious, they said, well, print out the list and do a sudo aptitude install .......... for everything that was removed. I wasn't happy with that solution so I tried to restore my /home directory and my /etc directory and that didn't fix it either because I guess most of the actual files are stored in /bin, /usr/bin/, or /usr/local/bin so basically what I restored was all the neccessary config files but none of the actual programs so I ended up with a machine full of crap. If I were you I would do what they told me to do, just do sudo aptitude install ......... for each of the things that were removed. I see that most of the stuff that was removed is exactly the same as what was removed from mine! I think it has to do with Automatix, did you use automatix to install mozilla-mplayer flash, your media code-c's like gstreamer etc etc, I think since we used automatix that there were some broken packages so when you did the -f option it wanted to remove them. Sorry I could be more help gotta go. let me know if you were able to fix it easily in case I do it again!  i better not, anytime I see "remove" and "yes or no" from now I on I know what I am hitting!

---

### Post by Anonii on 2006-09-06
> **dannyboy79 said:**
> YEP, I did the same thing. You should have never said yes when you say "the following packages will be removed"!!!!! Oh well, I posted a question for help about 2 weeks ago and no one responded with anything helpful. they basically told me the obvious, they said, well, print out the list and do a sudo aptitude install .......... for everything that was removed. I wasn't happy with that solution so I tried to restore my /home directory and my /etc directory and that didn't fix it either because I guess most of the actual files are stored in /bin, /usr/bin/, or /usr/local/bin so basically what I restored was all the neccessary config files but none of the actual programs so I ended up with a machine full of crap. If I were you I would do what they told me to do, just do sudo aptitude install ......... for each of the things that were removed. I see that most of the stuff that was removed is exactly the same as what was removed from mine! I think it has to do with Automatix, did you use automatix to install mozilla-mplayer flash, your media code-c's like gstreamer etc etc, I think since we used automatix that there were some broken packages so when you did the -f option it wanted to remove them. Sorry I could be more help gotta go. let me know if you were able to fix it easily in case I do it again!  i better not, anytime I see "remove" and "yes or no" from now I on I know what I am hitting!
Thank you. It sounds extreme, but what the heck.. I'll try it <:


I'll report back, soon enough. (I hope.)

---

### Post by Anonii on 2006-09-06
So... I removed all these and then installed them manually. It worked all right. Rebooted and its ok. But when I try "sudo aptitude -f install". I get this:

```
$ sudo aptitude -f install
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be installed:
  vim
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7323kB of archives. After unpacking 23.2MB will be used.
Do you want to continue? [Y/n/?] n
Abort.
habeeb@habeeb:~$ sudo aptitude -f install
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be installed:
  vim
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7323kB of archives. After unpacking 23.2MB will be used.
Do you want to continue? [Y/n/?] Y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  vim

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": Yes
(Reading database ... 111988 files and directories currently installed.)
Unpacking vim (from .../vim_2%3a0.20060517T160422_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/vim_2%3a0.20060517T160422_i386.deb (--unpack):
 trying to overwrite `/usr/bin/xxd', which is also in package vim-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/vim_2%3a0.20060517T160422_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on vim; however:
  Package vim is not installed.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-base:
 ubuntu-base depends on ubuntu-minimal; however:
  Package ubuntu-minimal is not configured yet.
dpkg: error processing ubuntu-base (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ubuntu-minimal
 ubuntu-base
```

Tried "sudo aptitude install vim"

and I get the same error :/

---

### Post by Anonii on 2006-09-06
Hmm, sorry for the triple-post, but seems like I'm having quite a problem here.

APT seems obsessed to install vim. I cant apt-get install anything, before I execute "apt-get -f install" which gives me this error:


```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  vim
Suggested packages:
  ctags vim-doc vim-scripts
The following NEW packages will be installed:
  vim
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/7323kB of archives.
After unpacking 23.2MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  vim
Install these packages without verification [y/N]? y
(Reading database ... 111988 files and directories currently installed.)
Unpacking vim (from .../vim_2%3a0.20060517T160422_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/vim_2%3a0.20060517T160422_i386.deb (--unpack):
 trying to overwrite `/usr/bin/xxd', which is also in package vim-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/vim_2%3a0.20060517T160422_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Also, when I try to install vim with "sudo apt-get -f install"
I get this:

```
$ sudo apt-get install vim
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  ctags vim-doc vim-scripts
The following NEW packages will be installed:
  vim
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/7323kB of archives.
After unpacking 23.2MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  vim
Install these packages without verification [y/N]? Y
(Reading database ... 111988 files and directories currently installed.)
Unpacking vim (from .../vim_2%3a0.20060517T160422_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/vim_2%3a0.20060517T160422_i386.deb (--unpack):
 trying to overwrite `/usr/bin/xxd', which is also in package vim-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/vim_2%3a0.20060517T160422_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Which is similar with the previous.


I'd like some help fast, because like I said, I can install _nothing_. :/

---

### Post by dannyboy79 on 2006-09-07
I want to first point out that I am a linuz newbie so anything I am telling you are only SUGGESTIONS not a for sure fix. now, from the errors it looks like it is trying to install vim from the .deb that is already on your computer which for 1 might be a problem but i don't knwo for sure. why don't you try and change the name to the file that's in /var/cache/apt/archives/vim_2%......... to something else only momentarily, then after you renamed it then try to do a sudo aptitude install vim and maybe apt will try and get it from the ubuntu repositories. Also, you could try to do sudo aptitude reinstall dpkg because it looks like your program dpkg which installs .deb files is having problems also. Also, you could try to sudo aptitude reinstall vim-common first. Just look at the errors and try things that make common sense. Good luck

---

