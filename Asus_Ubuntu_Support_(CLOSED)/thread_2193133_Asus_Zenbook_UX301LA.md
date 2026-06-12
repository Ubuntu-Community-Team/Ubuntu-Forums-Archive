---
title: "Asus Zenbook UX301LA"
date: 2013-12-11
forum: Asus Ubuntu Support (CLOSED)
---

### Post by pantale on 2013-12-11
Hi,

As anyone tried to install Ubuntu on an Asus Zenbook UX301LA ?
I tested 13.10 with a live USB stick and found quite everything working out of the box except the following:
Bluetooth
Functions keys to adjust bightness of the screen

Everything else including:
Wifi
Screen with touch screen 2650x1440

Now I'm going to install a dual boot with Windows 8.1 for Ubuntu massive usage.

Olivier

---

### Post by jakslev2 on 2013-12-12
How is it going?

---

### Post by pantale on 2013-12-14
Hi,

Unfortunately for the moment my laptop has been returned to Asus because of a battery problem. I was unable to switch it on whether the AC was plugged or not. I'm waiting for another one for replacement. 

I will of course install ubuntu on it as I'm only using linux for my work (ubuntu is installed for me on an UX31e, a R715 Dell,...)

Olivier

---

### Post by m-bachmann on 2013-12-19
Hi Olivier,

I will also definitively be interested in your report. Especially how it behaves when you plug in external, possibly hi-res displays. Maybe you even get a chance to plug it into an 4k / UHD display and see if it can deliver the full resolution. I would gladly send you a postcard in return with a written thank-you. :-)

- Martin

---

### Post by kifer on 2014-01-04
I installed  (Mint 16) without problems. The trick was to initially disable secure boot and launch CSM in the BIOS.

The brightness function keys indeed don't work, but bluetooth does out of the box.
However, touch screen doesn't work for me.

UPDATE: just 2 weeks into the use, the battery stopped charging and it goes back for repairs. I have also experienced fan racing problems on cold start, which can be stopped only by turning the unit off.
 Based on my experience and on what I read, these two appear to be a common problem with this model.

UPDATE: Upgrading BIOS to v206 didn't fix the problems with the fan and the battery.

---

### Post by kifer on 2014-01-04
I installed  (Mint 16) without problems. The trick was to initially disable secure boot and launch CSM in the BIOS.

The brightness function keys indeed don't work, but bluetooth does out of the box.
However, touch screen doesn't work for me.

---

### Post by aceat64 on 2014-01-05
> **pantale said:**
> Hi,

Unfortunately for the moment my laptop has been returned to Asus because of a battery problem. I was unable to switch it on whether the AC was plugged or not. I'm waiting for another one for replacement. 

I will of course install ubuntu on it as I'm only using linux for my work (ubuntu is installed for me on an UX31e, a R715 Dell,...)

Olivier

You are the 3rd person I know of with battery issues. My ux301la won't charge most of the time, this is the 2nd one I have had with the exact same issue.

---

### Post by pantale on 2014-01-06
I'm always waiting for the second one. Very long, seems there's stock problems for the model I have UX301LA-DE002H (512 Gb raid 0, 8Mb, WQHD touch screen).
Hope to receive the replacement laptop this week !

And hope there will be no battery problems with this one !

---

### Post by David_Semeria on 2014-01-16
Hi kifer, can you confirm bluetooth and external display still work fine with Mint 16?
Neither does for me with ubuntu 13.10, however touch screen does.

---

### Post by mistermagio on 2014-01-18
Hey everyone, writing from my own UX301 running Ubuntu 13.10.

