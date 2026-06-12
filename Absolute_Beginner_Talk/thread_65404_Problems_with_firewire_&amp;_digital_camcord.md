---
title: "Problems with firewire &amp; digital camcord"
date: 2005-09-13
forum: Absolute Beginner Talk
---

### Post by shagnthings on 2005-09-13
I'm a new user to Ubuntu, but dabled a bit in other Linux distros (Red Hat, Suse, Mandrake)...I can't get over how easy Ubuntu was to install.  Very impressed so far.

So, I've jumped in the deep end by wiping out Windows on this PC (only one I have with firewire), and am running Ubuntu.  It was my daughter's first day at school, and the wife is out of town.  I wanted to send her some video of my daughter going to school.  Need some help with the camcord though.

I've installed Kino, but it looks like the system doesn't reconized the camcorder pluged into the IEEE 1394 controller (Firewire) port.  I looked in device manager and under the IEEE 1394 controller icon, there are 2 unknown ports.  I'm assuming this is the problem.

Where can I go from here to work on this problem?

---

### Post by evilghost on 2005-09-13
Ah-ha, same exact problem I had :)

Here's what I did to get it working.  The issue has to do with permissions, where the AV Controls/firewire aren't accessible by a non-root user.  Recreating /dev/raw1394 and /dev/video1394 with user permissions work, however, upon reboot these settings are lost :(

As you can see below, only root has access to read from /dev/raw1394.
```

luser@400sc:/dev$ stat /dev/raw1394
  File: `/dev/raw1394'
  Size: 0               Blocks: 0          IO Block: 4096   character special file
Device: bh/11d  Inode: 4114        Links: 1     Device type: ab,0
Access: (0600/crw-------)  Uid: (    0/    root)   Gid: (   44/   video)
Access: 2005-09-12 21:39:52.724414640 -0500
Modify: 2005-09-12 21:39:52.724414640 -0500
Change: 2005-09-12 21:39:52.739412360 -0500

```

What I did, was instead of re-creating the raw1394 device over and over with correct permissions is I now simply run kino using sudo.

I created a new Launcher running the following command "sudo kino %F"

Attached is a screenshot.  I enter my "sudo" password and everything works great.  I'm using a Sony HC-21 DV camera.

Now, here is another thing I noticed.  When I am capturing the video, and I am done, if I close the window the entire computer freezes.  Instead, once I am done capturing, I "Force Quit" the application (see 'Add to panel', and select 'Force Quit').  Then, I reload it and open my captured videos.

It seems to vomit when it unhooks /dev/raw1394 :(

Here's a URL on how to then conver the video using Kino to something that can be burned on DVD.  When my wifes father passed away I used Kino to produce the funeral DVDs/etc and have also used them for some family stuff.

Hope this helps, let me know if I can help you any in the future.

---

### Post by evilghost on 2005-09-13
Edit, seems the URL is no longer valid, but I saved it for future reference.  I'll post it below.  Some of the sections are applicable, others are not.  Just apply those that matter, the creating the dvd-iso, conversion, etc.  I burn my DVDs using NeroLinux; I find it works better and is easier.



 Creating a video DVD from a miniDV camcorder with Linux : Complete step-by-step guide.

Of course, you will have to deal with your hardware compatibility problems and differences with your linux distribution, which is out of the scope of this guide.
0. What I wanted :

   1. Create a DVD of my wedding video shot with a digital camcorder.
   2. Use maximal power and flexibility with minimal cost : Linux seemed to be the good choice. 

1. What I had :

   1. Old computer : Athlon XP 1800/1.5GHz/512Mb RAM/120GB HDD.
   2. Sony HDCR-HC40 NTSC miniDV digital camcorder.
   3. Debian Linux/2.6 kernel. 

2. What I bought :

   1. Adaptec Firewire IEEE1394 PCI card: $30
   2. Firewire IEEE1394 cable: $30 (rip-off ...)
   3. Sony DVD burner DRU-710A: $110. 

Total = $170.
3. Install the new hardware :

   1. Firewire card :

          
	starvinh@saturn:~$dmesg | grep 1394
	ieee1394: Initialized config rom entry `ip1394'
	ohci1394: $Rev: 1203 $ Ben Collins 
	ohci1394: fw-host0: Unexpected PCI resource length of 1000!
	ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[5]  MMIO=[ea001000-ea0017ff]  Max Packet=[2048]        
	ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0000d100803f5c72]
	ip1394: $Rev: 1198 $ Ben Collins 
	ip1394: eth0: IEEE-1394 IPv4 over 1394 Ethernet (fw-host0)
	ieee1394: Current remote IRM is not 1394a-2000 compliant, resetting...
	ieee1394: Node added: ID:BUS[0-00:1023]  GUID[0800460103496d75]
	ieee1394: Node changed: 0-00:1023 -> 0-01:1023
	ieee1394: raw1394: /dev/raw1394 device initialized

   2. DVD burner :

             
      	hdc: SONY DVD RW DRU-710A, ATAPI CD/DVD-ROM drive
	ide1 at 0x170-0x177,0x376 on irq 15

