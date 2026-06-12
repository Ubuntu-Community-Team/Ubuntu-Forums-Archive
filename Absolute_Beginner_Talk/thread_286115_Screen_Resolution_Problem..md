---
title: "Screen Resolution Problem."
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by Jamesbowden on 2006-10-27
I have a Screen Resolution of 1280 x 800.

However When i Try to Switch to that from the Ubuntu Default (1024 x 768) my sceen goes all weird. can anyone help me with this.

this is what it looks like when i switch reolution to 1280 x 800 :[[IMG]http://img108.imageshack.us/img108/4328/screenshotuf4.th.png[/IMG]](http://img108.imageshack.us/my.php?image=screenshotuf4.png)

---

### Post by Henry Rayker on 2006-10-27
I have never seen anything like that. It may be risky, but have you tried allowing it to set that way and rebooting? The reason I say it may be risky is you might have to change it back with it looking this way...

What version of Ubuntu are you using? What is your video card?

Additionally, it is considered bad manners to post such a large pic rather than using a thumbnail that links to the full size...if you could change it, that'd be great...otherwise a moderator probably will, but no guarantees.

---

### Post by The Warlock on 2006-10-27
Okay, follow the following steps: 

First, open a terminal and type: 

sudo gedit /etc/X11/xorg.conf

Scroll down until you see something that looks like this:

```

	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection

```

Change it to look like this:

```

	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection

```

Save and exit gedit.

Restart X by pressing Ctrl+Alt+Backspace.

The part that pisses me off about this bug is that back in Hoary, it used to auto-detect this. Grr.

---

### Post by jd65pl on 2006-10-27
You could try reconfiguring the xserver.

Make a back up using this command
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```And then....

Use this command if you want to configure the whole of the xserver
```
sudo dpkg-reconfigure xserver-xorg
```Use this command if you want to just configure the resolution aspect
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then reboot the computer or do [ctrl+alt+backspace] to make the changes have effect.

---

### Post by Jamesbowden on 2006-10-27
The method that "the warlock" gave me worked. its all good now, thats for your help guys.

---

