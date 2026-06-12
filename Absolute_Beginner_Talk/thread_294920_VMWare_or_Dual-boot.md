---
title: "VMWare or Dual-boot?"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by tonyr1988 on 2006-11-07
My dad's finally fed up with WinXP on his computer, and said he wants to try Ubuntu (he's got to re-format his computer anyway). I think there's only a few programs that he would need Windows for, so I don't want to completely get rid of it.

Should I virtualize or dual-boot WinXP?

The two biggest programs I can think of are Adobe InDesign and Age of Empires II (what a nerd :P).

Also, I don't have much experience with VMWare (only messed around with it a little) - if there's a hardware issue...say, he plugs his digital camera into his computer and Ubuntu doesn't recognize it, will WinXP in VMWare be able to pick it up? I don't think it would, but it doesn't hurt asking.

For those of you still running some form of Windows, why did you pick the method you did?

---

### Post by geoffm33 on 2006-11-07
I am dual booting and will probably stay that way. I will probably do most of my computing from Ubuntu, but there are apps I need to go into Windows for.

---

### Post by taurus on 2006-11-07
I would dualboot.  Reinstall XP first and make sure you leave an empty partition for Ubuntu.  Then install Ubuntu and install GRUB on MBR so it will handle both XP and Ubuntu.

---

