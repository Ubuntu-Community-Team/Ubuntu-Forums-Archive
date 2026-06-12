---
title: "No sound, Emu 1212M &amp; AC'97 ALC850"
date: 2005-06-15
forum: Absolute Beginner Talk
---

### Post by halfpower on 2005-06-15
I currently have no sound with my Ubuntu OS.  When I initially installed Ubuntu, I noticed that it the Ubuntu thinks I have a Creative Labs Audigy on the PCI bus.  This is not true.  I have an E-mu 1212M on the PCI bus (E-mu is now owned by Creative Labs).  Thus far there are no Linux drivers for the E-mu 1212M, so I am trying to use the audio system built into my motherboard.  

Earlier today I found that I was unable to load MP3's.  I went to the [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs) page, followed the directions, and then through the following commands at terminal

> 
Q: How to install Multimedia Codecs?

   1. Read General Notes
   2. Read How to add extra repositories?

   3. sudo apt-get install w32codecs
   sudo apt-get install gstreamer0.8-plugins
   sudo apt-get install gstreamer0.8-lame
   sudo apt-get install lame
   sudo apt-get install sox
   sudo apt-get install ffmpeg
   sudo apt-get install mjpegtools
   sudo apt-get install vorbis-tools
   gst-register-0.8


I am now able to open MP3's, however, for some reason or another, not all of the items were installed.  Terminal told me that some of the items were not available.

Do you have any idea how I might fix the problem?  Perhaps set Ubuntu to use the on-board audio system?

---

### Post by poofyhairguy on 2005-06-15
[QUOTE=halfpower]
I am now able to open MP3's, however, for some reason or another, not all of the items were installed.  Terminal told me that some of the items were not available.[/QUOTE]

I know the problem. You need to add the Ubuntu Backports to you machine's menu.

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

[QUOTE=halfpower]Do you have any idea how I might fix the problem?  Perhaps set Ubuntu to use the on-board audio system?[/QUOTE]

Thats what I did. Turned it off, took out the pci card, and enable the onboard card in the bios and rebooted.

---

