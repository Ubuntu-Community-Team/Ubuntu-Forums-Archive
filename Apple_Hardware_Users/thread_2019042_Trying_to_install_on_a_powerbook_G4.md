---
title: "Trying to install on a powerbook G4"
date: 2012-07-06
forum: Apple Hardware Users
---

### Post by zmatt on 2012-07-06
I have a later model 1.5Ghz Powerbook G4 that I am trying to install 12.04 on. Its been awhile since I have used Ubuntu and it seems a lot has changed, especially in the interface. I loaded the live cd and it appears the Gui is not fully loading for me. When ever I click on the option to install 12.04 I get a large white area that takes up the majority of the screen and then nothing. It looks like there is supposed to be something in this window but its just empty whitespace. I've tried several other of the things listed on the side such as the home folder and ubuntu one and they give the same empty window. Sometimes the computer will wake up and obviously start doing something but I can't seem to get any more of a reaction. I was even able to start the terminal in an attempt to manually start the install but to no avail. Again, a large empty whitespace and typing as if it were there but just invisible didn't help either.

---

### Post by GREENH3ART on 2012-07-06
How are you installing it? Are you single-booting, dual-booting, or installing as a virtual machine? I don't know if I can help with this post, but that information might help others.

Good luck :)

---

### Post by zmatt on 2012-07-06
It will be a single boot, currently there is no OS on the hard drive.

---

### Post by zmatt on 2012-07-07
can i start the installer without loading the live cd? I checked the yaboot options and there are only live ones no straight installer.

---

### Post by zmatt on 2012-07-07
Ok so I have narrowed it down to a problem with the graphics drivers if that wasn't already obvious. 


Here is how it looked at first
[IMG]http://i80.photobucket.com/albums/j185/mbwhite/2012-07-07024729.jpg[/IMG]

no matter what I clicked on this is what I got, except for the dashboard. That worked but anything I tried to start gave me this screen. 

I tried the live video=ofonly at the yaboot prompt and that didn't change anything. 

Then I found [this]("http://ubuntuforums.org/showthread.php?t=1885263") thread and tried the nouveau.modeset=0 parameter. This got me a splash screen which I had not seen before and then some error messages about modset not being valid and it crashed nouveau. 

What this gave me when I reached the desktop was this:

[IMG]http://i80.photobucket.com/albums/j185/mbwhite/2012-07-07025704.jpg[/IMG]


As trippy as it is I was able to start the installer. 

[IMG]http://i80.photobucket.com/albums/j185/mbwhite/2012-07-07030233.jpg[/IMG]


The files copied to the hard drive without drama. 

[IMG]http://i80.photobucket.com/albums/j185/mbwhite/2012-07-07030327.jpg[/IMG]


But then I got some scattered errors about components crashing that were vague. Then the entire installer crashed when it was installing the copied files. At this point I gave up for the night. I don't remember it being this hard with 8.04. what gives?

---

### Post by seinch on 2012-07-07
You need to install a light version, like Lubuntu, with the alternate cd. This works fine with me Powerbook G4 12".

After some tunes, wifi, sound, and display workfine... You can use the search to find all the solutions.

Good luck!

Seinch

---

### Post by 2blue on 2012-07-07
I have an old G4 too, from 2005, 1,42 GHz prosessor. I have burned lubuntu, but cannot boot up. I get as far as a lubuntu logo, but not as far as the CD health check and boot up options. Firmware is not closed. Have you had any luck booting the live CD?

Regards

---

### Post by zmatt on 2012-07-07
well I'm out of cd-rs so i tried booting via flash drive. I have it formatted in fat as bootable with the lubuntu ppc on it. I was able to find it in the open firmware menu but when I tried to boot it the firmware says it can't open the device or file. I know usb flash booting is possible on new world macs I imagine there is just something wrong with the way the flash drive is configured.



EDIT

I found a blank cr-r. Lubuntu is even worse than ubuntu though. The thing wont boot to the live cd. It just throws a million dma errors. Then the whole session times out because of the dma error and it falls on its face. I though it was compatible with the powerbook g4?

---

### Post by 2blue on 2012-07-07
I suppose the new macs are regular pcs these days, since we easily can dual boot them with windows. Though I am have difficulties with this old thing. I might have to get more RAM, it has only 512MB, I know you can get buy with old CPUs around 1.42GHz for most regular stuff. I'm not giving up just yet.

---

### Post by seinch on 2012-07-08
I'm running a dual boot of MacOsX and Lubuntu 12.04 on Powerbook G4 12", 1.5Ghz with 1Gb Ram.

You can try to download the Alternate CD version, Install the system (without running live session) through the non graphical installer that Alternate Cd use. It works fine for me... 

After that, you can tune all the system to works pretty well in our machine.

Godd luck and regards!

---

### Post by str8bs on 2012-07-13
zmatt-
Saw your post on another forum as well. Are you still stuck with video issues?

That first picture looks similar to an issue I've seen in other desktops. It looks almost there but maybe EXA or composite issues. (workarounds to those in FAQ/Known Issues)
The second "psychedelic" is expected with modeset 0.

Did you try ruling out acceleration?
```
boot: live nouveau.noaccel=1
```If you can CTL-ALT-F1 or CTL-ALT-T to a prompt and get a copy of /var/log/Xorg.0.log and post it, others might be able to help more.

Also, IMHO, it is good practice to look up and post your video card model when discussing graphics issues so readers know exactly what hardware is being discussed. I'm assuming yours has Nvidia Go5200. everymac.com is a good source to look up.

---

### Post by peezee13 on 2012-12-08
Same problem here (cf my thread) with a Powerbook Alu G4 1.33GHz and GeForce FX Go5200 graphics, same solution (noaccel) and the only one that works (also get the blank screen or psychedelic colours, depending on what other boot commands I use).

Just wanted to check whether or not any progress had been made on this issue.

Other pbm is that playing MPEG video eats up almost 100% of CPU, Ok when playing the video in its native size, but when I set it to full screen the video slows down to like half normal speed, though audio continues to play at normal speed and therefore  quickly gets out of sync. (but the video plays until the end, while all controls in the player's GUI (gnome-mplayer is the only one I got working) behave normally.

Not sure the issues are related, although obviously both have to do with limited support for NVidia graphics chipset on PPC based Mac's.

---

### Post by asifnaz on 2012-12-13
I think you should try a lighter version (Lubuntu or xbuntu )

---

### Post by zenfunk on 2012-12-28
I recently installed Lubuntu on  an iBook G4. At first I had no hardware graphic acceleration also and the only Player that gave me aceptable video playback performance was VLC. All others where just too slow. After a downgrade of the Mesa drivers I got 3d acceleration and now its buisness as usual with mplayer. totem etc. also. 
So if you can't get hardware acceleration to work, try VLC. Better still, try hard to get your graphics card working correctly, so this is easier said than done.
Good luck, Christian

---

