---
title: "software for webcamming?"
date: 2005-07-03
forum: Absolute Beginner Talk
---

### Post by gammyhand on 2005-07-03
Is there any software for ubuntu for webcamming? I only bought the stupid thing to talk to my cousin/aunt/uncle who live about 300 miles away and I realised GAIM does not support it :(

---

### Post by Knome_fan on 2005-07-03
GnomeMeeting (which is installed by default, I think) should work.

---

### Post by gammyhand on 2005-07-03
[QUOTE=Knome_fan]GnomeMeeting (which is installed by default, I think) should work.[/QUOTE]
 Cool - can it talk to a windows user on msn (or more likely netmeeting)?

---

### Post by Knome_fan on 2005-07-03
I think it uses the same protocol as netmeeting, so that should work.

About msn, I don't think that's possible right now, but as far as I know some projects are working on it.

---

### Post by gammyhand on 2005-07-03
[QUOTE=Knome_fan]I think it uses the same protocol as netmeeting, so that should work.

About msn, I don't think that's possible right now, but as far as I know some projects are working on it.[/QUOTE]
 Thanks for the advice :)

---

### Post by rwabel on 2005-07-05
amsn has webcam functions. UI is ugly, but the only one so far!

---

### Post by arunsub on 2005-07-05
AMsn nightly builds have webcam function, not the stable release. If you are lucky, the nightly build will install without problems. It has some new dependency files and I couldn't get it working.

---

### Post by rwabel on 2005-07-05
[QUOTE=arunsub]AMsn nightly builds have webcam function, not the stable release. If you are lucky, the nightly build will install without problems. It has some new dependency files and I couldn't get it working.[/QUOTE]
 I've installed it some weeks ago without problems. What errors do you get?

---

### Post by arunsub on 2005-07-05
[QUOTE=rwabel]I've installed it some weeks ago without problems. What errors do you get?[/QUOTE]
I get the following error when i run ./configure in msn directory. 
./configure: line 3156: /usr/lib/tkConfig.sh: No such file or directory

---

### Post by rwabel on 2005-07-05
yep, that's because there is nothing to compile :-P

just go in the msn directory and use the command
 ```
./amsn
```

---

### Post by gammyhand on 2005-07-05
[QUOTE=rwabel]yep, that's because there is nothing to compile :-P

just go in the msn directory and use the command
 ```
./amsn
```[/QUOTE]
 I will give amsn a go and see how I get on with it. Personally I find the GAIM interface pretty horrible.

---

### Post by arunsub on 2005-07-05
[QUOTE=rwabel]yep, that's because there is nothing to compile :-P

just go in the msn directory and use the command
 ```
./amsn
```[/QUOTE]
I get the following error if i run that:
You can't load TkCximage, this is now needed to run amsn.  you can compile  it with the makefile inside amsn folder. 
i can't do makefile since ./configure didn't work.

---

### Post by rwabel on 2005-07-05
[QUOTE=arunsub]I get the following error if i run that:
You can't load TkCximage, this is now needed to run amsn.  you can compile  it with the makefile inside amsn folder. 
i can't do makefile since ./configure didn't work.[/QUOTE]
 It's a some weeks ago I did it.  but if I remember right, I've never done a ./configure
Nevermind, I've redownloaded amsn from [here]("http://amsn.sourceforge.net/amsn_cvs.tar.gz")
 ```
tar xvfz amsn_cvs.tar.gz
cd msn
./configure
make
sudo make install
```

worked fine!

Here is the prof, that I have configure in the msn directory
 ```
rwabel@RALPH:~/compiling/msn $ ls
abook.tcl	 config.tcl		 hotmlog.htm	 preferences.tcl
alarm.tcl	 configure		 icons		 progressbar.tcl
amsn			 configure.ac	 lang		 protocol.tcl
amsn.debianmenu CREDITS			 langlist		proxy.tcl
amsn.desktop	 ctadverts.tcl	 lang.tcl		README
amsn-remote	  ctthemes.tcl	    loging.tcl	  remote.help
amsn-remote-CLI  cvs_date		    Makefile.in	 remote.tcl
amsn.spec	 des.tcl			 migmd5.tcl	 skins
AppMain.tcl	 dock.tcl		 msncam.tcl	 skins.tcl
automsg.tcl	 docs			 msnp2p.tcl	 smileys.tcl
autoupdate.tcl FAQ				 mutex.tcl	 sndplay
balloon.tcl	 GNUGPL			 notes.tcl	 socks.tcl
blocking.tcl	 groups.tcl		 picture.tcl	 sxml.tcl
chatwindow.tcl   guicontactlist.tcl  plugins		 TODO
combobox.tcl	 gui.tcl			 pluginslog.tcl trayicon.tcl
Compile.mk	 HELP			 plugins.tcl	 utils
config.log	   hotmail.tcl		 png.tcl

```

I hope it works, let me know if you get other errors or run in other problems. good luck!

btw: you must have installed tk8.4-dev and tk8.4. Furthermore I guess you need also imlib11-dev and imlib11 and probably also imlib1

---

