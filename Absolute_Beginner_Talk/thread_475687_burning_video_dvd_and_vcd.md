---
title: "burning video dvd and vcd"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by zerobinary on 2007-06-16
how do u burn video dvd like avi ogm mkv and make vcd with avi

---

### Post by FleetAdmiral74 on 2007-06-16
there is a program called tovid, works quite well. do a quick search, lots of wikis and instructions.

---

### Post by zerobinary on 2007-06-16
i install it but i can't find the icon 
when i type it in terminal nothing pops up is a command line program and how do u use it 
and it there a gui program for those work
and after this 
  ```
XVID video with mad audio
Target format:
  720 x 480 pixels, 29.970 fps
  m2v video with ac3 audio
  5880 kbits/sec video, 224 kbits/sec audio
Using auto-detected aspect ratio 177:100 (override with -aspect)
No letterboxing necessary
Input is not 29.970 fps. Framerate will be adjusted.
Scaling picture to 720 x 480

=========================================================

Encoding audio stream to ac3 with the following command:
nice -n 0 ffmpeg -i /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E04.(704x396).[goat].avi -vn -ab 224 -ar 48000 -ac 2 -acodec ac3 -y /tmp/todisc-work/Afro.Samurai.E04.(704x396).[goat].avi.enc.0/audio.ac3

Processing started. Please wait...                                               
    ---  Encoding audio to ac3: 36 MB written to audio.ac3        

Audio encoding finished successfully.

=========================================================

Encoding video stream with the following commands:
nice -n 0 mplayer -noconsolecontrols -benchmark -nosound -noframedrop -noautosub -vo yuv4mpeg:file="/tmp/todisc-work/Afro.Samurai.E04.(704x396).[goat].avi.enc.0/video.yuv" -vf scale=720:480 "/home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E04.(704x396).[goat].avi"
cat "/tmp/todisc-work/Afro.Samurai.E04.(704x396).[goat].avi.enc.0/video.yuv" | yuvfps -r 30000:1001 -v 0 | nice -n 0 mpeg2enc --sequence-length 4300 --nonvideo-bitrate 285 --aspect 3 -f 8 -b 5880 -g 4 -G 11 -D 10 -K hi-res --frame-rate 4 -v 0 --video-norm n --reduction-4x4 2 --reduction-2x2 1 -q 7 -o "/tmp/todisc-work/Afro.Samurai.E04.(704x396).[goat].avi.enc.0/video.m2v"

Processing started. Please wait...                                               



Processing started. Please wait...                                               
    |||  Encoding video stream: 7 MB written to video.m2v        
                        deo stream: 107 MB written to video.m2v        ideo stream: 106 MB written to video.m2v        
    ---  Encoding video stream: 313 MB written to video.m2v        


=========================================================

Multiplexing audio and video together with the following command:
mplex -V -f 8 -o /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E04.(704x396).[goat].avi.enc.mpg /tmp/todisc-work/Afro.Samurai.E04.(704x396).[goat].avi.enc.0/video.m2v /tmp/todisc-work/Afro.Samurai.E04.(704x396).[goat].avi.enc.0/audio.ac3
Multiplexing finished successfully
Output files:
363M    /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E04.(704x396).[goat].avi.enc.mpg
363M    total

=========================================================

    ----------------------------------------
    Final statistics
    ----------------
    tovid 0.30
    File: /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E04.(704x396).[goat].avi.enc.mpg, 1321 secs DVD NTSC
    Final size:      371240 kilobytes
    Target bitrate:  5880 kbits/sec
    Average bitrate: 1980 kbits/sec
    Peak bitrate:    6124 kbits/sec
    Took 00:32:26 to encode on  Intel(R) Pentium(R) 4 CPU 2.40GHz 2400.945 mhz
    -----------------------------------------
Statistics written to /home/zerobinary/.tovid/stats.tovid
Cleaning up...
removed `/tmp/todisc-work/Afro.Samurai.E04.(704x396).[goat].avi.enc.0/video.yuv'

=========================================================

Do you want to keep the temporary files that were created ?
Please type "yes", or else they will be deleted

