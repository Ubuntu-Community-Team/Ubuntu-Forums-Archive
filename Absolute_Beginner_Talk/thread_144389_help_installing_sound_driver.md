---
title: "help installing sound driver"
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by screamingindigital on 2006-03-14
Hello all....as per recommendations of the forum, I purchased a CMI 8738 pci sound card for my Breezy system.  As always things are NOT working out (no sound).  Here is a C/P from the driver CD that came with the card:

Audio driver for CM8338/CM8738 chips by Chen-Li Tien

HARDWARE SUPPORTED

================================================== ==============================

C-Media CMI8338

C-Media CMI8738

On-board C-Media chips

WHAT'S NEW

================================================== ==============================

1. Support modem interface for 8738. (select in kernel configuration)

2. Enable S/PDIF-in to S/PDIF-out (S/PDIF loop).

3. Enable 4 channels analog duplicate mode on 3 jack or 4 jack

configurateion.

4. Enable joystick support. (joystick driver needed)

STEPS TO BUILD DRIVER

================================================== ==============================

1. Backup the Config.in and Makefile in the sound driver directory

(/usr/src/linux/driver/sound).

The Configure.help provide help when you config driver in step

4, please backup the original one (/usr/src/linux/Document) and

copy this file.

The cmpci is document for the driver in detail, please copy it

to /usr/src/linux/Document/sound so you can refer it. Backup if

there is already one.

2. Extract the tar file by 'tar xvzf cmpci-xx.tar.gz' in the above

directory.

3. Change directory to /usr/src/linux

4. Config cm8338 driver by 'make menuconfig', 'make config' or

'make xconfig' command.

5. Please select Sound Card (CONFIG_SOUND=m) support and CMPCI

driver (CONFIG_SOUND_CMPCI=m) as modules. Resident mode not tested.

For driver option, please refer 'DRIVER PARAMETER'

6. Compile the kernel if necessary.

7. Compile the modules by 'make modules'.

8. Install the modules by 'make modules_install'


INSTALL DRIVER

================================================== ==============================

1. Before first time to run the driver, create module dependency by

'depmod -a'

2. To install the driver manually, enter 'modprobe cmpci'.

3. Driver installation for various distributions:

a. Slackware 4.0

Add the 'modprobe cmpci' command in your /etc/rc.d/rc.modules

file.so you can start the driver automatically each time booting.

b. Caldera OpenLinux 2.2

Use LISA to load the cmpci module.

c. RedHat 6.0 and S.u.S.E. 6.1

Add following command in /etc/conf.modules:

alias sound cmpci