### Post by arunsub on 2005-07-05
[QUOTE=rwabel]It's a some weeks ago I did it.  but if I remember right, I've never done a ./configure
Nevermind, I've redownloaded amsn from [here]("http://amsn.sourceforge.net/amsn_cvs.tar.gz")
 ```
tar xvfz amsn_cvs.tar.gz
cd msn
./configure
make
sudo make install
```

worked fine!

Here is the prof, that I have configure in the msn directory
 ```
rwabel@RALPH:~/compiling/msn $ ls
abook.tcl	 config.tcl		 hotmlog.htm	 preferences.tcl
alarm.tcl	 configure		 icons		 progressbar.tcl
amsn			 configure.ac	 lang		 protocol.tcl
amsn.debianmenu CREDITS			 langlist		proxy.tcl
amsn.desktop	 ctadverts.tcl	 lang.tcl		README
amsn-remote	  ctthemes.tcl	    loging.tcl	  remote.help
amsn-remote-CLI  cvs_date		    Makefile.in	 remote.tcl
amsn.spec	 des.tcl			 migmd5.tcl	 skins
AppMain.tcl	 dock.tcl		 msncam.tcl	 skins.tcl
automsg.tcl	 docs			 msnp2p.tcl	 smileys.tcl
autoupdate.tcl FAQ				 mutex.tcl	 sndplay
balloon.tcl	 GNUGPL			 notes.tcl	 socks.tcl
blocking.tcl	 groups.tcl		 picture.tcl	 sxml.tcl
chatwindow.tcl   guicontactlist.tcl  plugins		 TODO
combobox.tcl	 gui.tcl			 pluginslog.tcl trayicon.tcl
Compile.mk	 HELP			 plugins.tcl	 utils
config.log	   hotmail.tcl		 png.tcl

```

I hope it works, let me know if you get other errors or run in other problems. good luck!

btw: you must have installed tk8.4-dev and tk8.4. Furthermore I guess you need also imlib11-dev and imlib11 and probably also imlib1[/QUOTE]
I did what you did and the error i got was the same as i stated earlier:
./configure: line 3156: /usr/lib/tkConfig.sh: No such file or directory

---

### Post by rwabel on 2005-07-06
you are for sure missing some packages. I even guess
tcl8.4 and tcl8.4-dev
and the others I told u before need to be installed too! Make sure you have them all installed and try ./configure again

---

### Post by arunsub on 2005-07-06
[QUOTE=rwabel]you are for sure missing some packages. I even guess
tcl8.4 and tcl8.4-dev
and the others I told u before need to be installed too! Make sure you have them all installed and try ./configure again[/QUOTE]
You are right. I was missing -dev packages. Sorry. It's working now. I haven't checked the webcam yet. Is there an option to select the camera source?

---

### Post by gammyhand on 2005-07-06
[QUOTE=arunsub]You are right. I was missing -dev packages. Sorry. It's working now. I haven't checked the webcam yet. Is there an option to select the camera source?[/QUOTE]
 According to gnomemeeting I have no camera installed. How do I install a device on linux/ubuntu?

---

