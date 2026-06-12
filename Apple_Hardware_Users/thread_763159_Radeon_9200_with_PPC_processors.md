---
title: "Radeon 9200 with PPC processors?"
date: 2008-04-22
forum: Apple Hardware Users
---

### Post by nageekdoog on 2008-04-22
This is a frustrating thing and PPC seems to keep screwing me as far as compatability goes sooo I hope I can solve this hehe.  

I'm running a PPC mac mini. I'm trying to get a resolution higher than 1024x768 on the ati radeon 9200 that came pre-installed with the machine. I've read a good amount of tutorials and forums that have told me that fglxr isn't compatible with PPC processors and I haven't really found anything that has told me that I can definitely edit my video drivers with my current setup. 

I've edited my xorg.conf, gdm.conf and gdm.conf-custom in different ways according to online directions but to no avail. I just want 1280x1024 on my monitor (its native resolution). If anyone knows how to combat this problem, please please let me know.

Also if you want to see any of the files listed above, I'll post them. 

Thanks so much in advance.

---

### Post by stream303 on 2008-04-22
Definitely check this out from the ppc archives about the mac mini and radeon:

[http://ubuntuforums.org/showthread.php?t=756916](http://ubuntuforums.org/showthread.php?t=756916)

Are you running Hardy, or an earlier version?

Configuring things in Hardy are going to be a bit different...

---

### Post by slacka-vt on 2008-04-22
I'm using an ATI Radeon 9600 on a PPC and I use the generic ati driver in Hardy.
Shouldn't that work for you as well ?
They really have changed the configuration quite a bit.

I'm not sure what release you are running but you can try:

```
sudo aptitude install xserver-xorg-driver-ati
```

~s

---

### Post by hqconverter on 2008-10-22
Share Dvd tools with Mac users!
Here is the reason why I want to share with Mac users:
1) Cost/Performance: Everybody wants to gain more with less money. 
2) Speed: Nobody wants to waste too much time waiting. 
3) Profile: Of course we want our software can convert all kinds of video formats. 
4) Personal Demands: For example, someone just wants to convert part of the DVD video, or others want the special output video format like PSP compliant forms and etc. 
5) Easy to use: we want to make things easy. 
[DVD Creator for Mac](http://www.dvdcreatormac.com/),
[DVD Burner for Mac ](http://www.dvdcreatormac.com/dvd_burner_for_mac.htm),
[DVD Copy for Mac](http://www.dvdcreatormac.com/dvd_copy_for_mac.htm),
[DVD Ripper for Mac](http://www.dvdcreatormac.com/dvd_ripper_for_mac.htm),
[AVI to DVD for Mac](http://www.dvdcreatormac.com/avi_to_dvd_for_mac.htm),
[DivX to DVD Converter for Mac](http://www.dvdcreatormac.com/divx_to_dvd_converter_for_mac.htm)
[DVD Decryption for Mac](http://www.dvdcreatormac.com/dvd_decryption_for_mac.htm),
[Clone DVD Mac](http://www.dvdcreatormac.com/clone_dvd_mac.htm),
[VOB Converter for Mac](http://www.dvdcreatormac.com/vob_converter_for_mac.htm)

---

