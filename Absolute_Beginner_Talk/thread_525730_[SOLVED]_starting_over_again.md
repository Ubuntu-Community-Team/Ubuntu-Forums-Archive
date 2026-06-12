---
title: "[SOLVED] starting over again"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by kerrymorgan1 on 2007-08-14
ok my specs first:
2Gb ram, amd400+, 500GB SATA HD, 8600GT graphics...... arrived 2 days ago new
when i tried to install Linux i got a little carried away in the terminal for the first time i was assured by a friend i couldn't wreck anything. when i restarted it would go blank for about 2 or 3 mins then start up linux. i thought by installing windows it would format and fix my issue........ Windows is fully installed and it's good but i want Linux. i tried to run the Live Cd but every time the Ubuntu Live Cd comes up i click on start or install (or any other option ie. safemode, the results the same) it goes blank screen dies and the cpu is still running then after a few minutes it runs linux? what have i done? have i killed the Graphics?:confused: 

I want a fresh start! a rematch i have tried to install Grub in the terminal tried, reset the BIOS what can i do? 

this is a new machine i don't know what to do
someone please any one please help

---

### Post by Blutack on 2007-08-14
So you could boot a Live CD and now you can't?
Is the computer DEFINATELY booting from the Live CD when you put one in?  Or is it booting into your borked linux install?

---

### Post by Jimmyfj on 2007-08-14
On a brand new computer you should have the option to select a boot menu when you turn on the computer from power off. Try hitting the F12 key to see if it gives you a boot menu then choose to boot from CD/DVD or removable device. 

If this doesn't give you a startup on the live Cd try altering your bios and make your frist boot device your CD-ROM/DVD drive. It obviously isn't so at the moment and it seems you are booting up in the screwed up install. Resetting the BIOS means you set back the BIOS to Facrory default which does not include a first boot device being your CD/DVD drive.

---

### Post by kerrymorgan1 on 2007-08-14
I am running from the Hd now but the result is the same the graphics screen comes up then blank few seconds while the system does something then Ubuntu starts up like nothing happened
the Live CD is the same i have run that and i just can't figure out why it's going blank for a few moments before it loads...........

---

### Post by redmonster13 on 2007-08-14
Try installing WUBI, it will give you a ubuntu install on your hdd instead of using the rather slow live cd version. 

It is the easiest way I have found to do a dual boot setup.

---

### Post by kerrymorgan1 on 2007-08-14
I have done that too..... thats how i run the Live Cd i have changed the boot priority 1 to CD device ..... the computer reboots and the live Cd runs when i click on the option ("install or start" or any other option(i have tried them all))  it goes blank then a few mins later starts up is this normal?)

---

### Post by jingo811 on 2007-08-14
If your hardware is fully functional according to your Windows install.  I have some reading material for you in case you're up to it.  Just click the colored link in my signature.  Can't promise you anything though!

---

### Post by WebSiteGuru on 2007-08-14
> 2Gb ram, amd400+, 500GB SATA HD, 8600GT graphics

Another thing you might want to look into, that I noticed, is SATA HD Setting in BIOS. Go to BIOS and edit your SATA configuration and make sure you select backward compatible mode.

---

### Post by kerrymorgan1 on 2007-08-14
Installing Wubi might reiinstall Linux but i have already installed it and it has problems Loading!!!!!
am i not explaining my problems well? umm:confused:

the Live Cd i got is for the 64bit machine i have tried the other 32 bit one too is new and shouldn't have any problems.
Linux is on my computer installed fully (i haven't installed any drivers or anything yet though)
windows too having problems with that....... another day another time.
i just wanna start over again any way of reformating everything and undoing it all?

---

### Post by kerrymorgan1 on 2007-08-14
how do i reset it to backward? 
i'm really new to this sort of thing, please help me take the first steps

---

### Post by WebSiteGuru on 2007-08-14
> **kerrymorgan1 said:**
> how do i reset it to backward? 
i'm really new to this sort of thing, please help me take the first steps

When the computer is booting up there should be an option to go into setup. (either ESC, F2, F12, etc...) Hit that keystroke and it should load up the BIOS setting. Go through all the setting and find the SATA setup setting. Change it from SATA ONLY to both. Exit and save setting.

---

### Post by kerrymorgan1 on 2007-08-14
THANKS! thunderbirds are all go FORUMS ROCK!!!!!!!

---

### Post by WebSiteGuru on 2007-08-14
> **kerrymorgan1 said:**
> THANKS! thunderbirds are all go FORUMS ROCK!!!!!!!

So, I would assume my method works. :guitar: And you are WELCOME! :D

---

### Post by kerrymorgan1 on 2007-08-15
there is no sata option!!! what do i do now?

---

### Post by WebSiteGuru on 2007-08-15
> **kerrymorgan1 said:**
> there is no sata option!!! what do i do now?


You mean in the BIOS configuration? Depends on what type of BIOS, you might have to search for it. It can be in the Harddrive configuration page. Look there.

---