Removing temporary files...
removed `/tmp/todisc-work/Afro.Samurai.E04.(704x396).[goat].avi.enc.0/tovid.log'
removed `/tmp/todisc-work/Afro.Samurai.E04.(704x396).[goat].avi.enc.0/tovid.scratch'
removed `/tmp/todisc-work/Afro.Samurai.E04.(704x396).[goat].avi.enc.0/audio.ac3'
removed `/tmp/todisc-work/Afro.Samurai.E04.(704x396).[goat].avi.enc.0/video.m2v'
removed directory: `/tmp/todisc-work/Afro.Samurai.E04.(704x396).[goat].avi.enc.0'

=========================================================

Done!

=========================================================

Your encoded video should be in the file(s) /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E04.(704x396).[goat].avi.enc.mpg.
You can author a disc with this video on it by running:
    makexml /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E04.(704x396).[goat].avi.enc.mpg -out MyDisc
    makedvd MyDisc.xml
You can also use todisc or makemenu to create menus for your disc.
See the manual pages (i.e. 'man todisc') for more information.
Thanks for using tovid!

=========================================================


=========================================================

Converting: 
/home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E05.Finale.
(704x396)[goat].avi
--------------------------------
tovid
DVD and (S)VCD video conversion script
Version 0.30
http://www.tovid.org
--------------------------------
Using config file /home/zerobinary/.tovid/tovid.config, containing the following options:
(none)
tovid command-line used:
-ntsc -dvd -in /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E05.Finale.(704x396)[goat].avi -out /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E05.Finale.(704x396)[goat].avi.enc
Changing to working directory: /tmp/todisc-work

=========================================================

Converting /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E05.Finale.(704x396)[goat].avi to NTSC DVD format
Encoding quality is 6 of 10 (use -quality to change)
Saving to /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E05.Finale.(704x396)[goat].avi.enc.mpg
Storing log and temporary files in /tmp/todisc-work/Afro.Samurai.E05.Finale.(704x396)[goat].avi.enc.0
Run 'tail -f "/tmp/todisc-work/Afro.Samurai.E05.Finale.(704x396)[goat].avi.enc.0/tovid.log"' in another terminal to monitor the log

=========================================================

Probing video for information. This may take several minutes...
The encoding process is estimated to require 924 MB of disk space.
You currently have 4524 MB available in this directory.
Analysis of file /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E05.Finale.(704x396)[goat].avi:
  704 x 396 pixels, 30.000 fps
  Duration (best guess): 00:22:00 (HH:MM:SS)
  XVID video with mad audio
Target format:
  720 x 480 pixels, 29.970 fps
  m2v video with ac3 audio
  5880 kbits/sec video, 224 kbits/sec audio
Using auto-detected aspect ratio 177:100 (override with -aspect)
No letterboxing necessary
Input is not 29.970 fps. Framerate will be adjusted.
Scaling picture to 720 x 480

=========================================================

Encoding audio stream to ac3 with the following command:
nice -n 0 ffmpeg -i /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E05.Finale.(704x396)[goat].avi -vn -ab 224 -ar 48000 -ac 2 -acodec ac3 -y /tmp/todisc-work/Afro.Samurai.E05.Finale.(704x396)[goat].avi.enc.0/audio.ac3

Processing started. Please wait...                                               
    ---  Encoding audio to ac3: 36 MB written to audio.ac3        

Audio encoding finished successfully.

=========================================================

Encoding video stream with the following commands:
nice -n 0 mplayer -noconsolecontrols -benchmark -nosound -noframedrop -noautosub -vo yuv4mpeg:file="/tmp/todisc-work/Afro.Samurai.E05.Finale.(704x396)[goat].avi.enc.0/video.yuv" -vf scale=720:480 "/home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E05.Finale.(704x396)[goat].avi"
cat "/tmp/todisc-work/Afro.Samurai.E05.Finale.(704x396)[goat].avi.enc.0/video.yuv" | yuvfps -r 30000:1001 -v 0 | nice -n 0 mpeg2enc --sequence-length 4300 --nonvideo-bitrate 285 --aspect 3 -f 8 -b 5880 -g 4 -G 11 -D 10 -K hi-res --frame-rate 4 -v 0 --video-norm n --reduction-4x4 2 --reduction-2x2 1 -q 7 -o "/tmp/todisc-work/Afro.Samurai.E05.Finale.(704x396)[goat].avi.enc.0/video.m2v"

Processing started. Please wait...                                               



Processing started. Please wait...                                               
    ---  Encoding video stream: 332 MB written to video.m2v        


=========================================================

Multiplexing audio and video together with the following command:
mplex -V -f 8 -o /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E05.Finale.(704x396)[goat].avi.enc.mpg /tmp/todisc-work/Afro.Samurai.E05.Finale.(704x396)[goat].avi.enc.0/video.m2v /tmp/todisc-work/Afro.Samurai.E05.Finale.(704x396)[goat].avi.enc.0/audio.ac3
Multiplexing finished successfully
Output files:
383M    /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E05.Finale.(704x396)[goat].avi.enc.mpg
383M    total

=========================================================

    ----------------------------------------
    Final statistics
    ----------------
    tovid 0.30
    File: /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E05.Finale.(704x396)[goat].avi.enc.mpg, 1320 secs DVD NTSC
    Final size:      391252 kilobytes
    Target bitrate:  5880 kbits/sec
    Average bitrate: 2106 kbits/sec
    Peak bitrate:    6158 kbits/sec
    Took 00:32:54 to encode on  Intel(R) Pentium(R) 4 CPU 2.40GHz 2400.945 mhz
    -----------------------------------------
Statistics written to /home/zerobinary/.tovid/stats.tovid
Cleaning up...
removed `/tmp/todisc-work/Afro.Samurai.E05.Finale.(704x396)[goat].avi.enc.0/video.yuv'

