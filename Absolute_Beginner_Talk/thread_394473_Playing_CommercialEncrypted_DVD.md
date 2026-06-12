---
title: "Playing Commercial/Encrypted DVD"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by Coryj100 on 2007-03-26
Playing Commercial/Encrypted DVD

Can someone please help?
 I have been searching though posts here, and on the Debian forums also Google searches for the past week or so.  I have been trying to play my son's “Cars”  DVD . I have as far as I can tell installed the correct library's,  libdvdcss plus dependencies also the win32codecs.
I started with VLC to make it play the DVD only because in my previous windows life I used it most.
after that one did not  work I tried uninstall totem and reinstall it with the xine lib.
then Mplayer, gine, Ogle , Xine player more or less in that order, I even tried Automatrix.
I know what I am trying to do is considered illegal in the US, but I don't live in the US.
I just want to play store bought DVD's on my computer mostly because my son thinks it cool to watch.
Heck at this point if there was a program out there like “PowerDVD” for Linux I would buy it. 
I'd love to rant about DRM,  but this is not the place.
Back to my problem, when I load the DVD into my ROM it mounts on my desktop automatically, but it shows up as a DVD – ROM DISK, right click on it and you either open, browse , stretch icon, eject, properties. When Open or browse it will not display anything in folder.
I am pretty much a complete NOOB when it comes to code, but i can copy and paste like theres no tomorrow.
So anyone who helps assume nothing other then I know where terminal is just tell me what you what code you need me to type in.  I will start with this because you may want to see this frist.
code
“ mplayer dvd”
produces 
“MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Unknown CPU Typ (Family: 6, Model: 10, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.


Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing dvd.
File not found: 'dvd'
Failed to open dvd.

also I have looked through any threads about either restricted dvd  or encrypted nothing worked for me.
thanks to anyone who takes time to help !!

---

### Post by crispy_420 on 2007-03-27
Just did a little search of DVD backup of this movie and it does appear that Disney does use a new version of protection. I know that you are not trying to backup this movie but this would be a good indication of new protection. And new protection means less compatibility. 

I my opinion there is nothing wrong the software you are using but rather Disney's new protection. Heck I've even had some DVDs not play in Windows and some not even recognized by the OS.

---

### Post by ridl on 2007-03-27
If you've got broadband, you could save yourself some time and just download a dvdrip. I wouldn't even consider that piracy, since you bought the darn thing and it's been viciously handicapped by the profit-rabid mouse.

---

### Post by zvacet on 2007-03-27
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs?highlight=%28dvd%29]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs?highlight=%28dvd%29")

---

### Post by wesley_of_course on 2007-03-27
Wesley here ;


    Perhaps ;   [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

   might help ?.  

      Good Luck !

---

### Post by Coryj100 on 2007-03-27
I have installed the libdvdcss before using that same link as posted in other threads on DVD's 

Here is the code from my terminal

troc@troc-desktop:~$ sudo /usr/share/doc/libdvdread3/install-css.sh
--21:22:23--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb)
           => `/tmp/libdvdcss.deb'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 25,178 (25K) [text/plain]

100%[====================================>] 25,178        40.50K/s             

21:22:24 (40.42 KB/s) - `/tmp/libdvdcss.deb' saved [25178/25178]

dpkg - warning: downgrading libdvdcss2 from 1.2.9-0.0ubuntu4 to 1.2.5-1.
(Reading database ... 130218 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.9-0.0ubuntu4 (using /tmp/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.5-1) ...

troc@troc-desktop:~$ 

So now after about 30 sec's  software updates  inform me of that I can install 
libdvdcss2
Simple foundation for reading DVD's - runtime libraries from version 1.2.5-1 to 1.2.9-0. Oubuntu4 (size: 33kb)

note I have done this step about 6 times previous to tonight

Tonight I tried some other store bought DVD's none that I tried worked.
I then tried rips of DVD's that I had in various formats DIVX, VOB, AVI, Mpeg 2,4
all worked with every player that i have installed.

---

### Post by Coryj100 on 2007-03-27
here is some more code just to show what i have installed

troc@troc-desktop:~$ sudo aptitude install libdvdread3
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
troc@troc-desktop:~$ sudo aptitude install libdvdread3 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
troc@troc-desktop:~$ sudo /usr/share/doc/libdvdread3/install-css.sh
--21:41:48--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb)
           => `/tmp/libdvdcss.deb'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 25,178 (25K) [text/plain]

100%[====================================>] 25,178        41.75K/s             

21:41:49 (41.70 KB/s) - `/tmp/libdvdcss.deb' saved [25178/25178]

