---
title: "screen resolution problem"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by uk_sphinx on 2006-10-01
hello,
i installed ubuntu recently with no probs whatsoever.
i was running the screen resolution at 1200 x 768 (cant remember the exact number but that is pretty close).

i usually dont turn my comp off but i have left it off for about 2 days.
since i have turned it back on the display has changed to 640 x 480.
when i try to change it from the option it wont list any options.
i never asked it to change to this resolution and it seems to have done it itself.

does anyone know what the problem is or how i can change it back?

i have a ati radeon 9550 if thats any help.
i havnt installed the driver for it because it was running fine on the one ubuntu defaulted to it.(maybe ubuntu installed the right one i dont know how to check).
i dont use the 3d on it for any progs so i didnt really need to install the catalyst drivers i guessed.
i only wont to use the comp for programming python but theres too much scrolling in 640 x 480.

---

### Post by bigken on 2006-10-01
try this in a terminal sudo dpkg-reconfigure xsever-xorg use the space bar to select your screen sizes when you have finished reboot ;)

---

### Post by Fass on 2006-10-01
nm

---

### Post by uk_sphinx on 2006-10-01
it says x server org is not installed.
what is x server org?
shall i install it from the terminal.
i have enabled all the repositories.or do i need to manualy install from website?


p.s  is that pic of yours the wolf guy from ffx?

---

### Post by chajuram on 2006-10-01
You can manually control the screen resolutions in the file /etc/X11/xorg.conf

More details may be found in [this post...]("http://www.ubuntuforums.org/showthread.php?t=195059&highlight=chajuram+screen")

---

### Post by cmaranhao on 2006-10-01
i also have this problem, when i typed that it appeared this:

Package `xsever-xorg' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xsever-xorg is not installed


i am a total noob, can you give me another option?

---

### Post by bigken on 2006-10-01
you typed it like I said sudo dpkg-reconfigure xserver-xorg

---

### Post by cmaranhao on 2006-10-01
i read the link you posted, i did this:

> sudo -s
<enter password>
nano -w /etc/X11/xorg.conf
scroll down to the bottom and you will find several sections looking like the one below:
Subsection "Display"
Depth 24
Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
EndSubsection

the problem is that i have this:

 SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection


i don't have the 1280x1024 option available. how can i edit those numbers and have the 1280X1024 resolution available??

---

### Post by cmaranhao on 2006-10-01
ok, i just finished editing them, now i have this:

 DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           16


how do i save these settings? after saving these settings will i be able to use 1280x1024 as a standard resolution?

---

### Post by uk_sphinx on 2006-10-01
thanks for the replys people.
i just installed the drivers for my card.
that seems to have sorted it.
does anyone know the actual cause of the problem?
just wondering if this will happen again and i will inevetably have to use your listed methods.

---

### Post by sbergman27 on 2006-10-01
> **cmaranhao said:**
> how do i save these settings? after saving these settings will i be able to use 1280x1024 as a standard resolution?

After editing the file, did you save it?  That should be enough.

---

### Post by cmaranhao on 2006-10-01
that is my problem, i don't know how to save ](*,)

---

### Post by sbergman27 on 2006-10-01
What editor are you using?

---

### Post by bodhi.zazen on 2006-10-01
> **cmaranhao said:**
> that is my problem, i don't know how to save ](*,)

What editor are you using?

You need to open xorg.conf as root:```
sudo gedit /etc/X11/xorg.conf
```

nano -> CtrlX, type Y to save.

gedit is a menu choice.

vi- i to edit, edit, then Esc, Shift :, type wq at the :, enter.

---

### Post by cmaranhao on 2006-10-01
i changed the numbers in the terminal.i went to the resolutions thru here (saw this posted somewhere):

sudo -s
<enter password>
nano -w /etc/X11/xorg.conf
scroll down to the bottom and you will find several sections looking like the one below:
Subsection "Display"
Depth 24
Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
EndSubsection

then i manually edited the resolutions, now i have this:

 DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600"
        EndSubSection
EndSection

i don't know how to save.. and will the resolution change alone?

---

### Post by bodhi.zazen on 2006-10-01
Look up....

Ctrl-X to exit nano, type Y to save.

Restart X. If you are in gnome now. Ctrl-alt-backspace.

---

### Post by cmaranhao on 2006-10-01
your last post slipped me, sorry

i saved but the resolution is the same, its at 1024x768 and i want it at 1280x1024.. what should i do now?

---

### Post by cmaranhao on 2006-10-01
i've done it again, this time thru gedit.. it is like this:

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800 Ultra/GeForce 6800 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1204x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1204x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1204x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1204x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1204x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1204x768" "800x600"
	EndSubSection
EndSection


i rebooted my pc but the resolution lowered from 1024x768 to 800x600 (the maximum resolution at the moment) and i cannot change it to 1280x1024..i cannot change the refresh rate either

---

### Post by bodhi.zazen on 2006-10-01
1. Lower the DefaultDepth to 16.

2. Confirm you monitor's horizontal and vertical refresh rates.

3. Install a driver for your video card.

To restore to default settings:```
sudo dpkg -reconfigure -phigh xserver-xorg
```

---

### Post by cmaranhao on 2006-10-01
my monitor is a samsung syncmaster 710n

i know it supports 75Hz of refresh rate, never heard about horizontal and vertical refresh rates.. 

about installing drivers, i had linux before (configured by a friend of mine) and that was not necessary

i remember seing him changing the resolutions (like i did maybe??) and i had 1280x1024 resolution after that

---