Ran into the same problems as those mentionned above, mine too stopped charging after a while, and mine too sometimes boots up with fans at full speed.
Thing is, I have found a solution (though it's neither permanent nor convenient) for the charging thing, that does not involve sending it back to Asus.

For some reason, if you boot from a Windows 8(.1) Usb Key, then shut it off without installing anything, and then reboot on Ubuntu, it will start charging again (if your battery was under 94-5% at that point, otherwise it will start charging when it crosses that line that I have not yet defined perfectly. It does reach 100% that way).
Now I have absolutely no clue why that works, but it does, for some reason, which is why I'm now carrying a Windows 8.1 USB (created with an ISO and Unetbootin, somehow that worked !) with me everywhere.

Because unfortunately, it does not work indefinitely. After a while (once lasted me 2 weeks and many reboots, another time I had to redo it a few hours after the last time), the process has to be repeated, and that's when it gets even weirder. Because the fan issue on boot seems to mean that the computer won't charge anymore, even if it boots normally afterwards. The LED on the Asus AC Adapter starts blinking between red and green at that point, too.

As you can see, I actually experimented a lot about that stuff, now it's not really stressful anymore, it's just really not convenient.

So I have no idea why it doesn't charge, no idea why it boots with fan at full speed from time to time, no idea how those things are related, no idea why my "fix" is a fix,... All I know is that for some reason all that stuff is true.

So yeah, hope that will help some of you guys, and if someone can make sense of that, that would be wonderful !

Edit: On a thread I created about this issue a while ago, a guy proposed a more convenient solution, however I have not had the occasion (thankfully) to test it out.
His solution is to Unplug the laptop while it's booted up, force it to shut down by pressing the power button for a while, then plug it in again, and look out for the blinking I was mentionning above. If it's not there, it's charging again.

---

### Post by drpauled on 2014-01-22
For anyone else who finds this while trying to get ubuntu installed, be aware that 12. is not new enough for the hardware but 13.10 is (seeing mistermagio's post was what showed this to me). I haven't tested 13.04. 

Has anyone been able to get the camera working? This seems to be another issue with the basic install.

---

### Post by pantale on 2014-01-24
My Laptop is Back.

Second try to install Kubuntu on it !

---

### Post by pantale on 2014-01-28
Well, here is a summary of what I have done.

First I broke the RAID0. It's a software one, so broke it using a live USB kubuntu.
New partition:
sda : EFI (300Mo) + Windows (NTFS 128 Go) + swap (8 Go) + ubuntu root (30 Go) + share (NTFS 85 Go)
sdb : home (256 Go)

Install Kubuntu 13.10 + Windows 8.1 dual boot.
Disabled in Windows 8 the hybrid hibernation (true power off)

Everything is working fine except the bluetooth for the moment.

---

### Post by carvalho-ruben on 2014-01-28
Thanks for that Pantale. Any idea where I can find more information on how to "break" the RAID0? I am considering doing this but don't want to mess things up.

Cheers

---

### Post by pantale on 2014-01-29
What I have done is the following:

1) On the pre-installed Windows 8 session: select Parameters - On/Off - Reboot and press reboot with the Shift key on. This will allow you to enter bios setup
2) In the bios, disable Fast Boot to allow to boot from a USB stick
3) Boot on your Live USB xUbuntu and select test the live usb
4) open a terminal
5) Enable your network
6) type apt-get install gparted gdisk
7) Use : **gdisk /dev/sda** to delete all partitions (there is 6 partitions)
8) Do the same on : **gdisk /dev/sdb** to delete all partitions (there is 6 partitions)
9) Reboot the live session

You now have no more raid0 and can use gparted or anything similar to partition **sda** and **sdb**.

---

### Post by carvalho-ruben on 2014-01-29
So no need to actually change the "RAID" setting in the BIOS to AHCI? Simply deleting all the partitions is enough?

---

### Post by pantale on 2014-01-29
No you don't need this change.
I have switched to AHCI further after one or two days. Better to do this before installing windows 8 because it will not boot anymore if you select ahci after the install. A google search may help you.
Or you have to reboot windows 8 using "safe mode" after changing the parameter in the bios in order to auto enable ahci in windows. Next boot wil be ok.

---

### Post by pantale on 2014-01-29
Found that disabling XHCI Pre-Boot Mode in BIOS makes the Bluetooth work. But unfortunately it disable the Usb 3.0 interface. Therefore external disks speed transfer drastically decrease.
Also when this parameter is disabled you can have the backlight keyboard operate.

---

### Post by carvalho-ruben on 2014-02-01
Excellent stuff. thanks for the info again.

---

### Post by pantale on 2014-02-04
Found something interesting !

Adding acpi_osi= to the kernel paremeters in grub makes the f5/f6 keys change the backlight level, but the is no relation with the backlight control through the sliders.
Have to put 'acpi_osi=' without any parameter. I know it's quite strange but it works, and I don't know why ?

Olivier

---

### Post by kifer on 2014-02-14
The external monitor works, but bluetooth does not.  After reinstalling, I noticed that touchscreen worked. But after downloading new packages and updates, it stopped working.

---

