---
title: "[SOLVED] dvd playback problems"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by ahounsome on 2008-03-14
Am running kde 3.5.8 and various flavours of xine, including kaffeine and codeine, but cannot get regular shop bought dvd's to play no matter what package I use.I get the error message "the source cant be read error reading NAV packet. Any ideas anyone?

---

### Post by dca on 2008-03-14
Are you sure 'libdvdcss2' package installed?
 
Don't know which version is needed but I think you can get it here...
 
[http://download.videolan.org/pub/libdvdcss/1.2.9/deb/](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/)

---

### Post by t0p on 2008-03-14
**vlc** is a great media player, it comes with all the codecs needed to play DVDs and just about every other media file type you're likely to want to watch!!  I use nothing else!!

---

### Post by ahounsome on 2008-03-14
No luck I'm afraid - neither option worked. Using vlc spins up the dvd but no playback.

---

### Post by mc4man on 2008-03-14
Have you ever played a dvd (commercial) in that drive either in windows or linux ?

---

### Post by ahounsome on 2008-03-14
no, the laptop was released to me from my employer with the latest gutsy build. I have since installed all the updates available (apt-get update) and a variety of media players. An avi plays fine from the onboard dvd.

---

### Post by dca on 2008-03-14
I'm at a loss, that's they only time I remember seeing that error message was in Gnome Ubuntu w/ Totem (Xine vers) installed...  It needed the libdvdcss to eliminate that NAV message...  If nobody else is able to throw in some ideas you can put "error reading NAV packet" in Google search and see if anyone else using other Linux distros had similar problems.  Be careful w/ package installs, though.  People could be using RPM-based packages...

---

### Post by mc4man on 2008-03-14
What you should check is that the drive is set to a dvd region - for encrypted disks it must be set
In synaptic search and install regionset
With a commercial (encrypted) disk in drive and mounted (icon on desktop) run in terminal
sudo regionset
If no region is set -  set it to your region 
post back if you don't know your region   most likely  - N. america - 1.  europe - 2 or  if not clear on anything

edit :if it is set to a region exit out with no changes and post make and model of drive - places>computer right click drive and in  properties will show info

---

### Post by ahounsome on 2008-03-14
ok thanks. I dont get rpm packages - how do I open them? I have found a supposed solution to the issue with commercial dvds  but it is an rpm package.

---

### Post by ahounsome on 2008-03-14
ok thanks for that. I have successfully changed the region code to 2 - but still no joy. It's a british released dvd so I guess it must be region2. What now?

---

### Post by mc4man on 2008-03-14
run vlc from the terminal - under file choose open disk and post the output from terminal

---

### Post by kenny1948 on 2008-03-14
I don't mean to break in on this thread, but I am having the same problem.

Tried to run the regionset command and got this:
ken@ken-desktop:~$ sudo regionset
sudo: regionset: command not found
ken@ken-desktop:~$ sudo totem regionset

sh: jackd: not found

** (totem:12405): WARNING **: Failed to connect to the session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

** (totem:12405): WARNING **: Error connecting to D-Bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
** Message: Error: Resource not found.
gstfilesrc.c(971): gst_file_src_start (): /play/source:
No such file "/home/ken/regionset"


Does anyone understand this?
Unfortunately I am not a computer genius. I cannot play any DVD's commercial or made on my computer. I have loaded all the supposedly necessary plugins, and codecs. 

I am in the USA, could this be the problem. I know that we use NTSC in this region.

I'm really frustrated, as one of the main uses of my computer in the past was to make video CD's and had wanted to make DVD's.:confused:

---

### Post by mc4man on 2008-03-14
@ kenny - you need to install regionset first - if region is set don't change - exit out with n. For troubleshooting vlc is best - install and run in terminal, ect.
note - you can run regionset without sudo
@ahounsome - go to home folder, enable hidden dir. (ctrl h) and find .dvdcss folder. Inside will be files named after dvd's you've tried to play - delete them and try vlc again

---

### Post by crjackson on 2008-03-14
> **ahounsome said:**
> Am running kde 3.5.8 and various flavours of xine, including kaffeine and codeine, but cannot get regular shop bought dvd's to play no matter what package I use.I get the error message "the source cant be read error reading NAV packet. Any ideas anyone?

Here, try this...

Go to SYSTEM>ADMINISTRATION>SOFTWARE SOURCES and enable the extra repositories first...

Start from scratch and don't worry if you've already done some of this before.  It will just skip any uneeded items.  This is for 32-bit Gutsy...

Go to your menu - Applications>Accessories>Terminal and click!

Next cut and paste the following into the terminal screen.

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w32codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```

---

### Post by swatsbiz on 2008-03-15
I had the same problem, this solved it for me, and even fixed a motherboard sound problem I was having ... the mic port was switched with the sound port ... and the front panel sound did not work at all ... but all sorted now magically :D

---

### Post by ahounsome on 2008-03-15
excellent! thanks very much for that. Video playback works fine - however, I have no audio! Any ideas?

---

### Post by ahounsome on 2008-03-15
HELP! I've no audio output at all now!:confused:

---

### Post by ahounsome on 2008-03-15
OK I've fixed it! There's a post here that did the trick. Hope it can benefit anyone else with a Lenovo T43 and no sounfd:-

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller:guitar:](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller:guitar:)

---