### Post by rwabel on 2005-07-06
what camera do you have?
If you have a Logitech check [this page](http://qce-ga.sourceforge.net/)
and [here](http://mxhaard.free.fr/download.html) for the driver

Here is my [blog entry](http://ralph.n3rds.net/index.php?/archives/20-Install-Logitech-QuickCam-Express-Plus.html) from my installation.

you can check with the program gqcam your webcam.

---

### Post by tikal26 on 2005-07-06
[QUOTE=rwabel]what camera do you have?
If you have a Logitech check [this page](http://qce-ga.sourceforge.net/)
and [here](http://mxhaard.free.fr/download.html) for the driver

Here is my [blog entry](http://ralph.n3rds.net/index.php?/archives/20-Install-Logitech-QuickCam-Express-Plus.html) from my installation.

you can check with the program gqcam your webcam.[/QUOTE]
 what about trying mercury  at mercury.to
it works like msn and the interface is so smooth

---

### Post by rwabel on 2005-07-06
thanks for the tip. I'm going to try that one out. It's java based, that makes me a little worry about its speed.

---

### Post by Jade Robbins on 2005-07-06
[QUOTE=rwabel]yep, that's because there is nothing to compile :-P

just go in the msn directory and use the command
 ```
./amsn
```[/QUOTE]
 Is there a program like WebcamXP out for linux? iwant a program that automatically takes a shot from my webcam then uploads it to my website. Any ideas?

---

### Post by rwabel on 2005-07-06
@tikal26
it's a very huge application. don't know why it needs so much space....the UI is a bit better, but still nothing really nice :-) webcam isn't yet available, at least for the stable version

@Jade Robbins
sorry, I've no idea!

---

### Post by arunsub on 2005-07-06
how do i select the webcam source in amsn? I have Intel PC camera, WinTV go and Firewire ports. I think Amsn is not selecting my PC camera by default. How do I change the camera source to select the pc camera?

---

### Post by rwabel on 2005-07-07
[QUOTE=arunsub]how do i select the webcam source in amsn? I have Intel PC camera, WinTV go and Firewire ports. I think Amsn is not selecting my PC camera by default. How do I change the camera source to select the pc camera?[/QUOTE]
 sorry no idea. I've not yet tried it out. but amsn has a forum I guess. Or try google

---

### Post by arunsub on 2005-07-07
[QUOTE=rwabel]sorry no idea. I've not yet tried it out. but amsn has a forum I guess. Or try google[/QUOTE]
I found out that I have to run ./test.tcl from utils/linux/capture folder. It showing my WinTV go card as the camera. It's not showing my Intel USB PC camera. How do i enable my USB PC camera (Intel) in ubunut?

---

### Post by rwabel on 2005-07-08
[QUOTE=arunsub]I found out that I have to run ./test.tcl from utils/linux/capture folder. It showing my WinTV go card as the camera. It's not showing my Intel USB PC camera. How do i enable my USB PC camera (Intel) in ubunut?[/QUOTE]
 what's happening when you start gqcam? can you see the picture from your webcam? If you don't have it download via apt-get.
let me know what it says when now picture is coming

---

### Post by arunsub on 2005-07-08
[QUOTE=rwabel]what's happening when you start gqcam? can you see the picture from your webcam? If you don't have it download via apt-get.
let me know what it says when now picture is coming[/QUOTE]
I installed gqcam, but i get the following error when i try to run.
/dev/video: No such file or directory

---

### Post by rwabel on 2005-07-09
[QUOTE=arunsub]I installed gqcam, but i get the following error when i try to run.
/dev/video: No such file or directory[/QUOTE]
 it seems that either you haven't installed your webcam or you get in the same problem. Check one of my older replies. There you can find some ressources and also my blog entry when I've installed the logitech webcam.
I've to do all the time a symlink
 ln -s /dev/video0 /dev/video

I've no idea why it gets removed all the time!

---

### Post by arunsub on 2005-07-09
[QUOTE=rwabel]it seems that either you haven't installed your webcam or you get in the same problem. Check one of my older replies. There you can find some ressources and also my blog entry when I've installed the logitech webcam.
I've to do all the time a symlink
 ln -s /dev/video0 /dev/video

I've no idea why it gets removed all the time![/QUOTE]
I created the symlink. gqcam then showed me my TV connection (Win TV Go) as the source since video0 has that only. It didn't detect my Intel PC Camera.

---

### Post by arunsub on 2005-07-09
[QUOTE=rwabel]it seems that either you haven't installed your webcam or you get in the same problem. Check one of my older replies. There you can find some ressources and also my blog entry when I've installed the logitech webcam.
I've to do all the time a symlink
 ln -s /dev/video0 /dev/video

I've no idea why it gets removed all the time![/QUOTE]
I downloaded spca5xx-20050701.tar.gz and untared it. it then did sudo make and got the following error.
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/prabha/download/spca5xx-20050701 modules
make: *** /lib/modules/2.6.10-5-386/build: No such file or directory.  Stop.
make: *** [default] Error 2

---

### Post by rwabel on 2005-07-09
[QUOTE=arunsub]I downloaded spca5xx-20050701.tar.gz and untared it. it then did sudo make and got the following error.
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/prabha/download/spca5xx-20050701 modules
make: *** /lib/modules/2.6.10-5-386/build: No such file or directory.  Stop.
make: *** [default] Error 2[/QUOTE]
 first of all, I don't know if spca is the right driver for your webcam. You have to google around.
about the error message, you need the kernel source package

---

### Post by arunsub on 2005-07-09
I couldn't find any other driver for my webcam when i googled. how do i get the kernel source? Just getting the kernel source is enough or do i have to recompile the kernel? If i have to recompile, then i don't want to take that risk.

---

### Post by rwabel on 2005-07-09
[QUOTE=arunsub]I couldn't find any other driver for my webcam when i googled. how do i get the kernel source? Just getting the kernel source is enough or do i have to recompile the kernel? If i have to recompile, then i don't want to take that risk.[/QUOTE]
 just download them via apt-get or synaptic. search for the headers for your kernel version. this should be enough. 
btw I guess you have "build-essential" already installed.

---

### Post by arunsub on 2005-07-10
[QUOTE=rwabel]just download them via apt-get or synaptic. search for the headers for your kernel version. this should be enough. 
btw I guess you have "build-essential" already installed.[/QUOTE]
When i searched for kernel in synaptic, i got one entry for kernel-pacakage with version as 8.119ubuntu3 and another entry as kernel-source-2.4.27 and version as 2.4.27-9. My kernel version number is 2.6.10-5-386. How do i get the kernel source and where do i put that?

---

### Post by rwabel on 2005-07-11
[QUOTE=arunsub]When i searched for kernel in synaptic, i got one entry for kernel-pacakage with version as 8.119ubuntu3 and another entry as kernel-source-2.4.27 and version as 2.4.27-9. My kernel version number is 2.6.10-5-386. How do i get the kernel source and where do i put that?[/QUOTE]
 kernel-package is needed for building Linux kernel related Debian packages. That one you probably need too.
you need to get the linux-source-2.x.x.x in your case it would be linux-source-2.6.10 and the respectiv linux-headers

---

### Post by arunsub on 2005-07-11
[QUOTE=rwabel]kernel-package is needed for building Linux kernel related Debian packages. That one you probably need too.
you need to get the linux-source-2.x.x.x in your case it would be linux-source-2.6.10 and the respectiv linux-headers[/QUOTE]
How do I get the source and the headers? I didn't find any in synaptic. 
Where do I (to which directory) install/copy them?

---

### Post by rwabel on 2005-07-11
[QUOTE=arunsub]How do I get the source and the headers? I didn't find any in synaptic. 
Where do I (to which directory) install/copy them?[/QUOTE]
 when you open synaptic and search for linux-source you should get some results. Same for kernel-package.
you then mark them click on apply and install them. It installs it automatically where it has to be installed.

---

### Post by arunsub on 2005-07-11
I'll go home, check and update you in the evening. Thanks.

---

### Post by arunsub on 2005-07-11
I install source, headers etc. i then did make and make install in spca5xx-20050701 folder. i then created symlink for /dev/video. 
ls -al /dev/video
lrwxrwxrwx  1 root root 11 2005-07-11 18:35 /dev/video -> /dev/video0
ls -al /dev/video0
crw-rw----  1 root video 81, 0 2005-07-10 16:17 /dev/video0

I ran gqcam and i still get hauppauge tv card only. I didn't get IBM PC camera. 

lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 003: ID 8086:0110 Intel Corp. Easy PC Camera
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

Is the device installed in different folder under /dev?

---

### Post by rwabel on 2005-07-11
[QUOTE=arunsub]I install source, headers etc. i then did make and make install in spca5xx-20050701 folder. i then created symlink for /dev/video. 
ls -al /dev/video
lrwxrwxrwx  1 root root 11 2005-07-11 18:35 /dev/video -> /dev/video0
ls -al /dev/video0
crw-rw----  1 root video 81, 0 2005-07-10 16:17 /dev/video0

I ran gqcam and i still get hauppauge tv card only. I didn't get IBM PC camera. 

lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 003: ID 8086:0110 Intel Corp. Easy PC Camera
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

Is the device installed in different folder under /dev?[/QUOTE]
 I don't know if spca5xx is the correct driver for your webcam.

Does```
 lsmod | grep usb
``` and ```
lsmod | grep videodev
``` show your driver

---

### Post by arunsub on 2005-07-11
[QUOTE=rwabel]I don't know if spca5xx is the correct driver for your webcam.

Does```
 lsmod | grep usb
``` and ```
lsmod | grep videodev
``` show your driver[/QUOTE]

This is what i got.

lsmod | grep usb
usblp                  12032  0
usbcore               107384  4 usblp,ehci_hcd,ohci_hcd

lsmod | grep videodev
videodev                9728  1 bttv

---

### Post by polo_step on 2005-07-11
[QUOTE=arunsub]This is what i got.

lsmod | grep usb
usblp                  12032  0
usbcore               107384  4 usblp,ehci_hcd,ohci_hcd

lsmod | grep videodev
videodev                9728  1 bttv[/QUOTE]
Purely for comparison purposes, this is what I got for an actual IBM webcam that is supposed to be supported by the "ibmcam" driver, but doesn't actually work properly under any circumstances and not at all in most programs:

anonymous@beatdown:~$ lsmod | grep usb
usbvideo               25988  1 ibmcam
videodev                9728  1 usbvideo
usbcore               107384  5 ibmcam,usbvideo,ehci_hcd,ohci_hcd
anonymous@beatdown:~$ lsmod | grep videodev
videodev                9728  1 usbvideo

---

### Post by rwabel on 2005-07-11
[QUOTE=arunsub]This is what i got.

lsmod | grep usb
usblp                  12032  0
usbcore               107384  4 usblp,ehci_hcd,ohci_hcd

lsmod | grep videodev
videodev                9728  1 bttv[/QUOTE]
 usblp: USB driver for printer
this means that the usb webcam didn't got recognized

bttv: that's the hauppauge wintv

the driver is the right one!

try to load the module with ```
sudo insmod spca5xx.o
``` or maybe the name is different. probabely for the new kernel it's .ko
 and then try again to see if the webcam is there.

---

### Post by arunsub on 2005-07-12
[QUOTE=rwabel]usblp: USB driver for printer
this means that the usb webcam didn't got recognized

bttv: that's the hauppauge wintv

the driver is the right one!

try to load the module with ```
sudo insmod spca5xx.o
``` or maybe the name is different. probabely for the new kernel it's .ko
 and then try again to see if the webcam is there.[/QUOTE]

sudo insmod spca5xx.o
insmod: error inserting 'spca5xx.o': -1 Invalid module format

sudo insmod spca5xx.ko
insmod: error inserting 'spca5xx.ko': -1 File exists

---

### Post by rwabel on 2005-07-14
[QUOTE=arunsub]sudo insmod spca5xx.o
insmod: error inserting 'spca5xx.o': -1 Invalid module format

sudo insmod spca5xx.ko
insmod: error inserting 'spca5xx.ko': -1 File exists[/QUOTE]
 strange, that means spca5xx.ko is already loaded. I'm getting a bit out of my knowledge. What happens, when you remove the wintv card? Maybe it troubles the webcam, would be astonishing...but I've no more ideas.

---

### Post by arunsub on 2005-07-14
[QUOTE=rwabel]strange, that means spca5xx.ko is already loaded. I'm getting a bit out of my knowledge. What happens, when you remove the wintv card? Maybe it troubles the webcam, would be astonishing...but I've no more ideas.[/QUOTE]
I'll try that this weekend.

---

### Post by st0ic on 2005-07-30
Has anyone gone futher with this?  I am currently gettng this error message

insmod: error inserting 'spca5xx.ko': -1 Unknown symbol in module

when I run insmod spca5xx.ko

thanks

---

### Post by arunsub on 2005-07-31
I didn't get time to take out my wintv card and try. I'm going to use windows for time being.

Edit: I meant I use Windows for video conference. I use Ubuntu for normal use.

---

### Post by Kimm on 2005-08-01
st0ic, I get the exact same error... no idea what causes it, any idea anyone?

---

### Post by Kimm on 2005-08-01
Ok, I solved the problem, before you load the module, type:

'sudo modprobe videodev'

in the terminal... then load the module. I got it working like that... for one reboot, first GnomeMeeting fonund th device as /dev/video0 but couldnt use it. Now /dev/video0 doesnt exist anymore...

any ideas?

---

### Post by trollzor on 2005-08-02
Just a quick note to people out there needing help who have webcams which register with a Vendor Id 0x46d of and a Product Id of 0x840, 0x850, or 0x870 to a "lsusb", I have written a HOWTO for logitech and labtec webcams that match those ids, and a little bit on getting gnomemeeting working for them.

HOWTO is [here](http://ubuntuforums.org/showthread.php?t=53755)

cheers, 

Trollzor

---

### Post by polo_step on 2005-08-02
[QUOTE=Kimm]Ok, I solved the problem, before you load the module, type:

'sudo modprobe videodev'[/QUOTE]
This doesn't help my GnomeMeeting to find the camera on /dev/video0, where it is.  I have no idea why.

Where's the bug?

Here's the debug file.  Note that the camera is found and everything is seemingly OK until it gets down to the "started listener" part, and then is erros out saying it can't find the device on /dev/video0:
======================================
anonymous@beatdown:~$ gnomemeeting -d4
2005/08/02 02:18:10.396   0:00.222                 gnomemeeting Detected audio plugins: ALSA,Quicknet
2005/08/02 02:18:10.406   0:00.237                 gnomemeeting Detected video plugins: Picture,V4L2
2005/08/02 02:18:10.428   0:00.253                 H323 Cleaner H323    Started cleaner thread
2005/08/02 02:18:12.497   0:02.323                 gnomemeeting Detected the following audio input devices: SiS SI7012,Default with plugin ALSA
2005/08/02 02:18:12.519   0:02.354                 gnomemeeting Detected the following audio output devices: SiS SI7012,Default with plugin ALSA
2005/08/02 02:18:12.549   0:02.385                 gnomemeeting Detected the following video input devices: /dev/video0,/dev/video0 with plugin V4L2
2005/08/02 02:18:13.323   0:03.150                 gnomemeeting GnomeMeeting version 1.2.1
2005/08/02 02:18:13.330   0:03.166                 gnomemeeting OpenH323 version 1.15.3
2005/08/02 02:18:13.347   0:03.183                 gnomemeeting PWLIB version 1.8.4
2005/08/02 02:18:13.363   0:03.199                 gnomemeeting GNOME support enabled
2005/08/02 02:18:13.379   0:03.215                 gnomemeeting Fullscreen support enabled
2005/08/02 02:18:13.396   0:03.232                 gnomemeeting DBUS support disabled
2005/08/02 02:18:13.412   0:03.248                 gnomemeeting Quicknet hardware support enabled
2005/08/02 02:18:13.444   0:03.269                 gnomemeeting Set TCP port range to 3000030010
2005/08/02 02:18:13.451   0:03.286                 gnomemeeting Set RTP port range to 50005016
2005/08/02 02:18:13.468   0:03.303                 gnomemeeting Set UDP port range to 50205023
2005/08/02 02:18:16.359   0:06.184                 gnomemeeting H323    FindCapability: "iLBC-13k3{sw}"
2005/08/02 02:18:16.366   0:06.220                 gnomemeeting H323    Added capability: iLBC-13k3{sw} <1>
2005/08/02 02:18:16.404   0:06.240                 gnomemeeting H323    FindCapability: "MS-GSM{sw}"
2005/08/02 02:18:16.421   0:06.258                 gnomemeeting H323    Added capability: MS-GSM{sw} <2>
2005/08/02 02:18:16.440   0:06.275                 gnomemeeting H323    FindCapability: "SpeexNarrow-15k{sw}"
2005/08/02 02:18:16.457   0:06.294                 gnomemeeting H323    Added capability: SpeexNarrow-15k{sw} <3>
2005/08/02 02:18:16.477   0:06.313                 gnomemeeting H323    FindCapability: "iLBC-15k2{sw}"
2005/08/02 02:18:16.495   0:06.350                 gnomemeeting H323    Added capability: iLBC-15k2{sw} <4>
2005/08/02 02:18:16.533   0:06.369                 gnomemeeting H323    FindCapability: "GSM-06.10{hw}"
2005/08/02 02:18:16.550   0:06.406                 gnomemeeting H323    FindCapability: "GSM-06.10{sw}"
2005/08/02 02:18:16.587   0:06.423                 gnomemeeting H323    Added capability: GSM-06.10{sw} <5>
2005/08/02 02:18:16.616   0:06.441                 gnomemeeting H323    FindCapability: "SpeexNarrow-8k{sw}"
2005/08/02 02:18:16.623   0:06.461                 gnomemeeting H323    Added capability: SpeexNarrow-8k{sw} <6>
2005/08/02 02:18:16.643   0:06.479                 gnomemeeting H323    FindCapability: "G.726-32k{sw}"
2005/08/02 02:18:16.661   0:06.517                 gnomemeeting H323    Added capability: G.726-32k{sw} <7>
2005/08/02 02:18:16.699   0:06.555                 gnomemeeting H323    FindCapability: "G.711-uLaw-64k{hw}"
2005/08/02 02:18:16.737   0:06.573                 gnomemeeting H323    FindCapability: "G.711-uLaw-64k{sw}"
2005/08/02 02:18:16.756   0:06.613                 gnomemeeting H323    Added capability: G.711-uLaw-64k <8>
2005/08/02 02:18:16.795   0:06.630                 gnomemeeting H323    FindCapability: "G.711-ALaw-64k{hw}"
2005/08/02 02:18:16.812   0:06.669                 gnomemeeting H323    FindCapability: "G.711-ALaw-64k{sw}"
2005/08/02 02:18:16.851   0:06.687                 gnomemeeting H323    Added capability: G.711-ALaw-64k <9>
2005/08/02 02:18:16.901   0:06.726                 gnomemeeting H323    Added capability: H.261-QCIF <10>
2005/08/02 02:18:16.909   0:06.765                 gnomemeeting H323    Added capability: H.261-CIF <11>
2005/08/02 02:18:16.948   0:06.784                 gnomemeeting H323    Added capability: UserInput/hookflash <12>
2005/08/02 02:18:16.967   0:06.839                 gnomemeeting H323    Added capability: UserInput/basicString <13>
2005/08/02 02:18:17.023   0:06.879                 gnomemeeting H323    Added capability: UserInput/dtmf <14>
2005/08/02 02:18:17.061   0:06.897                 gnomemeeting H323    Added capability: UserInput/RFC2833 <15>
2005/08/02 02:18:17.139   0:06.964                 gnomemeeting H323    Started listener Listener[ip$*:1720]
2005/08/02 02:18:17.310   0:07.135        H323 Listener:83de3f8 H323    Awaiting TCP connections on port 1720
2005/08/02 02:18:17.319   0:07.166        H323 Listener:83de3f8 TCP     Waiting on socket accept on ip$*:1720
Killed
anonymous@beatdown:~$

---

### Post by arunsub on 2005-08-02
I finally made my Intel PC Camera to work.  :smile: 
Here is the site that shows the list of video cam supported by Linux (total 332 records). [http://www.qbik.ch/usb/devices/showdevcat.php?id=9](http://www.qbik.ch/usb/devices/showdevcat.php?id=9) I downloaded the latest driver from here: [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html) (Did that before i started asking questions in this thread). I followed some of the instructions given in the README file after i untarred the file. Here is the part of it:
How do I use it?
================

Well, first you need to compile the driver (see below), then you need to make
sure that the v4l infrastructure is set up and then load the driver. After
you've done that, any v4l enabled application, such as spcaview, gqcam, xawtv,
gnomemeeting, camE etc should work.


Supported kernel versions
=========================
The driver should compile and run successfully against most stable versions of
the official Linux kernel (from <http://www.kernel.org/>), within the range
2.4.10 to 2.6.11 inclusive.should work with kernel 2.4 < 2.4.10 and 2.6.12 please report
your results
		--------------------------------------------------------
		-Distro patched Kernel should work but are unsupported.-
		--------------------------------------------------------
Specifically, it has been tested against:
 2.4.10		 Compiles ok, with 1 warning
 2.4.25		 Compiles ok, with 1 warning.	
 2.4.26		 Compiles ok, with 1 warning.	
/lib/modules/2.4.25/build/include/linux/highmem.h: Dans la fonction « bh_kmap »:
/lib/modules/2.4.25/build/include/linux/highmem.h:20: attention : usage en arithmétique d'un pointeur de type « void * »
Don't care module should load and works fine  :) 
 2.6.7		 Compiles ok, with no warnings.
 2.6.8.1	 Compiles ok, with no warnings.
 2.6.9		 Compiles ok, with no warnings.
 2.6.11.7	 Compiles ok, with no warnings.
 KERNEL 2.6.3 is UNSUPPORTED !!
Compiling it
============
The driver module can be built without modifying your kernel source tree.

Before trying to compile the driver, ensure that you've configured your
kernel, and updated the dependencies:
'make [config|menuconfig|xconfig]; make dep'.

Make sure, when compiling the driver, you use the same version of compiler as
was used to compile your kernel. Not doing so can create incompatible binaries.

If you wish to compile the driver against a kernel other than the currently
installed one, build the driver with
'make KINCLUDE=/usr/src/linux-<version>/include', or similar.

Please note, the default location for the kernel, according to the driver, is
/usr/src/linux.

To build just the driver, simply use 'make'.
Compiling against the linux kernel 2.4 source tree, there should be no
warnings at all.


This version of the driver offers an automatic installation facility.
Use 'make install' to have the driver installed into your kernel modules
directory, which is assumed to be /lib/modules/<version>/kernel/drivers/usb.
<version> is picked up from the currently running kernel, so if that's not
the right place, then don't use 'make install'!


Making sure the usb and v4l stuff is there
==========================================
For the module to function correctly, the video for linux subsystem needs to
be loaded. As root, check the output of lsmod for videodev. If its not there,
do: modprobe videodev.
Also, you need to make sure that the usbcore module is loaded (or compiled
into your kernel) and similarly the module appropriate for your usb controller
(uhci or ohci).


Loading it
==========
If you have compiled the module, but haven't done 'make install' you can load
the module in the top build directory by doing as root: insmod spca5xx.o

If you have made install, do as root: modprobe spca5xx

There are several parameter that can be passed in:

  force_rgb = 1 Set reverse rgb order
  OffRed    = -16 Initial red   offset -16  range [-128..+128]
  OffBlue   = -16 Initial blue  offset -16  range [-128..+128]
  OffGreen  = -16 Initial green offset -16  range [-128..+128]
  GRed      = 256 Initial gain setting to 1 range [0..512]
  GBlue     = 256 Initial gain setting to 1 range [0..512] 
  GGreen    = 256 Initial gain setting to 1 range [0..512] 
  gamma     = 3 Set gamma table to 1 range [0..7]
  
  usbgrabber = 1 if you use an usb grabber usbid 0x0733:0x430 otherwise
  usbgrabber=0
 
  debug=<n>   <-- set debug level 
  
  ccd=0       <-- SPCA505 only. Switch between the internal CCD (zero) and
                  the external video input (non-zero)
  osd=1       <-- Enable on-screen display if kernel patches applied
                  (see below)
 special note for kernel 2.6.x users:
 you can change the parameters trought sysfs you need to be root
	echo "1" > /sys/module/spca50x/gamma
	change the gamma parameters to 1
	to read a parameters
	cat /sys/module/spca50x/gamma
	
	

***********************************************************************
Remember to use
   insmod spca5xx.o usbgrabber=1 for for an usb grabber usbid 0x733:0x430
for Intel PC Camera Pro set usbgrabber to 0 
***********************************************************************

Here is the list of commands i issued. Some worked and some didn't, but it doesn't matter because gqcam finally showed my webcam.
download the driver and untar
go to that folder
make
lsmod | grep videodev
sudo modprobe videodev
ln -s /dev/video0 /dev/video
sudo modprobe videodev
sudo insmod spca5xx.o
sudo make install
sudo lsmod | grep videodev
sudo insmod spca5xx.o usbgrabber=1
gqcam

---

### Post by Kimm on 2005-08-03
I finly got my Creative Webcam NX working
amsn can use it, ad spcaview can use it... but not gnomemeeting, any ideas?

---

### Post by arunsub on 2005-08-03
I'm getting all wierd error messages while booting (sometimes doesn't boot) after fixing my webcam problem. I didn't have time to check the error messages and the reason.

edit: I tried starting the system during the lunch time and the regular boot didn't work. I then started it in the safe (recovery) mode. It told me that some corruption with the file system or something and told me to manually run fsck. I ran fsck and it asked me if i want to fix problems one by one and after it fixed the problem, i rebooted the machine and it worked fine. When i tried to open firefox or thunderbird after 3 hours, nothing is happening. Do you think compiling the driver corrupted the file system or kernel?

---

### Post by polo_step on 2005-08-03
[QUOTE=Kimm]I finly got my Creative Webcam NX working
amsn can use it, ad spcaview can use it... but not gnomemeeting, any ideas?[/QUOTE]
I dunno.  If we keep asking, eventually someone will answer, I suppose.

See my post & debug file.  My IBM webcam "works" in Xawtv (somewhat - bad color & no autoexposure, plus load errors), is on /dev/video0, but GnomeMeeting errors out as unable to load /dev/video0.

My intuitive take is that this is a misleading "generic" error, that it IS finding it, but is having some other problem.

There's a [GnomeMeeting mailing list](http://mail.gnome.org/mailman/listinfo/gnomemeeting-list) linked from their site.  I went through a few months of archives and saw nothing relevant to this problem, but you might join it and ask them.

---

### Post by chillibow123 on 2005-08-26
which version of aMSN supports webcams because i have .94 and it didnt work

---

### Post by rwabel on 2005-08-26
[QUOTE=chillibow123]which version of aMSN supports webcams because i have .94 and it didnt work[/QUOTE]
 you need the cvs version from their webpage

---

### Post by arunsub on 2005-08-26
It's version 0.95b. You have to get it from CVS, but I'm having problem accessing their site.

---

### Post by chillibow123 on 2005-08-26
whats the site?

---

### Post by arunsub on 2005-08-26
[QUOTE=chillibow123]whats the site?[/QUOTE]
amsn.sourceforge.net

---

### Post by rwabel on 2005-08-26
[QUOTE=chillibow123]whats the site?[/QUOTE]
 [http://amsn.sourceforge.net/](http://amsn.sourceforge.net/)

---

### Post by cowlip on 2005-08-28
[QUOTE=Kimm]I finly got my Creative Webcam NX working
amsn can use it, ad spcaview can use it... but not gnomemeeting, any ideas?[/QUOTE]

Hi Kimm, can you just post a link or something to show me how you got it to work?  I, too, have a creative webcam nx ;)

---

### Post by cowlip on 2005-08-28
[QUOTE=cowlip]Hi Kimm, can you just post a link or something to show me how you got it to work?  I, too, have a creative webcam nx ;)[/QUOTE]
 Oh I fixt it myself.  PS: Kopete now has MSN webcam support [http://bugs.kde.org/show_bug.cgi?id=70538](http://bugs.kde.org/show_bug.cgi?id=70538)

---

### Post by rwabel on 2005-08-29
[QUOTE=cowlip]Oh I fixt it myself.  PS: Kopete now has MSN webcam support [http://bugs.kde.org/show_bug.cgi?id=70538](http://bugs.kde.org/show_bug.cgi?id=70538)[/QUOTE]
 sounds great! how do we install the msn plugin or does it already work with the breezy version of kopete?

---

### Post by oofnik on 2005-08-30
Hey guys, I FINALLY got my Intel webcam working using the spca5xx driver. I must've compiled it about 30 times total, haha.

I kept getting this funky error from dmesg:
```
/home/oofnik/spca5xx-20050701/drivers/usb/spca5xx.c: spca5xx driver 00.57.00 registered
usb 5-8.1: new full speed USB device using ehci_hcd and address 8
/home/oofnik/spca5xx-20050701/drivers/usb/spca5xx.c: USB SPCA5XX camera found. Type Intel PC Camera Pro (SPCA505+SAA7113)
/home/oofnik/spca5xx-20050701/drivers/usb/spca5xx.c: [spca5xx_probe:8652] Camera type YYUV
```
Well that's the good part. It found and recognized the camera. But then:
```
/home/oofnik/spca5xx-20050701/drivers/usb/spca5xx.c: init isoc: usb_submit_urb(0) ret -12
/home/oofnik/spca5xx-20050701/drivers/usb/spca5xx.c: [spca5xx_open:4589]  DEALLOC error on init_Isoc
```
Ah! What the heck does that mean...
So I just copied some of that, fed it to Google, and came upon some forum that said that the camera has to be plugged in DIRECTLY TO THE COMPUTER! NO HUBS!
So that's what I did:
```
usb 5-8.1: USB disconnect, address 8
usb 3-1: new full speed USB device using uhci_hcd and address 2
/home/oofnik/spca5xx-20050701/drivers/usb/spca5xx.c: USB SPCA5XX camera found. Type Intel PC Camera Pro (SPCA505+SAA7113)
/home/oofnik/spca5xx-20050701/drivers/usb/spca5xx.c: [spca5xx_probe:8652] Camera type YYUV
```
Okay good. I want to try gqcam, so:
```
gqcam -v /dev/video0
```
And it works!  :-)  :-) 
I hope I helped some of you out with this, becuase it sure was giving me a hard time.

---

### Post by arunsub on 2005-08-30
Can you write a HOWTO to do this? I got my system screwed last time when i tried to install spcaxxxx driver. I'll appreciate if you can write a HOWTO.

---

### Post by oofnik on 2005-08-30
How did you screw up your system? You mean to the point where it wouldn't boot?
All I did basically was follow the wiki howto: [https://wiki.ubuntu.com/Spca5xx](https://wiki.ubuntu.com/Spca5xx)
However, the wiki states that you need to download the entire kernel source and recompile it... no. All you need is the kernel headers, a package that you can download easily with synaptic. Just make sure you get the right headers for whatever kernel you're running (default for Hoary 5.04 is 2.6.10-5-386 I'm pretty sure). You should be able to follow from step 4. Just remember, the camera has to be plugged directly into the computer and not an external hub. I don't have any idea why but that's the only way it works for me. Good luck!

---

### Post by arunsub on 2005-08-31
I'll give it a try again. Thanks.  :)

---

### Post by arunsub on 2005-09-12
I tried the wiki and i could install the camera. I have /dev/video0 for my WinTV card and /dev/video1 for my PC camera. I could see my pc camera video in gqcam after installation. I then created a link from /dev/video1 to /dev/video to use it in AMSN. When i rebooted the machine after some time, both /dev/video0 and /dev/video1 had WinTV card only. it didn't show the video from my PC camera. I didn't have time to check why. Do I have to modprobe or insmod or something every time i boot my machine?

---

### Post by DizzyWeb on 2005-10-11
[QUOTE=rwabel]sounds great! how do we install the msn plugin or does it already work with the breezy version of kopete?[/QUOTE]
It doesn't, not even with the updated version in KDE3.5 beta. You'll have to get the SVN version and compile... I'm reluctant to update it. It's impossible to remove kopete without removing kubuntu-desktop and I really don't want to do so. I could install it to some other location (/opt or something) but having two versions of kopete doesn't really sound that good.

Does anybody know how to build a .deb out of an SVN version easily? So I can update the kopete package?

---

