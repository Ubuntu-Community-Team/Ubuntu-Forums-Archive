---
title: "4 problems"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2006-08-12
1. My monitor works, but ONLY IF I plug it into the port that's built into the motherboard. The problem with this is that I can't use my nVidia graphics card, which has a monitor port that hooks into the motherboard via PCI. When I reboot and hit F2 (Setup), then change the default video adapter to "AUTO" (instead of "on-board") it allows me to "view" my computer on my monitor when it's plugged into the video card. But, when I boot, Ubuntu freezes on "Loading Hardware drivers..."  What do I do for this? I want to be able to use my video card

2. When I try to watch videos online with Macromedia flash player, the sound doesn't work. I know my soundcard works and I'm listening to music on amaroK right now. How do I fix this?

3. Yeah, so I don't know how to install programs or use .exe files, which sucks... For example: I want to install Star Craft, but when I put in the CD and open it, I can't run any of the .exe files. What am I supposed to do? I tried downloading wine, libwine, wine-dev, and libwine-dev, via Synaptic, but I can't find the programs anywhere on my computer and I don't know how to use them. Please help!

4. When I'm online and I try to view a video (mpeg, wmv, etc.) via Firefox, there's usually message saying I need a plugin to view it (ie - Quicktime). How/Where do I download the necessary plugins/programs to view these files online?


Thanks!

---

### Post by baldy1324 on 2006-08-12
i can't answer all of your questions but here's what ive got.
>  	1. My monitor works, but ONLY IF I plug it into the port that's built into the motherboard. The problem with this is that I can't use my nVidia graphics card, which has a monitor port that hooks into the motherboard via PCI. When I reboot and hit F2 (Setup), then change the default video adapter to "AUTO" (instead of "on-board") it allows me to "view" my computer on my monitor when it's plugged into the video card. But, when I boot, Ubuntu freezes on "Loading Hardware drivers..." What do I do for this? I want to be able to use my video card
do you already have an installed ubuntu system or is this the installation cd? not sure about the rest.

> 3. Yeah, so I don't know how to install programs or use .exe files, which sucks... For example: I want to install Star Craft, but when I put in the CD and open it, I can't run any of the .exe files. What am I supposed to do? I tried downloading wine, libwine, wine-dev, and libwine-dev, via Synaptic, but I can't find the programs anywhere on my computer and I don't know how to use them. Please help!
ok long answer basically wine can't emulate everything it is an ongoing project to emulate windows api's so don't think windows program support is build-in to linux. if using wine is what you want to do, follow the instructions on this thread-http://www.ubuntuforums.org/showthread.php?t=149585&highlight=wine+setup+howto.
it may be long but it gets it done (im running dreamweaver using that method). and p.s. wine itself dosen't have a gui, but winetools (in that thread does)

ok installing native ubuntu/debian programs with APT (command-line version that is faster than synaptic and you'll need to learn it sometime).:) 
here is a howto for using apt on debian website (which ubuntu is based off of). yes it is very long and a lot of it you will never use but you'll learn how to install programs great.-http://www.debian.org/doc/manuals/apt-howto/.

> 4. When I'm online and I try to view a video (mpeg, wmv, etc.) via Firefox, there's usually message saying I need a plugin to view it (ie - Quicktime). How/Where do I download the necessary plugins/programs to view these files online?
first run ```
gksudo gedit /etc/apt/sources.list
```
then uncomment (delete the pound signs in front of the lines that say either universe or multiverse) - this makes the unsupported software avaiablable.   and then run-
```
sudo apt-get install mozilla-mplayer
```

---

### Post by kbsuperstar on 2006-08-12
REPLYING TO YOUR SUGGESTIONS:

Problem #1 (video card):

> do you already have an installed ubuntu system or is this the installation cd? not sure about the rest.

Yes, I already have Ubuntu installed to my HD (I don't have Windows anymore). I'm not using the CD to boot.

Problem #3 (installing software):

Thank you for the manuals, I'm sure they'll help. I'll repost if I get lost :D

UPDATE: When I'm running Winetools, I have to install IE in order to continue installing the rest of the base windows software, but when I try to install it I get an error message saying that the installation is failed. WT won't let me install any other software until I install IE. What do I do?

Problem #4 (mplayer w/Firefox):

I ran the code through the terminal, and it successfully installed the mplayer plugin to Firefox. But, when I play/stream a video from the net, I can't see anything. It buffers to 100% and then nothing happens. Most of the time, I hear the sound, but no video. Help](*,) 



If anyone can help, it'd be greatly appreciated! Please go back to my original post to see all 4 of the problems I'm having. Thank you!

---

