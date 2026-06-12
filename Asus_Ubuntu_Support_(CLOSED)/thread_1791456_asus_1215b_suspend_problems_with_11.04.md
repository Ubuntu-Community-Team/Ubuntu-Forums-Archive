---
title: "asus 1215b suspend problems with 11.04"
date: 2011-06-26
forum: Asus Ubuntu Support (CLOSED)
---

### Post by moorent on 2011-06-26
Hi there.

I'm new to linux but have my system running perfectly except for whenever I try to resume from suspension (lid close or otherwise). The system will hang on a black screen (no backlight) and won't return to normal unless I hard reset.

I've read that this is a pretty common problem but have yet to find a working solution. Is there any hope?

---

### Post by gmargo on 2011-06-26
My Asus 1201t does the same thing with 11.04 Natty, with the default grub settings.

Try this:

[LIST]
[*]edit the file **/etc/default/grub** (make a backup first!)
[*]find the GRUB_CMDLINE_LINUX_DEFAULT entry
[*]replace the value (default is "quiet splash") with "nomodeset" (keep the quotes)
```

GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"

```
[*]run the "update-grub" command
[*]reboot
[/LIST]
Actually you can probably just add "nomodeset" to the "quiet splash" string, but I haven't tried it since I despise "quiet" and "splash".

---

### Post by moorent on 2011-06-26
this didn't fix the problem. 

The system seems to resume but the screen won't come back on.

---

### Post by Mathias1990 on 2011-06-27
I have the same problem. I work on an ASUS K52J and it won't resume after I close the lid and open it again. The fix did not work. :(

---

### Post by moorent on 2011-06-27
hibernate works fine, I guess i'll use that until this gets fixed.

It's a shame that so many people are experiencing this problem.

---

### Post by Chris11 on 2011-07-04
I have the same problem with a Eee PC 1015 PEM, I tried the fix but now the things are worse....

I can't start gonme any more and the the computer stops on a terminal-like level. I can og in but do no get over terminal level on a black screen. How can I edit /etc/default/grub back to the original version on terminal level? gedit dos not initiate...

Chris

EDIT: I found the command "nano" for editing in the terminal and reversed the changes, Gnome starts again, but still the suspending problem...

---

### Post by rgm3 on 2011-07-08
I too have an Asus EeePC 1215B that does not come back from suspend.  I am not running the proprietary video drivers (yet).

The is particularly annoying because by default the computer wants to suspend when inactive for some period of time.  To avoid problems, I had to go to System -> Preferences -> Power Management and set "Put computer to sleep when inactive for:  Never."  As an aside, the word "Never" there doesn't make sense in the sentence.  It should perhaps be replaced with "eleventy bazillion years."

I do hope that a solution will be found soon!  I'm willing to try anything to help if given some direction.

Things I've tried:
* Disabling kernel mode setting (KMS) via grub options
* Updating to latest BIOS 0401, changelog for which says "Update AGESA module from V1.0.0.2 to V1.0.9.0 for new CPU support."

---

### Post by rgm3 on 2011-07-09
I've got new information.   I installed the ATI Catalyst Control Center via Ubuntu's "Restricted drivers available" GUI and suspend WORKED!  It even resumed quickly, turned on the backlight, and gave me a login prompt.

BUT:

If you ever suspend, even once, it seems that the MBR is corrupted.  After suspending and resuming once, if i then choose "Shutdown" (or sudo poweroff) the system will refuse to turn itself off entirely.  I then hold the power button down for 5 seconds to turn it off.  When I turn it back on, I get a blinking _ cursor for about a minute then "Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key."  I think that this message is from the Windows 7 install on my drive.

I think this means that the MBR has been overwritten.  To fix it, I have to reinstall grub2 as described here:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

The salient command is:
(boot from liveCD)
```
sudo grub-install --boot-directory=/media/0d104aff-ec8c-44c8-b811-92b993823444/boot /dev/sda
```

Where 0d104aff... is specific to your system.

So, suspend works, but either it jacks up grub2 or the hard-poweroff does.   Hibernate does NOT work when the BIOS CPU Information "E6" mode is disabled, but does when that's enabled.

