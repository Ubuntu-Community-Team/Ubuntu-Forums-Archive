---
title: "Problemes amb el so a l'avidemux"
date: 2009-03-04
forum: Catalan Team
---

### Post by lo gambusí on 2009-03-04
Hola!

He passat a mpg un DVD amb el k9copy i vull reduir-ne la mida per poder-lo penjar a internet. He utilitzat l'avidemux per fer-ne la reducció, però un cop feta (i amb la mida reduïda) no em funciona el so.

Creieu que és perquè em deixo alguna cosa? O és algun error del programa?

Moltes gràcies.

---

### Post by lo gambusí on 2009-03-09
Pujo el fil a veure si algú em podria donar un cop de mà... espero no infringir moltes normes.:P

---

### Post by tanreb20 on 2009-03-09
Has provat de executar-ho desde consola? Per saber l'error que odna?

---

### Post by lo gambusí on 2009-03-11
El que em surt a la consola és això:

> logambusi@logambusi-laptop:~$ avidemux2_gtk
***************************
  Avidemux v2.4.3
***************************
 [http://www.avidemux.org](http://www.avidemux.org)
 Code      : Mean, JSC, Gruntster 
 GFX       : Nestor Di , [email]nestordi@augcyl.org[/email]
 Design    : Jakub Misak
 FreeBSD   : Anish Mistry, [email]amistry@am-productions.biz[/email]
 Audio     : Mihail Zenkov
 MacOsX    : Kuisathaverat
 Win32     : Gruntster

Compiler: GCC 4.3.1
Build Target: Linux (x86)
User Interface: GTK+ (2.14.4)

Large file available: 1 offset

Initialising prefs
Directory /home/logambusi/.avidemux exists.Good.
Using /home/logambusi/.avidemux as base directory for prefs/jobs/...
Preferences found and loaded
[cpuCaps]Checking CPU capabilities
		MMX detected 
		MMXEXT detected 
		SSE detected 
		SSE2 detected 
		SSE3 detected 
		SSSE3 detected 
[cpuCaps]End of CPU capabilities check (cpuMask :ffffffff)

 Registering Encoders
*********************
MJPEG encoder registered
Xvid-4 encoder registered
FFmpeg encoder registered

3 encoder(s) registered

[SDL] Version: 1.2.12
[SDL] Initialisation succeeded
[SDL] Video Driver: x11


[Locale] setlocale ca_ES.UTF-8
[Locale] Textdomain was messages
[Locale] Textdomain is now avidemux
[Locale] Files for avidemux appear to be in /usr/share/locale
[Locale] Test: _Fitxer

Initializing Dithering tables
[xvid] Initializing global Xvid 4
[xvid] Build: xvid-1.1.2
[xvid] SIMD supported: (cf)
		MMX
		MMXEXT
		SSE
		SSE2

(avidemux2_gtk:15235): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
Found 20 video encoder
Found 9 audio encoder
Found 13 Format 
Directory /home/logambusi/.avidemux/custom exists.Good.
No custom script
Found 0 custom scripts, adding them
Menu built
The screen seems to be 1280 x 800 px
/dev/input/event0: Permission denied
/dev/input/event1: Permission denied
/dev/input/event2: Permission denied
/dev/input/event3: Permission denied
/dev/input/event4: Permission denied
/dev/input/event5: Permission denied
/dev/input/event6: Permission denied
/dev/input/event7: Permission denied
/dev/input/event8: Permission denied
/dev/input/event9: Permission denied
/dev/input/event10: Permission denied
No physical Jog/Shuttle device found.
Initializing postproc
Deleting post proc
updating post proc
Enabled type:3 strength:3

 Registering Filters
*********************

Using real audio device
Spidermonkey initialized.
No crash file (/home/logambusi/.avidemux/crash.js)
ba010000 -> ba010000
 
 Mpeg file detected...
Filesystem is writable
Probing /home/logambusi/Vídeos/Arrels de Lluita.mpg for streams...
Probing : /home/logambusi/Vídeos/Arrels de Lluita.mpg

Simple loading: 
 file: /home/logambusi/Vídeos/Arrels de Lluita.mpg, size: 3517280256
 found 1 files 
Done 
/home/logambusi/Vídeos/Arrels de Lluita.mpg looks like Mpeg PS (392/1290)
Creating mpeg PS demuxer  main Pid: EA 

Simple loading: 
 file: /home/logambusi/Vídeos/Arrels de Lluita.mpg, size: 3517280256
 found 1 files 
Done 
Probe exceeded
Refill failed at 0  
Stopped at 0, 0 MB
a0: there is something 3322 kb
bf: there is something 74 kb
e0: there is something 6644 kb
Found video as e0, and 1 audio tracks
Probing : /home/logambusi/Vídeos/Arrels de Lluita.mpg

Simple loading: 
 file: /home/logambusi/Vídeos/Arrels de Lluita.mpg, size: 3517280256
 found 1 files 
Done 
/home/logambusi/Vídeos/Arrels de Lluita.mpg looks like Mpeg PS (392/1290)

Simple loading: 
 file: /home/logambusi/Vídeos/Arrels de Lluita.mpg, size: 3517280256
 found 1 files 
Done 
Creating mpeg PS demuxer  main Pid: E0 

Simple loading: 
 file: /home/logambusi/Vídeos/Arrels de Lluita.mpg, size: 3517280256
 found 1 files 
Done 
*********Indexing started (2 audio tracks)***********
Dmx IO: End of file met (3517280255 / 3517280256 seg1)
DmxPS: cannot sync  at 3517280255/3517280256
Refill failed at -777770994  

 io error , aborting sync 1
*********Indexing Ended (2 audio tracks)***********
Time difference:3191 s
25000 :50000 / 25005 , 49,990000
Seems to be frame encoded
*********Indexing stopped***********
Found       :6650 gop
Found       :79793 image
Average fps :25005 /1000 fps
594d4441 -> 594d4441
 
 New mpeg index file detected..

  opening d2v file : /home/logambusi/Vídeos/Arrels de Lluita.mpg.idx
For file :/home/logambusi/Vídeos/Arrels de Lluita.mpg
Pic      :720x576, 25000 fps
#Gop     :6650
#Img     :79793
Creating mpeg PS demuxer  main Pid: E0 

Simple loading: 
 file: /home/logambusi/Vídeos/Arrels de Lluita.mpg, size: 3517280256
 found 1 files 
Done 
Dropping 1 last B/P frames
 Creating start sequence (2062)..

 0000 : ...&#65533;-.@#.&#65533;#&#65533;....  00 00 01 b3 2d 02 40 23 13 88 23 81 10 11 11 12
 0010 : ................  12 12 13 13 13 13 14 14 14 14 14 15 15 15 15 15
 0020 : ................  15 16 16 16 16 16 16 16 17 17 17 17 17 17 17 17
 0030 : ..  18 18
Image :6647, seqLen : 98 seq 0 0 1 b3
Reordering mpeg frames
Renumbered Gop  1 /6650

  opening dmx file for audio track : /home/logambusi/Vídeos/Arrels de Lluita.mpg.idx
Creating mpeg PS demuxer  main Pid: A0 

Simple loading: 
 file: /home/logambusi/Vídeos/Arrels de Lluita.mpg, size: 3517280256
 found 1 files 
Done 
Building index with 6650 sync points
Filling audio header
Audio index loaded, probing...
Probing track:0, pid: 0 pes:a0

 DMX audio initialized (612817920 bytes)
With 6650 sync point
Mpeg index file successfully read
The video codec has some extradata (98 bytes)

 0000 : ...&#65533;-.@#.&#65533;#&#65533;....  00 00 01 b3 2d 02 40 23 13 88 23 81 10 11 11 12
 0010 : ................  12 12 13 13 13 13 14 14 14 14 14 15 15 15 15 15
 0020 : ................  15 16 16 16 16 16 16 16 17 17 17 17 17 17 17 17
 0030 : ................  18 18 18 18 18 18 18 19 1a 19 1a 1a 19 1b 1b 1b
 0040 : ...........!...&#65533;  1a 1b 1c 1c 1c 1c 1e 1e 1e 1f 1f 21 00 00 01 b5
 0050 : .&#65533;.......&#65533;#....B  14 82 00 01 00 00 00 00 01 b5 23 05 05 06 0b 42
 0060 : ..  12 00
Deleting post proc
Initializing postproc
Deleting post proc
updating post proc
Enabled type:3 strength:3
[Editor] Duration in seconds: 3191, in samples: 153200640

 Decoder FCC: MPEG (4745504D)
Searching decoder (720 x 576, extradataSize:98)...

 using Mpeg1/2 codec (libmpeg2)
[lavc] Build: 3352580
[lavc] Enabling MT decoder with 2 threads
[lavc] Decoder init: CODEC_ID_MPEG2VIDEO video decoder initialized!

 checking for B-Frames...
 scanning 125 frames
 * #  * #  * #  * #  * #  * # 
 * #  * #  * #  * #  * #  * #  * #  * #  * #  * # 
 * #  * #  * #  * #  * #  * #  * #  * #  * # 
 * #  * #  * #  * #  * #  * #  * #  * #  * # 
 * #  * #  * #  * #  * #  * #  * #  * #  * #  * # 
 * #  * #  * #  * #  * #  * #  * #  * #  * # 
 * #  * #  * #  * #  * #  * #  * #  * #  * # 
 * #  * #  * #  * #  * #  * #  * #  * # 

 Mmm this appear to have b-frame...

 And the index is ok

 Frames re-ordered, B-frame friendly now :)
 End of B-frame check

 Editor :Audio streamer initialized
 Audio codec:  LPCM swapped
