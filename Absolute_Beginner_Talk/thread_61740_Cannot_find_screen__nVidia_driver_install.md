---
title: "Cannot find screen / nVidia driver install"
date: 2005-09-01
forum: Absolute Beginner Talk
---

### Post by linux_is_2_hard_4_me on 2005-09-01
okay i just installed ubuntu...it seems really cool. one problem: i have no GUI interface at all. i am faced with a command prompt because there is a fatal error message that says something about not being able to find a screen. i researched this and it appears to be some kind of driver incompatibilty issue. i downloaded the nvidia driver for linux x86 through windows, and i need to know how to get that .run file into my linux root directory. OR:: i need to know how to access and edit my X configuration file and make it work. i am absolutely brand new to linux and i only know the commands Exec and Exit and i dont even really know how to use them that well. any help is greatly appriciated, i really want to use linux BAD!!! so thanks in advance to anyone that can help me out here.

---

### Post by heimo on 2005-09-02
Hi!

You should probably try to reconfigure Xorg (part of the graphical user interface). To do this, run this on command line:
 ```
sudo dpkg-reconfigure xserver-xorg
``` 

Pay attention to selecting video/graphics card driver and monitor settings. You can try selecting nv or vesa. As you have (I assume from your post) Nvidia card, it should work very well. :) Some more instructions, help to diagnose these problems:
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21](http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21)

:) Did these help? Anything new? Anything in logfile? (see post linked above)

Cheers!

---

### Post by linux_is_2_hard_4_me on 2005-09-02
[QUOTE=heimo]Hi!

You should probably try to reconfigure Xorg (part of the graphical user interface). To do this, run this on command line:
 ```
sudo dpkg-reconfigure xserver-xorg
``` 

Pay attention to selecting video/graphics card driver and monitor settings. You can try selecting nv or vesa. As you have (I assume from your post) Nvidia card, it should work very well. :) Some more instructions, help to diagnose these problems:
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21](http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21)

:) Did these help? Anything new? Anything in logfile? (see post linked above)

Cheers![/QUOTE]
 okay i tried the command and it brought me to the xorg configuration. i tried multiple driver selections and filled out all the information correctly. as i was selecting my color depth in bits...it comes up with an error message every time. "xserver-xorg postinst warning: overwriting pssoibly-customized configuration file; backup in /etc/x11/xorg.conf.200509021618" ...and i got that message every time. i try different color depth selections and many different driver selections and recieved that exact same error message every time. i will try looking at the other diagnostic link you sent me, but that is what's new for now. thanks for the help.

---

### Post by linux_is_2_hard_4_me on 2005-09-03
okay so it's been a day since i last posted. then i get back on here hoping someone has responded, but nobody has, so im still stuck using windows :( *tear tear*

---

### Post by Mustard on 2005-09-03
[QUOTE=linux_is_2_hard_4_me]okay so it's been a day since i last posted. then i get back on here hoping someone has responded, but nobody has, so im still stuck using windows :( *tear tear*[/QUOTE]
 How many attempts have you made on the install?

---

### Post by linux_is_2_hard_4_me on 2005-09-04
[QUOTE=Mustard]How many attempts have you made on the install?[/QUOTE]
 probably 20 to 25....and NOTHING at all has worked. its beginning to piss me off.

---

### Post by ubuntme on 2005-09-05
Hi, maybe try putting this in a different forum? e.g. instalation problems or something.

Not sure if that i going to help, but this is not really an absolute beginer problem...

You can install the nvidia drivers from the command line if necessary:

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-kernal-common

you can edit xorg.conf with the command:
sudo nano /etc/X11/xorg.conf

there will be a bit like this:
Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

make sure the driver is "nvidia" not "nv"

This is probably a difficult problem to solve for a beginner, Maybe a more user friendly dist may be in order?

btw what is your video card?

what happens when you run startx from the command line?
what does it say when you run:
cat /var/log/Xorg.0.log

(just interested in the main error messages)

Also what is the fatal error?

With some specific error messages someone may be able to help you.

---

### Post by rafakl on 2005-09-05
it can sound stupid but, check if your install cd is not damaged.

i installed one day from a damaged cd (i didnt noticed it), and i dont get installed some fonts or programs (like gedit).

 :razz:

---

### Post by ubuntme on 2005-09-05
This is quite possible, it happened to me, I certain archive was corrupt (it was in the error message!) so I looked for the file on the net, downloaded it an replaced the corrupt file and I got ubuntu owrking :)

---

### Post by linux_is_2_hard_4_me on 2005-09-06
Okay well i still got the exact same error message. i talked to someone fairly good with ubuntu and he corrected me, it is not an error message, but a warning message. this is what it says: "xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/x11/xorg.conf.200509021618" i did the install nvidia drivers off cd, and that was successful, but still no avail, and i made sure the driver was "nvidia" in the xorg config file. my exact graphics card is the nVidia GeForce4 MX 4000 PCI card. it is not the pci express version. nothing works, im thinking of just completely forgetting about it....but it looks so awesome.....

oh well....thanks for all the help. if anyone can figure this out, please help me!!

---

### Post by Knyven on 2005-09-06
[QUOTE=rafakl]it can sound stupid but, check if your install cd is not damaged.

i installed one day from a damaged cd (i didnt noticed it), and i dont get installed some fonts or programs (like gedit).

 :razz:[/QUOTE]
 I also agree that you have bad CD or bad download file.

Since you are using Nvidia, the Graphical interface should work at least.

---

### Post by ubuntme on 2005-09-07
Maybe try using the non- nvidia driver, change 'nvidia' to 'nv' and see if there is any change.

Also you didn't say what you got with:

what happens when you run startx from the command line?


what does it say when you run:
cat /var/log/Xorg.0.log

On this last one, only the last paragraph is of interest.

---

### Post by ubuntme on 2005-09-07
Actually, I have no idea what bit of the log will be of interest, but somewhere it should say what the problem is.

Another thing to run is dmesg and tell us if there is any nvidia related errors/warnings.

---

