---
title: "[SOLVED] 8.10 on Aluminum macbook issues"
date: 2008-10-30
forum: Apple Hardware Users
---

### Post by m.musashi on 2008-10-30
I have installed Ubuntu 8.10 on a new aluminum macbook (5,1) but I can't boot. I used boot camp to partiton and then followed mainly the [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) guide. I did add a partition for swap as when I tried to use just sda3 for / and no swap it gave an error about that. I could try again if that may be the issue. The guide does say more than two partitions will cause problems. However, even without it there are still 3 (one fat partition, the hpfs partition and the ext3). When I reboot and hold the option key I only see the mac hd. There is no "windows" option as usual when using boot camp.

I also installed grub to the sda3 partition as I didn't want it to mess with boot camp. However, I also left it as the normal (hd0) option on the first install which also didn't work. The current install is the second try.

As for what works and what doesn't, wifi works out of the box (on the live cd). Graphics is reduced at 1280x720 which isn't bad and it says there is an nvidia driver to install. Sound does not work on the live cd. The lighted keyboard also does not work. I did not try suspend or anything as it was a live cd.

Any suggestions on how to get it to boot? I did install Ubuntu on one of the white macbooks about a year ago and most things worked as well as it booted just fine. What am I missing?

Thanks.

---

### Post by twoodcc on 2008-10-30
i am not sure, but i think you need to install rEFIt for the boot loader, and then you should be able to use that to boot to either ubuntu or mac. i had the same issue on my macbook air today

---

### Post by jimmij01 on 2008-10-30
Have you tried refit?