4. Install the software :

   1. Kino : This is what I used to grab a DV file from the digital camcorder and do some basic frame editing.

      	     
	root@saturn:/home/starvinh# apt-get update
	root@saturn:/home/starvinh# apt-get install kino

   2. audacity : I used this to edit the audio stream.

        
	root@saturn:/home/starvinh# apt-get install audacity

   3. mjpegtools : I used this to encode the sound and video for the DVD and multiplex the two into MPEG-2 DVD compatible files.

      
        starvinh@saturn:~/pkg/install$tar -zxvf mjpegtools-1.6.2.tar.gz
	starvinh@saturn:~/pkg/install$cd mjpegtools-1.6.2/
	starvinh@saturn:~/pkg/install/mjpegtools-1.6.2$./configure
	starvinh@saturn:~/pkg/install/mjpegtools-1.6.2$make
	starvinh@saturn:~/pkg/install/mjpegtools-1.6.2$su root
	root@saturn:/home/starvinh/pkg/install/mjpegtools-1.6.2$make install

   4. smilutils : This is optional. I used this to pipe SMIL files produced by Kino to different encoders. This is the most flexible way to encode the edited video.

        root@saturn:/mnt/hdb1# apt-get install smilutils

   5. dvdauthor : I used this to create the DVD file structure from a XML file describing the MPEG files and chapters.

      
      	root@saturn:/home/starvinh# apt-get install dvdauthor

   6. dvdrecord : I used this to burn the final DVD ISO image.

        
	root@saturn:/home/starvinh# apt-get install dvdrecord

5. Acquire the DV file :

Configure the type of video that you want to use when acquiring. You can use the raw DV format. I chose to use the AVI to contain the DV as it is easier for me to play them directly.
6. Frame editing

I did all my frame editing by splitting and joining scenes and removing what was too dark or unnecessary.
7. Scene transitions

There are some pretty good video editors out there like Cinerella but my computer was too slow. I decided to use Kino directly and install some FX plugins :

root@saturn:# apt-get install kino-dvtitler
root@saturn:# apt-get install kino-timfx

8 . Encode the MPEG-2 video :

   1. Use either Kino's pipe to the MPJPEG tools, making sure the MPEG-2 DVD format is selected. Read the MAN page for the tools options :

  
	mpeg2enc -v 0 -f 8 -I 1 -n n -a 2
	mp2enc -v 0 -r 48000 -b 192
	mplex -v 0 -f 8

   2. Or use them separately(for example to edit the audio stream then multiplex it later with the video stream). That is done by reading the Kino SMIL file (using the smilutils package) and pipe it to an encoder :

        smil2yuv church.smil | mpeg2enc -v 0 -f 8 -I 1 -n n -a 2 -o church_test.mpv

This part is very CPU intensive. It took me around six or seven hours to render an hour and half of above average compresion video.

top - 00:46:26 up 1 day,  5:23,  2 users,  load average: 1.47, 1.28, 1.15
Tasks:  75 total,   2 running,  73 sleeping,   0 stopped,   0 zombie
Cpu(s): 91.7% us,  5.0% sy,  0.0% ni,  0.0% id,  2.6% wa,  0.3% hi,  0.3% si
Mem:    515556k total,   512020k used,     3536k free,    23740k buffers
Swap:        0k total,        0k used,        0k free,   315820k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
30136 root      25   0 48016  36m 2480 R 62.2  7.2  35:30.90 mpeg2enc
   
		  
starvinh@saturn:/mnt/hdb1/wedding_mpg$ acpi -V
     Thermal 1: ok, 54.0 degrees C
   