=========================================================

Do you want to keep the temporary files that were created ?
Please type "yes", or else they will be deleted
yes

Keeping temporary files in /tmp/todisc-work/Afro.Samurai.E05.Finale.(704x396)[goat].avi.enc.0

=========================================================

Done!

=========================================================

Your encoded video should be in the file(s) /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E05.Finale.(704x396)[goat].avi.enc.mpg.
You can author a disc with this video on it by running:
    makexml /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E05.Finale.(704x396)[goat].avi.enc.mpg -out MyDisc
    makedvd MyDisc.xml
You can also use todisc or makemenu to create menus for your disc.
See the manual pages (i.e. 'man todisc') for more information.
Thanks for using tovid!

=========================================================


=========================================================

create symbolic link `1.mpg' to `/home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E01.480p[goat].avi.enc.mpg'
create symbolic link `2.mpg' to `/home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E02.(704x396).[goat]syncfixed.avi.enc.mpg'
create symbolic link `3.mpg' to `/home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E03.(704x396).[goat]syncfixed.avi.enc.mpg'
create symbolic link `4.mpg' to `/home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E04.(704x396).[goat].avi.enc.mpg'
create symbolic link `5.mpg' to `/home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E05.Finale.(704x396)[goat].avi.enc.mpg'

Getting stats on /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E01.480p[goat].avi.enc.mpg

Getting stats on /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E02.(704x396).[goat]syncfixed.avi.enc.mpg

Getting stats on /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E03.(704x396).[goat]syncfixed.avi.enc.mpg

Getting stats on /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E04.(704x396).[goat].avi.enc.mpg

Getting stats on /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E05.Finale.(704x396)[goat].avi.enc.mpg

=========================================================

Stats for /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E01.480p[goat].avi.enc.mpg 

 video codec:    MPEG2 
 video bitrate:  1723.875 kbps 
 framerate:      29.970 fps 
 audio codec:    a52 
 audio bitrate:  224.0  kbps 
 video length:   1308.073  seconds

=========================================================

Stats for /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E02.(704x396).[goat]syncfixed.avi.enc.mpg 

 video codec:    MPEG2 
 video bitrate:  1840.963 kbps 
 framerate:      29.970 fps 
 audio codec:    a52 
 audio bitrate:  224.0  kbps 
 video length:   1321.353  seconds

=========================================================

Stats for /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E03.(704x396).[goat]syncfixed.avi.enc.mpg 

 video codec:    MPEG2 
 video bitrate:  1998.151 kbps 
 framerate:      29.970 fps 
 audio codec:    a52 
 audio bitrate:  224.0  kbps 
 video length:   1320.986  seconds

