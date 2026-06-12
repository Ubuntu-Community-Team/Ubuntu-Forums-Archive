---
title: "iMac 10,1 fan control with SSD &amp; HDD (no optical drive)"
date: 2014-05-03
forum: Apple Hardware Users
---

### Post by nobodyfamous on 2014-05-03
I can't seem to get anywhere with this.  Running OS X I am using "Macs Fan Control", it also worked in Windows 7 (windows now gone, replaced by Ubuntu 14.04!!!)

My iMac has the supper drive replaced with an SSD, which is where OS X is installed. And a 1T in the "normal" HDD bay.  That is where Ubuntu is installed.

A problem I had in OS X with other fan control software is that they would read the temperature of the SSD, because that was the OS disk, and as it climbed they would speed up the HDD bay fan, not the optical drive bay fan, where the SSd is.  (SSD is in Optical drive bay - HDD is in the HDD bay)

I think this is what is happening in Ubuntu.  Is there a file/setting I can edit to swap the sensor/fan?

lm-sensors is installed, and gives readings with sensors.

---

### Post by este.el.paz on 2014-05-05
@nobody:

I think this is also going to be my next project, to get 14.04 to run cooler in my MBPro . . . I believe there are some other threads around on this topic here in Apple users subsection--there was some mention of "macfanctrl" . . . or something like that, but when I looked recently I couldn't find it.  I thought in the PPCKnown issues there ws some data on how to set the fans to come on at like 5 degrees earlier, etc . . . I was hoping that 14.04 would handle this "fan control" issue in the kernel, and it seemed like it was, but when I actually checked the temps, it was warmer . . . so, in the coming weeks I'll be trying to find the way to fix it as well . . . .

First thing, check for other recent threads and the FAQ/known issues wikis, then you'd have to figure out which of the regular sensors are handling which of your HDs . . . and then try to tweak the settings of them, etc.

e.e.p.

---