[GTK] Changing size to 720 576
[GTK] Changing size to 720 576
[GTK] Changing size to 720 576

** conf updated **

(avidemux2_gtk:15235): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(avidemux2_gtk:15235): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(avidemux2_gtk:15235): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
Video duration :3192
Track1 bitrate :1536
Track2 bitrate :0
**saving:**
Output format:0
 AVI family

 video process mode : 0
 not encodable, cancelling smart mode
 mux mode : 1 mux param 0
[Raw shift] : Start:0 ms, shift  0
[Raw shift] : Start:0 ms, offset in sample  0
PacketQueue AVI audioQ created
[AudioQueueThread] Starting
[ODML] using ODML placeholder of size 4096 bytes
[ODML] using ODML placeholder of size 4096 bytes
Second audio track absent

 writing 79792 frames
EditorPacket : End of stream Segment :0/1 
This sample : 153200640 ((null)) total :153200640 ((null))
[AudioQueueThread] Exiting
[AudioThread] Target 4294901760, got 153200640, 0,035670 %

 writing 159584 index parts
 received 79792 video parts
 Updating headers...

 End of movie, 
 video frames : 79792
 audio frames : 612802560
 Saving AVI (v_engine)... done
[AVI] Cleaning audio
[lavc] Killing decoding threads
[lavc] Destroyed
Deleting post proc
[GTK] Changing size to 720 576
Cleaning up
Waiting for Spidermonkey to finish...
Cleaning up Spidermonkey.
[SDL] Quitting...
End of cleanup

Images stat:
___________
Max memory consumed (MB)     : 7897
Current memory consumed (MB) : 0
Max image used               : 13
Cur image used               : 0
Global mem stat
______________
	Memory consumed: 0 (MB)

Goodbye...

logambusi@logambusi-laptop:~$ 


Un cop convertit, he tornat a provar si funcionava i em passa el mateix: es reprodueix el vídeo però no el so. He anat a la pestanya "So" del VLC i sortia *Disabled*, i al dir-li que vull la pista de so *Track 1* em surt el següent missatge:> [QUOTE]No suitable decoder module:
VLC does not support the audio or video format "aflt". Unfortunately there is no way for you to fix this.
[/QUOTE]

---

### Post by lo gambusí on 2009-03-13
He provat amb altres reproductors multimèdia i tampoc em funciona el so.

---

