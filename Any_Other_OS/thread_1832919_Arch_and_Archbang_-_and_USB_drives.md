---
title: "Arch and Archbang - and USB drives"
date: 2011-08-25
forum: Any Other OS
---

### Post by 23dornot23d on 2011-08-25
Archbang  .... then when I get used to this Distro ... may try Arch .....

First time I have used it and its already causing me headaches.......

But I am sure it will be good once I get used to the way it works
and work out how to get it onto a USB drive ....

So for the time being will use Archbang .... on LiveCD as that is all I can get working on my machine ....

Even that is having problems going onto my USB stick ...... reports wrong settings for C.H.S ......
Even though it is supposedly doing the partitioning .....

[IMG]http://img30.imageshack.us/img30/6411/2011082513142846951360x.jpg[/IMG]


But as a plus this runs so quickly from CD ..... a install - probably not even needed

Has anybody got this running from a flash drive ok and is there a good explanation of how to set the flash drive for it

I tried just using Arch Installer ...... not a chance of it working ..... on a 2 Gig or 8 Gig USB so far
I tried using gparted to format the USB ready for it ..... still not a chance of it working .....
I tried it on My 1 Terra Hard drive ...... my partition table was lets say not the best looking partition table I have had
once using this Installer ...........

So lets start from the beginning ..... obviously I am doing something very wrong ....... with the USB ....
Maybe it should not be formatted first ..... maybe it should not be mounted ...... maybe it should be bigger than 8 Gig
Who knows ....
Maybe the CD I have is faulty .....

Lets run through as many things as possible in one night to see where we can get to ....... and see if others have had the same experiences .......

I have a feeling this will install ok to the main drive ..... 
( but I have no room left for it on there - so that is out for the time being )

So lets try again ...... this time I will just empty the USB completely ..... and try again ..... but recording what I do here
if anybody sees anything obvious that I do wrong feel free to add constructive criticism .....

First thing using the Archbang 300 Meg CD for installation ....
tried to a 2 Gig Memory stick ..... unformatted .... same problem ..... the Installer does not know how to use it ....

and it gives me no options to tell it anything about it ...... so it assumes the disk structure and gets it wrong ......
so the 2 Gig is out of the way now ......

Lets move onto the 8 Gig ...... as you probably guessed I have already tried a couple of times previous to this .....
so ..... is it worth it is my next question ..... as getting it to install is this much hassle whats the rest of the
trip going to be like ....... what do I stand to gain .....

Knowledge ...... so its worth the TRIP .....

First thing is the Google Search [_***Arch and USB Drives***_]("http://www.google.fr/search?q=Arch+and+USB+Drives&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a")

