---
title: "Yet another Kismet thread"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by KyleAwesome on 2006-08-05
Alright guys, after HOURS of trying to configure my wNIC (a linksys WPC54G v1.2) I finally got it working. So then I decided to try and install kismet... bad idea. I worked for hours to try and get it installed... 

Finally used sudo apt-get install kismet

seems like it worked, the files are in /etc/kismet/

now I went to start editing the kismet.conf file but I dont have permission to save the file?

I've used about every how-to on here and I cant find anywhere that says I need to change permissions or anything...

So how do I go about editing the kismet.conf file?

and what exactly do I need to add?
I know I have to tell it which user, but other then that I dont know where to add (or what for that matter) about my card and all. 

I'm in over my head! :-x 

Thanks in advance!
-Kyle

---

### Post by catlett on 2006-08-05
You have to preface commands with sudo to become root. If a file is owned by root you can't make any changes to it, only root can. To open the file /etc/kismet/kismet.conf in the gnome text editor gedit as root issue
```
sudo gedit /etc/kismet/kismet.conf
```
This post has some info on editing the file [http://www.ubuntuforums.org/showthread.php?t=191748&highlight=kismet](http://www.ubuntuforums.org/showthread.php?t=191748&highlight=kismet)

---

### Post by KyleAwesome on 2006-08-05
Thanks!

I added these two lines

```
# User to setid to (should be your normal user)
#suiduser=elyse
```

and 

```
# Sources are defined as:
# source=bcm43xx,wlan0,broadcom[,initialchannel]
```

Is that right so far?

now when I launch the program I get this

```
elyse@elyse-laptop:~$ sudo kismet
Password:
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'bcm43xx' in source 'bcm43xx,wlan0,broadcom[,initialchannel]'
elyse@elyse-laptop:~$

```

Is that because of my wNIC or is it because of something I didnt configure correctly? Thanks a TON!

---

### Post by catlett on 2006-08-05
I do not know this app personally, but I cut this out from that thread.
> 
Open a terminal and type sudo iwconfig ethX mode monitor and then sudo kismet.

Be sure you have /etc/kismet/kismet.conf correctly configured first. Read /usr/share/doc/kismet/README.gz for lots of direction.
It says to run 2 commands 
```
 sudo iwconfig ethX mode monitor
```With this command I do not know if ethx is the value to use or is it a way of saying eth? and you should replace x with the correct label.
then it is saying to run it as root ```
sudo kismet
```
The last line is the info to look into. It says there is a read me inside the kismet folder. That will have alot more info than me. Go to PLaces<Computer<Filesystem<usr<share<doc and look for the file it made. It should have installation and runtime instructions.
[COLOR="Red"]
EDIT Sorry I dsidn't see your post[/COLOR]. I've had the reply box open for over an hour, My sister is in the hospital with a difficult pregnancy and I got hung up on the phone,
Anyways it is about your wnic. 'bcm43xx' Is that how the computer sees the device

---

### Post by KyleAwesome on 2006-08-05
Whoa, hope she is okay Catlett!


How exactly do I tell how ubuntu see's my card?

I tried a few things and this is what I go

```
elyse@elyse-laptop:~$ sudo iwconfig eth1 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.
elyse@elyse-laptop:~$ sudo kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'bcm43xx' in source 'bcm43xx,wlan0,broadcom[,initialchannel]'
elyse@elyse-laptop:~$ sudo gedit /etc/kismet/kismet.conf
elyse@elyse-laptop:~$ sudo iwconfig eth1 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.
elyse@elyse-laptop:~$ sudo kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'bcm4306' in source 'bcm4306,eth1,broadcom[,initialchannel]'
elyse@elyse-laptop:~$

```

In the .conf file I set the device to be 43xx and that didnt work so I tried 4306 (the actual chipset) and still nothing. 

```
elyse@elyse-laptop:~$ sudo iwconfig eth1 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.
```

Does that mean my nic cant go into monitor mode and this is why I'm having issues? Or is that something else? Thanks again

---

### Post by catlett on 2006-08-06
Doyou have a wireless card? If so make sure you are entering it's correct label i.e. whatever  iwconfig
 gives as a reply
I do not run kismet so I do not know anything about it but looking at the documentation it monitors wireless cards and it has terrible documentation for setup.
I can't help furthere other than to say run 
```
iwconfig
```Then troubleshoot with the readme and kismet's site
[http://www.kismetwireless.net/documentation.shtml](http://www.kismetwireless.net/documentation.shtml)
[http://www.kismetwireless.net/forum.php](http://www.kismetwireless.net/forum.php)
[http://www.kismetwireless.net/links.shtml](http://www.kismetwireless.net/links.shtml)

---

### Post by insyzygy on 2006-08-06
It appears you are trying to get a broadcom chipset to work with kismet. I believe that the issue is that the version of kismet that is in the ubuntu repositories is about a year old and it seems to have been only recently that support for the broadcom chipset was added to kismet. If you look at the kismet website the latest version is 2006-04-R1. Whereas the one in the repository is 2005-08-R1. If you look at the changelog
[http://www.kismetwireless.net/CHANGELOG]("http://www.kismetwireless.net/CHANGELOG")
broadcom support wasn't added until december of 2005, i.e. 2005-12. So you have no chance of getting it to work with the version of kismet you installed 
by synaptic or apt-get.

If you really want to use kismet with your broadcom chipset you will probably have to compile the latest version of kismet yourself. Even then, it says support is experimental so it still may not work correctly. 

It might be easier to just see if you can find a cheap card with an atheros or prism chipset on ebay.

By the way I have a Dell with a mini-pci card that uses the broadcom chipset, I may try to compile this and see if I can get it to work (and so might be able to post instructions on the compilation process), however I also have a pcmcia card with the orinoco chipset that I already use with kismet so at the moment its not pressing to me and I won't have time to experiment for a couple days.

---

### Post by insyzygy on 2006-08-06
I have just compiled the latest version of kismet from source and it works great with my broadcom card. Get the source here
[http://www.kismetwireless.net/download.shtml]("http://www.kismetwireless.net/download.shtml")
I can describe the compilation process in more detail but basically just download the stable source to a directory, untar it. Then do assuming there are no errors at any stage
```
 ./configure 
```
```
 make dep 
```
```
 make 
```
```
 sudo make install 
```

I actually did 
```
 mkdir ~/kismet 
```
and 
then 
```
 ./configure --prefix=~/kismet --exec-prefix = ~/kismet 
```
so that it installed into my home directory and not my system files.

If you don't have make on your system you will have to download it from synaptic, there may be other compilers you need to download, I do a bit of programming so these were already on my system.

---

### Post by KyleAwesome on 2006-08-07
Thanks a ton!!! I'll give it a try tonight!
Thanks again

---

### Post by KyleAwesome on 2006-08-07
Hmm... it is still saying I dont have uclibc++ even after sudo apt-get install build-essential

So I did sudo apt-cache search uclibc++ and got this

```

elyse@elyse-laptop:~$ sudo apt-cache search uclibc++
libuclibc-dev - A small implementation of the C library
libuclibc0 - A small implementation of the C library
uclibc-toolchain - A compiler wrapper for uClibc
elyse@elyse-laptop:~$

```

So I try

```

elyse@elyse-laptop:~/kismet-2006-04-R1$ sudo apt-get install libuclibc-dev
Reading package lists... Done
Building dependency tree... Done
libuclibc-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
elyse@elyse-laptop:~/kismet-2006-04-R1$

```

Then I try again

```

elyse@elyse-laptop:~/kismet-2006-04-R1$ sudo ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... yes
checking how to run the C preprocessor... gcc -E
checking for platform-specific compiler flags... none needed
checking whether byte ordering is bigendian... no
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking for unistd.h... (cached) yes
checking for sys/types.h... (cached) yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking for an ANSI C-conforming const... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for ANSI C header files... (cached) yes
checking return type of signal handlers... void
checking whether lstat dereferences a symlink specified with a trailing slash... yes
checking whether stat accepts an empty string... no
checking for gettimeofday... yes
checking for memset... yes
checking for select... yes
checking for socket... yes
checking for strcasecmp... yes
checking for strftime... yes
checking for strstr... yes
checking for system-level getopt_long()... yes
checking for stdint.h... (cached) yes
checking for accept() addrlen type... socklen_t
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
checking for main in -luClibc++... no
configure: WARNING: uclibc++ not available on this system
checking for main in -lstdc++... yes
checking for group 'root'... yes
checking for group 'man'... checking for initscr in -lncurses... no
configure: WARNING: Unable to find libncurses
checking for initscr in -lcurses... no
configure: error: Unable to find libncurses or libcurses

```


Why is this happening?
Thanks!

---

### Post by insyzygy on 2006-08-07
ulibc isn't the issue, it just produced a warning (warnings tend not to be fatal for compiling). The error occured because you don't have libncurses and libncurses-dev installed. They can be apt-getted or obtained by synaptic. The specific packages I have are libncurses5 and libncurses5-dev. ncurses is a standard c library for controlling terminal style text interaces by the way, kismet uses it for its text based client.

---

### Post by KyleAwesome on 2006-08-07
Score one for linux noob.

I got the program complied and installed (as far as I know!)

then I went to start kismet and get this

```

elyse@elyse-laptop:~$ sudo kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
FATAL:  Could not find user 'your_user_here' for dropping priviledges.  Make sure you have a valid user set for 'suiduser' in your config file.  See the 'Installation & Security' and 'Configuration' sections of the README file for more information.
elyse@elyse-laptop:~$

```

so I went to edit my .conf file and changed everything to this


```

# User to setid to (should be your normal user)
suiduser=elyse

# Sources are defined as:
# source=bcm43xx,eth1,Broadcom[,initialchannel]
# Source types and required drivers are listed in the README under the

```

Is that right? my user is elyse and my wireless adapter is a linksys WPC54g v1.2 using the broadcom 4306 chipset. (p.s. am I supposed to leave the # sign's there or remove them?)
Thanks so much for your guy's help! It's been a life saver! :-)

---

### Post by insyzygy on 2006-08-07
Thats what I did. But you need to replace
```
# source=bcm43xx,eth1,Broadcom[,initialchannel
```
with
```
 source=bcm43xx,eth1,Broadcom[,initialchannel 
```
the 
```
# 
```
is a comment delimeter, the computer doesn't read lines starting with it (those are for people to read.)

Then you just do  ```
sudo kismet 
``` (if you installed as a system file) or go into the bin direction and
```
sudo ./kismet 
``` if you installed it in your home directory.
Kismet has to run with superuser priviliges so you need the sudo.

---

### Post by cantormath on 2006-08-07
this is suppose to be the user your logged in as:
```
# User to setid to (should be your normal user)
suiduser=elyse
```

and 

wlan0 should be the wireless card you are scanning with, erase [,initialchannel]
```
# Sources are defined as:
source=bcm43xx,wlan0,broadcom[,initialchannel]
```

should be 
```
source=bcm43xx,wlan0,broadcom
```

shouldnt have to change anything else.

```
elyse@elyse-laptop:~$ sudo kismet
Password:
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'bcm43xx' in source 'bcm43xx,wlan0,broadcom[,initialchannel]'
elyse@elyse-laptop:~$

```

Thats all you should have to change in kismet.conf, that should be it.
if you want to change what kismet does, take a look at kismet_ui.conf.

then you can open terminal and start kismet
```
sudo kismet
```

realize, that if you only have one card, you will loose internet because you card goes into monitor mode.  You might what to do this with 2 cards.

[here is my kismet.conf file]("http://cantormath.com/kismet.conf")

---

### Post by KyleAwesome on 2006-08-07
sorry this is taking so long...

this is what I have right now

```

# Name of server (Purely for organizational purposes)
servername=Kismet

# User to setid to (should be your normal user)
suiduser=elyse

# Sources are defined as:
source=bcm43xx,wlan0,Broadcom
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=none,none,addme

```

When I try to launch kismet I get this

```

elyse@elyse-laptop:~$ sudo kismet
Password:
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
FATAL:  Could not find user 'your_user_here' for dropping priviledges.  Make sure you have a valid user set for 'suiduser' in your config file.  See the 'Installation & Security' and 'Configuration' sections of the README file for more information.

```

What is it doing? In case you need to know, my login is

```

elyse

```

but when I run terminal it says 

```

elyse@elyse-laptop:~$

```

is that normal? and if so what else did I screw up, because it still wont launch...

Thanks alot!

---

### Post by insyzygy on 2006-08-07
Cantor math: you may want to remove the # in your first code snippet in front of suiduser, he has it correct in his post and if he changes it to the way you have it it would be unfortunate.

Firstly, you should only have one source line, leave the one withh bcm43xx alone and change

```
 source = none,none, none 
```
to 
```
 #source=none,none,none 
```.
Second are you sure our interface is wlan0, type 
```
iwconfig 
```
if you see wlan0 keep it as is, if you see eth1, replace wlan0 with eth1. 
If your login is elyse you should have suiduser=elyse as you do.

---

### Post by cantormath on 2006-08-07
instead of
```
 source=bcm43xx,wlan0,broadcom[,initialchannel]
```

try
```
source=bcm43xx,wlan0,broadcom
```

delete that last part,
and then

```
cantormath@cantormath-laptop:~$ sudo kismet
```

---

### Post by cantormath on 2006-08-07
> **insyzygy said:**
> Cantor math: you may want to remove the # in your first code snippet in front of suiduser, he has it correct in his post and if he changes it to the way you have it it would be unfortunate.

Firstly, you should only have one source line, leave the one withh bcm43xx alone and change

```
 source = none,none, none 
```
to 
```
 #source=none,none,none 
```.

thats wierd, I copied that from his quote.........hmmmm

---

### Post by KyleAwesome on 2006-08-07
it's still giving me this

```

elyse@elyse-laptop:~$ sudo kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
FATAL:  Could not find user 'your_user_here' for dropping priviledges.  Make sure you have a valid user set for 'suiduser' in your config file.  See the 'Installation & Security' and 'Configuration' sections of the README file for more information.
elyse@elyse-laptop:~$

```

here is my kismet.conf file

```

# Version of Kismet config
version=2005.06.R1

# Name of server (Purely for organizational purposes)
servername=Kismet

# User to setid to (should be your normal user)
suiduser=elyse

# Sources are defined as:
source=bcm43xx,wlan0,Broadcom
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
#source=none,none,addme

```

---

### Post by cantormath on 2006-08-07
> **KyleAwesome said:**
> it's still giving me this

```

elyse@elyse-laptop:~$ sudo kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
FATAL:  Could not find user 'your_user_here' for dropping priviledges.  Make sure you have a valid user set for 'suiduser' in your config file.  See the 'Installation & Security' and 'Configuration' sections of the README file for more information.
elyse@elyse-laptop:~$

```

here is my kismet.conf file

```

# Version of Kismet config
version=2005.06.R1

# Name of server (Purely for organizational purposes)
servername=Kismet

# User to setid to (should be your normal user)
suiduser=elyse

# Sources are defined as:
source=bcm43xx,wlan0,Broadcom
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
#source=none,none,addme

```

k, you need to uncomment
```
#source=none,none,addme
```
should be
```
source=<Capture Sources>,<Wireless_Card(ie. wlan0)>,<Just_a_name>
```

---

### Post by insyzygy on 2006-08-07
When you compiled did you just do ./configure or did you use the --prefix option. Oh and don't uncomment the source line, you already have a valid source line above it. 
Also type 
```
 finger 
```
what users does that display.

---

### Post by KyleAwesome on 2006-08-07
still gives me the same error about the user... :-| This is almost on the verge of being depressing!

Thanks everyone! (i know you guys have better things to do)

---

### Post by cantormath on 2006-08-07
> **KyleAwesome said:**
> still gives me the same error about the user... :-| This is almost on the verge of being depressing!

Thanks everyone! (i know you guys have better things to do)

did you uncomment
Code:

```
#source=none,none,addme
```

and put this
Code:

```
source=<Capture Sources>,<Wireless_Card(ie. wlan0)>,<Just_a_name>
```

---

### Post by insyzygy on 2006-08-07
Cantor Math: look at the beginning of the block of code he showed, he has a valid source line. He should leave it as he has it.

```
 source=bcm43xx,wlan0, Broadcom 
```

---

### Post by cantormath on 2006-08-07
Checkout my kismet.conf 
[here]("http://cantormath.com/kismet.conf")

---

### Post by cantormath on 2006-08-07
I thought it was messing up because he had comments, and [,initialchannel] at the end of his source line....

---

### Post by insyzygy on 2006-08-07
I don't think he is running as who he thinks he is, somehow. Try 
```
whoami
```
whatever is returned should be on the right side of suiduser =.

---

### Post by cantormath on 2006-08-07
> **insyzygy said:**
> I don't think he is running as who he thinks he is, somehow.
yeah, you are probably right, 
he should try to 
```
sudo -i
```
to see if he can get to root.
if not, he probably isnt in the right group.
either way though, I still dont think you can put 
```
[,initialchannel]
```
 at the end of the source, unless you actually put an initial channel...

GAWD I have to alway go and edit a post, ahhh!

---

### Post by insyzygy on 2006-08-07
k: are you sure you are editing the correct kismet.conf file.
The fact that you get the error "could not find user your_user_here" indicates that whatever kismet your trying to run isn't looking for elyse but "your_user_here" which means its looking at an unedited kismet.conf. There are a couple reasons this could happen.

 If you did not use the --prefix option, and just did make install then there is a kismet.conf file in /etc or /etc/kismet and you should be editing that one.

If you used the --prefix, then there is a <directory you installed to>/etc directory and in that directory you want to edit the kismet.conf there.

Another possibility is that you are editing the correct file but running a different version of kismet that is still on your system that is looking at a different kismet.conf. If you installed kismet via apt-get and didn't remove it, just typing kismet at the command might be running the old kismet.


If you used the --prefix option you will need to  either add the directory you installed to, to your path or go to <install directory>/bin and do 
```
sudo ./kismet
```

---

### Post by KyleAwesome on 2006-08-07
Alright here is this

```

whelyse@elyse-laptop:~$ whoami
elyse
elyse@elyse-laptop:~$

```

No i did not use the --prefix

I installed it to my home directory

when I would edit the kismet.conf file I would go

```

cd ~/kismet-2006-04-R1/conf

sudo gedit kismet.conf

```

So I went and checked in /etc/kismet/etc/kismet.conf

that has the same code as the one I've been editing

---

### Post by insyzygy on 2006-08-07
There we go if you are editing anything in 
```
~/kismet-2006-04-R1/conf
``` 
you are not doing anything, kismet will not look here for the file. It is fairly standing linux convention that config files will always be in /etc/

Look for ```
/etc/kismet.conf 
``` or 
```
/etc/kismet/kismet.conf 
```
That is the file you want to edit. It will be the same as the one you were editing but you won't have changed it. You need to do 
```
suiduser = elyse
```
and 
```
 source = bcm43xx, wlan0, Broadcom 
```
in this file (wlan0 or eth1 depending on what your iwconfig says.

---

### Post by cantormath on 2006-08-07
> **KyleAwesome said:**
> Alright here is this

```

whelyse@elyse-laptop:~$ whoami
elyse
elyse@elyse-laptop:~$

```

No i did not use the --prefix

I installed it to my home directory

when I would edit the kismet.conf file I would go

```

cd ~/kismet-2006-04-R1/conf

sudo gedit kismet.conf

```

So I went and checked in /etc/kismet/etc/kismet.conf

that has the same code as the one I've been editing

why did you not just

```
sudo apt-get install kismet
```?

---

### Post by KyleAwesome on 2006-08-07
here is everything!

```

elyse@elyse-laptop:~/kismet-2006-04-R1$ cd ~/kismet-2006-04-R1/conf
elyse@elyse-laptop:~/kismet-2006-04-R1/conf$ dir
ap_manuf      kismet.conf~       kismet_ui.conf      zaurus_kismet_ui.conf
client_manuf  kismet.conf.in     kismet_ui.conf.in
kismet.conf   kismet_drone.conf  zaurus_kismet.conf
elyse@elyse-laptop:~/kismet-2006-04-R1/conf$ sudo gedit kismet.conf
elyse@elyse-laptop:~/kismet-2006-04-R1/conf$


HERE IS MY .CONF
# Kismet config file
# Most of the "static" configs have been moved to here -- the command line
# config was getting way too crowded and cryptic.  We want functionality,
# not continually reading --help!

# Version of Kismet config
version=2005.06.R1

# Name of server (Purely for organizational purposes)
servername=Kismet

# User to setid to (should be your normal user)
suiduser=elyse

# Sources are defined as:
source=bcm43xx,wlan0,Broadcom
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
#source=bcm43xx,eth1,Broadcom

# Comma-separated list of sources to enable.  This is only needed if you defined
# multiple sources and only want to enable some of them.  By default, all defined
# sources are enabled.
# For example:
# enablesources=prismsource,ciscosource

# Do we channelhop?
channelhop=true

# How many channels per second do we hop?  (1-10)
channelvelocity=5

# By setting the dwell time for channel hopping we override the channelvelocity
# setting above and dwell on each channel for the given number of seconds.
#channeldwell=10

# Do we split channels between cards on the same spectrum?  This means if 
# multiple 802.11b capture sources are defined, they will be offset to cover
# the most possible spectrum at a given time.  This also controls splitting
# fine-tuned sourcechannels lines which cover multiple interfaces (see below)
channelsplit=true

# Basic channel hopping control:
# These define the channels the cards hop through for various frequency ranges
# supported by Kismet.   More finegrain control is available via the 
# "sourcechannels" configuration option.
# 
# Don't change the IEEE80211<x> identifiers or channel hopping won't work.

# Users outside the US might want to use this list:
# defaultchannels=IEEE80211b:1,7,13,2,8,3,14,9,4,10,5,11,6,12
defaultchannels=IEEE80211b:1,6,11,2,7,3,8,4,9,5,10

# 802.11g uses the same channels as 802.11b...
defaultchannels=IEEE80211g:1,6,11,2,7,3,8,4,9,5,10

# 802.11a channels are non-overlapping so sequential is fine.  You may want to
# adjust the list depending on the channels your card actually supports.
# defaultchannels=IEEE80211a:36,40,44,48,52,56,60,64,100,104,108,112,116,120,124,128,132,136,140,149,153,157,161,184,188,192,196,200,204,208,212,216 
defaultchannels=IEEE80211a:36,40,44,48,52,56,60,64

# Combo cards like Atheros use both 'a' and 'b/g' channels.  Of course, you
# can also explicitly override a given source.  You can use the script 
# extras/listchan.pl to extract all the channels your card supports.
defaultchannels=IEEE80211ab:1,6,11,2,7,3,8,4,9,5,10,36,40,44,48,52,56,60,64

# Fine-tuning channel hopping control:
# The sourcechannels option can be used to set the channel hopping for 
# specific interfaces, and to control what interfaces share a list of 
# channels for split hopping.  This can also be used to easily lock
# one card on a single channel while hopping with other cards.
# Any card without a sourcechannel definition will use the standard hopping
# list.
# sourcechannels=sourcename[,sourcename]:ch1,ch2,ch3,...chN

# ie, for us channels on the source 'prism2source' (same as normal channel
# hopping behavior):
# sourcechannels=prism2source:1,6,11,2,7,3,8,4,9,5,10

# Given two capture sources, "prism2a" and "prism2b", we want prism2a to stay
# on channel 6 and prism2b to hop normally.  By not setting a sourcechannels 
# line for prism2b, it will use the standard hopping.
# sourcechannels=prism2a:6

# To assign the same custom hop channel to multiple sources, or to split the 
# same custom hop channel over two sources (if splitchannels is true), list
# them all on the same sourcechannels line:
# sourcechannels=prism2a,prism2b,prism2c:1,6,11

# Port to serve GUI data
tcpport=2501
# People allowed to connect, comma seperated IP addresses or network/mask
# blocks.  Netmasks can be expressed as dotted quad (/255.255.255.0) or as
# numbers (/24)
allowedhosts=127.0.0.1
# Address to bind to.  Should be an address already configured already on
# this host, reverts to INADDR_ANY if specified incorrectly.
bindaddress=127.0.0.1
# Maximum number of concurrent GUI's
maxclients=5

# Do we have a GPS?
gps=true
# Host:port that GPSD is running on.  This can be localhost OR remote!
gpshost=localhost:2947
# Do we lock the mode?  This overrides coordinates of lock "0", which will
# generate some bad information until you get a GPS lock, but it will 
# fix problems with GPS units with broken NMEA that report lock 0
gpsmodelock=false

# Packet filtering options:
# filter_tracker - Packets filtered from the tracker are not processed or
#                  recorded in any way.
# filter_dump    - Packets filtered at the dump level are tracked, displayed,
#                  and written to the csv/xml/network/etc files, but not 
#                  recorded in the packet dump
# filter_export  - Controls what packets influence the exported CSV, network,
#                  xml, gps, etc files.
# All filtering options take arguments containing the type of address and
# addresses to be filtered.  Valid address types are 'ANY', 'BSSID',
# 'SOURCE', and 'DEST'.  Filtering can be inverted by the use of '!' before
# the address.  For example,
# filter_tracker=ANY(!00:00:DE:AD:BE:EF)
# has the same effect as the previous mac_filter config file option.
# filter_tracker=...
# filter_dump=...
# filter_export=...

# Alerts to be reported and the throttling rates.
# alert=name,throttle/unit,burst/unit
# The throttle/unit describes the number of alerts of this type that are
# sent per time unit.  Valid time units are second, minute, hour, and day.
# Burst rates control the number of packets sent at a time
# For example:
# alert=FOO,10/min,5/sec
# Would allow 5 alerts per second, and 10 alerts total per minute.
# A throttle rate of 0 disables throttling of the alert.
# See the README for a list of alert types.
alert=NETSTUMBLER,10/min,1/sec
alert=WELLENREITER,10/min,1/sec
alert=LUCENTTEST,10/min,1/sec
alert=DEAUTHFLOOD,10/min,2/sec
alert=BCASTDISCON,10/min,2/sec
alert=CHANCHANGE,5/min,1/sec
alert=AIRJACKSSID,5/min,1/sec
alert=PROBENOJOIN,10/min,1/sec
alert=DISASSOCTRAFFIC,10/min,1/sec
alert=NULLPROBERESP,10/min,1/sec
alert=BSSTIMESTAMP,10/min,1/sec

# Known WEP keys to decrypt, bssid,hexkey.  This is only for networks where
# the keys are already known, and it may impact throughput on slower hardware.
# Multiple wepkey lines may be used for multiple BSSIDs.
# wepkey=00:DE:AD:C0:DE:00,FEEDFACEDEADBEEF01020304050607080900

# Is transmission of the keys to the client allowed?  This may be a security
# risk for some.  If you disable this, you will not be able to query keys from
# a client.
allowkeytransmit=true

# How often (in seconds) do we write all our data files (0 to disable)
writeinterval=300

# Do we use sound?
# Not to be confused with GUI sound parameter, this controls wether or not the
# server itself will play sound.  Primarily for headless or automated systems.
sound=false
# Path to sound player
soundplay=/usr/bin/play
# Optional parameters to pass to the player
# soundopts=--volume=.3
# New network found
sound_new=/usr/local/share/kismet/wav/new_network.wav
# Wepped new network
# sound_new_wep=${prefix}/com/kismet/wav/new_wep_network.wav
# Network traffic sound
sound_traffic=/usr/local/share/kismet/wav/traffic.wav
# Network junk traffic found
sound_junktraffic=/usr/local/share/kismet/wav/junk_traffic.wav
# GPS lock aquired sound
# sound_gpslock=/usr/local/share/kismet/wav/foo.wav
# GPS lock lost sound
# sound_gpslost=/usr/local/share/kismet/wav/bar.wav
# Alert sound
sound_alert=/usr/local/share/kismet/wav/alert.wav

# Does the server have speech? (Again, not to be confused with the GUI's speech)
speech=false
# Server's path to Festival
festival=/usr/bin/festival
# Are we using festival lite?  If so, set the above "festival" path to also
# point to the "flite" binary
flite=false
# How do we speak?  Valid options:
# speech    Normal speech
# nato      NATO spellings (alpha, bravo, charlie)
# spell     Spell the letters out (aye, bee, sea)
speech_type=nato
# speech_encrypted and speech_unencrypted - Speech templates
# Similar to the logtemplate option, this lets you customize the speech output.
# speech_encrypted is used for an encrypted network spoken string
# speech_unencrypted is used for an unencrypted network spoken string
#
# %b is replaced by the BSSID (MAC) of the network
# %s is replaced by the SSID (name) of the network
# %c is replaced by the CHANNEL of the network
# %r is replaced by the MAX RATE of the network
speech_encrypted=New network detected, s.s.i.d. %s, channel %c, network encrypted.
speech_unencrypted=New network detected, s.s.i.d. %s, channel %c, network open.

# Where do we get our manufacturer fingerprints from?  Assumed to be in the
# default config directory if an absolute path is not given.
ap_manuf=ap_manuf
client_manuf=client_manuf

# Use metric measurements in the output?
metric=false

# Do we write waypoints for gpsdrive to load?  Note:  This is NOT related to
# recent versions of GPSDrive's native support of Kismet.
waypoints=false
# GPSDrive waypoint file.  This WILL be truncated.
waypointdata=%h/.gpsdrive/way_kismet.txt
# Do we want ESSID or BSSID as the waypoint name ?
waypoint_essid=false

# How many alerts do we backlog for new clients?  Only change this if you have
# a -very- low memory system and need those extra bytes, or if you have a high
# memory system and a huge number of alert conditions.
alertbacklog=50

# File types to log, comma seperated
# dump    - raw packet dump
# network - plaintext detected networks
# csv     - plaintext detected networks in CSV format
# xml     - XML formatted network and cisco log
# weak    - weak packets (in airsnort format)
# cisco   - cisco equipment CDP broadcasts
# gps     - gps coordinates
logtypes=dump,network,csv,xml,weak,cisco,gps

# Do we track probe responses and merge probe networks into their owners?
# This isn't always desireable, depending on the type of monitoring you're
# trying to do.
trackprobenets=true

# Do we log "noise" packets that we can't decipher?  I tend to not, since 
# they don't have anything interesting at all in them.
noiselog=false

# Do we log corrupt packets?  Corrupt packets have enough header information
# to see what they are, but someting is wrong with them that prevents us from
# completely dissecting them.  Logging these is usually not a bad idea.
corruptlog=true

# Do we log beacon packets or do we filter them out of the dumpfile
beaconlog=true

# Do we log PHY layer packets or do we filter them out of the dumpfile
phylog=true

# Do we mangle packets if we can decrypt them or if they're fuzzy-detected
mangledatalog=true

# Do we do "fuzzy" crypt detection?  (byte-based detection instead of 802.11
# frame headers)
# valid option: Comma seperated list of card types to perform fuzzy detection 
#  on, or 'all'
fuzzycrypt=wtapfile,wlanng,wlanng_legacy,wlanng_avs,hostap,wlanng_wext,ipw2200,ipw2915

# Do we use network-classifier fuzzy-crypt detection?  This means we expect 
# packets that are associated with an encrypted network to be encrypted too, 
# and we process them by the same fuzzy compare. 
# This essentially replaces the fuzzycrypt per-source option.
netfuzzycrypt=true

# What type of dump do we generate? 
# valid option: "wiretap" 
dumptype=wiretap
# Do we limit the size of dump logs?  Sometimes ethereal can't handle big ones.
# 0 = No limit
# Anything else = Max number of packets to log to a single file before closing
# and opening a new one.
dumplimit=0

# Do we write data packets to a FIFO for an external data-IDS (such as Snort)?
# See the docs before enabling this.
#fifo=/tmp/kismet_dump

# Default log title
logdefault=Kismet

# logtemplate - Filename logging template.
# This is, at first glance, really nasty and ugly, but you'll hardly ever
# have to touch it so don't complain too much.
#
# %n is replaced by the logging instance name
# %d is replaced by the current date as Mon-DD-YYYY
# %D is replaced by the current date as YYYYMMDD
# %t is replaced by the starting log time
# %i is replaced by the increment log in the case of multiple logs
# %l is replaced by the log type (dump, status, crypt, etc)
# %h is replaced by the home directory
# ie, "netlogs/%n-%d-%i.dump" called with a logging name of "Pok" could expand
# to something like "netlogs/Pok-Dec-20-01-1.dump" for the first instance and 
# "netlogs/Pok-Dec-20-01-2.%l" for the second logfile generated.
# %h/netlots/%n-%d-%i.dump could expand to
# /home/foo/netlogs/Pok-Dec-20-01-2.dump
#
# Other possibilities:  Sorting by directory
# logtemplate=%l/%n-%d-%i
# Would expand to, for example,
# dump/Pok-Dec-20-01-1
# crypt/Pok-Dec-20-01-1
# and so on.  The "dump", "crypt", etc, dirs must exist before kismet is run
# in this case.
logtemplate=%n-%d-%i.%l

# Where do we store the pid file of the server?
piddir=/var/run/

# Where state info, etc, is stored.  You shouldnt ever need to change this.
# This is a directory.
configdir=%h/.kismet/

# cloaked SSID file.  You shouldn't ever need to change this.
ssidmap=ssid_map

# Group map file.  You shouldn't ever need to change this.
groupmap=group_map

# IP range map file.  You shouldn't ever need to change this.
ipmap=ip_map

```

Here is the .conf in etc/kismet/etc

```

elyse@elyse-laptop:/etc/kismet$ sudo gedit kismet.conf

HERE IS THE .conf

# Kismet config file
# Most of the "static" configs have been moved to here -- the command line
# config was getting way too crowded and cryptic.  We want functionality,
# not continually reading --help!

# Version of Kismet config
version=2005.06.R1

# Name of server (Purely for organizational purposes)
servername=Kismet

# User to setid to (should be your normal user)
suiduser=elyse

# Sources are defined as:
source=bcm43xx,wlan0,Broadcom
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
#source=bcm43xx,eth1,Broadcom

# Comma-separated list of sources to enable.  This is only needed if you defined
# multiple sources and only want to enable some of them.  By default, all defined
# sources are enabled.
# For example:
# enablesources=prismsource,ciscosource

# Do we channelhop?
channelhop=true

# How many channels per second do we hop?  (1-10)
channelvelocity=5

# By setting the dwell time for channel hopping we override the channelvelocity
# setting above and dwell on each channel for the given number of seconds.
#channeldwell=10

# Do we split channels between cards on the same spectrum?  This means if 
# multiple 802.11b capture sources are defined, they will be offset to cover
# the most possible spectrum at a given time.  This also controls splitting
# fine-tuned sourcechannels lines which cover multiple interfaces (see below)
channelsplit=true

# Basic channel hopping control:
# These define the channels the cards hop through for various frequency ranges
# supported by Kismet.   More finegrain control is available via the 
# "sourcechannels" configuration option.
# 
# Don't change the IEEE80211<x> identifiers or channel hopping won't work.

# Users outside the US might want to use this list:
# defaultchannels=IEEE80211b:1,7,13,2,8,3,14,9,4,10,5,11,6,12
defaultchannels=IEEE80211b:1,6,11,2,7,3,8,4,9,5,10

# 802.11g uses the same channels as 802.11b...
defaultchannels=IEEE80211g:1,6,11,2,7,3,8,4,9,5,10

# 802.11a channels are non-overlapping so sequential is fine.  You may want to
# adjust the list depending on the channels your card actually supports.
# defaultchannels=IEEE80211a:36,40,44,48,52,56,60,64,100,104,108,112,116,120,124,128,132,136,140,149,153,157,161,184,188,192,196,200,204,208,212,216 
defaultchannels=IEEE80211a:36,40,44,48,52,56,60,64

# Combo cards like Atheros use both 'a' and 'b/g' channels.  Of course, you
# can also explicitly override a given source.  You can use the script 
# extras/listchan.pl to extract all the channels your card supports.
defaultchannels=IEEE80211ab:1,6,11,2,7,3,8,4,9,5,10,36,40,44,48,52,56,60,64

# Fine-tuning channel hopping control:
# The sourcechannels option can be used to set the channel hopping for 
# specific interfaces, and to control what interfaces share a list of 
# channels for split hopping.  This can also be used to easily lock
# one card on a single channel while hopping with other cards.
# Any card without a sourcechannel definition will use the standard hopping
# list.
# sourcechannels=sourcename[,sourcename]:ch1,ch2,ch3,...chN

# ie, for us channels on the source 'prism2source' (same as normal channel
# hopping behavior):
# sourcechannels=prism2source:1,6,11,2,7,3,8,4,9,5,10

# Given two capture sources, "prism2a" and "prism2b", we want prism2a to stay
# on channel 6 and prism2b to hop normally.  By not setting a sourcechannels 
# line for prism2b, it will use the standard hopping.
# sourcechannels=prism2a:6

# To assign the same custom hop channel to multiple sources, or to split the 
# same custom hop channel over two sources (if splitchannels is true), list
# them all on the same sourcechannels line:
# sourcechannels=prism2a,prism2b,prism2c:1,6,11

# Port to serve GUI data
tcpport=2501
# People allowed to connect, comma seperated IP addresses or network/mask
# blocks.  Netmasks can be expressed as dotted quad (/255.255.255.0) or as
# numbers (/24)
allowedhosts=127.0.0.1
# Address to bind to.  Should be an address already configured already on
# this host, reverts to INADDR_ANY if specified incorrectly.
bindaddress=127.0.0.1
# Maximum number of concurrent GUI's
maxclients=5

# Do we have a GPS?
gps=false
# Host:port that GPSD is running on.  This can be localhost OR remote!
gpshost=localhost:2947
# Do we lock the mode?  This overrides coordinates of lock "0", which will
# generate some bad information until you get a GPS lock, but it will 
# fix problems with GPS units with broken NMEA that report lock 0
gpsmodelock=false

# Packet filtering options:
# filter_tracker - Packets filtered from the tracker are not processed or
#                  recorded in any way.
# filter_dump    - Packets filtered at the dump level are tracked, displayed,
#                  and written to the csv/xml/network/etc files, but not 
#                  recorded in the packet dump
# filter_export  - Controls what packets influence the exported CSV, network,
#                  xml, gps, etc files.
# All filtering options take arguments containing the type of address and
# addresses to be filtered.  Valid address types are 'ANY', 'BSSID',
# 'SOURCE', and 'DEST'.  Filtering can be inverted by the use of '!' before
# the address.  For example,
# filter_tracker=ANY(!00:00:DE:AD:BE:EF)
# has the same effect as the previous mac_filter config file option.
# filter_tracker=...
# filter_dump=...
# filter_export=...

# Alerts to be reported and the throttling rates.
# alert=name,throttle/unit,burst/unit
# The throttle/unit describes the number of alerts of this type that are
# sent per time unit.  Valid time units are second, minute, hour, and day.
# Burst rates control the number of packets sent at a time
# For example:
# alert=FOO,10/min,5/sec
# Would allow 5 alerts per second, and 10 alerts total per minute.
# A throttle rate of 0 disables throttling of the alert.
# See the README for a list of alert types.
alert=NETSTUMBLER,10/min,1/sec
alert=WELLENREITER,10/min,1/sec
alert=LUCENTTEST,10/min,1/sec
alert=DEAUTHFLOOD,10/min,2/sec
alert=BCASTDISCON,10/min,2/sec
alert=CHANCHANGE,5/min,1/sec
alert=AIRJACKSSID,5/min,1/sec
alert=PROBENOJOIN,10/min,1/sec
alert=DISASSOCTRAFFIC,10/min,1/sec
alert=NULLPROBERESP,10/min,1/sec
alert=BSSTIMESTAMP,10/min,1/sec

# Known WEP keys to decrypt, bssid,hexkey.  This is only for networks where
# the keys are already known, and it may impact throughput on slower hardware.
# Multiple wepkey lines may be used for multiple BSSIDs.
# wepkey=00:DE:AD:C0:DE:00,FEEDFACEDEADBEEF01020304050607080900

# Is transmission of the keys to the client allowed?  This may be a security
# risk for some.  If you disable this, you will not be able to query keys from
# a client.
allowkeytransmit=true

# How often (in seconds) do we write all our data files (0 to disable)
writeinterval=300

# Do we use sound?
# Not to be confused with GUI sound parameter, this controls wether or not the
# server itself will play sound.  Primarily for headless or automated systems.
sound=false
# Path to sound player
soundplay=/usr/bin/play
# Optional parameters to pass to the player
# soundopts=--volume=.3
# New network found
sound_new=//usr/share/kismet/wav/new_network.wav
# Wepped new network
# sound_new_wep=${prefix}/com/kismet/wav/new_wep_network.wav
# Network traffic sound
sound_traffic=//usr/share/kismet/wav/traffic.wav
# Network junk traffic found
sound_junktraffic=//usr/share/kismet/wav/junk_traffic.wav
# GPS lock aquired sound
# sound_gpslock=//usr/share/kismet/wav/foo.wav
# GPS lock lost sound
# sound_gpslost=//usr/share/kismet/wav/bar.wav
# Alert sound
sound_alert=//usr/share/kismet/wav/alert.wav

# Does the server have speech? (Again, not to be confused with the GUI's speech)
speech=false
# Server's path to Festival
festival=/usr/bin/festival
# Are we using festival lite?  If so, set the above "festival" path to also
# point to the "flite" binary
flite=false
# How do we speak?  Valid options:
# speech    Normal speech
# nato      NATO spellings (alpha, bravo, charlie)
# spell     Spell the letters out (aye, bee, sea)
speech_type=nato
# speech_encrypted and speech_unencrypted - Speech templates
# Similar to the logtemplate option, this lets you customize the speech output.
# speech_encrypted is used for an encrypted network spoken string
# speech_unencrypted is used for an unencrypted network spoken string
#
# %b is replaced by the BSSID (MAC) of the network
# %s is replaced by the SSID (name) of the network
# %c is replaced by the CHANNEL of the network
# %r is replaced by the MAX RATE of the network
speech_encrypted=New network detected, s.s.i.d. %s, channel %c, network encrypted.
speech_unencrypted=New network detected, s.s.i.d. %s, channel %c, network open.

# Where do we get our manufacturer fingerprints from?  Assumed to be in the
# default config directory if an absolute path is not given.
ap_manuf=ap_manuf
client_manuf=client_manuf

# Use metric measurements in the output?
metric=false

# Do we write waypoints for gpsdrive to load?  Note:  This is NOT related to
# recent versions of GPSDrive's native support of Kismet.
waypoints=false
# GPSDrive waypoint file.  This WILL be truncated.
waypointdata=%h/.gpsdrive/way_kismet.txt
# Do we want ESSID or BSSID as the waypoint name ?
waypoint_essid=false

# How many alerts do we backlog for new clients?  Only change this if you have
# a -very- low memory system and need those extra bytes, or if you have a high
# memory system and a huge number of alert conditions.
alertbacklog=50

# File types to log, comma seperated
# dump    - raw packet dump
# network - plaintext detected networks
# csv     - plaintext detected networks in CSV format
# xml     - XML formatted network and cisco log
# weak    - weak packets (in airsnort format)
# cisco   - cisco equipment CDP broadcasts
# gps     - gps coordinates
logtypes=dump,network,csv,xml,weak,cisco,gps

# Do we track probe responses and merge probe networks into their owners?
# This isn't always desireable, depending on the type of monitoring you're
# trying to do.
trackprobenets=true

# Do we log "noise" packets that we can't decipher?  I tend to not, since 
# they don't have anything interesting at all in them.
noiselog=false

# Do we log corrupt packets?  Corrupt packets have enough header information
# to see what they are, but someting is wrong with them that prevents us from
# completely dissecting them.  Logging these is usually not a bad idea.
corruptlog=true

# Do we log beacon packets or do we filter them out of the dumpfile
beaconlog=true

# Do we log PHY layer packets or do we filter them out of the dumpfile
phylog=true

# Do we mangle packets if we can decrypt them or if they're fuzzy-detected
mangledatalog=true

# Do we do "fuzzy" crypt detection?  (byte-based detection instead of 802.11
# frame headers)
# valid option: Comma seperated list of card types to perform fuzzy detection 
#  on, or 'all'
fuzzycrypt=wtapfile,wlanng,wlanng_legacy,wlanng_avs,hostap,wlanng_wext,ipw2200,ipw2915

# Do we use network-classifier fuzzy-crypt detection?  This means we expect 
# packets that are associated with an encrypted network to be encrypted too, 
# and we process them by the same fuzzy compare. 
# This essentially replaces the fuzzycrypt per-source option.
netfuzzycrypt=true

# What type of dump do we generate? 
# valid option: "wiretap" 
dumptype=wiretap
# Do we limit the size of dump logs?  Sometimes ethereal can't handle big ones.
# 0 = No limit
# Anything else = Max number of packets to log to a single file before closing
# and opening a new one.
dumplimit=0

# Do we write data packets to a FIFO for an external data-IDS (such as Snort)?
# See the docs before enabling this.
#fifo=/tmp/kismet_dump

# Default log title
logdefault=Kismet

# logtemplate - Filename logging template.
# This is, at first glance, really nasty and ugly, but you'll hardly ever
# have to touch it so don't complain too much.
#
# %n is replaced by the logging instance name
# %d is replaced by the current date as Mon-DD-YYYY
# %D is replaced by the current date as YYYYMMDD
# %t is replaced by the starting log time
# %i is replaced by the increment log in the case of multiple logs
# %l is replaced by the log type (dump, status, crypt, etc)
# %h is replaced by the home directory
# ie, "netlogs/%n-%d-%i.dump" called with a logging name of "Pok" could expand
# to something like "netlogs/Pok-Dec-20-01-1.dump" for the first instance and 
# "netlogs/Pok-Dec-20-01-2.%l" for the second logfile generated.
# %h/netlots/%n-%d-%i.dump could expand to
# /home/foo/netlogs/Pok-Dec-20-01-2.dump
#
# Other possibilities:  Sorting by directory
# logtemplate=%l/%n-%d-%i
# Would expand to, for example,
# dump/Pok-Dec-20-01-1
# crypt/Pok-Dec-20-01-1
# and so on.  The "dump", "crypt", etc, dirs must exist before kismet is run
# in this case.
logtemplate=/var/log/kismet/%n-%d-%i.%l

# Where do we store the pid file of the server?
piddir=/var/run/

# Where state info, etc, is stored.  You shouldnt ever need to change this.
# This is a directory.
configdir=/var/lib/kismet/

# cloaked SSID file.  You shouldn't ever need to change this.
ssidmap=ssid_map

# Group map file.  You shouldn't ever need to change this.
groupmap=group_map

# IP range map file.  You shouldn't ever need to change this.
ipmap=ip_map

```

---

### Post by cantormath on 2006-08-07
> **insyzygy said:**
> Cantor Math: look at the beginning of the block of code he showed, he has a valid source line. He should leave it as he has it.

```
 source=bcm43xx,wlan0, Broadcom 
```

no he had
"```

# Sources are defined as:
# source=bcm43xx,wlan0,broadcom[,initialchannel]
```"

---

### Post by insyzygy on 2006-08-07
The version of kismet in the ubuntu repositories is about a year old, the broadcom bcm43xx, native linux driver is fairly recent. kismet support for this driver was not added until a later version than the one in the ubuntu repository, which is why we needed to compile the latest from source.

---

### Post by KyleAwesome on 2006-08-07
> **cantormath said:**
> why did you not just

```
sudo apt-get install kismet
```?

Because apparently that version is older then the version I'm using and does not support my card.

---

### Post by cantormath on 2006-08-07
> **insyzygy said:**
> The version of kisme in the ubuntu repositories is about a year old, the broadcom bcm43xx, native linux driver is fairly recent. kismet support for this driver was not added until a later version than the one in the ubuntu repository, which is why we needed to compile the latest from source.

icy......didnt know that.

---

### Post by insyzygy on 2006-08-07
k: was there no /etc/kismet.conf

It looks like it should be working or at least, we should be onto a different error.

---

### Post by KyleAwesome on 2006-08-07
both of those .conf's match up dont they? 

Are they actually two different files? or have I just been editing one file that is in two places?

---

### Post by KyleAwesome on 2006-08-07
> **insyzygy said:**
> k: was there no /etc/kismet.conf

It looks like it should be working or at least, we should be onto a different error.

there is a /etc/kismet/kismet.conf but no /etc/kismet.conf (that I see atleast)

---

### Post by insyzygy on 2006-08-07
I was just saying instead of /etc/kismet/etc/kismet.conf is there a /etc/kismet.conf.

In the directory try ```
ls -l 
``` if there is an arrow that has one file location pointing to the other then they are symlinked (more or less the same file in two places). And you still get the error that it can't find the user (your_user_here).

---

### Post by KyleAwesome on 2006-08-07
like this? 

```

elyse@elyse-laptop:~$ cd /etc/kismet
elyse@elyse-laptop:/etc/kismet$ ls -l
total 88
-rw-r--r-- 1 root root 13113 2005-11-15 12:47 ap_manuf
-rw-r--r-- 1 root root 25482 2005-11-15 12:47 client_manuf
-rw-r--r-- 1 root root 13453 2006-08-07 03:26 kismet.conf
-rw-r--r-- 1 root root 13457 2006-08-05 21:37 kismet.conf~
-rw-r--r-- 1 root root  4203 2005-11-15 12:47 kismet_drone.conf
-rw-r--r-- 1 root root  3584 2005-11-15 12:47 kismet_ui.conf
elyse@elyse-laptop:/etc/kismet$

```

---

### Post by insyzygy on 2006-08-07
I might have misled you, it appears kismet will be looking in 
```
/usr/local/etc/kismet.conf 
```
is this one edited.

You could try 
```
 cd / 
```
```
 locate kismet.conf 
```
and see if there are any others we are not aware of. Incidentally this is why I did the --prefix option, so it put everything related to this version of kismet I compiled into one place instead of all over my system.

---

### Post by KyleAwesome on 2006-08-07
Yup, that was the one. I edited that and tried sudo kismet

it came back saying there isnt a wlan0 (it shows up as eth1 on my machine :-\ ) so I tried that instead and then it says

```

elyse@elyse-laptop:~$ sudo kismet
Password:
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Will drop privs to elyse (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (Broadcom): Enabling monitor mode for bcm43xx source interface eth1 channel 6...
FATAL: Failed to set monitor mode: Invalid argument.  This usually means your drivers either do not support monitor mode, or use a different mechanism for getting to it.  Make sure you have a version of your drivers that support monitor mode, and consult the troubleshooting section of the README.
elyse@elyse-laptop:~$

```

Am I just hosed?

---

### Post by insyzygy on 2006-08-07
post the full results of 
```
 iwconfig eth1 
```
```
 lsmod | grep bcm43xx 
```
```
 iwconfig eth1 mode Monitor 
```

Also I'm assuming you have successfully used this card to connect wirelessly normally.
Also what version of the kernel are you using 
```
 uname -r 
```

---

### Post by KyleAwesome on 2006-08-07
here ya go

```

elyse@elyse-laptop:~$ iwconfig eth1
eth1      IEEE 802.11g  ESSID:"10118 NE Mason"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:16:B6:54:26:BB
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-51 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

elyse@elyse-laptop:~$

```

and 

```

elyse@elyse-laptop:~$ lsmod | grep bcm43xx

```

I get nothing after that so I tried
```

elyse@elyse-laptop:~$ lsmod|grep bcm43xx

```

still nothing...

what does that mean?

---

### Post by insyzygy on 2006-08-07
It means that your not using the bcm43xx driver for your nic. So I suppose the next question is at the beginning you said your spent hours trying to configure this card. How did you get it working. 

Please don't say you used ndiswrapper.

---

### Post by KyleAwesome on 2006-08-07
Honestly, I couldnt tell you, I read so many how to's and everyone only gave me a little help, so its kind of everything bashed together...

How do I tell if I've used it?

Thanks!

---

### Post by insyzygy on 2006-08-07
try 
```
 lsmod | grep ndiswrapper 
```
If this returns something with ndiswrapper you are using that if not, I have
no idea how you would have a working card with a broadcom chipset without the bcm43xx drivers.

---

### Post by KyleAwesome on 2006-08-07
so I'm hosed eh?

```

elyse@elyse-laptop:~$ lsmod | grep ndiswrapper
ndiswrapper           177364  0
usbcore               130692  3 ndiswrapper,ohci_hcd
elyse@elyse-laptop:~$

```

I just read that kismet doesnt support ndiswrapper, is there anyway to undo it?

---

### Post by insyzygy on 2006-08-07
I see. So you are using ndiswrapper. I should have asked earlier, I assumed since you were talking about bcm43xx, that you were using that driver.
You are not  hosed (but you will have to do some more work), undoing your ndiswrapper business is easy. To temporarily undo it you can just do ```
sudo rmmod ndiswrapper 
``` this will unload ndiswrapper.
To more permanently undo it without changing anything add 
```
 blacklist ndiswrapper
```
to ```
/etc/modprobe.d/blacklist
```
this keeps ndiswrapper from being loaded at boot (unless you explicitly load it) with sudo modprobe ndiswrapper. If you want ndiswrapper back just remove that blacklist line. Don't uninstall ndiswrapper, no point losing all your hard work incase things don't work, just blacklist it for the moment. According to 
[http://bcm43xx.berlios.de/?go=Devices]("http://bcm43xx.berlios.de/?go=Devices")
your card is compatible with the bcm43xx native linux drivers.
You just have to get them to work, this might be very simple.
It involves two parts. First you need to cut the firmware, to do this search on the forums for bcm43xx-fwcutter

The best reference is this 
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper")

I have some instructions and links to others here 
[http://www.ubuntuforums.org/showthread.php?t=227973&highlight=bcm4306]("http://www.ubuntuforums.org/showthread.php?t=227973&highlight=bcm4306")

Once you've done this (and blacklisted ndiswrapper).
you should be able to after inserting the card do 
```
sudo modprobe bcm43xx 
```
and have eth1 show up. Then kismet (may) work

I actually have bcm43xx and ndiswrapper both working on my system and both blacklisted I can choose which one i want to use by 
```
sudo modprobe bcm43xx
```
or
```
sudo modprobe ndiswrapper
```

Just so you know lsmod lists active modules (drivers). To check if ndiswrapper or bcm43xx are loaded do 
```
lsmod | grep ndiswrapper 
```
or 
```
lsmod | grep bcm43xx
```

(In case this is mysterious to you | is a pipe is sends the output of lsmod into grep, grep is a program for searching text, it searches to see if there was anything involving ndiswrapper or bcm43x. You could just type lsmod and search it yourself, but its about a page long full of drivers with nonsensical names.)

If you want to remove one or the other do 
```
rmmod ndiswrapper
```
```
rmmod bcm43xx
```
to load use modprobe as above. You can go back and forth just don' have them loaded simultaneously. I don't think you'll but crash but neither will actually work.

---

### Post by KyleAwesome on 2006-08-07
```

elyse@elyse-laptop:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5  invalid driver!
bcmwl5.sys      invalid driver!
lsbcmnds                driver present, hardware present
elyse@elyse-laptop:~$

```

I blacklisted ndiswrapper

then I went

```

elyse@elyse-laptop:~$ sudo apt-get install bcm43xx-fwcutter
Reading package lists... Done
Building dependency tree... Done
bcm43xx-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
elyse@elyse-laptop:~$

```

where exactly should I start?

EDIT

ok I di this

```

elyse@elyse-laptop:~$ lsmod | grep bcm43xx
bcm43xx               124044  0
ieee80211softmac       29696  1 bcm43xx
ieee80211              37064  2 bcm43xx,ieee80211softmac
elyse@elyse-laptop:~$

```

---

### Post by insyzygy on 2006-08-07
Your probably installed it at some point while trying to get the card to work. I would run the script 
```
sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh
```
If there are no errors, unload ndiswrapper 
```
sudo rmmod ndiswrapper
``` and see
what happens when you do 
```
sudo modprobe bcm43xx
``` 
Look at the end of dmesg by 
```
dmesg 
``` for errors loading bcm43xx.

---

### Post by KyleAwesome on 2006-08-07
ok did all that with no errors!!!

here is the output of dmesg I didnt see anything about bcm43xx

EDIT I redid every step and got this
```

[17182867.928000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17182868.068000] bcm43xx driver
[17182879.860000] eth1: no IPv6 routers present
[17182892.576000] device eth1 entered promiscuous mode
[17183110.248000] e100: eth0: e100_watchdog: link down
[17183136.876000] eth1: no IPv6 routers present
[17183207.976000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17183207.980000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17183207.980000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17183218.496000] eth0: no IPv6 routers present
[17184236.184000] ndiswrapper: device eth1 removed
[17184236.244000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[17184236.248000] Badness in remove_proc_entry at fs/proc/generic.c:705
[17184236.248000]  [<c0198793>] remove_proc_entry+0x113/0x120
[17184236.252000]  [<cfb027a4>] wrap_procfs_remove+0x24/0x30 [ndiswrapper]
[17184236.252000]  [<cfb043ce>] module_cleanup+0x3e/0xa0 [ndiswrapper]
[17184236.252000]  [<c013627e>] sys_delete_module+0x11e/0x150
[17184236.252000]  [<c0153a3a>] sys_munmap+0x3a/0x60
[17184236.252000]  [<c010304b>] sysenter_past_esp+0x54/0x79
elyse@elyse-laptop:~$



```

---

### Post by insyzygy on 2006-08-07
assuming you don't have ndiswrapper loaded (you did sudo rmmod ndiswrapper).
I would just try kismet again. you might want to reboot first. make sure ndiswrapper didn't load (lsmod | grep ndiswrapper returns nothing). Then load bcm43xx with sudo modprobe bcm43xx.

---

### Post by KyleAwesome on 2006-08-07
No such luck, now its saying

```

elyse@elyse-laptop:~$ sudo kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Will drop privs to elyse (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (Broadcom): Enabling monitor mode for bcm43xx source interface eth1 channel 6...
FATAL: GetIFFlags: interface eth1: No such device
elyse@elyse-laptop:~$

```

I'm so sorry this is taking so long. Thanks like no other

---

### Post by insyzygy on 2006-08-07
before you start kismet, make sure after you do 
```
 sudo modprobe bcm43xx
```
that ```
iwconfig 
```
list eth1 as present.

---

### Post by KyleAwesome on 2006-08-07
argh... lol

```

elyse@elyse-laptop:~$ sudo modprobe bcm43xx
elyse@elyse-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

elyse@elyse-laptop:~$ sudo kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Will drop privs to elyse (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (Broadcom): Enabling monitor mode for bcm43xx source interface eth1 channel 6...
FATAL: GetIFFlags: interface eth1: No such device
elyse@elyse-laptop:~$

```

---

### Post by KyleAwesome on 2006-08-07
ok rebooted now I get this

```

elyse@elyse-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=15 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

elyse@elyse-laptop:~$ sudo kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Will drop privs to elyse (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (Broadcom): Enabling monitor mode for bcm43xx source interface eth1 channel 6...
Source 0 (Broadcom): Opening bcm43xx source interface eth1...
Spawned channelc control process 6845
Dropped privs to elyse (1000) gid 1000
Source 1 (addme): Opening none source interface none...
FATAL: Please configure at least one packet source.  Kismet will not function if no packet sources are defined in kismet.conf or on the command line.  Please read the README for more information about configuring Kismet.
Sending termination request to channel control child 6845...
Waiting for channel control child 6845 to exit...
Kismet exiting.
elyse@elyse-laptop:~$

```

Should I reformat and start from scratch?

(PS what is this nm-- applet thing that asks for a password every boot? and the little wireless signal indicator in my main taskbar no longer connects if that has something to do with it)

---

### Post by insyzygy on 2006-08-07
UPDATE: From what you just posted its WORKING fine, you just didn't change the source = bcm43xx,eth1,Broadcom line in the kismet.conf file(the one at /usr/src/etc/kismet.conf) its still looking for the interface none which is what it is before you configure it.

Ok so we have't yet got the bcm43xx drivers working. I have to go to sleep now, but I'll continue tomorrow. There are a couple things you can do. First when you do 
```
sudo modprobe bcm43xx 
```
search through the logs in /var/log/dmesg , /var/log/syslog, or /var/log/messages for anything interested right after you load the module (errors, etc). 
You might search about bcm43xx and your card for specific info, I have a different card mini-pci, so 
Next by doing 
```
pccardctl ident 
```
you will get the manfid, check that it matches that listed on 
[http://bcm43xx.berlios.de/?go=Devices]("http://bcm43xx.berlios.de/?go=Devices")
So we know we really have the right card. 
Just mainly search for bcm43xx and your specific card.

---

### Post by insyzygy on 2006-08-07
No, I think your there, I think you didn't change the source line in /usr/src/etc/kismet.conf. I really am going to go to sleep now but from you last output from kismet everything is working except it has the wrong sources, you should have a line (and only one) in the correct kismet.conf that reads 
```
source=bcm43xx,eth1,Broadcom
```
and I think it will work.

---

### Post by insyzygy on 2006-08-07
You are so close. I was laying in bed and then realized I know what your doing wrong.  I'm pretty sure I'm correct because I just duplicated the error you got, on my machine. In /usr/src/etc/kismet.conf you probably have one line reading 
```
source=bcm43xx,eth1,Broadcom
```
but you have another reading
```
source=none,none,addme
```
delete this last one, it is causing kismet to crash. If I add that last line(which you should delete) to my working kismet.conf file, kismet fails with the same error you got. But if you look at the output you got, eth1 was put into monitor mode, so once you remove this extra source line, it should work.

---

### Post by KyleAwesome on 2006-08-07
Ahh man...

Well I lost all use of my wired nic and it was taking FOREVER to load into the OS I have no idea what happened but I just reformatted.

The only things I have done so far are

```

sudo apt-get install build-essential
sudo apt-get install bcm43xx-fwcutter
sudo apt-get install libncurses-dev

and then ran

sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh

```

I'm basiclly going to wait for further instructions, because I hosed the thing a few hours ago!
Thanks to everyone for putting up with this!

---

### Post by insyzygy on 2006-08-07
Ok. Hmm. Well first rebuild kismet. You will need to get libncurses and libncurses-dev again. 
If you ran the script is the card now working. If you insert the card 
does ```
iwconfig 
``` show eth1 present.
If the bcm43xx doesn' load when you insert the card, try
doing 
```
sudo modprobe bcm43xx 
```
this should cause 
```
iwconfig 
```
to list eth1 as present(it appeared this worked before you reformatted, so it ought to work again). Also if eth1 is present, check if you can connect wirelessly.

Does anyone else have more experience with this card to confirm that these steps work? His card is pcmcia, I have a mini-pci card (but with the same chipset).so I can't confirm the procedure. I think this is all one should have to do. 

After you recompile and install kismet 
again edit ```
/usr/src/etc/kismet.conf 
```
to change ```
suiduser = elyse
```
and ```
source = bcm43xx,eth1,Broadcom
```
Further makesure this is the only line beginning source =,  you delete any line like
```
source = none,none,addme 
```
that should be it. (But things are the never the way they should be, are they).

Also, its weird that you lost your regular internet connection. I had a similar problem on a thinkpad, it had way to many devices on the same irq and this often caused the kernel to disable this irq at boot, making these devices appear to dissapear. Try booting without the linksys card in, insert it after boot.

---

### Post by drewsimon on 2006-08-07
```

source=madwifi_b,ath1,madwifi

```

Here's a question. for the source you can put "madwifi_a"  "madwifi_b"  "madwifi_g" and a bunch of others. How do you know which one to use?

---

### Post by insyzygy on 2006-08-07
Assuming you are using madwifi drivers it depends on what mode you want to use.  If you have a device using madiwifi driviers then madwifi_a, madwifi_b, madwifig_g,etc correspond to whether your card is operating using 802.11a, b or g or combinations.

If you read the info at 
[http://www.kismetwireless.net/documentation.shtml]("http://www.kismetwireless.net/documentation.shtml")
(lookin section 12 under madwifi) they explain what corresponds to what.

---

### Post by KyleAwesome on 2006-08-08
So I re-did everything just now and FINALLY SUCCESS!!!

insyzygy I want to thank you so much! 

I've been letting it scan for about 10mins, and so fars its picked up my network, a probe network and one with the SSID of linksys

```

                                 T | W | Ch | Pkts | Flags |   IP   | Size
! 10118 NE Mason       a   o   011   3584     0     0.0.0.0     4k 
+ Probe Network        g   n  ---      10       0      0.0.0.0     0b
  linksys                     a   y   006     8       0      0.0.0.0    128b

```

What does all of this mean? And when I attempt to use any of the options it says that "the option is not available in autofit mode, how am I supposed to use any of the functions? Thanks!

---

### Post by insyzygy on 2006-08-08
I'm glad you got it working. Most things in ubuntu work without much hassle, wifi is not one of them. 

As for kismet first note what its doing. The whole reason we had to go through this trouble(bcm43xx instead of ndiswrapper) was so you card would go into monitor mode. 
Normally wifi cards only listen to packets that are meant for them and ignore (kindly) packets that aren't theirs. In monitor mode your card accepts every packet it hears regardless of who sent it and who it was meant for. Kismet uses this data to analyze the networks in your vicinity, including hidden networks (stealthed)

First note you can type the letter h at any time for a help menu. If you want to get more info on some networks first type the letter s, then choice some method of sorting (say packet count). Now you can scroll through the networks. Hitting enter will give you more details. The letter q will close this. There are lots of other features kismet has, there are also graphical clients that replace the text interface but I haven't used these.

Probe networks is the way kismet lists other clients (computers) searching for wifi connections (it listens to everything).  You'll have to read the kismet documentation for more info on all its capabilities.

In the example you posted 
T is the type, Ch is the channel, W is encryption(WEP or WPA), Packets is the number of packets it received, and IP Range is the internal ip address structure of the network.

Note that Kismet is actually recording all the packets it receives , they are put in (on my computer) /var/log/kismet/
If your interested in analyzing the captured data you should apt-get the program ethereal.  These files can get big if you let kismet run for a while so you should be aware they are there to delete old ones if you need to.

---

### Post by KyleAwesome on 2006-08-08
Yeah, I get the basics of it. But what I didnt understand is when its scanning say I go to hit i for detail information or any other command it says that its not supported under this mode.

So first question, do I leave it on default autofit mode?

Secondly, is ethereal anywhere near as complicated as kismet was? Or do I just sudo apt-get install ethereal and then what? 

So I'm assuming that is the progam I would use to look at the packets which may or may not contain information related to the characters needed to obtain a wep password correct? [-X  ;)  

What about all that packet injection and all that other fun stuff, or is that only in KisMAC? Thanks again!

---

### Post by insyzygy on 2006-08-08
To get around that "not being supported in this mode" just change the way its sorting things by pressing the letter s and then choosing some sorting method. Ethereal is just a standalone program it doesn't directly interact with your network devices so just sudo apt-get install it, and then open the dump files in /var/log/kismet. (It can I think be configured to analyze in real time but I've never used that.) 

If your goal is too crack WEP you need some other tools (and ethereal won't be helpful at analzing encrypted packets). You won't find WEP passcodes just by analyzing captured packets (its a very crappy encryption protocol but not that crappy). I would point you at aircrack which is in the repositories. It can analyze kismet dump files and if you have captured enough packets it can crack WEP keys. It also has a similar program called airodump that will just capture packets similarly to kismet (but without the analysis), this program (despite what it says in the documentation) will work with your bcm43xx driver you just have to first do \[sudo iwconfig eth1 mode Monitor \] before running it. 

These tools would in principle let you break a WEP key, but unless the network has massive amounts of traffic that you are intercepting it will probably take a long time. Packet injection would speed things up. Kismet does not support this. (Note kismet is totally silent and passive, packet injection is not.) 

Aircrack does support packet injection but only on certain cards. As the bcm43xx driver is new packet injection is not yet supported (but if you go to the the aircrack website people are developing it, it should be possible eventually. )

I mainly use kismet to search for stealthed networks (not broadcasting SSID) to get free wifi. I've played around with aircrack for a little while out of curiosity but never captured enough packets to break a key (I didn't try very hard).

Also if you are just trying to break into a network for free wifi you should be aware that this is clearly illegal and is likely detectable and most importantly is likely to cause problems for the owner of the connection.(Its questionable whether using unsecured wifi is illegal. I don't feel bad as long as I don't cause problems for anyone.) For one thing any network that is WEP encrypted likely also is using Mac filtering. Which means you will also have to spoof your mac address. This is easy in linux but you will have to spoof it to the mac address of someone in their network (this is easy since you can figure that out from kismet). However if you do this and have the same mac address as someone actively using the network at the same time, both you and them may have problems connecting correctly and it will probably be noticed. If its just joe blows router then maybe they won't figure it out, but you will be causing them problems. Just a warning.

---

### Post by KyleAwesome on 2006-08-09
Yeah, I got it installed and pulled up a dump file, took a look around everything appears to be in hex, do I need to convert this or is there something specific I'm looking for?

EDIT:
ah answers my questions! I dont have any WEP networks around here to test out but maybe someday I'll try out aircrack.

---

### Post by KyleAwesome on 2006-08-09
One more thing I dont undrestand and it doesnt say anything in the help section isd how to read the flags, two networks around here were  flagged and I was curious as to why?

---

### Post by insyzygy on 2006-08-09
Ethereal is very popular if you do some web searches you will find lots of info about it with how toos. A lot of what you will capture is just broadcast signals (access points proclaiming their presence). One thing that is useful is to find packets that have protocol tcp or http and go to analyze->follow tcp stream. I personally haven't had much use for ethereal its amusing sometimes to capture packets in a public place and then try and figure out what people were looking at, beyond that you would need a specific reason for analyzing packet data. If someone was retarded enough to telnet over wifi you could read their login and password in plain text, but most everything requires ssh now so thats unlikely. If your not a penetration tester it probably isn't useful other than the fact that its amusing to be able to watch other peoples traffic (even if it is encrypted). Also if you capture wep encrypted or ssl encrypted traffic it will be incomprehensible.

---

### Post by insyzygy on 2006-08-09
If you look in the help (press h) a couple screens down they explain what the flags correspond to .

---

### Post by KyleAwesome on 2006-08-09
Yeah, I took a look at that but didnt think it had what I was looking for until it dawned on my 

there is a network called linksys (default) and under flags it says   FT4 I was looking for a specific meaning for FT4, but I've now come to believe it reads like a legend!

F = factory
T = address found via TCP
and the 4 = how many address found

correct?

yeah I have no reason to look either, I just read a few pages of Wi-Foo at borders the other day and wanted to give it a try

---

### Post by insyzygy on 2006-08-09
I believe you are correct. As I said I don't really use the captured packets other than as a curiosity. (Anything else you could do would probably be somewhat malicious). Kismet is mostly useful to me due to the fact that it can identify networks regular scanning won't. The way wifi works access points normally broadcast their existence and name. Some are stealthed they are listening but you have to know about them apriori. Kismet detects these by analyzing clients connected to them. At the moment I'm connected on a stealted network that for some reason is unencrypted (why would you stealth and then not encrypt, probably factory setting.) Kismet can also detects networks who access points are out of range of you, if it can hear any connected clients. There are cool tools for constructing wifi maps using kismet as well with a gps plugin, never used that before. Kismet also lets you identify other computers trying to connect which is interesting.

---

### Post by tripwire45 on 2006-08-13
Sorry to pop in out of left field but I've been having a related issue. I got my sources issue settled with my PCMCIA Linksys card by entering:

```
source=wrt54g,wlan0,prismX
```

Another problem has cropped up and I can't seem to find documentation on it. When I type *kismet* on the command line, kismet opens in the same console. However, I can't figure out how to stop kismet and exit except by just closing the console. Problem is that my WLAN card is still stuck in monitor mode. The only way I can recover it is to reboot the system. 

There's got to be a better way. Any ideas? Thanks.

---

### Post by insyzygy on 2006-08-14
Shift + q should exit kismet. Many cards don't come out of monitor mode well (kismet even has a warning about this). If its pcmcia, just eject the card and reinsert it, should reset everything.

pressing h while kismet is running will give you a help menu.

---

### Post by Jimmmmy on 2007-05-15
Hi there, I am quite new to linux, actualy very new. I have managed to get my broadcom drivers installed using the fwcutter tool, and can connect to wireless networks ok. 

I'm having trouble with getting kismet to work properly, when I try to invoke it by typing kismet in console I get this error > FATAL: Support for capture source type 'bcm43xx' was not built. Check the output from 'configure' for more information about why it might not have been compiled in. 

After looking in the configure logs, I did a search for bcm43xx and it wasn't present in the logs, so basically I'm stuck here.

I would be really grateful if anyone could help me.

Also I'm using Dell Lattitude d600 laptop with a minipci truemobile 1400 with Broadcom 4306 chipset. And the OS is Ubuntu 7.0.4 (I think... the april release) kernel version 2.6.20-15-generic.

Thanks in advance.

---

### Post by Jimmmmy on 2007-05-16
Hi , solved the problem, well got kismet to start up not sure if it works properly yet. 

To get it to start up had to rebuild kismet from scratch when doing first step ./configure had to use this:

```
./configure --enable-bcm43xx
```

then do the rest as before.

---

### Post by gunbladeiv on 2007-06-12
im using kismet with bcm43xx capture source enable.
but i dun know how to crack wep. can someone teach me?

---

### Post by nieve on 2007-06-14
¿Could you tell me how did you rebuilt?
kiskmet tells me the same, but I dont know how to get where you did
thanks a lot

---

### Post by CrzyNic on 2007-06-16
I'm having problems with

> FATAL: Support for capture source type 'bcm43xx' was not built. Check the output from 'configure' for more information about why it might not have been compiled in.
So I tried doing
```
./configure --enable-bcm43xx
```

but I'm still having the same message.

Is there something I have to do before I recompile kismet? Do I need to delete the files or anything like that? I noticed that it just FLIES through it...any help would be great.

---

### Post by Joker5bb on 2008-07-05
bcm43xx is old, b43 is the new driver 

For a latest version of Kismet compile from source. 

```
wget http://www.kismetwireless.net/code/kismet-2008-05-R1.tar.gz
tar -xzf kismet-2008-05-R1.tar.gz
cd kismet-2008-05-R1
./configure
make dep
make
sudo make install

```

```
sudo gedit /usr/local/etc/kismet.conf
```

change the following line
source=b43,wlan0,broadcom
save

To run Kismet 
```
sudo kismet
```

---

