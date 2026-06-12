---
title: "dosbox/tombraider 1 gold"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by noob_1 on 2007-09-08
i have dosbox installed but when i try to install tombraider 1 gold game, the audio player pops up. help.

---

### Post by graigsmith on 2007-09-09
you have to set it up and then install it from WITHIN the dosbox program.

heres an example from my old ultima underworld game.  you need to make a config file for one. and to set it up properly  then you need to call it with the -conf option```
dosbox dosbox -conf /home/graig/.games/DOS/underworld.conf
```

the config file in this case looks like this.  the name is underworld.conf  Note at the bottom in the autoexec section. i include lines to set up the C: drive in the emulated dos.   so basically i just mounted the folder with the underworld game in it.  and when i go into dosbox with the config file, it mounts it. changes to drive c with the c: command.  then the uw command launches the game.   and for the most part you can simply just copy the whole conf file, and just make adjustments as needed.
```
[sdl]
# fullscreen -- Start dosbox directly in fullscreen.
# fulldouble -- Use double buffering in fullscreen.
# fullfixed -- Don't resize the screen when in fullscreen.
# fullresolution -- What resolution to use for fullscreen, use together with fullfixed.
# output -- What to use for output: surface,overlay,opengl,openglnb.
# hwscale -- Extra scaling of window if the output device supports hardware scaling.
# autolock -- Mouse will automatically lock, if you click on the screen.
# sensitiviy -- Mouse sensitivity.
# waitonerror -- Wait before closing the console if dosbox has an error.
# priority -- Priority levels for dosbox: lower,normal,higher,highest.
#             Second entry behind the comma is for when dosbox is not focused/minimized.
# mapperfile -- File used to load/save the key/event mappings from.

fullscreen=false
fulldouble=false
fullfixed=false
fullresolution=1024x768
output=surface
hwscale=2
autolock=true
sensitivity=100
waitonerror=true
priority=higher,normal
mapperfile=/home/graig/.games/DOS/uw.txt

[dosbox]
# language -- Select another language file.
# memsize -- Amount of memory dosbox has in megabytes.
# machine -- The type of machine tries to emulate:hercules,cga,tandy,vga.
# captures -- Directory where things like wave,midi,screenshot get captured.

language=
machine=vga
captures=capture
memsize=16

[render]
# frameskip -- How many frames dosbox skips before drawing one.
# aspect -- Do aspect correction.
# scaler -- Scaler used to enlarge/enhance low resolution modes.
#           Supported are none,normal2x,advmame2x,advmame3x,advinterp2x,interp2x,tv2x.

frameskip=1
aspect=false
scaler=normal3x

[cpu]
# core -- CPU Core used in emulation: simple,normal,full,dynamic.
# cycles -- Amount of instructions dosbox tries to emulate each millisecond.
#           Setting this higher than your machine can handle is bad!
# cycleup   -- Amount of cycles to increase/decrease with keycombo.
# cycledown    Setting it lower than 100 will be a percentage.

core=dynamic
cycles=50000
cycleup=500
cycledown=500

[mixer]
# nosound -- Enable silent mode, sound is still emulated though.
# rate -- Mixer sample rate, setting any devices higher than this will
#         probably lower their sound quality.
# blocksize -- Mixer block size, larger blocks might help sound stuttering
#              but sound will also be more lagged.
# prebuffer -- How many milliseconds of data to keep on top of the blocksize.

nosound=false
rate=22050
blocksize=2048
prebuffer=10

[midi]
# mpu401      -- Enable MPU-401 Emulation.
# intelligent -- Operate in Intelligent mode.
# device      -- Device that will receive the MIDI data from MPU-401.
#                This can be default,alsa,oss,win32,coreaudio,none.
# config      -- Special configuration options for the device.

mpu401=true
intelligent=true
device=default
config=

[sblaster]
# type -- Type of sblaster to emulate:none,sb1,sb2,sbpro1,sbpro2,sb16.
# base,irq,dma,hdma -- The IO/IRQ/DMA/High DMA address of the soundblaster.
# mixer -- Allow the soundblaster mixer to modify the dosbox mixer.
# oplmode -- Type of OPL emulation: auto,cms,opl2,dualopl2,opl3.
#            On auto the mode is determined by sblaster type.
# oplrate -- Sample rate of OPL music emulation.

type=sb16
base=220
irq=7
dma=1
hdma=5
mixer=true
oplmode=auto
oplrate=22050

[gus]
# gus -- Enable the Gravis Ultrasound emulation.
# base,irq1,irq2,dma1,dma2 -- The IO/IRQ/DMA addresses of the 
#            Gravis Ultrasound. (Same IRQ's and DMA's are OK.)
# rate -- Sample rate of Ultrasound emulation.
# ultradir -- Path to Ultrasound directory.  In this directory
#             there should be a MIDI directory that contains
#             the patch files for GUS playback.  Patch sets used
#             with Timidity should work fine.

gus=false
rate=22050
base=240
irq1=5
irq2=5
dma1=3
dma2=3
ultradir=C:\ULTRASND

[speaker]
# pcspeaker -- Enable PC-Speaker emulation.
# pcrate -- Sample rate of the PC-Speaker sound generation.
# tandyrate -- Sample rate of the Tandy 3-Voice generation.
#              Tandysound emulation is present if machine is set to tandy.
# disney -- Enable Disney Sound Source emulation.

#pcspeaker=true
#pcrate=22050
#tandyrate=22050
#disney=true

[bios]
# Nothing to setup yet!


[dos]
# xms -- Enable XMS support.
# ems -- Enable EMS support.

xms=true
ems=true

[modem]
# modem -- Enable virtual modem emulation.
# comport -- COM Port modem is connected to.
# listenport -- TCP Port the modem listens on for incoming connections.

modem=false
comport=2
listenport=23

[ipx]
# ipx -- Enable ipx over UDP/IP emulation.

ipx=false

[autoexec]
# Lines in this section will be run at startup.
mount c /home/graig/.games/DOS/UW
c:
uw
```

---