>>> ExportMJPEG::startExport
>>> Generated video pipe ' mpeg2enc -v 0 -f 8 -I 1 -n p -a 2 -o '/mnt/hdb1/wedding_mpg/reception'.mpv'
>>> Generated audio pipe '|mp2enc -v 0 -r 48000 -b 192 -o '/mnt/hdb1/wedding_mpg/reception'.mp2'
   
    Executing 'mplex -v 0 -f 8 -o '/mnt/hdb1/wedding_mpg/reception'%03d.mpeg '/mnt/hdb1/wedding_mpg/reception'.mpv '/mnt/hdb1/wedding_mpg/reception'.mp2'

9. Create the DVD file structure.

   1. Create a XML file to describe where the MPEG files are and to add the chapters : wedding.xml
   2. Use the XML file as input to dvdauthor:

starvinh@saturn:~$ mkdir dvdauthor_wedding
starvinh@saturn:~$ cd dvdauthor_wedding/
starvinh@saturn:~/dvdauthor_wedding$ dvdauthor -o wedding -x wedding.xml
DVDAuthor::dvdauthor, version 0.6.10.
Build options: gnugetopt magick iconv freetype fribidi
Send bugs to 

INFO: Locale=C
INFO: Converting filenames to ANSI_X3.4-1968
INFO: dvdauthor creating VTS
STAT: Picking VTS 01

STAT: Processing /mnt/hdb2/wedding_morning_mpeg/morning001.mpeg...
STAT: VOBU 1616 at 736MB, 1 PGCS
INFO: Video pts = 0.178 .. 964.574
INFO: Audio[8] pts = 0.178 .. 964.522

STAT: Processing /mnt/hdb1/wedding_mpg/church001.mpeg...
STAT: VOBU 4645 at 2091MB, 1 PGCS
INFO: Video pts = 0.178 .. 1816.625
INFO: Audio[8] pts = 0.178 .. 1816.618

STAT: Processing /mnt/hdb1/wedding_mpg/reception001.mpeg...
STAT: VOBU 9038 at 3803MB, 1 PGCS
INFO: Video pts = 0.178 .. 2603.578
INFO: Audio[8] pts = 0.178 .. 2603.506
STAT: VOBU 9046 at 3806MB, 1 PGCS
INFO: Generating VTS with the following video attributes:
INFO: MPEG version: mpeg2
INFO: TV standard: ntsc
INFO: Aspect ratio: 4:3
INFO: Resolution: 720x480
INFO: Audio ch 0 format: mp2/2ch, 48khz 20bps

STAT: fixed 9046 VOBUS
INFO: dvdauthor creating table of contents
INFO: Scanning wedding/VIDEO_TS/VTS_01_0.IFO

10. Create ISO image.

starvinh@saturn:/mnt/hda2/wedding_dvd_iso$ 
mkisofs -o imagedvd.iso -dvd-video /home/starvinh/dvdauthor_wedding/wedding/
  0.26% done, estimate finish Wed Nov 10 19:26:17 2004
  0.51% done, estimate finish Wed Nov 10 19:23:02 2004
  0.77% done, estimate finish Wed Nov 10 19:21:57 2004
  1.03% done, estimate finish Wed Nov 10 19:21:25 2004
  1.28% done, estimate finish Wed Nov 10 19:22:23 2004
  ...
 99.77% done, estimate finish Wed Nov 10 19:24:29 2004
Total translation table size: 0
Total rockridge attributes bytes: 0
Total directory bytes: 4096
Path table size(bytes): 42
Max brk space used 21000
1949570 extents written (3807 MB)

11. Verify ISO image

root@saturn:/mnt/hda2/wedding_dvd_iso# ll
total 3902952
-rw-r--r--    1 root     root     3992719360 Nov 10 19:24 imagedvd.iso
root@saturn:/mnt/hda2/wedding_dvd_iso# isoinfo -i imagedvd.iso -l

Directory listing of /
d---------   0    0    0            2048 Nov 10 2004 [    277 02]  .
d---------   0    0    0            2048 Nov 10 2004 [    277 02]  ..
d---------   0    0    0            2048 Nov 10 2004 [    279 02]  AUDIO_TS
d---------   0    0    0            2048 Nov 10 2004 [    278 02]  VIDEO_TS

Directory listing of /AUDIO_TS/
d---------   0    0    0            2048 Nov 10 2004 [    279 02]  .
d---------   0    0    0            2048 Nov 10 2004 [    277 02]  ..

