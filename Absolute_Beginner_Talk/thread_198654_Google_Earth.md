---
title: "Google Earth"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by saltscar on 2006-06-17
I have downloaded Google Earth to my home folder.  How do I install and run this?  Can I place an icon on my desktop?

---

### Post by s_h_a_d_o_w_s on 2006-06-17
You can double click the setup.exe if you have wine installed. Google earth is designed to work with windows, but you can get it working, though it looks bad. If you really need it, you can get vmware and run windows in a virtual PC. 

Hope that helps.

Drag the .exe that runs google earth to your desktop.

---

### Post by 5-HT on 2006-06-17
To install the Linux-native version:
In a terminal, go the directory where GoogleEarthLinux.bin is stored and enter: ```
 sh GoogleEarthLinux.bin 
``` 
If you want to make a shortcut on the desktop, the command to run Google Earth would be ```
 /home/<username>/google-earth/googleearth 
``` 
BTW, there are lots of threads around that describe how to install the program. 
A search can be quicker than creating a new post and waiting for a response, with the added benefit of keeping the forums less cluttered.

Hope that helps.

---

### Post by lapsey on 2006-06-17
google earth is available for linux, and i'll assume the OP is referring to that.



here is a howto: [http://ubuntuforums.org/showthread.php?t=195335](http://ubuntuforums.org/showthread.php?t=195335)

---

### Post by saltscar on 2006-06-17
Many thanks all.  It was in fact the Linux version I had downloaded.  I did look for any help in the forums that might let me do the job, to no avail - hence my post.

---

### Post by 5-HT on 2006-06-17
[quote=saltscar]Many thanks all.  It was in fact the Linux version I had downloaded.  I did look for any help in the forums that might let me do the job, to no avail - hence my post.[/quote]

Hope you get it running!
Post back if you have any problems.

---

### Post by Frank Golden on 2006-06-17
Hi Saltscar,
    aysiu has posted a script he wrote to make install of GoogleEarthLinux 4.0
BETA easier. See link below

[http://www.ubuntuforums.org/showthread.php?t=195767&page=3](http://www.ubuntuforums.org/showthread.php?t=195767&page=3)

the first line of code reads gedit instalge it should read gedit installge.
You need to sudo gedit installge. I installed on my Acer Aspire 5672WLMi
notebook with ATi Radeon x1400 video proc. Works great.
After install look in application menu under internet and you should find a shortcut for GE there. Right click and choose make desktop shortcut.
Hats off to Google for making GE for linux and for making install relatively 
easy. Though not much on their site about Linux install. 
Good luck. If you have problems feel free to ask for help.
BTW, See you are a Breezy user GE is supposed to be supported in Breezy but I haven't seen where it is supported in Dapper, but it works great on my Dapper install.

---

### Post by saltscar on 2006-06-18
Thanks for this Frank.  I have in fact upgraded to Dapper (personal details now amended), and GE works a treat

---

### Post by Frank Golden on 2006-06-18
[QUOTE=saltscar]Thanks for this Frank.  I have in fact upgraded to Dapper (personal details now amended), and GE works a treat[/QUOTE]
Your welcome. What kind of machine are you using?

---

### Post by saltscar on 2006-06-18
[QUOTE=Frank Golden]Your welcome. What kind of machine are you using?[/QUOTE]
I have a self built machine, AMD Sempron 2600+, 1 Gb RAM, NVIDIA FX5200 and 2 x 80 Gb HD (1 with XP Pro, 1 with Ubuntu 6.06)

---

### Post by Frank Golden on 2006-06-18
[QUOTE=saltscar]I have a self built machine, AMD Sempron 2600+, 1 Gb RAM, NVIDIA FX5200 and 2 x 80 Gb HD (1 with XP Pro, 1 with Ubuntu 6.06)[/QUOTE]
Cool looks like you have everything in place for Google Earth to run well.
If you have been playing around with GE in XP and have any my places
favorites you would like to export to your Linux GE setup, look in
c:\documents and settings\<user>\ application data\Google\GoogleEarth\myplaces.kml and save the myplaces.kml file to a
USB thumb drive or something. If you can see your XP drive from Ubuntu it's 
even easier. Anyway either plugin your thumb drive or make sure you can see
XP while in Ubuntu and open GE linux. go to file>open and navigate to the
myplaces.kml file on your thumb drive or to location above on your XP
machine. Open file and when you close GE a dialog box will ask you if you want to make the temporary myplaces.kml file you just opened permanent.
Choose yes. Enjoy.

---