also visit [http://www.cmedia.com.tw](http://www.cmedia.com.tw) for installation instruction.


DRIVER PARAMETER

================================================== ==============================

Some functions for the cm8738 can be configured in Kernel Configuration

or modules parameters. Set these parameters to 1 to enable.

spdif_loop: Enable S/PDIF loop, this route S/PDIF-in to S/PDIF-out

directly.

four_ch: Enable 4 channels mode, rear-out or line-in will output

the same as line-out.

rear_out: Enable this if you have independent rear-out jacket on

your sound card, otherwise line-in will be used as

rear-out.

modem: You will need to set this parameter if you want to use

the HSP modem. You need install the pctel.o, the modem

driver itself.

joystich: Enable joystick. You will need to install Linux joystick

driver.

**Would someone be so kind to translate this into UBUNTU speak and help me get this thing installed** :-k 

Thanks

p.s.  The CMI website list other drivers also (updated??)  They include..'cmpci-6.64.tar.bz2' and 'cmpci-patch-2.6.4.tar.bz2'  **would I need these also?**:-k

---

### Post by mlind on 2006-03-14
ALSA sound driver seems to [support]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=C-Media&card=.&chip=CMI8338%2C+CMI8738%2C+CMI8768&module=cmipci") your card.

could you post contents of */etc/modprobe.d/alsa-base* file ?

---

### Post by screamingindigital on 2006-03-14
Here are the contents of alsa-base:

# autoloader aliases
install sound-slot-0 modprobe snd-card-0
install sound-slot-1 modprobe snd-card-1
install sound-slot-2 modprobe snd-card-2
install sound-slot-3 modprobe snd-card-3
install sound-slot-4 modprobe snd-card-4
install sound-slot-5 modprobe snd-card-5
install sound-slot-6 modprobe snd-card-6
install sound-slot-7 modprobe snd-card-7
# Load optional modules above their base modules
install snd modprobe --ignore-install snd && { modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm modprobe --ignore-install snd-pcm && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }
install snd-emu10k1 modprobe --ignore-install snd-emu10k1 && { /lib/alsa/modprobe-post-install snd-emu10k1 ; modprobe --quiet snd-emu10k1-synth ; }
install snd-via82xx modprobe --ignore-install snd-via82xx && { /lib/alsa/modprobe-post-install snd-via82xx ; modprobe --quiet snd-seq ; }
# Cause a script to be run after *-synth module initialization
install snd-emu8000-synth modprobe --ignore-install snd-emu8000-synth && /lib/alsa/modprobe-post-install snd-emu8000-synth
install snd-emu10k1-synth modprobe --ignore-install snd-emu10k1-synth && /lib/alsa/modprobe-post-install snd-emu10k1-synth
# Cause a script to be run after card driver module initialization
install snd-ad1816a modprobe --ignore-install snd-ad1816a && /lib/alsa/modprobe-post-install snd-ad1816a
install snd-ad1848 modprobe --ignore-install snd-ad1848 && /lib/alsa/modprobe-post-install snd-ad1848
install snd-ali5451 modprobe --ignore-install snd-ali5451 && /lib/alsa/modprobe-post-install snd-ali5451
install snd-als100 modprobe --ignore-install snd-als100 && /lib/alsa/modprobe-post-install snd-als100
install snd-als4000 modprobe --ignore-install snd-als4000 && /lib/alsa/modprobe-post-install snd-als4000
install snd-armaaci modprobe --ignore-install snd-armaaci && /lib/alsa/modprobe-post-install snd-armaaci
install snd-asihpi modprobe --ignore-install snd-asihpi && /lib/alsa/modprobe-post-install snd-asihpi
install snd-atiixp modprobe --ignore-install snd-atiixp && /lib/alsa/modprobe-post-install snd-atiixp
install snd-au1x00 modprobe --ignore-install snd-au1x00 && /lib/alsa/modprobe-post-install snd-au1x00
install snd-au8810 modprobe --ignore-install snd-au8810 && /lib/alsa/modprobe-post-install snd-au8810
install snd-au8820 modprobe --ignore-install snd-au8820 && /lib/alsa/modprobe-post-install snd-au8820
install snd-au8830 modprobe --ignore-install snd-au8830 && /lib/alsa/modprobe-post-install snd-au8830
install snd-azt2320 modprobe --ignore-install snd-azt2320 && /lib/alsa/modprobe-post-install snd-azt2320
install snd-azt3328 modprobe --ignore-install snd-azt3328 && /lib/alsa/modprobe-post-install snd-azt3328
install snd-ca0106 modprobe --ignore-install snd-ca0106 && /lib/alsa/modprobe-post-install snd-ca0106
install snd-cmi8330 modprobe --ignore-install snd-cmi8330 && /lib/alsa/modprobe-post-install snd-cmi8330
install snd-cmi8380 modprobe --ignore-install snd-cmi8380 && /lib/alsa/modprobe-post-install snd-cmi8380
install snd-cmipci modprobe --ignore-install snd-cmipci && /lib/alsa/modprobe-post-install snd-cmipci
install snd-cs4231 modprobe --ignore-install snd-cs4231 && /lib/alsa/modprobe-post-install snd-cs4231
install snd-cs4232 modprobe --ignore-install snd-cs4232 && /lib/alsa/modprobe-post-install snd-cs4232
install snd-cs4236 modprobe --ignore-install snd-cs4236 && /lib/alsa/modprobe-post-install snd-cs4236
install snd-cs4281 modprobe --ignore-install snd-cs4281 && /lib/alsa/modprobe-post-install snd-cs4281
install snd-cs46xx modprobe --ignore-install snd-cs46xx && /lib/alsa/modprobe-post-install snd-cs46xx
install snd-darla20 modprobe --ignore-install snd-darla20 && /lib/alsa/modprobe-post-install snd-darla20
install snd-darla24 modprobe --ignore-install snd-darla24 && /lib/alsa/modprobe-post-install snd-darla24
install snd-dt019x modprobe --ignore-install snd-dt019x && /lib/alsa/modprobe-post-install snd-dt019x
install snd-echo3g modprobe --ignore-install snd-echo3g && /lib/alsa/modprobe-post-install snd-echo3g
install snd-emu10k1x modprobe --ignore-install snd-emu10k1x && /lib/alsa/modprobe-post-install snd-emu10k1x
install snd-ens1370 modprobe --ignore-install snd-ens1370 && /lib/alsa/modprobe-post-install snd-ens1370
install snd-ens1371 modprobe --ignore-install snd-ens1371 && /lib/alsa/modprobe-post-install snd-ens1371
install snd-es1688 modprobe --ignore-install snd-es1688 && /lib/alsa/modprobe-post-install snd-es1688
install snd-es18xx modprobe --ignore-install snd-es18xx && /lib/alsa/modprobe-post-install snd-es18xx
install snd-es1938 modprobe --ignore-install snd-es1938 && /lib/alsa/modprobe-post-install snd-es1938
install snd-es1968 modprobe --ignore-install snd-es1968 && /lib/alsa/modprobe-post-install snd-es1968
install snd-es968 modprobe --ignore-install snd-es968 && /lib/alsa/modprobe-post-install snd-es968
install snd-fm801 modprobe --ignore-install snd-fm801 && /lib/alsa/modprobe-post-install snd-fm801
install snd-fm801-tea575x modprobe --ignore-install snd-fm801-tea575x && /lib/alsa/modprobe-post-install snd-fm801-tea575x
install snd-gina20 modprobe --ignore-install snd-gina20 && /lib/alsa/modprobe-post-install snd-gina20
install snd-gina24 modprobe --ignore-install snd-gina24 && /lib/alsa/modprobe-post-install snd-gina24
install snd-gusclassic modprobe --ignore-install snd-gusclassic && /lib/alsa/modprobe-post-install snd-gusclassic
install snd-gusextreme modprobe --ignore-install snd-gusextreme && /lib/alsa/modprobe-post-install snd-gusextreme
install snd-gusmax modprobe --ignore-install snd-gusmax && /lib/alsa/modprobe-post-install snd-gusmax
install snd-harmony modprobe --ignore-install snd-harmony && /lib/alsa/modprobe-post-install snd-harmony
install snd-hda-intel modprobe --ignore-install snd-hda-intel && /lib/alsa/modprobe-post-install snd-hda-intel
install snd-hdsp modprobe --ignore-install snd-hdsp && /lib/alsa/modprobe-post-install snd-hdsp
install snd-hdspm modprobe --ignore-install snd-hdspm && /lib/alsa/modprobe-post-install snd-hdspm
install snd-ice1712 modprobe --ignore-install snd-ice1712 && /lib/alsa/modprobe-post-install snd-ice1712
install snd-ice1724 modprobe --ignore-install snd-ice1724 && /lib/alsa/modprobe-post-install snd-ice1724
install snd-indigo modprobe --ignore-install snd-indigo && /lib/alsa/modprobe-post-install snd-indigo
install snd-indigodj modprobe --ignore-install snd-indigodj && /lib/alsa/modprobe-post-install snd-indigodj
install snd-indigoio modprobe --ignore-install snd-indigoio && /lib/alsa/modprobe-post-install snd-indigoio
install snd-intel8x0 modprobe --ignore-install snd-intel8x0 && /lib/alsa/modprobe-post-install snd-intel8x0
install snd-interwave modprobe --ignore-install snd-interwave && /lib/alsa/modprobe-post-install snd-interwave
install snd-interwave-stb modprobe --ignore-install snd-interwave-stb && /lib/alsa/modprobe-post-install snd-interwave-stb
install snd-korg1212 modprobe --ignore-install snd-korg1212 && /lib/alsa/modprobe-post-install snd-korg1212
install snd-layla20 modprobe --ignore-install snd-layla20 && /lib/alsa/modprobe-post-install snd-layla20
install snd-layla24 modprobe --ignore-install snd-layla24 && /lib/alsa/modprobe-post-install snd-layla24
install snd-maestro3 modprobe --ignore-install snd-maestro3 && /lib/alsa/modprobe-post-install snd-maestro3
install snd-mia modprobe --ignore-install snd-mia && /lib/alsa/modprobe-post-install snd-mia
install snd-miro modprobe --ignore-install snd-miro && /lib/alsa/modprobe-post-install snd-miro
install snd-mixart modprobe --ignore-install snd-mixart && /lib/alsa/modprobe-post-install snd-mixart
install snd-mona modprobe --ignore-install snd-mona && /lib/alsa/modprobe-post-install snd-mona
install snd-mpu401 modprobe --ignore-install snd-mpu401 && /lib/alsa/modprobe-post-install snd-mpu401
install snd-msnd-pinnacle modprobe --ignore-install snd-msnd-pinnacle && /lib/alsa/modprobe-post-install snd-msnd-pinnacle
install snd-mtpav modprobe --ignore-install snd-mtpav && /lib/alsa/modprobe-post-install snd-mtpav
install snd-nm256 modprobe --ignore-install snd-nm256 && /lib/alsa/modprobe-post-install snd-nm256
install snd-opl3sa2 modprobe --ignore-install snd-opl3sa2 && /lib/alsa/modprobe-post-install snd-opl3sa2
install snd-opti92x-ad1848 modprobe --ignore-install snd-opti92x-ad1848 && /lib/alsa/modprobe-post-install snd-opti92x-ad1848
install snd-opti92x-cs4231 modprobe --ignore-install snd-opti92x-cs4231 && /lib/alsa/modprobe-post-install snd-opti92x-cs4231
install snd-opti93x modprobe --ignore-install snd-opti93x && /lib/alsa/modprobe-post-install snd-opti93x
install snd-pc98-cs4232 modprobe --ignore-install snd-pc98-cs4232 && /lib/alsa/modprobe-post-install snd-pc98-cs4232
install snd-pcsp modprobe --ignore-install snd-pcsp && /lib/alsa/modprobe-post-install snd-pcsp
install snd-pcxhr modprobe --ignore-install snd-pcxhr && /lib/alsa/modprobe-post-install snd-pcxhr
install snd-pdaudiocf modprobe --ignore-install snd-pdaudiocf && /lib/alsa/modprobe-post-install snd-pdaudiocf
install snd-pdplus modprobe --ignore-install snd-pdplus && /lib/alsa/modprobe-post-install snd-pdplus
install snd-portman2x4 modprobe --ignore-install snd-portman2x4 && /lib/alsa/modprobe-post-install snd-portman2x4
install snd-powermac modprobe --ignore-install snd-powermac && /lib/alsa/modprobe-post-install snd-powermac
install snd-pxa2xx-ac97 modprobe --ignore-install snd-pxa2xx-ac97 && /lib/alsa/modprobe-post-install snd-pxa2xx-ac97
install snd-rme32 modprobe --ignore-install snd-rme32 && /lib/alsa/modprobe-post-install snd-rme32
install snd-rme96 modprobe --ignore-install snd-rme96 && /lib/alsa/modprobe-post-install snd-rme96
install snd-rme9652 modprobe --ignore-install snd-rme9652 && /lib/alsa/modprobe-post-install snd-rme9652
install snd-s3c2410 modprobe --ignore-install snd-s3c2410 && /lib/alsa/modprobe-post-install snd-s3c2410
install snd-sa11xx-uda1341 modprobe --ignore-install snd-sa11xx-uda1341 && /lib/alsa/modprobe-post-install snd-sa11xx-uda1341
install snd-sb16 modprobe --ignore-install snd-sb16 && /lib/alsa/modprobe-post-install snd-sb16
install snd-sb8 modprobe --ignore-install snd-sb8 && /lib/alsa/modprobe-post-install snd-sb8
install snd-sbawe modprobe --ignore-install snd-sbawe && /lib/alsa/modprobe-post-install snd-sbawe
install snd-serialmidi modprobe --ignore-install snd-serialmidi && /lib/alsa/modprobe-post-install snd-serialmidi
install snd-serial-u16550 modprobe --ignore-install snd-serial-u16550 && /lib/alsa/modprobe-post-install snd-serial-u16550
install snd-sgalaxy modprobe --ignore-install snd-sgalaxy && /lib/alsa/modprobe-post-install snd-sgalaxy
install snd-sonicvibes modprobe --ignore-install snd-sonicvibes && /lib/alsa/modprobe-post-install snd-sonicvibes
install snd-sscape modprobe --ignore-install snd-sscape && /lib/alsa/modprobe-post-install snd-sscape
install snd-sun-amd7930 modprobe --ignore-install snd-sun-amd7930 && /lib/alsa/modprobe-post-install snd-sun-amd7930
install snd-sun-cs4231 modprobe --ignore-install snd-sun-cs4231 && /lib/alsa/modprobe-post-install snd-sun-cs4231
install snd-sun-dbri modprobe --ignore-install snd-sun-dbri && /lib/alsa/modprobe-post-install snd-sun-dbri
install snd-trident modprobe --ignore-install snd-trident && /lib/alsa/modprobe-post-install snd-trident
install snd-usb-audio modprobe --ignore-install snd-usb-audio && /lib/alsa/modprobe-post-install snd-usb-audio
install snd-usb-usx2y modprobe --ignore-install snd-usb-usx2y && /lib/alsa/modprobe-post-install snd-usb-usx2y
install snd-vx222 modprobe --ignore-install snd-vx222 && /lib/alsa/modprobe-post-install snd-vx222
install snd-vxp440 modprobe --ignore-install snd-vxp440 && /lib/alsa/modprobe-post-install snd-vxp440
install snd-vxpocket modprobe --ignore-install snd-vxpocket && /lib/alsa/modprobe-post-install snd-vxpocket
install snd-wavefront modprobe --ignore-install snd-wavefront && /lib/alsa/modprobe-post-install snd-wavefront
install snd-ymfpci modprobe --ignore-install snd-ymfpci && /lib/alsa/modprobe-post-install snd-ymfpci
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2


**see anything missing??**  :-k

---

### Post by screamingindigital on 2006-03-14
more info:

lspci:
0000:00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] System  Controller (rev 25)
0000:00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] AGP Bri dge (rev 01)
0000:00:07.0 ISA bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ISA (rev 0 1)
0000:00:07.1 IDE interface: Advanced Micro Devices [AMD] AMD-756 [Viper] IDE (re v 07)
0000:00:07.3 Bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ACPI (rev 03)
0000:00:07.4 USB Controller: Advanced Micro Devices [AMD] AMD-756 [Viper] USB (r ev 06)
0000:00:09.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet  10/100 (rev 11)
0000:00:0b.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10 )
0000:01:05.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)