### Post by chris062689 on 2006-11-07
I really think VMWare would be a better choice.
If he only needs to use a FEW programs (and WINE doesn't work with them) he could just boot up with VMware console, and he's off!

---

### Post by TripBR on 2006-11-07
Dual-booting..

One day you&apos;ll need to run a heavy program on your Windows and the VMWare won&apos;t will handle it.

Sds,
Alan

---

### Post by distroman on 2006-11-07
I would dual boot too. 
> The two biggest programs I can think of are Adobe InDesign and Age of Empires II (what a nerd :P).
You don't have hardware acceleration with VMware, so games would be a no go as I understand it. 
So I think you would have to look at wine for games. 


> Also, I don't have much experience with VMWare (only messed around with it a little) - if there's a hardware issue...say, he plugs his digital camera into his computer and Ubuntu doesn't recognize it, will WinXP in VMWare be able to pick it up? I don't think it would, but it doesn't hurt asking.
I do think that the free version vmware-server do support that, you'll just have to add it yourself when you create your virtual machine, it is not default as with the workstation I believe. 


> For those of you still running some form of Windows, why did you pick the method you did?
I think have been dual booting for +2 years or so, it's easy access when I need it and I do at times.

---

### Post by boban on 2006-11-07
> **distroman said:**
> 
You don't have hardware acceleration with VMware, so games would be a no go as I understand it. 
So I think you would have to look at wine for games. 


You can have some hardware acceleration - up to DirectX 8. I've been able to run Arcanum (rpg) under vmware server with no trouble at all. But for newer games - you'll better keep win partition. 

> **distroman said:**
> 
I do think that the free version vmware-server do support that, you'll just have to add it yourself when you create your virtual machine, it is not default as with the workstation I believe. 


Under vmware you have only "emulated" hardware - vmware is a layer between ubuntu and win - so if your hardware doesn't work in Ubuntu it won't work in virtual machine. I don't think that there is a way to give direct access to any hardware resources (except hdd).



> 
For those of you still running some form of Windows, why did you pick the method you did?

I need windows only for Visual Studio and it works in vmware... and only compilation is little bit slow... 

IMO you should try if your apps will work under vmware, after that you can remove windows partition... (but I keep mine "just in case"... for now)

---

### Post by geoffm33 on 2006-11-07
> **taurus said:**
> I would dualboot.  Reinstall XP first and make sure you leave an empty partition for Ubuntu.  Then install Ubuntu and install GRUB on MBR so it will handle both XP and Ubuntu.

You don't need to reinstall, just resize your XP partition. (Edit: just read that he is reinstalling anyway, but you *could* just resize).

I followed this: [http://www.ubuntuforums.org/showthread.php?p=74952#post74952]("http://www.ubuntuforums.org/showthread.php?p=74952#post74952")


Here is another guide (I didn't personally follow it): [http://users.bigpond.net.au/hermanzone/p3.htm]("http://users.bigpond.net.au/hermanzone/p3.htm")

---

### Post by distroman on 2006-11-07
> **boban said:**
> You can have some hardware acceleration - up to DirectX 8. I've been able to run Arcanum (rpg) under vmware server with no trouble at all. But for newer games - you'll better keep win partition. 
I did not know that, thanks for clearing it up. 

> **boban said:**
> Under vmware you have only "emulated" hardware - vmware is a layer between ubuntu and win - so if your hardware doesn't work in Ubuntu it won't work in virtual machine. I don't think that there is a way to give direct access to any hardware resources (except hdd).
As fare as “ his digital camera” goes, it would be fine as long as he adds whatever device is needed, right? Presuming that he has been using it so fare on windows.

---

### Post by boban on 2006-11-07
> **distroman said:**
> As fare as “ his digital camera” goes, it would be fine as long as he adds whatever device is needed, right? Presuming that he has been using it so fare on windows.

Your logic is good... But I don't know if that is possible with vmware... I had an issue with lexmark printer (Z810) and I thought - I'll install drivers on win in vmwere! But I didn't know how to add non-existing device (for Ubuntu) to windows through vmware. (eventually I've found linux drivers for that printer, but it required lot of compiling).

If you'll find a way to add "raw" devices to windows run through vmware, then let me know :) It will be handy :)

---

### Post by distroman on 2006-11-07
> **boban said:**
> Your logic is good... But I don't know if that is possible with vmware... I had an issue with lexmark printer (Z810) and I thought - I'll install drivers on win in vmwere! But I didn't know how to add non-existing device (for Ubuntu) to windows through vmware. (eventually I've found linux drivers for that printer, but it required lot of compiling).

If you'll find a way to add "raw" devices to windows run through vmware, then let me know :) It will be handy :)
I have never tried it, I just heard about USB (supposing that's what would be needed) being used with vmware. 
By “"raw" devices”, do you mean for instead USB support? I simply don't know a hole lot about it. 
[http://www.vmware.com/community/thread.jspa?messageID=496559&#496559](http://www.vmware.com/community/thread.jspa?messageID=496559&#496559)
[http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=3862823&sliceId=SAL_Public&dialogID=3477034&stateId=0%200%203475724&doctag=Author,%20KB%20Article](http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=3862823&sliceId=SAL_Public&dialogID=3477034&stateId=0%200%203475724&doctag=Author,%20KB%20Article)
If so and if I got it right then maybe this would be it?
As I said I don't know, I am not even sure this is what you mean, I just got curious.

---

### Post by Narzuhl on 2006-11-07
Personaly i would dual boot. I am doing something like that., execpt i have 2 hard drives and a removable drive tray, i wanted my XP and Ubuntu completely seperate.
I use XP for some of the newer games thats it.
I use VMWare for Visual Studio and SQL. 
As for hardware....not sure i plugged in my Kodak v550 the other night and it worked, it was seen as a removable drive, like a flash drive.

As for AOE II try wine or Cedega.

Biggest problem with Dual booting that i see is forcing yourself to use ubuntu if you were a diehard windows user....... Easy for me my game drive is only 20 gig so it will not hold a heck of alot else. my Ubuntu drive is 400 gig.

---

### Post by boban on 2006-11-07
> **distroman said:**
> I have never tried it, I just heard about USB (supposing that's what would be needed) being used with vmware. 
By “"raw" devices”, do you mean for instead USB support? I simply don't know a hole lot about it. 
[http://www.vmware.com/community/thread.jspa?messageID=496559&#496559](http://www.vmware.com/community/thread.jspa?messageID=496559&#496559)
[http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=3862823&sliceId=SAL_Public&dialogID=3477034&stateId=0%200%203475724&doctag=Author,%20KB%20Article](http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=3862823&sliceId=SAL_Public&dialogID=3477034&stateId=0%200%203475724&doctag=Author,%20KB%20Article)
If so and if I got it right then maybe this would be it?
As I said I don't know, I am not even sure this is what you mean, I just got curious.

Thanks for the links... That is but one part of the problem... I meant something like issue with my printer... or some other plugged in device (not necessary via USB) that linux doesn't recognise by itself...

---

### Post by distroman on 2006-11-07
Ok, I see.

---

### Post by Cool Surfer on 2006-11-07
I have Win Xp Prof, FC6, Ubuntu all three.

---

### Post by tettayes on 2008-04-03
using wubi is a good way to install ubuntu from windows, and that's what I did!
It is working great on my machine!

---

### Post by Xiong Chiamiov on 2008-04-03
On the original topic, I'm dual-booting XP and Kubuntu, and I only boot into Windows when I'm helping someone with their computer over the phone/im, or my mom wants to call me on Google Talk, since I haven't yet gotten my usb headset to work in Linux.  This weekend I think I'll be trying to triple-boot with OSX :p .

---

### Post by tonyr1988 on 2008-04-05
This is really old, but I'll update on my own topic. :)

I don't have any dual-boot machines....I've been away from Windows for >2 years. :D

But, on family/friends who still need Windows apps, I've been installing VirtualBox + WinXP + Seamless integration. It works perfectly (so long, of course, that they have the sys requirements for virtualization).

---

### Post by StOoZ on 2008-04-05
stay dual booted.
why : usually not all types of hardware is supported in ubuntu, for that, you have to use a REAL installation of windows, not virtualized.
for example : I have a sh*tty astra 5600 usb scanner, which doesn't work on linux & virtualized xp, but whenever I want to scan something, I just use my windows installation on the other partition.

---

