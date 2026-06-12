---
title: "unexpected log out"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by olivine on 2007-09-09
Hello. I just installed Feisty on a new PC. Once in a while when using mozilla (when clicking on a link, making a new tab or scrolling with the middle mouse button) the screen flashes and the system logs me out. 

This thread
[http://ubuntuforums.org/showthread.php?t=138089]("http://ubuntuforums.org/showthread.php?t=138089")
 deals with something similar. I do have Xgl installed by default, but following the advice on the thread doesn't change anything. 

Any ideas about the problem?

---

### Post by Hossie on 2007-09-09
This is probably not a "logout", but a crash of your X-Server. Did you look into /var/log/Xorg.0.log after that happened?

&#8364;: Im not quite sure if the logfile for Xgl is the same, but I think if you "ls /var/log", you'll find it.

---

### Post by olivine on 2007-09-09
It's a pretty huge file. There are various initialization successes and failures. What should I look for in there? 

I am not able to upload here (invalid file).

---

### Post by Hossie on 2007-09-09
Most of the file is output of the startup, the crash is probably only the last few lines of the file.

---

### Post by olivine on 2007-09-09
Alright. The end of the file doesn't seem *too* weird to the newbie I am:

**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!

...BUT on the other hand, the file Xorg.0.log.old has the same stuff, followed by:

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x6d) [0x48282d]
1: /lib/libc.so.6 [0x2ba9a86d4d40]
2: /lib/libc.so.6(cfree+0x3b) [0x2ba9a871721b]
3: /usr/lib/xorg/modules/extensions//libGLcore.so [0x2ba9ac07ed75]
4: /usr/lib/xorg/modules/extensions//libglx.so(__glXResetScreens+0x3a) [0x2ba9a9fb6afa]
5: /usr/X11R6/bin/X(CloseDownExtensions+0x35) [0x45a755]
6: /usr/X11R6/bin/X(main+0x47a) [0x43705a]
7: /lib/libc.so.6(__libc_start_main+0xf4) [0x2ba9a86c18e4]
8: /usr/X11R6/bin/X(FontFileCompleteXLFD+0x241) [0x436339]

Fatal server error:
Caught signal 11.  Server aborting

---

### Post by olivine on 2007-09-10
Bump. Thanks, Hossie, for your help so far.

Any chance someone has an idea about where to go from here?

---

### Post by tvrg on 2007-09-10
how about disabling desktop effects?

I suppose you've been messing with compiz/beryl/whatever on feisty, which is known not to work with some hardware or software combinations.

What links are you clicking on? containing movies? flash ads?...

---

### Post by olivine on 2007-09-10
I didn't install anything special; no beryl, no anything, just the default installation from feisty 64 bit alternate CD. I didn't think there'd be any desktop effects by default, and nothing happens when I click on the desktop effect preferences panel; but now I realize the first time it crashed there were some kind of new sound effects when I logged back in (I turned off the sound after that), so maybe you're right and it's got something to do with that.

Pretty much the only other things I installed were a couple of plugins for mozilla; flash etc., and the 'no script' add on. I'm not sure but it's possible it's always crashing when there are flash scripts (pages like espn.com).

I'll test the system after removing plugins, 'effect' packages and all the compiz stuff (not sure why it should be a problem if it's part of the default installation) and hopefully things get cleaned up a bit. :-?

---

