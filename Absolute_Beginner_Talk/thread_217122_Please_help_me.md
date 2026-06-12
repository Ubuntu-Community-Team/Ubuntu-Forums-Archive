---
title: "Please help me"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by machineitright on 2006-07-16
:confused: 

I'm just not getting these howtos. I'm having a really hard time getting on the Internet, which seems to be the #1 problem with Ubuntu from where I sit. I started with a Belkin card and found that it was the worst card I could have chosen so I went out and purchased a Netgear that was on the list of supported cards that said it worked out of the box, I am getting a signal as both lights are flashing but still no Internet. Looking back at the card it said that once the WPA stuff was loaded that the card worked flawlessly, every howto I find on the wiki or forum for WPA doesn't seem to be for my card and somewhere in each it will say if you have a different card go here and they start talking about this rev. and that rev., you need to have GNOME Network Manager loaded and I get so confused I don't know were to start. I would really like to use a Liux system but at this moment it doesn't seem to be very user friendly. I had the same feelings about Windows when I first started usind it, and although I'm no power user by any standards I do like using computers. Would one of you be so kind as to help me out, just to get started? I will keep studying the guides and howtos and try and get better.

machineitright,

---

### Post by encompass on 2006-07-16
If you goto system administration and then networking... you should be able to see your card there... if so... great... click once on the card then properties and enter the information for your wireless connection.  For testing reasons, I would take all your wireless settings to no security....
Network manager is a nice tool to connect seemlessly to many different networks.  But I think we should just get you up and on first.
Feel free to IM me... jsut be patient I spend 25+ hours a week with ubuntu forums.
I also want to say that in linux there at a billion way sto do one thing... kinda gets over whelming.

---

### Post by machineitright on 2006-07-16
Thanks for replying. When you say the information for my network do you meen to use a static IP? I have tryed using the DHCP and that does not work, I have tryed the static IP no luck on that either. maybe I'm not entering it correctly. I noticed in the wiki stuff that the card did not network until they entered the WPA settings. I tryed logging into my router which is A Netgear WGT624 and the site says try again later. I don't think I set it up as WPA so was going to check but no luck, is there another way to get to the router? The laptop which I'm using to get info shows the network as WEP security.

Again thanks for the help!

---

### Post by encompass on 2006-07-17
Nope... that information, the dhcp and other what not are what you need once your network card can talk to your wireless network...
you would have the following information...
your essid
and your wep encription key, if your on a secure network.  Hopefully you can shut off any security features just to see if your card is working properly.
Wireless is one of the most annoying things in the world... even in windows it is bad.  I don't even try to help people there.
Do you know the settings for your wireless network?  if not... you should be able to see them from your windows side.

---

