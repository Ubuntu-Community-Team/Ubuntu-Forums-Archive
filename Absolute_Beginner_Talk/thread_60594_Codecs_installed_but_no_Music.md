---
title: "Codecs installed but no Music?"
date: 2005-08-28
forum: Absolute Beginner Talk
---

### Post by Mike-97470 on 2005-08-28
Hello, yes this my first post:

I d/l'ed and installed without a hitch although I did have to learn how to spell iso.  Everything pretty much works great except for some minor gyrations like teaching Networking that a modem IP is not a DNS.  I've got my NTFS volumes mounted at /home (will probably switch to FAT), and OO, printer setup, Firefox, and T-Bird work geat. I switched to T-Bird to import mail and addresses and have the Calender and Hotmail extensions working.  I switched to the 686 kernel for no good reason, I guess, because I can't tell any difference. 

The worst thing that happened was when I once forgot the boot disk in the drive--hehe.

But I'm going to give up trying to get music working:

I'll describe Rhythmbox.  It doesn't play music.  It ripped a CD to ogg, it sees the files, but they are grayed out.  It also sees mp3's grayed out. I've assumed that gstreamer and the plug-ins aren't installed correctly, so I've checked everything against the user's Guide reccommended Codecs and reinstalled.

I've pasted a terminal session that I think shows that the reccomended plug-ins are up-to-date and installed.  (Perferences/Sound Perferences sound events play just fine.)

Please give me some hint of what to try next!
Thankks,
Mike


