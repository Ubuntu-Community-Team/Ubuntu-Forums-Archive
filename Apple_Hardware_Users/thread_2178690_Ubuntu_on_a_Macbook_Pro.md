---
title: "Ubuntu on a Macbook Pro"
date: 2013-10-04
forum: Apple Hardware Users
---

### Post by Cyb3 on 2013-10-04
How does it feel to put Ubuntu on Macbook Pro? And is it "hard" to accomplish this with drivers etc? I'm mostly worried about the touchpad how that will work for me. I've seen many guides etc for this but i wanted to ask you guys of your experience with this.

---

### Post by gamblor01 on 2013-10-06
It's not too bad but it's not perfect either.  My new job gave me a Macbook Pro and wanted me to get it setup however much I can before my first day.  I start on Wednesday so I have pretty much two more days to decide what to do...

You will need to install either rEFIt (which is no longer supported/developed) or rEFInd (a fork of rEFIt that is still maintained).  I just installed rEFInd by following this tutorial:


[http://randomtutor.blogspot.com/2013/02/installing-ubuntu-1304-on-retina.html](http://randomtutor.blogspot.com/2013/02/installing-ubuntu-1304-on-retina.html)





A few notes about that tutorial and my experience in general:


1. You have to copy over the vmlinuz and initrd files every time you update your kernel.  This is a bit of a pain, especially because when booting into the live mode -- the wireless doesn't work.  Finding them the first time can be a bit tricky.  One of the comments was exactly what I needed:


> 
After beating my head against a wall for a while, I find them:


First, I stopped trying to look only using terminal.
I opened up nautilus
There on the lower left was the name of my partition I had just installed ubuntu to. It wasn't mounted. I double clicked on it.


Now, back in terminal, going into /media there was a new directory that wasn't there before: ubuntu.


So Now I just cd /media/ubuntu/[the UUID of my partition]/boot
and there they are.







2. Suspend flat out doesn't work.  Closing the lid turns off the screen but when you open it back up, you can't use it.  It's clearly running, you can hear the fans and so on.  You just have to hold the power button it power it off and reboot.  :/




3. The touchpad works fine, though it lacks many gestures.  You cannot use three finger swipes, and you cannot use two finger left/right in the browsers (to go back/forward between pages).  There is a program called Touchegg which allows you to configure tons of multi-touch gestures but Unity intercepts all of these events and disables them.  So if you're going to use Ubuntu with Unity then you have to basically recompile Unity and prevent it from being updated.  Here is a good tutorial:


[http://elscreemo.blogspot.com/2013/05/restoring-three-finger-gesture-in.html](http://elscreemo.blogspot.com/2013/05/restoring-three-finger-gesture-in.html)




If you're not going to go that far, you should at least install the gpointing-device-settings package.  It makes the thing work a bit better all around, and allows for a reasonable amount of tweaks.

---

### Post by Cyb3 on 2013-10-07
> **gamblor01 said:**
> It's not too bad but it's not perfect either.  My new job gave me a Macbook Pro and wanted me to get it setup however much I can before my first day.  I start on Wednesday so I have pretty much two more days to decide what to do...

You will need to install either rEFIt (which is no longer supported/developed) or rEFInd (a fork of rEFIt that is still maintained).  I just installed rEFInd by following this tutorial:


[http://randomtutor.blogspot.com/2013/02/installing-ubuntu-1304-on-retina.html](http://randomtutor.blogspot.com/2013/02/installing-ubuntu-1304-on-retina.html)





A few notes about that tutorial and my experience in general:


1. You have to copy over the vmlinuz and initrd files every time you update your kernel.  This is a bit of a pain, especially because when booting into the live mode -- the wireless doesn't work.  Finding them the first time can be a bit tricky.  One of the comments was exactly what I needed:









2. Suspend flat out doesn't work.  Closing the lid turns off the screen but when you open it back up, you can't use it.  It's clearly running, you can hear the fans and so on.  You just have to hold the power button it power it off and reboot.  :/




3. The touchpad works fine, though it lacks many gestures.  You cannot use three finger swipes, and you cannot use two finger left/right in the browsers (to go back/forward between pages).  There is a program called Touchegg which allows you to configure tons of multi-touch gestures but Unity intercepts all of these events and disables them.  So if you're going to use Ubuntu with Unity then you have to basically recompile Unity and prevent it from being updated.  Here is a good tutorial:


[http://elscreemo.blogspot.com/2013/05/restoring-three-finger-gesture-in.html](http://elscreemo.blogspot.com/2013/05/restoring-three-finger-gesture-in.html)




If you're not going to go that far, you should at least install the gpointing-devices-settings package.  It makes the thing work a bit better all around, and allows for a reasonable amount of tweaks.

Hi, thanks for the answer. I installed it like you said and it was very bad. The graphics was very wierd and the computer frooze very often. I've now instead of doing all of that downloaded vmware and running it in fullscreen instead. But the speed isn't great, but it works much better though. I created another thread about getting the Dell XPS 13 Developer Edition, and i might just do that very soon to get the full Ubuntu experience on a laptop. I regret i was buying a Macbook :)

---

### Post by gamblor01 on 2013-10-07
> **Cyb3 said:**
> Hi, thanks for the answer. I installed it like you said and it was very bad. The graphics was very wierd and the computer frooze very often. I've now instead of doing all of that downloaded vmware and running it in fullscreen instead. But the speed isn't great, but it works much better though. I created another thread about getting the Dell XPS 13 Developer Edition, and i might just do that very soon to get the full Ubuntu experience on a laptop. I regret i was buying a Macbook :)


That's strange.  I didn't have any freezing issues.  I was just missing actions like two finger back/forward in the browsers.  It actually worked great and benchmarked slightly faster in geekbench while running Ubuntu than OS X.  I may reinstall with rEFIt and install grub2 so that I no longer have to manually copy the boot files.  Hopefully that might resolve the suspend problem as well.

Don't expect graphics to be great though unless you can get the proprietary nvidia driver working.  I tried to use bumblebee and borked the whole thing.  I couldn't seem to get it to function again even after purging all of those packages.  :(


The XPS refresh will be announced next month.  I have been commenting/following a thread about it on Dell's site.  The project lead at Dell (Barton George) just updated everyone recently:

[http://en.community.dell.com/techcenter/os-applications/f/4613/p/19494844/20456261.aspx#20456261](http://en.community.dell.com/techcenter/os-applications/f/4613/p/19494844/20456261.aspx#20456261)


I actually talked to my new boss about getting one and he has the current XPS 13 DE model.  His thoughts were that it was a great ultrabook but not ready to be a full-time development machine.  That's why they ordered me the MB pro.  I got a 512GB SSD and 16GB of RAM...so it's partitioned to be a 50/50 split right now.  I'm hoping I can get Ubuntu running a little better.  The touchpad wasn't perfect but I will be using an external mouse and keyboard while I'm at my desk anyway.

I'm anxious to see the new XPS models unveiled next month.  Not sure I could convince my new job to buy me one but I'm sure someone around the office could use a MB Pro...right???  :P

---

### Post by Cyb3 on 2013-10-08
> **gamblor01 said:**
> That's strange.  I didn't have any freezing issues.  I was just missing actions like two finger back/forward in the browsers.  It actually worked great and benchmarked slightly faster in geekbench while running Ubuntu than OS X.  I may reinstall with rEFIt and install grub2 so that I no longer have to manually copy the boot files.  Hopefully that might resolve the suspend problem as well.

Don't expect graphics to be great though unless you can get the proprietary nvidia driver working.  I tried to use bumblebee and borked the whole thing.  I couldn't seem to get it to function again even after purging all of those packages.  :(


The XPS refresh will be announced next month.  I have been commenting/following a thread about it on Dell's site.  The project lead at Dell (Barton George) just updated everyone recently:

[http://en.community.dell.com/techcenter/os-applications/f/4613/p/19494844/20456261.aspx#20456261](http://en.community.dell.com/techcenter/os-applications/f/4613/p/19494844/20456261.aspx#20456261)


I actually talked to my new boss about getting one and he has the current XPS 13 DE model.  His thoughts were that it was a great ultrabook but not ready to be a full-time development machine.  That's why they ordered me the MB pro.  I got a 512GB SSD and 16GB of RAM...so it's partitioned to be a 50/50 split right now.  I'm hoping I can get Ubuntu running a little better.  The touchpad wasn't perfect but I will be using an external mouse and keyboard while I'm at my desk anyway.

I'm anxious to see the new XPS models unveiled next month.  Not sure I could convince my new job to buy me one but I'm sure someone around the office could use a MB Pro...right???  :P

Haha, yeah you're probably right! :D Yes, i will try again. I've currently own two MB Pros. The one that i'm testing on is a late 2009 model 13 inch. It's slow so i thought i might try Ubuntu on it. But i can record the startup process and in the OS so you can see the problems. I will get back as soon as i can with a video!

I'm anxious too about it, but i'm worried it will cost more than 1500 dollars (approx 10000kr in Sweden). I want to get the CI7 8GB RAM model. The time will tell us...

---

### Post by Cyb3 on 2013-10-08
I've now recorded a video of the problem. But after the startup process i didn't see any problem with the graphics now. I downloaded the NVIDIA drivers and it works OK. However... It shows me some messages on the screen under the startup that i don't understand:

[http://www.youtube.com/watch?v=vwuOv78N1ss](http://www.youtube.com/watch?v=vwuOv78N1ss)

---

### Post by gamblor01 on 2013-10-10
Oh wow.  That doesn't look right.  I'm running a Macbook Pro 9,1 (it's the "mid 2012" model) so I'm sure that is why our experiences might be different.  Your model will just have 2 nvidia cards in it (9400 and 9600GT probably?).  Mine has the Intel chip on the i7 and then also a 650M...so I would need bumblebee to make it work to its full potential while you do not.

I'm not sure about any of the messages...looks like it might be caused by something with the fact that it's looking for EFI files but it's running in CSM mode (BIOS emulation) due to the fact that you're dual booting?  If you're just going to run Ubuntu only you are probably fine but apparently it's super dangerous to run a hybrid MBR like you are doing:

[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)


For what it's worth I found a much better setup (and am running it now!) that uses rEFInd, boots in EFI mode so it avoids the hybrid MBR, and doesn't require me the copy over the new kernel and ramdisk each time a kernel update occurs.  The steps are here:

[http://blog.kylebarlow.com/2013/05/installing-ubuntu-1304-raring-ringtail.html](http://blog.kylebarlow.com/2013/05/installing-ubuntu-1304-raring-ringtail.html)


I guess I just need to remove the old vmlinuz/initrd files from the /boot directory otherwise rEFInd shows multiple options to boot Ubuntu when I start.  But I'm OK with that.  I can test the new kernel and once I'm sure it boots up and works it is easy enough to just delete/rename/move the files I no longer want so they don't get picked up by rEFInd when it's first starting up and scanning for files.

One last thing...the fact that you see the nvidia splash screen indicates that you manually installed the drivers by running the executable install file?  I would not recommend that -- it's much easier to just run "apt-get install nvidia-current" and let the package manager handle everything for you.




Oh and you don't need TWO macbook pros.  What you need is a machine that boots Ubuntu out of the box and therefore doesn't require you to mess with all of these ridiculous issues that we are discussing here.  Sell one and then buy the new XPS with Ubuntu.  You should be able to fetch a reasonable amount of money for one of your two macbook pros...money that you can put toward the purchase of a machine that was meant to run Linux from the start.

;)

---

### Post by Ferren_MacIntyre on 2013-10-12
After several years of intermittent efforts to install one or another from the Ubuntu zoo (using rEFIt and then rEFInd), I--with the help of 2 MIT visitors from the US and an accumulated 150 years experience subduing operating systems--finally got Ringtail to work under Oracle's VirtualBox, where it is just another Mac app. Since all of my scientific FOSSware (Regress+, Sage, Gerris, AnalySys, MacForth, GenoDive, Calib510, PSPP, R, socsim) installs on Macs with Steve's usual 'Drag A to B', I have no real use for Linux except a couple of games. So far. In the early days of following complex instructions slavishly, I repeatedly produced CDs that wouldn't boot, thumbdrives that never recovered, and giant purplish-green clouds of frustration. All better now, but with the extra layer, a bit sluggish. One of my Linux gurus swore that he would never again try to install Linux on a Mac, however trivial it might be on a Windows PC.

---

### Post by Cyb3 on 2013-10-17
> **gamblor01 said:**
> Oh wow.  That doesn't look right.  I'm running a Macbook Pro 9,1 (it's the "mid 2012" model) so I'm sure that is why our experiences might be different.  Your model will just have 2 nvidia cards in it (9400 and 9600GT probably?).  Mine has the Intel chip on the i7 and then also a 650M...so I would need bumblebee to make it work to its full potential while you do not.

I'm not sure about any of the messages...looks like it might be caused by something with the fact that it's looking for EFI files but it's running in CSM mode (BIOS emulation) due to the fact that you're dual booting?  If you're just going to run Ubuntu only you are probably fine but apparently it's super dangerous to run a hybrid MBR like you are doing:

[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)


For what it's worth I found a much better setup (and am running it now!) that uses rEFInd, boots in EFI mode so it avoids the hybrid MBR, and doesn't require me the copy over the new kernel and ramdisk each time a kernel update occurs.  The steps are here:

[http://blog.kylebarlow.com/2013/05/installing-ubuntu-1304-raring-ringtail.html](http://blog.kylebarlow.com/2013/05/installing-ubuntu-1304-raring-ringtail.html)


I guess I just need to remove the old vmlinuz/initrd files from the /boot directory otherwise rEFInd shows multiple options to boot Ubuntu when I start.  But I'm OK with that.  I can test the new kernel and once I'm sure it boots up and works it is easy enough to just delete/rename/move the files I no longer want so they don't get picked up by rEFInd when it's first starting up and scanning for files.

One last thing...the fact that you see the nvidia splash screen indicates that you manually installed the drivers by running the executable install file?  I would not recommend that -- it's much easier to just run "apt-get install nvidia-current" and let the package manager handle everything for you.




Oh and you don't need TWO macbook pros.  What you need is a machine that boots Ubuntu out of the box and therefore doesn't require you to mess with all of these ridiculous issues that we are discussing here.  Sell one and then buy the new XPS with Ubuntu.  You should be able to fetch a reasonable amount of money for one of your two macbook pros...money that you can put toward the purchase of a machine that was meant to run Linux from the start.

;)

I definitely don't need 2 Macbooks. But i'm sad of the resale value :(. But i totally won't be dealing with Linux on Macbooks anymore and when the hardware of the Macbook is crap i will NEVER go that Apple road again. Beautiful machines but borring as hell. But i will save some money and then buy the newer Dell XPS Developer Edition. :)

---