modprobe snd-cmipci returns nothing  

Scott

---

### Post by mlind on 2006-03-14
well at least there's a lot of stuff. if command *lsmod | grep snd_cmipci* from terminal displays something,
modules are loaded, and probably ok.

Change your sound system to alsa, if it already isn't from System > Preferences > Multimedia Systems Selector

Start alsamixer from console, and unmute necessary channels.

btw. if you're using S/PDIF, you need to define non-default output device. This
can be done using .asoundrc file. There are examples here on forums.

---

### Post by screamingindigital on 2006-03-14
lsmod | grep snd_cmipci reports:

snd_cmipci             30368  0
gameport               14472  1 snd_cmipci
snd_pcm                78344  2 snd_cmipci,snd_pcm_oss
snd_opl3_lib            9856  1 snd_cmipci
snd_mpu401_uart         6784  1 snd_cmipci
snd                    48644  10 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device

tried running alsamixer and got the following error:

alsamixer: function snd_ctl_open failed for default: No such file or directory

can I try anything else????

---

### Post by mlind on 2006-03-14
try modprobing device again, *sudo modprobe cmpci*

does *cat /proc/asound/cards*
display your soundcard?

did you make sure that ALSA is selected as default sound device from Preferences?
does *aplay -l* display your sound card?
does file /var/lib/alsa/asound.state exist?