mike@MikesPavillion:~$ sudo apt-get install gstreamer0.8-plugins
Password:
Reading package lists... Done
Building dependency tree... Done
gstreamer0.8-plugins is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 40 not upgraded.
mike@MikesPavillion:~$ sudo apt-get install gstreamer0.8-plugins
Reading package lists... Done
Building dependency tree... Done
gstreamer0.8-plugins is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 40 not upgraded.
mike@MikesPavillion:~$ sudo apt-get install gstreamer0.8-lame
Reading package lists... Done
Building dependency tree... Done
gstreamer0.8-lame is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 40 not upgraded.
mike@MikesPavillion:~$ sudo apt-get install gstreamer0.8-ffmpeg
Reading package lists... Done
Building dependency tree... Done
gstreamer0.8-ffmpeg is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 40 not upgraded.
mike@MikesPavillion:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree... Done
w32codecs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 40 not upgraded.
mike@MikesPavillion:~$ sudo apt-get install libdivx4linux
Reading package lists... Done
Building dependency tree... Done
libdivx4linux is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 40 not upgraded.
mike@MikesPavillion:~$ sudo apt-get install lame
Reading package lists... Done
Building dependency tree... Done
lame is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 40 not upgraded.
mike@MikesPavillion:~$ sudo apt-get install sox
Reading package lists... Done
Building dependency tree... Done
sox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 40 not upgraded.
mike@MikesPavillion:~$ sudo apt-get install ffmpeg
Reading package lists... Done
Building dependency tree... Done
ffmpeg is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 40 not upgraded.
mike@MikesPavillion:~$ sudo apt-get install mjpegtools
Reading package lists... Done
Building dependency tree... Done
mjpegtools is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 40 not upgraded.
mike@MikesPavillion:~$ sudo apt-get install vorbis-tools
Reading package lists... Done
Building dependency tree... Done
vorbis-tools is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 40 not upgraded.
mike@MikesPavillion:~$
mike@MikesPavillion:~$ gst-register-0.8
Trying to load global_registry ...
Added plugin lame with 1 feature.
Added plugin swfdec with 1 feature.
Added plugin siddec with 1 feature.
Added plugin mpeg2dec with 1 feature.
Added plugin mikmod with 1 feature.
Added plugin jack with 3 features.
Added plugin festival with 1 feature.
Added plugin artsdsink with 1 feature.
Added plugin aasink with 1 feature.
Added plugin xwindowlistener with 0 features.
Added plugin jpeg with 5 features.
Added plugin hermescolorspace with 1 feature.
Added plugin gsm with 2 features.
Added plugin gnomevfs with 2 features.
Added plugin dvdreadsrc with 1 feature.
Added plugin dvdnavsrc with 1 feature.
Added plugin gst1394 with 1 feature.
Added plugin cdparanoia with 1 feature.
Added plugin y4menc with 1 feature.
Added plugin wavenc with 1 feature.
Added plugin volume with 1 feature.
Added plugin volenv with 1 feature.
Added plugin videotestsrc with 1 feature.
Added plugin videoscale with 1 feature.
Added plugin videorate with 1 feature.
Added plugin videomixer with 1 feature.
Added plugin gstvideofilter with 0 features.
Added plugin videodrop with 1 feature.
Added plugin videocrop with 1 feature.
Added plugin videobox with 1 feature.
Added plugin videobalance with 1 feature.
Added plugin vcdsrc with 1 feature.
Added plugin vbidec with 1 feature.
Added plugin video4linux2 with 2 features.
Added plugin video4linux with 5 features.
Added plugin udp with 2 features.
Added plugin typefindfunctions with 66 features.
Added plugin tta with 2 features.
Added plugin timeoverlay with 1 feature.
Added plugin textoverlay with 1 feature.
Added plugin gsttags with 1 feature.
Added plugin switch with 1 feature.
Added plugin subparse with 1 feature.
Added plugin stereo with 1 feature.
Added plugin speed with 1 feature.
Added plugin spectrum with 1 feature.
Added plugin snapshot with 1 feature.
Added plugin smpte with 1 feature.
Added plugin smooth with 1 feature.
Added plugin sine with 1 feature.
Added plugin silence with 1 feature.
Added plugin shout2send with 1 feature.
Added plugin rtjpeg with 2 features.
Added plugin rtp with 4 features.
Added plugin rfbsrc with 1 feature.
Added plugin games with 1 feature.
Added plugin png with 2 features.
Added plugin playondemand with 1 feature.
Added plugin playbin with 1 feature.
Added plugin passthrough with 1 feature.
Added plugin overlay with 1 feature.
Added plugin navigationtest with 1 feature.
Added plugin nassink with 1 feature.
Added plugin multipart with 2 features.
Added plugin gstmultifilesink with 1 feature.
Added plugin mulaw with 2 features.
Added plugin mpegaudioparse with 1 feature.
Added plugin mpegaudio with 1 feature.
Added plugin mpeg2sub with 1 feature.
Added plugin mpeg1videoparse with 1 feature.
Added plugin monoscope with 1 feature.
Added plugin median with 1 feature.
Added plugin level with 1 feature.
Added plugin ladspa with 0 features.
Added plugin interleave with 2 features.
Added plugin gconfelements with 2 features.
Added plugin gdkpixbuf with 2 features.
Added plugin gamma with 1 feature.
Added plugin filter with 3 features.
Added plugin ffmpegcolorspace with 1 feature.
Added plugin effectv with 8 features.
Added plugin efence with 1 feature.
Added plugin dvdlpcmdec with 1 feature.
Added plugin deinterlace with 1 feature.
Added plugin decodebin with 1 feature.
Added plugin debug with 5 features.
Added plugin colorspace with 1 feature.
Added plugin chart with 1 feature.
Added plugin cdplayer with 1 feature.
Added plugin auparse with 1 feature.
Added plugin autodetect with 2 features.
Added plugin audiorate with 1 feature.
Added plugin gstaudiofilter with 0 features.
Added plugin alphacolor with 1 feature.
Added plugin alpha with 1 feature.
Added plugin alaw with 2 features.
Added plugin ac3parse with 1 feature.
Added plugin gstvideo with 0 features.
Added plugin gstresample with 0 features.
Added plugin gstidct with 0 features.
Added plugin gstaudio with 0 features.
Added plugin gstspider with 2 features.
Added plugin gstindexers with 2 features.
Added plugin gstgetbits with 0 features.
Added plugin gstelements with 15 features.
Added plugin gstdataprotocol with 0 features.
Added plugin gstbytestream with 0 features.
Added plugin gstoptscheduler with 1 feature.
Added plugin gstoptomegascheduler with 1 feature.
Added plugin gstoptgthreadscheduler with 1 feature.
Added plugin gstfairgthreadscheduler with 1 feature.
Added plugin gstentryomegascheduler with 1 feature.
Added plugin gstentrygthreadscheduler with 1 feature.
Added plugin gstbasicomegascheduler with 1 feature.
Added plugin gstbasicgthreadscheduler with 1 feature.
Added plugin ffmpeg with 199 features.
Added plugin mad with 5 features.
Added plugin cacasink with 1 feature.
Added plugin a52dec with 1 feature.
Added plugin xvimagesink with 1 feature.
Added plugin ximagesink with 1 feature.
Added plugin vorbis with 4 features.
Added plugin theora with 2 features.
Added plugin speex with 2 features.
Added plugin sdlvideosink with 1 feature.
Added plugin flac with 3 features.
Added plugin dvdec with 1 feature.
Added plugin gstaf with 3 features.
Added plugin videoflip with 1 feature.
Added plugin tcp with 7 features.
Added plugin synaesthesia with 1 feature.
Added plugin smoothwave with 1 feature.
Added plugin rmdemux with 1 feature.
Added plugin qtdemux with 1 feature.
Added plugin mpegstream with 4 features.
Added plugin system_encode with 1 feature.
Added plugin modplug with 1 feature.
Added plugin mng with 2 features.
Added plugin mixmatrix with 1 feature.
Added plugin goom with 1 feature.
Added plugin flxdec with 1 feature.
Added plugin gstequalizer with 1 feature.
Added plugin dtsdec with 1 feature.
Added plugin cutter with 1 feature.
Added plugin audioscale with 1 feature.
Added plugin gstaudioconvert with 2 features.
Added plugin apetag with 1 feature.
Added plugin adder with 1 feature.
Added plugin alsa with 3 features.
Added plugin esdsink with 2 features.
Added plugin ossaudio with 3 features.
Added plugin riff with 0 features.
Added plugin wavparse with 1 feature.
Added plugin ogg with 5 features.
Added plugin matroska with 2 features.
Added plugin cdxaparse with 2 features.
Added plugin avi with 2 features.
Added plugin asf with 2 features.
Rebuilding user_registry (/home/mike/.gstreamer-0.8/registry.xml) ...
Loaded 158 plugins with 502 features.
mike@MikesPavillion:~$

