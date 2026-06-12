---
title: "Installing Ubuntu on PPC"
date: 2006-07-25
forum: Apple PPC Users
---

### Post by jaywalker13 on 2006-07-25
Hi

I tried putting this stuff on the beginners section, but was advised to try it here where the PPC people are likely to be.

I tried to run the live version of Ubuntu on my PPC but ran into problems from the first. If all the details below are too much, any general advice on this would be appreciated.

Hardware Overview:

  Machine Model:	Power Mac G4
  CPU Type:	PowerPC G4  (2.9)
  Number Of CPUs:	1
  CPU Speed:	467 MHz
  L2 Cache (per CPU):	1 MB
  Memory:	768 MB
  Bus Speed:	133 MHz
  Boot ROM Version:	4.1.8f5

ATY,Rage128Pro:

  Type:	display
  Bus:	AGP
  Display Type:	LCD
  Slot:	SLOT-1
  VRAM (Total):	16 MB
  Vendor:	ATI (0x1002)
  Device ID:	0x5046
  Revision ID:	0x0000
  ROM Revision:	113-72701-130

Display:

  Resolution:	1280 x 1024
  Depth:	32-bit Color
  Built-In:	Yes
  Main Display:	Yes
  Mirror:	Off
  Online:	Yes

1. Downloaded Ubuntu and burned the iso to a CD.
2. Restarted the PPC with the CD in the drive and "c" held down.
3. Got to a prompt that said just press enter and it should start the live version. After a brief flash of white, I got a black screen.
4. After about 3 minutes, a nice chime sounded, but the screen stayed dead.
5. Restarted the PPC.
6. At the prompt, I followed the on screen suggestion of entering "live video=ofonly".
7. A white bar appeared at the bottom of the screen and the word "Ubuntu" appeared in red on the right with a list of items that were loading and a bar that appeared to be showing the progress. However, the screen seemed to be split, with sentences starting halfway across and continuing on the left side of the screen.
8. I let it continue and after a few minutes of loading, it went to a blue screen with the same split screen effect. Included error message:
"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem? The <yes> option was not accessible at that stage. There were also numerous other messages spread across the screen, including the one about using "sudo" to access the root.
9. This screen included a prompt amongst all the scattered messages and I managed to find the xorg configuration file using: "sudo nano /etc/X11/xorg.config". I don't really know what to look for in this very long file, but I did notice that under "Screen", it mentioned 

 Monitor Generic Monitor 
 Default Depth 24
 SubSection "Display"
 Depth 1
 Modes "1024 x 768" "800 x 600" '640 x 480"

This was followed by a list of other "Depth" entries, all with the same "Mode" list. As my screen normally operates at 1280 x 1024, I wondered if this might at least have something to do with the split screen problem.

I messed around a bit more, but perhaps this is enough to ask you about now.

As I said above, any advice includiing "why don't you try something else instead" would be appreciated.

Regards

Jay

---

### Post by xurizaemon on 2006-07-25
i had similar experience with my G4-400 here ... will let you know if i find a way to move it forward.

must be a way to do console install and config from there?

---

### Post by avtolle on 2006-07-25
If you want to do an install, it seems to be the consensus of opinion on this Foru that the alternate CD should be downloaded and installed. If you're just seeing if 6.06 works, the Live CD is the only way to go; I would suggest you search the forum threads, as you are not the first with this issue.

---

### Post by KFASheldon on 2006-07-25
Not sure if this will help but the live cd fails on my iMAC G3 400Mhz in exactly the same way.  In this case it has something to do with the graphics settings.

For the iMAC DV I had to change /etc/X11/xorg.conf and restart gdm like so:

press control+alt+F1   after the chimes

you should see a text screen

type:

sudo nano /etc/X11/xog.conf

look down the text file for Device (ATi xxx xxx)

id you see an entry refering to DRI then put an # in fron of the line

goto the bottom of the file and you should see 3 line for DRI put a # in fron of them also.

now control+o

to save the file (write Out file)
then control+x to exit

then do this

sudu /etc/init.d/gdm restart
sudu killall -HUP gdm

If your issue is linked to mine that should get you a desktop

on the iMAC I also had to cahnge the refresh rate of Horizontal (in the xorg.conf file) to 60-60 and vertical to 75-117 but your screens should not need that but you could always try if you know the refresh rates sugested

Good luck hope it helps

---

### Post by zachws on 2006-07-25
If you have less than 192mb RAM, you want the alternate CD, with that config I would do the alternate CD anyway.

---

### Post by jaywalker13 on 2006-07-26
Thanks to all who responded. As I live in Austalia, we are a bit out of cync with times.

I followed your approach, KFASheldon. Changed the xog.conf file as suggested, with # placed in front of a number of lines.

Then did "sudo /etc/init.d/gdm restart"

Got the same blue screen as reported in my first posting. The screen was split as before, so is hard to read, but it appeared to say: 

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?" 

I accepted <Yes> and got (still split screen):

"X Window System Version 7.0.0 etc...
"Module Loader present
Markers: (--) probed, (**) from config file, (==)default setting, (++) from command line, (!!) notice, (II)informational, (WW) warning. (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: etc
"(==) Using config file: "/etc/X11/xorg.conf"

Clicked OK

"Would you like to view detailed X server output as well?"

Yes

Appeared to be exactly the same as the one I have detailed above.

OK

"The X server is now disabled. Restart when it is configured correctly."

OK

Back to prompt.

Got a similar result when I entered "sudo killall -HUP gdm". The same blue screens.

Also prompt message: "gdm: no process killed"

Re. other comments, I thought the alternate CD was for systems with limited RAM. I have 768 MB.

I have been trying to find references to this or similar problems on the threads, but have yet to track anything down. Any suggestions on where to look would be appreciated.

I really don't want to partition my internal HD, but would like to use my external firewire drive if possible. Any comments on doing that would also be appreciated.

Thanks for the responses. At least I am learning something, even if the OS won't work?

Jay

---

### Post by iamhugeinjapan on 2006-07-27
The alternate install is good for machines with low RAM but it's also very handy to install from anyway since the live-cd can be quite buggy, especially with PPC models.

---

### Post by jaywalker13 on 2006-07-27
Oh well. I have now tried installing the alternate cd, but still get the same split screen. I guess I will have to keep looking for ideas from these and other threads, but it's not looking good. I think it has defeated me for now.

Thanks for those who tried to help.

Jay

---

