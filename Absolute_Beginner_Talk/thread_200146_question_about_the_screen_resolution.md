---
title: "question about the screen resolution"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by Somenoob on 2006-06-19
I'm using the "fglrx" driver.

I did the "sudo dpkg-reconfigure xserver-xorg" configuration, but i did not see anything about resolutions.

But 1024 x 786 is the maxium resolution, why can't i go above that?

any help is deeply appreciated.

---

### Post by xXx 0wn3d xXx on 2006-06-19
Here is how to fix the screen res problem.

> sudo dpkg-reconfigure xserver-xorg

Then procede to answer the questions, it will basically pick the best things. When you get to the part that says "What resolutions would you like X to use ?" Uncheck the 3 at the bottom (using the space bar) and put a * in the box of the resolution that you want to use. Only select the one that you are going to use.

---

### Post by Somenoob on 2006-06-19
thank you.

---

### Post by Somenoob on 2006-06-19
Final question: where exactly is that part?

---

### Post by xXx 0wn3d xXx on 2006-06-19
[QUOTE=Somenoob]Final question: where exactly is that part?[/QUOTE]
Terminal aka: "Command line." (Applications > Accessories > Terminal)

---

### Post by Somenoob on 2006-06-20
The configuring process crashed at the monitor auto detection, i just saw a command line interference the same kind when booting up, it was obviously frozen.

Are there any other ways to change your resolution?

please help, i find this 1024x768 res to be quite annoying.

---

### Post by siccness on 2006-06-20
The other option to change resolutions is to actually manually edit xorg.conf file.

First make up backup copy:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.backupconf


Use this to edit the conf file [gedit] is a editing program.
sudo gedit /etc/X11/xorg.conf


Here's an example of what mine looks like:
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection

If you need to go back to the old configuration file (say something went wrong), type:
sudo mv /etc/X11/xorg.backupconf /etc/X11/xorg.conf

---

### Post by Somenoob on 2006-06-20
[QUOTE=siccness]The other option to change resolutions is to actually manually edit xorg.conf file.

First make up backup copy:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.backupconf


Use this to edit the conf file [gedit] is a editing program.
sudo gedit /etc/X11/xorg.conf[/QUOTE]

thanks, i would like "1280x1024" but where do i add that line?

should this then be present in "system > preferences > Screen resolution"?

---

### Post by siccness on 2006-06-20
You could use gtf to produce your mode line, which I think is better:

type this: (75 is the  example refresh rate):
gtf 1280 1024 75


It should produce something like this:
Modeline "1280x1024_75.00"  138.54  1280 1368 1504 1728  1024 1025 1028 1069 -HSync +Vsync


And then put that under the "Monitor" Section
Hang on, to make this easier I'll throw up an example xorg.conf file.

---

### Post by siccness on 2006-06-20
[QUOTE=Somenoob]
should this then be present in "system > preferences > Screen resolution"?[/QUOTE]

Yeah, although I *THINK* you have to restart X by: CTRL+ALT+BACKSPACE

---

### Post by Somenoob on 2006-06-20
I added this line in the monitor section, from the "gtf 1280 1024 75" command.

```
Modeline "1280x1024_75.00" 138.54 1280 1368 1504 1728 1024 1025 1028 1069 -HSync +Vsync
```

And i added "1280x1024 in the screen section, in all Depths.

Then i restarted the Xserver, and the changes are not in 

 "system > preferences > Screen resolution"

I rebooted the system and still no changes.

any suggestions?

---

### Post by Somenoob on 2006-06-20
are there any other method(s) of changing the resolution?

---

