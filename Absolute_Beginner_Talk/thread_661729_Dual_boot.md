---
title: "Dual boot????"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by G. Cotgreave on 2008-01-08
Hello people!!! Happy new year to everyone!!!

So the previous year i was living in Denmark were i discovered Ubuntu now that i returned back to Greece my sister saw ubuntu and she got really excited with it...now my problem...
She has a Sempron 2600 1.8GHz with 1GB RAM an ATI RADEON 9200 and i am not sure about the motherboard. I need to install to this machine both windows and Ubuntu, i have 2 hard drives one 100GB and one 200GB and i was thinking to install the 2 OSs separate in each hard drive. am i thinking the right way? what should i be careful during the ''operation'' Please give me your lights one more time...

---

### Post by Sef on 2008-01-08
1) Installing each on a separate drive is a good idea.  However, I do not know of tutorial on that.  

2) Run the Live CD for a while on her computer and see what problems, if any, occur.  If they occur on the Live CD, then most likely, they will occur when you install.

---

### Post by djbsteart1 on 2008-01-08
i cant say anything about the motherboard, but with 2 drives and windows already installed, it should be ok to just install ubuntu but make sure you check the data on disk and all, also, you can see what on the windows disk in ubuntu, but windows cannot read the ubuntu drive unless its formatted in fat 32, which i dont recommend as the main partition, so that can be done for data storage. another thing, is that you have one drive with 100gb and one with 200gb, if windows is on the 200gb drive you could have all data stored there and use the 100gb drive with a linux partition such as jfs or ext3. if the system is being installed from the base up, install windows first, this is very important as grub, the linux loader is far more adaptive and will generally recognise windows and list it on startup, where as is linux goes on first, the windows boot.ini needs editing which is annoying. good luck and hope it works out, for more info, use google.

---

### Post by bumanie on 2008-01-08
The most important thing to do is install windows onto the first (primary) drive, prior to installing ubuntu. Then install ubuntu whilst both drives are plugged in. [Some have made the mistake of installing each OS with the other drive unplugged. This is OK if you don't mind going into bios each time  and changing the drive boot order in accordance with the OS you want to use]. When you get up to the partitioning stage manually choose the second (slave) drive to install ubuntu to. 
It is a good idea to set up a separate /home as well as the mandatroy /root and /swap partitions. This way if something catastrophic happens to ubuntu later on, you should only have to reinstall the OS to /root and all your documents etc. should be safe.
By installing ubuntu after windows, grub should see the windows install and give you the option of which OS to boot.

---

### Post by G. Cotgreave on 2008-01-08
thank you very much!!! 
And something that i didn't mention is that i am going to make this computer from sratch with both hard drives formated...

---

### Post by bumanie on 2008-01-08
That should be perfect! - clean hard drives mean there shouldn't be any left over boot loaders from previous installs, which can sometimes be a hassle if they have not uninstalled correctly.

---

### Post by irish8890 on 2008-01-08
Clean installs of Windows and Linux on two separate drives is the best way to go.  I have been dual-booting this way on my desktop PC for about 10 years.

Make sure you install Windows first and then install Linux.  Windows must be on the primary drive.  Use the GRUB bootloader and Ubuntu will give you a menu to select OS after boot-up.  Try reading through some GRUB tutuorials/HOWTOs.  It will be useful.

Good Luck!

John

---

### Post by djbsteart1 on 2008-01-08
with ubuntu, both single and dual drive configurations work fine, just make sure windows goes on first. with a single drive config, you could have one drive for the systems and teh second one just for data in a format that both os's are happy with.

---

### Post by G. Cotgreave on 2008-01-09
i also thought about placing the 2 OSs in one Drive and data on the other but since i am new in ubuntu i will try the other way it seems to be cleaner and easier. Does anyone know if ubuntu supports the Ati Radeon series? I would like to have some of the 3d effects on my desktop but i know there is an issue between ubuntu and ATI.

---

### Post by bumanie on 2008-01-09
I have never installed an ati graphics card under ubuntu. I do know there are packages from ati available which include the card you ask about. Go here
[http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html](http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html)
I hope this works.
Also for yours and others information, ati is now owned by amd. Amd are planning to have ati graphics card drivers released under the open source model. So in the future, ati cards should be much easier to configure and install. I beleive all this is meant to come to fruition in the first half of this year.
Hope this helps.

---

