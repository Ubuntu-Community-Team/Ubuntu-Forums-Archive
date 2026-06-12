---
title: "Ok uBuntu 8.10 on Mac Pro..but now that I fixed it .."
date: 2009-02-02
forum: Apple Hardware Users
---

### Post by fufuntu on 2009-02-02
Hi Everybody ,
it's my first post and I need help from you, Guys. 
 
Here's my Mac:  

  model:	Mac Pro
  model ID:	MacPro2,1
  processor:	Quad-Core Intel Xeon
   processor speed:	3 GHz
   processor nr:	2
 clusters :	8
  Cache L2 (per processor):	8 MB
  Memory:	5 GB
   bus Speed:	1.33 GHz
   Boot ROM Version:	MP21.007F.B08
 SMC Version:	1.15f3

I installed ubuntu 8.10 64 bit on this machine using  rEFIt and **without** using Bootcamp (and I know this is a mistake)..But now  , after a week workin'on it (and during that it was working well) , having set up all system drivers (not all) and everything, when I switch on the Mac, I only get the rEFIt screen with no chance to move the preference for my systems to boot. I only get Osx bootin' after those 15 sec. It's like my keyboard is off during the boot ... And if I restart osX system I only get a blank screen and a dead machine..  
Anyone has an advice for me ?  I just tried on the Italian forum but there were not enough knowledge about rEFIt.( I just looked and posted at the program's site )

Thank you in Advance

---

### Post by cyberdork33 on 2009-02-02
unplug other USB devices

If you cannot use rEFIt, hold the Option Key during startup and you should get the standard Mac Boot chooser. See if OSX is listed there.

---

### Post by fufuntu on 2009-02-03
**No way man**.
 I wish it would be so simple , but when I try to boot holding the opt key , screen stays blanck and the computer is dead. 

What should I do ? First remove rEFIt, or could be something I can fit from terminal? 

I'm worried much by this situation: when I press "c" to boot from live cd, no way , same thing as option key. My ubuntu sistem is like buried into my hardisk, no way to get it at the moment.

And if I will have to repair the start up disc , how will I do without these features ?             [-o<

---

### Post by fufuntu on 2009-02-03
It may be useful, I'm posting the message I left at rEFIt's site : 

"Hi Everybody,
anyone knows about keyboard malfunction at boot choosing? I can visualize
those various systems I installed but my arrow-keys are disabled so I can't
boot in Linux from Osx! 
Bootin' with "c" pressed o "option" leaves my computer freezed, doesn't
boot. I removed rEFIt and installed again , I did the terminal stuff to
enabling it again, my boot choosing is visible again but I can't still
select the system. Please help"


 thanks  cyberdork 33 for the ready answer

---

### Post by pxwpxw on 2009-02-03
> **fufuntu said:**
> It may be useful, I'm posting the message I left at rEFIt's site : 

"Hi Everybody,
anyone knows about keyboard malfunction at boot choosing? I can visualize
those various systems I installed but my arrow-keys are disabled so I can't
boot in Linux from Osx! 
Bootin' with "c" pressed o "option" leaves my computer freezed, doesn't
boot. I removed rEFIt and installed again , I did the terminal stuff to
enabling it again, my boot choosing is visible again but I can't still
select the system. Please help"


 thanks  cyberdork 33 for the ready answer

One last resort when nothing makes much sense is to do a SMC reset, there should be info for your Mac on apple.com support. It can be as simple as shutting down, disconnect ALL cables of any kind, leave for 15 minutes, reconnect and restart - but it varies.

---

### Post by cyberdork33 on 2009-02-03
> **pxwpxw said:**
> One last resort when nothing makes much sense is to do a SMC reset, there should be info for your Mac on apple.com support. It can be as simple as shutting down, disconnect ALL cables of any kind, leave for 15 minutes, reconnect and restart - but it varies.
yea, and this would be the first time I have seen that in reference to a MacPro.

There is a bug somewhere about the keyboard not working in rEFIt with some machines, but I didn't think it was for Mac Pros.

Holding Alt for the boot menu is part of the Mac firmware. It should work no matter what software you have on the machine. When you say "blank screen" does that mean black, no video, or is it white, or what?

You can certainly try removing refit if it will make you feel any better.

---

### Post by fufuntu on 2009-02-03
Hi guys.

When I say blank I mean WHITE , no logos , no rEFIt interface.


..Just to know .. what do you mean for "SMC reset"?


any ideas?:confused:

---

### Post by fufuntu on 2009-02-03
OK sorry , 'seen: System Management Controller (SMC)  , just disconnect everything. ok

and do you think that the white screen is related ? 

I'm going to to try , I'll let you know.. ( cross fingers )

---

### Post by cyberdork33 on 2009-02-03
> **fufuntu said:**
> Hi guys.

When I say blank I mean WHITE , no logos , no rEFIt interface.


any ideas?:confused:
In that case, have you just let it sit there for awhile?

---

### Post by fufuntu on 2009-02-04
Ok I sat, I let it sit....I did the SMC reset....and it worked! 

But after that I saw the problem was coming back to evidence..than I realized that my unexperienced connections had an infuence on this bug : my keyboard was  not directly connected to  the Computer case but was bypassing thought the Cinema HD display...now that I' ve changed and connected correctly , it looks like it is all working well , and I've my Linux'system bachk again.

Now, to be honest my dear cyberdork33, when I told you the screen was staying white, it means I waited a lot...minutes...but no way to see it run..so I will keep you imformed if my problem is coming back again, to figure out this bug.

Maybe I can ask you one more thing ...I'm running Ubuntu 8.10 64bit on this mac Pro, with a GPU ATI radeon 1900xt 512Mb..I'm keeping installed Linux' drivers for this card. In a prior attempt to install Ubuntu I installed proprietary drivers and after that my system was corrupted , stoppin' at the grub..Have you any advice about this? Is there a way to see this card runnig faster on this system?
 Thank you

---

### Post by cyberdork33 on 2009-02-04
> **fufuntu said:**
> Now, to be honest my dear cyberdork33, when I told you the screen was staying white, it means I waited a lot...minutes...but no way to see it run..so I will keep you imformed if my problem is coming back again, to figure out this bug.
OK, that is usually evidence that the Mac firmware is searching for something bootable, or sees an external device that is confusing it (this used to happen to me if I had my iPod connected to my iMac and tried to startup). In the first case, it will usually continue booting after a good while. I think it was related to using the USB hub though, so that ought to have fixed it.

> **fufuntu said:**
> Maybe I can ask you one more thing ...I'm running Ubuntu 8.10 64bit on this mac Pro, with a GPU ATI radeon 1900xt 512Mb..I'm keeping installed Linux' drivers for this card. In a prior attempt to install Ubuntu I installed proprietary drivers and after that my system was corrupted , stoppin' at the grub..Have you any advice about this? Is there a way to see this card runnig faster on this system?
 Thank you
It doesn't really make sense that installing the proprietary ATI driver would affect grub... they shouldn't even be interacting. How did you install the proprietary driver?

---

### Post by fufuntu on 2009-02-04
Oh just simply from the gnome's Add&Remove feature, "proprietay drivers" ,I had to erase partitions and install again the OS , you know , I'm really new to this world :D

I'm just tryin' to figure out what would be the best configuration for my main interests such as 3d graphics , architectural visualization , and scientific data plotting (dem files , FEM, etc) My final dream would be to be able to build an all-open-source-machine with all this features

Now I had a look in synaptic
is it useful to install these?: 
-jockey kde
-xserver-xorg-video-ati-dbg
X.Org X server -- ATI display driver wrapper (debugging symbols) 
-same as above for display 

thank you cyberdork33

---

### Post by cyberdork33 on 2009-02-04
> **fufuntu said:**
> Oh just simply from the gnome's Add&Remove feature, "proprietay drivers" ,I had to erase partitions and install again the OS , you know , I'm really new to this world :D

I'm just tryin' to figure out what would be the best configuration for my main interests such as 3d graphics , architectural visualization , and scientific data plotting (dem files , FEM, etc) My final dream would be to be able to build an all-open-source-machine with all this features

Now I had a look in synaptic
is it useful to install these?: 
-jockey kde
-xserver-xorg-video-ati-dbg
X.Org X server -- ATI display driver wrapper (debugging symbols) 
-same as above for display 

thank you cyberdork33
under the system>adminstration menu there is a "hardware drivers" tool. You can use that to enable the driver properly.

I think that dataplot runs under Linux

---

### Post by fufuntu on 2009-02-05
Do you see what I'm afraid of?

[http://ubuntuforums.org/showthread.php?t=193116](http://ubuntuforums.org/showthread.php?t=193116)

and many posts with similar problems,,but none with my hardware configuration,,,we're pioneers!

---

### Post by cyberdork33 on 2009-02-05
> **fufuntu said:**
> Do you see what I'm afraid of?

[http://ubuntuforums.org/showthread.php?t=193116](http://ubuntuforums.org/showthread.php?t=193116)

and many posts with similar problems,,but none with my hardware configuration,,,we're pioneers!
that is from 2006. things have come a long way.

---

### Post by fufuntu on 2009-02-06
it was just to show kind of things and paranoid thought I had looking at the web about ATI's proprietary installations...

but finally I did! I've got the ATI's 64 bit installed on Mac Pro. And it's working like a charm

---

### Post by fufuntu on 2009-02-11
Anyway it's not been so intuitive..I had to configure manually the drivers (ATI's version 9.1) (following an italian guide) ...now the OpenGl is fast and Furious


Thank you everybody for help, and particularly cyberdork 33 
I had another issue to resolve but I'll post it in another thread

---

### Post by cyberdork33 on 2009-02-11
If you can contribute to the documentation, please take a whack at it:
[https://help.ubuntu.com/community/MacPro](https://help.ubuntu.com/community/MacPro)

---