it could be that ALSA is not configured,
does *sudo dpkg-reconfigure alsa-base* help any bit?

---

### Post by mlind on 2006-03-14
if these don't do any good, you should follow Debian installation
instructions on the ALSA site

they suggest you create file called */etc/modutils/alsa*
containing
```

# ALSA portion
alias char-major-116 snd
alias snd-card-0 snd-cmipci
# module options should go here

# OSS/Free portion
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0
	
# card #1
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

```

and run command *sudo update-modules*

---

### Post by screamingindigital on 2006-03-14
I am now currently at work and away from my system.  I will try all that you just suggested first thing in the morning and report back the finding.  Thank you for all your help so far.....:)

---

### Post by screamingindigital on 2006-03-15
OK...back at home and I tried the following:

> try modprobing device again, sudo modprobe cmpci
 tried and it returned nothing

> does cat /proc/asound/cards
display your soundcard?
 --- no soundcards ---

> did you make sure that ALSA is selected as default sound device from Preferences? yes but when I tried to test it displayed an error

> does aplay -l display your sound card?  aplay: device_list:218: no soundcards found...


> does file /var/lib/alsa/asound.state exist? no

> it could be that ALSA is not configured,
does sudo dpkg-reconfigure alsa-base help any bit? tried and didn't help.

