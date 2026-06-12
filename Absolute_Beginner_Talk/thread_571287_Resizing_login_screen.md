---
title: "Resizing login screen?"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by Tranquilo on 2007-10-09
Hello folks!
I switched to a new screen and for some reason the login screen no longer "fits" the screen.
I can see the box for typing loginname and password, but not much else.
So how do I resize the loginscreen?

---

### Post by jdavis on 2007-10-09
I have found in the past that using the auto-detect on my monitor has sometimes resolved this issue. If not then you may have to resort to editing the xorg.conf file.

Found a few related topics that may help:
[http://ubuntuforums.org/showthread.php?t=322768](http://ubuntuforums.org/showthread.php?t=322768)
[http://ubuntuforums.org/showthread.php?t=487878](http://ubuntuforums.org/showthread.php?t=487878)

Jonathan

---

### Post by Tranquilo on 2007-10-09
Thanks for the response!
Tried the auto-detect on my monitor - no luck
Tried mucking about with the xorg.conf file using the tips in the threads you posted - didn't seem to make any difference.
Then I tried using the: sudo dpkg-reconfigure -phigh xserver-xorg command from the conf file itself. That made login screen look good, but my screen resolutionwas stuck on 800x600....
So I reverted to my former xorg.conf.
This is what the xorg.conf looks like at the moment:
Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. ATI Default Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "800x600" "640x480"
	EndSubSection
EndSection

Any other thoughts?

---

### Post by jdavis on 2007-10-09
What screen res do you want to use for your main desktop?

During the reconfigure command you could try and select only the screen resolution you wish to use, and deselect any other resolutions.

---

### Post by Tranquilo on 2007-10-11
Hmmm. Strange. Tried your suggestion and it still defaults to 800x600. Even if i remove that as an option...And I don't have as many options for resolution in the system tray afterwards. If I then revert to the former xorg.conf I get my options back but wrong size login screen again.
What I don't get is why manually editing the xorg.conf didn't change the resolution? And why is the login screen resolution different from the main one?

---

