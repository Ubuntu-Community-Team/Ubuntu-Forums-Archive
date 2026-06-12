---
title: "Driver (nv/nouveau) and other details on getting 14.04 on G4 iMac?"
date: 2014-04-05
forum: Apple Hardware Users
---

### Post by este.el.paz on 2014-04-05
Folks:

I did read the PPC Known issues pages yesterday, and looked at the other PPC stuff, and I saw that for 14.04 even the radeon driver needs some, what?  KMS?  So, as I posted with the Lubuntu email list and on the old "Testers wanted for 12.04" thread I did try to boot the LiveDVD of a daily build of Lubun 14.04 from 3/28 on my G4 iBook w/radeon card & iMac with nvidia card.  I had not read the known issues at that time and traditionally everything has worked on my iBook, but getting something going on the iMac has been hard.

I got to a low res screen on the iBook, and some apps were clear, some not . . . so the known issue posting about the radeonfb kms stuff in the boot window should probably take care of that.  I then tried the iMac with the video=ofonly and got to the black screen that was the issue over a year ago.  Yesterday I read the PPC wiki, saw the radeon stuff, but didn't see anything about whether or not the "nv" driver will work with 14.04.  So, I tried to boot the livedvd again on the iMac and couldn't remember what we used before as boot parameters so I just typed from memory "live nouveau.nomodeset" . . . and surprisingly I got the splash window and then after several minutes of optical drive grinding away, there was an error about the "nouveau" . . . but I actually  got into the low res GUI . . . !!!!!  So, if someone could remind me what else I'm supposed to type in boot params that would be kind.  I tried to follow rsavages suggestions about switching to single user and turning off the video and then typing "modprobe nvidiafb" into the blank screen; which I did a long while back, but that was not successful . . . I didn't reboot but tried the other one, rividiafb???? but did not get back from the black screen.

However, seeing that perhaps 14.04 might actually work on the iMac, now my question is whether the "nv" driver can still be retro-installed to work with 14.04?  Seemed like in some of the recent upgrades people were saying it is "no longer available"????  And, seems like a custom or individual xorg.conf file is needed for the iMac, as well as now for the radeon card machines (judging from rsavages last post on his Tester thread) . . . my second question is whether the xorg.conf file I have now on my iMac (from the old poster str8bs, no longer posting here) . . . will work with 14.04?

e.e.p.

---

### Post by este.el.paz on 2014-04-05
Following up on my own question . . . a further question is on the feasibility of just editing the sources list to "trusty" to do the upgrade from 12.04 to 14.04?  Would that cleanly do the upgrade or would that just make a mess and easier to do a clean install?  

Question is if the sources list method would maintain the presently retro-installed version of the nv driver, as well as the xorg.conf file . . . and just upgrade the file system to the 14.04, etc?  Or, would I have to re-compile the nv driver after the 14.04 fresh install . . . and make any changes needed to the xorg.conf to deal with 14.04?

e.e.p.

---

