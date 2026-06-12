---
title: "[SOLVED] tar.gz files - completely confused"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by MikeSz on 2007-03-03
Sorry if this question has been asked a thousand times before but I just cant get my head round it and having read through some similar problems - its still no clearer.

I have downloaded several of these tar.gz files, the most recent being sauerbraten_2006_12_04_gui_edition_linux.tar.gz.  this is a game I found in one of the linux game sites.  Now please bear in mind that ive only been using Ubuntu for the last week or so and none of my books seem to address this (plusI havent a clue where the terminal is concerned)

When I double click on it, it opens up a window wanting me to extract and I can browse the files etc but I cant seem to "install" it or do anything meaningful with it!!!  How do you work these things???

Secondly, ive been into synaptic and noticed "beneath a steel sky" which was one of my favourite amiga games and a "SCUMM" game engine.  so I ckecked the boxes and 'installed' them.  It did a lot of downloading, said it had installed them and now I have absolutely no idea where they are or how to use them.  Sorry if that sonds a little vague but thats about as much as I know.  How do you use these things?  Shouldnt it just plonk a little icon or menu item somewhere that I can just use?

Sorry if thats a little bit long winded but its simple things like this that are really frustrating me! ](*,)

---

### Post by mitype2 on 2007-03-03
Hey Mike,

I'm having the same problem as you are. It's almost driven me to tears. I'm almost ready to say to heck with it and go back to Windows.

---

### Post by MikeSz on 2007-03-03
Hi mitype2 - glad someone else out there is having the same issues as me!!  (dont take that the wrong way, just thought I was starting to crack up thats all) 

ive added you to MSN if thats ok - maybe we can compare some notes?  Im loving Ubuntu but its little things like this that are probably really easy once you know how to do it, its just finding out - especially when a lot of the websites assume you have a level of knowledge to start with!

---

### Post by taurus on 2007-03-03
If you know the name of the program, try running it from a terminal.  For instance, if you want to run firefox from a terminal, type

Applications -> Accessories -> Terminal
```
firefox
```
If you want to know how to build something from source, then look at Step 4 of this guide.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
-or
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by mitype2 on 2007-03-03
Hey Mike I don't mind at all if you add me to your list. Maybe if we team up we can figure this stuff out.

---

### Post by igknighted on 2007-03-03
A tar.gz or a tar.bz2 file is nothing more than a compressed archive (think .zip or .ace or .rar in windows).  Linux comes with the tools to extract these archives, just right click the file and then "extract here" or "extract to...".  Inside might be a .bin or .run file (or even .deb) if you are lucky, but usually there are source files inside and you need to compile them.  It is strongly recommended that you search for these files in some sort of binary first, as source compiles can be difficult/frustrating at times.  The first place to look is synaptic.  Before searching, go to the software sources tab and enable every source there, except the CD.  Then search for the program.  Finally, post here and see if anyone has a .deb.  If this fails, these three commands are the basic process of a source install (enter them in a terminal, you must navigate to the directory of the source first):
```
auto-apt run ./configure
make
checkinstall
```

This will create a .deb package.  To install it:
```
sudo dpkg -i *packagename*.deb
```

You need certain programs installed to compile from source.  Run this command first to make sure they are installed:

```
sudo aptitude install build-essential checkinstall autoapt
```

As for the question about programs installed from synaptic, look in your menu's.  They should automatically update.  Since these are games, they should show up in games.  If they do not, open a terminal and try typing the name in all lower case letters and seeing if it launches.  Failing that, go back to synaptic and look at the details for the package you installed.  It should tell you there what the command is.  You can then make a shortcut on the desktop or panel, or right click the applications menu and edit menus, then add it manually once you know the command.

EDIT: One final thought, browsing websites for programs to install is generally a bad windows habit.  Installing through synaptic is safe, while anyone can post malware to websites and trick you into installing it.

---

### Post by Tomosaur on 2007-03-03
Beneath a steel sky added itself to the the Applications > Games menu for me. Also one of my favourite games :P

Tar.gz files are like .zip files - they're just archives. Extract them to wherver you want, and, depending on the program, you can either run it from that directory, or compile and install it. I think that particular game needs compiling. To do this, you need the build-essential package installed. Go to Applications > Accessories > Terminal, then type:

