---
title: "Firefox crashes with youtube"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by onemind on 2006-12-09
Hi,

I finally got sound to work with youtube and all was well. Now i get halfway through a video and firefox just closes suddenly. I thought linux programs didnt crash? :)

Anyone know why this is happening?

Thanks

---

### Post by 3rdalbum on 2006-12-09
Launch Firefox through the terminal (just open a terminal, type "firefox", don't close the terminal) and watch the video. When Firefox crashes, tell us what's in the terminal window.

Are you running Flash Player 7 or 9 beta? I recommend using the latest Version 9 beta - it shouldn't require any tweaking to get sound working on Gnome. And are you using Dapper or Edgy?

Linux programs do crash (no operating system can protect a program against its own bugs), but they never take down the whole system. Unless you use the proprietry ATI driver, that is ;-)

---

### Post by alienexplorers on 2006-12-10
I am having a similar problem in Firefox 2.0 running [www.youtube.com](www.youtube.com)...  My problem is that Firefox locks up while loading the video's.  I have tried about ten different video's and all cause the Firefox 2.0 program to lock up forcing a forced shutdown.  The only add-on I run is Tab Mix Plus.

Donnie

---

### Post by P235 on 2006-12-13
I am running Firefox 2.0 and have used both Easy Ubuntu to install flash then found [this Ubuntu forum thread]("http://www.ubuntuforums.org/showthread.php?t=315004") to install the latest linux release by Adobe.  Immediately after I followed the thread's installation procedure, websites like NBC worked quite nicely.  However, I left my browser open on a youtube video that was finished playing and walked away, later returning to a frozen PC.  After that, NBC's website behaved like it did before I installed Adobe's linux release.  Should I uninstall easy ubuntu's flashplugin-nonfree 7.0.68~ubuntu3 and libswfdec0.3?

---

### Post by P235 on 2006-12-14
The answer:  Just remove flashplugin-nonfree 7.0.68, it conflicts with the latest Linux release by Adobe.

---

### Post by towanda on 2006-12-14
How do you tell which version of flashplayer-nonfree is installed?  Will "sudo apt-get remove flashplayer-nonfree" remove all traces of it?

---

### Post by matchstich on 2006-12-14
firefox has been crashing for me also. once or twice on myspace , then on another site.  only thing i can do is reboot.

---

### Post by P235 on 2006-12-14
Since uninstalling flashplugin-nonfree I have not experienced any troubles other than the occasional, unrelated freak crash.  Run Synaptic and search for "flash," if you have flashplayer-nonfree installed it will appear there - just flashplayer-nonfree as I didn't remove my libswfdec0.3.  Don't forget to download the adobe plugin and [follow the instructions]("http://www.ubuntuforums.org/showthread.php?t=315004") of course.

---

### Post by towanda on 2006-12-16
I ran Firefox from a terminal, tried to watch a Youtube video, and got this:

towanda@my-machine:~$ firefox
/opt/firefox/run-mozilla.sh: line 131: 11212 Segmentation fault      "$prog" ${1+"$@"}

Then I uninstalled flashplayer-nonfree, went to try the same Youtube video, and Firefox asked me if I wanted to open the .swf with Totem.  So I went to [http://www.jibjab.com/originals/originals/jibjab/movieid/65](http://www.jibjab.com/originals/originals/jibjab/movieid/65) to see what would happen, and I got a white Flash screen with a green puzzle piece telling me to download the $#@%%$# plugin.

What do I have to do to get Flash 9 to work with Breezy?  I've been trying for almost three weeks now.  It's making me nuts.

---

### Post by K.Mandla on 2006-12-16
Look for the Adobe Flash 9 plugin. I believe it's still in beta, but I've been using it for months without problems.

If Firefox is crashing while you're watching Flash movies, it's possible that it's related to (of all things) your screen color depth. Try setting the color depth to 24 by editing your /etc/X11/xorg.conf file.

I was using Flash 9 with Firefox 1.5.0.7 and suffered the same crashes until I set the screen depth to 24. The problem was, it was a 300Mhz Pentium II with only 2Mb VRAM, so setting it at 24 made it crawl. In the end I dumped Flash rather than use a sluggish desktop. So if your video card can't handle it ...

---

### Post by K.Mandla on 2006-12-16
> **towanda said:**
> How do you tell which version of flashplayer-nonfree is installed?  Will "sudo apt-get remove flashplayer-nonfree" remove all traces of it?
Try

```
sudo aptitude remove --purge flashplayer-nonfree
```
That should scour your system of anything installed with flashplayer-nonfree, plus configuration files.

---

### Post by towanda on 2006-12-16
> **K.Mandla said:**
> Look for the Adobe Flash 9 plugin. I believe it's still in beta, but I've been using it for months without problems.

If Firefox is crashing while you're watching Flash movies, it's possible that it's related to (of all things) your screen color depth. Try setting the color depth to 24 by editing your /etc/X11/xorg.conf file.

I was using Flash 9 with Firefox 1.5.0.7 and suffered the same crashes until I set the screen depth to 24. The problem was, it was a 300Mhz Pentium II with only 2Mb VRAM, so setting it at 24 made it crawl. In the end I dumped Flash rather than use a sluggish desktop. So if your video card can't handle it ...

The video card in this computer is old, but still seems pretty speedy.  This machine also has three-quarters of a gig of RAM and an 800-mHz AMD Duron processor with two hard drives, one with Windows 2K Pro and one with Ubuntu.  Flash and other kinds of video work fine on the Windows drive, and non-Flash video works pretty well on the Ubuntu drive, so I'm not sure that the video card is the problem.  Youtube did start crashing or freezing Firefox on the Ubuntu drive after I went to Flash 9, though.

I'll try your code for removing flashplugin-nonfree and I'll try installing Flash 9 again.  Thanks!

I think the color depth is already set to 24.  Here's the entire Screen section of my xorg.conf:
> Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Monitor		"DELL 1800FP"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection


---

### Post by towanda on 2006-12-16
I removed flashplayer-nonfree.  Then I went back to jibjab.com and clicked on the puzzle piece to download the plugin.  Firefox installed something that it said was Flash.  Now I have sound but no picture.

](*,)

---

### Post by P235 on 2006-12-17
[Adobe Flash Ubuntu Forum Thread]("http://www.ubuntuforums.org/showthread.php?t=315004")

Read post #3

---