=========================================================

Stats for /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E04.(704x396).[goat].avi.enc.mpg 

 video codec:    MPEG2 
 video bitrate:  1980.945 kbps 
 framerate:      29.970 fps 
 audio codec:    a52 
 audio bitrate:  224.0  kbps 
 video length:   1321.987  seconds

=========================================================

Stats for /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E05.Finale.(704x396)[goat].avi.enc.mpg 

 video codec:    MPEG2 
 video bitrate:  2106.318 kbps 
 framerate:      29.970 fps 
 audio codec:    a52 
 audio bitrate:  224.0  kbps 
 video length:   1320.319  seconds


=========================================================


Creating 599 images from each video for the main menu
Working on /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E01.480p[goat].avi.enc.mpg
Seeking in video and creating images: 000598.jpg            
Created 599 images of 599
Working on /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E02.(704x396).[goat]syncfixed.avi.enc.mpg
Seeking in video and creating images: 000598.jpg            
Created 599 images of 599
Working on /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E03.(704x396).[goat]syncfixed.avi.enc.mpg
Seeking in video and creating images: 000598.jpg            
Created 599 images of 599
Working on /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E04.(704x396).[goat].avi.enc.mpg
Seeking in video and creating images: 000598.jpg            
Created 599 images of 599
Working on /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E05.Finale.(704x396)[goat].avi.enc.mpg
Seeking in video and creating images: 000598.jpg            
Created 599 images of 599


Chapters for /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E01.480p[goat].avi.enc.mpg are: 
00:00:00.000,00:03:38.012,00:07:16.024,00:10:54.036,00:14:32.048,00:18:10.060,00:21:48.070

Chapters for /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E02.(704x396).[goat]syncfixed.avi.enc.mpg are: 
00:00:00.000,00:03:40.226,00:07:20.452,00:11:00.678,00:14:40.904,00:18:21.130,00:22:01.360

Chapters for /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E03.(704x396).[goat]syncfixed.avi.enc.mpg are: 
00:00:00.000,00:03:40.164,00:07:20.328,00:11:00.492,00:14:40.656,00:18:20.820,00:22:00.980

Chapters for /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E04.(704x396).[goat].avi.enc.mpg are: 
00:00:00.000,00:03:40.331,00:07:20.662,00:11:00.993,00:14:41.324,00:18:21.650,00:22:01.990

Chapters for /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E05.Finale.(704x396)[goat].avi.enc.mpg are: 
00:00:00.000,00:03:40.053,00:07:20.106,00:11:00.159,00:14:40.212,00:18:20.260,00:22:00.320


=========================================================

Building main menu

=========================================================


Working on 599 images from 
/home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E01.480p[go
at].avi.enc.mpg
Processing 000598.jpg                                       
Working on 599 images from 
/home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E02.(704x39
6).[goat]syncfixed.avi.enc.mpg
Processing 000598.jpg                                       
Working on 599 images from 
/home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E03.(704x39
6).[goat]syncfixed.avi.enc.mpg
Processing 000598.jpg                                       
Working on 599 images from 
/home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E04.(704x39
6).[goat].avi.enc.mpg
Processing 000598.jpg                                       
Working on 599 images from 
/home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/Afro.Samurai.E05.Finale.
(704x396)[goat].avi.enc.mpg
Processing 000598.jpg                                       
=========================================================

Making 599 final montages and compositing onto background with title

=========================================================

Processing 599.jpg                                          
Converting images to video stream and encoding to DVD-compliant format

=========================================================

Running jpeg2yuv -v 0 -f 29.970 -I p -n 599 -L 1 -b1 -j 
/tmp/todisc-work/animenu/%d.jpg | ffmpeg -f yuv4mpegpipe -i - -an -r 29.970 -s 
720x480 -tvstd ntsc -b 7000k -maxrate 8000k -bufsize 230KiB -aspect 4:3 -y 
/tmp/todisc-work/intro.m2v

