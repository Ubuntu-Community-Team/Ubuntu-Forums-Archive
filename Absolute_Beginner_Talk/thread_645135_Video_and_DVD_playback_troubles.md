---
title: "Video and DVD playback troubles"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by SlyReaper on 2007-12-19
OK, I'm running Gutsy Gibbon and have intalled the ubuntu-restricted-extras package and can *sort of* get some of my video files playing.  Some play without a problem, others just close the player without an error message or anything.  Seems to be the ones which have a high resolution.  Any fixes for this?

Also, I can't seem to get DVDs to play.  The totem player comes up and tells me it "Could not read from resource".  Any advice?

---

### Post by RomeReactor on 2007-12-19
Hi. What video player are you having trouble with? try launching it from the terminal (Applications->Accessories->Terminal); if it's Totem:
```
totem
```
Mplayer:
```
gmplayer
```
Then use the player's menu to open one of the problematic files, and if it crashes see if there's a crash output left in the terminal; if so, please post it here.

As for DVDs, try switching to Totem-Xine:
```
sudo apt-get install totem-xine libxine1 libxine1-gnome libxine1-ffmpeg libxine1-plugins
```
ad try the DVDs again.

---

### Post by stchman on 2007-12-19
> **SlyReaper said:**
> OK, I'm running Gutsy Gibbon and have intalled the ubuntu-restricted-extras package and can *sort of* get some of my video files playing.  Some play without a problem, others just close the player without an error message or anything.  Seems to be the ones which have a high resolution.  Any fixes for this?

Also, I can't seem to get DVDs to play.  The totem player comes up and tells me it "Could not read from resource".  Any advice?

I have a tutorial that will get all your media playing right.

Install proprietary codecs
[http://www.stchman.com/codecs.html](http://www.stchman.com/codecs.html)

Watch encrypted DVDs
[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

Rip CDs
[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

---

### Post by SlyReaper on 2007-12-19
OK, thanks for the advice guys - I can now play DVDs.  However, I still have a few video files on my hard drive that close the player as soon as they're launched:

tom@Toms-laptop:~/misc$ totem x.wmvThe program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 82 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

"Insufficient resources for operation" confuses me, because I know these files work perfectly well when I run WinXP on the same machine.  That video has a resolution of 1920x1080 by the way, and video files that I have at quite small resolutions work fine.

---

### Post by RomeReactor on 2007-12-19
That's [a bug]("https://bugs.launchpad.net/ubuntu/+source/gst-plugins-base0.10/+bug/39050") that's been going on for some time. Try opening your xorg.conf in Gedit:
```
gksudo gedit /etc/X11/xorg.conf
```
Scroll down to **Section "Device"** and add the following line:
```
Option "LinearAlloc" "8160"
```
Save the file and close Gedit, then press CTRL+ALT+BACKSPACE to restart the display. Then try the videos again.

---

### Post by SlyReaper on 2007-12-19
Alright!  I'm slowly getting there.  The video plays now, but with problems.  In totem, the sound keeps cutting out.  In VLC, the sound is fine, but the video is extremely choppy and freezes in several places.  Is that as good as it's going to get?

---

### Post by philinux on 2007-12-19
Check out the multimedia link below.

---

### Post by SlyReaper on 2007-12-19
Actually, never mind.  My other high-res videos all seem to be playing perfectly well, so it may well be that one file I was testing with being corrupt.  Thanks for all the help, guys! :)

---

### Post by Dive4Life on 2007-12-20
I have just rented two new DVD's and they are not playing on my machine.  Older DVD's work fine.  Is there a new encryption being put on the new recently released titles?  If so how do you get them to play on Ubuntu?

---

### Post by Dive4Life on 2007-12-20
I just did an update of my packages and now the movies are playing fine.  Guess a little common sense goes a long way.  Thanks in advance.

---

