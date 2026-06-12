---
title: "Screen Resolution"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by coltonjared on 2006-04-11
How do I get my screen set to 1024 by 768? I can only get it to 800 by 600.

---

### Post by nalmeth on 2006-04-11
In a terminal:
sudo dpkg-reconfigure xserver-xorg
go through steps and pick defaults, and add the resolution's you want when the dialogue gets there.
In the next release (Dapper Drake), the missing resolution's things seems to be fixed, but for now this is what you have to do.
EDIT:
Yes I forgot to mention to restart x, thanks beerorkid. 
BTW thanks also for hosting automatix - never seen you in the forums.

---

### Post by beerorkid on 2006-04-11
*edit* woops.  looks like nalmeth beat me to it.  His would prob be better

well you can try this:

open a terminal  applications --> accessories --> terminal

put this in there:
```
sudo gedit /etc/X11/xorg.conf

```

look for this section and add the other resolutions (like I have listed) in there

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

save

restart X (alt + crtl + backspace) then see if you can get to a higher resolution.

if 1024 X 768 is the highest you want to go, just add that.

---

### Post by coltonjared on 2006-04-11
niether of them worked

---

### Post by malcolmb on 2006-04-11
thanks nalmeth, that was a easy solution.

Getting my screen resolution up was the first thing i needed to look for on this forum.  Lucky me i found it so quickly.

---

### Post by Mustard on 2006-04-11
[QUOTE=coltonjared]niether of them worked[/QUOTE]

It might be helpful to paste the contents of your xorg.conf file in here.

You find the output with this command..

```
cat /etc/X11/xorg.conf

#prints the output of the xorg.conf file
#in the terminal
```

If you prefer a graphical text editor to view the contents try this..

```
gedit /etc/X11/xorg.conf

#I've deliberately excluded the 'sudo' command
#in the above example because its only opening the file
#for the purposes of retrieving the contents
```

---

### Post by esteban2x on 2006-04-11
I'm not sure what I did. I went through what "beerorKid" said to do and that same session, I did an automatic update and install. Whatever happened, it worked and now I have a great big screen. Thanks to all of you. Amazing group of people. I'm down in Mexico and have been passing out the free software to everyone I know. Thanks a million.

---

### Post by ignorance on 2006-04-11
Just a little question, how come i could addapt my screenresolution with the installation of an ati-driver and debian is refusing me to go any higher than 800x600?

---

### Post by beerorkid on 2006-04-12
ATI is a tricky thing in linux.

They do not cater to the small percentage of us who use linux.  It is well documented.  Nvidia does way more to help the linux community.

I see ATI as equal to apple.  I will never use either until thay recognize me as a viable user of their products.  I am special, as are all users.  Recognize me, embrace me.  Other wise flip off you bastards.  Nvidia welcoms me, and I welcome their call.

---

### Post by MOGua on 2006-04-12
This probably sounds stupid but will long term usage of "915resolution" hurt my computer?

Doesn't it write to the VBios on every boot? Wouldn't that fry it after a while?

---

