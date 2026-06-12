---
title: "Logitech Webcam Crash Problem"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by richbarna on 2006-05-17
I don't know if anyone has one of these, but I have tried and tried to get it working to no avail.
It's a cheapo standard USB webcam and whenever I try to configure it, my system locks up.
I have downloaded webcam software from the repo's and read forum posts and it still locks up my pc.
It's only for messenger "kopete" and maybe skype later, and to be honest not super important, but I would like to solve the problem.

If anyone has ANY suggestions, they would be gratefully apreciated.
Thanks.

Oh, by the way, I have an Nvidia GeForce 5700 Fx 128 Mb Graphics card, 512 Mb RAM and no other problems with DVD, TV card or graphics in general.

---

### Post by woedend on 2006-05-17
what exact camera is it?  does it have  a specific model name?  Download camorama from repo's...does it work there?
please have it plugged in and post output of the command lsusb.
Ive spent the past week working on the quickcam messenger.  Ill do what I can if you have one.

---

### Post by richbarna on 2006-05-18
Hi woedend,
It's a logitech quickcam express. Picture Details :-
[http://computing.kelkoo.co.uk/b/a/sbs/116901/14013107.html]("http://computing.kelkoo.co.uk/b/a/sbs/116901/14013107.html")

I have tried all the software from the Repo's :-
came, camorama, camstream, gqcam, webcam, webcamd
Including the ov511-source USB only chipset.

lsusb output :-
> Bus 005 Device 004: ID 0dda:2005 Integrated Circuit Solution, Inc.
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 046d:0920 Logitech, Inc. QuickCam Express
Bus 001 Device 001: ID 0000:0000

It knows that the webcam is there, but if any program tries to connect to it, the whole system locks up (frustrating when you need to try and trace and solve).

It's quite funny really, I spend a lot of time walking "newbies" through console commands and graphics problems, and now I get shafted by a cheap 'ol webcam LOL.

Edit: Just trying the driver from sourceforge :-
[http://sourceforge.net/project/showfiles.php?group_id=12924&package_id=86447&release_id=415065]("http://sourceforge.net/project/showfiles.php?group_id=12924&package_id=86447&release_id=415065")

---

### Post by woedend on 2006-05-18
i understand that completely...its frustrating.  These little things make you wish for windows sometimes!
which exact driver are you using right now?
Your exact model should be covered under spca5xx..is that module loading?

---

### Post by richbarna on 2006-05-18
Source forge no go (kernel-source too new)
spca5xx no go       (kernel-source too old )
Hmm, I 've updated from the repo and got source-code 2.6.11-7
I got this on spca5xx install :-
> make: *** /lib/modules/2.6.12-10-386/build: No such file or directory.  Stop.
make: *** [default] Error 2

What do you think?
Got the driver here :-
[http://mxhaard.free.fr/download.html]("http://mxhaard.free.fr/download.html")

---

### Post by richbarna on 2006-05-18
Trying "arnieboy's" guide from here :-
[http://www.ubuntuforums.org/archive/index.php/t-75284.html]("http://www.ubuntuforums.org/archive/index.php/t-75284.html")

---

### Post by woedend on 2006-05-18
this is odd - are you using a ubuntu kernel?  It shouldn't matter which version you are using, as long as it's 2.6.x(and yours is i'm assuming?
Start by downloading your kernel headers. The entire source definetely isn't needed(you need build-essential package and in your case linux-headers-386, which should metapackage to make sure you ahve the right ones installed...but double check this in synaptic- you should have linux-headers-2.6.12-10 and 2.6.12-10-386 installed if you are using kernel 2.6.12-10!)
Then - It was simple for me, you download the spca5xx tar.gz file from the website you showed me.  Uncompress it into your home directory, for example /home/yourusername/spca5xx
cd to that directory, then just run
sudo make install

let me know if that still gives you errors, i think we arent on the same page here.

---

### Post by woedend on 2006-05-18
actually...i just read arnieboy's post that you pointed me to...it looks like he's got it right :)..let me know if his works for you please.
It looks like he's having you remove the original drivers and replace them with the new one.

---

### Post by richbarna on 2006-05-18
seems okay now, strange?
I checked my headers and code and they are 2.6.12-10 ?
So i don't know what the driver was talking about,
Anyhow got the spca5xx, went through the usual motions, all fine.
uninstalled and reinstalled camorama (just in case ;)
Hit camorama aaaaand can't find video device (it's actually pointed at the digital in socket) sooooo
Where IS the camorama config ? so that I can tell it to use the USB cam ?
I tried caminf, camorama-conf, etc. no luck.
God I feel so stupid, this really takes the p*ss. LOL

---

### Post by woedend on 2006-05-18
Tis a good question that I haven't figured out yet.  Let me ask - does the webcam work anywhere else other than camorama(ie amsn, other webcam programs?).  does it list the device name it cant find?  It gives me that error when it's either not plugged in or I was using the wrong driver.  Sometimes just doing 
sudo modprobe spca5xx followed by sudo modprobe videodev  fixes it.  But if the problem is related solely to camorama i'll see if  I can dig up some config info.

---

### Post by richbarna on 2006-05-18
Okay, this is what's happening, Driver installed and working, all "viewer" software go to my Hauppage TV card first (need to change that).
When i click the pulldown for devices (any program, camorama, camstream etc.) The webcam is there, so I select it, and that's when the system locks up. Only solution is to power off.
I need to be able to set the webcam as the default device somehow.
I can't do it from the viewer programs as they freeze as soon as i touch them.
One solution is to tear out the TV card (which was a pig to get configured with nVidia etc) so not really an option at the moment, more of a last resort.
Could do with command line :- 
sudo "Hey Computer ! Don't use the tv card for anything except the bloody TV"
sudo "now go and find the web cam and work nicely you muppet !"
 I don't suppose you know how to translate that into BASH do you ? :)

---

### Post by woedend on 2006-05-18
short of messing with the symlinks in /dev/ (the video/video0), I really have no idea!  frustrating enough.  But It naturally shouldn't be freezing at all - do you know for sure that if webcam was default device that it would work perfectly?  That really still seems like a driver issue.

---

### Post by richbarna on 2006-05-18
> do you know for sure that if webcam was default device that it would work perfectly? That really still seems like a driver issue.

No, not really, just clutching at straws. I'm going to have a google around and see if i can find a way to reset the file that all these programs go to to search for video input devices. I need to first see if I can get rid of the TV card link. Then come back to the webcam and see if it's a hardware or driver issue.
Maybe if there was a messed up previous install, some of the data still exists and therefore causing problems for the new driver, i really don't know.
Thanks for taking the time to help, much appreciated :)
I,ll post back if I get a result.

---

