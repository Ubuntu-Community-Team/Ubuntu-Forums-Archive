---
title: "Ubuntu 10.10 PPC - G4 Cube Sound - Via USB Speakers"
date: 2011-01-24
forum: Apple Hardware Users
---

### Post by BlastXng on 2011-01-24
Hello Folks

I have been poking around trying to see how I can get the USB speakers on my Mac G4 Cube to work.. Has anyone had any luck with these at all?

I'd really like to get the sound to work for my Cube is basically the music machine in the kitchen that my wife uses.. :-P

Thanks

---

### Post by oswaldkelso on 2011-01-24
I run Debian so ymmv. You may need to blacklist some sound modules. I have the on board sound card working and a usb one for ekiga 

[http://oswaldkelso.blogspot.com/2010/10/how-to-fix-no-sound-on-debian-powerpc.html](http://oswaldkelso.blogspot.com/2010/10/how-to-fix-no-sound-on-debian-powerpc.html)

---

### Post by linuxopjemac on 2011-01-24
try to unmute (with "m") channels with alsamixer

---

### Post by BlastXng on 2011-01-30
> **oswaldkelso said:**
> I run Debian so ymmv. You may need to blacklist some sound modules. I have the on board sound card working and a usb one for ekiga 

[http://oswaldkelso.blogspot.com/2010/10/how-to-fix-no-sound-on-debian-powerpc.html](http://oswaldkelso.blogspot.com/2010/10/how-to-fix-no-sound-on-debian-powerpc.html)

I went through your blog posting and unfortunately none of the items that you outlined worked for me. When reading the alsa Debian Wiki it talked about placing an order of cards like such which I did in the /etc/modprobe.d/alsa-base.conf file :

options snd-usb-audio index=-1

asound shows
/etc/modprobe.d $   cat /proc/asound/cards
 1 [Speakers       ]: USB-Audio - Speakers
                      Apple Computer, Inc. Speakers at usb-0001:10:18.0-2.1, full speed

alsactl init shows
/etc/modprobe.d $ sudo alsactl init
Unknown hardware: "USB-Audio" "USB Mixer" "USB05ac:1101" "" ""
Hardware is initialized using a guess method

Aplay shows
etc/modprobe.d $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: Speakers [Speakers], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

So far no luck getting the USB Speakers to play on my cube.. Ugh!

---

### Post by BlastXng on 2011-01-30
> **linuxopjemac said:**
> try to unmute (with "m") channels with alsamixer

Unfortunately alsamixer won't run.. Otherwise I would..

---

### Post by rasec_spain on 2011-08-08
Hi! Hi have a mac cube 450mhz ppc, there are few years that it was running debian with mldonkey, gnome, mediatomb... and it works all fine before i was upgrade to the last debian (6.0).


Now i have the ppc midle freeze because it can't start xserver (mldonkey and mediatomb works), if there are some way to stop the init xserver and fix i will send all my config (with some help!!), because the usb sound, decoder and all works fine.

I was try a lot of distros, xubuntu, fluxbuntu, and other, but debian use less cpu. 

Excuse my english, and i hope help...

Bye!

---

### Post by oswaldkelso on 2011-08-10
> **rasec_spain said:**
> Hi! Hi have a mac cube 450mhz ppc, there are few years that it was running debian with mldonkey, gnome, mediatomb... and it works all fine before i was upgrade to the last debian (6.0).


Now i have the ppc midle freeze because it can't start xserver (mldonkey and mediatomb works), if there are some way to stop the init xserver and fix i will send all my config (with some help!!), because the usb sound, decoder and all works fine.

I was try a lot of distros, xubuntu, fluxbuntu, and other, but debian use less cpu. 

Excuse my english, and i hope help...

Bye!


Debian 6 removes non-free binary blobs. To get that card working takes a little more work. I'm assuming you have the ati r128 card here. The card will still work but not as well with out the non-free firmware. If you want the firmware-linux-nonfree package you need to add non-free to your sources.list. If like me you don't. You need to tweak your xorg.conf. Search for r128 bugs list on debian bugs for hints. r128 seems a bit of a mess on ppc. I have it working fine now with out non-free and at a good resolution but only after removing gdm and starting x via startx I'm not sure what gdm had to do with it but if it ain't broke don't I don't touch it.

---