> if these don't do any good, you should follow Debian installation
instructions on the ALSA site

they suggest you create file called /etc/modutils/alsa
containing
Code:

# ALSA portion alias char-major-116 snd alias snd-card-0 snd-cmipci # module options should go here # OSS/Free portion alias char-major-14 soundcore alias sound-slot-0 snd-card-0 # card #1 alias sound-service-0-0 snd-mixer-oss alias sound-service-0-1 snd-seq-oss alias sound-service-0-3 snd-pcm-oss alias sound-service-0-8 snd-seq-oss alias sound-service-0-12 snd-pcm-oss


and run command sudo update-modules did this and still no sound.....this just flat out sucks.  What else is their to do?? :cry:

---

### Post by mlind on 2006-03-15
modprobe command should return empty line if it was successfull. Kinda weird, but
that's the case with many *nix commands. So modprobing was probably okay.

make sure that alsa packages are installed
*sudo apt-get alsa-base alsa-utils libasound2*

(and maybe that *gstreamer-alsa package* is installed too.)

then try to manually modprobe these modules for your soundcard.
doing *sudo modprobe <module>*
```

# ALSA portion
snd
snd-cmipci

# OSS/Free portion
soundcore
snd-card-0
	
# card #1
snd-mixer-oss
snd-seq-oss
snd-pcm-oss
snd-seq-oss
snd-pcm-oss

```

