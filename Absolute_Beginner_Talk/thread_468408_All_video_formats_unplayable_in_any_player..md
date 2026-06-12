---
title: "All video formats unplayable in any player."
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by SemtexRS on 2007-06-08
I installed everything i needed to play various media formats (libdvdcss2, w32codecs, libdvdread, libdvdnav, xine-ui, totem-xine) and now all video files are completely unplayable.  I have tried playing MPEG4, OGG, and a DVD in VLC, totem, xine, and mplayer, and in every player all the media formats will just close the window.  If i open and close the disc drive the DVD will autoplay and totem will start playing the audio for a second and then close.  I have no idea why this is happening, because in edgy all i had to to was install totem-xine and the codecs and everything would work.  Any ideas why this is happening?

---

### Post by dannystaple on 2007-06-08
Restricted codecs perhaps? I recommend having a look at this item on the Feisty ubuntu guide - [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs)

Cheers,
Danny

---

### Post by SemtexRS on 2007-06-08
Nope, I followed that whole guide and it's still doing the same thing.  It doesn't seem to be a problem with the codecs, but rather the player being able to use them properly, because it sometimes will play the first second of audio on the disc before closing.

EDIT: Definitely not the codecs.  I tried a different disc and for some reason this one played about half of the advertisements before it quit.

---

### Post by RomeReactor on 2007-06-08
Hi. Try opening the players from the terminal, open a video and see if they leave any crash output there. It might be of help to figure this issue out. Also, do you have Beryl running?

---

### Post by SemtexRS on 2007-06-08
Yeah, I am using Beryl, so i tried without it and it worked.

The error output i get from totem is:

```
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 131 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

EDIT:  Found the VLC workaround on the forums.  Thanks for all the help!

---

### Post by Thangarajerode on 2007-06-09
Dear All

We have download the ubuntu 7.0.4 Linux OS from below path.

[http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=i386&mirror=&debug=%5B%27country_US%27%2C+%27country_UK%27%2C+%27continent_NA%27%5D&download-button=%3CIMG+alt%3Ddownload+src%3D%22%2Fthemes%2Fubuntu07%2Fimages%2Fbutton-download-new.png%22%3E+Start+Download](http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=i386&mirror=&debug=%5B%27country_US%27%2C+%27country_UK%27%2C+%27continent_NA%27%5D&download-button=%3CIMG+alt%3Ddownload+src%3D%22%2Fthemes%2Fubuntu07%2Fimages%2Fbutton-download-new.png%22%3E+Start+Download)



After installation the OS.
We cannot play the video format and MP3,DVD format.

So we need the help.

1.Where to download the Video players(xine or Mplayer)
2. How to install the same

Since we are new to linux please help us in step by step procedure for downloading and installing the same.


regds
D.Thjangaraj

---

### Post by RomeReactor on 2007-06-09
Hi Thangarajerode. What programs have you tried to listen mp3 files in: Totem, Rhythmbox? In Rhythmbox, you need to install **gstreamer0.10-plugins-ugly**; search for it in Synaptic (System-->Administration-->Synaptic Package Manager). Or to install from the terminal (Applications-->Accessories-->Terminal):
```
sudo apt-get install gstreamer0.10-plugins-ugly
```
Just copy and paste the previous command there and press enter. Rhythmbox and Totem (Movie Player) should then be able to play them. Post back if you're having problems with it. For DVD playback see [this link]("http://ubuntuforums.org/showpost.php?p=2727375&postcount=3").

---

### Post by No Whammies on 2007-06-11
So, what IS the vlc workaround?

> **SemtexRS said:**
> Yeah, I am using Beryl, so i tried without it and it worked.

The error output i get from totem is:

```
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 131 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

EDIT:  Found the VLC workaround on the forums.  Thanks for all the help!

---

### Post by bone43 on 2007-06-11
> **RomeReactor said:**
> Hi Thangarajerode. What programs have you tried to listen mp3 files in: Totem, Rhythmbox? In Rhythmbox, you need to install **gstreamer0.10-plugins-ugly**; search for it in Synaptic (System-->Administration-->Synaptic Package Manager). Or to install from the terminal (Applications-->Accessories-->Terminal):
```
sudo apt-get install gstreamer0.10-plugins-ugly
```
Just copy and paste the previous command there and press enter. Rhythmbox and Totem (Movie Player) should then be able to play them. Post back if you're having problems with it. For DVD playback see [this link]("http://ubuntuforums.org/showpost.php?p=2727375&postcount=3").


Thanks!!!!

Wow after messing around forever DVD is working perfect! :D

---

### Post by pavan_bitsgoa on 2007-06-16
hei can some one help me out
i have the same plroblem ie vieo/audio plays fr just 3 to 4 sseconds before the application crashes
i tried the code given above and it gives

sudo apt-get install gstreamer0.10-plugins-ugly
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-plugins-ugly is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

so pls help me out
thanks

---

### Post by RomeReactor on 2007-06-17
Hi pavan. What format is the video you're trying to play (wmv, mpg, avi, etc.), and with what application? You can try opening the app from the terminal (Applications-->Accessories-->Terminal) so it leaves a message there about the crash:
```
totem
```
If you're using Totem; otherwise, try entering **mplayer**, **vlc**, **gxine**, and opening the file from the program's menu, and see if it leaves any messages on the terminal, and post that here.

Sorry for the late reply.

---

### Post by pavan_bitsgoa on 2007-06-17
i dried  every format ie specifcally .wav  .mp4  .avi. .mpeg .flv .bin 

i tried running them in mplayer, vlc, realplayer10,xmms,xine  (im usin ubuntu7.04)

only the first second infact only a flash of the screen that is playin that file appears but later a black screen appears in taht place (if i nun the application in full screen the entire screen is black)

the terminal message when i open .avi file through vlc in terminal
VLC media player 0.8.6 Janus
[00000287] main playlist: stopping playback

i closed the file as i couldnt c the video (only black screen) after the 1st second (audio is normal and has no problems)
also when i minimize or maximise i can c the video bein played (only the current frame) ie fr abt 1 sec after that again it goes back to black screen

hope this helps
thank you

---

### Post by RomeReactor on 2007-06-18
Do you have Beryl? and is it running while you try to watch a video? If so, then [this thread]("http://ubuntuforums.org/showthread.php?t=459020") might help.

---