I'd like to try setting up an EFI boot partition as described here:
[http://ubuntuforums.org/showthread.php?t=1741953](http://ubuntuforums.org/showthread.php?t=1741953)

Then, perhaps my suspend and hibernate can both work while using the ATI drivers.

---

### Post by mastergizmo on 2011-07-11
Hello,

> **rgm3 said:**
> I've got new information.   I installed the ATI Catalyst Control Center via Ubuntu's "Restricted drivers available" GUI and suspend WORKED!

Really that worked for you? 
For me to get suspend to ram working (I manually installed catalyst 11.6
maybe its because of that) I had to disable the c6 powersaving mode
in the bios and boot ubuntu with vga=0.
With that I can suspend to ram, but only one time, if I try it again
it hangs with a black screen with backlight on... 

So for now I have given up on that and use suspend to disk if I need suspend :/
Oh and I use the newest bios from the asus website...

> **rgm3 said:**
> 
BUT:

If you ever suspend, even once, it seems that the MBR is corrupted.  After suspending and resuming once, if i then choose "Shutdown" (or sudo poweroff) the system will refuse to turn itself off entirely.  I then hold the power button down for 5 seconds to turn it off.  When I turn it back on, I get a blinking _ cursor for about a minute then "Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key."  I think that this message is from the Windows 7 install on my drive.


Your MBR is fine! I have this problem too.

This seems to be some kind of nasty BIOS bug, you have to power
off the netbook and disconnect psu if connected. In worst case
take battery out for some seconds, than it will boot again.
This is super annoying and I hope this will get fixed somehow.

Really really hope all this gets better else I will never buy something
from ASUS again.

Something funny: The preinstalled expressgate seems to run inside
an intelframebuffer lol... Its beyond me that they can't team up with
amd and release this with proper hardware acceleration... Whatever
I removed expressgate anyway...

---

### Post by Wahlgren on 2011-07-12
I only got suspend to work by disable C9 in bios under CPU settings. I read this advice on some other forum and can confirm it works. Have not found out what C9 does yet, so I have it enable and wait for a fix with this bug. It all goes down to ATI to release a better driver for this hardware.

---

### Post by sikes on 2011-08-13
I was able to get suspend to function by dropping back to Ubuntu 10.10 amd64. After downloading the latest catalyst drivers ([http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)).

Using the following wiki ([http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)) I was able to get suspend mode to function.

I'll try it again with Natty ([http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide)) later and post results.

---

### Post by sikes on 2011-08-16
I could not get an install from the USB pendrive with 11.04 AMD64 to take. The alternative was to upgrade from 10.10 up.

From that point on, suspend mode functioned. Although, when I attempted to restart the system, the drive would not load until I removed the battery, power cord and restarted.

I installed the latest catalyst drivers (11.7) and restarted. Everything seemed to load alright. However, suspend mode does not function anymore. :-|

Back to the drawing board, I go.

---

### Post by Chris11 on 2011-08-17
I made a fresh install of 11.04 on my Eee PC. I had the suspending problems , but recently I realiz4ed that after a update the have magically gone away.. I dont know the reasons...

---

### Post by lakerssuperman on 2011-08-28
I tried running the alphas of 11.10 on my 1215b.  Suspend works and seems to be fairly reliable.  I have not installed the proprietary AMD drivers for video as they aren't currently compatible with 11.10 yet.

Using my 1215b with 11.04 was fairly rough at first but it seems support is picking up as the updates come and with 11.10 it seems there are good things ahead.

---

### Post by s3l3ct on 2011-09-19
Has there been any advances on this issue? I have 11.04 64 bits on my 1215b and suspend does not work, I have to remove battery and restart in order to get back into the computer. Whats more annoying is that even though I've shut of suspend in screen settings, it sometimes suspends itself anyway... 

Does anyone know if the problem disapears by switching to 10.10? If so, any pointers to how to downgrade would be much appreciated! ;)

---

### Post by lacinyC on 2011-09-23
I have the same issue, on an **Asus 1215B**, with proprietary **ATI** drivers installed. I am running **Linux Mint 11** 64bits Katya (latest).
Accidentally closed the lid, went to **hibernate** and it scared the heck out of me because the screen remained off.
Notice: I plugged an** external screen** on the **VGA** output and **no signal** came out of it either. After 2 or 3 "blind" reboots |a good **10 minutes** since the first hibernation], the screen came back on and everything went **fine**.
For now I set my power management preferences to "Suspend" instead of hibernate in case of lid closed, but I must say I am still a bit worried. Have yet to try this on my Win7 dual boot though.


> **mastergizmo said:**
> 
Something funny: The preinstalled expressgate seems to run inside
an intelframebuffer lol... Its beyond me that they can't team up with
amd and release this with proper hardware acceleration... Whatever
I removed expressgate anyway...
I've removed it as well! haha :D But I'm curious to know how to use this  second power up button now, there must be a way to link it to some  specific partition or boot sector or something. /offtopic

---

### Post by sprince09 on 2011-10-29
Can anyone verify if the suspend/resume problem still exists?

---

### Post by GreenRaccoon on 2011-10-30
I have an ASUS K53E and the problem was fixed once I installed Linux kernel 3.0.

---

### Post by richardhundt on 2011-11-19
I'm running 11.10 x86_64 with C6 disabled on a 1215b e350 and latest bios. Suspends fine when the lid is closed, and resumes too. However, on reboot the bios seems to be in a funny state and doesn't come up again unless I remove the battery.

I've tried the open source radeon driver, the distro packaged ATI drivers, as well as manually installing the latest Catalyst drivers from ATI's website. None of these makes any difference.

I've also gone up to kernel version 3.2, but some interface changes in the latest kernel breaks the bcwl wlan drivers so gave up on that initially, but I'm going to try it again.

It seems like a power management bug in the kernel which leaves the bios or CPU in a funny state after suspend, and not anything to do with the display drivers.

I'm no expert so this may be wrong, but from what I've read, the C6 thing in the bios seems to be effectively a zero voltage power state for the CPU, but even if it goes down to a low power C4 state (suspend?), it doesn't seem to be able to cycle back up to a full power state and come back up on reboot.