---

### Post by Kapre on 2005-08-28
Are we talking about sound in general on this issue? Or just sound on an application/program?

Is there sound coming out of your speakers when Ubuntu starts? If there is, and you just dont have the sound in your apps (XMMS, BEEP, XINE, TOTEM, etc). Try changing the sourse to ESD (not OSD or ALSA). 

K

---

### Post by Mike-97470 on 2005-08-28
Hello Again, yes this is my second post & hey, I'm on a roll!

Well the File System Checker fixed  /root which got totally hosed--here's the story--

According to suggestion, at least my interpretation, I went looking for esd, osd, and alsa.  Osd was something about video so I forgot that.  Gstreamer had both esd and alsa hooked up so I uninstalled alsa just to be sure it wasn't conflicting (hey, I'm newbie!).

So then I checked Rhythmbox and, sure enough, it could import and play ogg's and mp3's, but the Import Folder, Chose Files, files were still grayed-out.  I'd been had! Yep, tricked!  Those grayed-out file names had me baffled, buffaloed, and bamboozled!  And just yesterday I read this very fine article [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm) =  Linux is not Windows!

I then checked Muine which always has grayed-out file names in it's Import Folder window just like Rhythmbox, and it played just fine as well.  

Meanwhile, at some time along here, I re-installed -alsa and its codependent -plugins, well, basically that wasn't the problem and besides -plugins are in the Codecs section of the User's Guide.

I then checked BeepMP which doesn't have grayed-out file names, but would display scolling file names, but not play sound.  The Play(/Stop) button indicates it is playing, but no sound.  If I close it at that point it closes, but if I click the Stop(/Play) it hangs up.  Its little GUI application window goes completely dead.  And then when I close it via the Task Bar, a message  window like this appears: <<The window "1. Carole King - Smackwater Jack (3:42) - BMP" is not responding.  Forcing this application to quit will cause you to lose any unsaved changes. >>  Well, so much for Beep, I'm 2 for 3!

So then I installed XMMS to see if it could do better than Beep.  I imported the Cd's ogg files into a playlist, then . .  Well, somehow or other I got it to lockup the complete desktop UI except for cursor movement.

So I did a power reset and rebooted.  I tested XMMS again and didn't get the UI lockup, but it didn't play the selected file either.  I think it may behave the same as Beep, but I can't really remember and I'm afraid to test it again right now . . . because the next time I booted, /root had been corrupted (and I'm pretty sure it was the next time).  And I had visions of forgetting that boot disk in the drive, er, starting over.

So 2 for 4 isn't bad, and I really want to try to get faad2 and gtkpod working, not to mention efax.  

I'm really, really impressed with ext2 and fsck, but I'm considering switching to ext3.  I only have so many sets of clean underwear!

Mike

---