```

sudo aptitude install build-essential

``` (You can also do this through Synaptic Package Manager, CLI is just faster to explain it :P). Enter your password, and once it's finished downloading, change to the sauerbauten folder:
```

cd ~/directory_name

```

And then compile it :). The compilation process may vary slightly with different applications - there's normally a readme file included which you can read - but the usual process is as follows:

```

./configure
make

```

This will compile the game. You can now run it by simply typing the name of the executable file created.

If you want to install it system wide, do this command afterwards:
```

sudo make install

```

---

### Post by MikeSz on 2007-03-03
Thanks chaps - I think I sort of understand that now - unfortunately I cant seem to get this game file to do anything - Its not listed in synaptic so I guess im just going to have to do the command line thing - from what I can tell, my prompt is pointing to my desktop already and the game file is also sitting in my desktop - ive tried typing the things sugged into the prompt and i will paste all the results here...

mike@mike-desktop:~$ sudo aptitude install build-essential
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
Reading package lists... Done
Building dependency tree... Done
Initialising package states... Done
Building tag database... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
mike@mike-desktop:~$ cd /home/mike/desktop
bash: cd: /home/mike/desktop: No such file or directory
mike@mike-desktop:~$ cd ~/home/mike/desktop
bash: cd: /home/mike/home/mike/desktop: No such file or directory
mike@mike-desktop:~$ ./configure
bash: ./configure: No such file or directory
mike@mike-desktop:~$  ./configure sauerbraten_2006_12_04_gui_edition_linux.tar.g z
bash: ./configure: No such file or directory
mike@mike-desktop:~$ ./configure
bash: ./configure: No such file or directory
mike@mike-desktop:~$ make
bash: make: command not found
mike@mike-desktop:~$

Anyone know what im doing wrong?

---

### Post by taurus on 2007-03-03
Do you happen to have adept or synaptic running before you run that command?  There is something running so the system won't let you run aptitude.  Post the output of this command here.

```
ps -A
```

---

### Post by picpak on 2007-03-03
First, you need to extract the .tar.gz file using the Archive Manager.

Secondly, the terminal is case-sensitive: it's cd /home/mike/**D**esktop.