### Post by este.el.paz on 2014-04-08
[http://ubuntuforums.org/showthread.php?t=2090462](http://ubuntuforums.org/showthread.php?t=2090462)

Latest waffle update:

Trying to get a higher resolution GUI in the LiveDVD, so far I can get into a low res screen using ```
live nouveau.modeset=0
``` and when I try to follow the "What to do with no GUI" commands to try to switch to the nvidia fb . . . I can get the screen to go black, but when typing the "modprobe nvidiafb" commands the screen does not recover and I have to shut down the computer.  I've tried this several times, even getting into the "single" user is hit or miss, requiring about 3 tries before it worked.  Perhaps this is because this is the 3/28 daily build and we've already moved on??

Next time I'll flip over to the iBook and see if the "radeonfb" stuff works with it to get into a better class of resolution.

e.e.p.

---

### Post by este.el.paz on 2014-04-15
et al:

Latest update on the tesing for 14.04 on G4 iMac & iBook . . . the good news is that using the "live video=radeonfb:1024x768-32" I was able to boot the iBook into a clean GUI using the LiveDVD.  However, the saga continues in trying to get beyond the low res GUI when booting the same DVD in the iMac; multiple attempts to get the "nvidiafb" driver to work, and/or get it into a higher resolution screen have not been successful.  As I reported above I can get into the fuzzy GUI and if I'm familiar with the layout I can "read" well enough, e.g, I was able to open the LXTerminal, run "sudo lshw" and send it to myself as an email . . . and it was clear when I rebooted back into OSX, or now I'm using Xu 12.04 to type this post . . . .  So, perhaps it's possible to get 14.04 running on the iMac, or perhaps drivers are not compatible . . . on the flip side it does look like the iBook might work as a test mule for an update . . . which I might be able to do by editing sources.list, or reading again the "software updater" option to "upgrade to newer system" . . . .  

Then question is if I would try the same method on the iMac whether the nv driver I've got set up on the xorg.conf file would run 14.04 as well as it is doing with 12.04?  Time will only tell . . . .

e.e.p.

---

### Post by abtabt on 2014-04-15
hei if you use only  live-nosplash at boot

i get a better desktop like menu and lxterminal and
i use usb to store logs etc

---

### Post by este.el.paz on 2014-04-17
> **abtabt said:**
> hei if you use only  live-nosplash at boot

i get a better desktop like menu and lxterminal and
i use usb to store logs etc

@abtabt:

So far have not been able to replicate any of these boot params to successfully get to a higher resolution screen on my iMac . . . booting with "live nosplash" . . . ugh, seeing now that you have a hyphen between them, I guess I'll have to try that again . . . .  But "live nosplash" got me to the thin color field across the top of a black field.

But, same thing with the "live video=offb: off nomodeset single" . . . and then toggling the F1 & F7 keys . . . gets me to black screen and then I enter the modprobe nvidiafb etc etc . . . I still get "cannot request PCI regions" as the error. Don't know if I'm supposed to type "lubuntu" ***before**** I enter the "modprobe" line???  When the CLI comes back on after I hit return it is showing the CLI w/ ~# after lubuntu, so I think it's super user already??  Anyway, so far not working like it did when I went through this for 12.04 to nv, etc . . . .

Perhaps I'll wait until the final release version comes out in a bit and try again . . . so far this is only working on the iBook using radeonfb . . . .

e.e.p.

---

### Post by abtabt on 2014-04-17
> **este.el.paz said:**
> @abtabt:

So far have not been able to replicate any of these boot params to successfully get to a higher resolution screen on my iMac . . . booting with "live nosplash" . . . ugh, seeing now that you have a hyphen between them, I guess I'll have to try that again . . . .  But "live nosplash" got me to the thin color field across the top of a black field.
e.e.p.

yes thats tru but the text is good and you can read and use pcmanfm etc and you see the boot message its  better then black screen 
and the last show tty1 so tty1 and tty7 is the key 

> **este.el.paz said:**
> @abtabt:
But, same thing with the "live video=offb: off nomodeset single" . . . and then toggling the F1 & F7 keys . . . gets me to black screen and then I enter the modprobe nvidiafb etc etc . . . I still get "cannot request PCI regions" as the error. Don't know if I'm supposed to type "lubuntu" ***before**** I enter the "modprobe" line???  When the CLI comes back on after I hit return it is showing the CLI w/ ~# after lubuntu, so I think it's super user already??  Anyway, so far not working like it did when I went through this for 12.04 to nv, etc . . . .

Perhaps I'll wait until the final release version comes out in a bit and try again . . . so far this is only working on the iBook using radeonfb . . . .

e.e.p.

to get  good  GUI 

is         live video=offb:off nomodeset single    

and then   modprobe nvidiafb mode_option=1024x768-16    when cd stops 

change to tty7    modprobe nvidiafb mode_option=1024x768-16   enter key tvice
change to tty1    modprobe nvidiafb mode_option=1024x768-16    enter key tvice
etc then when you get promt 

do lshw 
*-display
             description: VGA compatible controller
             product: NV11 [GeForce2 MX/MX 400]
             vendor: NVIDIA Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: b2
             width: 32 bits
             clock: 66MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=nvidiafb latency=248 maxlatency=1 mingnt=5
             resources: irq:48 memory:91000000-91ffffff memory:98000000-9fffffff memory:90000000-9000ffff
 
if you get driver=nvidiafb  you can get  16 or 24 bit        if you get  driver=nouveau you get only 8 bit uggly GUI

or [    55.897] (II) FBDEV(0): hardware: NV11 (video memory: 32768kB)   in  nano /var/log/Xorg.0.log   its good 32768 

then you can put xorg.conf.txt  in /etc/X11  rename to xorg.conf and get good GUI

i have done two installs with this trick and a lot of live cd boots on this ilamp

---

### Post by este.el.paz on 2014-04-17
> **abtabt said:**
> yes thats tru but the text is good and you can read and use pcmanfm etc and you see the boot message its  better then black screen 
and the last show tty1 so tty1 and tty7 is the key 
to get  good  GUI 

is         live video=offb:off nomodeset single    

and then   modprobe nvidiafb mode_option=1024x768-16    when cd stops 

change to tty7    modprobe nvidiafb mode_option=1024x768-16   enter key tvice
change to tty1    modprobe nvidiafb mode_option=1024x768-16    enter key tvice
etc then when you get promt 

do lshw 

i have done two installs with this trick and a lot of live cd boots on this ilamp

@abtabt:

OK, this spells it out in more detail . . . I saw you said "Hit enter each time" . . . but I didn't realize that you were doing all three "modprobes" . . . with the tty7 & tty1 . . . so this would definitely be different than what I've been doing . . . again it'll be maybe a day before I'm back with the iMac . . . and then I'll post the new "lshw" file.

e.e.p.

edit1:  Did try this multiple "modprobe" technique this morning, a number of times . . . each time brought different result . . . sometimes showing lubuntu # after first modprobe, sometimes after the tty7 . . . but ran through it several times and brought me to the same grainy GUI screen.  Ran "lshw" again, and display did not show any change from last time.  Maybe I'll try again tomorrow, or maybe I'll burn the "final release" and try that one . . . .  I tried.

---

### Post by este.el.paz on 2014-04-20
Latest update: [waffle alert!! Oh, wrong thread, cancel the waffle alert]:

Downloaded the Lubun 14.04 LTS .iso on Friday and burned it to DVD, it's oversize for CD . . . and tried the "live-nosplash" command . . . that took me to a green-black screen . . . rebooted and ran the "abtabt" suggestions for the "nvidifb modprobe" . . . several times, still repeating the same commands brings different results each time . . . but, none of them will bring a revived and higher resolution GUI.  

Sort of perplexed . . . perhaps when I get a free moment I'll try just running one of the tty option lines and see what happens . . . or, might try making a usb boot from the iso, which I can do from my LM16 system--however I thought I saw on the wiki that it's only computers made ****after**** 2004 that can be booted from USB drive??  My iMac is from earlier than that . . . .

So far doesn't seem like the gamble to do the install on the iMac is worth the time, but might be do-able on my '04 iBook . . . .

e.e.p.

---

