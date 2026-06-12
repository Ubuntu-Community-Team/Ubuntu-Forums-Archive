---
title: "Realplayer video"
date: 2005-10-03
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2005-10-03
I want to watch the little videos on the  bbc news page, but when i  try to get the plugin, firefox says it has finished installing and tells me to  restart the browser. 
I do
And the plugin is not there. So i end up going aound in a circle :(

---

### Post by darkmatter on 2005-10-03
Plugin installation doesn't work the way it does in Windows. To install flash, Java, etc.

```
sudo apt-get install <putnameofapphere>
```

Or the easy way, open synaptic and search for the application needed and mark for installation then hit Apply.

---

### Post by adwait on 2005-10-03
I think he is talking about EXTENSIONS not PLUGINS........so they work the same as they do in windows.

---

### Post by Qrk on 2005-10-03
I have never gotten Realplayer to work in video. Has anyone else? I can watch real's format in gxine, but Realplayer won't do it.

---

### Post by Goober on 2005-10-04
I have got MPlayer to work with Hoary to play those little videos on BBC and such.  I forget how, it would be in Synpatic somewhere.

Actually, this might work.  For Hoary, i am pretty sure I followed these instructions:

[http://ubuntuguide.org/#mplayer](http://ubuntuguide.org/#mplayer)

I've yet to figure it out for Breezy, but I don't want to unecessarily mes around with it since it is unstable.

---

### Post by Mustard on 2005-10-04
I haven't bothered to try yet, but I'd sure like someone to pave the way. :D

---

### Post by darkmatter on 2005-10-04
They play with RealPlayer installed under Breezy without any problems.

---

### Post by dgrafix on 2005-10-04
i looked on the realplayer site and could not seem to find a linux version

---

### Post by darkmatter on 2005-10-04
[QUOTE=dgrafix]i looked on the realplayer site and could not seem to find a linux version[/QUOTE]
[http://www.real.com/](http://www.real.com/)

The entire frontpage is dedicated to it. Just click the download button

---

### Post by cletusbaird on 2005-10-17
Anybody can find the links; anyone can download the binary; but, not everyone is fortunate enough to have a copy of bree;) zy that works with realplayer10. I have tried to install on the breezy Gnome and the  Breezy KDE.(Ubuntu and Kubuntu) respectively and end up with
libc problems. Its like breezy has changed the libc back to five instea of 6 or something.
I had no problems with Warty or Hoary.
Except, Hoary did not recognize  ancient video card in one of my old computers unless you count 640x480 a resolution.

But, Ubuntu is still about the best distro , I have used.
I have tried  both rpm and debian based distros...from Redhat 6 to Fedora4, Sarge 3.1,Mandrake 8,9,10,10.1, second best debian for me anyway is Mepis...everything works on it ...but, its easy to blow a lot of stuff  if you stray into the pure deb repositories.

At any rate, I see enough comments on the Ubuntu Forum to indicate that I am not the only
one having configuration problems with what use to be a simple download, extract, change permissions and run.(Warty and Hoary).
Hopefully by release and shipit CD's these problems will be eliminated or I will probably just have to stick with Hoary.

---

### Post by tutti13 on 2005-10-17
I am really new to Ubuntu.  I am using version 5.10 and having the worst time installing Real Player.  No problem downloading the bin files or rpm.  What next?  The installation instructions coming with Real Player 10 GOLD don't do squat towards getting it going.  Through reading the forum,  I have got it to a point where The installation is looking for libstdc++.so.5.  Where can that be downloaded from and installed?  Thanks.

(Can you give instructions in opeing up files saved on the desktop)

---

### Post by Goober on 2005-10-17
Ok, never mind, a restart seems to have solved everything . . .

---

### Post by Goober on 2005-10-18
[QUOTE=tutti13]I am really new to Ubuntu.  I am using version 5.10 and having the worst time installing Real Player.  No problem downloading the bin files or rpm.  What next?  The installation instructions coming with Real Player 10 GOLD don't do squat towards getting it going.  Through reading the forum,  I have got it to a point where The installation is looking for libstdc++.so.5.  Where can that be downloaded from and installed?  Thanks.

(Can you give instructions in opeing up files saved on the desktop)[/QUOTE]

So, I assume you downloaded the .bin file from [www.real.com?](www.real.com?)  The next thing to do is either stick it into your Home folder, or go to the location where it is via your Command Terminal (I assume you know how to do this, if not, just ask), and do the following:

Installation Instructions

- Ensure that the .bin file you downloaded is executable. You can make the .bin file executable by running the "chmod a+x RealPlayer10GOLD.bin" command from a terminal window.

- Run the .bin file by typing "./RealPlayer10GOLD.bin". Follow the prompts provided to finish installing the player.

- When you launch the player for the first time, a set-up assistant will take you through configuring your player.

- Enjoy your RealPlayer10 for Linux!

That has worked for me.  Try looking for that file in Synpatic, if you still need it.

---

### Post by Marrea on 2005-10-18
I downloaded and installed Ubuntu 5.10 last weekend and on the website I noticed that one of the new features was a tool to ease the task of adding applications.  I therefore went to Applications>Add Applications, and I scrolled down to RealPlayer.  Instead of the program being installed for me, I was told the program was currently not installable, but should be available in the 'multiverse' repository.  Would I like to enable this repository?	 

Yes, I would. 

Then I'm told Real Networks does not allow redistribution of their software.  This package requires the user to fetch Realplayer separately from their website.  When you install this package you will be guided through that process.  This package installs the file rp8_linux20_libc6_i386_cs2_rpm from the real.com website (look for the Unix player).

Well file rp8 doesn't seem to exist anywhere.  What is the point of Ubuntu including RealPlayer in their list of Add Applications if all it leads to is a lot of rubbish about an unobtainable/obsolete file.

So off I go to [www.real.com/linux](www.real.com/linux) and download RealPlayer10GOLD.bin, which is probably what I should have done in the first place.  Did the chmod a+x RealPlayer10GOLD.bin stuff.  And then ran ./RealPlayer10GOLD.bin.   But no go.  It needs libstdc++.so.5, so I went to Synaptic and installed libstdc++5.   Then ran ./ RealPlayer10GOLD again.  This time it ran OK.   Only slight problem is you are asked where you want to install.  How are newbies supposed to know this?  I'm not exactly a newbie but I was a bit stumped at this point.  I'm used to letting things go wherever they want !!   I chose /usr/local/bin, which is probably wrong.   However, it had to go somewhere!

I went to the BBC site and could watch and hear the news videos and also listen to the radio sites there as well, so it all seems to have worked OK. 

All fairly easy in the end if you know what you are doing.  But why doesn't the RealPlayer entry in the Add Applications list direct you straight to RealPlayer10GOLD instead of leading you up a blind alley with all this nonsense about a rp8 file which doesn't seem to exist?   :p

---

