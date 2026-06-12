---
title: "Power Mac G5 Refusing to Install 12.04"
date: 2012-07-20
forum: Apple Hardware Users
---

### Post by ImAliveG5 on 2012-07-20
I am somewhat new to linux (especially on apple computers) but I have been trying to install ubuntu 12.04 for the past 2 days, using what I could find in the forums as a guide. So far I have tried both the Live and text based installers with no luck-both never get far enough to actually start installing anything. I am probably doing something wrong but I have no idea what it is.
 
The live installer loads the kernel and briefly boots to a white screen with text followed by a solid black screen.
 
The text based installer starts working after I type cli-expert-powerpc64 and the kernel loads, but after a while it shows a screen that looks like this:
[     1.              ]
[     1.              ]
 
^this goes all the way to the bottom of the screen which just a bit odd imo.
 
These are the specs of the G5 I am fighting with:
Power Mac G5 Dual 2.0GHz (late 2005)
Nvidia 6600LE Display Adapter
2 GB ram; 1.5 TB HDD
 
I would love to get this working so I can help with linux support on PowerPC processors in the future since apple kicked the platform aside.
 
I am frustrated with this machine and cannot let it win!

---

### Post by kestrel1 on 2012-07-20
I assume you are using the powerpc CD for Ubuntu?
[https://wiki.ubuntu.com/PowerPC/](https://wiki.ubuntu.com/PowerPC/)
Also check this for hardware supported:
[https://wiki.ubuntu.com/HardwareSupportMachinesDesktopsApple](https://wiki.ubuntu.com/HardwareSupportMachinesDesktopsApple)

---

### Post by ImAliveG5 on 2012-07-20
I saw that same compatibility chart and it does suggest that I can't run ubuntu with the late 2005 model G5 with my graphics card.:( I was hoping that there may be a way to at least get the text based installer to work and experiment from there.
 
It seems like some people have had success with g5's, theres even a thread for people who are testing 12.04 on these machines.

---

### Post by kestrel1 on 2012-07-20
I expect they are using the later G5's
Have you tried an older version of Ubuntu?
Maybe 10.10:
[http://cdimage.ubuntu.com/ports/releases/10.10/release/](http://cdimage.ubuntu.com/ports/releases/10.10/release/)
You could try upgrading after installing.

---

### Post by ImAliveG5 on 2012-07-20
> **kestrel1 said:**
> I expect they are using the later G5's
Have you tried an older version of Ubuntu?
Maybe 10.10:
[http://cdimage.ubuntu.com/ports/releases/10.10/release/](http://cdimage.ubuntu.com/ports/releases/10.10/release/)
You could try upgrading after installing.
 
I think I will give it a shot, may be a while until I know if it works. I won't hold my breath, as the model of G5 I have is very different from the earlier years, which may be why it wont work. I think this is the last model they made.

---

### Post by str8bs on 2012-07-20
That chart hasn't been updated since 2010 judging from the stamp on the page.  FWIW, My PowerMac is the very first generation 1.6 GHZ and it handles Ubuntu fine minus some current graphics bugs. Mine has different video card though. (FX 5200)  I'm not recommending it or saying it is fast, but I have had Unbuntu,Lubuntu, Xubuntu, and Kubuntu 12.04 running on a G3 before. I'm a glutton for tinkering. 

ImaAliveG5 By "live" do you mean second link on this page? [http://cdimage.ubuntu.com/releases/precise/release/](http://cdimage.ubuntu.com/releases/precise/release/)

---

### Post by ImAliveG5 on 2012-07-20
> **str8bs said:**
> That chart hasn't been updated since 2010 judging from the stamp on the page. FWIW, My PowerMac is the very first generation 1.6 GHZ and it handles Ubuntu fine minus some current graphics bugs. Mine has different video card though. (FX 5200) I'm not recommending it or saying it is fast, but I have had Unbuntu,Lubuntu, Xubuntu, and Kubuntu 12.04 running on a G3 before. I'm a glutton for tinkering. 
 
ImaAliveG5 By "live" do you mean second link on this page? [http://cdimage.ubuntu.com/releases/precise/release/](http://cdimage.ubuntu.com/releases/precise/release/)
 the ISOs i downloaded are the first and second links on this page [http://ubuntuforums.org/showthread.php?t=427714](http://ubuntuforums.org/showthread.php?t=427714) when I refer to the live install, i am talking about the first one.

---

### Post by str8bs on 2012-07-20
It may be easier to test with the desktop ISO (you already downloaded). I don't have a 6600 so..

What physical display port are you plugged in to and what display are you using?
Is it a DVI connector or ADC connector?

Have you tried any kernel boot parameters with live?

---

### Post by ImAliveG5 on 2012-07-20
I have a DVI to HDMI adapter cable connected to the first out of 2 DVI connectors on the card. My monitor is a 22 inch visio flatscreen.
 
I have tried the nosplash and another that I found for a similar problem: video=ofsonly-something like that.
 
they both load the kernel and go to a white screen with text, followed by the "black screen of doom"
 
i can try things with the desktop cd-i still have it and can load it into the g5.

---

### Post by str8bs on 2012-07-20
When it goes to black screen, can you press CTL+ALT+F1 to get to a terminal?
If not, I would suspect a phantom port issue like the 5200's have or the HDMI adapter may be confusing things.

Just speculation, but I wonder if the 6600 has phantom port issues as well? I can't really tell without seeing the logs.

Things I would try if possible:
1. ```
boot: live video=TV-1:d
```2. ```
boot: live 1 nosplash video=ofonly nouveau.modeset=0
``` Should at least boot to command line unless the adapter is causing problems.
2. Another display with DVI. (To rule out the adapter.)
3. Swap port it is plugged in to.

Also, I've never seen the 1. 1. 1. you described from CLI install so I may be way off base. Since you are dual booting, I presume the firmware is the latest?

---

### Post by rsavage on 2012-07-20
> **str8bs said:**
> That chart hasn't been updated since 2010 judging from the stamp on the page. 
+1 .  Which is why I just deleted it.
 
video=ofonly should have no effect with nouveau.
I think nosplash is also a myth.  You should use the option live64-nosplash (or whatever it is called) instead:
 
```

boot: live64-nosplash single nouveau.modeset=0

```

---

### Post by str8bs on 2012-07-20
> **rsavage said:**
> 
 
video=ofonly should have no effect with nouveau.
I think nosplash is also a myth.  You should use the option live64-nosplash (or whatever it is called) instead:
 


Thanks rsavage! Good to know!

---

### Post by ImAliveG5 on 2012-07-20
> **str8bs said:**
> When it goes to black screen, can you press CTL+ALT+F1 to get to a terminal?
If not, I would suspect a phantom port issue like the 5200's have or the HDMI adapter may be confusing things.
 
Just speculation, but I wonder if the 6600 has phantom port issues as well? I can't really tell without seeing the logs.
 
Things I would try if possible:
1. ```
boot: live video=TV-1:d
```2. ```
boot: live 1 nosplash video=ofonly nouveau.modeset=0
``` Should at least boot to command line unless the adapter is causing problems.
2. Another display with DVI. (To rule out the adapter.)
3. Swap port it is plugged in to.
 
Also, I've never seen the 1. 1. 1. you described from CLI install so I may be way off base. Since you are dual booting, I presume the firmware is the latest?
I believe the firmware is the latest, as software update on osx says I am up to date. If it makes it any easier I dont really have to keep it dual boot, i dont use this thing for anything but file storage at this point. 
 
boot: live 1 nosplash video=ofonly nouveau.modeset=0 seems to have made the computer hang at the white screen instead of the black one. all of the others stopped at the black screen.
 
I should also note that after the computer loads the kernel the fans go to full speed, which is very annoying

---

### Post by rsavage on 2012-07-20
I should probably qualify that since you also use debian.
 
video=ofonly shouldn't be necessary in ubuntu, but in debian you may need it (if the installer doesn't add it automatically).

---

### Post by ImAliveG5 on 2012-07-20
My 10.10 desktop iso finished downloading and I am staring at the ubuntu live desktop right now-it worked! Is there anything I can get off of here that can help with getting 12.04 to work? I didnt have to use any special options-just hit enter, saw the white screen, and ubuntu loaded-graphics look the way they should.

---

### Post by str8bs on 2012-07-20
rsavage- clarification appreciated

ImAliveG5- Cool. I speculate you could distribution upgrade from there, but may run in to the same problems. IIRC, 10.04 used driver NV instead of Nouveau and hardware acceleration is disabled (3D.) Don't know about 10.10.

I do know that driver "NV" will avoid phantom port issues that "nouveau" will not.
So you may want to find the issue in 12.04 if you want to get current.

From within your live 10.10 boot, if you could get a copy of /var/log/Xorg.0.log and post it, I might be able to tell how it is seeing the ports/adapter. No promises though.

---

### Post by ImAliveG5 on 2012-07-20
10.10 seems to be working, so I will try toupgrade from that once I can get in the swing of things.
 
I can keep you posted-after all my g5 is still refusing to install 12.04 lol
 
It is still amazing that ubuntu on PPC hardware even exists! I must say it is great that there are people who even try to make this possible.

---

### Post by str8bs on 2012-07-20
Sounds good. When I make time, I need to file a proper bug report on the phantom port issue the FX5200 has. It would be helpful if we could confirm whether the 6600 does or does not have the same issue.

Would you mind if I PM you when I get to it? The live ISO can be used to gather logs if you have a USB flash drive or something to copy them to. It may be helpful to the maintainers if we confirm other cards. The idea being the problem gets resolved in the long run so the next person who installs on the same hardware won't go through what you just did and it will work "out of the box."


PS: The dual boot will not impact the display issues. I would leave it for now unless you are hurting for disk space.

---

### Post by ImAliveG5 on 2012-07-20
> **str8bs said:**
> rsavage- clarification appreciated
 
ImAliveG5- Cool. I speculate you could distribution upgrade from there, but may run in to the same problems. IIRC, 10.04 used driver NV instead of Nouveau and hardware acceleration is disabled (3D.) Don't know about 10.10.
 
I do know that driver "NV" will avoid phantom port issues that "nouveau" will not.
So you may want to find the issue in 12.04 if you want to get current.
 
From within your live 10.10 boot, if you could get a copy of /var/log/Xorg.0.log and post it, I might be able to tell how it is seeing the ports/adapter. No promises though.
 here it is
[http://pastebin.com/t3Zd7ctg](http://pastebin.com/t3Zd7ctg)

---

### Post by str8bs on 2012-07-20
ImAliveG5- Thanks for the log. Looks like 10.10 is using nouveau and I don't see a phantom port. No reason for me to bug you further. (pun intended)  Assuming you checked MD5 sums and their was nothing wrong with the ISO burn, I'm out of ideas.

---

### Post by ImAliveG5 on 2012-07-20
im not sure either. 10.10 is running pretty well, so I may stay with it for a while. Im trying to get the gigabit ports to work by iinstalling broadcom's driver now. Thank you for all of your help.

---

### Post by prymus on 2012-07-22
Just thought I'd chip in since I have the exact same hardware and running Ubuntu 12.04 almost without a hitch!

The video issues you are experiencing are likely related to that HDMI adapter. I have my 47" LG TV connected as a monitor to the first DVI port of the 6600 (that's the one nearest the casing) and connected to the VGA port of the TV via an Apple DVI to VGA adapter. I have had no problems with this configuration other than the screen being black on the left-hand-side when using a resolution of 1920 x 1080. Using 1280 x 1024 is just fine although the icons on the Launcher are white and the alpha seems altogether a bit weird. 

The fans issue is normal, I think, and it's due to the fact that the thermal support isn't correctly implemented on the original install disc. It shouldn't hurt the Mac, just run Software Update in Ubuntu once you get it going and it will right itself. 

I would be interested to see how you get on as I think the G5 is a fantastic piece of hardware and we're all going to get a lot of use out of these babies yet!

---

### Post by kestrel1 on 2012-07-22
Glad 10.10 is working. You could try to upgrade to 11.04 next & see if that works.

---

### Post by ImAliveG5 on 2012-07-22
Im going to try the 12.04 disk with a monitor that supports dvi. The 11.04 update broke the install and i can only get tin by using the "old" command.
 
ps: did you get it going with the live or alternate installer? what parameters did you use?

---

### Post by str8bs on 2012-07-22
Prymus - Thanks for confirming the hardware. I would be curious to know if the other "weirdness" you mentioned was acceleration related. I've noticed "what I see" changes depending on the default resolution of the monitor connected.

ImAliveG5- Just my own preference when running in to tough issues like you are seeing. CLI install first (no parameters should be needed) to verify you can at least get kernel loaded and command line and then just run tasksel to install your desktop/s. (This is if simply removing the HDMI adapter doesn't improve things. My speculation concurs with what prymus posted.)

---

### Post by ImAliveG5 on 2012-07-22
the basic live cd **and cli install** still do not work. I am using a samsung monitor with dvi inputs.
 
the cli install is doing the same thing I described in the first post.

---

### Post by str8bs on 2012-07-22
IMO, that leaves us with:
Something up with the ISO you are using, or
See if we can find a difference between your hardware and prymus. The only one we know right now is the connected display.

Probably stating the obvious, but try omitting any hardware that isn't necessary. IE: USB hubs, KVM, Firewire, etc.

---

### Post by ImAliveG5 on 2012-07-22
I changed monitors and I only have a keyboard and mouse plugged in.

This page details the hardware configuration of the late 2005 g5s:

[http://support.apple.com/kb/SP37](http://support.apple.com/kb/SP37)

Mine is the Dual 2GHz with the Nvidia GeForce 6600LE
I added the Airport Extreme Card when the Gigabit Ethernet ports stopped working 2 years ago.
Speaking of the Ethernet ports... what happened was I literally just turned the computer on one day and the interface in osx said cable unplugged for both ports. So I deleted the configurations from network settings and couldn't create new ones because the network interfaces disappeared. I only had options to make a FireWire connection. After installing 10.10, I typed lshw into terminal and it saw the Ethernet ports! I can't get an internet connection from them, but Linux being able to see them makes me think they can be fixed. Any idea what happened?

---

### Post by str8bs on 2012-07-23
I'm grasping at straws unless prymus or others see a difference.

That OSX sees a hardware problem where Linux does not with your ethernet is curious. You mentioned adding Wi-FI: Does anyone know if the current b43 problem in known issues could preset as the "1. 1. 1...." failure ImAliveG5 is seeing?

Might be worth a shot: see b43 here: [https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

---

### Post by rsavage on 2012-07-23
> **str8bs said:**
> rsavage- clarification appreciated

I'm pretty sure if you don't use video=ofonly in debian, then you get this sort of thing [http://www.mintppc.org/forums/viewtopic.php?f=15&t=973](http://www.mintppc.org/forums/viewtopic.php?f=15&t=973) . 
 
Getting back to ImAliveG5's problem..... in the back of my mind I always have pauljwell's bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/912071](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/912071) . I'm sure he has a similar machine, although they all sound the same to me. 
 
Do you get any part of the installer going before the 1's appear?
 
It's pretty common for ubuntu to output on a different port to Mac OS X. Have you tried booting with it connected to each port?
 
You need to use the relevant nosplash option to see where it stalls.
 
If you can't boot into single user mode even with nouveau turned off, and you've tried every port then I don't know what else there is to suggest. It's contact the powerpc kernel people time.....

---

### Post by ImAliveG5 on 2012-07-23
I removed the airport card to eliminate that bug str8bs was talking about but I was still running into the same problem, so I loaded the alternate CD and tried cli-expert video=ofonly. I could only read these things for a brief amount of time because the text was scrolling, but one of the errors that appeared was "sata link down!". The computer first hangs at the message: Attached SCSI generic sg1 type 5- this is when my fans go full speed. Moments later this message appears: CPU #1 stuck for 23s!-this is followed by exception errors and eventually the 1.s I was talking about in the first post. Its like the installer isn't detecting my hardware correctly and loading the wrong drivers and causing problems.

---

### Post by str8bs on 2012-07-23
> **rsavage said:**
> I'm pretty sure if you don't use video=ofonly in debian, then you get this sort of thing [http://www.mintppc.org/forums/viewtopic.php?f=15&t=973](http://www.mintppc.org/forums/viewtopic.php?f=15&t=973) .  In my thick skull now. Thanks!


ImAliveG5- the ofonly option is a Debian and not Ubuntu thing which rsavage pointed out. My fault for confusing the issue. Won't solve your problem though.

Doubt it will affect your current issue, but the ethernet in OSX issue is an unresolved anomaly.
In OSX, rename the file /Library/Preferences/SystemConfiguration/preferences.plist
to
/Library/Preferences/SystemConfiguration/preferences.plist.old
Reboot and see if the interfaces show back up in OSX.

Probably stating the obvious again, but other than getting kernel people as rsavage mentioned, I'm at a loss.

Sometimes resetting PRAM or PMU work miracles, but I doubt those would impact what your are seeing.[http://support.apple.com/kb/HT1379]("http://support.apple.com/kb/HT1379")
[http://support.apple.com/kb/HT1379]("http://support.apple.com/kb/HT1379")

Hopefully prymus will check back in and see something we are missing.

---

### Post by rsavage on 2012-07-24
What messages do you get when you use the 64 bit option (which you should be using)?

---

### Post by ImAliveG5 on 2012-07-24
> **rsavage said:**
> What messages do you get when you use the 64 bit option (which you should be using)?

The computer hangs at:

[   2.494484] USB 3-2.1 new full-speed USB device number 3 using ohci_hcd

Then shows this after a while:

[  28.036468] BUG: soft lockup-CPU#0 stuck for 23s!(modprobe:52)

This is followed by modules linked in, a call trace, and exception-all are followed by other values that I can post if I need to.

str8bs, I tried that and it made no difference. Osx does see my ports, but I cannot use them. They appear in the about this mac but for the past 2 years they show to have no driver installed, even when I reinstall the OS.

---

### Post by str8bs on 2012-07-24
> **ImAliveG5 said:**
>  str8bs, I tried that and it made no difference. Osx does see my ports, but I cannot use them. They appear in the about this mac but for the past 2 years they show to have no driver installed, even when I reinstall the OS.

I was hoping to rule out and not possibly confirm a hardware issue. Be aware, I am WAY in to speculation territory at this point. Here is my thinking:
1. prymus confirms no problem on same hardware
2. OSX says drivers not installed for ethernet (Maybe not recognizing hardware correctly?)
3. 10.10 doesn't seem to have an issue booting.

All I see left is kernel problem or hardware problem. Might be worth a shot:
To rule out ethernet, there may be a way to use boot params to blacklist where your ethernet gets modprobed. (Similar to the b43 issue.) I would have to google which module/parameters. Anyone else have ideas?

BTW- Kudos to your tenacity. Don't let it win. Bonus points for your screen name that reminds of Ally Sheedy and the robot in 86.:)

---

### Post by rsavage on 2012-07-25
Install 10.04. It still has nearly a year left of support. Otherwise you are going to get disheartened pretty quickly. Setup a separate partition you can use for testing.
 
Once you find your feet in linux you can then start tackling your kernel problem in 12.04.

---

### Post by ImAliveG5 on 2012-07-25
> **rsavage said:**
> Install 10.04. It still has nearly a year left of support. Otherwise you are going to get disheartened pretty quickly. Setup a separate partition you can use for testing.
 
Once you find your feet in linux you can then start tackling your kernel problem in 12.04.

I can begin once I get home.

---

### Post by rcristofrf on 2012-07-29
I successfully installed 12.04 on a 2005 Mac Mini G4 1,4GhZ with the boot option 

live-nosplash-powerpc

However, this didn't work on an iMac G3 700MhZ (iLamp). Here I used

live video=ofonly nouveau.modeset=0

which lead to the installation desktop, but it is in the often cited "psychedelic colors". The installation runs now and I hope, that the colour issue will have gone after the reboot. I will give an update, when it's done.

Best regards,
Ricardo Cristof

//Edit: Nope, color issue remains and I'm too tired for further experiments today...

---

