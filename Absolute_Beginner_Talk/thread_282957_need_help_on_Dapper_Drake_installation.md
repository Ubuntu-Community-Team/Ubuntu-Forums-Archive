---
title: "need help on Dapper Drake installation"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by epapalexis on 2006-10-23
I have recently installed Dapper Drake on a Sony Vaio VGN-B1XP. It works OK but I would like to have 1400x1050 screen analysis and hear the sound. What must I do to make it possible? I am a beginner at Linux... any help would be appreciated

---

### Post by hellblade on 2006-10-23
Unfortunately I can't help you very much because I have no idea about your laptop specs... but I will try.

To enable the resolution you want, you must put it in '/etc/X11/xorg.conf' file, under the screen section. It should look something like that:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Default Device"
	Monitor		"Default Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1400x1050" "1440x900" "1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050" "1440x900" "1280x800" "1024x768" "800x600"
	EndSubSection
EndSection
```
Notice that 1400x1050 is the first resolution in these lines so that it gets selected by default.
Also it might be better to tell us which graphic chip you have so that you can install a better driver if available.

To see if your soundcard is supported by ALSA (the sound system) we need to know its model, first. Try this command in a terminal:
```
$ lspci | grep audio
```
and paste here the results. If nothing appear try the following two commands and paste all the output here.
```
$ lspci
$ lsusb
```

PS. It would be better to start two different topics as these are two different problems/subjects.

---

### Post by grim918 on 2006-10-23
Here is a link to a thread dealing with screen resolutions:[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

Ubuntu should have sound working by default. You should double check and make sure that your speakers are connected and turned on and that your sound volume is turned up on them and on your ubuntu box. Posting infomation about your sound card might help a more experienced user figure out your problem.

---

### Post by spacegypsy on 2006-10-23
Did you installed the latest driver?
ATI I think?

Some links that helped me out;
[http://ubuntuforums.org/showthread.php?t=271775](http://ubuntuforums.org/showthread.php?t=271775)

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

Hopefully it will help you to.

---

