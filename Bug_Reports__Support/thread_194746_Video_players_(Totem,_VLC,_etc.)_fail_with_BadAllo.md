---
title: "Video players (Totem, VLC, etc.) fail with BadAlloc error"
date: 2006-06-11
forum: Bug Reports / Support
---

### Post by Baddox on 2006-06-11
When I try to play a video with totem, vlc, mplayer, etc. the command line shows a consistent error.
For totem:
```
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 86 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```
For vlc:
```
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  83
  Current serial number in output stream:  84
```

It's clearly a problem with the actual displaying of video, because vlc does not crash until a video file is loaded (it will play mp3's, ogg's, etc. fine).  Also, I have uninstalled and reinstalled the video players, so I know the programs themselves are not the issue.

I've scoured forums like crazy, and several people have posted these errors, but with no successful results.  It's not just an Ubuntu thing, because people on Fedora forums have posted the same problem.  Most people indicate a likely xorg.conf problem, although I can't pin down what it could be.  I'm using a Dell 2005fpw monitor with resolution of 1680x1050, which required some tweaking in xorg.conf, but everything worked great in Ubuntu 5.10, which I just got rid of in lieu of 6.06 (I didn't actually upgrade, I just formatted and installed 6.06).  This is *extremely* frustrating, if anyone has any clue what's going on, I would definitely appreciate it.

---

### Post by cskeide on 2006-06-11
I get the same error when trying to play high resolution videos. For example, I made a 'screencast' with ffmpeg in 1024x768 resoulution which I can't play with any video player. Can you play low resolution videos, or does this happen regardless of resolution?

---

### Post by Baddox on 2006-06-11
I believe the problem occurs with all videos.  Even a video from zefrank.com/theshow, which are something like 230x170, cause the error to occur.  More info:  I installed the MPlayer firefox plugin, and once it's buffered, it will attempt to start playing, show a completely blue frame for less than a second, then simply stop.

---

### Post by Baddox on 2006-06-11
Well, as always, Linux has made me feel like an idiot :-).  On a whim, I decided to install [Automatix]("http://www.ubuntuforums.org/showthread.php?t=177646") and have it reinstall the nvidia drivers for me.  Somehow or another, everything's fine now.  I don't even know exactly what the problem was or what fixed it, which is the worst part.

---

### Post by cskeide on 2006-06-15
Thought I'd post my solution to this error. I'm using the i810 graphics driver, and my video card uses shared memory, which seems to be causing the error. My problem was that all movie players crashed when playing any video with a resolution higher than 640x480. After adding two lines to my xorg.conf file, I can finally play my 1024x768 screencasts.

I added these lines to Section "Device" in xorg.conf:
```

        Option  "VideoRam"      "65536"
        Option  "CacheLines"    "1980"

```

Related to [bug #4229]("https://launchpad.net/distros/ubuntu/+source/totem/+bug/4229")

---

### Post by jackn on 2006-06-17
Thanks a lot, cskeide.

I've tried this solution, but it won't save the changes (read-only, it says).

I'm also not sure I'm in the right place in the file, as the word 'device' appears several times. I tried to append the suggested lines to a section called 'device section' only, while in other cotexts, it said other things as well, such as 'input device'.

Thanx,
Jackn

---

### Post by cskeide on 2006-06-18
[QUOTE=hroit]Thanks a lot, cskeide.

I've tried this solution, but it won't save the changes (read-only, it says).

I'm also not sure I'm in the right place in the file, as the word 'device' appears several times. I tried to append the suggested lines to a section called 'device section' only, while in other cotexts, it said other things as well, such as 'input device'.

Thanx,
Jackn[/QUOTE]

You have to use sudo in order to edit the file:```
sudo gedit /etc/X11/xorg.conf
```

Add the lines to Section "Device"... Mine looks like this:```
Section "Device"
        Identifier      "Intel Corporation 82852/855GM Integrated Graphics Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option  "VideoRam"      "65536"
        Option  "CacheLines"    "1980"
EndSection

```

EDIT: To avoid further misunderstandings; this solution is **hardware specific**! It works on my system, which has an Intel Integrated Graphics Device with 64Mb of shared memory and using the i810 driver.

---

### Post by jackn on 2006-06-19
Applied above change to xorg.conf. Used also two other values for the  'VideoRam' line, mentioned in the above bug #4229 link.

To no avail. Changing the screen resolution to 640 x 480 (from 1024 x 728) was of no help either.

So Totem still doesn't work in my hands... It says it doesn't 'have the plugin' for 'this file' (a DVD)...

---

### Post by cskeide on 2006-06-20
hroit: I am sorry that my solution didn't work for your setup. However, it seems like you are applying my solution to a totally different problem. The error my system gave me was:```
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 86 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

Now, a missing plugin for DVD playback, as you say is your problem, has nothing in common with the original issue in this thread.

As a possible solution to your problem, I would suggest the following:
1. Make sure you have enabled the necessary repositories (Read [How to add extra repositories]("http://doc.gwos.org/index.php/DapperGuide#How_to_add_extra_repositories"))
2. Open up a terminal (Applications -> Accessories -> Terminal) and install libdvdcss2:```
sudo apt-get update
sudo apt-get install libdvdcss2
```

Hope this helps

---

### Post by jackn on 2006-06-21
[QUOTE=cskeide]However, it seems like you are applying my solution to a totally different problem. The error my system gave me was:```

The error was 'BadAlloc (insufficient resources for operation)'.
  
```

Now, a missing plugin for DVD playback, as you say is your problem, has nothing in common with the original issue in this thread.
[/QUOTE]

Have followed both of the above suggestions, the library and 'apt-get update'. The library had already been installed, and the update only fetched negligible stuff.

I still get an error message. Still working on it...

---

### Post by jackn on 2006-06-22
[QUOTE=cskeide]Thought I'd post my solution to this error. I'm using the i810 graphics driver, and my video card uses shared memory, which seems to be causing the error. My problem was that all movie players crashed when playing any video with a resolution higher than 640x480. After adding two lines to my xorg.conf file, I can finally play my 1024x768 screencasts.

I added these lines to Section "Device" in xorg.conf:
```

        Option  "VideoRam"      "65536"
        Option  "CacheLines"    "1980"

```

Related to [bug #4229]("https://launchpad.net/distros/ubuntu/+source/totem/+bug/4229")[/QUOTE]

cskeide, quite sure personally that you're right as to the reason for the BadAlloc error - the name suggests it, the bug report you refer to explains it, I've seen at least one other place with this problem and a similar analysis. Finally, I do have a shared memory, rather weak, graphics card, and, when in Windows, I'm asked to change the screen resolution in order to play DVD's. The whole picture is also consistent with some people only having the problem, probably due to hardware differences.

---

### Post by jackn on 2006-06-22
Sorry, cskeide, my bad.

It is still BadAlloc, now too. 

It's only that 'missing plugin' is what the GUI (or doing totem AND  the filename from terminal) tells you, whereas 'BadAlloc' is what the terminal says (upon doing just 'totem'). 

Forgot that the error message came from following stuff on the terminal. Sincere apologies.

Jackn

---