Then, you would cd to the folder of the extracted file. (If you don't want to type out the whole name, type in the first few letters and hit Tab.)

Once you're there, then run:

```
sudo apt-get install build-essential checkinstall
auto-apt run ./configure
make
sudo checkinstall
```

Are you running Synaptic or the Update Manager? If so, exit those first.

---

### Post by MikeSz on 2007-03-03
Hi Taurus and Pikpack - firstly, the response to the ps -A command was as follows:

mike@mike-desktop:~$ sudo aptitude install build-essential
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
Reading package lists... Done
Building dependency tree... Done
Initialising package states... Done
Building tag database... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
mike@mike-desktop:~$ cd /home/mike/desktop
bash: cd: /home/mike/desktop: No such file or directory
mike@mike-desktop:~$ cd ~/home/mike/desktop
bash: cd: /home/mike/home/mike/desktop: No such file or directory
mike@mike-desktop:~$ ./configure
bash: ./configure: No such file or directory
mike@mike-desktop:~$  ./configure sauerbraten_2006_12_04_gui_edition_linux.tar.g z
bash: ./configure: No such file or directory
mike@mike-desktop:~$ ./configure
bash: ./configure: No such file or directory
mike@mike-desktop:~$ make
bash: make: command not found
mike@mike-desktop:~$

Il try the other things now.....

---

### Post by MikeSz on 2007-03-03
oops, sorry, posted from wrong window - proper results are 

mike@mike-desktop:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:00 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
    8 ?        00:00:00 kblockd/0
    9 ?        00:00:00 kacpid
  161 ?        00:00:00 pdflush
  162 ?        00:00:00 pdflush
  164 ?        00:00:00 aio/0
  163 ?        00:00:00 kswapd0
  759 ?        00:00:00 kseriod
 1777 ?        00:00:00 ata/0
 1778 ?        00:00:00 ata_hotplug/0
 1781 ?        00:00:00 scsi_eh_0
 1782 ?        00:00:00 scsi_eh_1
 1785 ?        00:00:00 scsi_eh_2
 1786 ?        00:00:00 scsi_eh_3
 1942 ?        00:00:00 khubd
 2053 ?        00:00:00 kjournald
 2285 ?        00:00:00 udevd
 3149 ?        00:00:00 shpchpd_event
 3709 ?        00:00:00 dhclient3
 4054 ?        00:00:00 acpid
 4141 ?        00:00:00 syslogd
 4167 ?        00:00:00 dd
 4169 ?        00:00:00 klogd
 4188 ?        00:00:00 dbus-daemon
 4204 ?        00:00:00 hald
 4205 ?        00:00:00 hald-runner
 4210 ?        00:00:00 hald-addon-acpi
 4218 ?        00:00:00 hald-addon-keyb
 4221 ?        00:00:00 hald-addon-keyb
 4270 ?        00:00:00 hald-addon-keyb
 4277 ?        00:00:00 hald-addon-stor
 4278 ?        00:00:00 hald-addon-stor
 4280 ?        00:00:00 hald-addon-stor
 4281 ?        00:00:01 hald-addon-stor
 4610 ?        00:00:00 gdm
 4639 ?        00:00:00 gdm
 4644 tty7     00:11:16 Xorg
 4653 ?        00:00:00 hpiod
 4657 ?        00:00:00 python
 4704 ?        00:00:01 cupsd
 4746 ?        00:00:00 powernowd
 4785 ?        00:00:00 hcid
 4789 ?        00:00:00 sdpd
 4804 ?        00:00:00 krfcommd
 4817 ?        00:00:00 mdadm
 4851 ?        00:00:00 atd
 4864 ?        00:00:00 cron
 4936 tty1     00:00:00 getty
 4937 tty2     00:00:00 getty
 4938 tty3     00:00:00 getty
 4939 tty4     00:00:00 getty
 4940 tty5     00:00:00 getty
 4941 tty6     00:00:00 getty
 4962 ?        00:00:00 x-session-manag
 5004 ?        00:00:00 ssh-agent
 5007 ?        00:00:00 dbus-launch
 5008 ?        00:00:00 dbus-daemon
 5010 ?        00:00:01 gconfd-2
 5013 ?        00:00:00 gnome-keyring-d
 5015 ?        00:00:00 bonobo-activati
 5017 ?        00:00:03 gnome-settings-
 5019 ?        00:00:00 esd
 5026 ?        00:00:30 metacity
 5032 ?        00:00:17 gnome-panel
 5034 ?        00:00:25 nautilus
 5039 ?        00:00:00 gnome-volume-ma
 5050 ?        00:00:01 update-notifier
 5053 ?        00:00:00 gnome-vfs-daemo
 5059 ?        00:00:08 gnome-cups-icon
 5079 ?        00:00:01 gnome-power-man
 5081 ?        00:00:00 mapping-daemon
 5086 ?        00:00:00 trashapplet
 5090 ?        00:00:00 clock-applet
 5093 ?        00:00:01 mixer_applet2
 5109 ?        00:00:06 gnome-screensav
 7595 ?        00:06:28 firefox-bin
10839 ?        00:00:08 gaim
13046 ?        00:00:00 gnome-terminal
13047 ?        00:00:00 gnome-pty-helpe
13048 pts/0    00:00:00 bash
13074 pts/0    00:00:00 ps
mike@mike-desktop:~$

---

### Post by taurus on 2007-03-03
What is the output when you run this command from a terminal?

```
sudo aptitude update
```

---

### Post by picpak on 2007-03-03
Hello,

if you're still interested in compiling, that's great. However, I have found you something to make your life a LOT easier:

[sauerbraten-data_0.0.20061204-1_all.deb](http://http.us.debian.org/debian/pool/non-free/s/sauerbraten-data/sauerbraten-data_0.0.20061204-1_all.deb)
[sauerbraten_0.0.20061204.dfsg-1_i386.deb](http://http.us.debian.org/debian/pool/contrib/s/sauerbraten/sauerbraten_0.0.20061204.dfsg-1_i386.deb)

They're .deb files, the package management system Ubuntu uses. They're made for Debian, but they should work in Ubuntu. After downloading these two files, just run

```
cd /home/mike/Desktop
sudo dpkg -i *.deb
```

and it should all work out.

---

### Post by MikeSz on 2007-03-03
fantastic - thanks for that!!!  Il probably give the compliling a miss if this works!!:lolflag: 

the second file downloaded in like two seconds flat, is that normal?  I accidently opened it and it gave me an error box but im assiming that because the first one, whichi is 130mb hasnt downloaded yet?  

On the subject of the command line Taurus, il run that now...

---

### Post by MikeSz on 2007-03-03
taurus - here is what I got...

mike@mike-desktop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Initialising package states... Done
Building tag database... Done
Get:1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg [191B]
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Fetched 5B in 4s (1B/s)
Reading package lists... Done
mike@mike-desktop:~$

---

### Post by picpak on 2007-03-03
> **MikeSz said:**
> fantastic - thanks for that!!!  Il probably give the compliling a miss if this works!!:lolflag: 

the second file downloaded in like two seconds flat, is that normal?  I accidently opened it and it gave me an error box but im assiming that because the first one, whichi is 130mb hasnt downloaded yet?  

On the subject of the command line Taurus, il run that now...

That's very normal. Most deb packages are small.

Glad you like it. You really don't need to compile anything if you search enough :)

---

### Post by taurus on 2007-03-03
Now

```
sudo aptitude install build-essential checkinstall
```

---

### Post by MikeSz on 2007-03-03
Ok, heres what I got - I downloaded the files, did nothing to them and copied and pasted the commands you gave me - here it all is....

mike@mike-desktop:~$ cd /home/mike/Desktop
mike@mike-desktop:~/Desktop$ sudo dpkg -i *.deb
Selecting previously deselected package sauerbraten.
(Reading database ... 80125 files and directories currently installed.)
Unpacking sauerbraten (from sauerbraten_0.0.20061204.dfsg-1_i386.deb) ...
Selecting previously deselected package sauerbraten-data.
Unpacking sauerbraten-data (from sauerbraten-data_0.0.20061204-1_all.deb) ...
Preparing to replace scummvm 0.8.0-1ubuntu1 (using scummvm_0.9.1-0.sarge.1_i386.deb) ...
Unpacking replacement scummvm ...
dpkg: dependency problems prevent configuration of sauerbraten:
 sauerbraten depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.4.
 sauerbraten depends on libgcc1 (>= 1:4.1.1-12); however:
  Version of libgcc1 on system is 1:4.0.3-1ubuntu5.
 sauerbraten depends on libsdl-image1.2 (>= 1.2.5); however:
  Package libsdl-image1.2 is not installed.
 sauerbraten depends on libsdl-mixer1.2 (>= 1.2.6); however:
  Package libsdl-mixer1.2 is not installed.
 sauerbraten depends on libsdl1.2debian (>= 1.2.10-1); however:
  Version of libsdl1.2debian on system is 1.2.9-0.0ubuntu2.
 sauerbraten depends on libstdc++6 (>= 4.1.1-12); however:
  Version of libstdc++6 on system is 4.0.3-1ubuntu5.
dpkg: error processing sauerbraten (--install):
 dependency problems - leaving unconfigured
Setting up sauerbraten-data (0.0.20061204-1) ...
dpkg: dependency problems prevent configuration of scummvm:
 scummvm depends on libflac6; however:
  Package libflac6 is not installed.
dpkg: error processing scummvm (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sauerbraten
 scummvm

I get the feeling it didnt work?

---

### Post by picpak on 2007-03-03
Oh no!! :( 

You've got what they call "dependency hell"...it's trying to get so many programs, and the latest version of all those programs, but Ubuntu doesn't have them yet. This was what I feared would happen.

I guess now, compiling is your last choice...but before that, make sure you remove the programs (since they don't work):

```
sudo apt-get remove sauerbraten sauerbraten-data
```

---

### Post by MikeSz on 2007-03-03
Thanks guys for your help, looks like we hit a problem though - got a message telling me my software packages were broken (or words to that effect) after I ran the lines for that game.  This is what happened next....

mike@mike-desktop:~$ cd /home/mike/Desktop
mike@mike-desktop:~/Desktop$ sudo dpkg -i *.deb
Selecting previously deselected package sauerbraten.
(Reading database ... 80125 files and directories currently installed.)
Unpacking sauerbraten (from sauerbraten_0.0.20061204.dfsg-1_i386.deb) ...
Selecting previously deselected package sauerbraten-data.
Unpacking sauerbraten-data (from sauerbraten-data_0.0.20061204-1_all.deb) ...
Preparing to replace scummvm 0.8.0-1ubuntu1 (using scummvm_0.9.1-0.sarge.1_i386. deb) ...
Unpacking replacement scummvm ...
dpkg: dependency problems prevent configuration of sauerbraten:
 sauerbraten depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.4.
 sauerbraten depends on libgcc1 (>= 1:4.1.1-12); however:
  Version of libgcc1 on system is 1:4.0.3-1ubuntu5.
 sauerbraten depends on libsdl-image1.2 (>= 1.2.5); however:
  Package libsdl-image1.2 is not installed.
 sauerbraten depends on libsdl-mixer1.2 (>= 1.2.6); however:
  Package libsdl-mixer1.2 is not installed.
 sauerbraten depends on libsdl1.2debian (>= 1.2.10-1); however:
  Version of libsdl1.2debian on system is 1.2.9-0.0ubuntu2.
 sauerbraten depends on libstdc++6 (>= 4.1.1-12); however:
  Version of libstdc++6 on system is 4.0.3-1ubuntu5.
dpkg: error processing sauerbraten (--install):
 dependency problems - leaving unconfigured
Setting up sauerbraten-data (0.0.20061204-1) ...
dpkg: dependency problems prevent configuration of scummvm:
 scummvm depends on libflac6; however:
  Package libflac6 is not installed.
dpkg: error processing scummvm (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sauerbraten
 scummvm
mike@mike-desktop:~/Desktop$ sudo apt-get install -f
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
mike@mike-desktop:~/Desktop$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies...Done
The following extra packages will be installed:
  libsdl-mixer1.2 libsmpeg0
The following packages will be REMOVED
  beneath-a-steel-sky sauerbraten scummvm
The following NEW packages will be installed
  libsdl-mixer1.2 libsmpeg0
0 upgraded, 2 newly installed, 3 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 232kB of archives.
After unpacking 77.6MB disk space will be freed.
Do you want to continue [Y/n]? y
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libsmpeg0 0.4.5+cvs20030824-1.7 [99 .8kB]
Get: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libsdl-mixer1.2 1.2.6-1.1 [132kB]
Fetched 232kB in 2s (108kB/s)
(Reading database ... 82930 files and directories currently installed.)
Removing sauerbraten ...
Removing beneath-a-steel-sky ...
Removing scummvm ...
Selecting previously deselected package libsmpeg0.
(Reading database ... 82893 files and directories currently installed.)
Unpacking libsmpeg0 (from .../libsmpeg0_0.4.5+cvs20030824-1.7_i386.deb) ...
Selecting previously deselected package libsdl-mixer1.2.
Unpacking libsdl-mixer1.2 (from .../libsdl-mixer1.2_1.2.6-1.1_i386.deb) ...
Setting up libsmpeg0 (0.4.5+cvs20030824-1.7) ...

Setting up libsdl-mixer1.2 (1.2.6-1.1) ...

mike@mike-desktop:~/Desktop$ sudo aptitude install build-essential checkinstall
Reading package lists... Done
Building dependency tree... Done
Initialising package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  binutils cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0 installwatch
  libc6-dev libmudflap0 libmudflap0-dev libstdc++6-4.0-dev
  linux-kernel-headers make
The following NEW packages will be installed:
  binutils build-essential checkinstall cpp cpp-4.0 dpkg-dev g++ g++-4.0
  gcc gcc-4.0 installwatch libc6-dev libmudflap0 libmudflap0-dev
  libstdc++6-4.0-dev linux-kernel-headers make
0 packages upgraded, 17 newly installed, 0 to remove and 0 not upgraded.
Need to get 12.3MB of archives. After unpacking 48.1MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main binutils 2.16.1cvs20060117 -1ubuntu2.1 [1407kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main linux-kernel-headers 2.6.11.2-0ubunt u18 [1039kB]
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main libc6-dev 2.3.6-0ubuntu20 .4 [2822kB]
Get:4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main dpkg-dev 1.13.11ubuntu7 [163kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main cpp-4.0 4.0.3-1ubuntu5 [1987kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main cpp 4:4.0.3-1 [31.0kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main gcc-4.0 4.0.3-1ubuntu5 [513kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main gcc 4:4.0.3-1 [5048B]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libstdc++6-4.0-dev 4.0.3-1ubuntu5 [1471kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main g++-4.0 4.0.3-1ubuntu5 [2271kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main g++ 4:4.0.3-1 [1386B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main make 3.80+3.81.b4-1 [286kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main build-essential 11.1 [6826B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe installwatch 0.6.3-2ubuntu1 [11.0kB]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe checkinstall 1.5.3-3ubuntu2 [35.1kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libmudflap0 4.0.3-1ubuntu5 [156kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libmudflap0-dev 4.0.3-1ubuntu5 [95.2kB]
Fetched 12.3MB in 1m8s (179kB/s)
Selecting previously deselected package binutils.
(Reading database ... 82907 files and directories currently installed.)
Unpacking binutils (from .../binutils_2.16.1cvs20060117-1ubuntu2.1_i386.deb) ...
Selecting previously deselected package linux-kernel-headers.
Unpacking linux-kernel-headers (from .../linux-kernel-headers_2.6.11.2-0ubuntu18_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.3.6-0ubuntu20.4_i386.deb) ...
Selecting previously deselected package cpp-4.0.
Unpacking cpp-4.0 (from .../cpp-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package cpp.
Unpacking cpp (from .../cpp_4%3a4.0.3-1_i386.deb) ...
Selecting previously deselected package gcc-4.0.
Unpacking gcc-4.0 (from .../gcc-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_4%3a4.0.3-1_i386.deb) ...
Selecting previously deselected package libstdc++6-4.0-dev.
Unpacking libstdc++6-4.0-dev (from .../libstdc++6-4.0-dev_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package g++-4.0.
Unpacking g++-4.0 (from .../g++-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.0.3-1_i386.deb) ...
Selecting previously deselected package make.
Unpacking make (from .../make_3.80+3.81.b4-1_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.11ubuntu7_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.1_i386.deb) ...
Selecting previously deselected package installwatch.
Unpacking installwatch (from .../installwatch_0.6.3-2ubuntu1_i386.deb) ...
Selecting previously deselected package checkinstall.
Unpacking checkinstall (from .../checkinstall_1.5.3-3ubuntu2_all.deb) ...
Selecting previously deselected package libmudflap0.
Unpacking libmudflap0 (from .../libmudflap0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package libmudflap0-dev.
Unpacking libmudflap0-dev (from .../libmudflap0-dev_4.0.3-1ubuntu5_i386.deb) ...
Setting up binutils (2.16.1cvs20060117-1ubuntu2.1) ...

Setting up linux-kernel-headers (2.6.11.2-0ubuntu18) ...
Setting up libc6-dev (2.3.6-0ubuntu20.4) ...
Setting up cpp-4.0 (4.0.3-1ubuntu5) ...
Setting up cpp (4.0.3-1) ...

Setting up gcc-4.0 (4.0.3-1ubuntu5) ...
Setting up gcc (4.0.3-1) ...

Setting up make (3.80+3.81.b4-1) ...

Setting up dpkg-dev (1.13.11ubuntu7) ...
Setting up installwatch (0.6.3-2ubuntu1) ...
Setting up checkinstall (1.5.3-3ubuntu2) ...
Setting up libmudflap0 (4.0.3-1ubuntu5) ...

Setting up libmudflap0-dev (4.0.3-1ubuntu5) ...
Setting up g++-4.0 (4.0.3-1ubuntu5) ...
Setting up libstdc++6-4.0-dev (4.0.3-1ubuntu5) ...

Setting up g++ (4.0.3-1) ...

Setting up build-essential (11.1) ...
mike@mike-desktop:~/Desktop$

---

### Post by taurus on 2007-03-03
So you have successfully installed both build-essential and checkinstall packages.  ;)

---

### Post by picpak on 2007-03-03
The problem seems to have been fixed...but just for good measure, run

```
sudo apt-get remove sauerbraten-data
```

to clear out everything.

---

### Post by MikeSz on 2007-03-03
I have no idea what its done! after the error, I fixed the sudo apt-get install -f to fix my synaptic and then reinstalled the secret of monkey island and scummvm.  After that ive just run that last command like suggested.  Other than that I have no idea whats happened - does this mean the game is installed and ready to play somewhere?

---

### Post by picpak on 2007-03-03
No, you've removed the game completely. It's not there now. Now you have to compile.

---

