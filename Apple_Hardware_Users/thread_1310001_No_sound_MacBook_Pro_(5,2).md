---
title: "No sound MacBook Pro (5,2)"
date: 2009-11-01
forum: Apple Hardware Users
---

### Post by thinktyler on 2009-11-01
Reading these docs I've still yet to get sound.

--> [https://help.ubuntu.com/community/MacBookPro5-1_5-2/Karmic](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Karmic)
= Applying ALSA .19 mb1 patch ends in error. Wrong Kernel version.

```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.19.tar.bz2
wget http://qwe.pl/~kacper/alsa-driver-1.0.19-mb51.patch

Unpack and apply the patch

tar jxf ./alsa-driver-1.0.19.tar.bz2
mv ./alsa-driver-1.0.19-mb51.patch ./alsa-driver-1.0.19
cd ./alsa-driver-1.0.19
patch -p2 < ./alsa-driver-1.0.19-mb51.patch

Build new alsa modules

./configure
make
sudo make install
```

/home/tdhz77/alsa-driver-1.0.19/acore/info.c:161: error: &#8216;struct proc_dir_entry&#8217; has no member named &#8216;owner&#8217;
/home/tdhz77/alsa-driver-1.0.19/acore/info.c: In function &#8216;snd_info_register&#8217;:
/home/tdhz77/alsa-driver-1.0.19/acore/info.c:1020: error: &#8216;struct proc_dir_entry&#8217; has no member named &#8216;owner&#8217;
make[3]: *** [/home/tdhz77/alsa-driver-1.0.19/acore/info.o] Error 1
make[2]: *** [/home/tdhz77/alsa-driver-1.0.19/acore] Error 2
make[1]: *** [_module_/home/tdhz77/alsa-driver-1.0.19] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [compile] Error 2


Second attempt: Via ([https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/46209](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/46209))


```
aptitude purge pulseaudio
apt-get instal ubuntu-desktop

```
Ubuntu desktop was not removed, and reinstalling pulse audio did nothing.


Attempt 3: Tried to install latest ALSA release .20

Attempt 4: Attempted the MacBook Pro 5,3 patch. SOURCE: [https://help.ubuntu.com/community/MacBookPro5-3/Karmic#Sound](https://help.ubuntu.com/community/MacBookPro5-3/Karmic#Sound)

More error. 

```

sudo rm -rf /lib/modules/`uname -r`/kernel/sound
sudo aptitude reinstall linux-headers-`uname -r` linux-image-`uname -r`
rm alsa-driver-snapshot.tar.gz
wget ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz
tar xf alsa-driver-snapshot.tar.gz
cd alsa-driver
sudo ./configure --enable-dynamic-minors --without-oss --with-cards="hda-intel"
sudo make
sudo make install

Rebooting. And then, installing also gnome-alsamixer to unmute the frontspeaker and check he surround setting, since it seems that these changes can't be done with the general sound-preferences dialogue.

sudo apt-get install gnome-alsamixer
```

I need help!

---

### Post by nickthecook on 2009-11-01
Just in case anyone else runs into it: I have had a similar experience with the guide linked to at the top on my MBP 5,1. I had sound through the speakers out of the box, but none through the headphones, so I decided to try the steps in the guide.

I encountered the same errors you did installing the patched alsa driver. I downloaded and installed alsa-1.0.21, and still no sound.

I commented out the line in /etc/modprobe.d/options.conf:

#options snd_hda_intel model=mbp3

rebooted, and am now back to the functionality that I had after a fresh install: sound through speakers, but nothing through headphones.

---

### Post by nickthecook on 2009-11-01
In gnome-alsamixer, unmuting the "HP" source gives sound through the headphones!

However, I cannot isolate the headphones volume from the speaker volume using any of the controls in gnome-alsamixer -- they either both output or neither does.

---

### Post by thinktyler on 2009-11-23
Post deleted...

---

### Post by alexmurray on 2009-11-23
MacBook Pro 5,2 should be supported out of the box - you really shouldn't need to download and compile alsa-driver manually. Just make sure HP (headphones) channel is unmuted for headphones.

---

### Post by thinktyler on 2009-11-24
> **alexmurray said:**
> MacBook Pro 5,2 should be supported out of the box - you really shouldn't need to download and compile alsa-driver manually. Just make sure HP (headphones) channel is unmuted for headphones.


Not true according to ([https://help.ubuntu.com/community/MacBookPro5-1_5-2/Karmic](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Karmic))

> 5.2 hardware

Sound doesn't work with Karmic final release on MacBook Pro 5,2 hardware. 

Please correct me. I hate OSX and I want to get the sound working on my Ubuntu baby.

---

### Post by linds2009 on 2009-11-25
I'll give those a try!
Thanks for the links
Thank for sharing,I like it

---

### Post by Mmmm on 2009-11-26
I have followed the instructions here:

[https://help.ubuntu.com/community/MacBookPro5-1_5-2/Karmic#Sound]("https://help.ubuntu.com/community/MacBookPro5-1_5-2/Karmic#Sound")

and 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/462098]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/462098")

but my audio still doesn't work.  I have not had any sound from either the speakers or the headphones since installing Karmic (64bit) on my MBP 5,2.  It doesn't work if I boot from the Live CD either.  It works fine if I boot into OSX, and worked in Jaunty (after I installed the patched ALSA driver) so it's not a hardware issue.  Is there a some other way to get audio working?

---

### Post by lepukowsky on 2009-11-27
I am right there with you Mmmm, I've been reading the supposed fixes but nothing's worked on my 5,2...so don't think you are crazy...

---

### Post by linuxopjemac on 2009-11-27
my guess is that you have to wait for kernel 2.6.32
[http://mac.linux.be/content/more-improvements-macs-upcoming-2632-kernel](http://mac.linux.be/content/more-improvements-macs-upcoming-2632-kernel)

---

### Post by thinktyler on 2009-11-27
> **linuxopjemac said:**
> my guess is that you have to wait for kernel 2.6.32
[http://mac.linux.be/content/more-improvements-macs-upcoming-2632-kernel](http://mac.linux.be/content/more-improvements-macs-upcoming-2632-kernel)


Thank you very much for this link. I'm glad at least progress is being made on this problem. I will revert back to jaunty for the time being, or until the kernel (2.6.32) is released. 

Good luck.

---

### Post by thinktyler on 2009-12-04
According to [http://mac.linux.be/content/kernel-2632-released](http://mac.linux.be/content/kernel-2632-released)
2.6.32 has been released.

---

### Post by Sloth on 2009-12-06
I'm running 2.6.32 on a 5,2 MacBook Pro.  

Sounds works perfectly.

---

### Post by thinktyler on 2009-12-07
Everything works now after all updates have been applied.

I can't listen to headphones without muting the front sound. 

I've installed gnome-alsa mixer and unmuted "HP" and get sound.

---

### Post by thinktyler on 2009-12-09
I can't find the solution to the headphones. As a college student I really need headphones to be working, so I don't interrupt other students while studying.

I have tried, "sudo apt-get install gnome-alsamixer" and unmuting the HP jack, but the sound still comes from the main speakers. If I mute the front speakers, I can't hear from my headphones. 

Any help would be great, ubuntu is working 99.9% and I love it!!!

---

### Post by alexmurray on 2009-12-11
Try not completely muting the front speakers, just turn them down until you can't hear anything from them but don't completely mute them. That's how I have to do it on my MBP5,1 so 5,2 is probably same.

---

### Post by alexmurray on 2010-01-14
I've just posted a patch to enable auto-muting of speakers when headphones are plugged in on MacBook Pro 5,2: [http://ubuntuforums.org/showthread.php?t=1379971](http://ubuntuforums.org/showthread.php?t=1379971) - this contains a how-to to enable it and get sound working much better.

---