### Post by kifer on 2014-02-14
> **David_Semeria said:**
> Hi kifer, can you confirm bluetooth and external display still work fine with Mint 16?
Neither does for me with ubuntu 13.10, however touch screen does.



The external monitor works, but bluetooth does not. After reinstalling, I noticed that touchscreen worked. But after downloading new packages and updates, it stopped working.

---

### Post by drpauled on 2014-02-20
> **pantale said:**
> Found something interesting !

Adding acpi_osi= to the kernel paremeters in grub makes the f5/f6 keys change the backlight level, but the is no relation with the backlight control through the sliders.
Have to put 'acpi_osi=' without any parameter. I know it's quite strange but it works, and I don't know why ?

Olivier

For those ignorant of how to do this (like I was) edit the grub file:
*/etc/default/grub*

The acpi_osi= is added to the line (or a least the line on my rather unmodified version):
*GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"*
to give you:
*GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi= "*

then run:
*sudo update-grub*

The keys then work after restart, thanks to Oliver's discovery.

---

### Post by belgianfries on 2014-02-22
Thanks for sharing all this useful info! A friend just got himself a UX301LA and I'm going to install (k)Ubuntu on it - and try to contribute anything additional here.

Can anyone give me a hint on what I have to take care of to be able to restore Windows if necessary after an installation of (k)Ubuntu?

---

### Post by rifak on 2014-02-22
> **drpauled said:**
> For those ignorant of how to do this (like I was) edit the grub file:
*/etc/default/grub*

The acpi_osi= is added to the line (or a least the line on my rather unmodified version):
*GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"*
to give you:
*GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi= "*

then run:
*sudo update-grub*

The keys then work after restart, thanks to Oliver's discovery.

Can confirm this has solved the f5/f6 fn brightness keys. Slight aside though, I'm using an Asus Vivobook S/Q301LA model, so I'm thinking the underlying boot parameters are going to be applicable across most of the newer Asus ultrabooks.

---

### Post by Gavyn_Long on 2014-03-30
Hello everyone, I've just got my grubby mitts on a UX301LA and most things worked out of the box (touchscreen is fine with the latest updates). The acpi_osi= argument made the brightness work.

However, I'm still stuck on the bluetooth. I've tried installing blueman - no change. rfkill list shows they are always on. The only other thing I've found is the XHCI setting in the BIOS, this works, annoyingly for one boot only, so I suspect that's not it. As it stands, a bluetooth is unusable until a solution is found.

Has anyone had any success with bluetooth?

---

### Post by pantale on 2014-03-31
For bluetooth, in Bios, deselect XHCI. This works fine without any problem except that USB 3.0 is disabled. This is the only workaround I found, but I don't have any problem with reboot. This is a permanent change for me.

---

### Post by Chris_Welty on 2014-06-01
Hi all.  I've been working for two days on my Asus UX301 with Ubuntu 14.04LTS.  Using pantale's fix for the screen brightness keys as well.

Most things are working well - its a beautiful machine, that's for sure.

I'm seeing a few minor problems, wondering if anyone has experienced/looked into these:

Flakey wifi with low signal: the intel 7260 wireless interface drops every few minutes when the signal strength is low.  I'm finding reports of this behavior with others who have this wifi hardware ([https://gist.github.com/aboisvert/9357500](https://gist.github.com/aboisvert/9357500)). I will report back on my experience if I don't hear.

The touchscreen works OK, but not great.  In windows 8.1 you could use tablet-style gestures (swipe & pinch) for scrolling, zooming, but in Ubuntu it only seems to work as a single-button mouse, with a few multi-touch gestures (4 fingers brings up search, 3 fingers resizes the window - which is great on the ux301since the borders are so fine they are hard to grab) .  Ive seen articles on this ([http://www.html5rocks.com/en/mobile/touchandmouse/](http://www.html5rocks.com/en/mobile/touchandmouse/)) but haven't yet investigated.

Chrome doesn't see the touchscreen input at all.

I see Ubuntu forums has shut down the asus support forum since APril 4  - is there a community for ux301 users somewhere?

Chris

---

### Post by maurix2 on 2014-07-31
About the battery issue: mine has too, seems like a firmware problem. A workaround is to let the battery drain to 0%, after that it will charge again.

The fastest method I can think of is opening 4 terminals (one for each cpu core) and run

dd if=/dev/zero of=/dev/null

This will cause a high cpu load and make the battery drain in a little time.

---

