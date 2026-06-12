---
title: "[SOLVED] no sound, AGAIN!! ugh!"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by andyho on 2007-12-17
[COLOR="Navy"]So I finally get around to fixing a usb issue I was having.. then I get brave and decided to go from Feisty to Gutsy.. and now my sound doesn't want to work again. :mad: And I've been trying all the tutorials and I came across a post about re-installing the alsa driver, which I had to do before. And here's what I'm getting in the terminal...

andyho@andyho-ubuntu:~/alsa-driver-1.0.15$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/andyho/alsa-driver-1.0.15
checking cross compile...
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build...
checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

So am I assuming correctly that my kernel is jacked up somewhere?? Whenever I try to play some mp3's in amarok I get -  sound output unavailable; device is busy; xine parameters. Last time it seemed like a pretty quick fix, not so sure I'll be as lucky this time around?! Any ideas?!? Thanks!!
 [/COLOR]

---

### Post by diatribe on 2007-12-17
you probably need the kernel development headers, in synpatic the kernel package will have -dev at the end

---

### Post by mali2297 on 2007-12-17
I think you need to install some packages...
```

sudo apt-get install build-essential ncurses-dev gettext linux-headers-$(uname -r)

```

---

### Post by andyho on 2007-12-17
Ok well tried that and no such luck. I even uninstalled and reinstalled alsamixer and utils, but that didn't do anything either. :( Any other ideas? Here's a couple things I pulled too from terminal..


andyho@andyho-ubuntu:~$ alsamixer
alsamixer: function snd_ctl_open failed for default: No such device

andyho@andyho-ubuntu:~$ sudo lshw -C multimedia
[sudo] password for andyho:
  *-multimedia UNCLAIMED
       description: Audio device
       product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

andyho@andyho-ubuntu:~$ cat /proc/asound/cards
 1 [U0x46d0x8b2    ]: USB-Audio - USB Device 0x46d:0x8b2
                      USB Device 0x46d:0x8b2 at usb-0000:00:1d.0-2, full speed

andyho@andyho-ubuntu:~$ cat /etc/modprobe.d/alsa-base
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388


THANKS!!!

---

### Post by andyho on 2007-12-26
all is good and fixed! I went back into synaptic like someone else did and added the meta kernel package, rebooted and sound was back! :)

---