### Post by nobodyfamous on 2014-05-05
macfanctrl seems to do nothing for the iMac.  As for sensor names, this proves helpful [http://www.parhelia.ch/blog/statics/k3_keys.html](http://www.parhelia.ch/blog/statics/k3_keys.html)

If I could just set my fans to run at a set rpm I would be happy for now. . . I just don't know where the fan speeds are handled.

---

### Post by este.el.paz on 2014-05-05
[http://ubuntuforums.org/showthread.php?t=2212785](http://ubuntuforums.org/showthread.php?t=2212785)

This thread seems to have some detailed instruction on the "10.1" computer . . . did you see it?

e.e.p.

---

### Post by nobodyfamous on 2014-05-06
I have looked at those threads already.  Fan is still running 6283 rpm :(

it is fan2 labelled HDD.  Using "Disks" I can get the SMART data temps for both the HDD and SSD, they are fine.
i 
It appears to me that the HHD fan (fan2) is infact cooling the HDD as it's temp is way down.  If I use the command as root ```
echo 1200 > /sys/devices/platform/applesmc.768/fan2_output
``` the fan will slow down for less then a second, but speeds right up again

---

### Post by este.el.paz on 2014-05-06
@nobodyfamous:

Ah, since you had posted on the other thread about "iMac runs hotter" I made the assumption that the fans weren't running and your problem was heat . . . which is the problem I'm having in my MBPro now running 14.04 at much higher temps than OSX does.

However, I do have this fan running overtime/blasting noisily in my iBook with a Xubun 12.04 partition . . . particularly with several tabs open in a browser and having Thunderbird open . . . which seems to overwhelm its little brain and it literally starts blowing its top. 

I did post a question about it, perhaps a year back . . . if there was a reply to it, it involved the "therm adt 768" ???? module, which 12.04 does have and then fiddling with the script to get the fan to shut off or not start up until certain temps, etc.  At that time I couldn't find anything from Apple showing the recommended temp ranges, and I had no "Temp Monitor" app installed to get some idea of where they wanted the temps to be.  It was beyond my skillset and or time to deal with it, but if you've tried the link to the ppa thingie for "mactel" and installed those tools and it still isn't working, then you might search back for my thread and see if you can make sense of it . . . I know I posted the issue on a couple forums hoping for a simple command string to fix the issue . . . .  There just aren't a whole lot of rainy days in SoCal that I can sit around and fiddle with basic running of the machine problems . . . same thing with 14.04 . . . I do most of my actual computer work in OSX and check into linux for a brief change of scenery due to a number of these mechanical issues dealing with Macs . . . .

e.e.p.

---

### Post by alan26 on 2014-05-13
What temps are you guys getting?

---

### Post by Library Eye on 2014-10-31
This is same issue that still keeps me from running Linux on my secondhand iMac6,1 24" 2.33 Intel Core 2 Duo. Previous owner had a bigger replacement HDD put in when new and I need some way to control via SMART fan status. An easy fix on Snow Leopard and Vista, which are both running on here: 3rd party utilities readily available. Would prefer to run Linux though because seemingly Snow Leopard isn't supported anymore, and neither Snow Leopard nor Vista can actually use all 4GB RAM on here, but I think Linux may be able to via PAE. But, HDD fan runs full speed all the time and I can't stand that. Anyone find any hope of an upcoming possible solution?

---

### Post by este.el.paz on 2014-10-31
> **Library Eye said:**
> This is same issue that still keeps me from running Linux on my secondhand iMac6,1 24" 2.33 Intel Core 2 Duo. Previous owner had a bigger replacement HDD put in when new and I need some way to control via SMART fan status. An easy fix on Snow Leopard and Vista, which are both running on here: 3rd party utilities readily available. Would prefer to run Linux though because seemingly Snow Leopard isn't supported anymore, and neither Snow Leopard nor Vista can actually use all 4GB RAM on here, but I think Linux may be able to via PAE. But, HDD fan runs full speed all the time and I can't stand that. Anyone find any hope of an upcoming possible solution?

@LE:
[http://ubuntuforums.org/showthread.php?t=2222611](http://ubuntuforums.org/showthread.php?t=2222611)

I just went through this process again just a few days ago when my Xubun 14.04 system got corrupted . . . read or look at the "mactel ppa" page . . . I added the "quantal" and "raring" "deb" and "deb-src" versions to my software sources list (GUI in Software manager >edit? or >file or other> Software sources . . . mactel PPA and then "edit URL to "quantal" and "raring" . . . replacing "trusty" . . . .  Then install "applesmc lm-sensors macfanctld coretemp" . . . read through Mike Braxner's instructions . . . carefully.

There are a number of posts where the posters is claiming to not use "macfanctld" . . . up to you.  It does take a bit of study to figure it out . . . as soon as I added these packages the fan started to blow in my MBPro, whereas before it wasn't . . . .  You can adjust when the fan comes on or shuts off, but seems like linux/ubuntu base system doesn't seem to handle the apple system . . . .

e.e.p.

---

### Post by nobodyfamous on 2014-11-01
I have an iMAC, and still no solution.  MBPro's are different.  When I have time I will look through what you linked, but am doubtful it will work.

MBPros = fan does not run
iMac = fan runs full speed ALL THE TIME!

At best, I have had the fans slow for 1/2 second each time software resets the speeds, but the software speed is not being kept, the hardware values (max) keep restoring.

---

### Post by este.el.paz on 2014-11-01
> **nobodyfamous said:**
> I have an iMAC, and still no solution.  MBPro's are different.  When I have time I will look through what you linked, but am doubtful it will work.

MBPros = fan does not run
iMac = fan runs full speed ALL THE TIME!

At best, I have had the fans slow for 1/2 second each time software resets the speeds, but the software speed is not being kept, the hardware values (max) keep restoring.

[http://ubuntuforums.org/showthread.php?t=2212785](http://ubuntuforums.org/showthread.php?t=2212785)

Post #4 from Partisan Entity . . . "This works for my iMac . . . " . . . I believe that thread is another way, different than Mike Braxner's instructions that he gave me . . . .

e.e.p.

---

### Post by Library Eye on 2014-11-05
thanks for reply este.el.paz

I took a quick look at all that, and I may have missed it, but it doesn't look any of it addresses my specific issue. I need to be able to control the HDD's built-in fan, via SMART status. Neither OSX nor Wind-ws can handle this, but for OSX I use this :
[http://exirion.net/ssdfanctrl/](http://exirion.net/ssdfanctrl/)
& under Wind-ws I use this:
[http://www.crystalidea.com/macs-fan-control](http://www.crystalidea.com/macs-fan-control)

But, like I said I haven't had time to read everything in all those posts. If I get a chance to, I will, and I'll try out any likely solution if it looks like there is one and report back with results.

I sure wish there were a relatively easily (and more importantly, surefire) way to get this to work.

thanks again.

---

### Post by este.el.paz on 2014-11-05
@Library Eye:

I can't guarantee it, but, if the fan has a sensor, then more than likely those 4 apps should detect it and offer some adjustment.  But, for this issue I wouldn't think there would be an "easy" one step GUI app . . . that would be free . . . and "surefire" . . . .  It does take some reading and fiddling . . . .

e.e.p.

---