kernel should find you card and make it visible on file /proc/asound/cards

---

### Post by screamingindigital on 2006-03-15
> make sure that alsa packages are installed
sudo apt-get alsa-base alsa-utils libasound2  

alsa-base is already the newest version.
alsa-utils is already the newest version.
libasound2 is already the newest version.


> (and maybe that gstreamer-alsa package is installed too.)

E: Couldn't find package gstreamer-alsa

> then try to manually modprobe these modules for your soundcard.
doing sudo modprobe <module>
Code:

# ALSA portion snd snd-cmipci # OSS/Free portion soundcore snd-card-0 # card #1 snd-mixer-oss snd-seq-oss snd-pcm-oss snd-seq-oss snd-pcm-oss

 everything returned nothing except: 
admin@ubuntu2:~$ sudo modprobe snd-card-0
FATAL: Module snd_card_0 not found.

> kernel should find you card and make it visible on file /proc/asound/cards  

---no soundcards---

It looks like I'm SOL :cry:

---

### Post by mlind on 2006-03-15
oh man, this is getting frustrating :-k 

could you tell the version of alsa-base package?
```

dpkg -l 'alsa*'

```

does *modinfo snd_cmipci* show information about your card's driver?

if it's older than 0.9.0beta11, you should modprobe *snd-card-cmipci*
instad of that module which gave you error.

