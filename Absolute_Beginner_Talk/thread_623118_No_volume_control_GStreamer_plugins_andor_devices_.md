---
title: "No volume control GStreamer plugins and/or devices found."
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by Saurabh0704 on 2007-11-25
my volume control was doing well since last 2-3 hours earlier now it shows this message when i click on volume button
I am using gutsy
and it was working well since last two days
i shutdown my comp and when started it after an hour it shows this error i have also rebooted it but it is consistensely showing this
How can i rectify this??

---

### Post by Pumalite on 2007-11-25
Did you update or are you using a different kernel?
Post this please:
sudo lshw -C sound
uname -r

---

### Post by StJack on 2007-11-25
I'm not the original poster, but I'm having the same problem.

Can't ssh in from this computer (don't get me started) but here's what I get when I run sudo lshw -C sound:

*-multimedia UNCLAIMED
   description: Multimedia audio controller
   product: 5880 AudioPCI
   vendor: Ensoniq
   physical id: 9
   version: 02
   width: 32 bits
   clock: 33MHz
   capabilities: pm cap_list
   configuration: latency=64 maxlatency=128 mingt=12

I ran uname -r and got:

2.6.22-14-server

any suggestions?  No sound, plus I get the message that no audio devices/mixers installed.

I've run the master comprehensive guide, to no avail.

aplay -l gives me
aplay: device_list:204 no soundcards found...

lspci -v gives me a bunch of results, including that it recognizes the card, but can't play

---

### Post by repran on 2007-12-08
I have exact the same problem - did not touch anything:

  *-multimedia UNCLAIMED  
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
stefan@stefan-desktop:~$ uname -r
2.6.22-14-generic
stefan@stefan-desktop:~$ 

many thanks!

---

### Post by lswest on 2007-12-08
i had that problem a couple of hours ago (i was trying to set up my headphone jacks right, then everything went awry:P)  my fix is this:
1) go to [this site]("http://alsa-project.org/main/index.php/Main_Page")
2) download the alsa-driver-1.0.15 files.
3) extract to a folder
4) in a terminal do ```
cd [location of alsa-driver]
```
5) in a terminal run ```
./configure
``` (this requires the build-essential package installed, if it is not run ```
sudo apt-get install build-essential
``` and the linux-headers (if missing install with ```
sudo apt-get install linux-headers
```
6) in the terminal run ```
make
```
7) then run ```
sudo make install
``` in the terminal

this then re-installs the default drivers for soundcards, should get it all working again.

---

### Post by tomm3h on 2007-12-09
I'm having the exact same problem. The biggest kick in the teeth is that the login sound plays just fine, yet the volume control applet reports that there are no Gstreamer compatible devices, and Amarok just says that the audio output device is busy.

The card is the on-board soundcard included with the DFI NF4 SLI boards. Supported by the intel8x0 alsa driver.

Alsamixer works fine, and I've recompiled alsa-source (from respository) after following the comprehensive sound problems guide, to no effect.

