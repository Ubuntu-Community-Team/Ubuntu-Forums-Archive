---
title: "install and monitor"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by tbrownarcher on 2007-11-26
My monitor seems to be a problem it's a westinghouse LCD flat panel 

model l2046nv

I put in the disc and it started ubuntu , I clicked install and it started but not long at all it had issues with my monitor and so I manually chose LCD flat panel at 1024x768.  which is way under the capabilities of this monitor.  when I clicked or entered continue it went back to one of the first dos type screens (text screen) with no prompt and a flashing cursor.  I don't know what input it wanted but that seemed to be waiting on me... after 7 or 8 min i just dumped out and now it won't read the disk on boot as it did the first time.  

Can you help me ? 


thanks,

Tbrownarcher (nate)

---

### Post by tbrownarcher on 2007-11-26
Well, at least i was wrong about the cd not booting ... it does .  Now i need to get the monitor and video card going.  I clicked the closest to my monitor and my NVIDIA gforce fx5500. 

the same stuff happened as in the first post.  pretty much nothing but a text screen with a blinking cursor assuming it wanted input what input?  

Maybe I have a problem with my system there is an integrated video card from intel that came with the system.  It's a dell.  

I also have an NVIDIA Gforce FX5500 which i mentioned in the first post .. I probably need to disable the first or the intel video card but don't know how.  

any help? 

Thanks,
tbrownarcher (nate)

---

### Post by Hospadar on 2007-11-26
did it finish installation, or did it poop out with the black screen in the middle of installation?  are you plugged into a digital (white, with flat pins) or vga (blue, round pins) port.  Also, I assume the monitor is plugged into a port on the video card (not the integrated video on the motherboard)

What happens when you just boot off the cd, do the graphics work ok then?  when exactly do they stop working, randomly during installation (try and see what it's doing when stuff dies) or after installation during boot off the hard drive (what happens before it dies)?

---

### Post by tbrownarcher on 2007-11-26
**"did it finish installation, or did it poop out with the black screen in the middle of installation?"**

I'm not sure at all.  This is the very first thing it stops at after I select the "Start /install" line which comes up first on the cd install.

**"are you plugged into a digital (white, with flat pins) or vga (blue, round pins) port. Also, I assume the monitor is plugged into a port on the video card (not the integrated video on the motherboard)"**

I am plugged into the same port type I have always been plugged into.  I do not know what a digital flat pin plugin is so i assume it's the vga (it is a blue connector ) 
Yes the monitor is plugged into the NVIDIA port, the intel integrated port is empty.

[B][
What happens when you just boot off the cd, do the graphics work ok then?/B]

I will try that not sure.

** when exactly do they stop working, randomly during installation (try and see what it's doing when stuff dies) or after installation during boot off the hard drive (what happens before it dies)?**

It goes from the 'start/install' initialization right into the window for setting up my moniter/video card.  a message comes up that it is displaying in low graphic mode and asks me to configure which i try that don't work, it asks me to continue (the same stuff happens) or it also asks if i want to always run in low graphics mode ( which i have not yet tried).  

then after i complete that it takes me to a black screen with text lines 4 of them .  they say  they are ok and the cursor just sits there and blinks like it needs an input from me.  I wait not knowing what it's doing exactly and then after 7 or 8 minutes i just kill it ... 


Thanks,
Nate

---

### Post by the-edmeister on 2007-11-26
Did you run the LiveCD first to see if all your hardware is compatible?
> a message comes up that it is displaying in low graphic mode and asks me to configure which i try that don't work, it asks me to continue (the same stuff happens) or it also asks if i want to always run in low graphics mode ( which i have not yet tried).
Try running the installation in low graphics mode, if your video card and monitor are compatible you should be able to change the resolution once 7.10 is running on your PC.
.

---

### Post by tbrownarcher on 2007-11-26
Try running the installation in low graphics mode, if your video card and monitor are compatible you should be able to change the resolution once 7.10 is running on your PC.

I did try that later and it does the same thing as far as going to the 4 line text black screen that says 
"Running local boot graphics (etc/rc.local)"

thanks,
tbrownarcher (nate)

---

### Post by tbrownarcher on 2007-11-27
I seem to have worked around this first problem for now.  I have not ever set up the graphics card or the monitor nor do i have a user name nor have i set up the internet yet. 

What I have done is start this installation from the screen given by from the install disk into the **[COLOR="Red"]safe graphics mode[/COLOR]** 

On that screen is an icon that says install and so I tried it.  One of the first things is to repartition the system so I'm asking what to do .  Here is the way my drives are

I have 2 hard drives ... both are on IDE cables

the first one with windows on it is a 40 gig hard drive with enough space on it to also have linux on it.

The second one is a 100 gig drive with only a very few pictures on it over 95 %  or maybe 98 % free space but formatted of course for the windows file system.   

What I want to do is put linux on the first drive with windows and make that the dual boot system Or i could make one drive ubuntu and the other windows exclusively but I need a portion someday for windows files on the large one .

I'm actually open to suggestion on how to partition this system. 

Also when I got to the partition screen the terminology and the system were not straight forward to me so I need some esplanation abou the partition graphics system.

thanks very much,
tbrownarcher (nate)

---

