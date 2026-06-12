---
title: "DVB device works in dapper/edgy but not in feisty?"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by Yes_It's_Me on 2007-04-17
Hey.

My tv tuner (Leadtek DTV 1000t works fine with kaffeine in both edgy and dapper right out of the box, so how come when i fire up the feisty release candidate and install kaffeine it says that a dvb device is not detected? I know that the card has been supported since the 2.6.15 kernel. I have also had the same issue in the latest test releases for PCLinuxOS.

thanks in advance guys and gals!

---

### Post by bobplano on 2007-04-17
it's probably the drivers. see if you can install the drivers needed from the edgy or dapper cd. you'll need to add the cd to the repos though

---

### Post by Yes_It's_Me on 2007-04-17
what drivers? how would i know what to install?

---

### Post by bobplano on 2007-04-17
hmm it sounds like all you need is the updated kernel 2.6.15. try this link if you already have a kernel number higher or equal to that

[http://www.linuxtv.org/wiki/index.php/First_steps_with_a_DVB_device](http://www.linuxtv.org/wiki/index.php/First_steps_with_a_DVB_device)

---

### Post by Yes_It's_Me on 2007-04-17
how about if i follow this;

[http://www.linuxtv.org/wiki/index.php/HOW_TO_Installing_DVB#Obtain_latest_source](http://www.linuxtv.org/wiki/index.php/HOW_TO_Installing_DVB#Obtain_latest_source)

do you think it will work?

I am using the 2.6.20 kernel so it should work out of the box...

---

### Post by bobplano on 2007-04-17
that looks like it will work fine

---

### Post by Yes_It's_Me on 2007-04-17
ok, stand by...

---

### Post by Yes_It's_Me on 2007-04-17
ok, i get to the end where we compile the firmware, i run the command sudo make install in the directory and i get:

make: *** No targets specified and no makefile found.  Stop.

and i dunno what to do.

---

### Post by bobplano on 2007-04-17
is there a makefile in the directory where the files are? go to the terminal and go to the directories and use ls to check for a makefile, then use sudo make install

---

### Post by Yes_It's_Me on 2007-04-17
they are just a whole lot of .fw files. I don't even know if i downloaded the right firmware, it directed me to:

[http://linuxtv.org/downloads/firmware/](http://linuxtv.org/downloads/firmware/)

and i had no idea whatsoever which one to download, i just assumed it was the dvb-firmwares-1.tar.bz2 one.

---

### Post by bobplano on 2007-04-17
ah i see now. ok you need to run
```
lspci -v
or 
lsusb -v
```
or just look on your device but anyway you do it you need to know what your device is. then you get the firmware and put it in what ever folder your installation used; examples from them  '/lib/firmware'     "/usr/lib/hotplug/firmware/" . then from the source code you downloaded you need to now run (most likely)
```
sudo make uninstall
make
sudo make install
```
where the source code for the drivers are

---

### Post by Yes_It's_Me on 2007-04-17
i've done all of that exept for the last part, when i do it i get the same error.

---

### Post by Yes_It's_Me on 2007-04-17
anyone have any ideas? i really need to get this working.

---

### Post by Yes_It's_Me on 2007-04-18
Please!

---

### Post by Yes_It's_Me on 2007-04-18
*desperate*

---

### Post by Yes_It's_Me on 2007-04-18
last try.

---

### Post by bobplano on 2007-04-18
sorry but last night i was very tired. i don't have much time now but just know i am thinking about this problem.

---

### Post by Azathoth_ on 2007-04-20
I have the same problem... my DVB-T worked in Edgy and Dapper but NOT in Feisty :'(

---

### Post by bobplano on 2007-04-20
ok now that i reread all the posts i think you were trying to compile the firmware. the drivers are the ones you need to compile. 

make sure you have run this:
```
sudo apt-get install mercurial linux-headers-$(uname -r) build-essential gcc make
```

then to get the drivers and compile them:
```
hg clone http://linuxtv.org/hg/v4l-dvb
cd v4l-dvb
make 
sudo make install
```

now you are done with the drivers. to install the firmware you need to run
```
lspci -v
``` 
or
```
lsusb -v
```

once you know which firmware to get you need to download that firmware then you just need to copy the files over to someplace like /lib/firmware or  /usr/lib/hotplug/firmware/
or go where you downloaded them in the terminal and use

```
 sudo cp *firmware name* -t /lib/firmware
```
or 
```
 sudo cp *firmware name* -t /usr/lib/hotplug/firmware
```
in my case the firmware was in /lib/firmware/*kernel*
wherever i've used italics replace it with whatever you have

---

### Post by Yes_It's_Me on 2007-04-20
I actually got it working by loading the kernel modules by typing modprobe cx88-dvb. but this was in the release candidate and it worked fine.

now in the final release (new install) it seems to work, kaffeine sees the card and finds channels, but when clicking on one to watch i get a black screen with the error:

No plugin found to handle this resource (/home/simon/.kaxtv.ts)

09:20:12: xine: couldn't find demux for >/home/simon/.kaxtv.ts<
09:20:12: xine: found input plugin : file input plugin
09:20:12: video_decoder: no plugin available to handle 'XviD'
09:20:12: xine: found demuxer plugin: AVI/RIFF demux plugin
09:20:12: xine: found input plugin : file input plugin

dammit! so close.

I will follow your instructions again and see if it does anything...

---

### Post by Yes_It's_Me on 2007-04-20
nope, didn't work :(

I think i will try the release candidate again, i had better luck with it, i guess i can just update to the current stable release of feisty?

---

### Post by r-mo on 2007-04-20
I have nova-t pci card, no /dev/dvb in feisty but there was in edgy

had to do the following to get it to work found at (info for lots of other tuners too) [https://help.ubuntu.com/community/MythTV_Feisty_hardware_list](https://help.ubuntu.com/community/MythTV_Feisty_hardware_list) 

```

sudo modprobe cx88-dvb
sudo sh -c "echo "cx88_dvb" >> /etc/modules"

```

now /dev/dvb was there :) 

then on to kaffeine installed this and got an error about plugins, in the end I added the medibuntu repositories [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and from these installed:

kaffeine
kaffeine-xine
libdvdcss2 (I'm sure this one's not needed)
w64codecs (w32 on 32 bit system)
ffmpeg

and these from standard repos:

gxine
libxine1-ffmpeg

Guess you don't need all of these but it made my tv work again :popcorn: 

HTH

---

### Post by Yes_It's_Me on 2007-04-20
I got it going!

i got a tip from another forum to install automatix and install all codecs, worked like a charm. However, the quality from the video feeds is so-so, especially when showing fast motion, is there a way to enhance the quality?

thanks for all the help guys!

---

### Post by bobplano on 2007-04-20
well im glad you got it working (not much thanks to me). automatix has been blamed for causing problems, although i never had any problems, so just be cautious. the only way i can think to enhance to quality would be to get new drivers for your video card

---

### Post by Yes_It's_Me on 2007-04-20
automatix seems fine to me, i didn't use it before because i heard of security issues and stuff.

if i install crossover office with it will it be a trial or something?

---

### Post by Azathoth_ on 2007-04-21
I have reported it to bug.launchpad:
[https://bugs.launchpad.net/ubuntu/+bug/108073](https://bugs.launchpad.net/ubuntu/+bug/108073)

---

### Post by Yes_It's_Me on 2007-04-21
> **Azathoth_ said:**
> I have reported it to bug.launchpad:
[https://bugs.launchpad.net/ubuntu/+bug/108073](https://bugs.launchpad.net/ubuntu/+bug/108073)

thanks, i was thinking of doing it but decided against it because i didn't really know if it classifies as a bug or how to explain it etc.

---

### Post by Azathoth_ on 2007-04-22
> **Yes_It's_Me said:**
> thanks, i was thinking of doing it but decided against it because i didn't really know if it classifies as a bug or how to explain it etc.

Nevermind. The bug is classified

---

### Post by Azathoth_ on 2007-04-22
I have tried a lot of methods for my cx23880 dvb-t card, but i can't get it work

---

### Post by easyease on 2007-04-27
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg293846.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg293846.html)
 this link solved it for me.....

---

### Post by Azathoth_ on 2007-04-27
> **easyease said:**
> [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg293846.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg293846.html)
 this link solved it for me.....

LOL   This bug report was created for me :D  Mario García

Thanks anyway

---

### Post by easyease on 2007-05-07
the spooky fector of google strikes again lol.

---

### Post by Azathoth_ on 2007-05-07
For anyone with this issue:

You have to add to /etc/modules:

dvb-core
cx88-dvb

Reboot and all ok ;)

---

### Post by jacksonz123z on 2007-05-26
I have a leadtek DTV1000T running under Feisty.  I got it to work by "sudo modprobe cx88-dvb".  I added "cx88-dvb" to etc/modules to load the module at boot.  Works really well with Kaffeine the card is a bargain price.

---

