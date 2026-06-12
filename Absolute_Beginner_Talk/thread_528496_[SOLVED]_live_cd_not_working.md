---
title: "[SOLVED] live cd not working"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by Niklas Schröder on 2007-08-17
i made a post a while back about my future plans of an ubuntu for seniors.  well it's kinda in the works and i'm attempting to put a stock ubuntu install on my grandma's dell dimension 2350 to no avail.  it shows me the start-up screen for the live cd, i select start or install, and it goes through it's normal loading of the linux kernels, but then shows a blank screen.  i've also tried my gparted live cd to see what the problem was.  i used the terminal mode and found that the live cd's couldn't locate any screens.  could it be because of her intel graphics card?  (i have an intel in my laptop and didn't have any problems with the live cd).  i'm currently stuck in windows on her computer and using a weak wireless network i'm using without the knowledge of the neighbors.  ;)  so if possible, when you ask for more information about her computer, it'd be nice if you could tell me how to give it to you in windows.  i would normally be able to get it to you that way, but i haven't even booted into windows in three months.  :p 

UBUNTU IS JUST TOO GOOD!!!  lol.

---

### Post by Sef on 2007-08-18
1) Did you md5 sum the download?

2) Did you burn it at 4x or less?

3) Did you check for errors?

---

### Post by Niklas Schröder on 2007-08-18
how would md5 sum the download? k3b came up with something about md5.  but i didn't know what it meant.  :p  i burned at 10x cause that's the slowest my burner goes, but the disk works fine on my laptop.  when i check for errors, i get pretty much the same problem described above.

---

### Post by overdrank on 2007-08-18
> **Niklas Schröder said:**
> how would md5 sum the download? k3b came up with something about md5.  but i didn't know what it meant.  :p  i burned at 10x cause that's the slowest my burner goes, but the disk works fine on my laptop.  when i check for errors, i get pretty much the same problem described above.

HI how much ram is on the system? 10x could be some problems for some older drives. Have you tried the alternate cd since you are not trying to show them ubuntu but just installing it.

---

### Post by Niklas Schröder on 2007-08-18
i believe there is only a single ram chip.  i could be mistaken though.  probably 128 mb.  and i haven't tried the alternate cause i kinda like the graphical interface.  i'm not exactly sure i can successfully install the way i want without the GUI.

---

### Post by overdrank on 2007-08-18
> **Niklas Schröder said:**
> i belive there is only a single ram chip.  i could be mistaken though.  probably 128 mb.  and i haven't tried the alternate cause i kinda like the graphical interface.  i'm not exactly sure i can successfully install the way i want without the GUI.

Ok well if it is 128mb that will stall the install. And if is is 256 that may be a problem also because some of the memory is dedicated to the onboard video. Then alternate cd is not bad at all to install with and with the limited ram It still may have trouble running the system. :(

---

### Post by Niklas Schröder on 2007-08-18
is there a way of seeing how much ram there is on her computer through windows short of taking apart the computer (i'm totally fine doing that, but i don't think my grandma would be too happy.  ;) )?

---

### Post by overdrank on 2007-08-18
> **Niklas Schröder said:**
> is there a way of seeing how much ram there is on her computer through windows short of taking apart the computer (i'm totally fine doing that, but i don't think my grandma would be too happy.  ;) )?

Hi yes there is if you have a my computer icon on the desk top you can right click on it and choose properties and on the fist window it tells you how memory and what type of cpu.

---

### Post by Niklas Schröder on 2007-08-18
ok.  here's the specs i brought up through control panel.

> 
Dell DIMENSION DIM2350
Inte(R)
Celeron(R) CPU 2.20GHz
2.19 GHz
128 MB of RAM


(the right-click thing didn't work.  you have to go to control panel and select "system")

---

### Post by mysticmatrix on 2007-08-18
The live cd requires atleast 256 MB of ram to start. However, you can use the alternate cd to install Ubuntu. Although the installer is text based, it is not hard to install at all except that you will have to use left/right keys and enter instead of a mouse.

A good guide using Alternate CD installation is at [https://help.ubuntu.com/community/Installation/I386](https://help.ubuntu.com/community/Installation/I386)

---

### Post by Niklas Schröder on 2007-08-18
ok.  but the big problem is that i need to resize the windows partition in gparted before i install.  and my gparted live cd won't do the trick.

---

### Post by mysticmatrix on 2007-08-18
Although I haven't tried to resize any any partition till now, I guess Ubuntu CD can resize your Windows Partition for you. Here is guide I believe that exactly fits your case:

[http://users.bigpond.net.au/hermanzone/p2.htm](http://users.bigpond.net.au/hermanzone/p2.htm)

---

### Post by New Fawn on 2007-08-18
Hi ,

I am also new  on the ubuntu wagon. system is Pentium III 500mhz , 256mb ram , 10gig hdsk ntfs , nividia geforce2 max 400 grafik card ( infact asus V7100 combo delux which has a tv tuner also , but if tv tuner does not work for the time being no care)  , soundblaster live snd crd system.

The live cd fro fiesty fawn never boots up. I have a nec usb 2 pci card also installed is this the one causing trouble and not detected ? 

I do not mind tptaly getting the windows kicked out of the system if i can install a good X windows loaded system. this is my old pc which i want to make my open linux learning platform.

thanks a ton for all advice how to do this struggling for alst one week.

---

### Post by Niklas Schröder on 2007-08-18
i don't think i can help you that much since i'm in the same boat, but i would like to point out that i'm NOT an ubuntu noob.  i've been doing it for quite a while now.  but i've never installed on a tower before, just laptops.  now if you have problems with composite managers or re-partitioning hard drives, THAT'S what i'm good at.  ;)

---