[https://wiki.archlinux.org/index.php/Installing_Arch_Linux_on_a_USB_key](https://wiki.archlinux.org/index.php/Installing_Arch_Linux_on_a_USB_key)

ok so 3 Gig is the recomended minimum ........... so the 2 Gig has no chance then .......

from the above link ....
> 
It is best to manually partition the drive, as the auto partition may not work, and will create unnecessary partitions. 
So Exactly how do I get it to partition the 8 Gig stick then ..... and get the Install onto it ......

Choices ..... that I have seen so far ....

1 ..... Use the Arch install CD ...... tried and failed
2 ...... Use the Archbang CD ........ tried and failed
3 ....... Use [_***another Linux operating system ***_]("https://wiki.archlinux.org/index.php/Install_from_Existing_Linux")to load it up ..... ok sounds good ....

Lets check [[COLOR=Red]_***Archbang Forums ***_[/COLOR]]("http://bbs.archbang.org/")out too ....whats the latest ....

[http://bbs.archbang.org/viewtopic.php?id=776](http://bbs.archbang.org/viewtopic.php?id=776)


Looking at trying this out now ..... its old ..... but it may do what I want ....

[http://archlinux.me/brain0/2010/05/29/arch-linux-usb-install-and-resuce-media/](http://archlinux.me/brain0/2010/05/29/arch-linux-usb-install-and-resuce-media/)

which then got me to look at this [_***ISOLINUX***_]("http://www.syslinux.org/wiki/index.php/Doc/isolinux#HYBRID_CD-ROM.2FHARD_DISK_MODE")

---

### Post by cbowman57 on 2011-08-25
Wish I could offer assistance but I don't have any experience using external USB drives.  If I find anything I'll post it.

I found this [https://bbs.archlinux.org/viewtopic.php?id=115012](https://bbs.archlinux.org/viewtopic.php?id=115012)

How far are you getting into installation?  It won't let you partition the USB drive at all?

---

### Post by 23dornot23d on 2011-08-25
Cheers Chuck

USB's are a dead loss on this old machine ...... so its not just Arch - did the same with Slackware too ....

I have Arch on my main drive now ..... sda4 ..... 

I wiped a installation of Slackware off .... still have one on sda6 though ..... with the steampunk setup .... 
looks good too ..... keep using it now .....

It goes onto the main drive easily ...... am now faced with setting up the graphics and 
getting the package manager to work .....

But at the command line everything is good ...... ty for the link too .....

I did the full install from the i686 CD ...... the latest I could find ..... 3.0-Arch is returned
from uname -r

---

### Post by cbowman57 on 2011-08-25
So, save the list in the code box as **pkglist**, copy it to your new installation and execute it like this 
[B]pacman -S $(< pkglist)

[/B]Assuming that machine can use the proprietary Nvidia drivers it should set you up pretty quick.


This might be useful, my pkglist:
$ pacman -Qeq

```

afio
alacarte
appset-qt
arch-firefox-search
at-spi2-atk
at-spi2-core
audit
bash
bash-completion
binutils
bison
bleachbit
brasero
bzip2
clementine
coreutils
cronie
cryptsetup
customizepkg
device-mapper
dhcpcd
diffutils
e2fsprogs
empathy
eog
epiphany
evolution
fakeroot
fatrat-git
file
file-roller
filesystem
findutils
firefox-nightly
flashplugin-prerelease
flex
fuseiso
gawk
gcc-libs
gconf-editor
gdm
gedit
geoip
gettext
gksu
glibc
gnome-applets
gnome-backgrounds
gnome-control-center
gnome-desktop
gnome-icon-theme
gnome-icon-theme-extras
gnome-icon-theme-symbolic
gnome-keyring
gnome-media
gnome-nettool
gnome-packagekit
gnome-panel
gnome-power-manager
gnome-screensaver
gnome-session
gnome-settings-daemon
gnome-settings-daemon-updates
gnome-shell
gnome-shell-extensions-common
gnome-shell-extension-user-theme
gnome-system-monitor
gnome-terminal
gnome-themes-standard
gnome-tweak-tool
gnome-user-docs
gnome-utils
gparted
grep
grub2-bios
grub-customizer
gstreamer0.10-bad
gstreamer0.10-bad-plugins
gstreamer0.10-good-plugins
gstreamer0.10-ugly-plugins
gtk
gtk-engine-murrine
gtkhotkey
gzip
hdparm
heirloom-mailx
hwdetect
initscripts
iputils
jfsutils
jre
less
libchunfeng
libpipeline
libzeitgeist
licenses
linux
log4cpp
logrotate
luaposix
lvm2
lzo
lzop
make
man-db
man-pages
mdadm
metacity
mindi-busybox
mousetweaks
mutter
nano
nautilus
nautilus-open-terminal
nautilus-p7zip
nautilus-sendto
networkmanager
network-manager-applet
networkmanager-dispatcher-ntpd
notification-daemon
numlockx
nvidia
os-prober
package-query
packer
pacman
pacman-color
patch
pciutils
pcmciautils
perl
pion-net
pkg-config
ppp
procps
psmisc
python
quilt
rdflib
readahead-fedora
reiserfsprogs
rsync
sed
shadow
steadyflow-bzr
sudo
synapse
sysfsutils
syslog-ng
systemd-arch-units
sysvinit
tar
telepathy-gabble
texinfo
transmission-gtk
ttf-ms-fonts
ttf-ubuntu-font-family
udev
ulatencyd-git
unrar
unzip
upx
usbutils
util-linux
vdpau-video
vi
vlc
vpack
wget
which
wpa_supplicant
xf86-input-evdev
xf86-input-keyboard
xf86-input-mouse
xf86-input-void
xf86-video-dummy
xf86-video-fbdev
xf86-video-nv
xf86-video-rendition
xf86-video-vesa
xf86-video-xgi
xf86-video-xgixp
xfsprogs
xorg-bdftopcf
xorg-docs
xorg-fonts-100dpi
xorg-fonts-75dpi
xorg-fonts-encodings
xorg-font-util
xorg-iceauth
xorg-luit
xorg-mkfontdir
xorg-mkfontscale
xorg-server
xorg-sessreg
xorg-setxkbmap
xorg-smproxy
xorg-x11perf
xorg-xauth
xorg-xbacklight
xorg-xcmsdb
xorg-xcursorgen
xorg-xdpyinfo
xorg-xdriinfo
xorg-xev
xorg-xgamma
xorg-xhost
xorg-xinit
xorg-xinput
xorg-xkbcomp
xorg-xkbevd
xorg-xkbutils
xorg-xkill
xorg-xlsatoms
xorg-xlsclients
xorg-xmodmap
xorg-xpr
xorg-xprop
xorg-xrandr
xorg-xrdb
xorg-xrefresh
xorg-xset
xorg-xsetroot
xorg-xvinfo
xorg-xwd
xorg-xwininfo
xorg-xwud
yaourt
yaourt-gui
yelp
zeitgeist
zeitgeist-userspace
zsync

```[https://wiki.archlinux.org/index.php/Pacman_Tips#Backing_up_and_retrieving_a_list_of_installed_packages](https://wiki.archlinux.org/index.php/Pacman_Tips#Backing_up_and_retrieving_a_list_of_installed_packages)

---

### Post by cbowman57 on 2011-08-25
**pacman -S xorg gdm** is pretty productive

Edited previous post.  I think it will make it practically automatic.

---

### Post by 23dornot23d on 2011-08-25
For some reason pacman is not working ..... yet ..... ?

error could not open file /var/lib/pacman/sync/extra.db 

community too .....

not sure why yet ,,,

---

### Post by cbowman57 on 2011-08-25
Did you already pacman -Syu ?

(Their version of Ubuntu apt-get update.)

---

### Post by 23dornot23d on 2011-08-25
[FONT=Book Antiqua]Its ok now [/FONT]- we are working ty :P

This is getting interesting ,,,, but will need to upgrade as I just installed the Archbang in ...

just run into dependency problems upgrading .....

[IMG]http://img839.imageshack.us/img839/3260/2011082513143252391360x.jpg[/IMG]

Looks like I need to upgrade this a lot ...... the other version is 3.0 .... but would not run pacman ...

I wonder if I can upgrade from the other CD now somehow ....

[IMG]http://img88.imageshack.us/img88/5186/2011082513143261711360x.jpg[/IMG]

This is so very new ...... but interesting too .... ;)

and a dependency nightmare .... guess its start again time ..... already .....

somehow I need to keep the config files from here to use in the new one ..... though ..... Arch .... 3.0

as this is not going to upgrade ..... ( lols ..... it upgraded ..... ;) _ )

[IMG]http://img820.imageshack.us/img820/4246/gnomeshellv.jpg[/IMG]

---

### Post by mips on 2011-08-26
I suspect your issues are related to using quite an old version of the Arch(bang) install media which can cause issues with pacman, depencies, kernel as significant changes has transpired over time.

As these issues arose they were posted on the front page of [http://www.archlinux.org/](http://www.archlinux.org/) with solutions & in the forum announcements I think. So my suggestion to you would be to go read up on those.

My recommendation to you would be to grab the latest Arch install media [http://www.archlinux.org/download/](http://www.archlinux.org/download/). Grab the netinstall Dual Architecture (can be used on both 32bit & 64bit systems) image and install from scratch. Things will be way smoother and you will end up with stuff only you want.

If you have any questions along the way just ask here and we will assist but keep the beginners guide handy (it's also on the install media) and look for solutions in the Arch forums. If you do this I doubt you will have many questions if any at all.

---

### Post by cbowman57 on 2011-08-26
Yeah, what mips said. :)

I have no idea what differences there are between Archbang & Archlinux, maybe they are significant.

Once you get past the basic installation nightmare though you might find this link useful:

[https://wiki.archlinux.org/index.php/GNOME](https://wiki.archlinux.org/index.php/GNOME)

This one is old but still some good stuff.

[https://wiki.archlinux.org/index.php/GNOME_Tips](https://wiki.archlinux.org/index.php/GNOME_Tips)

---

### Post by mips on 2011-08-26
> **cbowman57 said:**
> 
I have no idea what differences there are between Archbang & Archlinux, maybe they are significant.


None from what I recall, they build it on pure Arch with no special packages/repos. They just give you their default apps and make changes to config files if I'm not mistaken.

---

### Post by cbowman57 on 2011-08-26
I've installed Arch twice in the past week or so, one I did with the latest multi-arch core iso, the other with the net install, before the update on the 19th.

Haven't tried Archbang, I think I'm done distro-hopping for awhile.  I really like Arch & G-S.

I do have a strange thing going on though, no gnome fallback option in the gdm. I tried copying the GNOME.desktop and create a Gnome fallback but it failed to start.

---

### Post by 23dornot23d on 2011-08-26
Cheers for the information ....

The NET is still working and I have the Arch3-0 installed and
Gnome-shell .... 3.0.2 installed ....

Problem is the module does not load in at boot ..... comes up with 
a red fail ..... from what I am reading this may be to do with name changes .....

While I have a working system as such I will take it a little further , I quite like this install ...... and will see if I can understand why it did not fully upgrade ....

It does not seem that far away from complete now ..... but who knows ....

GIMP works
CHROMIUM BROWSER works (typing this from ARCH 3.0 now
NETWORK obviously working
PACMAN works ..... (but for some reason is only picking up the packages I have already downloaded ..... 

So my guess is - PACMAN links may not be working properly ...

How do I check this ... ?

Cheers for the help so far ..... ( see screenshot 3 .... the bottom one .... Gnome-Shell version 3.0.2 was loaded in at the stage just before I went to sleep last night. )

Will see what I can do today ..... guess a lot of reading is needed - but already this is interesting .....:)

I would like to know how to load Nvidia drivers too if its possible ...

If I break this beyond repair .... then I will do a full re-install of the one you mentioned in your post mips ....

> 
My recommendation to you would be to grab the latest Arch install media [http://www.archlinux.org/download/](http://www.archlinux.org/download/). Grab the netinstall Dual Architecture (can be used on both 32bit & 64bit systems) image and install from scratch. Things will be way smoother and you will end up with stuff only you want.


I have a copy of this waiting .....

How did you install the fallback ... Chuck .... 
So I can try it too ...
> 
I do have a strange thing going on though, no gnome fallback option in the gdm. I tried copying the GNOME.desktop and create a Gnome fallback but it failed to start.


I have installed gnome-shell and gdm upto just ..... plus the packages needed to get a working internet .... as this morning I did not have one ...

But I do now have Internet and a wired connection .... and usually if I have a connection to the Net .... most things for me become much easier to sort out .

Will keep trying and report here what happens ....

As I say the main thing is modules [COLOR="Red"]FAIL[/COLOR]

But the system appears to be working ...

---

### Post by cbowman57 on 2011-08-26
Nvidia drivers:  pacman -S nvidia

---

### Post by 23dornot23d on 2011-08-26
Cheers Chuck ..

Seems my internet connection for pacman is working ....

[IMG]http://img189.imageshack.us/img189/9467/2011082613143615901360x.jpg[/IMG]

Just installed gnome-tweak-tool and Inkscape .... plus Blender ...

[IMG]http://img43.imageshack.us/img43/8076/2011082613143619571360x.jpg[/IMG]

Will now try Nvidia .... ty

Nvidia .... lots of dependency problems .... opengl and lots of drivers to
remove .... but no doubt we need to do this .... sooner rather than later ...

Nouveau seem to be working quite well though .... will gnome-shell run with nouveau ok ?

---

### Post by cbowman57 on 2011-08-26
> Nouveau seem to be working quite well though .... will gnome-shell run with nouveau ok ?

No, not unless you have the experimental gl and I'm not sure Arch has that.  I had fallback mode until I installed Nvidia drivers.

You made a lot of progress over night.

---

### Post by 23dornot23d on 2011-08-26
I have fallback now ..... just 

Added gnome-panels also added kde too

to be honest this is looking good now other than getting Gnome shell - I am happy with the way it runs and the
speed is wicked ..... on this old machine 512 Meg ram ...

[IMG]http://img607.imageshack.us/img607/2238/snapshot1vt.jpg[/IMG]


Ok will leave the Nvidia for the time being ...... need to do some reading now ...... ty ...

I am pretty confident the shell has all it needs to run now ...... 

( just missing one thing I think ... the Nvidia graphics driver ..... I might try the same method I used for slackware )

and build them into the kernel using the Nvidia download .... if its similar to slackware .... it may work ....

If not guess its plan B ....

---

### Post by cbowman57 on 2011-08-26
Yeah, Arch runs great, and you probably haven't even begun to tweak it.  Those wiki's have a wealth of info.

---

### Post by 23dornot23d on 2011-08-26
I am finding that there is a wealth of info .... and once you get used to having to set things up manually - you realise its helping you to understand how the system really works.

I only now realise why so many people rave about Arch ..... 

Looking forward to a good session on this tonight ..... now ..... ;)

---

### Post by cbowman57 on 2011-08-26
Yeah, that's what I really like about it, learning and having a better understanding of linux.  I thought I knew my way around Ubuntu pretty well to suit my needs, even Debian over the last couple weeks, but this is like WOW!!  Setting up your daemons, trimming the fat, troubleshooting, it's an eye opener for sure.

I could have never gotten here without going through Ubuntu & the other distros first though.

One thing Ubuntu has over the others though is this forum.

---

### Post by 23dornot23d on 2011-08-26
Yep - just looking at the kernel source files now ....

[http://kernel.org/pub/linux/kernel/](http://kernel.org/pub/linux/kernel/)

Nvidia needs them and the headers to compile properly .....

not sure what else yet ...... if I do not return you will know I messed up big style .... :confused:

Just a quick re-install ..... see if there is something here I need like versions etc ....

```

[root@archbang keith]# pacman -S linux
warning: linux-3.0.3-1 is up to date -- reinstalling
resolving dependencies...
looking for inter-conflicts...

Targets (1): linux-3.0.3-1 [36.22 MB]

Total Download Size:    0.00 MB
Total Installed Size:   53.87 MB

Proceed with installation? [Y/n] y
(1/1) checking package integrity                   [----------------------] 100%
(1/1) checking for file conflicts                  [----------------------] 100%
(1/1) upgrading linux                              [----------------------] 100%
>>> Updating module dependencies. Please wait ...
>>> Generating initial ramdisk, using mkinitcpio.  Please wait...
==> Building image from preset: 'default'
  -> -k /boot/vmlinuz-linux -c /etc/mkinitcpio.conf -g /boot/initramfs-linux.img
==> Starting build: 3.0-ARCH
  -> Parsing hook: [base]
  -> Parsing hook: [udev]
  -> Parsing hook: [autodetect]
  -> Parsing hook: [pata]
  -> Parsing hook: [scsi]
  -> Parsing hook: [sata]
  -> Parsing hook: [filesystems]
  -> Parsing hook: [usbinput]
==> Generating module dependencies
==> Creating gzip initcpio image: /boot/initramfs-linux.img
7277 blocks
==> Image generation successful
==> Building image from preset: 'fallback'
  -> -k /boot/vmlinuz-linux -c /etc/mkinitcpio.conf -g /boot/initramfs-linux-fallback.img -S autodetect
==> Starting build: 3.0-ARCH
  -> Parsing hook: [base]
  -> Parsing hook: [udev]
  -> Parsing hook: [pata]
  -> Parsing hook: [scsi]
  -> Parsing hook: [sata]
  -> Parsing hook: [filesystems]
  -> Parsing hook: [usbinput]
==> Generating module dependencies
==> Creating gzip initcpio image: /boot/initramfs-linux-fallback.img
23389 blocks
==> Image generation successful
[root@archbang keith]# 


```When I run NVIDIAxxxx.run

its complaining it cannot find the headers or source ..... now why is that ....
as the kernel just built above .... what did it use ?


There are no files in /usr/source/?

---

### Post by cbowman57 on 2011-08-26
Pretty sure it pulled in whatever it needed when I installed them.  No surprises. :)

---

### Post by 23dornot23d on 2011-08-26
/usr/src/

```

[root@archbang usr]# ls
bin  features  include  lib  local  sbin  share  src
[root@archbang usr]# pacman -S nvidia
resolving dependencies...
looking for inter-conflicts...
:: nvidia-utils and libgl are in conflict. Remove libgl? [y/N] 
error: unresolvable package conflicts detected
error: failed to prepare transaction (conflicting dependencies)
:: nvidia-utils and libgl are in conflict
[root@archbang usr]# cd /usr/
[root@archbang usr]# ls
bin  features  include  lib  local  sbin  share  src
[root@archbang usr]# cd src
[root@archbang src]# ls
linux-3.0-ARCH
[root@archbang src]# 

root@archbang /]# ls
bin                  etc         media                        proc  srv  var
boot                 home        mnt                          root  sys
dev                  lib         NVIDIA-Linux-x86-280.13.run  run   tmp
disable-nouveau.old  lost+found  opt                          sbin  usr
[root@archbang /]# ./NVIDIA-Linux-x86-280.13.run
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86 280.13...............................................................................................................................
[root@archbang /]# 




```Will keep looking for more information ...... on this .......

I can disable nouveau just by adding this

Disabling the noveau driver involves creating a file **/etc/modprobe.d/disable-nouveau.conf** with the following lines:     Code:
     
blacklist nouveau 
options nouveau modeset=0 

This was the solution for Slackware ...... 


and to re-instate nouveau ...... I just delete that file from out of [B]here ....

/etc/modprobe.d/disable-nouveau.conf

That gives me my graphics back while I am figuring things out .....




 

[/B]

---

### Post by cbowman57 on 2011-08-26
Yes, remove libgl & whatever else it starts recommending.  When you go to remove libgl it will tell you that something else is dependent on it, so you have to remove that first, then a few more before you can finally get rid of libgl and proceed with the nvidia installation.

Despite some of the prompts & warnings I haven't run into a dependency problem yet.  Arch is a lot smarter than it appears on the surface, at least that's how it seems to me.

---

### Post by 23dornot23d on 2011-08-26
Do you have Gnome shell fully working on Arch now then ?

if so I will remove all the dependencies below this .... and install using pacman.



Here is a [[COLOR=Red]_***SCREENSHOT***_[/COLOR]]("http://img834.imageshack.us/img834/1283/1000sz.jpg") of what I get through using NVIDIAxxxx.run

---

### Post by cbowman57 on 2011-08-26
Sure do, have had one for about a week but I took a detour for a couple days getting it installed to Raid0, that was a little tricky but it is wickedly fast. :)

[ATTACH]200833[/ATTACH]

---

### Post by 23dornot23d on 2011-08-26
Ok that looks good ..... 

I will remove any dependencies that get in my way now ... ;)

also added the headers too - [[COLOR=Red]_***I like options ***_[/COLOR]]("http://img714.imageshack.us/img714/8026/snapshot3ol.jpg")...

```

[root@archbang keith]# pacman -S linux-headers
resolving dependencies...
looking for inter-conflicts...

Targets (1): linux-headers-3.0.3-1 [4.34 MB]

Total Download Size:    4.34 MB
Total Installed Size:   41.86 MB

Proceed with installation? [Y/n] y
:: Retrieving packages from core...
 linux-headers-3.0....     4.3M  991.8K/s 00:00:04 [----------------------] 100%
(1/1) checking package integrity                   [----------------------] 100%
(1/1) checking for file conflicts                  [----------------------] 100%
(1/1) installing linux-headers                     [----------------------] 100%
[root@archbang keith]# 


```

---

### Post by cbowman57 on 2011-08-26
Did you try that method with the list I put in post #5?  I executed it, but selected the y/N option to abort since I didn't want to break anything on this setup.  It looked like it was going to work as described.  I may have had to install the kernel source & headers too but I don't remember doing that. Pretty sure I just did the pacman -S nvidia thing and it installed without any problems.

---

### Post by 23dornot23d on 2011-08-26
I have not loaded your list in yet ...... but may do ....

I have got the Nvidia going .... just by adding the headers

and running NVIDIAxxxx.run

But I have no Gnome-Shell yet ..... so I must be missing more files

therefore going through your list may solve this now ....... ty  

[IMG]http://img809.imageshack.us/img809/662/snapshot4t.jpg[/IMG]

---

### Post by cbowman57 on 2011-08-26
You have to be awfully close since you're already in fallback mode.

Did you run exec ck-launch-session gnome-session from the terminal?  Not sure if that's necessary but I've got it in my notes.

Also have the installation of mesa in my must have column.  I dunno. :)

Wish I could offer more help, most of my notes consist of things I had to do to get Raid running.

---

### Post by 23dornot23d on 2011-08-26
Using that command I get this 

[[COLOR=Red]_**SCREENSHOT -Fullsize**_[/COLOR]]("http://img233.imageshack.us/img233/7229/snapshot5l.jpg")

I am wondering - do you have another repository or something setup where you are getting later files.....

as some of the packages in your list are not being found ......

like 
gnome-extensions-common
gnome-extensions-user-themes

or did you add the seperately from a rpm or something else ?

---

### Post by cbowman57 on 2011-08-26
I've got community, community-testing, core, extra & testing active.  I think the extensions are in [extra].  You probably already have, but I'll ask anyway. Do you have dbus installed, & is it running?

From the command line I think you can start it up with /etc/rc.d start dbus

---

### Post by satanselbow on 2011-08-26
> **23dornot23d said:**
> Using that command I get this 

[[COLOR=Red]_**SCREENSHOT -Fullsize**_[/COLOR]]("http://img233.imageshack.us/img233/7229/snapshot5l.jpg")

I am wondering - do you have another repository or something setup where you are getting later files.....

as some of the packages in your list are not being found ......

like 
gnome-extensions-common
gnome-extensions-user-themes

or did you add the seperately from a rpm or something else ?

Hi fellas - glad to see you are experimenting with the arch-side :D

The gnome-shell-extensions can all be found in the AUR which cannot directly be downloaded with pacman :(

You can however download YAOURT which is a pacman wrapper and facilitates access to the goodies AUR provides ;)

YAOURT itself has one dependecy in the AUR "package-query" which should be installed by downloading the tarball from AUR, extract and swap into it's folder then:

```

makepkg -s
makepkg -i

```

Do the same for yaourt and then you can just install pkgs from the AUR with yaourt -S <pkgname>

Enjoy ;)

See you on the Arch forums? 

Gnome 3 purrs like a kitten on Arch BTW - not played with ArchBang myself :guitar:

Edit:

The only daemons you need running in /etc/rc/conf for G3 are:

```

DAEMONS=(hwclock @syslog-ng @network @netfs @crond dbus @networkmanager gdm)

```

gdm MUST be at the end of the list ;)

---

### Post by cbowman57 on 2011-08-26
I just combine it into makepkg -si, I tried yaourt but went with packer primarily.

Still exploring, I forgot the extensions were in AUR.  I've covered a lot of ground the past week or so, as did Keith with Slackex. :)

---

### Post by sanderd17 on 2011-08-26
> **23dornot23d said:**
> 

or did you add the seperately from a rpm or something else ?

You never need to install something from rpm. If it's not in the AUR already, it should be added to it, and everyone can do it.

---

### Post by 23dornot23d on 2011-08-26
Ok great to see all the responses ....

just been out doing my shopping and having my tea and now work to do ......

:)

First one ...... cheers Chuck yep dbus is up and running ..... checked HTOP .....

[COLOR=Red][B]Is there a easy way to quicly check which repositories are active ..... ?

just checked in /var/lib/pacman/sync

I have .....

community
core
extra

[COLOR=Black]So ..... need these 2 too ...

[/COLOR][/B][/COLOR]community-testing
testing active

> 
I've got community, community-testing, core, extra & testing active.   I think the extensions are in [extra].  You probably already have, but  I'll ask anyway. Do you have dbus installed, & is it running?

Second cheers Statanselbow

```

[keith@archbang ~]$ cd package-query
[keith@archbang package-query]$ ls
PKGBUILD  yaourt  yaourt.tar.gz
[keith@archbang package-query]$ makepkg -si
==> Making package: package-query 0.8.1-1 (Fri Aug 26 13:47:17 EDT 2011)
==> Checking runtime dependencies...
==> Installing missing dependencies...
Password: 
resolving dependencies...
looking for inter-conflicts...

Targets (1): yajl-2.0.2-1 [0.03 MB]

Total Download Size:    0.03 MB
Total Installed Size:   0.21 MB

Proceed with installation? [Y/n] y
:: Retrieving packages from community...
 yajl-2.0.2-1-i686        35.8K  122.6K/s 00:00:00 [----------------------] 100%
(1/1) checking package integrity                   [----------------------] 100%
(1/1) checking for file conflicts                  [----------------------] 100%
(1/1) installing yajl                              [----------------------] 100%
==> Checking buildtime dependencies...
==> Retrieving Sources...
  -> Downloading package-query-0.8.1.tar.gz...
--2011-08-26 13:47:29--  http://mir.archlinux.fr/~tuxce/releases/package-query/package-query-0.8.1.tar.gz
Resolving mir.archlinux.fr... 213.186.62.207
Connecting to mir.archlinux.fr|213.186.62.207|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 331159 (323K) [application/x-gzip]
Saving to: `package-query-0.8.1.tar.gz.part'

100%[======================================>] 331,159      161K/s   in 2.0s    

2011-08-26 13:47:52 (161 KB/s) - `package-query-0.8.1.tar.gz.part' saved [331159/331159]

==> Validating source files with md5sums...
    package-query-0.8.1.tar.gz ... Passed
==> Extracting Sources...
  -> Extracting package-query-0.8.1.tar.gz with bsdtar
==> Starting build()...
checking for a BSD-compatible install... /bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert i686-pc-linux-gnu file names to i686-pc-linux-gnu format... func_convert_file_noop
checking how to convert i686-pc-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... no
checking if : is a manifest tool... no
checking how to run the C preprocessor... gcc -E
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking ctype.h usability... yes
checking ctype.h presence... yes
checking for ctype.h... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/utsname.h usability... yes
checking sys/utsname.h presence... yes
checking for sys/utsname.h... yes
checking for alpm_version in -lalpm... yes
checking for yajl_free in -lyajl... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LIBCURL... yes
checking for git... git
checking for .git/... no
configure: creating ./config.status
config.status: creating src/Makefile
config.status: creating doc/Makefile
config.status: creating Makefile
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing libtool commands

package-query:

  Build information:
    source code location   : .
    prefix                 : /usr
    sysconfdir             : /etc
       conf file           : /etc/pacman.conf
    localstatedir          : /var
       database dir        : /var/lib/pacman/
    compiler               : gcc
    compiler flags         : -march=i686 -mtune=generic -O2 -pipe -fstack-protector --param=ssp-buffer-size=4 -D_FORTIFY_SOURCE=2

    package-query version  : 0.8.1
    using git version      : no
       git ver             : 

  Variable information:
    root working directory : /
    aur base url           : http://aur.archlinux.org

make  all-recursive
make[1]: Entering directory `/home/keith/package-query/src/package-query-0.8.1'
Making all in src
make[2]: Entering directory `/home/keith/package-query/src/package-query-0.8.1/src'
gcc -DLOCALEDIR=\"/usr/share/locale\" -DCONFFILE=\"/etc/pacman.conf\" -DROOTDIR=\"/\" -DDBPATH=\"/var/lib/pacman/\" -DAUR_BASE_URL=\"http://aur.archlinux.org\" -DHAVE_CONFIG_H  -I. -I..     -D_GNU_SOURCE -march=i686 -mtune=generic -O2 -pipe -fstack-protector --param=ssp-buffer-size=4 -D_FORTIFY_SOURCE=2 -MT aur.o -MD -MP -MF .deps/aur.Tpo -c -o aur.o aur.c
mv -f .deps/aur.Tpo .deps/aur.Po
gcc -DLOCALEDIR=\"/usr/share/locale\" -DCONFFILE=\"/etc/pacman.conf\" -DROOTDIR=\"/\" -DDBPATH=\"/var/lib/pacman/\" -DAUR_BASE_URL=\"http://aur.archlinux.org\" -DHAVE_CONFIG_H  -I. -I..     -D_GNU_SOURCE -march=i686 -mtune=generic -O2 -pipe -fstack-protector --param=ssp-buffer-size=4 -D_FORTIFY_SOURCE=2 -MT alpm-query.o -MD -MP -MF .deps/alpm-query.Tpo -c -o alpm-query.o alpm-query.c
alpm-query.c: In function &#8216;alpm_pkg_get_realsize&#8217;:
alpm-query.c:499:10: warning: ignoring return value of &#8216;chdir&#8217;, declared with attribute warn_unused_result [-Wunused-result]
alpm-query.c:501:10: warning: ignoring return value of &#8216;chdir&#8217;, declared with attribute warn_unused_result [-Wunused-result]
mv -f .deps/alpm-query.Tpo .deps/alpm-query.Po
gcc -DLOCALEDIR=\"/usr/share/locale\" -DCONFFILE=\"/etc/pacman.conf\" -DROOTDIR=\"/\" -DDBPATH=\"/var/lib/pacman/\" -DAUR_BASE_URL=\"http://aur.archlinux.org\" -DHAVE_CONFIG_H  -I. -I..     -D_GNU_SOURCE -march=i686 -mtune=generic -O2 -pipe -fstack-protector --param=ssp-buffer-size=4 -D_FORTIFY_SOURCE=2 -MT util.o -MD -MP -MF .deps/util.Tpo -c -o util.o util.c
util.c: In function &#8216;ltostr&#8217;:
util.c:453:11: warning: ignoring return value of &#8216;asprintf&#8217;, declared with attribute warn_unused_result [-Wunused-result]
util.c: In function &#8216;itostr&#8217;:
util.c:446:11: warning: ignoring return value of &#8216;asprintf&#8217;, declared with attribute warn_unused_result [-Wunused-result]
util.c: In function &#8216;string_fcat&#8217;:
util.c:328:11: warning: ignoring return value of &#8216;vasprintf&#8217;, declared with attribute warn_unused_result [-Wunused-result]
mv -f .deps/util.Tpo .deps/util.Po
gcc -DLOCALEDIR=\"/usr/share/locale\" -DCONFFILE=\"/etc/pacman.conf\" -DROOTDIR=\"/\" -DDBPATH=\"/var/lib/pacman/\" -DAUR_BASE_URL=\"http://aur.archlinux.org\" -DHAVE_CONFIG_H  -I. -I..     -D_GNU_SOURCE -march=i686 -mtune=generic -O2 -pipe -fstack-protector --param=ssp-buffer-size=4 -D_FORTIFY_SOURCE=2 -MT color.o -MD -MP -MF .deps/color.Tpo -c -o color.o color.c
mv -f .deps/color.Tpo .deps/color.Po
gcc -DLOCALEDIR=\"/usr/share/locale\" -DCONFFILE=\"/etc/pacman.conf\" -DROOTDIR=\"/\" -DDBPATH=\"/var/lib/pacman/\" -DAUR_BASE_URL=\"http://aur.archlinux.org\" -DHAVE_CONFIG_H  -I. -I..     -D_GNU_SOURCE -march=i686 -mtune=generic -O2 -pipe -fstack-protector --param=ssp-buffer-size=4 -D_FORTIFY_SOURCE=2 -MT package-query.o -MD -MP -MF .deps/package-query.Tpo -c -o package-query.o package-query.c
mv -f .deps/package-query.Tpo .deps/package-query.Po
/bin/sh ../libtool --tag=CC   --mode=link gcc  -D_GNU_SOURCE -march=i686 -mtune=generic -O2 -pipe -fstack-protector --param=ssp-buffer-size=4 -D_FORTIFY_SOURCE=2 -lcurl   -Wl,-O1,--sort-common,--as-needed,-z,relro,--hash-style=gnu -o package-query aur.o alpm-query.o util.o color.o package-query.o  -lyajl -lalpm 
libtool: link: gcc -D_GNU_SOURCE -march=i686 -mtune=generic -O2 -pipe -fstack-protector --param=ssp-buffer-size=4 -D_FORTIFY_SOURCE=2 -Wl,-O1 -Wl,--sort-common -Wl,--as-needed -Wl,-z -Wl,relro -Wl,--hash-style=gnu -o package-query aur.o alpm-query.o util.o color.o package-query.o  -lcurl -lyajl -lalpm
make[2]: Leaving directory `/home/keith/package-query/src/package-query-0.8.1/src'
Making all in doc
make[2]: Entering directory `/home/keith/package-query/src/package-query-0.8.1/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/keith/package-query/src/package-query-0.8.1/doc'
make[2]: Entering directory `/home/keith/package-query/src/package-query-0.8.1'
make[2]: Leaving directory `/home/keith/package-query/src/package-query-0.8.1'
make[1]: Leaving directory `/home/keith/package-query/src/package-query-0.8.1'
==> Entering fakeroot environment...
==> Starting package()...
Making install in src
make[1]: Entering directory `/home/keith/package-query/src/package-query-0.8.1/src'
make[2]: Entering directory `/home/keith/package-query/src/package-query-0.8.1/src'
test -z "/usr/bin" || /bin/mkdir -p "/home/keith/package-query/pkg/usr/bin"
  /bin/sh ../libtool   --mode=install /bin/install -c package-query '/home/keith/package-query/pkg/usr/bin'
libtool: install: /bin/install -c package-query /home/keith/package-query/pkg/usr/bin/package-query
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/keith/package-query/src/package-query-0.8.1/src'
make[1]: Leaving directory `/home/keith/package-query/src/package-query-0.8.1/src'
Making install in doc
make[1]: Entering directory `/home/keith/package-query/src/package-query-0.8.1/doc'
make[2]: Entering directory `/home/keith/package-query/src/package-query-0.8.1/doc'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/man/man8" || /bin/mkdir -p "/home/keith/package-query/pkg/usr/share/man/man8"
 /bin/install -c -m 644 package-query.8 '/home/keith/package-query/pkg/usr/share/man/man8'
make[2]: Leaving directory `/home/keith/package-query/src/package-query-0.8.1/doc'
make[1]: Leaving directory `/home/keith/package-query/src/package-query-0.8.1/doc'
make[1]: Entering directory `/home/keith/package-query/src/package-query-0.8.1'
make[2]: Entering directory `/home/keith/package-query/src/package-query-0.8.1'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/keith/package-query/src/package-query-0.8.1'
make[1]: Leaving directory `/home/keith/package-query/src/package-query-0.8.1'
==> Tidying install...
  -> Purging other files...
  -> Compressing man and info pages...
  -> Stripping unneeded symbols from binaries and libraries...
==> Creating package...
  -> Generating .PKGINFO file...
  -> Compressing package...
==> Leaving fakeroot environment.
==> Finished making: package-query 0.8.1-1 (Fri Aug 26 13:48:06 EDT 2011)
==> Installing package package-query with pacman -U...
resolving dependencies...
looking for inter-conflicts...

Targets (1): package-query-0.8.1-1 [0.02 MB]

Total Download Size:    0.00 MB
Total Installed Size:   0.07 MB

Proceed with installation? [Y/n] y
(1/1) checking package integrity                   [----------------------] 100%
(1/1) checking for file conflicts                  [----------------------] 100%
(1/1) installing package-query                     [----------------------] 100%
[keith@archbang package-query]$ cd yaourt
[keith@archbang yaourt]$ ls
PKGBUILD
[keith@archbang yaourt]$ makepkg -si
==> Making package: yaourt 0.10.1-2 (Fri Aug 26 13:48:29 EDT 2011)
==> Checking runtime dependencies...
==> Checking buildtime dependencies...
==> Retrieving Sources...
  -> Downloading yaourt-0.10.1.tar.gz...
--2011-08-26 13:48:29--  http://mir.archlinux.fr/~tuxce/releases/yaourt/yaourt-0.10.1.tar.gz
Resolving mir.archlinux.fr... 213.186.62.207
Connecting to mir.archlinux.fr|213.186.62.207|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 52450 (51K) [application/x-gzip]
Saving to: `yaourt-0.10.1.tar.gz.part'

100%[======================================>] 52,450       271K/s   in 0.2s    

2011-08-26 13:48:31 (271 KB/s) - `yaourt-0.10.1.tar.gz.part' saved [52450/52450]

==> Validating source files with md5sums...
    yaourt-0.10.1.tar.gz ... Passed
==> Extracting Sources...
  -> Extracting yaourt-0.10.1.tar.gz with bsdtar
==> Starting build()...
    GEN yaourt.sh
    GEN pacdiffviewer.sh
    GEN lib/util.sh
    GEN lib/pkgbuild.sh
    GEN lib/pacman.sh
==> Entering fakeroot environment...
==> Starting package()...
/bin/install  -d /home/keith/package-query/yaourt/pkg/usr/bin
/bin/install  -d /home/keith/package-query/yaourt/pkg/usr/lib/yaourt
/bin/install  -d /home/keith/package-query/yaourt/pkg/etc
/bin/install  -d /home/keith/package-query/yaourt/pkg/etc/bash_completion.d
/bin/install  -d /home/keith/package-query/yaourt/pkg/usr/share/man/man{5,8}
# Scripts
/bin/install  -m755 yaourt.sh /home/keith/package-query/yaourt/pkg/usr/bin/yaourt
/bin/install  -m755 pacdiffviewer.sh /home/keith/package-query/yaourt/pkg/usr/bin/pacdiffviewer
# Configuration
/bin/install  -m644 yaourtrc /home/keith/package-query/yaourt/pkg/etc/yaourtrc
/bin/install  -m644 bashcompletion /home/keith/package-query/yaourt/pkg/etc/bash_completion.d/yaourt
# Libs
/bin/install  -m644 lib/alpm_backup.sh /home/keith/package-query/yaourt/pkg/usr/lib/yaourt
/bin/install  -m644 lib/alpm_query.sh /home/keith/package-query/yaourt/pkg/usr/lib/yaourt
/bin/install  -m644 lib/alpm_stats.sh /home/keith/package-query/yaourt/pkg/usr/lib/yaourt
/bin/install  -m644 lib/abs.sh /home/keith/package-query/yaourt/pkg/usr/lib/yaourt
/bin/install  -m644 lib/aur.sh /home/keith/package-query/yaourt/pkg/usr/lib/yaourt
/bin/install  -m644 lib/util.sh /home/keith/package-query/yaourt/pkg/usr/lib/yaourt
/bin/install  -m644 lib/io.sh /home/keith/package-query/yaourt/pkg/usr/lib/yaourt
/bin/install  -m644 lib/pacman.sh /home/keith/package-query/yaourt/pkg/usr/lib/yaourt
/bin/install  -m644 lib/pkgbuild.sh /home/keith/package-query/yaourt/pkg/usr/lib/yaourt
# Man
/bin/install  -m644 man/*.5 /home/keith/package-query/yaourt/pkg/usr/share/man/man5
/bin/install  -m644 man/*.8 /home/keith/package-query/yaourt/pkg/usr/share/man/man8
# Locales
test -x /usr/bin/msgfmt && for file in po/*/*.po; \
do \
  package=$(echo $file | /bin/sed -e 's#po/\([^/]\+\).*#\1#'); \
  lang=$(echo $file | /bin/sed -e 's#.*/\([^/]\+\).po#\1#'); \
  /bin/install  -d /home/keith/package-query/yaourt/pkg/usr/share/locale/$lang/LC_MESSAGES; \
  /usr/bin/msgfmt -o /home/keith/package-query/yaourt/pkg/usr/share/locale/$lang/LC_MESSAGES/$package.mo $file; \
done
==> Tidying install...
  -> Purging other files...
  -> Compressing man and info pages...
  -> Stripping unneeded symbols from binaries and libraries...
==> Creating package...
  -> Generating .PKGINFO file...
  -> Compressing package...
==> Leaving fakeroot environment.
==> Finished making: yaourt 0.10.1-2 (Fri Aug 26 13:48:33 EDT 2011)
==> Installing package yaourt with pacman -U...
resolving dependencies...
looking for inter-conflicts...

Targets (1): yaourt-0.10.1-2 [0.04 MB]

Total Download Size:    0.00 MB
Total Installed Size:   0.22 MB

Proceed with installation? [Y/n] y
(1/1) checking package integrity                   [----------------------] 100%
(1/1) checking for file conflicts                  [----------------------] 100%
(1/1) installing yaourt                            [----------------------] 100%
Optional dependencies for yaourt
    aurvote: vote for favorite packages from AUR for inclusion in [community]
    customizepkg: automatically modify PKGBUILD during install/upgrade
    rsync: retrieve PKGBUILD from official repositories
    pacman-color: fully colorized output
[keith@archbang yaourt]$ 


```used this to get everything working ..... as AUR did not seem to pick up first time....

[http://archlinux.fr/yaourt](http://archlinux.fr/yaourt)

> 
Still exploring, I forgot the extensions were in AUR.  I've covered a  lot of ground the past week or so, as did Keith with Slackex. :smile:
Yep I think this last two weeks has been the best for learning things .... just hope I can remember some of it


Do not know what it is doing now .... asked it to upgrade using yaourt .... 
and it seems to be re-compiling the kernel adding 

linux-aufs_friendly

Oh well ..... could take all night on this machine ....

Just hope it still works at the end of this ......

> 
You never need to install something from rpm. If it's not in the AUR already, it should be added to it, and everyone can do it.
Cheers have just been looking at [COLOR=Red][U][I][AUR]("http://aur.archlinux.org/")

[B][maybe what I have done was not so wise ...]("http://img405.imageshack.us/img405/6981/snapshot10y.jpg")

still going .... do not know what will happen here if I kill it .......

do not want to mess the package manager up ....
[/B] [/I][/U][/COLOR]

---

### Post by cbowman57 on 2011-08-26
It seems to turn into a blur, but for some strange reason it all seems to make sense after a bit. 

Hope it's still running when you come back to it.

---

### Post by 23dornot23d on 2011-08-26
ITs Finished now and I have a choice ......

it took over two hours doing the file ..... now do I dump it or use it ?

[[COLOR=Red]_***SCREENSHOT***_[/COLOR]]("http://img594.imageshack.us/img594/9499/snapshot13w.jpg")

Not exactly sure what I stand to gain here ..... but it has been compiled for my system now.

Will try it ..... can always re-install everything again should it fail .....

---

### Post by cbowman57 on 2011-08-26
I'd say you have to use it. :)

But I break things on occasion.

---

### Post by 23dornot23d on 2011-08-26
Yep I do too ,,,, will continue ... no point in stopping now .....

Still need to get the Shell working ....

Well re-booted and its still running ..... but no shell yet ...... well no rush 

It took a week in Slackware , so anything better than that is good for me ;)


what I need to know now is how to get the missing packages ....

I will continue on your list

But am going through it one by one .... to see what is and is not available for me ....

will mark them as I go through them .....

---

### Post by cbowman57 on 2011-08-26
I have absolutely no doubt that you can get it done.

If you can get Gnome shell running on Slack you can do anything. :lol:

---

### Post by 23dornot23d on 2011-08-26
:lolflag: Someone else did Slackex not me ...... it was already done ....

Here is a screen shot of what we have here .....

I need the other repos adding ..... how do you do that on here now ....

[[COLOR=Red]_***SCREENSHOT OF YOUR LIST ***_[/COLOR]]("http://img836.imageshack.us/img836/4417/snapshot14u.jpg")as I go through it ..... a few are missing still

It could take a long time ..... this way ......

Could do it automatically from the list ..... I just do not get to know what happened that
way though .....

My package List so far ..... too

```

abiword
accountsservice
alsa-firmware
alsa-oss
alsa-utils
arandr
arch-firefox-search
at-spi2-atk
aufs2-util
autoconf
automake
bash
bash-completion
binutils
bison
blender
brasero
bridge-utils
bzip2
catfish
chromium
clementine
compiz-core
compiz-decorator-gtk
compiz-decorator-kde
conky
coreutils
cpio
cronie
cryptsetup
dash
dbus-core
device-mapper
dhclient
dhcpcd
dia
dialog
diffutils
dmenu
dnsutils
dosfstools
e2fsprogs
empathy
eog
epiphany
erlang
evolution
fakeroot
file
file-roller
filesystem
findutils
firefox
flashplugin-prerelease
flex
foxitreader
freemind
fuse
gawk
gcalctool
gcc
gcc-libs
gdm
gedit
geeqie
gettext
gimp
gksu
glibc
gmrun
gnome-common
gnome-disk-utility
gnome-menus
gnome-mplayer
gnome-packagekit
gnome-panel
gnome-power-manager
gnome-screensaver
gnome-settings-daemon-updates
gnome-shell
gnome-system-monitor
gnome-terminal
gnome-themes-standard
gnome-tweak-tool
gnome-user-docs
gnome-utils
gnumeric
gpart
gparted
grep
grub
gsettings-desktop-schemas
gsimplecal
gstreamer0.10-bad
gstreamer0.10-bad-plugins
gstreamer0.10-base
gstreamer0.10-base-plugins
gstreamer0.10-ffmpeg
gstreamer0.10-good
gstreamer0.10-good-plugins
gstreamer0.10-ugly
gstreamer0.10-ugly-plugins
gtk2-theme-neutronium
gvfs
gzip
hal
hardinfo
heirloom-mailx
hicolor-icon-theme
htop
ifplugd
initscripts
inkscape
iputils
iso-codes
jfsutils
kdeaccessibility-jovie
kdeaccessibility-kaccessible
kdeaccessibility-kmag
kdeaccessibility-kmousetool
kdeaccessibility-kmouth
kdeadmin-kcron
kdeadmin-ksystemlog
kdeadmin-kuser
kdeadmin-system-config-printer-kde
kdeartwork-aurorae
kdeartwork-colorschemes
kdeartwork-desktopthemes
kdeartwork-emoticons
kdeartwork-iconthemes
kdeartwork-kscreensaver
kdeartwork-sounds
kdeartwork-styles
kdeartwork-wallpapers
kdeartwork-weatherwallpapers
kdebase-dolphin
kdebase-kdepasswd
kdebase-kdialog
kdebase-keditbookmarks
kdebase-kfind
kdebase-konq-plugins
kdebase-konqueror
kdebase-konsole
kdebase-kwrite
kdebase-plasma
kdeedu-blinken
kdeedu-cantor
kdeedu-kalgebra
kdeedu-kalzium
kdeedu-kanagram
kdeedu-kbruch
kdeedu-kgeography
kdeedu-khangman
kdeedu-kig
kdeedu-kiten
kdeedu-klettres
kdeedu-kmplot
kdeedu-kstars
kdeedu-ktouch
kdeedu-kturtle
kdeedu-kwordquiz
kdeedu-marble
kdeedu-parley
kdeedu-rocs
kdeedu-step
kdegames-bomber
kdegames-bovo
kdegames-granatier
kdegames-kajongg
kdegames-kapman
kdegames-katomic
kdegames-kbattleship
kdegames-kblackbox
kdegames-kblocks
kdegames-kbounce
kdegames-kbreakout
kdegames-kdiamond
kdegames-kfourinline
kdegames-kgoldrunner
kdegames-kigo
kdegames-killbots
kdegames-kiriki
kdegames-kjumpingcube
kdegames-klickety
kdegames-klines
kdegames-kmahjongg
kdegames-kmines
kdegames-knetwalk
kdegames-kolf
kdegames-kollision
kdegames-konquest
kdegames-kpatience
kdegames-kreversi
kdegames-kshisen
kdegames-ksirk
kdegames-kspaceduel
kdegames-ksquares
kdegames-ksudoku
kdegames-ktron
kdegames-ktuberling
kdegames-kubrick
kdegames-lskat
kdegames-palapeli
kdegraphics-gwenview
kdegraphics-kamera
kdegraphics-kcolorchooser
kdegraphics-kgamma
kdegraphics-kolourpaint
kdegraphics-kruler
kdegraphics-ksnapshot
kdegraphics-okular
kdemultimedia-dragonplayer
kdemultimedia-ffmpegthumbs
kdemultimedia-juk
kdemultimedia-kioslave
kdemultimedia-kmix
kdemultimedia-kscd
kdemultimedia-mplayerthumbs
kdenetwork-filesharing
kdenetwork-kdnssd
kdenetwork-kget
kdenetwork-kopete
kdenetwork-kppp
kdenetwork-krdc
kdenetwork-krfb
kdepim-akonadiconsole
kdepim-akregator
kdepim-blogilo
kdepim-console
kdepim-kaddressbook
kdepim-kalarm
kdepim-kjots
kdepim-kleopatra
kdepim-kmail
kdepim-knode
kdepim-knotes
kdepim-kontact
kdepim-korganizer
kdepim-kresources
kdepim-ktimetracker
kdepim-wizards
kdeplasma-addons-applets-bball
kdeplasma-addons-applets-binary-clock
kdeplasma-addons-applets-blackboard
kdeplasma-addons-applets-bookmarks
kdeplasma-addons-applets-bubblemon
kdeplasma-addons-applets-calculator
kdeplasma-addons-applets-charselect
kdeplasma-addons-applets-comic
kdeplasma-addons-applets-community
kdeplasma-addons-applets-dict
kdeplasma-addons-applets-eyes
kdeplasma-addons-applets-fifteenpuzzle
kdeplasma-addons-applets-filewatcher
kdeplasma-addons-applets-frame
kdeplasma-addons-applets-fuzzy-clock
kdeplasma-addons-applets-incomingmsg
kdeplasma-addons-applets-kdeobservatory
kdeplasma-addons-applets-kimpanel
kdeplasma-addons-applets-knowledgebase
kdeplasma-addons-applets-kolourpicker
kdeplasma-addons-applets-konqprofiles
kdeplasma-addons-applets-konsoleprofiles
kdeplasma-addons-applets-lancelot
kdeplasma-addons-applets-leavenote
kdeplasma-addons-applets-life
kdeplasma-addons-applets-luna
kdeplasma-addons-applets-magnifique
kdeplasma-addons-applets-mediaplayer
kdeplasma-addons-applets-microblog
kdeplasma-addons-applets-news
kdeplasma-addons-applets-notes
kdeplasma-addons-applets-nowplaying
kdeplasma-addons-applets-paste
kdeplasma-addons-applets-pastebin
kdeplasma-addons-applets-plasmaboard
kdeplasma-addons-applets-previewer
kdeplasma-addons-applets-qalculate
kdeplasma-addons-applets-rememberthemilk
kdeplasma-addons-applets-rssnow
kdeplasma-addons-applets-showdashboard
kdeplasma-addons-applets-showdesktop
kdeplasma-addons-applets-social-news
kdeplasma-addons-applets-spellcheck
kdeplasma-addons-applets-systemloadviewer
kdeplasma-addons-applets-timer
kdeplasma-addons-applets-unitconverter
kdeplasma-addons-applets-weather
kdeplasma-addons-applets-weatherstation
kdeplasma-addons-applets-webslice
kdeplasma-addons-containments
kdeplasma-addons-runners-audioplayercontrol
kdeplasma-addons-runners-browserhistory
kdeplasma-addons-runners-characters
kdeplasma-addons-runners-contacts
kdeplasma-addons-runners-converter
kdeplasma-addons-runners-datetime
kdeplasma-addons-runners-events
kdeplasma-addons-runners-katesessions
kdeplasma-addons-runners-konquerorsessions
kdeplasma-addons-runners-konsolesessions
kdeplasma-addons-runners-kopete
kdeplasma-addons-runners-mediawiki
kdeplasma-addons-runners-spellchecker
kdeplasma-addons-wallpapers-mandelbrot
kdeplasma-addons-wallpapers-marble
kdeplasma-addons-wallpapers-pattern
kdeplasma-addons-wallpapers-virus
kdeplasma-addons-wallpapers-weather
kdesdk-cervisia
kdesdk-dolphin-plugins
kdesdk-kapptemplate
kdesdk-kate
kdesdk-kcachegrind
kdesdk-kdeaccounts-plugin
kdesdk-kdepalettes
kdesdk-kioslave
kdesdk-kmtrace
kdesdk-kompare
kdesdk-kpartloader
kdesdk-kprofilemethod
kdesdk-kstartperf
kdesdk-kuiviewer
kdesdk-lokalize
kdesdk-okteta
kdesdk-poxml
kdesdk-scripts
kdesdk-strigi-analyzer
kdesdk-umbrello
kdetoys-amor
kdetoys-kteatime
kdetoys-ktux
kdeutils-ark
kdeutils-filelight
kdeutils-kcalc
kdeutils-kcharselect
kdeutils-kdf
kdeutils-kfloppy
kdeutils-kgpg
kdeutils-kremotecontrol
kdeutils-ktimer
kdeutils-kwallet
kdeutils-printer-applet
kdeutils-superkaramba
kdeutils-sweeper
kde-wallpapers
kdewebdev-kfilereplace
kdewebdev-kimagemapeditor
kdewebdev-klinkstatus
kdewebdev-kommander
leafpad
less
libcanberra
libcanberra-gstreamer
libcanberra-pulse
libgl
libtool
licenses
linux
linux-headers
logrotate
lvm2
lxappearance
lxdm
lxinput
lxterminal
m4
make
man-db
man-pages
mdadm
memtest86+
mesa
nano
netcfg
net-tools
nitrogen
notification-daemon
nouveau-dri
nouveau-firmware
ntfs-3g
ntfsprogs
obconf
obkey-git
oblogout
obmenu
openbox
openbox-themes
p7zip
package-query
packer
pacman
parcellite
patch
pciutils
pcmciautils
perl
pkg-config
ppp
procps
psmisc
pstoedit
python
reiserfsprogs
rp-pppoe
rsync
scrot
sed
shadow
simplygrey-icon-theme
slim
squashfs-tools
streamtuner
sudo
sysfsutils
syslinux
syslog-ng
sysvinit
tango-icon-theme
tar
tcp_wrappers
texinfo
texlive-core
thunar
thunar-archive-plugin
thunar-media-tags-plugin
tint2
tintwizard
transmission-gtk
ttf-ms-fonts
tumbler
udev
unrar
unzip
upower
usbutils
util-linux
vattery
vi
volumeicon
vym
wget
which
wicd
wireless_tools
wpa_supplicant
xaos
xcompmgr
xf86-input-evdev
xf86-input-synaptics
xf86-video-apm
xf86-video-ark
xf86-video-ast
xf86-video-ati
xf86-video-chips
xf86-video-cirrus
xf86-video-dummy
xf86-video-fbdev
xf86-video-geode
xf86-video-glint
xf86-video-i128
xf86-video-i740
xf86-video-intel
xf86-video-mach64
xf86-video-mga
xf86-video-neomagic
xf86-video-nouveau
xf86-video-nv
xf86-video-r128
xf86-video-rendition
xf86-video-s3
xf86-video-s3virge
xf86-video-savage
xf86-video-siliconmotion
xf86-video-sis
xf86-video-sisusb
xf86-video-tdfx
xf86-video-trident
xf86-video-tseng
xf86-video-v4l
xf86-video-vesa
xf86-video-vmware
xf86-video-voodoo
xf86-video-xgi
xf86-video-xgixp
xfburn
xfsprogs
xorg-docs
xorg-fonts-100dpi
xorg-fonts-75dpi
xorg-res-utils
xorg-server
xorg-server-utils
xorg-twm
xorg-utils
xorg-xinit
xorg-xkill
xterm
xz
yaourt
zip
[keith@archbang ~]$ 


```

---

### Post by cbowman57 on 2011-08-26
/etc/pacman.conf

[http://www.archlinux.org/pacman/pacman.conf.5.html](http://www.archlinux.org/pacman/pacman.conf.5.html)

---

### Post by 23dornot23d on 2011-08-26
Ok cheers Chuck ....

will now add the ones in blue

```

                       #toc, .toc, .mw-warning { border: 1px solid rgb(170, 170, 170); background-color: rgb(249, 249, 249); padding: 5px; font-size: 95%; }#toc h2, .toc h2 { display: inline; border: medium none; padding: 0pt; font-size: 100%; font-weight: bold; }#toc #toctitle, .toc #toctitle, #toc .toctitle, .toc .toctitle { text-align: center; }#toc ul, .toc ul { list-style-type: none; list-style-image: none; margin-left: 0pt; padding-left: 0pt; text-align: left; }#toc ul ul, .toc ul ul { margin: 0pt 0pt 0pt 2em; }#toc .toctoggle, .toc .toctoggle { font-size: 94%; }body { font-family: 'Times New Roman'; font-variant: normal; text-indent: 0in; widows: 2; font-style: normal; font-weight: normal; text-decoration: none; color: rgb(0, 0, 0); text-align: left; font-size: 12pt; }table {  }td { border-collapse: collapse; text-align: left; vertical-align: top; }p, h1, h2, h3, li { color: rgb(0, 0, 0); font-family: 'Times New Roman'; font-size: 12pt; text-align: left; }         #
    [LEFT]# /etc/pacman.conf[/LEFT]
    #
    [LEFT]# See the pacman.conf(5) manpage for option and repository directives[/LEFT]
    
    #
    [LEFT]# GENERAL OPTIONS[/LEFT]
    #
    [LEFT][options][/LEFT]
    [LEFT]# The following paths are commented out with their default values listed.[/LEFT]
    [LEFT]# If you wish to use different paths, uncomment and update the paths.[/LEFT]
    [LEFT]#RootDir     = /[/LEFT]
    [LEFT]#DBPath      = /var/lib/pacman/[/LEFT]
    [LEFT]#CacheDir    = /var/cache/pacman/pkg/[/LEFT]
    [LEFT]#LogFile     = /var/log/pacman.log[/LEFT]
    [LEFT]HoldPkg     = pacman glibc[/LEFT]
    [LEFT]# If upgrades are available for these packages they will be asked for first[/LEFT]
    [LEFT]SyncFirst   = pacman[/LEFT]
    [LEFT]#XferCommand = /usr/bin/wget --passive-ftp -c -O %o %u[/LEFT]
    [LEFT]#XferCommand = /usr/bin/curl -C - %u > %o[/LEFT]
    [LEFT]#CleanMethod = KeepInstalled[/LEFT]
    [LEFT]Architecture = auto[/LEFT]
    
    [LEFT]# Pacman won't upgrade packages listed in IgnorePkg and members of IgnoreGroup[/LEFT]
    [LEFT]#IgnorePkg   =[/LEFT]
    [LEFT]#IgnoreGroup =[/LEFT]
    
    [LEFT]#NoUpgrade   =[/LEFT]
    [LEFT]#NoExtract   =[/LEFT]
    
    [LEFT]# Misc options (all disabled by default)[/LEFT]
    [LEFT]#UseSyslog[/LEFT]
    [LEFT]ShowSize[/LEFT]
    [LEFT]#UseDelta[/LEFT]
    [LEFT]TotalDownload[/LEFT]
    [LEFT]ILoveCandy[/LEFT]
    
    #
    [LEFT]# REPOSITORIES[/LEFT]
    [LEFT]#   - can be defined here or included from another file[/LEFT]
    [LEFT]#   - pacman will search repositories in the order defined here[/LEFT]
    [LEFT]#   - local/custom mirrors can be added here or in separate files[/LEFT]
    [LEFT]#   - repositories listed first will take precedence when packages[/LEFT]
    [LEFT]#     have identical names, regardless of version number[/LEFT]
    [LEFT]#   - URLs will have $repo replaced by the name of the current repo[/LEFT]
    [LEFT]#   - URLs will have $arch replaced by the name of the architecture[/LEFT]
    #
    [LEFT]# Repository entries are of the format:[/LEFT]
    [LEFT]#       [repo-name][/LEFT]
    [LEFT]#       Server = ServerName[/LEFT]
    [LEFT]#       Include = IncludePath[/LEFT]
    #
    [LEFT]# The header [repo-name] 
[/LEFT]
                        #toc, .toc, .mw-warning { border: 1px solid rgb(170, 170, 170); background-color: rgb(249, 249, 249); padding: 5px; font-size: 95%; }#toc h2, .toc h2 { display: inline; border: medium none; padding: 0pt; font-size: 100%; font-weight: bold; }#toc #toctitle, .toc #toctitle, #toc .toctitle, .toc .toctitle { text-align: center; }#toc ul, .toc ul { list-style-type: none; list-style-image: none; margin-left: 0pt; padding-left: 0pt; text-align: left; }#toc ul ul, .toc ul ul { margin: 0pt 0pt 0pt 2em; }#toc .toctoggle, .toc .toctoggle { font-size: 94%; }body { font-family: 'Times New Roman'; font-variant: normal; text-indent: 0in; widows: 2; font-style: normal; font-weight: normal; text-decoration: none; color: rgb(0, 0, 0); text-align: left; font-size: 12pt; }table {  }td { border-collapse: collapse; text-align: left; vertical-align: top; }p, h1, h2, h3, li { color: rgb(0, 0, 0); font-family: 'Times New Roman'; font-size: 12pt; text-align: left; }         # The header [repo-name] is crucial - it must be present and
    [LEFT]# uncommented to enable the repo.[/LEFT]
    #
    
    [LEFT]# The testing repositories are disabled by default. To enable, uncomment the[/LEFT]
    [LEFT]# repo name header and Include lines. You can add preferred servers immediately[/LEFT]
    [LEFT]# after the header, and they will be used before the default mirrors.[/LEFT]
    
    [LEFT][COLOR=Blue]**[testing]**[/COLOR][/LEFT]
    [LEFT]# Add your preferred servers here, they will be used first[/LEFT]
    [LEFT]Include = /etc/pacman.d/mirrorlist[/LEFT]
    
    [LEFT]**[COLOR=Red][core][/COLOR]**[/LEFT]
    [LEFT]# Add your preferred servers here, they will be used first[/LEFT]
    [LEFT]Include = /etc/pacman.d/mirrorlist[/LEFT]
    
    [LEFT]**[COLOR=Red][extra][/COLOR]**[/LEFT]
    [LEFT]# Add your preferred servers here, they will be used first[/LEFT]
    [LEFT]Include = /etc/pacman.d/mirrorlist[/LEFT]
    
    [LEFT][COLOR=Blue][community-testing][/COLOR][/LEFT]
    [LEFT]# Add your preferred servers here, they will be used first[/LEFT]
    [LEFT]Include = /etc/pacman.d/mirrorlist[/LEFT]
    
    [LEFT][COLOR=Red]**[community]**[/COLOR][/LEFT]
    [LEFT]# Add your preferred servers here, they will be used first[/LEFT]
    [LEFT]Include = /etc/pacman.d/mirrorlist[/LEFT]
    
    [LEFT]# An example of a custom package repository.  See the pacman manpage for[/LEFT]
    [LEFT]# tips on creating your own repositories.[/LEFT]
    [LEFT]#[custom][/LEFT]
    [LEFT]#Server = file:///home/custompkgs[/LEFT]
    
    
   
  [LEFT]
[/LEFT]
   
  

```ok got them now

```

[root@archbang etc]# pacman -Syyu
:: Synchronizing package databases...
 testing                  16.8K   89.2K/s 00:00:00 [----------------------] 100%
 core                     44.3K  155.8K/s 00:00:00 [----------------------] 100%
 extra                   508.4K  407.2K/s 00:00:01 [----------------------] 100%
 community-testing         0.5K  366.9K/s 00:00:00 [----------------------] 100%
 community               454.8K  446.9K/s 00:00:01 [----------------------] 100%
:: Starting full system upgrade...
resolving dependencies...
looking for inter-conflicts...

Targets (16): avahi-0.6.30-5 [0.39 MB]  isl-0.07-1 [0.55 MB]
              cloog-0.16.3-1 [0.10 MB]  gcc-libs-4.6.1-4 [0.78 MB]
              gcc-4.6.1-4 [16.09 MB]  libcups-1.5.0-1 [0.27 MB]
              linux-firmware-20110822-1 [10.49 MB]  logrotate-3.8.0-2 [0.03 MB]
              lzo2-2.06-1 [0.10 MB]  netcfg-2.6.8-1 [0.02 MB]
              net-tools-1.60.20110819cvs-1 [0.11 MB]  perl-5.14.1-4 [11.86 MB]
              texlive-bin-2011.1-1 [13.52 MB]
              texlive-core-2011.23170-1 [104.11 MB]  udisks-1.0.4-1 [0.15 MB]
              wicd-1.7.0-11 [0.25 MB]

Total Download Size:    158.83 MB
Total Installed Size:   459.63 MB

Proceed with installation? [Y/n] 


```

I said no to the above for the moment ..... not sure how stable the upgrades are in testing ....

But Interesting .....  I still not getting the other packages yet ..... using individual installs 
must be something else .... !!!

---

### Post by cbowman57 on 2011-08-26
That looks good, if you're installing to your 32-bit machine you will obviously want some repos that I don't have active.

There are probably some you'll have to get from AUR, a pacman -Qm shows that I currently have these installed from AUR:

```
afio 2.5-3
alacarte 0.13.2-4
audit 2.1.2-1
bleachbit 0.8.8-1
chromium-browser-l10n-ppa 15.0.861.0.97968-1
chromium-browser-ppa 15.0.861.0.97968-1
chromium-codecs-ffmpeg-extra-ppa 15.0.861.0.97968-1
fatrat-git 20110824-1
firefox-nightly 9.0a1-1
flashplugin-prerelease 11.0.1.98-1
grub-customizer 79-1
gtkhotkey 0.2.1-4
libchunfeng 0.1.0-2
libpng12 1.2.46-2
libzeitgeist 0.3.10-1
log4cpp 1.0-5
luaposix 5.1.11-1
mindi-busybox 1.18.3-3
nautilus-p7zip 1.0.0-2
os-prober 1.48-1
package-query 0.8.1-1
packer 20110823-1
pacman-color 3.5.4-1
picard-plugins 0.15-2
pion-net 4.0.5-1
python-nautilus 1.0-1
quilt 0.48-2
rdflib 3.1.0-1
readahead-fedora 1.5.6-2
synapse 0.2.6-1
ttf-ms-fonts 2.0-8
ttf-ubuntu-font-family 0.71.2-1
ulatencyd-git 20110824-1
vpack 20110825-1
zeitgeist 0.8.1.1-1
zeitgeist-userspace 0.1-1
zsync 0.6.2-1
 
```

---

### Post by wojox on 2011-08-26
> **cbowman57 said:**
> 

Did you run exec ck-launch-session gnome-session from the terminal?  

```
sudo pacman -S consolkit
```

Needs to be installed to ck-launch-session. That command should reside in .xinitrc :P

I used Gnome3 when it was still in testing on Arch. Ran great. Switched to DWM for now.

---

### Post by cbowman57 on 2011-08-26
> **wojox said:**
> ```
sudo pacman -S consolkit
```

Needs to be installed to ck-launch-session. That command should reside in .xinitrc :P

I used Gnome3 when it was still in testing on Arch. Ran great. Switched to DWM for now.

Ok, while I do remember running that command, I didn't use it in my .xinitrc (just looked).  Isn't that just for the non-display manager method? If not I need to do a quick edit, since it's not active nor do I have consolkit installed.  Is it a miracle that I even have a working system? :)

---

### Post by wojox on 2011-08-26
> **cbowman57 said:**
> Ok, while I do remember running that command, I didn't use it in my .xinitrc (just looked).  Isn't that just for the non-display manager method? If not I need to do a quick edit, since it's not active nor do I have consolkit installed.  Is it a miracle that I even have a working system? :)

Good question. :p Yes, I've always been a startx dude.

It may pick it up. I'm not to sure on the display manager policy.

Do you just add your dm of choice to DAEMONS=()?

---

### Post by 23dornot23d on 2011-08-26
Don't do the upgrades from testing .....

Just lost my network ....

Got it back by downgrading again ......

_____________________

Me too startx - I prefer to use .... or gdm .... at the moment I am in slim is there a way to stop it starting up .... ?

something to do with runlevels ?

3: Multi user: Normal mode

adding 3 at the end of the boot line ....

does not work .... stops to let you log in ...... then continues into the graphics mode ......

Ok but go to terminal 3 tty3

and we now have Gnome - Shell working ...... sorted

---

### Post by cbowman57 on 2011-08-26
wojox, yeah, I just added gdm as a daemon.

Despite what I kept reading about having to load dbus too I kept getting a fail error on boot because it was loading twice, still don't know what  was loading it already but I disabled it in rc.conf and something still loads it up so I'm good.

---

### Post by cbowman57 on 2011-08-26
> **23dornot23d said:**
> Don't do the upgrades from testing .....

Just lost my network ....

Got it back by downgrading again ......

Did it upgrade wicd?  I noticed you installed that in one of your captures earlier.

---

### Post by 23dornot23d on 2011-08-26
Yep [[COLOR=Red]_***wicd***_[/COLOR]]("http://wicd.sourceforge.net/") .... upgraded as well as some other things to do with the net ..... have gone through them and downgraded
where I could ..... 

I have the internet back now ......

I downgraded and rebooted alls ok now ..........

want to know how to stop slim starting up automatically .....

is it done using runlevels or is there an easier way ?

[https://wiki.archlinux.org/index.php/Runlevels](https://wiki.archlinux.org/index.php/Runlevels)

I can get to another terminal I just would like for X not to be running ....

---

### Post by cbowman57 on 2011-08-26
This what my inittab looks like, I'm using gdm but pretty sure everything else is the same.

```
#
# /etc/inittab
#

#  Runlevels:
#    0    Halt
#    1(S)	Single-user
#    2    Not used
#    3    Multi-user
#    4    Not used
#    5    X11
#    6    Reboot

## Only one of the following two lines can be uncommented!
# Boot to console
id:3:initdefault:
# Boot to X11
#id:5:initdefault:

rc::sysinit:/etc/rc.sysinit
rs:S1:wait:/etc/rc.single
rm:2345:wait:/etc/rc.multi
rh:06:wait:/etc/rc.shutdown
su:S:wait:/sbin/sulogin -p

# -8 options fixes umlauts problem on login
c1:2345:respawn:/sbin/agetty -8 -s 38400 tty1 linux
c2:2345:respawn:/sbin/agetty -8 -s 38400 tty2 linux
#c3:2345:respawn:/sbin/agetty -8 -s 38400 tty3 linux
#c4:2345:respawn:/sbin/agetty -8 -s 38400 tty4 linux
#c5:2345:respawn:/sbin/agetty -8 -s 38400 tty5 linux
#c6:2345:respawn:/sbin/agetty -8 -s 38400 tty6 linux

# Serial Virtual Console for KVM and others VMs
#s0:2345:respawn:/sbin/agetty -8 -s 9600 ttyS0 linux

# Hypervisor Virtual Console for Xen and KVM
#h0:2345:respawn:/sbin/agetty -8 -s 38400 hvc0 linux

ca::ctrlaltdel:/sbin/shutdown -t3 -r now

# Example lines for starting a login manager
#x:5:respawn:/usr/bin/xdm -nodaemon
x:5:respawn:/usr/sbin/gdm -nodaemon
#x:5:respawn:/usr/bin/kdm -nodaemon
#x:5:respawn:/usr/bin/slim >/dev/null 2>&1

# End of file
```

---

### Post by 23dornot23d on 2011-08-26
Just adding 3 after the boot line did it ..... straight after RO 

[IMG]http://img829.imageshack.us/img829/9960/screenshotey.jpg[/IMG]

Cheers chuck ..... it needed to start from gdm and it is fine now ....

another one .... sorted ...


[IMG]http://img851.imageshack.us/img851/2194/screenshot2ja.jpg[/IMG]

:D Cheers/Thanks for all the help Chuck ... satanselbow ... wojox .... mips and Sanderd17



Whats next .... just wondering if all of these will upgrade ok when Gnome 3.2
is released .....

---

### Post by cbowman57 on 2011-08-26
Fantastic! :)

I just switched gdm from a daemon in rc.conf to loading run level 5 in inittab.  Was hoping for a speed boost but there wasn't any.  Think I'll continue using this method though, it is recommended in the wiki.

Oh, what do you think so far? Good performance compared to the other distros we've tried G-S on?

---

### Post by 23dornot23d on 2011-08-26
Ok that's what I should do too ....

Am happy now ..... half an hour back 

I was almost going to re-install ....  networks and losing them 
become my worst nightmare on a system ... so re-install is often
quickest for me ....

But luckily did not have to .... cheers again everyone ... :D


Very good performance wise so far .... 251 Mb mem used and I have firefox and conky running ...
My processor is 8 % .....

Great system .... now a little customization is needed ....

---

### Post by cbowman57 on 2011-08-26
I know what you mean,when the network breaks I'm dead in the water too.

For me this was a bit of a challenge to setup but the reward was worth it.

---

### Post by 23dornot23d on 2011-08-26
The thing with each one - we get to learn a little more too - and
being so conversant now with Gnome Shell we sort of know what to
expect ....

I saw the error saying polkit problem .... and thought this is not
something I have seen before .... and Gnome Shell was trying for 
a while to start with no apparent errors in the terminal.

Glad it was just Slim .... that caused the problem ....

Gdm must do something different - but its good now.

Ok going to call it a night at that ... some steady work tomorrow
customizing it a little .... 

Catch you later ,,, thanks again for working to get a good result ...

[IMG]http://img199.imageshack.us/img199/882/screenshot7xx.jpg[/IMG]

Will be on again tomorrow to finish it off ...

---

### Post by cbowman57 on 2011-08-27
Keith, when you start working on this again here's a fresh snapshot of what I'm running at the moment, pretty self-explanatory but here's that link again that makes some sense of pacman for script installation [https://wiki.archlinux.org/index.php/Pacman_Tips#Backing_up_and_retrieving_a_list_of_installed_packages](https://wiki.archlinux.org/index.php/Pacman_Tips#Backing_up_and_retrieving_a_list_of_installed_packages)

That chessboard wallpaper with that theme looks really elegant.

---

### Post by mips on 2011-08-27
> **cbowman57 said:**
> Was hoping for a speed boost but there wasn't any.

[https://wiki.archlinux.org/index.php/Systemd](https://wiki.archlinux.org/index.php/Systemd)
[https://wiki.archlinux.org/index.php/Improve_Boot_Performance](https://wiki.archlinux.org/index.php/Improve_Boot_Performance)
[https://wiki.archlinux.org/index.php/Maximizing_Performance](https://wiki.archlinux.org/index.php/Maximizing_Performance)

For the tweakers out there.

---

### Post by cbowman57 on 2011-08-27
It's 4:22AM here mips, you're evil. :lol:

Woke up around 2 for reasons unknown, had some things I wanted to try.  Was fairly successful, I'm pleased.  Now I have to decide, make a pot of coffee or try to fall asleep again.

---

### Post by cbowman57 on 2011-08-27
Well, should have made the coffee or gone back to sleep. :)

Had a little scare myself this morning, but it did solve the mystery of what was loading dbus (outside of rc.conf).  I was experimenting with daemon arrangements and other things when I decided to use my old standby preload instead of ulatencyd & fedora-readahead.  So after I installed preload I did a few reboots to see how things went and noticed that fedora-readahead was running too, so I uninstalled it and did a couple other tweaks.  Rebooted, everything looked great, but gdm didn't load.

After some furious editing with nano I discovered that removing fedora-readahead had replaced or rewritten the inittab, changing it back to init 3 and in the process dbus was no longer loaded.

Long story short, changed inittab back to init 5 & gdm --nodaemon.  In rc.conf I had to put dbus back in as a daemon.  

Life is good again. :)

---

### Post by 23dornot23d on 2011-08-27
> 
Well, should have made the coffee or gone back to sleep. :smile:
I am similar .... last night could not sleep until I had done a couple of tweaks to the desktop .... the chess board is a standard background with kde

[[COLOR=Red]_***SCREENSHOT 1***_[/COLOR]]("http://img717.imageshack.us/img717/8623/snapshot24k.jpg") ( KDE running by itself ..... KDM as the DM )

then after running gnome-shell --replace

[[COLOR=RoyalBlue]**SCREENSHOT 2**[/COLOR] ]("http://img854.imageshack.us/img854/8923/screenshot10gs.jpg")( Gnome Shell running ...... with the KDE Panel + other goodies )

notice the memory usage and CPU usage ,,,, this is still on a 512 Meg Ram machine ...

This is incredible ..... could almost run it on a 256 Meg Machine .....

I am looking to use the KDM Steampunk Ksplash Theme ..... but cannot work out
how to set up Ksplash
at the moment ..... :confused:

I have downloaded your list for packages too ty .... will try to get the steampunk
running too ..... does remastersys or anything else work on this .... to create a 
live CD ..... has anyone done one yet for Gnome-Shell ?

Good to hear you got sorted .... I am just adding 3 onto the end of the boot line and
it does what I want ..... eventually I will just boot into KDM ...... but for the time
being I prefer just going to the terminal .... and starting it myself .....

I have a slightly better idea of whats going on then ..... 

Jobs to do ....

1 ..... Ksplash ...... using the [_***Steampunk Login***_]("http://kde-look.org/content/show.php/SteampunK+KDM+Theme?content=142139")

need to know how to set it up ... so find an example ,,
[https://bbs.archlinux.org/viewtopic.php?id=52257](https://bbs.archlinux.org/viewtopic.php?id=52257)

2 ...... Remastersys or something else .....

---

### Post by cbowman57 on 2011-08-27
I am so completely sold on Arch right now, I love being able to get right inside & know what's going on.

No Remastersys for Arch, there is archboot, which might do something similar but it certainly isn't point & click.

Got my local repository setup, that's relatively simple with Arch, and better documented than either Debian or Ubuntu.

If you want a gui frontend for pacman I suggest wakka, I tried appset-qt, which has some nice features, but it seemed buggy.  On a system with KDE installed it might be stable, I don't know for certain.

I've been creating some very basic bash scripts to do some maintenance, sync my repository, etc.. I think I included one in that tarball I attached this morning.  It creates those pkg lists.

---

### Post by sanderd17 on 2011-08-27
> **cbowman57 said:**
> I am so completely sold on Arch right now, I love being able to get right inside & know what's going on.

Same here
> 
Got my local repository setup, that's relatively simple with Arch, and better documented than either Debian or Ubuntu.

An app repository? Why do you need it? (Just interested)
> 
If you want a gui frontend for pacman I suggest wakka, I tried appset-qt, which has some nice features, but it seemed buggy.  On a system with KDE installed it might be stable, I don't know for certain.

Also tried appset (and some gtk one too), but prefered a CLI tool until now. Will try wakka.
> 
I've been creating some very basic bash scripts to do some maintenance, sync my repository, etc.. I think I included one in that tarball I attached this morning.  It creates those pkg lists.

---

### Post by 23dornot23d on 2011-08-27
You are back on the job early - good to see ....

What is the advantage of the local repository .... is this if you have slow download
access .... ( so by doing it the way you do it ..... you only download once )

But then waht about updates to packages ?

ok you answered that with the sync ....

[IMG]http://img841.imageshack.us/img841/7060/snapshot28kf.jpg[/IMG]

wakka - no go .... need to be root but will not sudo .... 

but runs from the $ wakka  ( good for viewing things - but can do nothing else with it )

So how do you run it as root .... as it fails from the hash and it fails from sudo

Not sure whats wrong .... built it as root using yaourt .... may be the problem ...

---

### Post by cbowman57 on 2011-08-27
> **sanderd17 said:**
> 

An app repository? Why do you need it? (Just interested)



Insurance, plus I'm on a slow connection.  This way I can do simple downgrades even if I lose my network.

When I was working with gNatty & Debian I was doing multiple installs, I'd take the packages that were in the apt/cache (can't remember the exact location anymore) and copy them to a safe lcation, then if I wanted to do a fresh installation I'd copy them to the fresh partition & proceed normally, but instead of downloading the same files over & over again I just recycled, saved me hundreds of hours.

I've been pretty cautious not to break Arch but if I get the urge to try something risky all the files will be where I can get to them quickly.  Besides, since I've got this running on Raid, and my favorite backup method won't work (Clonezilla) I need to have something that makes me feel comfortable.  From what I can tell so far I can use pacman to automate an installation based on the pkg lists that I'm generating from this installation.  I could be totally wrong and am just giving myself a false sense of security, but at least it's something. :)

---

### Post by cbowman57 on 2011-08-27
I don't know Keith, it's listed in my System Tools menu, I click on it & it runs.  A dependency is xdg-su, maybe yours somehow installed without that.  I might look at editing the .desktop file to use gksu instead of xdg-su, but that's not critical at the moment.

---

### Post by 23dornot23d on 2011-08-27
What you said about having a local repository would be good in so many ways for others
too with similar needs ....

It would also save hours of un needed downloads for a lot of people too .......

The savings on the NET could be worth a proper system being written to add this where
people may need it .....

There must be lots of good reasons for having it ......

One I can think of - is that when you build your system and it works ...... all the files you used at that time are there to re-use again ...... this for people that do not mess with
there systems much and just want to put it back together as it was at the time of installation would be great.

gksu works great ..... with wakka

[IMG]http://img689.imageshack.us/img689/3565/snapshot29u.jpg[/IMG]

too many hours on here for me .... time for a bike ride .... ;)

gksu wakka

Thanks ,,,

---

### Post by sanderd17 on 2011-08-27
> **cbowman57 said:**
> I don't know Keith, it's listed in my System Tools menu, I click on it & it runs.  A dependency is xdg-su, maybe yours somehow installed without that.  I might look at editing the .desktop file to use gksu instead of xdg-su, but that's not critical at the moment.

Is xdg-su causing that terminal window to appear before wakka gets loaded?

---

### Post by cbowman57 on 2011-08-27
This is the wiki link for the local repo [https://wiki.archlinux.org/index.php/Pacman_Tips#Custom_local_repository](https://wiki.archlinux.org/index.php/Pacman_Tips#Custom_local_repository)

This is not working as expected.  I'll leave it here just in case somebody else wants to mess with it before I find a solution.

```
#!/bin/sh
cp /var/cache/pacman/pkg/*.pkg.tar.xz /home/chuck/Downloads/ArchRepo/
pacman -Sc
repo-add /home/chuck/Downloads/ArchRepo/archie.db.tar.gz /home/chuck/Downloads/ArchRepo/*.pkg.tar.gz
pacman -Syu
```

---

### Post by 23dornot23d on 2011-08-27
The terminal window in my screen shot is there as I am downloading abiword - just checking that it works ok  ..... it goes away after the installation .... just close it.

The package manager wakka looks good .... very similar in its layout to synaptic.


_____________________________

also ...


Just copied and ran your script with username as keith now ..... 

I have a backup too roughly 1.3 Gig .... in size ....

So if you have 1.3Gig spare its a good backup - especially should you lose the Net too ...



I just need to point pacman to it in an emergency ...... thanks for the link wwill keep it here
for reference ....

[https://wiki.archlinux.org/index.php/Pacman_Tips#Backing_up_and_retrieving_a_list_of_installed_packages](https://wiki.archlinux.org/index.php/Pacman_Tips#Backing_up_and_retrieving_a_list_of_installed_packages)

Like the problem last night ..... luckily I had kept all the files - 
but if not for the ones in the repository last night it would have had to have been a full re-install from scratch .... 

I would not know how to fix the net problem caused by adding the testing package wicd ....

But with a backup of the last set of files that worked - where I know where they are ..... should meen I can just point pacman to it somehow .....  now .....

Possible problem may come if the config files get altered though .....

and

My only real worry would be having two if you pointed to both and they ever do get out of sync ....

So pacman needs to point to one or the other but not both .....

Or a way in wakka to choose which one to use would be good ..... ;)
i.e
The [normal set of repos] or the [backup set] ....


Also changed my inittab

to be 3 rather than 5 now .....

```

#
# /etc/inittab
#

#  Runlevels:
#    0    Halt
#    1(S)    Single-user
#    2    Not used
#    3    Multi-user
#    4    Not used
#    5    X11
#    6    Reboot

## Only one of the following two lines can be uncommented!
# Boot to console
id:[COLOR=Red]**3**[/COLOR]:initdefault:
# Boot to X11
#id:5:initdefault:

rc::sysinit:/etc/rc.sysinit
rs:S1:wait:/etc/rc.single
rm:2345:wait:/etc/rc.multi
rh:06:wait:/etc/rc.shutdown
su:S:wait:/sbin/sulogin -p

# -8 options fixes umlauts problem on login
c1:2345:respawn:/sbin/agetty -8 38400 tty1 linux
c2:2345:respawn:/sbin/agetty -8 38400 tty2 linux
c3:2345:respawn:/sbin/agetty -8 38400 tty3 linux
c4:2345:respawn:/sbin/agetty -8 38400 tty4 linux
c5:2345:respawn:/sbin/agetty -8 38400 tty5 linux
c6:2345:respawn:/sbin/agetty -8 38400 tty6 linux

ca::ctrlaltdel:/sbin/shutdown -t3 -r now

# Example lines for starting a login manager
#x:5:respawn:/bin/su keith -l -c "/bin/bash --login -c /usr/bin/startx >/dev/null 2>&1"
#x:5:respawn:/usr/sbin/gdm -nodaemon
#x:5:respawn:/usr/bin/kdm -nodaemon
x:5:respawn:/usr/bin/slim >& /dev/null

# End of file

```Ok that works perfectly now ..... if you use (ctrl+alt+f1) or (ctrl+alt+f3)
 
tty1 ittakes you in using slim still .... into a xfce environment .....
tty3 takes you to use anything you want ..... in my case just type in >>> kdm

A very good blog ..... just for basic information for initially setting up Arch ..... looks good
to me anyway ..... ( at this moment in time - very helpful )

[http://lifehacker.com/5680453/build-a-killer-customized-arch-linux-installation-and-learn-all-about-linux-in-the-process](http://lifehacker.com/5680453/build-a-killer-customized-arch-linux-installation-and-learn-all-about-linux-in-the-process)


> 
If you want a gui frontend for pacman I suggest wakka, I tried  appset-qt, which has some nice features, but it seemed buggy.  On a  system with KDE installed it might be stable, I don't know for certain.
Just tried this too .... 

[IMG]http://img51.imageshack.us/img51/2367/snapshot31d.jpg[/IMG]

looks good ....
[URL="http://img217.imageshack.us/img217/5729/snapshot32s.jpg"][U][I][B]
SCREENSHOT of appset-qt[/B][/I][/U][/URL]


_______________________________

Just slowly going through everything covvered last night ...... and this morning ...

[[COLOR=Blue]**ARCHBOOT**[/COLOR]]("http://www.google.fr/search?q=archboot&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a")

---

### Post by cbowman57 on 2011-08-27
The problem I was having with appset-qt was when I tried to do anything with the AUR section, it would crash.  I did like the feature set though.  An older version I used last week didn't have that flaw so I don't know if my experience was isolated or introduced in the newer version.

---

### Post by 23dornot23d on 2011-08-27
Same thing here ..... it crashed just trying to get a list of AUR installed ...... :confused:
[COLOR=Blue][B]
wakka[/B][/COLOR] it is then ..... as my package manager .....

---

### Post by cbowman57 on 2011-08-27
> **23dornot23d said:**
> Same thing here ..... it crashed just trying to get a list of AUR installed ...... :confused:
[COLOR=Blue][B]
wakka[/B][/COLOR] it is then ..... as my package manager .....

Yeah, worth looking at it again in the future.  I'm sure it will get a bug fix rather soon.

Ok, something useful, a script to create a usable pkglist & one to restore from one.  tested both, they work well for me. (create-restore.tar.gz) [COLOR=Red]<< Updated 28 Aug 2011[/COLOR]

---

### Post by 23dornot23d on 2011-08-27
____________________________

Where to report Bugs  ....... > 

[COLOR=Red][U][I][B][ARCH BUGS]("https://bugs.archlinux.org/")

[/B][/I][/U]No USB booting for Arch or Archbang - from a 1 Terra USB Samsung Hard Drive .... 

( may be due to old computer BIOS ? >>> but grub 2 and UBUNTU works from it ok ....... on the same machine )[/COLOR]  [COLOR=Red]
[U][I][B] 
[KDE BUGS]("https://bugs.kde.org/buglist.cgi?bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&bug_status=UNCONFIRMED&bugidtype=include&chfield=%5BBug+creation%5D&chfieldfrom=1d&chfieldto=Now&bug_file_loc=&cmdtype=doit")

[/B][/I][/U]appset-qt ..... crashes using AUR repos  ....[/COLOR]


--------------------------------------------------------------


ok ty .... saved both will take a look tonight ....  :P .... both installed and working

[IMG]http://img707.imageshack.us/img707/7450/snapshot41.jpg[/IMG]

would love to get this running on my laptop now ...... 

But it needs to go on a [[COLOR=Blue]_***USB first***_[/COLOR]]("https://bbs.archlinux.org/viewtopic.php?id=65844") and then be swapped over to the laptop ,,,

and upto now .... no luck with the USB part of it.

--------------------------------------------------------------

I just realized there is another option ..... 

I have the two computers connected over ethernet ...... could I boot either slackware or arch across the ethernet 

never yet successfully set up Linux on my network ..... 

( Although a long while back I did ok with Windows - but that was simply moving the settings on a 
     disk from one computer to the next )

**ifconfig** gives the info if there is any ......

So where next .......

[http://www.linuxheadquarters.com/howto/networking/networkconfig.shtml](http://www.linuxheadquarters.com/howto/networking/networkconfig.shtml)

Really not confident in altering my network while it is working ok ....
but would like to boot to [[COLOR=Blue]_***Arch across the Network***_[/COLOR]]("https://wiki.archlinux.org/index.php/Diskless_network_boot_NFS_root")

Guess this is not going to happen ....

---

### Post by cbowman57 on 2011-08-28
Keith said:
> I just realized there is another option ..... 

I have the two computers connected over ethernet ...... could I boot either slackware or arch across the ethernet 

never yet successfully set up Linux on my network .....

How you coming with this?  I don't even know where to start, and don't have a network to try it on.

---

### Post by 23dornot23d on 2011-08-28
I had a try last night ..... altered one setting and lost my network .....

The way it said to do it was temporary ..... so on next reboot all was ok again.

As I have said before - I am lost with Networks and altering it and losing it all
I would have no idea what to do or where to start to put hings right.

So for the time being this will remain a mystery to me ....

I have little to gain here ..... as I have big USB drives I can just take what I need from
one computer to the next .

Other than of course booting across the Net - but reading that document you need to
jump through more hoops than I can manage ........ ;)

---

### Post by cbowman57 on 2011-08-28
Keith, don't know if this is pertinent or not but thought I'd post the link in case it might help with the USB problem [https://bbs.archlinux.org/viewtopic.php?pid=983030#p983030](https://bbs.archlinux.org/viewtopic.php?pid=983030#p983030)

> 
Fallback has all mkinitcpio hooks loaded, the normal one only has  what is needed. Adding usb to the HOOKS= line in /etc/mkinitcpio.conf  and running 'mkinitcpio -g /boot/kernel26.img' as root will allow you to  boot from USB.
Running as fallback all of the time isn't going to hurt anything, but fixing the problem is always better.

---

### Post by 23dornot23d on 2011-08-28
Cheers Chuck ........ I have added that in now ..... ty

Adding usb to the HOOKS= line in /etc/mkinitcpio.conf 

```

# vim:set ft=sh
# MODULES
# The following modules are loaded before any boot hooks are
# run.  Advanced users may wish to specify all system modules
# in this array.  For instance:
#     MODULES="piix ide_disk reiserfs"
MODULES=""

# BINARIES
# This setting includes any additional binaries a given user may
# wish into the CPIO image.  This is run first, so it may be used to
# override the actual binaries used in a given hook.
# (Existing files are NOT overwritten if already added)
# BINARIES are dependency parsed, so you may safely ignore libraries
BINARIES=""

# FILES
# This setting is similar to BINARIES above, however, files are added
# as-is and are not parsed in any way.  This is useful for config files.
# Some users may wish to include modprobe.conf for custom module options
# like so:
#    FILES="/etc/modprobe.d/modprobe.conf"
FILES=""

# HOOKS
# This is the most important setting in this file.  The HOOKS control the
# modules and scripts added to the image, and what happens at boot time.
# Order is important, and it is recommended that you do not change the
# order in which HOOKS are added.  Run 'mkinitcpio -H <hook name>' for
# help on a given hook.
# 'base' is _required_ unless you know precisely what you are doing.
# 'udev' is _required_ in order to automatically load modules
# 'filesystems' is _required_ unless you specify your fs modules in MODULES
# Examples:
##   This setup specifies all modules in the MODULES setting above.
##   No raid, lvm2, or encrypted root is needed.
#    HOOKS="base"
#
##   This setup will autodetect all modules for your system and should
##   work as a sane default
#    HOOKS="base udev autodetect pata scsi sata filesystems"
#
##   This is identical to the above, except the old ide subsystem is
##   used for IDE devices instead of the new pata subsystem.
#    HOOKS="base udev autodetect ide scsi sata filesystems"
#
##   This setup will generate a 'full' image which supports most systems.
##   No autodetection is done.
#    HOOKS="base udev pata scsi sata usb filesystems"
#
##   This setup assembles a pata mdadm array with an encrypted root FS.
##   Note: See 'mkinitcpio -H mdadm' for more information on raid devices.
#    HOOKS="base udev pata mdadm encrypt filesystems"
#
##   This setup loads an lvm2 volume group on a usb device.
#    HOOKS="base udev usb lvm2 filesystems"
HOOKS="base udev autodetect pata scsi sata [COLOR=Red]**usb**[/COLOR] filesystems usbinput"

# COMPRESSION
# Use this to compress the initramfs image. With kernels earlier than
# 2.6.30, only gzip is supported, which is also the default. Newer kernels
# support gzip, bzip2 and lzma. Kernels 2.6.38 and later support xz
# compression.
#COMPRESSION="gzip"
#COMPRESSION="bzip2"
#COMPRESSION="lzma"
#COMPRESSION="xz"
#COMPRESSION="lzop"

# COMPRESSION_OPTIONS
# Additional options for the compressor
#COMPRESSION_OPTIONS=""

```
Not sure if I should have anything else in here ...... for USB ......

---

### Post by cbowman57 on 2011-08-28
Looks just like mine, except I have mdadm instead of usb.

---

### Post by 23dornot23d on 2011-08-28
Ok Cheers Chuck

Another job to do too - just going to look at the Slackware one as that may need altering too .....

gksu gedit /etc/mkinitcpio.conf

Interesting there is not one of these in Slackware ...... ? !!!


Also

found this too for USB sticks ...

[http://usalug.com/phpBB3//viewtopic.php?t=12377](http://usalug.com/phpBB3//viewtopic.php?t=12377)

---

### Post by cbowman57 on 2011-08-28
Whoah!  A lot of information in that link.  Good to have for future reference.

---

### Post by 23dornot23d on 2011-08-28
Give it a try ..... see if it works .... for USB sticks .... was a old article though .... mentions
much smaller USB's 1 Gig even .... ;)

I tried but this OLD machine
does not want to recognise 8 Gig USB sticks from startup ....

( I dont think they were around at the time this BIOS was made )

will see them though once the OS takes over .....

________________________________________________

My main problem is that I have to mess about with this old machine ....

To even get the computer to recognise that a USB 1 TERRA Seagate HDD is attached ......

1 ..... I have to unplug the power to the USB before starting the computer ( count to 10 replug the power in )

2 ..... Booting the computer and pressing F11 will show its there and I can boot to UBUNTU etc ....

3 ..... Reboot ..... and the USB no longer appears when doing a F11 ....... ( to boot from any bootable device )

so its back to shutdown ...... unplug the USB drive ...... restart ....... its a pain .... :confused:

---

### Post by cbowman57 on 2011-08-28
Is there a setting in the bios for timeout, or something like that for USB?  I know this desktop has one for number of seconds for detection (can't remember how it's listed eactly).

Just brainstorming, trying to find a way around that inconvenience.

---

### Post by 23dornot23d on 2011-08-28
Will have a look ..... ty ......

Just been altering the sudoers file .... not advised ...... but got out of my problem with this link

____________________________________ A small inconvenience _____________

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

I edited it and it was no longer 440 ........ was 640 or something ...... kept refusing to work .....

```

slack : Aug 28 18:16:56 : keith : /etc/sudoers is mode 0640, should be 0440 ; TTY=pts/1 ; PWD=/home/keith ; COMMAND=gedit


```chmod 0440 /etc/sudoers

but all's ok now ......
____________________________________

It does not appear to be a " time " thing with the USB drive ..... 
I enabled slow boot where it checks the memory etc out before starting ..... but this made no difference either ..... 
Could not see any other settings that would alter the way it works ..... ( so will just have to live with it )

I know some USB drives need more time to be recognized ...... but this does not seem to be the 
case here ....... possibly the electrics here not having a proper earth that does it ..... !!!

---

### Post by cbowman57 on 2011-08-28
Well there is the recommende way, and then there's my way. :)

I just :
su
nano /etc/sudoers

then duplicate the root entry with my user name. :lol:

Have yet to figure out visudo and absolute security isn't really required for me.

---

### Post by 23dornot23d on 2011-08-28
vi drives me mad ...... cannot get used to the way it works ...... nothing seems to be standard ......

it has its own standards .....

Seems ok now and re-booted back into it ...... 

I may give it another try on a USB ..... as I have a older 320 Gig that it may work better on it ......

Time to find out I guess ........:)

swap a few things over now ....

I may have a way forward as the 320 Gig does appear in the boot list even after a warm
restart ....... so tonights challenge .... get Arch to run from this USB drive .....

So moving right along now ..... version 2 of Arch .......

A couple of good things came from that - This Western Digital 320 Gig drive I rarely use ....

but it works well on the older computer ..... so later tonight will give it a try out ....

__________________________________________________________________

Its picked Slackware and Arch out to now and both boot from grub 2 on the main drive sda1 internal hard drive ....

__________________________________________________________________

If I can get either or both onto the 320 Gig USB ..... then there is a chance one could 

become my main OS on the Laptop and Dual screen .... will be interesting .. as they should fly

on the dual core - hopefully ..... ;)


_________________________________

This is just for testing .... ( if it works out may do a proper one bigger partition sizes ..... )

ok the installer expects a few things .......

so will make a separate boot partition ...... /boot ............... sdb10 ...... (a bit big but 900 meg)
will also make a root partition .................../.........   arch3 ..sdb9 ............ 9.92 Gig
will also make a home partition ................ /home ............ sdb11 ....... 7.92 Gig
also the swap partition ............................./swap ............. sdb6 ............. ( 1.44 Gig )


ok and going through the stages ...... it first gives this warning again .....

[IMG]http://img88.imageshack.us/img88/2570/2011082513142739151360x.jpg[/IMG]


so I carry on as it will not let you exit  ..... and use the partitions as I set them up and it says Installation succeeded ....

moment of truth ..... now ..... did it work ?

seems to format the partitions ok ..... ( moving right along ..... )

ok configuring ALSA card .... building database ..... searching sound cards found one via82xx (accepted and ok)

---

### Post by cbowman57 on 2011-08-28
> ok the installer expects a few things .......

so will make a separate boot partition ...... /boot ............... sdb10 ...... (a bit big but 900 meg)
will also make a root partition .................../.........   arch3 ..sdb9 ............ 9.92 Gig
will also make a home partition ................ /home ............ sdb11 ....... 7.92 Gig
also the swap partition ............................./swap ............. sdb6 ............. ( 1.44 Gig )

It might expect that but all I used was a swap & / and it went without a problem. (For next time :) )

---

### Post by 23dornot23d on 2011-08-28
Yep I am trying to do it as it expects everything so as to not do something that may 

give me cause to say ...... ( I wonder if I had have done it that way - would it work > ? )

ok got a partition table that looks reasonable ...... [COLOR=Red]**as 1.82 Gig is now used on sdb9**[/COLOR]

I did not trust the boot loader ...... so will have to do this one by hand ....

[IMG]http://img692.imageshack.us/img692/9131/screenshot1cs.jpg[/IMG]

Fullsize SCREENSHOT
[http://img819.imageshack.us/img819/2157/screenshot1wa.jpg](http://img819.imageshack.us/img819/2157/screenshot1wa.jpg)

Boot is on sdb7 ..... will update grub 2 from Ubuntu or Debian .... this is in >>>  and see if it picks it up first .....

( ok we are safe as this is just a test ...... in a partition that does not matter ...... but if it was for real .... ? )


[IMG]http://img51.imageshack.us/img51/7707/errorzr.jpg[/IMG]


It does but it gives this error ..... same as I had before ...... for some reason it will not pick up in grub2 ......

question now is ..... will the boot loader be trash ..... now ...... 
( this is where you wish you kept a copy )


Seems ok though as its not created a new cfg ..... this is the old one its kept ....

```

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod reiserfs
set root='(/dev/sdb,msdos4)'
search --no-floppy --fs-uuid --set=root eacba95e-305a-4f1c-98e6-9d0ae32060c0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod reiserfs
set root='(/dev/sdb,msdos4)'
search --no-floppy --fs-uuid --set=root eacba95e-305a-4f1c-98e6-9d0ae32060c0
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod reiserfs
set root='(/dev/sdb,msdos4)'
search --no-floppy --fs-uuid --set=root eacba95e-305a-4f1c-98e6-9d0ae32060c0
insmod png
if background_image /boot/grub/moreblue-orbit-grub1.png; then
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-9-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sdb,msdos4)'
    search --no-floppy --fs-uuid --set=root eacba95e-305a-4f1c-98e6-9d0ae32060c0
    linux    /boot/vmlinuz-2.6.38-9-generic root=UUID=eacba95e-305a-4f1c-98e6-9d0ae32060c0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-9-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-9-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sdb,msdos4)'
    search --no-floppy --fs-uuid --set=root eacba95e-305a-4f1c-98e6-9d0ae32060c0
    echo    'Loading Linux 2.6.38-9-generic ...'
    linux    /boot/vmlinuz-2.6.38-9-generic root=UUID=eacba95e-305a-4f1c-98e6-9d0ae32060c0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-9-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sdb,msdos4)'
    search --no-floppy --fs-uuid --set=root eacba95e-305a-4f1c-98e6-9d0ae32060c0
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=eacba95e-305a-4f1c-98e6-9d0ae32060c0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sdb,msdos4)'
    search --no-floppy --fs-uuid --set=root eacba95e-305a-4f1c-98e6-9d0ae32060c0
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=eacba95e-305a-4f1c-98e6-9d0ae32060c0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sdb,msdos4)'
    search --no-floppy --fs-uuid --set=root eacba95e-305a-4f1c-98e6-9d0ae32060c0
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=eacba95e-305a-4f1c-98e6-9d0ae32060c0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sdb,msdos4)'
    search --no-floppy --fs-uuid --set=root eacba95e-305a-4f1c-98e6-9d0ae32060c0
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=eacba95e-305a-4f1c-98e6-9d0ae32060c0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sdb,msdos4)'
    search --no-floppy --fs-uuid --set=root eacba95e-305a-4f1c-98e6-9d0ae32060c0
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=eacba95e-305a-4f1c-98e6-9d0ae32060c0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sdb,msdos4)'
    search --no-floppy --fs-uuid --set=root eacba95e-305a-4f1c-98e6-9d0ae32060c0
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=eacba95e-305a-4f1c-98e6-9d0ae32060c0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sdb,msdos4)'
    search --no-floppy --fs-uuid --set=root eacba95e-305a-4f1c-98e6-9d0ae32060c0
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=eacba95e-305a-4f1c-98e6-9d0ae32060c0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sdb,msdos4)'
    search --no-floppy --fs-uuid --set=root eacba95e-305a-4f1c-98e6-9d0ae32060c0
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=eacba95e-305a-4f1c-98e6-9d0ae32060c0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sdb,msdos4)'
    search --no-floppy --fs-uuid --set=root eacba95e-305a-4f1c-98e6-9d0ae32060c0
    linux    /boot/vmlinuz-2.6.35-10-generic root=UUID=eacba95e-305a-4f1c-98e6-9d0ae32060c0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sdb,msdos4)'
    search --no-floppy --fs-uuid --set=root eacba95e-305a-4f1c-98e6-9d0ae32060c0
    echo    'Loading Linux 2.6.35-10-generic ...'
    linux    /boot/vmlinuz-2.6.35-10-generic root=UUID=eacba95e-305a-4f1c-98e6-9d0ae32060c0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sdb,msdos4)'
    search --no-floppy --fs-uuid --set=root eacba95e-305a-4f1c-98e6-9d0ae32060c0
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=eacba95e-305a-4f1c-98e6-9d0ae32060c0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sdb,msdos4)'
    search --no-floppy --fs-uuid --set=root eacba95e-305a-4f1c-98e6-9d0ae32060c0
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=eacba95e-305a-4f1c-98e6-9d0ae32060c0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sdb,msdos4)'
    search --no-floppy --fs-uuid --set=root eacba95e-305a-4f1c-98e6-9d0ae32060c0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sdb,msdos4)'
    search --no-floppy --fs-uuid --set=root eacba95e-305a-4f1c-98e6-9d0ae32060c0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 9.04, kernel 2.6.28-16-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root c2db1822-24aa-47e5-9d87-504f34b10e44
    linux /boot/vmlinuz-2.6.28-16-generic root=UUID=c2db1822-24aa-47e5-9d87-504f34b10e44 ro quiet splash
    initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root c2db1822-24aa-47e5-9d87-504f34b10e44
    linux /boot/vmlinuz-2.6.28-16-generic root=UUID=c2db1822-24aa-47e5-9d87-504f34b10e44 ro single
    initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root c2db1822-24aa-47e5-9d87-504f34b10e44
    linux /boot/vmlinuz-2.6.28-15-generic root=UUID=c2db1822-24aa-47e5-9d87-504f34b10e44 ro quiet splash
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root c2db1822-24aa-47e5-9d87-504f34b10e44
    linux /boot/vmlinuz-2.6.28-15-generic root=UUID=c2db1822-24aa-47e5-9d87-504f34b10e44 ro single
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-14-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root c2db1822-24aa-47e5-9d87-504f34b10e44
    linux /boot/vmlinuz-2.6.28-14-generic root=UUID=c2db1822-24aa-47e5-9d87-504f34b10e44 ro quiet splash
    initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root c2db1822-24aa-47e5-9d87-504f34b10e44
    linux /boot/vmlinuz-2.6.28-14-generic root=UUID=c2db1822-24aa-47e5-9d87-504f34b10e44 ro single
    initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root c2db1822-24aa-47e5-9d87-504f34b10e44
    linux /boot/vmlinuz-2.6.28-13-generic root=UUID=c2db1822-24aa-47e5-9d87-504f34b10e44 ro quiet splash
    initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root c2db1822-24aa-47e5-9d87-504f34b10e44
    linux /boot/vmlinuz-2.6.28-13-generic root=UUID=c2db1822-24aa-47e5-9d87-504f34b10e44 ro single
    initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root c2db1822-24aa-47e5-9d87-504f34b10e44
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=c2db1822-24aa-47e5-9d87-504f34b10e44 ro quiet splash
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root c2db1822-24aa-47e5-9d87-504f34b10e44
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=c2db1822-24aa-47e5-9d87-504f34b10e44 ro single
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-3-rt (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root c2db1822-24aa-47e5-9d87-504f34b10e44
    linux /boot/vmlinuz-2.6.28-3-rt root=UUID=c2db1822-24aa-47e5-9d87-504f34b10e44 ro quiet splash
    initrd /boot/initrd.img-2.6.28-3-rt
}
menuentry "Ubuntu 9.04, kernel 2.6.28-3-rt (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root c2db1822-24aa-47e5-9d87-504f34b10e44
    linux /boot/vmlinuz-2.6.28-3-rt root=UUID=c2db1822-24aa-47e5-9d87-504f34b10e44 ro single
    initrd /boot/initrd.img-2.6.28-3-rt
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root c2db1822-24aa-47e5-9d87-504f34b10e44
    linux /boot/memtest86+.bin 
}
menuentry "Kanotix64 GNU/Linux, with Linux 2.6.38-7-generic (on /dev/sda2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root b0ee1075-8818-4316-ae52-c2631773cf0d
    linux /boot/vmlinuz-2.6.38-7-generic root=UUID=b0ee1075-8818-4316-ae52-c2631773cf0d ro quiet splash
    initrd /boot/initrd.img-2.6.38-7-generic
}
menuentry "ArchBang Linux (on /dev/sda4)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 6c8e8a35-6ca5-458a-be34-5867d3ec892a
    linux /boot/vmlinuz26 root=/dev/disk/by-uuid/6c8e8a35-6ca5-458a-be34-5867d3ec892a ro quiet resume=/dev/sda5
    initrd /boot/kernel26.img
}
menuentry "ArchBang Linux Fallback (on /dev/sda4)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 6c8e8a35-6ca5-458a-be34-5867d3ec892a
    linux /boot/vmlinuz26 root=/dev/disk/by-uuid/6c8e8a35-6ca5-458a-be34-5867d3ec892a ro
    initrd /boot/kernel26-fallback.img
}
menuentry "Exton-Slack (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root cc4550ca-559a-4461-a7a1-e04469e97c29
    linux /boot/vmlinuz root=/dev/sda6 ro append = "3 vga = 791
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root 28bfe950-cadb-4bc7-bfb2-9e96b2bc0c93
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=28bfe950-cadb-4bc7-bfb2-9e96b2bc0c93 ro quiet splash
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root 28bfe950-cadb-4bc7-bfb2-9e96b2bc0c93
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=28bfe950-cadb-4bc7-bfb2-9e96b2bc0c93 ro single
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sdb2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod reiserfs
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root 28bfe950-cadb-4bc7-bfb2-9e96b2bc0c93
    linux /boot/memtest86+.bin 
}
menuentry "Linux Mint 9, 2.6.32-24-generic (/dev/sdb5) (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root dbabc73e-b72f-46ce-8fa7-e137a0e73c06
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=dbabc73e-b72f-46ce-8fa7-e137a0e73c06 ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Linux Mint 9, 2.6.32-24-generic (/dev/sdb5) -- recovery mode (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root dbabc73e-b72f-46ce-8fa7-e137a0e73c06
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=dbabc73e-b72f-46ce-8fa7-e137a0e73c06 ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sdb5) (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root dbabc73e-b72f-46ce-8fa7-e137a0e73c06
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=dbabc73e-b72f-46ce-8fa7-e137a0e73c06 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sdb5) -- recovery mode (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root dbabc73e-b72f-46ce-8fa7-e137a0e73c06
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=dbabc73e-b72f-46ce-8fa7-e137a0e73c06 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 8 Helena, linux 2.6.31-20-generic (/dev/sdd8) (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos7)'
    search --no-floppy --fs-uuid --set=root 13ab2ccf-7048-49bb-aa29-221cd138957b
    linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sdd8 ro quiet splash
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Linux Mint 8 Helena, linux 2.6.31-20-generic (recovery mode) (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos7)'
    search --no-floppy --fs-uuid --set=root 13ab2ccf-7048-49bb-aa29-221cd138957b
    linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sdd8 ro single
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Linux Mint 8 Helena, linux 2.6.31-19-generic (/dev/sdd8) (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos7)'
    search --no-floppy --fs-uuid --set=root 13ab2ccf-7048-49bb-aa29-221cd138957b
    linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sdd8 ro quiet splash
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Linux Mint 8 Helena, linux 2.6.31-19-generic (recovery mode) (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos7)'
    search --no-floppy --fs-uuid --set=root 13ab2ccf-7048-49bb-aa29-221cd138957b
    linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sdd8 ro single
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Linux Mint 9 Isadora, 2.6.32-27-generic (/dev/sdb8) (on /dev/sdb8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos8)'
    search --no-floppy --fs-uuid --set=root 4a7f0a74-f218-4692-98db-c0177b3a6923
    linux /boot/vmlinuz-2.6.32-27-generic root=UUID=4a7f0a74-f218-4692-98db-c0177b3a6923 ro quiet splash
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Linux Mint 9 Isadora, 2.6.32-27-generic (/dev/sdb8) -- recovery mode (on /dev/sdb8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos8)'
    search --no-floppy --fs-uuid --set=root 4a7f0a74-f218-4692-98db-c0177b3a6923
    linux /boot/vmlinuz-2.6.32-27-generic root=UUID=4a7f0a74-f218-4692-98db-c0177b3a6923 ro single
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Linux Mint 9 Isadora, 2.6.32-21-generic (/dev/sdb8) (on /dev/sdb8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos8)'
    search --no-floppy --fs-uuid --set=root 4a7f0a74-f218-4692-98db-c0177b3a6923
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=4a7f0a74-f218-4692-98db-c0177b3a6923 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9 Isadora, 2.6.32-21-generic (/dev/sdb8) -- recovery mode (on /dev/sdb8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos8)'
    search --no-floppy --fs-uuid --set=root 4a7f0a74-f218-4692-98db-c0177b3a6923
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=4a7f0a74-f218-4692-98db-c0177b3a6923 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "LinuxMint GNU/Linux, with Linux 2.6.32-5-amd64 (on /dev/sdc12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos12)'
    search --no-floppy --fs-uuid --set=root e53e12d7-aedd-492c-9c11-c1ae3337b850
    linux /boot/vmlinuz-2.6.32-5-amd64 root=UUID=e53e12d7-aedd-492c-9c11-c1ae3337b850 ro quiet
    initrd /boot/initrd.img-2.6.32-5-amd64
}
menuentry "LinuxMint GNU/Linux, with Linux 2.6.32-5-amd64 (recovery mode) (on /dev/sdc12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos12)'
    search --no-floppy --fs-uuid --set=root e53e12d7-aedd-492c-9c11-c1ae3337b850
    linux /boot/vmlinuz-2.6.32-5-amd64 root=UUID=e53e12d7-aedd-492c-9c11-c1ae3337b850 ro single
    initrd /boot/initrd.img-2.6.32-5-amd64
}
menuentry "Kanotix GNU/Linux, with Linux 3.0.0-1-686-pae (on /dev/sdc13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos13)'
    search --no-floppy --fs-uuid --set=root 11a3e9c3-5841-4590-b0e9-5291b8c229b8
    linux /boot/vmlinuz-3.0.0-1-686-pae root=/dev/sdb13 ro quiet splash
}
menuentry "Kanotix GNU/Linux, with Linux 3.0.0-1-686-pae (recovery mode) (on /dev/sdc13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos13)'
    search --no-floppy --fs-uuid --set=root 11a3e9c3-5841-4590-b0e9-5291b8c229b8
    linux /boot/vmlinuz-3.0.0-1-686-pae root=/dev/sdb13 ro single
}
menuentry "Kanotix GNU/Linux, with Linux 3.0.0-1-486 (on /dev/sdc13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos13)'
    search --no-floppy --fs-uuid --set=root 11a3e9c3-5841-4590-b0e9-5291b8c229b8
    linux /boot/vmlinuz-3.0.0-1-486 root=/dev/sdb13 ro quiet splash
}
menuentry "Kanotix GNU/Linux, with Linux 3.0.0-1-486 (recovery mode) (on /dev/sdc13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos13)'
    search --no-floppy --fs-uuid --set=root 11a3e9c3-5841-4590-b0e9-5291b8c229b8
    linux /boot/vmlinuz-3.0.0-1-486 root=/dev/sdb13 ro single
}
menuentry "Kanotix GNU/Linux, with Linux 2.6.38-7-generic (on /dev/sdc13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos13)'
    search --no-floppy --fs-uuid --set=root 11a3e9c3-5841-4590-b0e9-5291b8c229b8
    linux /boot/vmlinuz-2.6.38-7-generic root=UUID=11a3e9c3-5841-4590-b0e9-5291b8c229b8 ro quiet splash
    initrd /boot/initrd.img-2.6.38-7-generic
}
menuentry "Kanotix GNU/Linux, with Linux 2.6.38-7-generic (recovery mode) (on /dev/sdc13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos13)'
    search --no-floppy --fs-uuid --set=root 11a3e9c3-5841-4590-b0e9-5291b8c229b8
    linux /boot/vmlinuz-2.6.38-7-generic root=UUID=11a3e9c3-5841-4590-b0e9-5291b8c229b8 ro single
    initrd /boot/initrd.img-2.6.38-7-generic
}
menuentry "Kanotix GNU/Linux, with Linux 2.6.32-5-486 (on /dev/sdc13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos13)'
    search --no-floppy --fs-uuid --set=root 11a3e9c3-5841-4590-b0e9-5291b8c229b8
    linux /boot/vmlinuz-2.6.32-5-486 root=/dev/sdb13 ro quiet splash
}
menuentry "Kanotix GNU/Linux, with Linux 2.6.32-5-486 (recovery mode) (on /dev/sdc13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos13)'
    search --no-floppy --fs-uuid --set=root 11a3e9c3-5841-4590-b0e9-5291b8c229b8
    linux /boot/vmlinuz-2.6.32-5-486 root=/dev/sdb13 ro single
}
menuentry "Exton-Slack (on /dev/sdc14)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos14)'
    search --no-floppy --fs-uuid --set=root 9a60d4a4-1db6-4f0c-aa2b-7956959aefac
    linux /boot/vmlinuz root=/dev/sdb14 ro append = "3 vga = 791
}
menuentry "LinuxMint GNU/Linux, with Linux 3.0.0-1-686-pae (on /dev/sdc16)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos16)'
    search --no-floppy --fs-uuid --set=root 0acb7a0c-a265-4a54-9316-3feaf505c02c
    linux /boot/vmlinuz-3.0.0-1-686-pae root=UUID=d9b8f176-faa5-4bd0-acae-76f4d37f2ad1 ro quiet
    initrd /boot/initrd.img-3.0.0-1-686-pae
}
menuentry "LinuxMint GNU/Linux, with Linux 3.0.0-1-686-pae (recovery mode) (on /dev/sdc16)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos16)'
    search --no-floppy --fs-uuid --set=root 0acb7a0c-a265-4a54-9316-3feaf505c02c
    linux /boot/vmlinuz-3.0.0-1-686-pae root=UUID=d9b8f176-faa5-4bd0-acae-76f4d37f2ad1 ro single
    initrd /boot/initrd.img-3.0.0-1-686-pae
}
menuentry "LinuxMint GNU/Linux, with Linux 2.6.39-2-686-pae (on /dev/sdc16)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos16)'
    search --no-floppy --fs-uuid --set=root 0acb7a0c-a265-4a54-9316-3feaf505c02c
    linux /boot/vmlinuz-2.6.39-2-686-pae root=UUID=d9b8f176-faa5-4bd0-acae-76f4d37f2ad1 ro quiet
    initrd /boot/initrd.img-2.6.39-2-686-pae
}
menuentry "LinuxMint GNU/Linux, with Linux 2.6.39-2-686-pae (recovery mode) (on /dev/sdc16)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos16)'
    search --no-floppy --fs-uuid --set=root 0acb7a0c-a265-4a54-9316-3feaf505c02c
    linux /boot/vmlinuz-2.6.39-2-686-pae root=UUID=d9b8f176-faa5-4bd0-acae-76f4d37f2ad1 ro single
    initrd /boot/initrd.img-2.6.39-2-686-pae
}
menuentry "LinuxMint GNU/Linux, with Linux 2.6.32-5-686 (on /dev/sdc16)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos16)'
    search --no-floppy --fs-uuid --set=root 0acb7a0c-a265-4a54-9316-3feaf505c02c
    linux /boot/vmlinuz-2.6.32-5-686 root=UUID=d9b8f176-faa5-4bd0-acae-76f4d37f2ad1 ro quiet
    initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "LinuxMint GNU/Linux, with Linux 2.6.32-5-686 (recovery mode) (on /dev/sdc16)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos16)'
    search --no-floppy --fs-uuid --set=root 0acb7a0c-a265-4a54-9316-3feaf505c02c
    linux /boot/vmlinuz-2.6.32-5-686 root=UUID=d9b8f176-faa5-4bd0-acae-76f4d37f2ad1 ro single
    initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "Kanotix GNU/Linux, with Linux 2.6.38-7-generic (on /dev/sdc17)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos17)'
    search --no-floppy --fs-uuid --set=root cb5e2789-a3b9-40bf-94b7-942cde4bfe07
    linux /boot/vmlinuz-2.6.38-7-generic root=UUID=cb5e2789-a3b9-40bf-94b7-942cde4bfe07 ro quiet splash
    initrd /boot/initrd.img-2.6.38-7-generic
}
menuentry "Kanotix64 GNU/Linux, with Linux 2.6.38-7-generic (on /dev/sdc2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos2)'
    search --no-floppy --fs-uuid --set=root 04c1dceb-f5e0-42b6-8e94-c5727f9230c0
    linux /boot/vmlinuz-2.6.38-7-generic root=UUID=b0ee1075-8818-4316-ae52-c2631773cf0d ro quiet splash
    initrd /boot/initrd.img-2.6.38-7-generic
}
menuentry "Ubuntu, with Linux 3.0-0-generic (on /dev/sdc7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos7)'
    search --no-floppy --fs-uuid --set=root bf53f9c4-89d2-4238-82a0-7de304e296ed
    linux /boot/vmlinuz-3.0-0-generic root=UUID=bf53f9c4-89d2-4238-82a0-7de304e296ed ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0-0-generic
}
menuentry "Ubuntu, with Linux 3.0-0-generic (recovery mode) (on /dev/sdc7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos7)'
    search --no-floppy --fs-uuid --set=root bf53f9c4-89d2-4238-82a0-7de304e296ed
    linux /boot/vmlinuz-3.0-0-generic root=UUID=bf53f9c4-89d2-4238-82a0-7de304e296ed ro single nomodeset
    initrd /boot/initrd.img-3.0-0-generic
}
menuentry "Ubuntu, with Linux 2.6.39-3-generic (on /dev/sdc7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos7)'
    search --no-floppy --fs-uuid --set=root bf53f9c4-89d2-4238-82a0-7de304e296ed
    linux /boot/vmlinuz-2.6.39-3-generic root=UUID=bf53f9c4-89d2-4238-82a0-7de304e296ed ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.39-3-generic
}
menuentry "Ubuntu, with Linux 2.6.39-3-generic (recovery mode) (on /dev/sdc7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos7)'
    search --no-floppy --fs-uuid --set=root bf53f9c4-89d2-4238-82a0-7de304e296ed
    linux /boot/vmlinuz-2.6.39-3-generic root=UUID=bf53f9c4-89d2-4238-82a0-7de304e296ed ro single nomodeset
    initrd /boot/initrd.img-2.6.39-3-generic
}
menuentry "Ubuntu, with Linux 2.6.38-9-generic (on /dev/sdc7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos7)'
    search --no-floppy --fs-uuid --set=root bf53f9c4-89d2-4238-82a0-7de304e296ed
    linux /boot/vmlinuz-2.6.38-9-generic root=UUID=bf53f9c4-89d2-4238-82a0-7de304e296ed ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-9-generic
}
menuentry "Ubuntu, with Linux 2.6.38-9-generic (recovery mode) (on /dev/sdc7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos7)'
    search --no-floppy --fs-uuid --set=root bf53f9c4-89d2-4238-82a0-7de304e296ed
    linux /boot/vmlinuz-2.6.38-9-generic root=UUID=bf53f9c4-89d2-4238-82a0-7de304e296ed ro single nomodeset
    initrd /boot/initrd.img-2.6.38-9-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

```Time to reboot and see what's changed ..... if anything ?

But I certainly get the feeing the boot CD and installer will not work on a USB HDD

how can it be altered ? ....... 

or how do I write it into the other boot loader ..... Grub 1

the one I have that works 

root   (hd0,3)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/6c8e8a35-6ca5-458a-be34-5867d3ec892a ro quiet resume=/dev/sda5
initrd /boot/kernel26.img

---

### Post by cbowman57 on 2011-08-28
Do you have a working grub2 menu entry for an example?

---

### Post by 23dornot23d on 2011-08-28
```

menuentry "ArchBang Linux (on /dev/sda4)" --class gnu-linux --class gnu --class os { 
    insmod part_msdos 
    insmod ext2 
    set root='(/dev/sda,msdos4)' 
    search --no-floppy --fs-uuid --set=root 6c8e8a35-6ca5-458a-be34-5867d3ec892a 
    linux /boot/vmlinuz26 root=/dev/disk/by-uuid/6c8e8a35-6ca5-458a-be34-5867d3ec892a ro quiet resume=/dev/sda5 
    initrd /boot/kernel26.img 
}


```That works on sda4 as a grub 2 entry ......

I will go onto sdb9 and grab the uuid .... for it ....

/dev/sdb9             10233400   1742052   7971516  18% /media/21e5450c-cc14-4631-81d5-095b25659bca


so by rights ..... it should look something like this .....

```

menuentry "ArchBang Linux (on /dev/sdb9)" --class gnu-linux --class gnu --class os { 
    insmod part_msdos 
    insmod ext2 
    set root='(/dev/sdb,msdos9)' 
    search --no-floppy --fs-uuid --set=root  21e5450c-cc14-4631-81d5-095b25659bca
    linux /boot/vmlinuz26 root=/dev/disk/by-uuid/21e5450c-cc14-4631-81d5-095b25659bca ro quiet resume=/dev/sdb10
    initrd /boot/kernel26.img 
}


```so will it work adding this as a custom entry

```

#! /bin/sh -e
echo "Adding custom boot entry(s)" >&2
 cat << EOF
menuentry "ArchBang Linux (on /dev/sdb9)" --class gnu-linux --class gnu --class os { 
    insmod part_msdos 
    insmod ext2 
    set root='(/dev/sdb,msdos9)' 
    search --no-floppy --fs-uuid --set=root  21e5450c-cc14-4631-81d5-095b25659bca
    linux /boot/vmlinuz26 root=/dev/disk/by-uuid/21e5450c-cc14-4631-81d5-095b25659bca ro quiet resume=/dev/sdb10
    initrd /boot/kernel26.img 
}
menuentry "Chainload 
Windows Vista" {
    set root=(hd0,1)
    chainloader +1
}
EOF

```Ok well I have a way forward .......

once I sort out how to get update-grub to work ...... 

I have a empty boot folder on sdb9 ..... so I think this is the problem .......

What I need to do is make a copy of the existing boot for sdb7 ....... so if I write it
to a flash drive now .... all should be well .......

Then I can continue in relative ,,, safety ...... 


or in Grub1

or how do I write it into the other boot loader ..... Grub 1

the one I have that works 

root   (hd1,9
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/21e5450c-cc14-4631-81d5-095b25659bca ro quiet resume=/dev/sdb5
initrd /boot/kernel26.img                                                                                               __________________




----------------------------------------------------------------------------



OK FResh start ,,,,, due to the boot folder being empty ..... I re-installed .....
so have a different id now for the partition ....

also a new Grub ..... and Menu.1st

```

# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,1)
#  /dev/sda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  http://wiki.archlinux.org/index.php/GRUB#Framebuffer_Resolution 

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) ArchBang Linux
title  ArchBang Linux
root   (hd1,9)
kernel /vmlinuz26 root=/dev/disk/by-uuid/03f1762b-8fec-4452-87b3-875c70579451 ro quiet resume=/dev/sdb6   
initrd /kernel26.img

# (1) ArchBang Linux fallback (useful if you change your hard disk/mainboard)
title  ArchBang Linux Fallback
root   (hd1,9)
kernel /vmlinuz26 root=/dev/disk/by-uuid/03f1762b-8fec-4452-87b3-875c70579451 ro
initrd /kernel26-fallback.img

# (2) Optional entry for Windoze
#title Windoze
#rootnoverify (hd0,0)
#makeactive
#chainloader +1

```But it still gives the errors if I try to update grub2 ..... so it was not the empty boot folder.

```

root@keith-MS-7181:/home/keith# update-grub
Generating grub.cfg ...
Found background image: moreblue-orbit-grub1.png
Found linux image: /boot/vmlinuz-2.6.38-9-generic
Found initrd image: /boot/initrd.img-2.6.38-9-generic
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.35-27-generic
Found initrd image: /boot/initrd.img-2.6.35-27-generic
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-10-generic
Found initrd image: /boot/initrd.img-2.6.35-10-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 9.04 (9.04) on /dev/sda1
Found Debian GNU/Linux (6.0.1) on /dev/sda2
Found Arch on /dev/sda4
Found Slackware Linux (Slackware 13.37.0) on /dev/sda6
Found Linux Mint 9 Isadora (9) on /dev/sdb5
Found Linux Mint 8 Helena - Main Edition (8) on /dev/sdb7
Found Linux Mint 9 Isadora (9) on /dev/sdb8
Found Arch1 on /dev/sdb9
error: out of memory.
error: syntax error.
error: Incorrect command.
error: syntax error.
error: line no: 536
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
done
root@keith-MS-7181:/home/keith# 


```I have tried manually with both Grub 1
and with Grub 2 

to get the USB to boot neither recognize the partition as existing ..... !!!

```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb4             27444404  16530936  10913468  61% /
none                    244048       708    243340   1% /dev
none                    254000       168    253832   1% /dev/shm
none                    254000       216    253784   1% /var/run
none                    254000         0    254000   0% /var/lock
/dev/sdb9             10233400   1742064   7971504  18% /media/03f1762b-8fec-4452-87b3-875c70579451
/dev/sdb5             19805208  17830700    968444  95% /media/dbabc73e-b72f-46ce-8fa7-e137a0e73c06_
/dev/sdb7             21537012  18552720   1890268  91% /media/13ab2ccf-7048-49bb-aa29-221cd138957b_
/dev/sdb10             1049204     37684    958224   4% /media/b696df65-05f3-493a-9a0f-d1c50421aad8
/dev/sdb1            312484288 218472544  94011744  70% /media/Elements_
/dev/sdb8              4219708   3629252    376084  91% /media/4a7f0a74-f218-4692-98db-c0177b3a6923_
/dev/sdb11             8171192    149312   7606804   2% /media/9a3669ab-fbb0-40bf-9320-a23ef1a5dd3c
/dev/sr0                541310    541310         0 100% /media/ARCH_201102
keith@keith-MS-7181:~$ 


```

---

### Post by cbowman57 on 2011-08-28
If you installed grub2-bios & common + os-prober from AUR this is my update-grub script

```
#!/bin/bash
grub-mkconfig -o /boot/grub/grub.cfg

exit 0
```

---

### Post by cbowman57 on 2011-08-28
This distro is a tweaker's dream, you can edit the /etc/makepkg.conf file and make it compile for your architecture

[https://wiki.archlinux.org/index.php/Makepkg](https://wiki.archlinux.org/index.php/Makepkg)
[https://wiki.archlinux.org/index.php/Linux-ck](https://wiki.archlinux.org/index.php/Linux-ck)

for installing packages from AUR I've found I like to use makepkg -sci , that downloads dependencies (if possible), cleans up after itself & installs like pacman -U.

---

### Post by 23dornot23d on 2011-08-29
Ok will try them out ...... seems that there is a problem with installing to USB

but will give it another go .....

Also will try grub 2 out on Arch ....

---

### Post by cbowman57 on 2011-08-29
Oh, that doesn't sound good.

---

### Post by 23dornot23d on 2011-08-29
Lols ..... everything is running ok ...... after using grub2 again .....

But I did have Grub one on the Desktop computer

and Grub 2 on the USB  Drive which worked out quite well .....

Thing with adding Arch to the USB ..... it messed it up last time on another
completely different USB ....

and its had a go again with this one ..... not filling me with confidence in how it
sees them ...... as I showed earlier it thinks there is a problem with every USB
I have given it ..... where no other OS has ..... so either all the other OS are wrong
and seeing my USB's as being ok ....

Or Arch [[COLOR=Red]**Cfdisk**[/COLOR]]("https://bbs.archlinux.org/viewtopic.php?id=105106") is right and the partition does start after the end of the drive ....... 

Just finally put everything back to normal again ...... it does make me think
each time I have tried this with Arch on a USB its messed it up ...

and reading the posts about USB's leads me to believe some work is required here to
sort things out properly ....

Back to normal now ..... took a few hours sorting the boot loaders out .....

Remind me never to install Arch to a USB HDD ..... 

Its ok on the main drive - no problems .....

Cfdisk ...... seems to be the problem here with USB's .

( Always keep a back up of your Grub on a Flash drive )
( Easy as grub-install /dev/sdbc ) >>> ( if sdbc is your flash drive )
( Put it somewhere safe and update it - if you add more systems )

I have always used gparted and had no problems.

Loaded Sabayon up this morning too ( so something else to have a go with now )

Arch is running fine on my main drive and I am going to leave it that way ....

Anyone wanting to continue this thread to work out what the problem with

USBs and CFdisk  ...... as I would be quite interested to know what could be

done differently to get it to work properly on a USB HDD

---

### Post by cbowman57 on 2011-08-29
I hope you have better luck with Sabayon than I did. :)

---

### Post by 23dornot23d on 2011-08-29
I just loaded a older version in of Sabayon and tried emerge ....... lols .....
( forgot the trouble you had with it ..... its another thats history now )

Am sticking with Arch ...... runs so smooth on this old machine ...... its just 
re-vitalised a machine I hardly ever used to one I cannot help but to choose

Arch ...... :) ....... each and every time now .....

---

### Post by cbowman57 on 2011-08-29
Yeah, I have to admit, Arch w/G-S just seems so right.

So are you using it on the desktop or the laptop?  I've scattered some links throughout this thread you might find useful when you get the time to look at them. graysky has a repo for current kernels compiled for different architecture, the modifications of the makepkg.conf to generate packages specific to your hardware (As far as I know it's only applied to packages installed via AUR but I'm not sure) If you use Firefox the firefox-tmpfs daemon is pretty nice too.

The hardware in the computer I use is pretty capable but no other distro has been this responsive. I don't think I could go back to anything else if I wanted to now that I've sampled this. :)

---

### Post by mips on 2011-08-29
> **cbowman57 said:**
> I don't think I could go back to anything else if I wanted to now that I've sampled this. :)

That tends to happen, once hooked you don't stray.

---

### Post by 23dornot23d on 2011-08-29
> 
So are you using it on the desktop or the laptop?
I am on the desktop machine most of the time now ..... even doing 3D on it last night
which is unheard of .... because it was not responsive enough, before Arch ....

[IMG]http://img828.imageshack.us/img828/9845/screenshot2pz.jpg[/IMG]

I was looking at the gears on the clock background I have and started to play ......
see if I could re-create the main gear easily .....

[IMG]http://img845.imageshack.us/img845/8551/screenshot3iu.jpg[/IMG]


Working like clockwork now ......

[IMG]http://img10.imageshack.us/img10/5359/screenshot5rw.jpg[/IMG]

---

### Post by cbowman57 on 2011-08-29
Darn it mips, the first one is always free. :lol:

---

### Post by cbowman57 on 2011-08-29
> **23dornot23d said:**
> I am on the desktop machine most of the time now ..... even doing 3D on it last night
which is unheard of .... because it was not responsive enough,

I was looking at the gears on the clock background I have and started to play ......
see if I could re-create it easily .....

You use blender right?  Here's a wicked thought, modify that makepkg.conf and compile a version specific to that hardware. [https://aur.archlinux.org/packages.php?O=0&K=blender&do_Search=Go](https://aur.archlinux.org/packages.php?O=0&K=blender&do_Search=Go)

This is the essential change:
```
CFLAGS="-march=native -O2 -pipe -fstack-protector --param=ssp-buffer-size=4 -D_FORTIFY_SOURCE=2"
CXXFLAGS="${CFLAGS}"
#CFLAGS="-march=x86-64 -mtune=generic -O2 -pipe -fstack-protector --param=ssp-buffer-size=4 -D_FORTIFY_SOURCE=2"
#CXXFLAGS="-march=x86-64 -mtune=generic -O2 -pipe -fstack-protector --param=ssp-buffer-size=4 -D_FORTIFY_SOURCE=2"
```

I think it's great that it extends the uefulness of older hardware, same can be said of all distros I guess but this one really takes the cake IMO.

---

### Post by 23dornot23d on 2011-08-29
Woah .... nice cheers ..... some plugins and extra packages for using Blender .....

never thought to look ....... thanks ..... :)

Will have a good search through now ..... mine was customized for the old Blender ..... but its
all new now ..... so starting again with the new one  .....

I guess building everything for this system will make it fly ..... so will carry on along this path now.

---

### Post by cbowman57 on 2011-08-29
> **23dornot23d said:**
> Woah .... nice cheers ..... some plugins and extra packages for using Blender .....

never thought to look ....... thanks ..... :)

Will have a good search through now ..... mine was customized for the old Blender ..... but its
all new now ..... so starting again with the new one  .....

AUR is a veritable Pandora's box.  Imagine the trouble we can get into now. :)

I don't see myself getting bored with this any time soon.

---

### Post by 23dornot23d on 2011-08-29
Really looking forward to getting some things done on it now ...... winter is coming and
I tend to get into photography editing.

Will have to look see what programs are in the repos ....

Cannot see this on there ....
[http://qtpfsgui.sourceforge.net/](http://qtpfsgui.sourceforge.net/)

[http://sourceforge.net/projects/qtpfsgui/files/qtpfsgui/1.9.3/qtpfsgui-1.9.3.tar.gz/download](http://sourceforge.net/projects/qtpfsgui/files/qtpfsgui/1.9.3/qtpfsgui-1.9.3.tar.gz/download)
got the source file here

qmake
make
make install

Hugin is though ( yaourt -S hugin )

---

### Post by cbowman57 on 2011-08-30
[http://www.archlinux.org/packages/community/i686/luminancehdr/](http://www.archlinux.org/packages/community/i686/luminancehdr/)

[http://pkgs.org/package/luminancehdr](http://pkgs.org/package/luminancehdr)

---

### Post by 23dornot23d on 2011-08-30
Cheers Chuck ...... 

Got Samba running last night - so I also have file sharing 
between the computers now ..... but using UBUNTU .... :)

Looked for System-Config-Samba on Arch and could not find it ...
and if I try adding Samba ..... it wants to remove things ....
as I say with Networks I am lost and would not want to loose my Internet on it now I have it ...

---

### Post by cbowman57 on 2011-08-30
Has to be some way to do it.  I don't have a network to test it on here.  What is it trying to remove is you add samba?

---

### Post by 23dornot23d on 2011-08-30
It comes up like this ,,,,


[root@archbang keith]# pacman -S samba
resolving dependencies...
looking for inter-conflicts...
:: ***_[gamin and fam]("http://www.google.ca/search?aq=f&sourceid=chrome&ie=UTF-8&q=gamin+and+fam")_*** are in conflict. Remove fam? [y/N]


[https://bbs.archlinux.org/viewtopic.php?id=66516](https://bbs.archlinux.org/viewtopic.php?id=66516)


***_[GAMIN]("https://wiki.archlinux.org/index.php/Gamin")_***

---

### Post by cbowman57 on 2011-08-30
Ok, was just looking at the wiki, seems that fam is deprecated so samba recommends gamin.

I'm not networked but I jumped on my other Arch installation, going to install gamin & see if it breaks anything on a non-samba system. :)

---

### Post by 23dornot23d on 2011-08-30
Yep I have got it in now ..... 


```

[root@archbang keith]# pacman -S samba
resolving dependencies...
looking for inter-conflicts...
:: gamin and fam are in conflict. Remove fam? [y/N] n
error: unresolvable package conflicts detected
error: failed to prepare transaction (conflicting dependencies)
:: gamin and fam are in conflict
[root@archbang keith]# 
[root@archbang keith]# pacman -Rd fam
checking dependencies...
error: failed to prepare transaction (could not satisfy dependencies)
:: thunar-vfs: requires fam
[root@archbang keith]# pacman -Rd thunar
checking dependencies...
error: failed to prepare transaction (could not satisfy dependencies)
:: thunar-archive-plugin: requires thunar
:: thunar-media-tags-plugin: requires thunar
[root@archbang keith]# pacman -S gamin
resolving dependencies...
looking for inter-conflicts...
:: gamin and fam are in conflict. Remove fam? [y/N] y

Remove (1): fam-2.7.0-16 [0.29 MB]

Total Removed Size:   0.29 MB

Targets (1): gamin-0.1.10-5 [0.04 MB]

Total Download Size:    0.04 MB
Total Installed Size:   0.20 MB

Proceed with installation? [Y/n] y
:: Retrieving packages from extra...
 gamin-0.1.10-5-i686      44.1K  151.8K/s 00:00:00 [----------------------] 100%
(1/1) checking package integrity                   [----------------------] 100%
(1/1) checking for file conflicts                  [----------------------] 100%
(1/1) removing fam                                 [----------------------] 100%
(1/1) installing gamin                             [----------------------] 100%
Optional dependencies for gamin
    python2: for the python module.
[root@archbang keith]# pacman -S thunar
warning: thunar-1.2.2-3 is up to date -- reinstalling
resolving dependencies...
looking for inter-conflicts...

Targets (1): thunar-1.2.2-3 [2.56 MB]

Total Download Size:    0.00 MB
Total Installed Size:   9.73 MB

Proceed with installation? [Y/n] y
(1/1) checking package integrity                   [----------------------] 100%
(1/1) checking for file conflicts                  [----------------------] 100%
(1/1) upgrading thunar                             [----------------------] 100%
[root@archbang keith]# pacman -S samba
resolving dependencies...
looking for inter-conflicts...

Targets (1): samba-3.6.0-8 [9.76 MB]

Total Download Size:    9.76 MB
Total Installed Size:   61.46 MB

Proceed with installation? [Y/n] y
:: Retrieving packages from extra...
 samba-3.6.0-8-i686        9.8M 1039.1K/s 00:00:10 [----------------------] 100%
(1/1) checking package integrity                   [----------------------] 100%
(1/1) checking for file conflicts                  [----------------------] 100%
(1/1) installing samba                             [----------------------] 100%
[root@archbang keith]# 


```Restarted the desktop now in KDE and everything is still working ok .....

Just this bit to do now .....

[http://ubuntuguide.net/createmodifydelete-samba-shares-with-system-config-sambagui-in-ubuntu-linux](http://ubuntuguide.net/createmodifydelete-samba-shares-with-system-config-sambagui-in-ubuntu-linux)

Wonder if there is a similar file for Arch for [[COLOR=Red]_*Samba*_[/COLOR]]("https://wiki.archlinux.org/index.php/Samba") setup

System-Config-Samba

the way things are I may be able to just grab the ubuntu smb.conf file that I set up that works and pull it into here now .....

/etc/samba/smb.conf

got it that worked .....

just had to change one thing in it ...... where it said **Ubuntu** ....... >>>> replaced it with **archbang**

basically was the hostname .....  ( found this in the /etc/rc.conf file .....)

and now my file sharing works from ARCH too ..... great another job done .... almost ....

Can see the laptop from the Desktop ..... Arch sees the Ubuntu Share ...

But not the other way around .....Ubuntu does not see the Arch Files yet

---

### Post by cbowman57 on 2011-08-31
Ok, I did an xorg or xf86 upgrade (guess it was yesterday morning) that hosed my system, fortunately I figured that one out.  Having the Testing repo on might not have been the brightest thing.

I did install gamin to replace fam though, haven't seemed to suffer any ill effects, obviously you haven't either judging by your progress.

Also, just installed the patched fgetty to replace agetty, much lighter than agetty.  I recommend you give it a try on the desktop. [https://wiki.archlinux.org/index.php/Improve_Boot_Performance#TTY_terminal_management](https://wiki.archlinux.org/index.php/Improve_Boot_Performance#TTY_terminal_management)

---

### Post by 23dornot23d on 2011-08-31
Did you clone it ..... hope you can get it back quickly .....


Ok me too I took a bit of a hit on performance ...... not that its bad ......
( also something wiped out two boot sectors ..... easily replaced ..... yet to work out why )

Two things happened yesterday ...... but I added so much stuff to do with video editing
and video recording as well as the network files and programs.

So what got added

samba
webmin ( not sure on this yet - a work in progress - sort of worries me a little )

openshot
pitivi
mplayer ( may have already been on but reinstalled anyway )
vlc
gtk-recordmydesktop ( there is a video I did on my homepage again - still getting blue )

possibly a couple of others cannot remember now ....... will add here if I do ....

What I have lost 50 meg of memory ...... now running at 318 Meg with Firefox open.

The graphics are not quite as crisp and sweet at opening as they were.

Conclusion ....... this happens with most systems once you start adding lots of software
but to have a fully working system ...... 

I need most of the programs above ..... some double up though ...... so If I were to
loose any ...... pitivi - possibly and openshot ....... as my videos on this machine are
going directly onto You-Tube now . ( was having to convert them before )

Maybe on the double monitor I will need Pitivi and openshot again ...... seems to be the size of the screen You-Tube has problems with ....... standard single monitor stuff may be ok for it to convert them properly.

Ok might try some tweaks later to get it flying again ....... ;)

---

### Post by cbowman57 on 2011-08-31
Yeah, I was able to recover it pretty quickly since I had a Clonezilla backup of one of them.  The one I prefer, on Raid0, wasn't so fortunate but I was able to correct it once I figured out a system.  It also pointed out a flaw in my backup script that I corrected last night.

The problem was the result of an xorg pacakge update from the testing repository, caused some type of error in the display manager, affected both installations.  The fix, su to root, nano /etc/pacman.conf, # out the tesing repo & run pacman -Syu, that will display the pkgs installed that are newer than what is in the repo.  After that it was a fairly simple matter of removing the bad ones by simply pacman -S pkgname until the offending packages were replaced.

Ok, don't know how much memory your machne has (you probably mentioned it, I forgot) but 2 enhancements I found useful that put some snap back in the system was readahead-fedora & firefox-tmpfs. Of course you're going to trade off available memory for performance but if you have it to spare it's worth it.

---

### Post by cbowman57 on 2011-08-31
Another recommendation. graysky builds some super kernels optimized for the cpu, noticed a big boost here. Unfortunately bfq is not quite ready in kernel 3.0 yet but I'm looking forward to trying that.

Here's the pertinent info for your pacman.conf file

```
[repo-ck]
Server = http://repo-ck.com/$arch
```

I'm running the kernel optimized for core2 and it is noticably faster.

---

### Post by 23dornot23d on 2011-08-31
Cheers for th info - will go through things tonight .....

> 
Ok, don't know how much memory your machne has (you probably mentioned  it, I forgot) but 2 enhancements I found useful that put some snap back  in the system was readahead-fedora & firefox-tmpfs. Of course you're  going to trade off available memory for performance but if you have it  to spare it's worth it.
[IMG]http://img21.imageshack.us/img21/2156/snapshot57a.jpg[/IMG]


Its 512 Meg Ram ..... but its ok ......

[*_**VIDEO**_*]("http://www.youtube.com/watch?v=PWmKk7jdzro") ......

Excuse the lag .... 

At the start ..... Wings3D + Blender is Running Firefox is running ..... also KDE and Gnome-Shell

Obviously gtk-recordmydesktop has to be running too to record it ......

This is a AMD _***[COLOR=Red][Sempron]("http://fr.wikipedia.org/wiki/AMD_Sempron")[/COLOR]***_ 3000+ computer single core ....


> 
The fix, su to root, nano /etc/pacman.conf, # out the tesing repo & [COLOR=Red]** run pacman -Syu, that will display the pkgs installed that are newer  than what is in the repo**[/COLOR].  After that it was a fairly simple matter of  removing the bad ones by simply pacman -S pkgname until the offending  packages were replaced.
Yep I like that part too ..... the time I had testing in and lost network wicd  ..... and a few other network programs were updated ...... 

But could quickly see - what were newer this way too ...........

I still have to get it onto the laptop which is dual core ....... but until I get it onto USB that is not
going to happen ..... as there is no main drive in my laptop .....

It just runs from USB drives I plug in ..... and boot from .....

---

### Post by cbowman57 on 2011-08-31
I think it's great that this is breathing new life back into that machine. :)

My first PC was a notebook, I had it upgraded to 6megs of RAM.. what a powerhouse that was. :lol:

---

### Post by 23dornot23d on 2011-08-31
I had stopped using this machine totally ..... was too slow with anything else really ....

other than Slackware ..... which is very similar by design - but less package management.

[URL="http://www.youtube.com/user/23dornot23d#p/a/u/1/WXLl-7Ba3y8"][COLOR=Red][U][I][B]
VIDEO[/B][/I][/U][/COLOR][/URL]


This is another short video ..... and it is still doing the one thing that does annoy me ....

The blue blocks everywhere on the back screen ..... its the only thing wrong and only appears in the gtk-recordmydesktop videos ......

I maybe should do one with my camera as it does ruin the whole thing ..... people are
going to believe that is what you see on the desktop - when it is not .....


Well as you say its saved a machine from getting covered in dust now ....

But I would love to see the performance on the dual core laptop I have.


May try one more time to get it onto a USB drive ...... but it is prone to mess the drive and
boot up ...... which takes me a lot of time to get back right again.

---

### Post by cbowman57 on 2011-08-31
Well, don't know if makes you feel any better but I get the same blue blocks the couple times I've tried to record mine too.  Seems to be connected to just abot any activities using the panel or dash. :(

So it's not your hardware that is the cause.

Looks like I did my downgrade recovery the hard way yesterday.  According to what I just read all you have to do is disbale testing and run pacman -Suu & that usually takes care of it.  Duh! :)

---

### Post by 23dornot23d on 2011-08-31
> 
According to what I just read all you have to do is disbale testing and run pacman -Suu & that usually takes care of it.
Thats good to know ..... will note it down ..... for reference .... if I do decide to start doing
more with this .....

Nice to have escape routes ..... ;)

Yep the Blue even web8upd mentioned it early on too .....

Could just be some tweaking needed in the gtk-recordmydesktop program ..... who knows :confused:

---

### Post by cbowman57 on 2011-08-31
Yeah, that's what I'm thinking, maybe mutter or clutter introduced a new set of problems to the recording software.  I get the same thing sporadically when I take screenshots too, but if I cancel and shoot again it usually clears up.  Strange.

---

### Post by 23dornot23d on 2011-08-31
Yep must admit - it does affect screen shots too ..... 

Not so much a problem there - as you see it straight away and get rid of it ......

If gtk-recordmydesktop is basically a stream of screenshots .....

Then maybe the heart of it lies there ...... possibly all comes from the same bit of code

Why just the back screen though ..... !!!

What is different ...... it all seems to be a series of Frames ..... and each one lights up as the

mouse pointer goes across ..... when recording .... so maybe to do with focus ... ?

who knows ......

---

### Post by cbowman57 on 2011-08-31
I don't know, composited images?  Definitely some conflict in the code somewhere.

---

### Post by 23dornot23d on 2011-08-31
Watched it again .... and it definately seems to be related to where the mouse is on the screen ..... 

Some places and its fine ...... so I guess you work out where the safe spots are and then
start looking for something that is different or the same in the other places ......

I would like it fixed though ...... how do we get it fixed ?

It is a Gnome Shell only problem .

It is a back screen only problem .

It is related to where the mouse crosses boundaries .......

But why BLUE ..... ? ........ 

( almost seems to be it messes the colour schemes/codes for an area up just before it takes focus )
( at the point focus takes place - only the old frames are still BLUE and the visible one becomes ok )

---

### Post by sanderd17 on 2011-09-01
Are you really using gtk-record-my desktop (as it used to be in Gnome2)? Or is gtk-record-my-desktop the app behind the CTRL+ALT+SHIFT+R shortcut?

If I do CTRL+ALT+SHIFT+R, everything records fine (although I get a slight lag in visual effects).

---

### Post by cbowman57 on 2011-09-01
> **sanderd17 said:**
> Are you really using gtk-record-my desktop (as it used to be in Gnome2)? Or is gtk-record-my-desktop the app behind the CTRL+ALT+SHIFT+R shortcut?

If I do CTRL+ALT+SHIFT+R, everything records fine (although I get a slight lag in visual effects).

That's the ticket.  I'd never used that before but saw it referenced in different posts & articles around trhe web.  When I tried it though it didn't work, I probably didn't have the correct key combination.

Just tried it, worked perfect, though as you said it sucks the system down just a tad while using it.

Now, how to convert what looks like an oddball format into something usable?

---

### Post by sanderd17 on 2011-09-01
It's recorded in WebM, that's a format created (or bought and released) by Google to get around patent trolls who were attacking Vorbis.

So it's an open format and it will probably become the most popular open format in a few years. Most tools already support WebM, and you can use it natively in HTML5 webpages in Firefox, Chrome and Opera.

---

### Post by cbowman57 on 2011-09-01
That sounds really good.

Have you found any performance tweaks or configuration that affect the recorder?  Something that reduces the load even at the expense of a few FPS would be nice.

---

### Post by sanderd17 on 2011-09-01
> **cbowman57 said:**
> That sounds really good.

Have you found any performance tweaks or configuration that affect the recorder?  Something that reduces the load even at the expense of a few FPS would be nice.

No, I didn't look into tweaking it. I don't even know how the program is called.

---

### Post by cbowman57 on 2011-09-01
I don't know what it's called either, but if you can't tweak it, what good is it?  :lol:

---

### Post by 23dornot23d on 2011-09-01
Just tried CTRL + ALT + SHIFT + R now and it started to work in my Arch install
but quickly ground everything to a HALT ..... its unusable on my system with 512 Meg memory ...

I was using the gtk-recordmydesktop to do mine with , maybe there are plans for a gtk3-recordmydesktop ......

What are the commands to stop that recorder too CTRL + ALT +  SHIFT + S would seem logical but again that did nothing once mine got started it would not stop and the mouse was so unresponsive it was not of any use on this machine .......

May be ok on a faster setup ...... good to know though as Its the first time I have seen it.

---

### Post by cbowman57 on 2011-09-01
I just used the same ctl+alt+shft+r to stop it, but yeah, it's writing to disk in realtime and definitely pulls the system down when it's running.

---

### Post by 23dornot23d on 2011-09-01
I might try it out later on the laptop and see how it works on that .....

Good to know you just do the same command to stop it ...... 

Maybe there are other recorders now that I do not know about ...... will do a search.

[http://en.wikipedia.org/wiki/Table_of_keyboard_shortcuts](http://en.wikipedia.org/wiki/Table_of_keyboard_shortcuts)


[http://linuxhelp.blogspot.com/2011/04/how-to-create-screencast-in-gnome-3.html](http://linuxhelp.blogspot.com/2011/04/how-to-create-screencast-in-gnome-3.html)

---

### Post by cbowman57 on 2011-09-01
I wish when people update a blog or other web article they would date it.  Not certain if this guys update was before or after the reader's comment that there was some configurability thru dconf-editor.

It **might** be possible to adust frame rates, I'll have to look at that later.

[http://dmdrummond.wordpress.com/2011/04/08/gnome-3-desktop-recording/](http://dmdrummond.wordpress.com/2011/04/08/gnome-3-desktop-recording/)

---

### Post by 23dornot23d on 2011-09-01
Ok got my first recording and it is crisp ...... as you say if you can reduce the FPS

it may be more useful too .....

[http://www.youtube.com/watch?v=ttVdcBCylx8](http://www.youtube.com/watch?v=ttVdcBCylx8)

With any 3D activated like Wings3d ..... its not useable on this machine .....

But impressive display - the output is very good ...... need to try this later on a better
machine to see if I can do small 3D tutorials on it ....

---

### Post by cbowman57 on 2011-09-01
Yeah, I tried it dropped to 7fps, it seemed to run well but I was doing a backup in the background and I don't know how to verify the properties of the resulting file.  Visually it looked great.

Now I'm going to check out this youtube video. :)
Looks quite good.

---

### Post by 23dornot23d on 2011-09-01
It is ok for non graphic intensive things ...... add a Wings3d window and thats it its dead as
a dodo .... just crawls to a halt ..... on mine .....

yet gtk-recordmydesktop ..... 

I had Blender Wings3d and a Firefox session going ...... on the gtk-recordmydesktop .....
same machine ..... and other than the blue on the background screen - it ran ok.

I guess there has to be some give and take ...... for what I need gtk-recordmydesktop will
do as I do not need to drop to the back screen often ....

---

### Post by cbowman57 on 2011-09-02
Keith, you really have to look at ABS [https://wiki.archlinux.org/index.php/Arch_Build_System](https://wiki.archlinux.org/index.php/Arch_Build_System)
that's where the real power of Arch comes into play.

---

### Post by cbowman57 on 2011-09-02
Hope you guys can tolerate my enthusiasm, I discover things that are a revelation to me, but everybody else probably already knows about them.

Anyway, a few days ago I discovered the tweaks that can be done to makepkg.conf that get incorporated into packages compiled & installed from the AUR.

This morning I discovered the ABS app, which creates a tree of all or a select repo of Arch. What does that mean you say?  Easy, every package available for installation now has a PKGBUILD file located on your HDD.  I re-installed using source with the "native' setting in makepkg.conf, gnome-shell, mutter, metacity, networkmanager &  a few others this morning.  All I can say is WOW!!  I thought the shell was fast & fluid before, I wish you could see it now.  I can only assume that the code really responded to some of the core2 specific instructions with the re-compilation.

I'll probably screw with it until I render the system useless, but I'll try to keep you guys updated. :)

sudo pacman -S abs

---

### Post by sanderd17 on 2011-09-02
This goes a bit beyond my knowledge, but that also means I can learn.

With what kind of options do you tweak those build files? Is there a wiki page about it?

When I get asked to edit the build file, I always answer 'no'.

---

### Post by cbowman57 on 2011-09-02
> **sanderd17 said:**
> This goes a bit beyond my knowledge, but that also means I can learn.

With what kind of options do you tweak those build files? Is there a wiki page about it?

When I get asked to edit the build file, I always answer 'no'.


Here's the wiki page on it [https://wiki.archlinux.org/index.php/Linux-ck](https://wiki.archlinux.org/index.php/Linux-ck)

This is the post where I posted the pertinent part of it [http://ubuntuforums.org/showpost.php?p=11199228&postcount=104](http://ubuntuforums.org/showpost.php?p=11199228&postcount=104)

Like I said, I don't know if my results are typical, might just be a lucky combination of hardware, but this is blowing my mind.  Truthfully, it couldn't respond much faster unless it started anticipating my thoughts.

When I build from AUR, or now ABS, I use makepkg -csi which is a really nice combination.

---

### Post by sanderd17 on 2011-09-02
Sorry for my ignorance.

The brain **** scheduler seems interesting, but what does it have to do with ABS?

It seems I have a lot of work with ABS, pacbuilder, PKGBUILD and makepkg before I will fully understand what options will be benificial for my computer.

---

### Post by cbowman57 on 2011-09-02
> **sanderd17 said:**
> Sorry for my ignorance.

The brain **** scheduler seems interesting, but what does it have to do with ABS?

It seems I have a lot of work with ABS, pacbuilder, PKGBUILD and makepkg before I will fully understand what options will be benificial for my computer.

The bfqs isn't the important part, it's the modifications to the makepkg.conf that will automatically build packages with enhancements specific to your platform that matter on that link.

Here's the link for ABS [https://wiki.archlinux.org/index.php/Arch_Build_System](https://wiki.archlinux.org/index.php/Arch_Build_System)

It's the combination of the information from those 2 links that make it EASY to get fantastic results.  All the years of people taling about building from source just for their hardware, the performance gains.  What this means is that you don't have to be programmer, or even know how to compile your packages from source, it's basically all done for you.

But, I don't blame you, best to stay in the comfort zone until you're ready to explore this aspect.  To me the hard part is done, just getting Arch installed & setup.  This just lets us really reap the reward.

I just wanted to share what I've been discovering with you guys since this doesn't seem to jump out when using the Arch forums, at least it didn't for me.

These are the packages I've processed & reinstalled using the PKGBUILD info provided by ABS:

```
clementine
fatrat
file-roller
gnome-desktop
gnome-disk-utility
gnome-js-common
gnome-session
gnome-shell
gnome-system-monitor
gnome-terminal
mdadm
metacity
mutter
networkmanager
network-manager-applet
p7zip 
```

Here's a link to the ABS FAQ that might make it easier to understand. [https://wiki.archlinux.org/index.php/ABS_FAQ](https://wiki.archlinux.org/index.php/ABS_FAQ)

---

### Post by 23dornot23d on 2011-09-02
If I can ever get Arch to run on the Dual core machine - I will go through the same packages you have gone
through to see how good it is .....
 
Thanks for all the information - I am reading it all - just need a reason for using it ..... that will come soon. :)

---

### Post by cbowman57 on 2011-09-02
I actually think your desktop machine might benefit more than the dual core, it's architecture specific compiling. Plus I think it strips out all the extra crap and creates smaller & faster executables.

It makes sense really, every distro has packages for the two primary architectures and they have to take a one-size-fits-all approach for maximum compatibility.

---

### Post by 23dornot23d on 2011-09-03
Just following Oneiric for a while .... only a month for that to be released ....want to check Gnome-Shell
is working in it .....

---

### Post by cbowman57 on 2011-09-03
Yeah, I've been reading some posts as well. I may check the beta out myself to see how far they've come since the alpha.

---

### Post by cbowman57 on 2011-09-03
Ok, setup a folder on Spider Oak that I can use to share files with anybody that is curious. Just threw a desktop recording I did with the native Gnome recorder, also keep my package lists and some scripts there.

If there is anything you can think of that you would like to examine at your convenience & that I can put there let me know.

[Link to my Spider Oak public folder]("https://spideroak.com/browse/share/Chuck_Bowman/KeG-dUCe-hAh93")

---

### Post by 23dornot23d on 2011-09-03
That video is so smooth .... love it ..... cannot wait to get it onto my dual core now ......

Went looking for a new computer today too ..... but will wait till Xmas time .

Great work ..... put more videos in there of the things that you do ......

Its a great share site ..... must see if I can set one up too ...... is it free .....

---

### Post by cbowman57 on 2011-09-03
> **23dornot23d said:**
> That video is so smooth .... love it ..... cannot wait to get it onto my dual core now ......

Went looking for a new computer today too ..... but will wait till Xmas time .

Great work ..... put more videos in there of the things that you do ......

Its a great share site ..... must see if I can set one up too ...... is it free .....

Yeah, not sure if the settings actually took but I changed from the default 15 to 7fps. 2GB free, been using it off & on for a few years, the linux client is really good, though a little quirky to get used to.

Yeah, recompiled most everything associated with the shell, this things runs smooth as glass. Almost anticipates a mouse or keystroke.  I have to admit, this is the smoothest setup I've ever used and it's just a $40 MSI motherboard, an intel E6500 & Nvidia GT9500, hardly state of the art but still very capable.  Neither Ubuntu or Debian ran nearly this fast or as smooth.

You are more familiar with graphics & video, can you verify the fps that video recorded at?  The info I found online implies that you can change the setting but it doesn't actually change anything.  I'd like to know for certain if possible.

---

### Post by 23dornot23d on 2011-09-03
Ok the settings did work ..... check the properties sheet for the video ..... 7 FPS is what is showing on that

[IMG]http://img822.imageshack.us/img822/2285/fpsko.jpg[/IMG]

> 
Yeah, recompiled most everything associated with the shell, this things  runs smooth as glass. Almost anticipates a mouse or keystroke.  I have  to admit, this is the smoothest setup I've ever used and it's just a $40  MSI motherboard, an intel E6500 & Nvidia GT9500, hardly state of  the art but still very capable.  Neither Ubuntu or Debian ran nearly  this fast or as smooth.



Nice I prefer building my own ..... I have a old desktop machine coming over from the UK soon ..... but I bet its dated now
was top spec when I built it ..... but that was a few years ago now ..... cannot even remember whats in it .....

But I got into the habit of making them and it was always good fun ..... miss that now .... and the bits do not seem to
be as readily available in France or its me not knowing where to look ....

---

### Post by cbowman57 on 2011-09-03
Odd, I don't have that 4th tab.

---

### Post by 23dornot23d on 2011-09-03
Thats using Oneiric and was updated last night ...... not sure why you are not seeing it if you are
up to date .... 

Unless its appeared through me adding something else - but I cannot think what ..... only extra ppa 
I have is for cairo-dock and I cannot see that making any difference ....

Be careful of latest updates/upgrades on Oneiric someone reported the last few [[COLOR=Red]_***network ones***_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1838043") may kill off the network
I am now going to leave it for a while - but will keep watching the progress .....

Next major upgrade may be when they finalize it now ....as everything else seems ok at the moment

---

### Post by bulldog on 2011-09-04
Reading your progress,pretty impressive!
Makes me wonder if I should try this too :)
Just joking.........have not the skills nor the time to do this.

Killed my Debian with some updates from unstable,a new version of xserver-xorg-core which cannot play nice with the nVidia driver.
Have it all up and running again,had to downgrade some packages,but missing the skills to do it right in once,I had to do it several times and my tty skills are increasing now :P.

But all is running fine again,I have the fourth tab from the video and nothing special installed.

---

### Post by cbowman57 on 2011-09-04
I think I got hit by the same xorg the other day, I had the Arch testing on, learned my lesson, deactivated that one.

Yeah, I went into gconf-editor, under nautilus and turned on advanced-permissions, which is supposed to give those properties but it doesn't work.  Not sure if it's an Arch bug or I broke something.  I guess I'll do without it until I can figure it out.  With all the experimentation that I've done on it I could have screwed it up somewhere.  If it was Ubuntu I would have just reinstalled. :)

Installation and setup is a little more time consuming, but if you have the time I think it's worth it.

---

### Post by bulldog on 2011-09-04
Setting up Arch needs reading so much,I'll pass for now.
But if I get some free time,I'll give it a go,just keep posting all the interesting stuff.

I salute you both with this achievement,you're pretty much on your way to be a 'linux Guru'.

---

### Post by cbowman57 on 2011-09-04
Yeah, it really is a bit daunting, had it not for all the time on Ubuntu, working on gNatty & messing with Debian I don't know that I could have muddled through it.

Fortunately I like fiddling around on stuff like this, so it keeps my time occupied.

Reinstalling Arch doesn't put me off too bad, but my favorite installation, the one I'm in now, uses that Raid0 which makes it a lot trickier to set up, not certain I could duplicate it.

I enjoy this though, and like to share the little things along the way that I find interesting, and sometimes hard to discover.

Glad you're following the progress, and find it interesting.  We've got the freedom to discuss things like this in a much freer manner than you'll find in the Arch forums.  It's funny the "personalities" that each distro seems to have.  The community really plays a huge role in how the distro is perceived.

Ubuntu does have the best community for new users in my opinion.

---

### Post by sanderd17 on 2011-09-04
I'm going to upgrade the family computer, but I don't know to what.

Currently they are using Mint 10 (based on Ubuntu 10.10) with almost everything default.

It's going to be used by my father and my sister (both are not too computer savvy, but they are not afraid of change, as long as it runs good). I'll do the maintenance (upgrading software, installing new things if they ask for it), but they have to work on it.

My father and my sister have worked with XP (at home), Win7 (at school/work) and Gnome2 (work with it now).

It's a pentium 4 computer with an nVidia graphical card, 1GB of RAM and two hard disks (one of 320GB and one of 500GB).

I'm doubting between Ubuntu 11.10 and Arch (it doesn't matter it's dangerous to upgrade with Arch because I will do any upgrade).

I will probably try to put the hard disks in RAID0 for the root directory (except for /boot and /home) if that also works in Ubuntu.

What do you guys think will give them the best experience? Gnome-Shell with the speed of Arch (in RAID0) or the new Unity (which I also like) on Ubuntu.

The Unity dock looks a lot like the Win7 taskbar. So it would be easy for them to get used to it, but I fear it will be a bit slow on that system. Maybe Gnome-shell with a good dock (with a lot of Unity dock features)?

Or if someone could get the unity dock running in Gnome-shell under Arch, that would solve most of my doubts (it gives the goodies of both: easy window management of Gnome-Shell and pinned shortcuts of the unity dock).

---

### Post by bulldog on 2011-09-04
Well,after some fiddling with SuSe and Fedora I was stuck on Ubuntu,did use it though,but didn't get to deep into it's structure.
Meeting you guys on the forums,did awake my interest in other distro's again.
Now on Debian,which I probably not had done without you guys for support.
I'm not afraid to dig into something,I have always other working distro's installed.
But I was used if something was broken,not to repair,but re-install the distro,that was quicker in my opinion,but learned nothing from it.
Now I'll try to repair,even if it takes me days,the downside is it takes me occupied till late in the evening,but you guys do the same :P.
But I learned a lot,I'm no longer lost in tty.

I learn a lot just by reading your conversation,not understand everything though,but I think if I was on the same distro as you are,things were become much clearer.

---

### Post by bulldog on 2011-09-04
> **sanderd17 said:**
> I'm going to upgrade the family computer, but I don't know to what.

Currently they are using Mint 10 (based on Ubuntu 10.10) with almost everything default.

It's going to be used by my father and my sister (both are not too computer savvy, but they are not afraid of change, as long as it runs good). I'll do the maintenance (upgrading software, installing new things if they ask for it), but they have to work on it.

My father and my sister have worked with XP (at home), Win7 (at school/work) and Gnome2 (work with it now).

It's a pentium 4 computer with an nVidia graphical card, 1GB of RAM and two hard disks (one of 320GB and one of 500GB).

I'm doubting between Ubuntu 11.10 and Arch (it doesn't matter it's dangerous to upgrade with Arch because I will do any upgrade).

I will probably try to put the hard disks in RAID0 for the root directory (except for /boot and /home) if that also works in Ubuntu.

What do you guys think will give them the best experience? Gnome-Shell with the speed of Arch (in RAID0) or the new Unity (which I also like) on Ubuntu.

The Unity dock looks a lot like the Win7 taskbar. So it would be easy for them to get used to it, but I fear it will be a bit slow on that system. Maybe Gnome-shell with a good dock (with a lot of Unity dock features)?

Or if someone could get the unity dock running in Gnome-shell under Arch, that would solve most of my doubts (it gives the goodies of both: easy window management of Gnome-Shell and pinned shortcuts of the unity dock).

Can't say anything about Arch,never used it,but I would go for ubuntu 11.10.
You've got unity,or gnome-shell and you can add a dock like AWN or something like that.

---

### Post by 23dornot23d on 2011-09-04
> 
Or if someone could get the unity dock running in Gnome-shell under  Arch, that would solve most of my doubts (it gives the goodies of both:  easy window management of Gnome-Shell and pinned shortcuts of the unity  dock).
You can do this by running UNITY 2D ...... then doing gnome-shell --replace

But only in Oneiric at the moment ....

[[COLOR=Red][/COLOR]]("http://img217.imageshack.us/img217/9537/conkyz.jpg")

---

### Post by sanderd17 on 2011-09-05
Guess it's gonna be Oneiric than.

I tried installing Unity in Arch before (it is in the AUR), but it didn't want to compile.

---

### Post by mips on 2011-09-05
For those using ext4 try this [https://wiki.archlinux.org/index.php/E4rat](https://wiki.archlinux.org/index.php/E4rat)

Shaved 10-12 seconds of my boot time this morning (using debian).

---

### Post by 23dornot23d on 2011-09-07
I did have a read through that Mips looks interesting .... not tried it out yet though

still wanting to get a version running on my main computer ......

hopefully tomorrow I will be able to try some more things out.



Tried to use UNetbootin


get the following error .... both as root or user

[root@archbang Downloads]# ./unetbootin-linux-555
./unetbootin-linux-555: error while loading shared libraries: libpng12.so.0: cannot open shared object file: No such file or directory
[root@archbang Downloads]# 


I have the answer and a link to the problem above

[http://aur.archlinux.org/packages.php?ID=21989&comments=all](http://aur.archlinux.org/packages.php?ID=21989&comments=all)

[IMG]http://img52.imageshack.us/img52/8702/snapshot64.jpg[/IMG]

[[COLOR=Red]**SCREENSHOT**[/COLOR]]("http://img713.imageshack.us/img713/8702/snapshot64.jpg")

---

### Post by cbowman57 on 2011-09-07
Use the dd method, that works great for Arch.

---

### Post by 23dornot23d on 2011-09-08
Cheers Chuck ....

I got a old computer through today with a few drives on it to have a play about with later on ..... may start experimenting now .... do not realize how computers date though ....


2 x 180 Gig drives on it but one is just clicking away to itself ....... so its naff .... ;)
but one is good so it will get some use now .....

---

### Post by cbowman57 on 2011-09-08
Wish I could come up with something like that.  The only access I've got right now is with Windows. :(

---

### Post by 23dornot23d on 2011-09-08
I found windows 98 was installed on one of the drives here and it still booted up ..... on my newer desktop machine ...... nostalgia time.

Hope you get yours sorted out soon ....

---

### Post by cecilpierce on 2011-09-09
You guys are having better luck with Arch then I am, tried it 3 times, I like it but it kept giving me headaches, so Im going to wait awhile on it. Messing with Bodhi for awhile.

---

### Post by mips on 2011-09-09
> **cecilpierce said:**
> You guys are having better luck with Arch then I am, tried it 3 times, I like it but it kept giving me headaches....

What's the problem?

---

### Post by cbowman57 on 2011-09-11
Wish I was on my computer so I could check this out.

Gnome 3.2 beta2 is available in [gnome-unstable] 
[https://bbs.archlinux.org/viewtopic.php?id=126318](https://bbs.archlinux.org/viewtopic.php?id=126318)

---

### Post by 23dornot23d on 2011-09-11
Looks like a good link - I will be trying it out sometime soon ..... thanks ;)

Arch is running really well for me at the moment - so may do this a little nearer the
release date for 3.2 ..... not long now I know .....

---

### Post by cecilpierce on 2011-09-13
How the heck did you guys get GS going in Arch ?
I must have installed and reinstalled everything that Ive read in the Arch-Wiki's and tried a million copy's and paste's.

All I have that work good is Xfce and Gnome3 and I guess the default, open-box I think its called ???   :confused:

---

### Post by mips on 2011-09-13
> **cecilpierce said:**
> 
All I have that work **good** is Xfce and Gnome3 and I guess the default, open-box I think its called ???   :confused:

well

---

### Post by 23dornot23d on 2011-09-13
If you have Gnome3 you must almost be there ..... then Cecil .... :confused:

what errors do you get when you run 

```

**gnome-shell --replace**

```

from a terminal ....

---

### Post by cecilpierce on 2011-09-13
Let me reboot into arch and see if it will start !   
):P

---

### Post by 23dornot23d on 2011-09-13
Ok when you get in - let me know what you use is it GDM .... KDM ..... or SLIM ....

and which of the above can you go into ......

[ We will start with the DM and then the GRAPHICS driver ..... if you can get into it ok ]

my two main problems were that SLIM did not want to work with Gnome-Shell ......
( both kdm and gdm work fine though with Gnome-Shell )
and secondly the Nvidia drivers needed loading in ....... and I think you use the same 
Nvidia card as me so the earlier links in this thread may be of use ..... [[COLOR=Red]_*** page 3***_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1832919&page=3")

---

### Post by cecilpierce on 2011-09-13
[cecil@archbang ~]$ 
[cecil@archbang ~]$ gnome-shell --replace
failed to create drawable

(gnome-shell:1219): Clutter-CRITICAL **: Unable to initialize Clutter: Unable to select the newly created GLX context
Window manager error: Unable to initialize Clutter.
[cecil@archbang ~]$ 

I get errors tring to install nvidia, and it boots to a terminal and the only thing I can start is 'startxfce4' but I think I can logout and get to slim, it use to boot right into gnome but I must have screwed up inittab or rc.conf, I cant remeber and my notes are all over the place, geeeeez !!!

---

### Post by 23dornot23d on 2011-09-13
Ok no problem ..... as long as we have a terminal ......

it sounds like the Nvidia drivers are not installed ..... but lets see what we can get 

I will just find the link for the Nvidia Drivers I used ....... what card is in the machine you
are using .....

This is the routine for loading the Nvidia Drivers ..... it was for Slackware ..... but the [[COLOR=Blue]_***same routine I used here***_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1824180&highlight=slackware&page=3")....

and the [[COLOR=Blue]***Nvidia Driver link***[/COLOR]]("http://www.nvidia.com/Download/index.aspx?lang=en-us")

Chuck gave me this at the beginning ..... to get gdm installed .....
[B]pacman -S xorg gdm


to see if gdm works ..... type gdm in the terminal ........ at start up .... ( i.e - before you enter the DM )


Start by downloading the Nvidia driver ...... and let me know once you have it ..... 
I start by copying it to the root directory ...  / 
[/B]

---

### Post by cecilpierce on 2011-09-13
changed inittab now im in gnome>

# Example lines for starting a login manager
#x:5:respawn:/bin/su cecil -l -c "/bin/bash --login -c /usr/bin/startx >/dev/null 2>&1"
#x:5:respawn:/usr/sbin/gdm
#:5:respawn:/usr/bin/kdm -nodaemon
#x:5:respawn:/usr/bin/slim >& /dev/null
x:5:respawn:/usr/sbin/gdm -nodaemon

---

### Post by 23dornot23d on 2011-09-13
ok do you have nvidia-settings installed yet .....

[[COLOR=Blue]_***SCREENSHOT***_[/COLOR]]("http://img707.imageshack.us/img707/7198/screenshot1cv.jpg")

just to see if the driver is working or not ...... ( if not we will go through step by step )

---

### Post by cecilpierce on 2011-09-13
just got it, shud i blacklist tje nouveau b4 installing ?

gforce 6200

---

### Post by 23dornot23d on 2011-09-13
Yep it needs that blacklist file in place first .....

Then it will use the new Nvidia one ....... that we install ......

( Thats for - When you reboot .... )
( you will have to run the graphics install from a root terminal too ..... thats why I copy it to root easy to find and make it executable too )

[COLOR=Red]**Ensure you have the latest Linux headers and kernel first though ...... they need to be there ......**[/COLOR]
( it will work on the old kernel - I just like everything up to date ... but the headers need to be there for it ... )
(you can do this afterwards ..... but I always update all at once )

```


pacman -S linux

pacman -S linux-headers


you can try this ..... if you want to ..... 

I would do it after a re-boot ....

pacman -S nvidia


```If it works ok then we do not need the one we downloaded ..... but it is there just in case we have no graphics ...
we can run it from root. .....

---

### Post by cecilpierce on 2011-09-13
root@archbang cecil]# pacman -S nvidia
resolving dependencies...
looking for inter-conflicts...
:: nvidia-utils and libgl are in conflict. Remove libgl? [y/N] 
error: unresolvable package conflicts detected
error: failed to prepare transaction (conflicting dependencies)
:: nvidia-utils and libgl are in conflict
[root@archbang cecil]# 

thats what I always got b4 ???

linux upgraded to 3.0.4-1

---

### Post by 23dornot23d on 2011-09-13
Ok I think I got that originally too ...... just run the Nvidia xxxx .run

as root ....... it does the rest for you I think .....[[COLOR=Red]_*** looking back thats what I did***_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1832919&page=3") ......

( to make it executable if you did not do it already )

[COLOR=Blue]**chmod u+x NVIDIA-Linux-x86-280.13.run**[/COLOR]

[root@archbang /]# ./NVIDIA-Linux-x86-280.13.run 
Verifying archive integrity... 
OK Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86 280.13............................................................................................................................... 
[root@archbang /]#

Then rebooted and I had the graphics set as I wanted it .... with Nvidia drivers working .....[[COLOR=Red]_*** see post 29***_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11189533&postcount=29")

Once you get to this point let me know .... ( hopefully all should go well )

You have to drop out of the graphics manager to do this ..... it will not work from a terminal inside of gdm ....

---

### Post by cecilpierce on 2011-09-13
Well well gnome-shell, all I have in the chooser is gnome, gnome-openbox and xfce ???

When I chose gnome it went into gnome-shell ?

I have been tring to fix the time on the clock, its set for NY but reads 4 hrs ahead, so I set the map thingy to Alaska so it reads the right time, boy Im sure haveing bad luck or is it dumb luck?

---

### Post by 23dornot23d on 2011-09-13
Ok good to see it is working .....

Next the time ...... its one thing I too have problems with on Arch for some reason
mine is 2 hours behind here .....

I did spend some time trying to fathom it out ...... all my settings seem to be correct for my location too

Ok going to have to leave now --- up early tomorrow .... time to sleep ..... catch you later.....

Best of luck with the time ( I use this in Ubuntu .... not sure for Arch )

[URL="http://www.google.com/search?client=ubuntu&channel=fs&q=txdata&ie=utf-8&oe=utf-8#pq=tzdata&hl=en&sugexp=gsis%2Ci18n%3Dtrue&cp=5&gs_id=y&xhr=t&q=dpkg+reconfigure+tzdata&qe=ZHBrZyB0emRhdGE&qesig=h-olmAJpwApz0zD5iAIx2w&pkc=AFgZ2tl2I6qnKAui1koaHdesKg7wflORV8w65mICvbPSZRzpCLjxP2NK_sISg969PEkxI0X3cfh_lDRwXH7VzMakQuQVO9EVEQ&pf=p&sclient=psy&client=ubuntu&hs=OQy&channel=fs&biw=1187&bih=520&source=hp&pbx=1&oq=dpkg+tzdata&aq=0c&aqi=g-c1g-v1g-b1&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.&fp=1fa7c254c97e187f"][COLOR=Red][U][I][B]dpkg -reconfigure tzdata
[/B][/I][/U][/COLOR][/URL]

---

### Post by cecilpierce on 2011-09-13
> **23dornot23d said:**
> Ok good to see it is working .....

Next the time ...... its one thing I too have problems with on Arch for some reason
mine is 2 hours behind here .....

I did spend some time trying to fathom it out ...... all my settings seem to be correct for my location too

Thanks Keith..
same here, its been driving me koko, just do what I did in the map  :lolflag:

How do I change what shows up in the chooser and what do you have in the inittab file, I think I messed mine up, I keep editing it !
Should have made a backup, DA  :confused:

---

### Post by 23dornot23d on 2011-09-13
This is mine ........ I drop to console though ..... the 3 wants to be a 5 to boot into a shell
by booting to a console ..... 

I type gdm or kdm .... to get into the environment I want ....



#
# /etc/inittab
#

#  Runlevels:
#    0    Halt
#    1(S)    Single-user
#    2    Not used
#    3    Multi-user
#    4    Not used
#    5    X11
#    6    Reboot

## Only one of the following two lines can be uncommented!
# Boot to console
id:[COLOR=Red]***3***[/COLOR]:initdefault:
# Boot to X11
#id:5:initdefault:

rc::sysinit:/etc/rc.sysinit
rs:S1:wait:/etc/rc.single
rm:2345:wait:/etc/rc.multi
rh:06:wait:/etc/rc.shutdown
su:S:wait:/sbin/sulogin -p

# -8 options fixes umlauts problem on login
c1:2345:respawn:/sbin/agetty -8 38400 tty1 linux
c2:2345:respawn:/sbin/agetty -8 38400 tty2 linux
c3:2345:respawn:/sbin/agetty -8 38400 tty3 linux
c4:2345:respawn:/sbin/agetty -8 38400 tty4 linux
c5:2345:respawn:/sbin/agetty -8 38400 tty5 linux
c6:2345:respawn:/sbin/agetty -8 38400 tty6 linux

ca::ctrlaltdel:/sbin/shutdown -t3 -r now

# Example lines for starting a login manager
#x:5:respawn:/bin/su keith -l -c "/bin/bash --login -c /usr/bin/startx >/dev/null 2>&1"
#x:5:respawn:/usr/sbin/gdm -nodaemon
#x:5:respawn:/usr/bin/kdm -nodaemon
x:5:respawn:/usr/bin/slim >& /dev/null

# End of file

---

### Post by cecilpierce on 2011-09-13
Thanks again Keith, I thought you went to sleep so I had dinner, Ill try it tomarrow, I road my bike at the beach all day and got sun burned back and I tired to ! CUL
Cecil

---

### Post by 23dornot23d on 2011-09-14
Hope you are enjoying using Arch Cecil ....... its revived my old computer .....


The file I posted above in my previous post .....

tty1 ....... if you log in to this ..... Slim will start automatically and it goes into the normal 

Archbang Desktop ..... very light

tty3 ...... I usually log into this ...... and then type in 

gdm or kdm


A little more hungry on resources - but both run well with either KDE or Gnome Shell



If I run KDE up and the ALT+F2 ........ gnome shell --replace

Gnome Shell runs and the KDE things that I like are also on the desktop ..... it allows for
placing autostart icons on the desktop as well as retaining some of the blue glow themeing .......

I quite like the environment above and its supprising how little memory is needed for it ...

Ok have fun ....... will be back on later tonight ...... hope you keep trying things out on Arch as it is very good ..... :)

---

### Post by cecilpierce on 2011-09-14
Thanks, Ive put in alot of extensions in and they all work but theme-selector, it locks up the screen and have to reboot.

I cant seem to get back to the old gnome3 that I had originally ?

KDE works good and Xfce but dont like Xfce to much.

When I bootup it goes right into the login screen gizzmo and theres no choice to select slim just kde,gnome,xfce and openbox ?

Oh well, I'll keep plugin away  ):P

---

### Post by 23dornot23d on 2011-09-14
> 
Thanks, Ive put in alot of extensions in and they all work but theme-selector, it locks up the screen and have to reboot.
Ok good to hear all the other extensions are working ok ...... with themes you probably already know I stick with one the Tron one ..... but I can say too that the theme selector
does not seem to be working on anything other than the older versions for me too.

> 
I cant seem to get back to the old gnome3 that I had originally ?
I know what you mean ..... although I still have installation disks to load the old GS one
v3.0.1/v3.0.2 ....... themes are still working ok for me in these versions .....
 
I have no idea how to move them onto ARCH ...... unless there is a version in AUR .....

Hopefully when 3.2 comes out we will maybe see some new features ...... who knows 
which distro will be first to get it up and running properly though ..... 

> 
KDE works good and Xfce but dont like Xfce to much.
I too do like KDE on ARCH ..... because its less memory intensive and faster to load than
on any other system I have used ...... Xfce is good for a start desktop for Archbang ....
but for better machines I believe people will use what they prefer once they see the speed and low memory usage of ARCH .....

> 
When I bootup it goes right into the login screen gizzmo and theres no choice to select slim just kde,gnome,xfce and openbox ?
If you change the 5 to a 3 as I have it above in the /etc/inittab you can do all the things I mentioned ..... but if you prefer to boot into a desktop manager leave it at 5 ........

ok CUL .... ;)

---

### Post by cbowman57 on 2011-09-15
[https://bbs.archlinux.org/viewtopic.php?pid=991142#p991142](https://bbs.archlinux.org/viewtopic.php?pid=991142#p991142)

You guys been tracking G-S 3.2 in Arch?  Looks to be moving along pretty well, but not without some bugs.

According to a note I saw on fpmurphy's website he's not doing anything with his extensions until 3.2 is released, I assume that means when Fedora releases 3.2.

---

### Post by 23dornot23d on 2011-09-15
Interesting read ..... Cheers Chuck 

My best versions are the earlier ones ...... everyone else seems to be waiting for 3.2
so there is something solid to build on ...... so me too ..... ;)

I will wait it out too ...... am quite happy with the versions I have .....

If I ever get a few copies of Arch running I will test it out ....... but at the moment I only have one 
so its wrapped in cotton wool ....... :)

---

### Post by sanderd17 on 2011-09-16
> **cbowman57 said:**
> 

According to a note I saw on fpmurphy's website he's not doing anything with his extensions until 3.2 is released, I assume that means when Fedora releases 3.2.

So that means most of the extensions don't work on GS 3.2 beta yet?

---

### Post by cbowman57 on 2011-09-16
Well, when I was trying out 3.1.3 it broke about 1/3 of what I was using.  3.2 beta might break even more.  

So, if you're gonna give it a try be prepared for that.

---

### Post by cecilpierce on 2011-09-19
Where all you Arch-Bangers been hiding or fiddling with some thing new ?

Ive been following the OO tista thread, the extensions are working pretty good, im going to see if I can get some of the others from fpmurphy to work.

Later gators. 
Cecil
:)

---

### Post by cecilpierce on 2011-09-19
So far no luck with fpmurphy or venemo 
:confused:

---

### Post by buntu63 on 2011-09-19
> **cecilpierce said:**
>  dont like Xfce to much

me 2!

**i'd prefer 'yentu'[B]... anyway arch is not the **pan·a·ce·a 4 old boxes...

[http://distrowatch.com/table.php?distribution=gentoo](http://distrowatch.com/table.php?distribution=gentoo)
[/B]

---

### Post by sanderd17 on 2011-09-20
I'm bringing some themes from Devianart into the AUR.

---

### Post by cbowman57 on 2011-09-20
Right now I'm detained up in northern Illinois, not sure when I'm getting home but I sure miss my Linux.  :)

---

### Post by cecilpierce on 2011-09-20
> **cbowman57 said:**
> Right now I'm detained up in northern Illinois, not sure when I'm getting home but I sure miss my Linux.  :)

I know what you mean Chuck,I just went for a bike ride and came back in an hour to try to fix OO-gs.
Well after the first big snow I hope you come running back !   :lolflag:

---

### Post by cbowman57 on 2011-09-20
> **sanderd17 said:**
> I'm bringing some themes from Devianart into the AUR.

Cool, are you going to package them to install ~/.themes or universal?  One reason I install just about everything manually is because I prefer per user installation.

---

### Post by cbowman57 on 2011-09-20
> **cecilpierce said:**
> I know what you mean Chuck,I just went for a bike ride and came back in an hour to try to fix OO-gs.
Well after the first big snow I hope you come running back !   :lolflag:

Hopefully it will be before the snow flies, but I'm here for family & will stay as long as it takes.

What extensions have you been trying to get working?

---

### Post by sanderd17 on 2011-09-20
> **cbowman57 said:**
> Cool, are you going to package them to install ~/.themes or universal?  One reason I install just about everything manually is because I prefer per user installation.

I'm copying them to /usr/share/themes

I don't know if it's possible to copy them to ~/.themes because the script is ran as root. So ~ would be /root (and I can't guess your username :-P)

---

### Post by cbowman57 on 2011-09-20
> **buntu63 said:**
> me 2!

**i'd prefer 'yentu'[B]... anyway arch is not the **pan·a·ce·a 4 old boxes...

[http://distrowatch.com/table.php?distribution=gentoo](http://distrowatch.com/table.php?distribution=gentoo)
[/B]

I think the last time I looked at Gentoo the installation stopped me right in my tracks, which is funny because I could have sworn I installed it a few years ago and it wasn't that difficult.

---

### Post by cbowman57 on 2011-09-20
> **sanderd17 said:**
> I'm copying them to /usr/share/themes

I don't know if it's possible to copy them to ~/.themes because the script is ran as root. So ~ would be /root (and I can't guess your username :-P)

Better that way than no way. :) 

Seems like there should be a simple method to install per user. $HOME maybe?  but that would still need to identify which user and assign the correct permissions.  Just seems like it should be something that Linux can do.

---

### Post by sanderd17 on 2011-09-20
Sorry, I was wrong.

Since the PKGBUILD is ran as normal user, I can use it to create a personal Arch package. So a package that installs to your home directory (but that you can't share with others).

And the AUR only needs a PKGBUILD file. So it works.

Now, how should I name those packages?

Something like 

```

gnome-shell-theme-*adwaita*-single-user

```

---

### Post by cbowman57 on 2011-09-20
> **sanderd17 said:**
> Sorry, I was wrong.

Since the PKGBUILD is ran as normal user, I can use it to create a personal Arch package. So a package that installs to your home directory (but that you can't share with others).

And the AUR only needs a PKGBUILD file. So it works.

Now, how should I name those packages?

Something like 

```

gnome-shell-theme-*adwaita*-single-user

```

I don't really know what naming convention is best, or correct, but that sure looks good to me.  I can see only advantages & no disadvantage to this method.


I think that most of the extension & theme authors are probably in favor of the per user method, though I think just about every distro installs them as root. IMO your method is the most correct.

BTW, thanks for tackling this for AUR, I think it's a nice contribution. :)

---

### Post by sanderd17 on 2011-09-21
I'm trying to use sed and do automatic conversions of the PKGBUILD files (since it's only changing the installation path, package name and maintainer).

It works quite well (only one problem with a \n that shouldn't be there). I guess I'll be uploading some when that last problem is fixed.

---

### Post by cbowman57 on 2011-09-21
> **sanderd17 said:**
> I'm trying to use sed and do automatic conversions of the PKGBUILD files (since it's only changing the installation path, package name and maintainer).

It works quite well (only one problem with a \n that shouldn't be there). I guess I'll be uploading some when that last problem is fixed.

I look forward to trying it out.

---

### Post by sanderd17 on 2011-09-24
I've added most of them. If you have any requests, please say them.

Sorry for the delay, I had problems with the bureaucratic system of my university that I needed to solve first.

---

### Post by sanderd17 on 2011-09-27
Ok, am I dreaming?

I added most of those packages, and now they are gone. Without a trace, without a notification.

Was it treated as spam? (because I did upload a lot of packages together), or aren't you allowed to put single-user packages in the AUR?

I don't know.

BTW, I added the new google theme, but not as a single user install (I'm afraid it will be deleted too).

---

### Post by cbowman57 on 2011-09-27
> **sanderd17 said:**
> Ok, am I dreaming?

I added most of those packages, and now they are gone. Without a trace, without a notification.

Was it treated as spam? (because I did upload a lot of packages together), or aren't you allowed to put single-user packages in the AUR?

I don't know.

BTW, I added the new google theme, but not as a single user install (I'm afraid it will be deleted too).

I have no idea what the requirements are for AUR.  Maybe it conflicts with some guideline?

---

### Post by sanderd17 on 2011-09-27
> **cbowman57 said:**
> I have no idea what the requirements are for AUR.  Maybe it conflicts with some guideline?

But why didn't I get a notification?

---

### Post by cbowman57 on 2011-10-16
> **sanderd17 said:**
> Ok, am I dreaming?

I added most of those packages, and now they are gone. Without a trace, without a notification.

Was it treated as spam? (because I did upload a lot of packages together), or aren't you allowed to put single-user packages in the AUR?

I don't know.

BTW, I added the new google theme, but not as a single user install (I'm afraid it will be deleted too).

Did you ever find out what the problem was?

---

### Post by sanderd17 on 2011-10-17
No, I didn't. But I haven't asked it on the Arch forums too.

---

### Post by cbowman57 on 2011-10-17
I was just curious.

---

### Post by cbowman57 on 2011-10-21
Old article but probably one of the nicest "Installing Arch for Dummies" guides I've found.

[http://lifehacker.com/5680453/build-a-killer-customized-arch-linux-installation-and-learn-all-about-linux-in-the-process](http://lifehacker.com/5680453/build-a-killer-customized-arch-linux-installation-and-learn-all-about-linux-in-the-process)

---

### Post by cbowman57 on 2011-10-21
Ok, I'm getting used to 3.2 & the extensions are catching up fast.  Only one I **really** miss is righthotcorner, which I hope gets refreshed soon.

A little video of what my desktop is looking like can be found here [https://spideroak.com/browse/share/Chuck_Bowman/KeG-dUCe-hAh93](https://spideroak.com/browse/share/Chuck_Bowman/KeG-dUCe-hAh93)

I scrapped my Raid 0 setup because of the problems maintaining [Clonezilla]("http://clonezilla.org/clonezilla-live.php") backups.  There was a slight improvement in performance but not enough to justify the backup headache.

---

### Post by cbowman57 on 2011-12-12
Well after many month's of use I've reached the conclusion that I like Gnome shell better on Arch than Ubuntu, more things just seem to work correctly.  It's not always as simple as an Ubuntu box but finding & fixing things are more in the hands of the user.

I still use both, bouncing back & forth between a Precise & my Arch installations, but spend more time on Arch these days.

Just thought you guys might be interested in a long term assessment considering all the distro hopping I was doing. :)

Oh, for a friendly version of Arch you can check out [KahelOS]("http://distrowatch.com/?newsid=07015")

---

