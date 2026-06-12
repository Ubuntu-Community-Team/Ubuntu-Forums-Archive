---
title: "Installation question"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by O-pos on 2007-04-07
Hello,

I'm trying to install VLC media player on my computer. I'm trying to do it as describet at [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html), but it somehow doesn't work, or maybe it works but I don't know where to find it. Usually, where can one find installed program? in Applications?

---

### Post by oilchangeguy on 2007-04-07
probably the easiest way would be to use automatix. [www.getautomatix.com](www.getautomatix.com)

---

### Post by Maestro23 on 2007-04-07
> **O-pos said:**
> Hello,

I'm trying to install VLC media player on my computer. I'm trying to do it as describet at [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html), but it somehow doesn't work, or maybe it works but I don't know where to find it. Usually, where can one find installed program? in Applications?

VideoLan is in the Ubuntu repositories.

Synpatic(GUI): Search vlc.  Mark for install.  

Command line:

> sudo aptitude install vlc

*If you dont' see it, you need to add extra repositories:[https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

*Always check the Ubuntu repositories first for a program.  Will make things easy for you.

Good luck.

---

### Post by O-pos on 2007-04-07
thanks. however, here's a code from terminal, what I already tried to install. Can you tell me whether it's installed and where can I find it?

```
 wacho@wacho:~$ sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  liba52-0.7.4 libavcodec0d libavformat0d libdc1394-13 libdvbpsi4 libdvdnav4
  libdvdread3 libgsm1 libid3tag0 libiso9660-4 libmad0 libmodplug0c2 libmpcdec3
  libmpeg2-4 libpostproc0d libsdl-image1.2 libtar libvcdinfo0 libvlc0 libwxbase2.6-0
  libwxgtk2.6-0 libxosd2 vlc-nox
Suggested packages:
  libdvdcss2 xfonts-base-transcoded
Recommended packages:
  videolan-doc
The following NEW packages will be installed:
  liba52-0.7.4 libavcodec0d libavformat0d libdc1394-13 libdvbpsi4 libdvdnav4
  libdvdread3 libgsm1 libid3tag0 libiso9660-4 libmad0 libmodplug0c2 libmpcdec3
  libmpeg2-4 libpostproc0d libsdl-image1.2 libtar libvcdinfo0 libvlc0 libwxbase2.6-0
  libwxgtk2.6-0 libxosd2 mozilla-plugin-vlc vlc vlc-nox vlc-plugin-esd
0 upgraded, 26 newly installed, 0 to remove and 160 not upgraded.
Need to get 12.2MB/12.2MB of archives.
After unpacking 33.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://security.ubuntu.com edgy-security/universe libvlc0 0.8.6-svn20061012.debian-1ubuntu1.1 [955kB]
Get:2 http://at.archive.ubuntu.com edgy/universe libavcodec0d 3:0.cvs20060823-3.1ubuntu1 [1506kB]
Get:3 http://security.ubuntu.com edgy-security/universe vlc-nox 0.8.6-svn20061012.debian-1ubuntu1.1 [4136kB]
Get:4 http://at.archive.ubuntu.com edgy/main libdc1394-13 1.1.0-3ubuntu1 [31.6kB]     
Get:5 http://at.archive.ubuntu.com edgy/universe libavformat0d 3:0.cvs20060823-3.1ubuntu1 [284kB]
Get:6 http://at.archive.ubuntu.com edgy/universe libdvbpsi4 0.1.5-2 [31.1kB]          
Get:7 http://at.archive.ubuntu.com edgy/universe libdvdnav4 0.1.9-3 [77.7kB]          
Get:8 http://at.archive.ubuntu.com edgy/universe libdvdread3 0.9.6-3ubuntu1 [55.0kB]  
Get:9 http://at.archive.ubuntu.com edgy/main libid3tag0 0.15.1b-8 [34.9kB]            
Get:10 http://at.archive.ubuntu.com edgy/universe libiso9660-4 0.76-1ubuntu1 [94.6kB] 
Get:11 http://at.archive.ubuntu.com edgy/main libmad0 0.15.1b-2.1 [76.9kB]            
Get:12 http://at.archive.ubuntu.com edgy/main libmodplug0c2 1:0.7-5 [115kB]           
Get:13 http://at.archive.ubuntu.com edgy/main libmpcdec3 1.2.2-1 [25.3kB]             
Get:14 http://at.archive.ubuntu.com edgy/universe libmpeg2-4 0.4.0b-4ubuntu1 [61.9kB] 
Get:15 http://at.archive.ubuntu.com edgy/universe libpostproc0d 3:0.cvs20060823-3.1ubuntu1 [35.3kB]
Get:16 http://at.archive.ubuntu.com edgy/main libsdl-image1.2 1.2.5-2 [29.2kB]        
Get:17 http://at.archive.ubuntu.com edgy/universe libtar 1.2.11-4 [19.0kB]            
Get:18 http://at.archive.ubuntu.com edgy/universe libvcdinfo0 0.7.23-3 [124kB]        
Get:19 http://at.archive.ubuntu.com edgy-updates/universe libwxbase2.6-0 2.6.3.2.1.5ubuntu0.1 [530kB]
Get:20 http://at.archive.ubuntu.com edgy-updates/universe libwxgtk2.6-0 2.6.3.2.1.5ubuntu0.1 [2726kB]
Err http://security.ubuntu.com edgy-security/universe vlc-nox 0.8.6-svn20061012.debian-1ubuntu1.1
  Connection timed out
Get:21 http://security.ubuntu.com edgy-security/universe vlc 0.8.6-svn20061012.debian-1ubuntu1.1 [1147kB]
Err http://at.archive.ubuntu.com edgy-updates/universe libwxgtk2.6-0 2.6.3.2.1.5ubuntu0.1
  Connection timed out
Get:22 http://at.archive.ubuntu.com edgy/universe libxosd2 2.2.14-1.3 [24.5kB]        
Err http://security.ubuntu.com edgy-security/universe vlc 0.8.6-svn20061012.debian-1ubuntu1.1
  Connection timed out
Get:23 http://security.ubuntu.com edgy-security/universe mozilla-plugin-vlc 0.8.6-svn20061012.debian-1ubuntu1.1 [27.2kB]
Get:24 http://security.ubuntu.com edgy-security/universe vlc-plugin-esd 0.8.6-svn20061012.debian-1ubuntu1.1 [4872B]
Fetched 4144kB in 8m9s (8471B/s)      
Failed to fetch http://at.archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.6/libwxgtk2.6-0_2.6.3.2.1.5ubuntu0.1_i386.deb  Connection timed out
Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-nox_0.8.6-svn20061012.debian-1ubuntu1.1_i386.deb  Connection timed out
Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc_0.8.6-svn20061012.debian-1ubuntu1.1_i386.deb  Connection timed out
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
wacho@wacho:~$ Hello,
bash: Hello,: command not found
wacho@wacho:~$ 
wacho@wacho:~$ I'm trying to install VLC media player on my computer. I'm trying to do it as describet at http://www.videolan.org/vlc/download-ubuntu.html, but it somehow doesn't work, or maybe it works but I don't know where to find it. Usually, where can one find installed program? in Applications?
bash: Im trying to install VLC media player on my computer. Im: command not found
wacho@wacho:~$ sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  liba52-0.7.4 libavcodec0d libavformat0d libdc1394-13 libdvbpsi4 libdvdnav4
  libdvdread3 libgsm1 libid3tag0 libiso9660-4 libmad0 libmodplug0c2 libmpcdec3
  libmpeg2-4 libpostproc0d libsdl-image1.2 libtar libvcdinfo0 libvlc0 libwxbase2.6-0
  libwxgtk2.6-0 libxosd2 vlc-nox
Suggested packages:
  libdvdcss2 xfonts-base-transcoded
Recommended packages:
  videolan-doc
The following NEW packages will be installed:
  liba52-0.7.4 libavcodec0d libavformat0d libdc1394-13 libdvbpsi4 libdvdnav4
  libdvdread3 libgsm1 libid3tag0 libiso9660-4 libmad0 libmodplug0c2 libmpcdec3
  libmpeg2-4 libpostproc0d libsdl-image1.2 libtar libvcdinfo0 libvlc0 libwxbase2.6-0
  libwxgtk2.6-0 libxosd2 mozilla-plugin-vlc vlc vlc-nox vlc-plugin-esd
0 upgraded, 26 newly installed, 0 to remove and 160 not upgraded.
Need to get 8009kB/12.2MB of archives.
After unpacking 33.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://at.archive.ubuntu.com edgy-updates/universe libwxgtk2.6-0 2.6.3.2.1.5ubuntu0.1 [2726kB]
Get:2 http://security.ubuntu.com edgy-security/universe vlc-nox 0.8.6-svn20061012.debian-1ubuntu1.1 [4136kB]
Get:3 http://security.ubuntu.com edgy-security/universe vlc 0.8.6-svn20061012.debian-1ubuntu1.1 [1147kB]
Fetched 6176kB in 2m56s (34.9kB/s)                                                    
Selecting previously deselected package liba52-0.7.4.
(Reading database ... 95222 files and directories currently installed.)
Unpacking liba52-0.7.4 (from .../liba52-0.7.4_0.7.4-3_i386.deb) ...
Selecting previously deselected package libgsm1.
Unpacking libgsm1 (from .../libgsm1_1.0.10-13_i386.deb) ...
Selecting previously deselected package libavcodec0d.
Unpacking libavcodec0d (from .../libavcodec0d_3%3a0.cvs20060823-3.1ubuntu1_i386.deb) ...
Selecting previously deselected package libdc1394-13.
Unpacking libdc1394-13 (from .../libdc1394-13_1.1.0-3ubuntu1_i386.deb) ...
Selecting previously deselected package libavformat0d.
Unpacking libavformat0d (from .../libavformat0d_3%3a0.cvs20060823-3.1ubuntu1_i386.deb) ...
Selecting previously deselected package libdvbpsi4.
Unpacking libdvbpsi4 (from .../libdvbpsi4_0.1.5-2_i386.deb) ...
Selecting previously deselected package libdvdnav4.
Unpacking libdvdnav4 (from .../libdvdnav4_0.1.9-3_i386.deb) ...
Selecting previously deselected package libdvdread3.
Unpacking libdvdread3 (from .../libdvdread3_0.9.6-3ubuntu1_i386.deb) ...
Selecting previously deselected package libid3tag0.
Unpacking libid3tag0 (from .../libid3tag0_0.15.1b-8_i386.deb) ...
Selecting previously deselected package libiso9660-4.
Unpacking libiso9660-4 (from .../libiso9660-4_0.76-1ubuntu1_i386.deb) ...
Selecting previously deselected package libmad0.
Unpacking libmad0 (from .../libmad0_0.15.1b-2.1_i386.deb) ...
Selecting previously deselected package libmodplug0c2.
Unpacking libmodplug0c2 (from .../libmodplug0c2_1%3a0.7-5_i386.deb) ...
Selecting previously deselected package libmpcdec3.
Unpacking libmpcdec3 (from .../libmpcdec3_1.2.2-1_i386.deb) ...
Selecting previously deselected package libmpeg2-4.
Unpacking libmpeg2-4 (from .../libmpeg2-4_0.4.0b-4ubuntu1_i386.deb) ...
Selecting previously deselected package libpostproc0d.
Unpacking libpostproc0d (from .../libpostproc0d_3%3a0.cvs20060823-3.1ubuntu1_i386.deb) ...
Selecting previously deselected package libsdl-image1.2.
Unpacking libsdl-image1.2 (from .../libsdl-image1.2_1.2.5-2_i386.deb) ...
Selecting previously deselected package libtar.
Unpacking libtar (from .../libtar_1.2.11-4_i386.deb) ...
Selecting previously deselected package libvcdinfo0.
Unpacking libvcdinfo0 (from .../libvcdinfo0_0.7.23-3_i386.deb) ...
Selecting previously deselected package libvlc0.
Unpacking libvlc0 (from .../libvlc0_0.8.6-svn20061012.debian-1ubuntu1.1_i386.deb) ...
Selecting previously deselected package libwxbase2.6-0.
Unpacking libwxbase2.6-0 (from .../libwxbase2.6-0_2.6.3.2.1.5ubuntu0.1_i386.deb) ...
Selecting previously deselected package libwxgtk2.6-0.
Unpacking libwxgtk2.6-0 (from .../libwxgtk2.6-0_2.6.3.2.1.5ubuntu0.1_i386.deb) ...
Selecting previously deselected package libxosd2.
Unpacking libxosd2 (from .../libxosd2_2.2.14-1.3_i386.deb) ...
Selecting previously deselected package vlc-nox.
Unpacking vlc-nox (from .../vlc-nox_0.8.6-svn20061012.debian-1ubuntu1.1_i386.deb) ...
Selecting previously deselected package vlc.
Unpacking vlc (from .../vlc_0.8.6-svn20061012.debian-1ubuntu1.1_i386.deb) ...
Selecting previously deselected package mozilla-plugin-vlc.
Unpacking mozilla-plugin-vlc (from .../mozilla-plugin-vlc_0.8.6-svn20061012.debian-1ubuntu1.1_i386.deb) ...
Selecting previously deselected package vlc-plugin-esd.
Unpacking vlc-plugin-esd (from .../vlc-plugin-esd_0.8.6-svn20061012.debian-1ubuntu1.1_i386.deb) ...
Setting up liba52-0.7.4 (0.7.4-3) ...

Setting up libgsm1 (1.0.10-13) ...

Setting up libavcodec0d (0.cvs20060823-3.1ubuntu1) ...

Setting up libdc1394-13 (1.1.0-3ubuntu1) ...

Setting up libavformat0d (0.cvs20060823-3.1ubuntu1) ...

Setting up libdvbpsi4 (0.1.5-2) ...

Setting up libdvdnav4 (0.1.9-3) ...

Setting up libdvdread3 (0.9.6-3ubuntu1) ...

Setting up libid3tag0 (0.15.1b-8) ...

Setting up libiso9660-4 (0.76-1ubuntu1) ...

Setting up libmad0 (0.15.1b-2.1) ...

Setting up libmodplug0c2 (0.7-5) ...

Setting up libmpcdec3 (1.2.2-1) ...

Setting up libmpeg2-4 (0.4.0b-4ubuntu1) ...

Setting up libpostproc0d (0.cvs20060823-3.1ubuntu1) ...

Setting up libsdl-image1.2 (1.2.5-2) ...

Setting up libtar (1.2.11-4) ...

Setting up libvcdinfo0 (0.7.23-3) ...

Setting up libvlc0 (0.8.6-svn20061012.debian-1ubuntu1.1) ...

Setting up libwxbase2.6-0 (2.6.3.2.1.5ubuntu0.1) ...

Setting up libwxgtk2.6-0 (2.6.3.2.1.5ubuntu0.1) ...

Setting up libxosd2 (2.2.14-1.3) ...

Setting up vlc-nox (0.8.6-svn20061012.debian-1ubuntu1.1) ...
Setting up vlc (0.8.6-svn20061012.debian-1ubuntu1.1) ...

Setting up mozilla-plugin-vlc (0.8.6-svn20061012.debian-1ubuntu1.1) ...
Setting up vlc-plugin-esd (0.8.6-svn20061012.debian-1ubuntu1.1) ...
wacho@wacho:~$ 

 
```

---

### Post by Maestro23 on 2007-04-07
In termina type:

> vlc

Should also be a menu entry for it now as well.

---

### Post by O-pos on 2007-04-07
Yes, it's cool :) it works!

but is it an easier way to avoid every time to open terminal and enter vlc?

---

### Post by oilchangeguy on 2007-04-07
go to applications, accessories, alacatre menu editor. and add it from there.

---

### Post by Maestro23 on 2007-04-07
> **O-pos said:**
> Yes, it's cool :) it works!

but is it an easier way to avoid every time to open terminal and enter vlc?

Like I said above, check your menus. Should be an entry for it.

Also, some links for ya:

Useful Links:

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

Restricted Formats(mp3, playing DVD, etc..): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Managing Repositories: [https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

CommandLine Beginners: [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

Basic Commands: [https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

LinuxCommand.org(Commands & Linux File Structure): [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Graphic Card Drivers
ATI supported cards: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)
Installing ATI Drivers: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
Installing Nvidia Drivers:[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
Envy Script(ATI/Nvidia): [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Super Grub Disk: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)


Welcome and Good luck.

---