---

### Post by screamingindigital on 2006-03-15
dpkg -l 'alsa*' reports:

un  alsa           <none>         (no description available)
ii  alsa-base      1.0.9b-4       ALSA driver configuration files
ii  alsa-oss       1.0.9-1        ALSA wrapper for OSS applications
ii  alsa-source    1.0.9b-4       ALSA driver sources
ii  alsa-utils     1.0.9a-4ubuntu ALSA utilities
un  alsa-xmms      <none>         (no description available)
un  alsalib        <none>         (no description available)
un  alsalib0.1.3   <none>         (no description available)
un  alsalib0.3.0   <none>         (no description available)
un  alsalib0.3.0-d <none>         (no description available)
un  alsalib0.3.2   <none>         (no description available)
un  alsalib0.3.2-d <none>         (no description available)
ii  alsamixergui   0.9.0rc2-1-7ub graphical soundcard mixer for ALSA soundcard
un  alsaplayer     <none>         (no description available)
ii  alsaplayer-als 0.99.76-6ubunt PCM player designed for ALSA (ALSA output mo
ii  alsaplayer-com 0.99.76-6ubunt PCM player designed for ALSA (common files)
ii  alsaplayer-dae 0.99.76-6ubunt PCM player designed for ALSA (non-interactiv
ii  alsaplayer-esd 0.99.76-6ubunt PCM player designed for ALSA (ESD output mod
ii  alsaplayer-gtk 0.99.76-6ubunt PCM player designed for ALSA (GTK version)
un  alsaplayer-int <none>         (no description available)
ii  alsaplayer-jac 0.99.76-6ubunt PCM player designed for ALSA (jack output mo
ii  alsaplayer-nas 0.99.76-6ubunt PCM player designed for ALSA (NAS output mod
ii  alsaplayer-oss 0.99.76-6ubunt PCM player designed for ALSA (OSS output mod
un  alsaplayer-out <none>         (no description available)
ii  alsaplayer-tex 0.99.76-6ubunt PCM player designed for ALSA (text version)
ii  alsaplayer-xos 0.99.76-6ubunt PCM player designed for ALSA (osd version)

modinfo snd_cmipci shows:

filename:       /lib/modules/2.6.12-10-386/kernel/sound/pci/snd-cmipci.ko
author:         Takashi Iwai <tiwai@suse.de>
description:    C-Media CMI8x38 PCI
license:        GPL
vermagic:       2.6.12-10-386 386 gcc-3.4
depends:        snd-pcm,snd-opl3-lib,snd-mpu401-uart,snd,gameport
alias:          pci:v000013F6d00000100sv*sd*bc*sc*i*
alias:          pci:v000013F6d00000101sv*sd*bc*sc*i*
alias:          pci:v000013F6d00000111sv*sd*bc*sc*i*
alias:          pci:v000013F6d00000112sv*sd*bc*sc*i*
alias:          pci:v000010B9d00000111sv*sd*bc*sc*i*
srcversion:     117FB7B6932D78567ED05CD
parm:           joystick_port:Joystick port address. (array of int)
parm:           soft_ac3:Sofware-conversion of raw SPDIF packets (model 033 only). (array of bool)
parm:           fm_port:FM port. (array of long)
parm:           mpu_port:MPU-401 port. (array of long)
parm:           enable:Enable C-Media PCI soundcard. (array of bool)
parm:           id:ID string for C-Media PCI soundcard. (array of charp)
parm:           index:Index value for C-Media PCI soundcard. (array of int)


and I tried the other modprobe that you suggested and it said:

FATAL: Module snd_card_cmipci not found.


does any of this help??? :-k

---

### Post by mlind on 2006-03-15
well your alsa portion looks just fine. did you try alsamixer from terminal, does it work?

You should have all necessary modules already loaded at boottime.


But doing
```

modprobe snd-cmipci;modprobe snd-pcm-oss;modprobe snd-mixer-oss;modprobe snd-seq-oss

alsamixer

```

unmute channels, and things should *just work*. I'm out of ideas after this.. :confused:

Maybe that ALSA page will provide something I'm missing here. Their instrctions
are somewhat ambiguous tho..

Just remember that you don't need to compile or make anything, modules are
already provided by kernel.

btw. You can at least see you sound card using *sudo lshw* or *sudo report-hw *commands?

---

### Post by screamingindigital on 2006-03-15
me again.....I tried all the modprobe commands and they returned nothing.  I then tried alsamixer and received the error: 
alsamixer: function snd_ctl_open failed for default: No such file or directory

sudo lshw reports:

 *-multimedia UNCLAIMED
             description: Multimedia audio controller
             product: CM8738
             vendor: C-Media Electronics Inc
             physical id: a
             bus info: pci@00:0a.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             resources: ioport:de00-deff irq:10

still no sound.....I want to thank you for trying to get this working.  I'm going to try a few more things and if that doesn't work then I'll just scrap it and hold out for dapper or try to find a 4th sound card.  Thanks again!!!

---

### Post by mlind on 2006-03-15
no problem mate. Just don't give up ;)

There must be someone else how know these things better than me, or even has  
a same sound card that you do.

I haven't ever broked my sound system, so I don't know how to fix yours either :mrgreen:

---

### Post by DjDarkman on 2006-04-06
I have same soundcard and it works ,but very badly ,for example hardware mixing doesn`t work and I tried to install It`s driver ,but it`s readme is outdated ,it contains information with witch is impossible to install the driver ,I know ,I read that alsa supports it ,but if alsa supports it ,then why doesn`t hardware mixing work ,by the way I have two cmedias "cat /proc/asound/cards
0 [CMI8738MC6     ]: CMI8738-MC6 - C-Media PCI CMI8738-MC6
                     C-Media PCI CMI8738-MC6 (model 55) at 0xb000, irq 17
1 [CMI8738MC6_1   ]: CMI8738-MC6 - C-Media PCI CMI8738-MC6
                     C-Media PCI CMI8738-MC6 (model 55) at 0xa800, irq 16" and they work ,but no hardware mixing is available ,and they support it ,what should I do ,I have major problems ,because of this.

---

### Post by dvarsam on 2006-04-08
Before messing with all these stuff, did you try typing on a Terminal window:

```
alsamixer
```

I thought I had to install drivers & ended up realizing that my Sound card's "audio out" was muted!!!

No need to install drivers for myself...

So, before messing with all those stuff here (& compiling), why don't you check if the your Audio Card works just out of the box?

Hope I helped...

---