Directory listing of /VIDEO_TS/
d---------   0    0    0            2048 Nov 10 2004 [    278 02]  .
d---------   0    0    0            2048 Nov 10 2004 [    277 02]  ..
----------   0    0    0            6144 Nov 10 2004 [    283 00]  VIDEO_TS.BUP;1
----------   0    0    0            6144 Nov 10 2004 [    280 00]  VIDEO_TS.IFO;1
----------   0    0    0           61440 Nov 10 2004 [1949389 00]  VTS_01_0.BUP;1
----------   0    0    0           61440 Nov 10 2004 [    286 00]  VTS_01_0.IFO;1
----------   0    0    0      1073709056 Nov 10 2004 [    316 00]  VTS_01_1.VOB;1
----------   0    0    0      1073709056 Nov 10 2004 [ 524588 00]  VTS_01_2.VOB;1
----------   0    0    0      1073709056 Nov 10 2004 [1048860 00]  VTS_01_3.VOB;1
----------   0    0    0       770574336 Nov 10 2004 [1573132 00]  VTS_01_4.VOB;1


11. Burn the ISO image onto DVD

root@saturn:/mnt/hda2/wedding_dvd_iso# ll
total 3902936
-rw-r--r--    1 root     root     3992702976 Nov 10 21:43 imagedvd.iso
root@saturn:/mnt/hda2/wedding_dvd_iso# dvdrecord -scanbus
dvdrtools v0.1.4
Portions (c) 2002-2003 Ark Linux 
Based on:
Cdrecord 1.11a15 (i386-pc-linux-gnu) Copyright (C) 1995-2001 Jörg Schilling
Linux sg driver version: 3.5.30
Using libscg version 'bero-0.5a'
dvdrecord: Warning: using inofficial version of libscg (bero-0.5a '@(#)scsitransp.c     1.81 01/04/20 Copyright 1988,1995,2000 J. Schilling').
scsibus0:
        0,0,0     0) 'SONY    ' 'DVD RW DRU-710A ' 'BY01' Removable CD-ROM
        0,1,0     1) *
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *
root@saturn:/mnt/hda2/wedding_dvd_iso# dvdrecord speed=4 -dao dev=0,0,0 imagedvd.iso
dvdrtools v0.1.4
Portions (c) 2002-2003 Ark Linux 
Based on:
Cdrecord 1.11a15 (i386-pc-linux-gnu) Copyright (C) 1995-2001 J?rg Schilling
scsidev: '0,0,0'
scsibus: 0 target: 0 lun: 0
Linux sg driver version: 3.5.30
Using libscg version 'bero-0.5a'
dvdrecord: Warning: using inofficial version of libscg (bero-0.5a '@(#)scsitrans
p.c     1.81 01/04/20 Copyright 1988,1995,2000 J. Schilling').
Device type    : Removable CD-ROM
Version        : 2
Response Format: 2
Capabilities   : 
Vendor_info    : 'SONY    '
Identifikation : 'DVD RW DRU-710A '
Revision       : 'BY01'
Device seems to be: Generic mmc2 DVD.
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Starting to write CD/DVD at speed 4 in write mode for single session.
Last chance to quit, starting real write in 0 seconds. Operation starts.
trackno=0
dvdrecord: WARNING: Drive returns wrong startsec (0) using -150
Track 01: Total bytes read/written: 3992702976/3992702976 (1949562 sectors).

- starvinh 11/13/2004.

---

### Post by akhicks on 2005-11-07
Thanks Evil. Excellent post. I had the same problem, which your solution solved.

---

### Post by starvinh on 2006-08-25
Hi there,

I have no idea how some Linux DVD howto I wrote 2 years ago appeared here ...[-X 
Anyways, this is the new link since I moved to a different domain:
[http://www.minhchauvinh.com/weblog/archives/creating-a-video-dvd-from-a-minidv-camcorder-with-linux-complete-step-by-step-guide/18]("http://www.minhchauvinh.com/weblog/archives/creating-a-video-dvd-from-a-minidv-camcorder-with-linux-complete-step-by-step-guide/18")

Hope it's still useful! ;)

---

### Post by evilghost on 2006-08-25
> **starvinh said:**
> Hi there,

I have no idea how some Linux DVD howto I wrote 2 years ago appeared here ...[-X 
Anyways, this is the new link since I moved to a different domain:
[http://www.minhchauvinh.com/weblog/archives/creating-a-video-dvd-from-a-minidv-camcorder-with-linux-complete-step-by-step-guide/18]("http://www.minhchauvinh.com/weblog/archives/creating-a-video-dvd-from-a-minidv-camcorder-with-linux-complete-step-by-step-guide/18")

Hope it's still useful! ;)

Thanks that is useful.  I wrote a bash-script to take the dvd-author xml and create the iso file struction and then the actual ISO.  I'll post it once I get home.

---

