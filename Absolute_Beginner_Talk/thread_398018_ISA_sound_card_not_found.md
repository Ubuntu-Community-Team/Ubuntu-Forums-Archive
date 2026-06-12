---
title: "ISA sound card not found"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by wgn on 2007-03-31
I'm trying a liveCD of Xubuntu on an old computer to see how it runs.  Other than being slow, it's runs pretty good, but I can't get any sound.

I've got an old ISA Sound Blaster 16 AWE64 that works fine in the various MS OS versions that have been installed.  Currently runs fine under 2K.  I've searched the forum and tried several of the recommendations. (I don't know how to link to any of the threads I've already tried, sorry.  Or how to box in the output from my terminal session.  Guess I'm in for some OJT.)

The output from aplay is

```
ubuntu@ubuntu:~$ aplay -l
aplay: device_list:222: no soundcards found...
```

I've tried manually installing the ALSA driver and get this

```
ubuntu@ubuntu:~$ sudo modprobe snd-sbawe
FATAL: Error inserting snd_sbawe (/lib/modules/2.6.17-10-generic/kernel/sound/isa/sb/snd-sbawe.ko): No such device

```
I've printed out the kernel ring buffer and get a huge output file [file attached]

It looks like it found the 2 ISA PnP cards [127.427444] but didn't allocate any resources to them[127.554881] & [127.554889].

Sorry this post is so long, but any help would be greatly appreciated.

---

### Post by wgn on 2007-04-05
Still haven't been able to get the sound card to work.  I thought it could be a problem with the OS finding the PnP cards, so I turned off the PnP OS block in the BIOS.  I get the same types of messages, just worded slightly differently [file attached] 

I then found another post that said to use

```
lspnp -v
```

After discovering I had to install the pnpbios_tools package first I've got more info that doesn't really tell me a whole lot. [file attached]

When I get a chance I'm going to try aadebug.  Until then, does anyone see anything that jumps out as a problem?  Or any other suggestions?  Any help would be appreciated.  Thanks.

---

### Post by sirhalos on 2007-04-05
You are correct linux does not like PnP ISA cards you need to disable PnP in the bios and set the card up manually using modprobe. After you have tested you need to add it to your /etc/modprobe.conf so it will always find it at startup also as you have already discovered the default kernel no longer has ISA sound cards, please make a customer kernel and select the sound card you have so it has the device installed.

---

### Post by wgn on 2007-04-05
modprobe still says there's no such device.  I've read that I can add some other parameters to the modprobe command to force it to acknowledge the device.  After I run aadebug I will supposedly have enough info to try.

I'm still booting from a liveCD (want to make sure everything works before doing an install).  If I can get the card to work, I'll append the modprobe.conf file after install.

btw, what's a "customer kernel"?

---

### Post by sirhalos on 2007-04-05
Oh my bad meant Custom Kernel... haha sorry I'm at work dealing with Customers... haha funny.

---

### Post by sirhalos on 2007-04-05
But yes you would have to put in the full commands for modprobe with the I/O's of the device.

---

### Post by wgn on 2007-04-05
Well, aadebug didn't give me any more useful info (at least as far as a I can tell)

```
ubuntu@ubuntu:~$ chmod +x aadebug
ubuntu@ubuntu:~$ ./aadebug
ALSA Audio Debug v0.1.0 - Thu Apr  5 20:28:29 UTC 2007
http://alsa.opensrc.org/aadebug
http://www.gnu.org/licenses/gpl.txt

Kernel ----------------------------------------------------
Linux ubuntu 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux

Loaded Modules --------------------------------------------

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Warning: /proc/asound does not exist
This indicates that ALSA is not installed correctly
Check various logs in /var/log for a clue as to why

Dev Snd ---------------------------------------------------
Warning: /dev/snd does not exist

CPU -------------------------------------------------------
model name      : Pentium III (Katmai)
cpu MHz         : 601.436

RAM -------------------------------------------------------
MemTotal:       515940 kB
SwapTotal:           0 kB

Hardware --------------------------------------------------
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)

ubuntu@ubuntu:~$ 
```

I hate to do it, but I'm going to have to boot up 2K and check what the settings on the card are.

Any other suggestions?

---

### Post by halitech on 2007-04-05
I've been fighting this as well and I found the easier route was to simply drop by the flea market and buy a PCI card and it worked as soon as I powered on.

There was a thread on a script that would help find ISA cards but the file is no longer available.

---

