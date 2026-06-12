---
title: "Accessing music/photos in dual boot. Baby talk needed"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by johnwillyums on 2007-10-22
Hi all. I'm a complete noob both with Ubuntu 64x and Vista 64x and computers in general.
3 days with Ubuntu 7.10 64x and 2 months with Vista 64x and my computer.
I've managed to set up a dual boot so am very pleased with myself about that but now I want to start playing my music (mp3 and FLAC files) and viewing my photos (jpg and cr2 raw files) in Ubuntu.
Of course they're all in the Vista section of my hard drive. I can see the folders in system but they open up empty.
I read some other posts about this but I don't really understand this stuff about mounting to a NTFS partition etc. Also everything seems to be about Windows XP and Feisty Fawn and I presume there might be a difference with Gutsy and also 2 64x OSs.
I'd be really grateful if someone could baby talk me through the process of accessing the music etc so I can play it in Ubuntu also I'd like to try out Gimp and if it is as good as PS CS3 I might sack Vista altogether (maybe not just yet though)

My system is as follows- Intel Q6600, Asus P5N-E SLI, 4GB ram, nVidia 8600GT, 500GB hard drive. Ubuntu seems to have found itself about 25GB of free space which is odd because over half the drive is unused. Oh well.

Thanks for listening, John Williams

PS. I've got compizfusion set up with cube effects etc enabled. Can anyone point me at a tutorial on how to use it. I presume it's some kind of keyboard operation but at the moment I don't know how to switch it on. J

---

### Post by benerivo on 2007-10-22
To use the cube, you have to hold down <Ctrl> and <Alt> together and then with the left mouse held down as well, you can swing the cube around. However, if you have it installed already, it should appear as a rotating cube every time you change to a different desktop screen.

It's odd how you can see the folders of your ntfs partition, but not the files within thwem. I have never come across this before on a Windows partition. How do you go about looking at the drive contents? Is the vista partition mounted automatically, and visible from a nautilus window?

---

### Post by benerivo on 2007-10-22
Also make sure you have 'Compiz configuration settings manager' installed in Synaptic. This is a great compiz settings manager.

---

### Post by Shazaam on 2007-10-22
Ubuntu usually "automounts" other drives/partitions as READ only. You probably have icons on your Ubuntu desktop for them.
A couple of things that might help.
1. Have you enabled viewing hidden files in nautilus? View>Show Hidden Files (or CTRL+H)
2. Boot Vista. Drag the folders that have the files you want to access to "Shared Folders" (is that still there in Vista?),  After you do that reboot into Ubuntu, open the Shared folder (access it from Ubuntu) then copy/paste the files  to Ubuntu. I did that with my music and pic collections. Depending on the amount (size) of the files you may need to either resize the Ubuntu partition bigger or make a separate partition for the media files.

Some here will probably tell you to install tools for WRITE access between Vista/Ubuntu. Use at your own risk. I did that but WidowsXP developed a habit of scattering files all over my Ubuntu partition which I didn't like. YMMV.

---

### Post by johnwillyums on 2007-10-22
Thanks everyone. I can now hear music through amarok and view my photos. 
Not sure whether I can edit images in gimp or whatever.
I'll try that tomorrow.
As for compizfusion I have installed the manager but only get a 2 sided desk top. Maybe I've got it set up wrong in the manager but I've enabled the rotating cube effect and a couple of other cube related things but still no cube> I can just manipulate a two sided flat..

Thanks to you all for your input, John Williams

---

### Post by benerivo on 2007-10-22
> I've enabled the rotating cube effect and a couple of other cube related things but still no cube> I can just manipulate a two sided flatThis is quite common, and i can't seem to get around this at all when using kubuntu/kde, but try changing the number of desktops you have in ubuntu (by right clicking on the little desktop window. in the taskbar and going to preferences). With compiz, playing around with the settings can often fix things that don't work straight away.

---

