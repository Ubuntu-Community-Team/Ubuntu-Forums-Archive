---
title: "How to fix the DVI problem?"
date: 2010-03-31
forum: Apple Hardware Users
---

### Post by 007casper on 2010-03-31
motherboard Intel BOXDG45FC
monitor 24 inch cinema display

DVI doesnt work on the 24inch display correctly.

what I dont understand is that hdmi works on a sony tv on the same motherboard.  

I hooked it up to DVI 24 inch cinema display and gnome interface looks puke brown.  

I figured DVI on the motherboard is faulty.  I hooked up an adapter to the motherboard's DVI, 
and it works flawlessy on the old a55 monitor that doesnt support DVI.

Do DVI's come at different pins on the mac monitors?  why colors are so massed up?
Do I need a special adapter?

Please, advise. Thank you.

---

### Post by linuxopjemac on 2010-03-31
[http://mac.linux.be/content/nvidia-driver-19053-released-fix-apple-24-display](http://mac.linux.be/content/nvidia-driver-19053-released-fix-apple-24-display)

Don't know if DVI will ever work, but VGA should work

---

### Post by buntuLo on 2010-03-31
DVI output works for me with a Samsung 21' external screen and the Apple MiniDisplayPort>DVI adapter. no special configuration, the NVIDIA setting gui recognises it and uses it properly.
video extension cables and comuter boxes always give me trouble, both for VGA and DVI, as the driver is unable to read the screen specifications. do you connect them directly, with one original cable?

---

### Post by 007casper on 2010-03-31
thanks for the link linuxopjemac.  Does this monitor have NVidia embedded in it?  The monitor is not iMac.  It is a plain monitor that I used to hook up to mac mini.  

@buntuLo - Yes.  I connected it with original cable.  Can you pull the cable on this monitor?  It seems like it wont come out.

I cant find the specs for the 24" monitor.  I should look around further...

After having color, and artifact pixel rain issues on the 24" monitor with Intel BOXDG45FC motherboard. I checked the motherboards video specs. It has Onboard Video Chipset Intel GMA X4500HD

Since, hdmi worked on Sony tv, and on an old monitor that doesnt support dvi (hooked it up with an adapter) on this motherboard.
I tried with another board I had, which is Intel BOXDQ45EK.  It has Onboard Video Chipset Intel GMA 4500.  I was using KDE interface, instead of Gnome on that board.  The monitor worked flawlessly again.

Is this a Gnome issue?  or just a plain driver problem?

What is the best solution?

Thank you

---

### Post by 007casper on 2010-03-31
anybody?  

I am just trying to figure out the main problem.  I am not sure if it is the drive vs. the interface gnome/kde.  I mean two mobo I tried have slightly different video chipset. 

It did work with kde.  I cant load that driver right now to the BOXDG45FC since I am not located there right now.  I am going to work on it the next few days.  I am just trying to figure out the best way to tackle the problem right now.

Thank you.

edit: I just found this.
> 
[http://ubuntuforums.org/showthread.php?t=1038269&highlight=nVidia+driver+190.53+released&page=2](http://ubuntuforums.org/showthread.php?t=1038269&highlight=nVidia+driver+190.53+released&page=2)

---

### Post by buntuLo on 2010-04-01
> **007casper said:**
> edit: I just found this
[http://ubuntuforums.org/showthread.php?t=1038269&highlight=nVidia+driver+190.53+released&page=2](http://ubuntuforums.org/showthread.php?t=1038269&highlight=nVidia+driver+190.53+released&page=2)

i'm now running nvidia-195, but tested the DVI output one year ago with 175 and 180, no problems. tested only under KDE, as in my signature.

from the few threads around that i remember about, it appeared to me to depend very much on the specific display connected. you may just test another one, if available.

i'm afraid i cannot help any further.. good luck!

---

### Post by 007casper on 2010-04-05
I installed kde without uninstalling gnome.  I still have the same issue.  

There are tremendous amount of pixelated screen, discoloration etc. 

I tried to find nvidia-195 in the synaptic.  It is not listed.  

I am not even sure what the package is called.
In the synaptic I have nvidia-settings, nvidia-180-kernel-source, nvidia-common, nvidia-71 modaliases etc

Is it suppose to say?
Package 	  | Installed Version 
nvidia-settings   |  195.00

---

### Post by buntuLo on 2010-04-05
> **007casper said:**
> In the synaptic I have nvidia-settings, nvidia-180-kernel-source, nvidia-common, nvidia-71 modaliases etc
which means you have nvidia-180 installed.
> **007casper said:**
> I tried to find nvidia-195 in the synaptic.  It is not listed.
as i said, updating the driver from 180 to 195 did not make the difference for me, as it was working already with 180 and 175.
you will not find nvidia-195 in in the official Ubuntu repositories yet. if you want to try it, you need to add the following repository (it is an experimental PPA) to you surces.list file:
```
http://ppa.launchpad.net/thefirstm/karmic-testing/ubuntu karmic main
```
then remove the corresponding old-version packages. finally install the new packages with:
```
sudo apt-get install nvidia-glx-195 nvidia-195-libvdpau nvidia-195-kernel-source nvidia-settings
```
a system reboot is necessary. i advise to remove the repository from the source.list file after the nvidia driver is installed, in order to avoid automatic updates of other packages present in the same repository.

but, seriously, try to get a chance to test the current driver with a different display: i would go to a large hardware store and ask to test one with my laptop.

---

### Post by 007casper on 2010-04-09
I did test the mobo with another monitor.  It was a VGA monitor it worked flawlessly.  

I should try to find another dvi monitor.  However, I think it is only a mac monitor issue.  There are a lot of people with similar problems.

The mobo is just having issues with the mac monitor.  Which is weird... I read somewhere that some guy uninstall every nvidia driver and installed the new one, and it worked.  However there are a lot of nvidia drivers listed under the whole thing.  And he didnt specify which ones to delete.  Still working on it...

---

### Post by linuxopjemac on 2010-04-10
Please keep us informed, I am also following this thread. It is useful information for future users ;)

---

### Post by 007casper on 2010-04-16
there is a link here on how to install nvidia drivers...
[http://ubuntuforums.org/showthread.php?t=990978&highlight=cinema+display](http://ubuntuforums.org/showthread.php?t=990978&highlight=cinema+display)

that didnt solve the issue for me yet...

ironically, I got two same motheboards and they are pretty much the same except model number due to hdmi and the other one doesnt have hdmi.  However, they are very similar in performance and components etc.

it comes out that mac mobos have nvidia, and so does the apple monitor.  They are competible to each other.  If you have a different mobo with different grfx card you may run into problems.  One solution to use a monitor that doesnt have grfx card in it.  Acer is a good option.  I got a set up with acer it works without a problem.

I am still trying to figure out how to use it with apple 30" cinema monitor.  The 30" monitor doesnt flicker, and doesnt have dancing pixels.  But it doesnt go over 1280x800... :-( 

does anyone know how to make the resolution higher? 
The monitor handles up to 2560 x 1600 pixels which is the optimum resolution for this monitor.


I will post back if I got a solution for it

---