Will have a go with the latest Alsa drivers, but I'm not convinced that's the problem :(

---

### Post by tomm3h on 2007-12-09
> **tomm3h said:**
> I'm having the exact same problem. The biggest kick in the teeth is that the login sound plays just fine, yet the volume control applet reports that there are no Gstreamer compatible devices, and Amarok just says that the audio output device is busy.

The card is the on-board soundcard included with the DFI NF4 SLI boards. Supported by the intel8x0 alsa driver.

Alsamixer works fine, and I've recompiled alsa-source (from respository) after following the comprehensive sound problems guide, to no effect.

Will have a go with the latest Alsa drivers, but I'm not convinced that's the problem :(
And I've fixed it! There's another thread on here with a link to a blog post.

General jist of it is; due to a bug in Gnome, users sometimes get removed from the 'audio' group and thus have no permissions for /dev/snd (read or otherwise.)

There's a gui way to fix it: run 'gksu users-admin' and make sure that your user account has access to sound devices.

Or alternatively you can user 'users-mod' to add yourself to the audio group (man users-mod for usage.)

It's always permissions isn't it :p

---

### Post by frfrfr on 2008-02-14
Hmmm, there's always one guy with the 'extra problem' and it's me this time.

In the group manager I get multiple identical entries, all entries have root and me disabled. When I click one of the two users (root or me) to add them to a group, it's erased next time I view that group.

To make things worse, when I boot in rescue mode and edit /etc/groups everything appears to be normal.

I pretty much  re-installed everything: Gstreamer, went back to generic kernel, went to alsa 1.0.14 with recompilation, ... zip result. Still no audio. 

```

aplay -l

aplay: device_list:207: no soundcards found...
```

```

lspci -v

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Fujitsu Siemens Computer GmbH Unknown device 10ac
        Flags: bus master, fast devsel, latency 0, IRQ 4
        Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```

the /etc/groups:
```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:frpuy
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:frpuy
fax:x:21:
voice:x:22:
cdrom:x:24:haldaemon,frpuy
floppy:x:25:haldaemon,frpuy
tape:x:26:
sudo:x:27:
audio:x:29:frpuy,root
dip:x:30:frpuy
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:frpuy
sasl:x:45:
plugdev:x:46:haldaemon,frpuy
staff:x:50:
games:x:60:
users:x:100:frpuy
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:hplip,frpuy
nvram:x:105:
fuse:x:106:root,frpuy
ssl-cert:x:107:
lpadmin:x:108:frpuy
messagebus:x:109:
admin:x:110:frpuy
crontab:x:111:
ssh:x:112:
avahi-autoipd:x:113:
avahi:x:114:
netdev:x:115:frpuy
haldaemon:x:116:
powerdev:x:117:haldaemon,frpuy
slocate:x:119:
fre:x:1000:
gdm:x:118:
pulse:x:120:frpuy
pulse-access:x:121:
pulse-rt:x:122:
```

To be honest, I'm starting to get fed up with Ubuntu. First I spent a week getting my wireless and video driver installed. Then there was the "load/unload" issue with the APM which made me choose between a deteriorating HD or some dirty hacks. I did the dirty hacks and three days later the system crashed: it didn't shut down on empty battery and the filesystem went corrupt. Now it's this audio thing.

I've been programming & fiddling on computers (mainly Windows) for 16 years now - started with a Commodore 64 - and I've tried Linux at least a dozen times during those years (heck, I still have a box with Minix and Beos somewhere). Nothing has changed. Yes, there are spectacular bells and whistles. But you're f'ed when you're not running a 386DX with 640kb graphics card. Windows is crap - I know - but at least it works and they are liable. If something works in Ubuntu it's because the bug hasn't been activated yet. "Linux for humans" is probably the biggest joke since the millenium bug. How can a bug like this be spread ? The words "testing" and "no" keep popping up in my head. But don't worry, that's all covered by the disclaimer, somewhere.

Great marketing campaign, though: a mix of South Africa, open source and a dash of polarization against Microsoft is a brilliant idea. I'd like to see the face of the teachers in Kenya each time one of these issues pops up. "Sorry 'Mbeele - we don't have internet this week, you'll have to use Windows 95 again."

I've posted my system configs above because google and the rest are clogged with "change the groups and it's fixed" patterns. Hopefully people who have the same experience as me will be able to find the sollution here. I won't need it anymore.

Simon

---

### Post by bionicyeti on 2008-02-14
> To be honest, I'm starting to get fed up with Ubuntu. First I spent a week getting my wireless and video driver installed. Then there was the "load/unload" issue with the APM which made me choose between a deteriorating HD or some dirty hacks. I did the dirty hacks and three days later the system crashed: it didn't shut down on empty battery and the filesystem went corrupt. Now it's this audio thing.



I'm having the exact same problem with the audio drivers so I feel your pain. I just can't quit Ubuntu. ;-)

Non of the solutions above helped me either. :(

I just updated my alsa drivers to the 1.0.16 version. I'm rebooting in a minute. Maybe that will fix it.

---

### Post by bionicyeti on 2008-02-14
It worked.

Installed the 1.0.16 alsa drivers > rebooted and I have my sound back.

Also, when I said none of the solutions above worked, I lied. Looks like lswest solution worked. When he posted it (dec 08) the 1.0.16 drivers probably were not released yet.

---

### Post by ruffnick99 on 2008-02-17
I am having the same problem with my sound.  I downloaded and extracted the drivers to the desktop and when I type ./configure in the terminal it says that there is no such file or directory.  I installed the build essentials package and try to install the headers and it said they were already installed.  Please help.

---

### Post by safesite on 2008-02-26
> **frfrfr said:**
> Hmmm, there's always one guy with the 'extra problem' and it's me this time.

In the group manager I get multiple identical entries, all entries have root and me disabled. When I click one of the two users (root or me) to add them to a group, it's erased next time I view that group.

To make things worse, when I boot in rescue mode and edit /etc/groups everything appears to be normal.

I pretty much  re-installed everything: Gstreamer, went back to generic kernel, went to alsa 1.0.14 with recompilation, ... zip result. Still no audio. 

```

aplay -l

aplay: device_list:207: no soundcards found...
```

```

lspci -v

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Fujitsu Siemens Computer GmbH Unknown device 10ac
        Flags: bus master, fast devsel, latency 0, IRQ 4
        Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```

the /etc/groups:
```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:frpuy
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:frpuy
fax:x:21:
voice:x:22:
cdrom:x:24:haldaemon,frpuy
floppy:x:25:haldaemon,frpuy
tape:x:26:
sudo:x:27:
audio:x:29:frpuy,root
dip:x:30:frpuy
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:frpuy
sasl:x:45:
plugdev:x:46:haldaemon,frpuy
staff:x:50:
games:x:60:
users:x:100:frpuy
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:hplip,frpuy
nvram:x:105:
fuse:x:106:root,frpuy
ssl-cert:x:107:
lpadmin:x:108:frpuy
messagebus:x:109:
admin:x:110:frpuy
crontab:x:111:
ssh:x:112:
avahi-autoipd:x:113:
avahi:x:114:
netdev:x:115:frpuy
haldaemon:x:116:
powerdev:x:117:haldaemon,frpuy
slocate:x:119:
fre:x:1000:
gdm:x:118:
pulse:x:120:frpuy
pulse-access:x:121:
pulse-rt:x:122:
```

To be honest, I'm starting to get fed up with Ubuntu. First I spent a week getting my wireless and video driver installed. Then there was the "load/unload" issue with the APM which made me choose between a deteriorating HD or some dirty hacks. I did the dirty hacks and three days later the system crashed: it didn't shut down on empty battery and the filesystem went corrupt. Now it's this audio thing.

I've been programming & fiddling on computers (mainly Windows) for 16 years now - started with a Commodore 64 - and I've tried Linux at least a dozen times during those years (heck, I still have a box with Minix and Beos somewhere). Nothing has changed. Yes, there are spectacular bells and whistles. But you're f'ed when you're not running a 386DX with 640kb graphics card. Windows is crap - I know - but at least it works and they are liable. If something works in Ubuntu it's because the bug hasn't been activated yet. "Linux for humans" is probably the biggest joke since the millenium bug. How can a bug like this be spread ? The words "testing" and "no" keep popping up in my head. But don't worry, that's all covered by the disclaimer, somewhere.

Great marketing campaign, though: a mix of South Africa, open source and a dash of polarization against Microsoft is a brilliant idea. I'd like to see the face of the teachers in Kenya each time one of these issues pops up. "Sorry 'Mbeele - we don't have internet this week, you'll have to use Windows 95 again."

I've posted my system configs above because google and the rest are clogged with "change the groups and it's fixed" patterns. Hopefully people who have the same experience as me will be able to find the sollution here. I won't need it anymore.

Simon





I couldn't agree more with you and here is why...



[http://ubuntuforums.org/showthread.php?t=694038](http://ubuntuforums.org/showthread.php?t=694038)


So I too have decided (as stated in my thread) to finally go back to Windows. Junk? Maybe! But at least junk you already know...! :biggrin::lolflag:

---

### Post by leehach on 2008-02-27
tomm3h's post had the answer.  It sounded right because I have two users on my computer and one user had sound but the other didn't, so I didn't think there were anything wrong with the drivers.  Went to System-->Administration-->Users and Groups.  Looked at the user's properties on the User Privileges tab, and all the boxes were unchecked.  Checked "Use audio devices" "Use CD-ROM drives", etc.  After reboot, everything worked fine.

---

