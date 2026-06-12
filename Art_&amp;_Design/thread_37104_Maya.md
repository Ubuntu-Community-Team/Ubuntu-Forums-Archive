---
title: "Maya"
date: 2005-05-25
forum: Art &amp; Design
---

### Post by tikal26 on 2005-05-25
I am wondering if anyone has gotten Maya to work in ubuntu. I know of other that got it to work in suse and madriva

---

### Post by TravisNewman on 2005-05-26
Alias/Wavefront DOES release a version of Maya for Linux. They used RedHat (I think) running Maya for Shrek 2. You'll have to pay just as much, though you may be able to use the same license and only have to pay one price for both versions, not sure, and if you "aquired" it without paying for it, I imagine it'll be a little harder to find the linux version.

As far as the Windows version running in Linux, I have no clue. But I thought the above info may be of interest :)

---

### Post by bored2k on 2005-05-26
[QUOTE=panickedthumb]Alias/Wavefront DOES release a version of Maya for Linux. They used RedHat (I think) running Maya for Shrek 2. You'll have to pay just as much, though you may be able to use the same license and only have to pay one price for both versions, not sure, and if you "aquired" it without paying for it, I imagine it'll be a little harder to find the linux version.

As far as the Windows version running in Linux, I have no clue. But I thought the above info may be of interest :)[/QUOTE]
 Shrek 2 was made on RedHat 7. So that is true. Titanic also.
[http://www.vnunet.com/news/1156282](http://www.vnunet.com/news/1156282)
[http://www.computer.org/computer/homepage/0202/ec/](http://www.computer.org/computer/homepage/0202/ec/)

---

### Post by Poul on 2005-05-26
i got maya to work in ubuntu

---

### Post by tikal26 on 2005-05-26
[QUOTE=Poul]i got maya to work in ubuntu[/QUOTE]
 I have a linux educational version and I am just wondering how you got it to run in ubuntu did you just use the alien command so far I hava had mied results with alien. Maybe the version you have had beign hack already to run on debian based distros. by the way I got it for free, but is a legal copy. Did you have to install the requiremenst in the page
[http://www.alias.com/eng/support/maya/qualified_hardware/QUAL/maya_65_linux.html](http://www.alias.com/eng/support/maya/qualified_hardware/QUAL/maya_65_linux.html)
or did you have to do anything special?
thanks for all of your replies. YOu are fats

---

### Post by 23meg on 2005-05-26
do proprietary third party plugins work as they do on the windows version as well?

---

### Post by tikal26 on 2005-05-26
[QUOTE=23meg]do proprietary third party plugins work as they do on the windows version as well?[/QUOTE]
 I don't know because I have not intalled it yet. I found someone that is going to help me set it up in linux this weekend so I'll let you know. This is so exciting now the only reason I need windows is for CAD and napster. and I just heard about them making inteliCAD for linux. We have four computers at home and with all the money I am saving with ubuntu now we have money left fro things like CAD

---

### Post by fawazarahman on 2005-05-26
Hi Guys I want to know more about Maya in Linux \\:D/

---

### Post by bored2k on 2005-05-26
[QUOTE=fawazarahman]Hi Guys I want to know more about Maya in Linux \\:D/[/QUOTE]
 What exactly.
[http://www.alias.com/eng/support/maya/qualified_hardware/QUAL/maya_60_linux.html](http://www.alias.com/eng/support/maya/qualified_hardware/QUAL/maya_60_linux.html)
[http://encyclopedia.thefreedictionary.com/Maya%20(software](http://encyclopedia.thefreedictionary.com/Maya%20(software))

---

### Post by kfc on 2005-05-29
I've got maya running in ubuntu.
Got alot of link lib fixxed manually and almost everything works now.
now the only problem left is the sound scrubbing part.
When i import sound in to maya, it stated that there "missing of libaudiofile.so".
So i've took the opportunities to try linking libaudiofile.so from /use/lib to /usr/aw/maya6.5/lib . at one point it works that I can get waveform display in the timesline. But when i scrub the timeline, maya just freezes and this clearly shows that my steps isn't correct in fixing this broken lib.

I've tried other distro like vidalinux (gentoo), Suse9.3, mandriva and redhat. All doesn't have such problem maybe it's because that they supports RPM installers. And the way i've installed maya in ubuntu (debian) is by using the alien converter.

for everybody who's interested to try installing maya in ubuntu and wanted to try fixing some broken lib on their own. here's a thread where u can find links for installation instructions and some of my post about fixing maya.
[http://www.cgtalk.com/showthread.php?t=227112&highlight=ubuntu+maya](http://www.cgtalk.com/showthread.php?t=227112&highlight=ubuntu+maya)

I hope someone in this forum will beable to gives me some idea in fixing the sound. I've tried using Alsa drivers according to ubuntu forums to see if it works. but still, no luck with that.

As for questions about 3rd part plugins. there's quite a handfull of linux maya plugins in [www.highend3d.com](www.highend3d.com)
I've got my Syflex cloth plugin, Shave and haircut and Turtle working. All sharing the same license from my windows version. Currently the only thing that doesn't allow me to use my linux maya for production is just because of the sounds problem. But atleast i did rendered quite alot of stuff out of my linux boxes for sometimes but after spending alot of time on fixing the sound. I'm starting to quit and rather rely on my windox box for animating.

Phew... enuff rant. Let's hope we can have someone good in linux to help us with this.
Cheer.

---

### Post by tikal26 on 2005-05-31
[QUOTE=kfc]I've got maya running in ubuntu.
Got alot of link lib fixxed manually and almost everything works now.
now the only problem left is the sound scrubbing part.
When i import sound in to maya, it stated that there "missing of libaudiofile.so".
So i've took the opportunities to try linking libaudiofile.so from /use/lib to /usr/aw/maya6.5/lib . at one point it works that I can get waveform display in the timesline. But when i scrub the timeline, maya just freezes and this clearly shows that my steps isn't correct in fixing this broken lib.

I've tried other distro like vidalinux (gentoo), Suse9.3, mandriva and redhat. All doesn't have such problem maybe it's because that they supports RPM installers. And the way i've installed maya in ubuntu (debian) is by using the alien converter.

for everybody who's interested to try installing maya in ubuntu and wanted to try fixing some broken lib on their own. here's a thread where u can find links for installation instructions and some of my post about fixing maya.
[http://www.cgtalk.com/showthread.php?t=227112&highlight=ubuntu+maya](http://www.cgtalk.com/showthread.php?t=227112&highlight=ubuntu+maya)

I hope someone in this forum will beable to gives me some idea in fixing the sound. I've tried using Alsa drivers according to ubuntu forums to see if it works. but still, no luck with that.

As for questions about 3rd part plugins. there's quite a handfull of linux maya plugins in [www.highend3d.com](www.highend3d.com)
I've got my Syflex cloth plugin, Shave and haircut and Turtle working. All sharing the same license from my windows version. Currently the only thing that doesn't allow me to use my linux maya for production is just because of the sounds problem. But atleast i did rendered quite alot of stuff out of my linux boxes for sometimes but after spending alot of time on fixing the sound. I'm starting to quit and rather rely on my windox box for animating.

Phew... enuff rant. Let's hope we can have someone good in linux to help us with this.
Cheer.[/QUOTE]
 I also got it half way working. I was having problems with metal ray but your link gave me some idea on how to fix it.

---

