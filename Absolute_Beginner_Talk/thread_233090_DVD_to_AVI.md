---
title: "DVD to AVI"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by doomstone on 2006-08-09
Dose any have have a good guide how-to rip a dvd to avi divx/xvid on linux?

---

### Post by John.Michael.Kane on 2006-08-09
This may help
[**[COLOR="Red"]acidrip[/COLOR]**]("http://sourceforge.net/projects/acidrip/")
[**[COLOR="Blue"]AcidRip_Simple.html[/COLOR]**]("http://www.togaware.com/linux/survivor/AcidRip_Simple.html")

---

### Post by kebes on 2006-08-09
Not a guide really, but here is a short list of programs I've used when working with DVD and video on Linux.

mplex       -- Command-line utility that combines multiple audio and video streams into an mpeg file.
dvdauthor   -- Command-line utility that makes a DVD filesystem from mpeg files.
growisofs   -- Command-line CD/DVD burning utility.
tovid       -- A collection of command-line scripts that automate detection of video type and transcoding to mpeg format.

avidemux2   -- GUI for extracting audio and video.
DVD::rip    -- GUI for ripping, copying, burning DVDs.
K3B         -- KDE GUI for CD/DVD burning.

Various other programs (mpeg2desc, transcode, etc.) will probably be installed when you install the above software components.

For a rough idea of what a script using the above tools might look like, see:
[http://www.mythtv.org/docs/mythtv-HOWTO-23.html#ss23.19](http://www.mythtv.org/docs/mythtv-HOWTO-23.html#ss23.19)
[http://www.mythtv.org/wiki/index.php/Archiving_Recordings_to_DVD](http://www.mythtv.org/wiki/index.php/Archiving_Recordings_to_DVD)
(These are geared towards working with MythTV files, of course, but much of it would apply to your situation.)

---

