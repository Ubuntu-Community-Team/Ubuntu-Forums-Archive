---
title: "Fiesty on Pismo screen resolution problem"
date: 2007-08-20
forum: Apple PPC Users
---

### Post by Jim Baker on 2007-08-20
As a real noob I'm struggling with the terminal and screen resolution. I got Feisty to run a liveCD install procedure of KDE on my Pismo 400/512, with apparent full screen and good resolution during kernal load. But then the screen whacks to scrolling horizontal lines. One thing I noticed was at start of load, option to select *live powerpc. I presume that's correct for my Pismo, NO?

Still, with that selected, only thing that changes is the color of the horizontal stripes at end of load. I found some posts that seem to hold the solution—reconfigure xorg. but I tried typing the commands in the startup window, just got an invalid volume error or something invalid and stopped loading. This is really elementary, I know, but how do I get a terminal window on startup, or am I already in one when the screen is black and text white with what seems like load commands and options?

I tried F9 and Shift-F9 like someone suggested, that doesn't seem to do anything. Help getting unstuck would be appreciated.

---

### Post by frog_pilot on 2007-08-24
1. after booting from the cd, when the screen is black and the text is white, as you said, this is a prompt (it's like a terminal in a graphical environment), there you can type in your commands.

you cold try ```
sudo dpkg-reconfigure xserver-xorg
``` if you know what you are doing and if you know your hardware. You will get an interactive menu, where you have to fill in your hardware-specs for the correct setting of /etc/X11/xorg.conf (your main configuration-file). It is very important to type **sudo** to get administrator-rights, because only the superuser root is permitted to make modifications in the filesystem.

2. may be, the edgy alternate/ desktop cd works better

---

### Post by Jim Baker on 2007-08-31
Back in action with a working cd drive. Kubuntu live cd loads ok to the end but screen display is rolling horizontal bars with no discernable images visible so I can't do any setups. How can I break into live cd load sequence to command line and then type in x.org lines that were suggested? I guess that's what I need to try next but not sure how to proceed.
I know the answer is out there; step by step would be great!
Thanks.
Jim

---

### Post by curly_nostrill on 2007-08-31
Hey Jim,  

I have finally gotten Xubuntu feisty running pretty well on my iBook dual USB 500mhz 256MB.  What a pain.  First off I would suggest Xubuntu for a machine with your/our specs as Kubuntu w/ KDE is heavy on the resource use.  But maybe to just get you going here try "ctrl + option(alt) + F1 - F6" to get a plain terminal.  F7 is the terminal where the GUI runs.

Be careful with that "dpkg-reconfigure" command.  I ran that without knowing what I was doing and really horked my keyboard.  I finally had to resort to starting up with a Xubuntu Dapper Live CD(which works fantastically btw) to replace xorg.conf with a copy of the xorg.conf ajmctaggart posted in[ your other thread (http://ubuntuforums.org/showpost.php?p=3227440&postcount=2)]("http://ubuntuforums.org/showpost.php?p=3227440&postcount=2") which works just great for me On Xubu-Feisty.  After a bunch of other hurdles I won't describe right now, finally I restarted with the Xubuntu Dapper CD.  I had to mount the hard drive ```
sudo mkdir /media/<yourmount>
``` then ```
sudo mount -t ext3 /dev/<your hda#> /media/<yourmount>
```and did the "sudo ..." commands in the first part of that post to replace the horked xorg.conf with the one that works.

I also made the mistake of copy/paste in Mousepad (the editor in Xubu) which gave me an X error due to EOF problem.  That meant that there was no "new line" (return) at the very end of the text.  You may be able to make it work with Mousepad but you might have better luck to edit it in a terminal with 'nano': ```
sudo nano 
``` then "ctrl +shift + v" to paste in the code from the posted xorg and make sure there is a new line at the end of the file.  Then "ctrl + o" to save the file.  Nano will prompt you for a file name.  Specify /media/<your mount>/etc/X11/xorg.conf" (w/o quotes) then answer "y" to overwrite.  Then "ctrl + x" to exit.  If you manage to edit the file from your current install you will probably have to stop gdm or I think it's kdm in Kubu in a terminal with ```
sudo /etc/init.d/kdm stop
```.  Then just type```
kdm
``` without "sudo".  I made the mistake of "sudo"-ing that and ended up with a /home/<me> folder that was not entirely owned by me.  I then had to ```
sudo chown <me> /home/me
``` to get rights to my system menu tasks back.

Mind you I'm just substituting "gdm" with "kdm" since I'm using gnome so I'm not absolutely certain about the subst. in Kubuntu since I don't think I've ever used Kubu.  You might also try the Edgy version of any of these cd's as frog_pilot suggested.  I've never tried Edgy PPC.

You could also edit xorg.conf in a plain terminal if that's all you get but you won't have a copy/paste buffer AFAIK so you'll have to type in all the code precisely letter by letter.  Good luck with THAT.

Good luck.  I hope I didn't screw anything up here.  I'm pretty noobish as well.

---