---

### Post by cafeschintze on 2011-11-23
I can confirm this bug and I think I have found two different types of its appearence.

I've had the ASUS 1215B now since two weeks. I'm running Ubuntu 11.10 on it.

Most of the times when I had put the laptop into a powersaving mode (hibernate or suspend), it would not wake up correctly.

The first type of the same behavior: looks like this: After pressing the suspend button, the screen turns black (off) but the cpu fan is still on.
Nothing but taking the battery out for a couple of seconds will help to make the laptop power up normally again.

After having read a couple if entries in forums I disabled C6 Mode in the Bios settings. Currently I don't use hibernate, I want standby for a quicker wake up. To be honest I can't really say if disabling C6 has really helped a lot.

Still I get about 5-10 sucessful wakeups and then one buggy one.

The second type of what I believe has to do with the same bug is the laptop not powering up correctly after reboot or poweroff. I will power up the laptop, see the bios logo and then instead of seeing the ubuntu boot logo, there will be only a blinking cursor in the top left corner of the screen.
In some another forum thread [[SOLVED] Asus 1215b - 11.04 installed but doesn't boot]("http://ubuntuforums.org/showthread.php?t=1809898") they suggest to reeinstall grub from a live usb stick. This is a solution, that I had used whenever this bug would appear to me (rarely). But as I found out yesterday taking out the battery for a couple of seconds helps, also.

It could be coincidence, but what is it with the Asus 1215B and taking out the battery? What is it forgetting?

Maybe somebody could verify this? And maybe we could try to find a way to provoke the appearence of the bug all the time. (I noticed something very strange happening everytime I set off /etc/init.de/networking stop).

---

### Post by fragment137 on 2011-12-11
I have an ASUS A53E... I had to use a fix that I discovered through rigorous Googling....

This fix worked for me: 

[ASUS Hibernate/Suspend fix]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug")

Something to try I suppose,

---

### Post by rgm3 on 2011-12-20
> **fragment137 said:**
> I have an ASUS A53E... I had to use a fix that I discovered through rigorous Googling....  This fix worked for me: 

[ASUS Hibernate/Suspend fix]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug")


The linked-to page suggests creating a script [FONT="Courier New"]/etc/pm/sleep.d/20_custom-ehci_hcd[/FONT] that unbinds the ehci and xhci USB drivers (via [FONT="Courier New"]/sys/bus/pci/drivers/{e,x}hci_hcd/[/FONT]) on shutdown, then adds them back on resume.

This did not work for me.

---

### Post by mihas on 2012-01-25
was battery life/suspend any better with 10.10?

---

### Post by water-man on 2012-02-22
If you google around with "suspend problems Ubuntu" you get pages with similar complaints for HP, Lenovo etc. etc.

I think the problem is so common that a well working laptop is the exception and a refuse-to-wakeup laptop is the rule.
Time somebody comes out of hibernation at Canonical and solves this problem before version 12.04 comes out. This is embarrasing.

NOTE: my wife uses an Asus EeePC 1215b on which I installed Ubuntu for her (she is a 3 year happy user of Ubuntu). She is so fed-up with this suspend problem that she is now gone back to W'7 and I cannot blame her!](*,)

---

### Post by Spae on 2012-02-24
Ummm... i am.. or was thinking about buying this laptop.
Should i not? This seems like an annoying problem. But do most laptops have this problem when running ubuntu? I have always used desktop so.. Should i go for the 1215b?

> NOTE: my wife uses an Asus EeePC 1215b on which I installed Ubuntu for her (she is a 3 year happy user of Ubuntu). She is so fed-up with this suspend problem that she is now gone back to W'7 and I cannot blame her!
oh no, i don't want to use w7....! >.<

---

### Post by aelg on 2012-06-15
Just wanted to say that today I upgraded to kernel 3.4.2 and pm-utils 1.4.1-5 on an Archlinux setup on an asus 1215b. This seemed to have solved the suspend problem. Since the upgrade I've done about 20 suspends and it has worked every time (earlier I had the exact same problem as i had with my previous Ubuntu installation, suspend causes the screen to go black with fans on and then hang).
A problem that remains is that if I suspend and wake and after that turn off the computer it will not start without removing the battery. That is what happend earlier when you restarted after a hangup when you tried to suspend.

---

### Post by mulligan7nbj on 2012-06-15
Does anyone know when this kernel will be made available to either a ppa or the general repositories for Ubuntu? I do not trust myself to compile the kernel directly and I have the exact problem described here. If I cant fix the issue I'm going to have to stick with Windows for the time being. :(

I'm using an ASUS a53z laptop.

---

### Post by rykel on 2012-09-05
> **aelg said:**
> Just wanted to say that today I upgraded to kernel 3.4.2 and pm-utils 1.4.1-5 on an Archlinux setup on an asus 1215b. This seemed to have solved the suspend problem.

The latest kernel in Ubuntu 12.04 is 3.2 and Suspend still does NOT work. I am using a ASUS 1215B with Radeon 6320.

---

