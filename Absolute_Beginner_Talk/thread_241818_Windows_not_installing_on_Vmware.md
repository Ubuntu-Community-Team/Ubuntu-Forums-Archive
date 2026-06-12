---
title: "Windows not installing on Vmware?"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by Yusayoh on 2006-08-22
Hey :D 
I'm completely new to Linux and Ubuntu and just recently installed this wonderful OS. However, I need to use windows for drivers, games etc so I installed the newest version of VMware server using the tutorial on these forums. When I go to install windows, it says a file is missing: /1386/halapic.dll is missing. The Error code is 7.

How can I fix this to make windows be installed onto my Hard Drive so I can use it?

Thank you! :)

---

### Post by anaconda on 2006-08-23
Cant help you with your problem.

BUT you wrote:
> 
I need to use windows for drivers, games etc

And that is just wrong.. You can't use windows drivers in VMWare, because VMWare runs on top of ubuntu, and uses ubuntus drivers.. so you can't get any device working in VMWare that you can't get vorking in ubuntu!
And games dont work very well in VMWare either. Or they work othervise well, but graphics are horribly slow in VMWare, I even tried to run some older games (DOOM1) and they were reeeeaaaaly slow. (wolf3d worked ok! though)
I have 2,6GHz processor and 512MB ram..

---

### Post by Yusayoh on 2006-08-23
> **anaconda said:**
> Cant help you with your problem.

BUT you wrote:

And that is just wrong.. You can't use windows drivers in VMWare, because VMWare runs on top of ubuntu, and uses ubuntus drivers.. so you can't get any device working in VMWare that you can't get vorking in ubuntu!
And games dont work very well in VMWare either. Or they work othervise well, but graphics are horribly slow in VMWare, I even tried to run some older games (DOOM1) and they were reeeeaaaaly slow. (wolf3d worked ok! though)
I have 2,6GHz processor and 512MB ram..
Ah, okay I see. I have played Wolf3d and it's awesome ^^
Hm..Looks like I'll have to dual-boot then?

---

### Post by h0mer on 2006-08-23
> **Yusayoh said:**
> Looks like I'll have to dual-boot then?

If its for games and drivers, yes. If its for other apps, there is still hope, though you'll have be more precise with your problem. I've installed many windows through vmware and haven't encountered anything like this. Maybe a problem with your source CD?

btw, if your unrecognised devices are USB, you probably CAN set them up properly in win through vmware, since the host only sends usb info and the guest interprets it correctly with a proper driver.

---

### Post by Yusayoh on 2006-08-23
> **h0mer said:**
> If its for games and drivers, yes. If its for other apps, there is still hope, though you'll have be more precise with your problem. I've installed many windows through vmware and haven't encountered anything like this. Maybe a problem with your source CD?

btw, if your unrecognised devices are USB, you probably CAN set them up properly in win through vmware, since the host only sends usb info and the guest interprets it correctly with a proper driver.
Ah okay. My video camera isn't being picked up (made by Sony), I haven't gotten my creative Zen to show up either and I can't mount one of my Fat32 drives. I would also like to play games that you can play on ubuntu but they go really slow. I'm thinking it's my source CD and I'm going to try to get another one (via a friend or something). I have a Windows 2000 CD so that may work right? I mean of setting up the drivers? I'm not quite sure though if the drivers can be installed from 2000 if it says in the manuals that it cannot be run on 2000. I dunno.

---