Cleaning up montage images
cat: write error: Broken pipe
removed `/tmp/todisc-work/intro.wav'

Multiplexing main menu audio and video together

=========================================================


=========================================================

Running spumux /tmp/todisc-work/spumux.xml < /tmp/todisc-work/intro.mpg > 
animenu.mpg

=========================================================

Menu file animenu.mpg created
Running dvdauthor to create the DVD filesystem
DVDAuthor::dvdauthor, version 0.6.11.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: Locale=en_US.UTF-8
INFO: Converting filenames to UTF-8
INFO: dvdauthor creating VTS
STAT: Picking VTS 01

STAT: Processing animenu.mpg...
STAT: VOBU 48 at 9MB, 1 PGCS
INFO: Video pts = 0.178 .. 20.131
INFO: Audio[0] pts = 0.178 .. 20.114
INFO: Audio[32] pts = 0.178 .. 0.178
STAT: VOBU 50 at 10MB, 1 PGCS
INFO: Generating VTSM with the following video attributes:
INFO: MPEG version: mpeg2
INFO: TV standard: ntsc
INFO: Aspect ratio: 4:3
INFO: Resolution: 720x480
INFO: Audio ch 0 format: ac3/2ch, 48khz drc

STAT: Processing /home/zerobinary/todisc-work/1.mpg...
STAT: VOBU 3552 at 317MB, 5 PGCS
INFO: Video pts = 0.178 .. 1308.318
INFO: Audio[0] pts = 0.178 .. 1308.274

STAT: Processing /home/zerobinary/todisc-work/2.mpg...
WARN: attempt to update aspect ratio from 4:3 to 16:9; skipping
STAT: VOBU 7165 at 657MB, 5 PGCS
INFO: Video pts = 0.178 .. 1321.598
INFO: Audio[0] pts = 0.178 .. 1320.914

STAT: Processing /home/zerobinary/todisc-work/3.mpg...
STAT: VOBU 10766 at 1022MB, 5 PGCS
INFO: Video pts = 0.178 .. 1321.231
INFO: Audio[0] pts = 0.178 .. 1321.106

STAT: Processing /home/zerobinary/todisc-work/4.mpg...
STAT: VOBU 14366 at 1384MB, 5 PGCS
INFO: Video pts = 0.178 .. 1322.232
INFO: Audio[0] pts = 0.178 .. 1321.522

STAT: Processing /home/zerobinary/todisc-work/5.mpg...
STAT: VOBU 17952 at 1764MB, 5 PGCS
INFO: Video pts = 0.178 .. 1320.563
INFO: Audio[0] pts = 0.178 .. 1318.994
STAT: VOBU 17966 at 1766MB, 5 PGCS
INFO: Generating VTS with the following video attributes:
INFO: MPEG version: mpeg2
INFO: TV standard: ntsc
INFO: Aspect ratio: 4:3
INFO: Resolution: 720x480
INFO: Audio ch 0 format: ac3/2ch, 48khz drc

STAT: fixed 50 VOBUS                         
STAT: fixed 17966 VOBUS                         
INFO: dvdauthor creating table of contents
INFO: Scanning /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/alfo/VIDEO_TS/VTS_01_0.IFO
Cleaning up unwanted files in /home/zerobinary/todisc-work
removed directory: `/tmp/todisc-work/animenu'
removed directory: `/tmp/todisc-work/pics/0'
removed directory: `/tmp/todisc-work/pics/1'
removed directory: `/tmp/todisc-work/pics/2'
removed directory: `/tmp/todisc-work/pics/3'
removed directory: `/tmp/todisc-work/pics/4'
removed directory: `/tmp/todisc-work/pics'
Removing the link in /tmp
removed `/tmp/todisc-work'

=========================================================
todisc took 04:09:59 to finish on  Intel(R) Pentium(R) 4 CPU 2.40GHz 2400.945 mhz
=========================================================
Your new DVD should be in /home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/alfo
You can preview them in gxine with this command:
    gxine "dvd://home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/alfo"
If you are satisfied with the results, you can burn a disc with:
    makedvd -burn "/home/zerobinary/Desktop/Afro.Samurai.Ep1-5.WS.Web.Rips/alfo"

Thanks for using todisc.

Cleaning up...
Removing /home/zerobinary/todisc-work
Removing the symlink in /tmp . . .
```
then iburn the files but is not working i can't play it in my dvd player]

---

