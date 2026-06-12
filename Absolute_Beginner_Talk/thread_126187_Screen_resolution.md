---
title: "Screen resolution"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by RKF on 2006-02-05
have Benq lcd screen

Currently the linux setting is 1024 x760 or thereabout and it is killing my eyes.

The Screen resolution dropdown doesn't allow me to set it to native resolution of 1280x1024. 

Did a search and did see 'amend etc/ whatever??.  found the page but could not edit it; there were multiple entries to be edited.  Also went into terminal but it wouldn't access the page.

cheers 

RKF

---

### Post by jimrz on 2006-02-05
from the terminal use 'sudo gedit <whatever>' then enter, it will ask for your password, use your regular login pw, you will not see any characters when typing pw but it is there, then  enter, proceed with text editor. I would recommend baking up your original file before editing (ex; 'sudo cp <whatever> <whatever_original>'

---

### Post by RKF on 2006-02-06
Well that was a "did not work"

managed the edit and save Ok but did nothing for the screen and the "resolution"drop down still doesn't have 1280x1024 to select from??  next!

'ELP

RKF

---

### Post by GreyFox503 on 2006-02-06
Try these instructions:

[https://wiki.ubuntu.com/FixVideoResolutionHowto](https://wiki.ubuntu.com/FixVideoResolutionHowto)

---

### Post by RKF on 2006-02-06
Ok guys got this licked.

Crashed the bloody thing after trying the previous message, had to reload yet again.

Got to the screen resolution screen which is full of gobblygook. Who writes this stuff? 

Too many negatives and contradictory statements in the instructions. Also it wouldn't hurt to insert an instruction that one has to use the bloody space bar not the return/enter to insert the selection. 

It is as bad as Franglais or Chinglish.

This sort of thing is not bleeding obvious. 

For whomever - used to be technical and regulatory writer/draftman in the aviation industry. If my/our instructions and "help" were this bad none of you would want to get on an airplane because of all of the holes in the ground.

How about a prime moving "honcho" to discuss.

Cheers

RKF

---

### Post by d4rk on 2006-02-06
It doesn\t work for me, so i guess ill just have to live with that damn resolution for the rest of my time usin linux. Same with mp3 files, guess Ill might as well drop that too.

---

### Post by Perfect Storm on 2006-02-06
First:
```
sudo gedit /etc/X11/xorg.conf
```
Change the **HorizSync** and **VertRefresh**. You'll find the number in your monitor manual.

reboot.  

Second: If that doesn't help, try with:
```
sudo dpkg-reconfigure xserver-xorg
```

reboot.

Third: 
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by d4rk on 2006-02-06
[QUOTE=Artificial Intelligence]First:
```
sudo gedit /etc/X11/xorg.conf
```
Change the **HorizSync** and **VertRefresh**. You'll find the number in your monitor manual.

reboot.  

Second: If that doesn't help, try with:
```
sudo dpkg-reconfigure xserver-xorg
```

reboot.

Third: 
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)[/QUOTE]

Nothing of this works for me :(     But in the xorg.confi file I open in the first method, below where I write in those values it is this :
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
EndSubSection
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
And it goes on with several of this. So now I'll try changing this values...:-k 
Before I start, is that safe ?

---

### Post by RKF on 2006-02-06
Didn't work for me - and System died!

Re-loaded and that is where I found instructions for the xserver xorg bit for the screen resolution were badly worded and crappy. It was at the time, fleeting as I brought my finger down on the Enter key

All loaded booted and fine but with a crookscreen again. Then lost it all again; ie System crashed in big heaps when following geeky instructions from the website above.  

Last time re-loaded, when I got to the boot screen which asked for the screen resolution I was extremely careful to not touch the "Enter"  key. Real trick is to find the right key to insert one's choice of resolution.  

Use the up down arrows to move (as one would expect). Use the "space" bar to insert the screen resolutions marker/asterix that you want to use.  

Be helpful if this was actually annotated.

Long way round but it does work.

RKF

---

### Post by d4rk on 2006-02-07
So what u r saying is that i can change from these nubers i showed in the upper post ? Or is that what will crash my system ?..

---

### Post by infoseeker on 2006-02-07
I have this in my '/etc/X11/xorg.conf'  file :

> SubSection "Display"
	Depth		24
	Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection

---

### Post by GreyFox503 on 2006-02-07
If you're making a change to your xorg.conf file (or running a command like "dpkg-reconfigure xserver-xorg"), then you can make a backup file in case you don't like the changes.

To create backup:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
``` 
If something goes wrong, to restore backup:

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

---

