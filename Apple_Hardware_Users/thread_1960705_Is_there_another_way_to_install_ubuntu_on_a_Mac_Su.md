---
title: "Is there another way to install ubuntu on a Mac? Suggestions welcome"
date: 2012-04-17
forum: Apple Hardware Users
---

### Post by fysicsandpholds on 2012-04-17
Hey Guys,

Edit*: I want to stress that I have installed rEFIt and done all of the usual steps. I am pretty sure this is an error and not just my fault since I was able to do it effortlessly in the past.

So I've been trying really hard to install Ubuntu on my intel iMac alongside OS X. I have tried to install multiple linux versions and even versions of Ubuntu both using CDs and USB. Here is the post related to that
[http://ubuntuforums.org/showthread.php?t=1927883](http://ubuntuforums.org/showthread.php?t=1927883)

However nothing has worked. I was wondering if anyone knew of any alternatives to installing Ubuntu on a mac using USB or CD. 
Note: I'm not sure whether the problem I have been having is a hardware or software related issue, if it's a software issue, then a different installation method probably won't help. 
When trying the USB install, rEFIt does tell me that booting a legacy os from an external drive is not well-supported when it fails. Also my built in CD drive is broken so I have been using an external CD drive. Perhaps the problem is they both require booting drives through the USB port (my external CD drive connects via USB), which for whatever reason isn't supported. 
So I guess figuring out how to get my machine to boot successfully to a usb drive would do the trick.

Sam

---

### Post by gennatolls on 2012-04-18
I have been able to boot USB using rEFIt it usually would show two boot images and I remember one didn't work. Nothing against rEFIt, but I didn't find it as elegant as I thought it could be (you know to go with the mac theme) I upgraded to Lion so not sure if this works in SL but it used to. Used to, you could create a partition with bootcamp then boot a live cd. I reinstalled ubuntu with a fully update lion mac and i did the bootcamp method, however I had to pop a winblows disk in to get it to continue then on reboot ejected and put the ubuntu disk in. (sneaky). This way all you do is hold Option key on boot and you select Windows boot drive and into ubuntu you go. This method was easier on the eye for me. I know mac doesn't support booting usb if it doesn't have os x on it (you need rEFIt to do this) Good luck

---

### Post by fysicsandpholds on 2012-04-18
> **gennatolls said:**
> I have been able to boot USB using rEFIt it usually would show two boot images and I remember one didn't work. Nothing against rEFIt, but I didn't find it as elegant as I thought it could be (you know to go with the mac theme) I upgraded to Lion so not sure if this works in SL but it used to. Used to, you could create a partition with bootcamp then boot a live cd. I reinstalled ubuntu with a fully update lion mac and i did the bootcamp method, however I had to pop a winblows disk in to get it to continue then on reboot ejected and put the ubuntu disk in. (sneaky). This way all you do is hold Option key on boot and you select Windows boot drive and into ubuntu you go. This method was easier on the eye for me. I know mac doesn't support booting usb if it doesn't have os x on it (you need rEFIt to do this) Good luck

Thanks, but I have done all of this. I have even tried installing Windows using bootcamp (it didn't work either)
To re-iterate, I'm not looking for help on doing a standard installation method on Mac. I know how to do that, however, for whatever reason, the standard installation methods won't work any more.

Thank you for trying though

Sam

---

### Post by markbl on 2012-04-18
Run Ubuntu full screen in Virtualbox as I do on my 2011 MBA. Triple finger sideways swipe between OS X and Ubuntu. 3D video so can use Unity or Gnome-shell etc. Everything works great, no stuffing around.

---

### Post by gennatolls on 2012-04-18
Sounds like your partitions may be messed up or something similar. Have you ever dual booted your mac? Now that we know you're bootcamp windows install failed it will help. I have had a similar problem. I had hell installing Arch Linux on my macbook pro. Almost identical to what you have described. Disk Utility under Mac is garbage. If you've ever messed with your partitions using it (make a partition and shrink it etc), this caused mine to be messed up. I'm no expert with partitions and the really specific stuff about them so maybe someone will chime in with a different idea. What finally fixed mine and allowed me to install Arch was to backup OS x then wipe the drive clean and do a clean install of mac and create a new partition for ubuntu. This was all done with Bootcamp. Bypassing rEFIt.

What OS X are you using? I encountered this bug under Lion (it still has many bugs) but I never had an issue under SL. I installed windows 4-5 times and ubuntu and backtrack as well, most of the time as a triple boot (in SL). In Lion, what i noticed caused my install to fail was when i created a partition with Bootcamp then later removed it with Disk Utility instead of Bootcamp. I feel your frustration, I worked at if for 10 days or so and finally said the hell with Mac and erased and reinstalled and lucked out with fixing my problem in the process. 

Best of luck

ETA: I have crashed my mac 3 times now with Disk Utility under lion :shock:

---

### Post by gennatolls on 2012-04-18
I noticed other people have had trouble installing Ubuntu 11.10 on mac here [http://ubuntuforums.org/showthread.php?t=1927883](http://ubuntuforums.org/showthread.php?t=1927883)

I didn't have the mentioned troubles running 11.10 but I am running 12.04 now.

I highly recommend 12.04, it is very stable and brings tremendous improvements for mac support. I've been running it since Alpha 1 as my day to day pc and have had no issues.

---

