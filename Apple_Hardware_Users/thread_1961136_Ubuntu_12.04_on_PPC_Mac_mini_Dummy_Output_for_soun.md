---
title: "Ubuntu 12.04 on PPC Mac mini: Dummy Output for sound card?"
date: 2012-04-18
forum: Apple Hardware Users
---

### Post by KiwiPal on 2012-04-18
Hello everyone,

I hope that you can help a complete novice to enable sound output following my otherwise successful installation of Ubuntu 12.04 from an early April LiveCD build onto my 1.42 GHz PowerPC Mac mini.

When I initially tried booting my Mac mini from the LiveCD, audio was enabled by default in System Settings where, under the Sound preference, Output was set to play through headphones by KeyLargo/Intrepid Mac I/O.

However, after installing Ubuntu 12.04 the G4 Mac mini was mute. In the System Settings under the Sound preference, Output is now set to play through Dummy Output.

How to I restore/add drivers to enable KeyLargo/Intrepid Mac I/O again?

Any help or advice gratefully received.

Sincerely,

Ade

---

### Post by Michel Sardou on 2012-04-18
Hi!
Well, same problem here, on the very same machine, after a fresh Debian Wheezy install.
Using the 3.2.0-1-powerpc kernel (is that the same on 12-04 ?)
lsmod shows the modules snd, snd_powermac, snd_timer, snd_pcm, snd_page_alloc and soundcore enabled, but alsa can't find any soundcard.
Running alsaloop gives :

```

ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
playback hw:0,0 open error: No such file or directory
Loopback initialization failure.
```
Honestly, I'm still wondering what does the actual job of a soundcard on this machine.:confused:
It seems to be NEC hardware, and I've heard about a AOA driver (from gentoo people).
But I couldn't say more for now.

I'll keep looking around, keep in touch!

---

### Post by Michel Sardou on 2012-04-18
> How to I restore/add drivers to enable KeyLargo/Intrepid Mac I/O again?


Here are some useful elements of reflexion, for any purpose, but they may be outdated (in regards to the kernel version) :
[http://kmuto.jp/debian/hcl/Apple/Mac+Mini+G4](http://kmuto.jp/debian/hcl/Apple/Mac+Mini+G4)

I'm suspecting the problem could lie somewhere in /etc/modprobe.d/alsa-base.conf
but I'll see about that tomorrow.

Cheers

---

### Post by linuxopjemac on 2012-04-19
[http://oswaldkelso.blogspot.com/2010/10/how-to-fix-no-sound-on-debian-powerpc.html](http://oswaldkelso.blogspot.com/2010/10/how-to-fix-no-sound-on-debian-powerpc.html)

---

### Post by rsavage on 2012-04-19
Have you had a look at the FAQ [https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F](https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F) ?
 
Have a read of the debian bug report that is linked there. If you have the same problem can you raise a bug against the hw-detect package [https://launchpad.net/ubuntu/+source/hw-detect](https://launchpad.net/ubuntu/+source/hw-detect) or the debian-installer package. Thanks

---

### Post by linuxopjemac on 2012-04-19
[http://lists.debian.org/debian-power.../msg00063.html](http://lists.debian.org/debian-power.../msg00063.html) is a wrong link in the FAQ....

---

### Post by rsavage on 2012-04-19
Fixed. Thanks.
 
It was the other link I was referring to though [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=650588](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=650588) which should already be familiar to you!

---

### Post by linuxopjemac on 2012-04-19
rsavage: do I notice some humor in your response ?

---

### Post by KiwiPal on 2012-04-19
Thanks, everyone, for your suggestions thus far.

So, bearing in mind that I'm a real novice at this and following the logic (I hope) of the [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=650588](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=650588) discussion as a possible solution, how do I create /etc/modules and add the following kernel modules to (hopefully) make sound work:
snd_aoa_i2sbus
snd_aoa_fabric_layout
snd_aoa_codec_tas
snd_aoa_codec_onyx

Once again, any help gratefully received. Thanks, Ade

---

### Post by linuxopjemac on 2012-04-19
```
sudo nano /etc/modules
```
you enter a text editor
scroll down and add the following lines:
```
snd_aoa_i2sbus
snd_aoa_fabric_layout
snd_aoa_codec_tas
snd_aoa_codec_onyx
```
then CTRL-X and "y" to save
reboot
sound works hopefully

---

### Post by KiwiPal on 2012-04-21
Gentlemen, I salute you! Thanks to that last tip, linuxopjemac, I have audio. Very grateful! Ade

---

### Post by TuxMini on 2012-10-19
> **linuxopjemac said:**
> ```
sudo nano /etc/modules
```
you enter a text editor
scroll down and add the following lines:
```
snd_aoa_i2sbus
snd_aoa_fabric_layout
snd_aoa_codec_tas
snd_aoa_codec_onyx
```
then CTRL-X and "y" to save
reboot
sound works hopefully
Thanks linuxopjemac!! I had exactly the same problem with my old MacMini running Ubuntu. Totally fixed!

---

### Post by kpalling on 2012-11-03
Thanks for the fix. 
This enabled sound on my Apple Mac Mini M9971B/B PowerPC G4 running Mint 11 Linux for PowerPC.
Keith

---

### Post by kamikazekatze on 2013-01-23
I got the same problem. But editing /etc/modules doesnt help.
running g5 lubuntu 12.10.
[http://www.alsa-project.org/db/?f=6d8c37d0e46e62aaaf2e2b3a1842ae6fe41d8880](http://www.alsa-project.org/db/?f=6d8c37d0e46e62aaaf2e2b3a1842ae6fe41d8880)

In addition I cant find any file /etc/modprobe.d/blacklist.local.conf.
I got a blacklist.conf, but there is nearly no alsa driver blocked, mainly other things.

---