dpkg - warning: downgrading libdvdcss2 from 1.2.9-0.0ubuntu4 to 1.2.5-1.
(Reading database ... 130218 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.9-0.0ubuntu4 (using /tmp/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.5-1) ...

troc@troc-desktop:~$ sudo aptitude install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages will be upgraded:
  libdvdcss2 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/34.0kB of archives. After unpacking 45.1kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 130217 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.5-1 (using .../libdvdcss2_1.2.9-0.0ubuntu4_i386.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.9-0.0ubuntu4) ...

troc@troc-desktop:~$ sudo aptitude install w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
troc@troc-desktop:~$

---

### Post by Coryj100 on 2007-03-27
this is what i get when using code "aptitude search libdvd"

 troc@troc-desktop:~$ aptitude search libdvd
p   libdvd-dev                      - extract video and audio tracks - devel fil
p   libdvd0                         - extract video and audio tracks - runtime f
v   libdvdcss                       -                                           
i   libdvdcss2                      - Simple foundation for reading DVDs - runti
i   libdvdcss2-dev                  - Simple foundation for reading DVDs - devel
i   libdvdnav-dev                   - The DVD navigation library, development pa
i   libdvdnav4                      - The DVD navigation library                
i   libdvdplay0                     - portable abstraction library for DVD menus
i   libdvdplay0-dev                 - development files for libdvdplay0         
i   libdvdread-dev                  - library for reading DVDs (development)    
i   libdvdread3                     - library for reading DVDs                  
v   libdvdread3-dev                 -                                           
troc@troc-desktop:~$

---

### Post by fenian on 2007-03-27
You may have to set the region code for your DVD drive in a terminal type 
> 
regionset

if it says this

> regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not retrieve region code settings of the drive!
This could mean your drive is region free and doesn't need any setting.
Would you like to change the region setting of your drive? [y/n]:


you don,t need to set anything so answer no.If it says something like this...

> regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: NONE
vendor resets available: 4
user controlled changes resets available: 5
drive plays discs from region(s):, mask=0xFF

Would you like to change the region setting of your drive? [y/n]:n

you will need to set the region code if you are in the USA the region code is 1 a list of codes for other regions can be found [here]("http://en.wikipedia.org/wiki/DVD_region_code")

---

### Post by Coryj100 on 2007-03-27
here is the last bit of code ill post for awhile, sorry if i putting up either to much infor or the wrong kind of info, basically I am just following suggestions that I have already tried, from other threads to show what steps i have already tried.

Code
 troc@troc-desktop:~$ sudo aptitude install libdvdnav4 libdvdplay0 libdvdread3
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
troc@troc-desktop:~$ aptitude show libc6-dev
Package: libc6-dev
State: installed
Automatically installed: no
Version: 2.4-1ubuntu12.3
Priority: optional
Section: libdevel
Maintainer: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Uncompressed Size: 8061k
Depends: libc6 (= 2.4-1ubuntu12.3), linux-libc-dev
Recommends: gcc | c-compiler
Suggests: glibc-doc, manpages-dev
Conflicts: libstdc++2.10-dev (< 1:2.95.2-15), gcc-2.95 (< 1:2.95.3-9),
           libpthread0-dev, libdl1-dev, libdb1-dev, libgdbm1-dev, libc6-dev (<
           2.0.110-1), locales (< 2.1.3-5), libstdc++2.9-dev, netkit-rpc,
           libc-dev
Replaces: man-db (<= 2.3.10-41), gettext (<= 0.10.26-1), ppp (<= 2.2.0f-24),
          libgdbmg1-dev (<= 1.7.3-24), ldso (<= 1.9.11-9), netkit-rpc, netbase
          (< 4.0), kerberos4kth-dev (< 1.2.2-10), libc6-prof (< 2.3.5-2)
Provides: libc-dev
Description: GNU C Library: Development Libraries and Header Files
 Contains the symlinks, headers, and object files needed to compile and link
 programs which use the standard C library.

troc@troc-desktop:~$

---

### Post by Coryj100 on 2007-03-27
> **fenian said:**
> You may have to set the region code for your DVD drive in a terminal type 


if it says this



you don,t need to set anything so answer no.If it says something like this...



you will need to set the region code if you are in the USA the region code is 1 a list of codes for other regions can be found [here]("http://en.wikipedia.org/wiki/DVD_region_code")

regionset is a bad command .

troc@troc-desktop:~$ regionset
bash: regionset: command not found
troc@troc-desktop:~$ regionset
bash: regionset: command not found
troc@troc-desktop:~$ regionset
bash: regionset: command not found
troc@troc-desktop:~$

---

### Post by fenian on 2007-03-27
sorry install regioset with...
> 
sudo apt-get install regionset

---

### Post by Coryj100 on 2007-03-28
here is what got,  I tried several of my dvd's with the same result

troc@troc-desktop:~$ sudo apt-get install regionset 
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  regionset
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 11.1kB of archives.
After unpacking 73.7kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe regionset 0.1-2 [11.1kB]
Fetched 11.1kB in 0s (20.3kB/s)
Selecting previously deselected package regionset.
(Reading database ... 130266 files and directories currently installed.)
Unpacking regionset (from .../regionset_0.1-2_i386.deb) ...
Setting up regionset (0.1-2) ...
troc@troc-desktop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.
troc@troc-desktop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.
troc@troc-desktop:~$

---

### Post by tcrroadie on 2007-03-28
Try using regionset with a standard commercial music cd in you cdrom/dvd drive. 

Should work.

---

### Post by ReverendJ1 on 2007-03-28
I know you said you tried Automatix to install everything, but have you tried EasyUbuntu? [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/) Its the same idea as Automatix. It got me up and running quickly. I am not sure if it would fix your problem, but it is fast and newbie friendly, so its worth a shot. Just a thought, but then again, I'm a newbie too.

---

### Post by Coryj100 on 2007-03-28
alright after "regionset"  I didn't change any settings  
code
troc@troc-desktop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 1, mask=0xFE

Would you like to change the region setting of your drive? [y/n]:n
troc@troc-desktop:~$ 


I can play the "Cars" dvd  but its really strange how this works, I cannot play DVD's in my main dvd-rom (plextor px-716a), 
I have to put the DVD in my slave dvd-rom (generic) if it reads the first time cool.
All of the players I have installed will play except Mplayer.
If the disk does not mount, I eject the disk, put the disk in my plextor rom it will mount it, but will not play the disk (I can open the disk and see the files on it). 
So I eject the disk, put it back in the generic drive and presto it reads and plays the same disk the previous it would not even mount??

oh well at least it works 
thanks for the help

---

### Post by fenian on 2007-03-28
From the info above it appears that regionset is not set and your master dvd drive is not region free.In order for it to play commercial dvds you will need to set it.Put a dvd in the drive and run regionset again answer yes to change the code.Libdvdcss will allow you to read disks from other regions even though the code is set though it can take some time to load them.

---

### Post by amr2205 on 2007-05-28
> **Coryj100 said:**
> I have installed the libdvdcss before using that same link as posted in other threads on DVD's 

Here is the code from my terminal

troc@troc-desktop:~$ sudo /usr/share/doc/libdvdread3/install-css.sh
--21:22:23--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb)
           => `/tmp/libdvdcss.deb'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 25,178 (25K) [text/plain]

100%[====================================>] 25,178        40.50K/s             

21:22:24 (40.42 KB/s) - `/tmp/libdvdcss.deb' saved [25178/25178]

dpkg - warning: downgrading libdvdcss2 from 1.2.9-0.0ubuntu4 to 1.2.5-1.
(Reading database ... 130218 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.9-0.0ubuntu4 (using /tmp/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.5-1) ...

troc@troc-desktop:~$ 

So now after about 30 sec's  software updates  inform me of that I can install 
libdvdcss2
Simple foundation for reading DVD's - runtime libraries from version 1.2.5-1 to 1.2.9-0. Oubuntu4 (size: 33kb)

note I have done this step about 6 times previous to tonight

Tonight I tried some other store bought DVD's none that I tried worked.
I then tried rips of DVD's that I had in various formats DIVX, VOB, AVI, Mpeg 2,4
all worked with every player that i have installed.

Je je, I've forgotten this one, thanks for refreshing my memory! By the way, it really works!

---

