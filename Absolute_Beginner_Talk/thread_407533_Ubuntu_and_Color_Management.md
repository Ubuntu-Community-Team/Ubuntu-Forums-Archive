---
title: "Ubuntu and Color Management"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by claude05 on 2007-04-12
Hello all, 

After 9 months of being away from Ubuntu (due to work etc) I am finally ready to give it another go. I'm excited about fiesty fawn and can't wait to give it a go, however,  I have a quick question regarding color management before I take the plunge. 
I work mostly in photography and my LCD monitor has been calibrated by using a spyder2 color calibration unit. While I will still be mostly working on my photos in windows, I'd like to have ubuntu calibrated exactly the same should I need it to be. How can I do this? I know the Spyder2 doesn't work in linux so what are my options? And simply, can I just make a copy of the ICC profle created in windows after calibration and use it in the ubuntu environment?

---

### Post by Obor on 2007-04-12
Look in[ this thread]("http://ubuntuforums.org/showthread.php?t=339990&page=6") (post #54) Those guys might give you more details.

---

### Post by claude05 on 2007-04-12
> **Obor said:**
> Look in[ this thread]("http://ubuntuforums.org/showthread.php?t=339990&page=6") (post #54) Those guys might give you more details.

Thanks for the reply, however there really wasn't any pertinent information in that thread.

---

### Post by Shay Stephens on 2007-04-12
> **claude05 said:**
> Thanks for the reply, however there really wasn't any pertinent information in that thread.

Sure there was! hehehe
What program are you using to edit the photos?  If it is color aware, you can load your windows profile into it.

Something new I have come across in the weeks since that post, is that the project argyle is able to generate profiles:
[http://www.argyllcms.com/](http://www.argyllcms.com/)

I am researching this as I am going to need a profile eventually, right now I don't need one.  What I hear is the next version of argyle is going to have support for the gretag eye1 colorimeter  And if you can't wait, then to try to find an X-Rite DTP94 colorimeter which is currently supported.  I have been poking around looking for a link to that colorimeter, but have not come across one yet.  If you find one, let me know.

---

### Post by adamklempner on 2007-04-12
I don't know much about this, but wikipedia has a fair amount of info.  Here is a snipit from:

[http://en.wikipedia.org/wiki/Linux_color_management](http://en.wikipedia.org/wiki/Linux_color_management)

> ICC profiles are cross-platform and can thus be created on other operating systems and used under Linux. Monitor profiles, however, require some additional attention. Since a monitor profile depends both on the monitor itself and on the video card, a monitor profile should only be used with the same monitor and video card with which it was created. The monitor settings should not be adjusted after creating the profile. In addition, since most calibration software use LUT adjustments during calibration, the corresponding LUTs must be loaded every time the X server is started (e.g. with every graphical login).

For users of certain colorimeters such as Xrite DTP-94 and Xrite DTP-92 that come in Monaco OPTIX and ColorEyes bundles, there is an option for calibrating their monitors on Linux. For native Linux monitor calibration, they would need to install Argyll Color Management System (also available from Softpedia). Argyll CMS is a set of command-line utilities. Its dispcal module will let you natively calibrate a monitor under Linux.

To avoid using command-line utilities, or if a colorimeter is unsupported by Argyll CMS (such as Spyder2 or EyeOne), a profile created under Windows or Mac OS X can be used under Linux. Normally the profile has to be created on the same machine with the same monitor settings.

---

### Post by zorglb on 2007-04-27
Hi,

I'm usually on the french ubuntu forum, but I think this news is very important to share for linux photographers :

As the argyll main site doesn't says (not updated), the 0.70 beta version of Argyll supports now the Gretag eye one :

It directly supports the following color measurement instruments:
 
 X-Rite:
     DTP20 Pulse                                - "swipe" type reflective spectrometer, that can be used untethered.
     DTP22 Digital Swatchbook            - spot type reflective spectrometer.
     DTP41                                         - spot and strip reading reflective spectrometer.
     DTP41T                                       - spot and strip reading reflective/tranmissive spectrometer.
     DTP51                                         - strip reading reflective colorimeter.
     DTP92                                         - CRT display colorimeter.
     DTP94 Optix                                - display colorimeter.
 
 Gretag-Macbeth:
     Spectrolino                                   - spot reflective/emissive spectrometer
     SpectroScan                                 - spot reflective/emissive, XY table reflective spectrometer  
     SpectroScanT                               - spot reflective/emissive/transmissive, XY table reflective spectrometer
     Eye-One Pro                                 - spot and "swipe" reflective/emissive spectrometer
     Eye-One Display 1/2                      - display colorimeter
 
 Other:
     Colorimètre HCFR                          - display colorimeter

Look here for download.
[http://www.freelists.org/archives/argyllcms/04-2007/msg00006.html](http://www.freelists.org/archives/argyllcms/04-2007/msg00006.html)

Unfortunately, I couldn't figure yet how to make it working...

The dispcal utility of the bin version returns me an error :
(dispcal is the utility the argyll suite uses for screen calibration)

dispcal: 1: Syntax error: "(" unexpected

The compilation with the sources fails too. (it uses Jam for compiling, available in the repositories and by the jam website).

If someone is interested in testing it and seeing if he can make it working.... ;)

Perhaps in a close future we could have a .deb in repositories for screen calibration ?
 
And no more needs of windows for the "artistgeeks" linux photographers !

---

### Post by loud_tiger on 2007-05-31
i got this to work. i'm using the eye-one display 2, under feisty fawn. 

wow, i never knew ubuntu had such a... beige/orange theme. it seems like my laptop LCD was leaning heavily toward the blue side. 

i kept getting an error "conjgrad failed", but after starting with the lower quality calibration, and running it again at the medium level, it worked. i think the curves with the default monitor colors were just too far off for it to calibrate correctly.

thanks to everyone in this forum... without it i wouldn't have even know this software existed!

---

### Post by Shay Stephens on 2007-05-31
> **loud_tiger said:**
> i got this to work. i'm using the eye-one display 2, under feisty fawn. 

wow, i never knew ubuntu had such a... beige/orange theme. it seems like my laptop LCD was leaning heavily toward the blue side. 

i kept getting an error "conjgrad failed", but after starting with the lower quality calibration, and running it again at the medium level, it worked. i think the curves with the default monitor colors were just too far off for it to calibrate correctly.

thanks to everyone in this forum... without it i wouldn't have even know this software existed!

Sweet that is great to hear!!!  What did you do to get it working?

---

### Post by tvds on 2007-08-20
So... anyone got the spyder2 working under ubuntu.

I just bought it to use under Windows Vista... but yesterday I shot my Vista PC and installed Ubuntu.

---

### Post by netengineer on 2007-09-28
I would also like to get this working under Ubuntu..... I just got a Spyder2 and it would be great if I didn't have to use Windows (tm) to get this done.

---

### Post by VHans on 2008-01-01
> **loud_tiger said:**
> i got this to work. i'm using the eye-one display 2, under feisty fawn. 

wow, i never knew ubuntu had such a... beige/orange theme. it seems like my laptop LCD was leaning heavily toward the blue side. 

i kept getting an error "conjgrad failed", but after starting with the lower quality calibration, and running it again at the medium level, it worked. i think the curves with the default monitor colors were just too far off for it to calibrate correctly.

thanks to everyone in this forum... without it i wouldn't have even know this software existed!

Can you explain how you got dispcal to work? I always get an error regarding libXss.so.1 not found.

---

### Post by rvdean on 2008-02-27
I have access to a Spyder2 Pro and wondered if this could be made to work with Ubuntu
On searching the internet I found a tutorial on how to get Spyder2 working but no information on the 
pro version . Has anybody had experience getting the pro version going ?

---

