---
title: "Macbook Air and Ubuntu ?"
date: 2012-06-06
forum: Apple Hardware Users
---

### Post by IanViator on 2012-06-06
Here is my situation. Thinking/wanting to switch to Ubuntu from osx, and I am a Macbook Air user. I prefer the Air hardware, I cannot find anything comparable in the windows world.

Can anyone advise me: I have read of difficulties in installing U onto an Air, the lack of a dvd drive. Just how difficult is this process? Second, when it is installed, how well does U run on an Air?

Thanks for any assistance.

---

### Post by markmaus on 2012-06-09
I've got a macbook air also.  I'd also like to put ubuntu on it.  Too bad nobody is replying to your post.  I was imagining that I could hook up a removable usb cdrom drive with an Ubuntu disk on it and boot to that.  I'm not sure that it will even boot from an external drive.  Also I'll need bootcamp or something like efi loader as a boot loader.  Good luck to you.

---

### Post by Greenborn on 2012-06-09
> **IanViator said:**
> Here is my situation. Thinking/wanting to switch to Ubuntu from osx, and I am a Macbook Air user. I prefer the Air hardware, I cannot find anything comparable in the windows world.

Can anyone advise me: I have read of difficulties in installing U onto an Air, the lack of a dvd drive. Just how difficult is this process? Second, when it is installed, how well does U run on an Air?

Thanks for any assistance.

[https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick)

---

### Post by jonas2012 on 2012-06-09
Ubuntu on Mac is so so. I would strongly advise you to make backups beforehand. And dont use acpi off as boot parameter as this may fry your hardware, when it gets hot.

---

### Post by IanViator on 2012-06-10
Thanks for the replies. The plan is to wait until Appl brings out the next Air. If it has larger mass storage (512 -- I have lots of pics), I will be buying. This will give me a blank space to work with while I play around with installing ubun onto a Mac. The lack of a drive is clearly a problem, but it is something that the community should look at, I see this becoming the norm over the next few years. A DVD will be so 0s soon.

---

### Post by virucidal on 2012-06-13
If you want to use a USB stick to install Ubuntu 12.04 on a Macbook Air 1,1, you have to create the USB stick using Ubuntu 12.04's "Startup Disk Creator". No other option I tried worked. I tried:

UNetBootin
Disk Utility (as per Ubuntu instructions on their website)
Refit
Some crazy partitioning tricks (ugh, this failed and took forever)
Manual instructions from [https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick) (linked in previous post, this does not work!)

This is unfortunate for people that only have a Macbook Air (without the external CD drive) and want to install Ubuntu on it, for they need to have access to Ubuntu 12.04 to create the USB disk. I first installed Ubuntu on my Macbook Pro 6,2 using a DVD, and then used Ubuntu 12.04 on my Macbook Pro to create the installable USB stick for the Macbook Air 1,1.

Keep in mind that if you get a newer Macbook Air, it may take a while for drivers to come out. My Macbook Air 1,1 (which is the first air released) is very fast with Ubuntu installed (it is super-slow with OS X Lion).

Cheers!

---

### Post by IanViator on 2012-06-13
Virucidal,
Thanks for that info. I am not in a hurry. Right now I am looking at the new Airs just announced by Appl. I want the 500gb drive option (I have lots of photos). I am willing to wait until the drivers appear.
At that time I will be asking more questions!

---

### Post by pe7er on 2012-06-13
> **jonas2012 said:**
> Ubuntu on Mac is so so. I would strongly advise you to make backups beforehand. And dont use acpi off as boot parameter as this may fry your hardware, when it gets hot.
I tried to install Ubuntu as dual boot on my **MacBook Pro** using the instruction from [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation) (yes, after I made a good backup :))

I got it to work more or less (didn't get to testing the camera + mic). However, as I am used to my PC with PC keyboard, I didn't like the Apple keyboard with all it's other short cut keys. And I was able to access the Apple partition from Ubuntu, but not vice verse.

So in the end I removed my dual boot and now I use that MacBook Pro with OSX only...

---