### Post by encompass on 2006-07-17
I have a search on your error here on the posts....
[http://ubuntuforums.org/search.php?searchid=6801614](http://ubuntuforums.org/search.php?searchid=6801614)
[http://ubuntuforums.org/showthread.php?t=217099&highlight=Buffer+I%2FO+Error+install](http://ubuntuforums.org/showthread.php?t=217099&highlight=Buffer+I%2FO+Error+install)
[http://ubuntuforums.org/showthread.php?t=215002&highlight=Buffer+I%2FO+Error+install](http://ubuntuforums.org/showthread.php?t=215002&highlight=Buffer+I%2FO+Error+install)
[http://ubuntuforums.org/showthread.php?t=214105&highlight=Buffer+I%2FO+Error+install](http://ubuntuforums.org/showthread.php?t=214105&highlight=Buffer+I%2FO+Error+install)

These give these solutions:
Burn the cd at a much slower rate like 4x
What are the specs of the computer your putting this cd into?
Try the alternet install cd.
Can you get to the live cd?
Try the other options on the boot... like the alternet boot graphics thingy, it should shut dma off which may fix your problem.

I am swinging here... lets hope I hit the ball. ¶:

---

### Post by machineitright on 2006-07-17
Thanks encompass!

I was able to login to my router finally, changed all the security settings to none and got Internet access what a joy it was to finally see progress! It was the WPA-PEK that I had set on the router that was keeping me from gaining access. I would still like to know how to load and use the WPA client. Kudos on the networking comment I 100% agree.

---

### Post by sailor2001 on 2006-07-17
> **machineitright said:**
> Thanks encompass!

I was able to login to my router finally, changed all the security settings to none and got Internet access what a joy it was to finally see progress! It was the WPA-PEK that I had set on the router that was keeping me from gaining access. I would still like to know how to load and use the WPA client. Kudos on the networking comment I 100% agree.

For general information, with my ip, after the modem is disconnected, it takes 4 hours to recycle to the ip address........have to have a lot of patience when setting up wireless

---

### Post by encompass on 2006-07-17
Well, I really don't know what wpa is... as I am new to wireless myself...
I used wep 128 encription and used an ascii key.  Everything seems fine with those settings... in addition... it may be useful to make your connection hidden, that is just a nother layer of protection.  Like more deoderant, but you can still stink in the end.:-?

---

### Post by Sef on 2006-07-17
> Well, I really don't know what wpa is...

Here's a wiki on [WPA.]("http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access")

---

### Post by machineitright on 2006-07-17
Had a problem tonite, I downloaded the available updates and I lost my Internet connection so I just reloaded Ubuntu off the cd I downloaded from the net and it is working again. Do I need to report this as a bug? Where do I report it to and how?#-o

---

### Post by encompass on 2006-07-18
I would... did you have to do any speacial setting for your card to work in linux?  if not... yeah, I would call it a bug... it is probably from your kernal.. when you reboot... press excape and select the old kernal... you will have at least four options 2 are recovery modes... and 2 are full kernels... pick the older one... then see if your card works.. if so... I cna show you how to stay with the older kernal till things get fixed.  Sorry about that dude.](*,)

---

### Post by machineitright on 2006-07-18
I've had to do this before with XP believe it or not:mrgreen: . Do I just enter the bug report on the Ubuntu web site? The card worked right out of the box, it was one of the cards that was listed as supported on the wiki documents, that was why I purchased it. What was keeping me from getting the Internet was the router security settings for WPA. Ubuntu has a WPA client for using those settings but I still don't know or understand how to load or use it. Maybe one of the forum GURU's would help me out with this;).

---

### Post by encompass on 2006-07-21
I would recommend reporting the error to the ubuntu website.  I think it is something called launchpad.
Then, on the ubuntu hardware support wiki.  I would make the change to the site about your card telling that you couldn
t get the wpa support working.  But MAKE SURE that the card does not work with wpa support.  Heck, you could even chack for wep support.. that would be good for others to know.
I am excited that you are willing to help the open source community!

---

### Post by machineitright on 2006-08-01
I've been away for awhile and not able to retry the updates, I did this tonite and had the same problem as before, no internet. What is worse Ubuntu doesn't even see the card, I have a lite flashing but when I go to the network manager it doesn't show the card. I think I will go ahead and report this as a bug. Another thing that is happening is that when I try and shutdown the computer hangs-up on "Will now halt" and does not finish the shutdown sequence, maybe I should report this too.:confused:

---

### Post by encompass on 2006-08-02
It sounds like you made some special changes to something in your kernel.  If there is ever a kernel update and you made changes... you need to update you kenrel changes too... in other words, everything you did to get the wireless to work.
Sucks, but that is what happens when companies won't make open drivers for a device.  WE can't put it in the kernel updates.
Hope this explains it.

---

### Post by encompass on 2006-08-02
check that acpi is working... that is why it would not halt... at least to my knowledge... but yeah cool report a bug.

---

### Post by machineitright on 2006-08-02
Hey encompass,

I wouldn't even begin to know if I had changed the kernel, but the card at least showed in the connections window in version 6.06-15-23 with the update it did not. I will have to reload the OS tonite off the mirror I downloaded because when I tryed to load the driver for my Nvidia Vanta graphics card according to the instructions in the wiki my GNOME failed to come back up, not knowing how to fix this I decided to just reload the OS. Luckily I have the 6.06-15-23 mirror that works with my wireless card, by the way how do you check to see if acpi is working? 
  I originally wanted to work with Ubuntu because of EMC2, a CNC machinetool controller and this OS is the one that LinuxCNC recommended to download, I am having so much trouble with the OS that I'm not even getting to work with what originally brought me to Linux, so much to learn and so little time.:rolleyes:

---

### Post by encompass on 2006-08-03
Don't worry it is worth it.
If it is a kernel thing that changed, you can go back without reinstalling.
when the computer is booting... you will see a small count down time for something called grub boot loader... when you see it... press esc and you'll see your boot options... one will be your old kernel with a standard boot not the fail safe.  Try that one.  If you computer works fine... then we know tha the knew kernel will work with some tweaking.
It is all worth it when you get this taken care of.  Linux is better because... well, when windows has errors like this... you can't do anythig about it.:???:

---

### Post by machineitright on 2006-08-03
Well I feel like an idiot! It had nothing to do with the updates, it was the script that loads EMC2 on Ubuntu that was the culprit, it turns off some of the packages so that they do not mess up signals going out to motors and such. The script loads some realtime components to the kernel then recompiles it to fun machinery in realtime mode.
   I also had to set the USB keyboard to enabled so that when the system booted I could hit the esc key and change between the realtime kernel load and the standard kernel load. It sucks but that is all I know to do for now. Going to see if Chris Radek can help me test using Madwifi in the realtime kernel to see if it interfers with EMC2 or not, would be nice to just let the system boot normally and not have to restart everytime I want to use the internet.

---