[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

I have used this on multiple Macbooks and it works great.

---

### Post by m.musashi on 2008-10-30
> **jimmij01 said:**
> Have you tried refit?

[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

I have used this on multiple Macbooks and it works great.

No, I haven't installed it yet. I've used it before but I would like to use the regular mac boot option this time. I know it can be done without rEFIt. I've dual booted the previous generation macbook with just boot camp and it works fine. It does say windows for the Ubuntu volume but I can live with that.

---

### Post by twoodcc on 2008-10-30
i could not get it to work that way on my macbook air today. i would have liked to go that route also

---

### Post by m.musashi on 2008-10-30
> **twoodcc said:**
> i could not get it to work that way on my macbook air today. i would have liked to go that route also

[http://ubuntuforums.org/showthread.php?t=947947&page=13](http://ubuntuforums.org/showthread.php?t=947947&page=13) has some discussion about this. I can't find a solution but seems it's an issue for others. From what I can gather you either have to use rEFIt or "bless" the partition or otherwise re-enable it from OSX. I'm not sure yet how to do that.

---

### Post by twoodcc on 2008-10-30
> **m.musashi said:**
> [http://ubuntuforums.org/showthread.php?t=947947&page=13](http://ubuntuforums.org/showthread.php?t=947947&page=13) has some discussion about this. I can't find a solution but seems it's an issue for others. From what I can gather you either have to use rEFIt or "bless" the partition or otherwise re-enable it from OSX. I'm not sure yet how to do that.

thanks. i'll try to keep an eye on this thread to see if you get it worked out. since i've already got rEFIt working, i guess i'll just stick with it for now

---

### Post by cyberdork33 on 2008-10-30
There is a bug in the installer (it was in hardy too).

You need to install refit and use it to sync the partition tables. once that is done, you can remove it if you like.
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by m.musashi on 2008-10-30
> **cyberdork33 said:**
> There is a bug in the installer (it was in hardy too).

You need to install refit and use it to sync the partition tables. once that is done, you can remove it if you like.
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

Thanks. That seems to have fixed it. At least now it boots but there a few other issues to fix (graphics, sound, touchpad, etc that everyone seems aware of).

I would really like to not have to use rEFIt. It's not that I have an issue with it. It's just that I'd prefer my work computer not to be obvious about having been modified. Is this possible or is rEFIt currently required? You mentioned I can remove it once it's booting right. So if I just uninstall it the normal mac dual boot option works (i.e. pressing option key to get boot menu)?

---

### Post by kosumi68 on 2008-10-31
> **m.musashi said:**
>  It's just that I'd prefer my work computer not to be obvious about having been modified.


In that case you might also be interested in this: [http://ubuntuforums.org/showthread.php?t=865180](http://ubuntuforums.org/showthread.php?t=865180)

It might well let you run *ubuntu* at work without anyone noticing ;-)

---

### Post by cyberdork33 on 2008-10-31
> **m.musashi said:**
> I would really like to not have to use rEFIt... Is this possible or is rEFIt currently required? You mentioned I can remove it once it's booting right. So if I just uninstall it the normal mac dual boot option works (i.e. pressing option key to get boot menu)?
Yes it will work as you are suggesting:
[http://refit.sourceforge.net/doc/c1s3_remove.html](http://refit.sourceforge.net/doc/c1s3_remove.html)

The "real" requirement for refit is the ability to sync the partition tables. Once that is done refit is not needed (unless you need to sync them again I guess...) You can also get a tool in Ubuntu to sync the tables (I think it is gptsync).

---

### Post by m.musashi on 2008-10-31
Thanks again. I went ahead and removed rEFIt and it's booting normally for both OSs. Ubuntu doesn't work real well yet though. I've been following the other thread I linked above and I see a lot of discussion about the trackpad, keyboard lights, power management, etc.

I installed applesmc-dkms,bcm5974-dkms,and hal-applesmc but I'm not sure if just installing is all I need to do or if they have to be setup. I'm guessing the latter as nothing seemed to change - i.e. no keyboard lights, no right click or tapping and the trackpad is jerky and freezes semi-frequently. I know all the kinks are probably not worked out yet, but I'm wondering if I've done what I need to to be a well off as possible.

The wiki page that was started is nice, but a bit more how to info would be nice. I'd be happy to add the right info once I know what the fixes are. If anyone can give me a quick rundown I'll add the info. I'll also add the info about rEFIt as it seems a crucial bit of info.

---

### Post by cyberdork33 on 2008-10-31
> **m.musashi said:**
> I'll also add the info about rEFIt as it seems a crucial bit of info.
Unfortunately, you shouldn't need it, but there is a bug that wipes the MBR partition table for some reason.

[https://bugs.edge.launchpad.net/mactel-support/+bug/222126](https://bugs.edge.launchpad.net/mactel-support/+bug/222126)

---

### Post by m.musashi on 2008-10-31
Well, I went ahead and added a section on installing and the boot issue for anyone like me that was a bit lost. Hopefully that was okay.

[https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum)

---

### Post by cyberdork33 on 2008-10-31
> **m.musashi said:**
> Well, I went ahead and added a section on installing and the boot issue for anyone like me that was a bit lost. Hopefully that was okay.

[https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum)
Excellent!

That is what a wiki is for!

---

### Post by kosumi68 on 2008-10-31
> **m.musashi said:**
> Thanks again. I went ahead and removed rEFIt and it's booting normally for both OSs. Ubuntu doesn't work real well yet though. I've been following the other thread I linked above and I see a lot of discussion about the trackpad, keyboard lights, power management, etc.

I installed applesmc-dkms,bcm5974-dkms,and hal-applesmc but I'm not sure if just installing is all I need to do or if they have to be setup. I'm guessing the latter as nothing seemed to change - i.e. no keyboard lights, no right click or tapping and the trackpad is jerky and freezes semi-frequently. I know all the kinks are probably not worked out yet, but I'm wondering if I've done what I need to to be a well off as possible.

The wiki page that was started is nice, but a bit more how to info would be nice. I'd be happy to add the right info once I know what the fixes are. If anyone can give me a quick rundown I'll add the info. I'll also add the info about rEFIt as it seems a crucial bit of info.

Thanks for understanding that the new macbooks are very much work in progress - they are, after all, brand new. Older models are pretty well covered in the kernel.

For applesmc, you need to make sure /etc/modules contains the line 'applesmc'. This module should in principle be loaded by default, but due to its many problems historically (problems that has been fixed recently), it was deliberately left out by the ubuntu team. This will most likely change to the next release. Also, it could in principle be added by the applesmc-dkms package, but it does not solve the problem for all pre-aluminum macbook users, who do not need this package.

Regarding the trackpad, there is currently an issue with making the HID modules ignore the new device id. I will most likely update the bcm5974-dkms package to remove this problem. Meanwhile, you might need to follow the instructions here: [http://ubuntuforums.org/showpost.php?p=6070087&postcount=170](http://ubuntuforums.org/showpost.php?p=6070087&postcount=170). Also, if you have trackpad settings set in /etc/X11/xorg.conf, you would want to remove them, since those settings are confusing the new fdi interface (/usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi).

Hope this helps!

---

### Post by m.musashi on 2008-10-31
> **kosumi68 said:**
> Thanks for understanding that the new macbooks are very much work in progress - they are, after all, brand new. Older models are pretty well covered in the kernel.

Certainly. I'm just happy there are people willing and able to help others. I'm sure we get anxious at times for our beloved OS to work but always understanding.

> For applesmc, you need to make sure /etc/modules contains the line 'applesmc'. This module should in principle be loaded by default, but due to its many problems historically (problems that has been fixed recently), it was deliberately left out by the ubuntu team. This will most likely change to the next release. Also, it could in principle be added by the applesmc-dkms package, but it does not solve the problem for all pre-aluminum macbook users, who do not need this package.

Makes sense. I'll check that as soon as I can. I thought I noticed that the install set up the module but maybe it was a different one or something else entirely.

> Regarding the trackpad, there is currently an issue with making the HID modules ignore the new device id. I will most likely update the bcm5974-dkms package to remove this problem. Meanwhile, you might need to follow the instructions here: [http://ubuntuforums.org/showpost.php?p=6070087&postcount=170](http://ubuntuforums.org/showpost.php?p=6070087&postcount=170). Also, if you have trackpad settings set in /etc/X11/xorg.conf, you would want to remove them, since those settings are confusing the new fdi interface (/usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi).

I didn't modify xorg.conf. I'll give those instructions a try.

> Hope this helps!

It certainly does. I'll post back with results.

---

### Post by kosumi68 on 2008-10-31
> **m.musashi said:**
> Certainly. I'm just happy there are people willing and able to help others. I'm sure we get anxious at times for our beloved OS to work but always understanding.



Makes sense. I'll check that as soon as I can. I thought I noticed that the install set up the module but maybe it was a different one or something else entirely.



I didn't modify xorg.conf. I'll give those instructions a try.



It certainly does. I'll post back with results.

There is a new version of bcm5974 available - please reload the sources before installing, and it should appear automatically.

---

### Post by m.musashi on 2008-11-01
> **kosumi68 said:**
> There is a new version of bcm5974 available - please reload the sources before installing, and it should appear automatically.

Thanks for the info and the work but for some reason it refuses to upgrade. It get a message about it being "kept back". Should I force it or is something going on?

---

### Post by m.musashi on 2008-11-01
> **m.musashi said:**
> Thanks for the info and the work but for some reason it refuses to upgrade. It get a message about it being "kept back". Should I force it or is something going on?

Okay, never mind. I used the update tool rather than apt-get from cli and it worked fine. Not sure why it didn't from a terminal. I also added the applesmc to /etc/modules. After a reboot my keyboard lit up to my extreme pleasure. Thanks.

However, I'm still not getting a left click out of the trackpad and no tapping. Normally on non mac hardware I would install gsynaptics to manage tapping. Is likely to help here? My gut feeling says no but thought I'd ask.

Wait, I take that back. A two finger click is a right click. So it's just the tapping that isn't working for me. Wow, that was some magic pill. Nearly everything is working.

---

### Post by kosumi68 on 2008-11-01
> **m.musashi said:**
> Okay, never mind. I used the update tool rather than apt-get from cli and it worked fine. Not sure why it didn't from a terminal. I also added the applesmc to /etc/modules. After a reboot my keyboard lit up to my extreme pleasure. Thanks.


There were some changes to the build repository yesterday, due to the new release. Maybe it hade something to do with it.

> 
However, I'm still not getting a left click out of the trackpad and no tapping. Normally on non mac hardware I would install gsynaptics to manage tapping. Is likely to help here? My gut feeling says no but thought I'd ask.


The synaptics driver is in a transition from using the notorious SHMConfig option to a more straight-forward and safe properties protocol. This affects all programs designed to work with synaptics, so problems are foreseeable at this time.

> 
Wait, I take that back. A two finger click is a right click. So it's just the tapping that isn't working for me. Wow, that was some magic pill. Nearly everything is working.

Lovely. Getting the kernel module plus synaptics to understand the difference between holding one finger on the pad, then clicking with the other for left click, and clicking the pad with two fingers from one hand for a right click, is a challenge...

---

### Post by cyberdork33 on 2008-11-01
> **m.musashi said:**
> Okay, never mind. I used the update tool rather than apt-get from cli and it worked fine. Not sure why it didn't from a terminal. I also added the applesmc to /etc/modules. After a reboot my keyboard lit up to my extreme pleasure. Thanks.

To install held back packages you have to do a 'dist-upgrade' rather than just 'upgrade'.

---

### Post by m.musashi on 2008-11-01
> **kosumi68 said:**
> The synaptics driver is in a transition from using the notorious SHMConfig option to a more straight-forward and safe properties protocol. This affects all programs designed to work with synaptics, so problems are foreseeable at this time.

So does that mean that at the moment tapping is not an option? I guess it's not a big deal but the trackpad on these is really well suited to tapping and less so to clicking (too hard to press towards the top and kind of loud).


> Lovely. Getting the kernel module plus synaptics to understand the difference between holding one finger on the pad, then clicking with the other for left click, and clicking the pad with two fingers from one hand for a right click, is a challenge...

A challenge that was met it seems. Congrats and thanks. Too bad Apple isn't a bit more open since they certainly got a nice leg up from the community to begin with. Although I thought I read that they did make quite a few contributions from Darwin (I think).

> **cyberdork33 said:**
> To install held back packages you have to do a 'dist-upgrade' rather than just 'upgrade'.

Ah, good to know. I see that from time to time and usually just waited as eventually it fixes itself.

---

### Post by kosumi68 on 2008-11-01
> **m.musashi said:**
> 
So does that mean that at the moment tapping is not an option? I guess it's not a big deal but the trackpad on these is really well suited to tapping and less so to clicking (too hard to press towards the top and kind of loud).


Not at all - you can change it in five ways, just not at the same time:

1. Modify the settings in /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi. This is not recommended, because your settings will be lost with the next update to the synaptics driver.

2. Copy the settings over to /etc/hal/fdi/policy/ and change them there. This is the recommended way in Intrepid currently.

3. Turn on the SHMConfig option, and use gsynaptics to modify the settings. This might not work well, because of conflicts between the fdi functions and the shared memory functions. Discouraged.

4. Add these lines to /etc/X11/xorg.conf:
```

Section "ServerFlags"
     Option "AutoAddDevices" "off"
EndSection

```
then you can modify /etc/X11/xorg.conf as in Hardy. Mind you that the default set of values is important: You find settings here: [http://web.comhem.se/rydberg/Bits/](http://web.comhem.se/rydberg/Bits/). This way is deprecated, and bound to give you troubles sooner or later.

5. Modify settings using the synclient program. Currently requires SHMConfig, but will eventually work using the properties interface. Thus currently discouraged, but should work fine in Jaunty.

> 
A challenge that was met it seems. Congrats and thanks.


Actually, this problem is not solved yet, but it might be eventually.

---

### Post by calebio on 2008-11-01
> **kosumi68 said:**
> Not at all - you can change it in five ways, just not at the same time:

1. Modify the settings in /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi. This is not recommended, because your settings will be lost with the next update to the synaptics driver.

2. Copy the settings over to /etc/hal/fdi/policy/ and change them there. This is the recommended way in Intrepid currently.

...

kosumi, you're a genius! Option 2 finally solved this problem for me, allowing me to tap-to-click on my MacBook Pro (late 2008). This is so much more elegant and quieter than click-to-click on this computer.

---

### Post by calebio on 2008-11-02
> **kosumi68 said:**
> Not at all - you can change it in five ways, just not at the same time:...

I have updated [https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum) with these instructions, since they worked for me.

---

### Post by kosumi68 on 2008-11-02
> **calebio said:**
> I have updated [https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum) with these instructions, since they worked for me.

Great! Were there more problems in this thread, or can it be switched to solved?

---

### Post by guggi on 2008-11-02
option 2 is the way :-)
can tap my trackpad now. thx for ur efforts, solved!

cheers

---

### Post by m.musashi on 2008-11-02
> **kosumi68 said:**
> Great! Were there more problems in this thread, or can it be switched to solved?

Well, I tried to follow the option 2 directions but after copying the file to /etc/hal/fdi/policy (which is incorrect in the wiki directions as /etc is left off) I'm not sure what to do. Just copying has no effect. The wiki page mentions editing but the file is rather long and complex. I'm not sure what to add or where to add it. So, for me, I have not been able to have the same success as others.

EDIT: I went and took a closer look at the 11-x11-synaptics.fdi file and I'm guessing that changing a 0 to a 1 in a merge line turns the option from off to on. I when ahead and did that for TapButton1 and now a single finger tap works. Very nice. However, I noticed that changes to TapButton2 and TapButton3 have no effect. Also, I'm guessing that RBCornerButton refers to the option is OSX to have the bottom right corner be a right click. I set that to 1 as well with no effect. Are these simply options that are not working yet or am I doing something wrong? Thanks.

Also, the trackpad likes to freeze a lot. I've heard others mention this too so maybe something we live with for now.

There are also a few other issues that I've discovered. While keyboard lights work, I cannot change the brightness of the screen with the F1 and F2 keys. This may be a known issue but I'm not sure.

Sound does not work from speakers even after adding the option to /etc/modprobe.d/options as mentioned on the wiki page. I go get sound from headphones.

If there are fixes for these issues I'd love to know. Otherwise, I guess what can be solved has been. Thanks for the help.

---

### Post by kosumi68 on 2008-11-02
> **m.musashi said:**
> 
Also, the trackpad likes to freeze a lot. I've heard others mention this too so maybe something we live with for now.


Actully, now that it has been confirmed that several people are experiencing freezes, we should start tracking down *what* it is that makes the computer freeze. It could be a lot of different things, and being random, it can be very tricky to find. 
[http://ubuntuforums.org/showthread.php?t=966834](http://ubuntuforums.org/showthread.php?t=966834)

> 
There are also a few other issues that I've discovered. While keyboard lights work, I cannot change the brightness of the screen with the F1 and F2 keys. This may be a known issue but I'm not sure.


Apparently, the new nvidia card is not supported in RandR yet. When it is, I'm sure we will hear about it.

> 
Sound does not work from speakers even after adding the option to /etc/modprobe.d/options as mentioned on the wiki page. I go get sound from headphones.


You might have something to add to this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/218696](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/218696)

---

### Post by cyberdork33 on 2008-11-02
> **m.musashi said:**
> EDIT: I went and took a closer look at the 11-x11-synaptics.fdi file and I'm guessing that changing a 0 to a 1 in a merge line turns the option from off to on. I when ahead and did that for TapButton1 and now a single finger tap works. Very nice. However, I noticed that changes to TapButton2 and TapButton3 have no effect. Also, I'm guessing that RBCornerButton refers to the option is OSX to have the bottom right corner be a right click. I set that to 1 as well with no effect. Are these simply options that are not working yet or am I doing something wrong? Thanks.
Actually, I think for those button options, the number you set tells the option what button it emulates, with 1 = left mouse button, 2 = middle mouse button, 3 = right mouse button. So to make the Right Bottom Corner act as the right mouse button, you should set RBCornerButton = 3

The same is true for the TapButtonX options. TapButton1 is the single-finger tap, TapButton2 is a two-finger tap, etc. So if I wanted to make a two-finger tap be a right click I would set TapButton2 = 3.

You can find details of all the synaptics options in the man page
```
man synaptics
```

---

### Post by m.musashi on 2008-11-02
> **cyberdork33 said:**
> Actually, I think for those button options, the number you set tells the option what button it emulates, with 1 = left mouse button, 2 = middle mouse button, 3 = right mouse button. So to make the Right Bottom Corner act as the right mouse button, you should set RBCornerButton = 3

The same is true for the TapButtonX options. TapButton1 is the single-finger tap, TapButton2 is a two-finger tap, etc. So if I wanted to make a two-finger tap be a right click I would set TapButton2 = 3.

Ah, now I get it. It all works beautifully now but the bottom right corner stuff still doesn't seem to have any effect yet.

Thanks. Although, now that the tapping works I'm stuck with the other issue of inadvertent touches moving the cursor around when I'm trying to type. It's always something :). I'll play around with things now that it's all more or less working and see what seems the best solution for me.

Thanks to cyberdork33 and kosumi68 for all the help. I'm marking it solved now but if any additional info comes to light on the touchpad, sound, screen brightness, etc. I'd appreciate hearing. I'll watch the wiki too.

---

### Post by m.musashi on 2008-11-02
Well, one more little issue. I've noticed that it doesn't want to wake up from sleep mode. It go  in just fine and the little light "breathes" but when trying to wake by pressing the space bar I here a drive or some other sound that indicates it is trying to wake but nothing happens. If I hold the power button for a few seconds sometimes it wakes and sometimes not. If I hold it too long it just shuts off.

Is there a tweak to fix this or just another issue to live with for now?

Thanks.

---

### Post by cyberdork33 on 2008-11-02
> **m.musashi said:**
> Is there a tweak to fix this or just another issue to live with for now?
Probably something that will need work to fix. Suspend almost never just works on new hardware. It is likely something to do with the graphics driver not waking correctly.

---

### Post by m.musashi on 2008-11-04
Just an addition about power management for anyone watching this. I noticed that it is just taking a long time to wake. After pressing a button to start the waking process, it takes about 30 seconds for it to actually wake up but it does. It then takes about 15 seconds more (after entering password to unlock screen) for the wifi to start searching again for a connection. However, it also connects and continues working.

Therefore, it seems that it is slow to wake but it does work. I was just being impatient. This might be good for others to know.

---

### Post by Nikos.Alexandris on 2008-11-05
Hi!

Again, not really sure where to post this (or make a new thread). I left the MBP aluminum to run till it eats all battery power up. And I can confirm that the last message stated the computer is about to shut-down (with power left for less than a minute!) and it turned-off (=powered off) while the shut-down process was on-going. I have "show text during boot" enabled (through StartUp-Manager) and the computer never really made to complete the shut-down process.

I assume this is not normal. Can anybody else test this? Do we need a bug report?

Kind regards, Nikos

---

