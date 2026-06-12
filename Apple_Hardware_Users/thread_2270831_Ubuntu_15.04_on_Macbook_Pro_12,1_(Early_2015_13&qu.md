---
title: "Ubuntu 15.04 on Macbook Pro 12,1 (Early 2015 13&quot; Retina) - trackpad issues"
date: 2015-03-25
forum: Apple Hardware Users
---

### Post by Sentynel on 2015-03-25
So I've got 15.04 installed and running successfully (future people Googling this: see footnote [1]). However, this version of the MBP has Apple's shiny new Force Touch trackpad, and surprising exactly nobody, it's not working particularly well. The basics work - I can move the mouse and left click - but nothing more than that. According to my Xorg.log (relevant section [here](http://pastebin.com/Dyrg73Mb)), it's just getting the class "pointer" and the generic evdev driver - neither the Synaptic driver or mtrack (I have both installed) are picking it up.

I'm not sure whether there's a simple configuration change I can make to get mtrack to Just Work or whether this is going to be more complicated. Any ideas?

Also, possibly related, my keyboard doesn't appear to be registering the fn key at all. xev doesn't pick anything up when it's pressed, nor does it affect other keypresses when held down. But in OSX, fn+down generates page down, and so forth. I'm not sure if that's fixable by changing the keyboard layout (it's set to UK Macintosh at the moment, which is mostly right for the other keys, except that the `/~ and §/± keys are switched).


[1] I had the same issues getting started as the Macbook Air in [this thread](http://ubuntuforums.org/showthread.php?t=2270613) - GTK apps weren't rendering their window contents in 14.10, but it works fine in 15.04. And the wireless drivers weren't working even with all updates installed, until I downloaded the [firmware](https://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/plain/brcm/brcmfmac43602-pcie.bin) from the Linux firmware git repo and dropped it in /lib/firmware/brcm.
Warning: do not install the bcmwl-kernel-source package (the official Broadcom drivers), on pain of them freezing the kernel up upon loading.

---

### Post by baozhanbingyai on 2015-03-28
I am very happy that I am not alone. I just install Ubuntu 15.04 on macbook pro Early 2015, And it works fine.

But I have four problems also: 
- 1. the wifi is not working, and when I install the bcmwl-kernel-source package(the official Broadcom drivers from update software in addition drivers), my macbook pro cannot shutdown properly. And the worst thing is that I can not shut down my Ubuntu properly even I uninstall it from the software center. Then I think I will reinstall it and try your method. Thanks a lot. 
- 2. the keyboard backlight is always lighting with full value. 
- 3. the screen backlight is always lighting with fuall value too.      After try some method with the google result. I can not make them the value I like :(. 

If you has just setting the keyboard or screen backlight properly. Would you like to share it with me ? 

     Thanks advance.

---

### Post by fechler2 on 2015-03-28
Hi guys,

Im happy about this topic, i bought also a macbook pro 13 early 2015 and want to install Ubuntu, too.
So I hope we will fix the trackpad and wlan issue, did anybody try 14.04 or the newest linux kernel?
I read some people have problems with overheating on linux, will that problem be fixed ?
I hope in the future everything will work fine, perfect hardware and a hight configurational OS ... a dream will come true :-)
Did anybody try a other linux distribution like fedora or suse ?

---

### Post by Sentynel on 2015-03-28
Backlights:
The keyboard brightness setting is the file /sys/class/leds/smc::kbd_backlight/brightness, on a scale of 0 to 255. Edit that file (with sudo) and write whatever brightness you want to it, and you should see the keyboard brightness change.
Likewise, the screen brightness is /sys/class/backlight/intel_backlight/brightness. I believe the reason adjusting this from the GUI doesn't work is that there's also an acpi_video0 backlight detected, which doesn't work properly.
I don't know if there's a GUI tool that will set these correctly, but you should be able to write a startup script or something which sets them to your desired values.

Other distros/verisons:
I haven't tried 14.04, but the kernel won't be new enough for the wireless to work. Trying a new kernel from mainline is one of the things I want to try re the trackpad, along with trying to just force the mtrack driver on it in xorg.conf, and failing that packet capturing the damn thing and comparing it to a working trackpad. However, Pillars of Eternity just got released so there are some competing demands on my spare time here...
The latest version of Fedora ran fine for me, but had the same wireless and trackpad issues as Ubuntu. I imagine making sure it has a 3.19 kernel and installing the firmware blob will fix the wireless.

Overheating:
I haven't had any problems, but I haven't done anything particularly stressful with it yet. You probably want to install lm-sensors and macfanctld and keep an eye on the output of `sensors` and/or /var/log/macfanctl.log.

---

### Post by este.el.paz on 2015-03-28
Gents:

Not to be a dark cloud, but, I've had a few threads posted here and over on the LM forum asking about trackpad problems for my '10 MBPro . . . with no ***easy*** to me solutions provided.  My problem was text being highlighted and erased while typing on the keyboard--and I didn't swipe the trackpad--and the "ultimate" solution for me was to check "disable trackpad while typing" . . . .  However, one poster on the LM forum did post some data about how to add "synaptics" data to the xorg.conf file . . . but, just didn't have the chops to try that method.  My point is that if linux didn't have a handle on the '10 tp it ***probably**** won't have the complexities of the latest and greatest at all covered.  But, you could try to find that thread on LM; it's something like "why does LM 13 erase data??" . . . .  It's a free OS, be happy with what it does do.

Also, in terms of the "try 14.04" suggestion . . . yes, I would support that idea.  I have LM17.1 running on my MBPro and the broadcom module installed through "additional drivers" without a problem.  15.04 is still "testing" I believe . . . and that might explain the issues . . . 14.04.2 might even work the tp better . . . .

e...

---

### Post by Sentynel on 2015-03-28
Ah, ye of little faith. I'm optimistic that a solution exists; given the basics are working it can't be doing anything *too* weird. Not necessarily an easy solution, but I'm not afraid of xorg.conf. (If I wasn't up for a challenge I wouldn't try putting Linux on difficult hardware in the first place.)

The problem with older versions is that older kernels don't support brand new hardware. The open source drivers for the particular model of Broadcom wireless chip in the 2015 MBP, for example, were only added to the kernel in 3.19, and there are likely to be other issues even if the official driver behaves (which I'm not optimistic about - I had the same problem with the official driver in 3.17 on Fedora).

---

### Post by este.el.paz on 2015-03-28
@sentynel:

Happy to be proven wrong . . . please post back when you get it "fixed" to your satisfaction . . . and then post the details of what you did so that others could learn your procedure . . . .

Not to put too fine a point on it, but in the comparison to how OSX runs its own machines, the relative sophistication of an ***expensive*** operating system to a free OS really designed to run on PCs . . . linux is a tad behind that curve . . . no harm no foul.  So, in terms of the kernel needing to be the latest, you may or may not be correct; I'd still venture that it would need some . . . possibly major tweaking to get it to do what OSX is offering.  And, then the question is, to what end???  

Rather than trying to get it to work in the same way as the more or less unobtaniumism of apple, why not just enjoy the things and applications that it does offer . . . and let the very basic functions of the tp suffice, while you are booted in linux.  When you want the maximum function and capacity use the OS that apple designed for it . . . why waste time?  Many of us in this sub-forum are here because the computers that apple no longer "supports" have viable function that linux offers . . . .  Enjoy the process.

e....

---

### Post by baozhanbingyai on 2015-03-29
@Sentynel
Thanks for your post, I can make my wifi working !!! I think it is a simple, elegant method to make wifi working. I just curious why the wifi does not work out-of-the-box considering that the driver link you proposed point to git.kernel.org web site.
Yes, the keyboard/screen brightness can be setting manually. I also want to make it automatically. So I follow the method proposed [http://askubuntu.com/questions/529924/disable-brightness-and-keyboard-back-light-at-start-up?rq=1](http://askubuntu.com/questions/529924/disable-brightness-and-keyboard-back-light-at-start-up?rq=1), I add the follow command in my /etc/rc.local file, but It does not work for me:

echo '470' > [COLOR=#000000]/sys/class/backlight/intel_backlight/brightness[/COLOR]
echo '0' > [COLOR=#000000][FONT=Verdana] /sys/class/leds/smc::kbd_backlight/brightness[/FONT][/COLOR]Would you like share the method that how you make it automatically ?

And I find that the 'delete' key in GUI interface does not work also. I think it is cause by a key mapping, but I can not fix it also.

My next path will to make the keyboard function do something I like. e.g. make the function key(the first row key) to behave combined with the 'fn' key (bottom left key). I know this will take my a lot of time. but anyway I will have a try.

Thanks for your great advice and method to make wifi work.

---

### Post by eviljackson1 on 2015-03-30
I'm thinking of buying a new MBP but I have a question about the force touch trackpad in Ubuntu/Other Distros. Does the tactile response work? I understand that there is no tactile response if you try to click while the machine is off, but there is a tactile response if you click in OSX. Does the tactile response "Just Work" in Ubuntu, or is there any known driver to make it work?

---

### Post by Sentynel on 2015-03-31
On setting the backlights - if you're sure that your script is actually getting executed and works properly, you might be finding that your rc.local script is getting triggered before the drivers have finished loading, or that something later in the startup process is resetting the brightness. I'd try getting it to happen later somehow.

The wifi firmware only got added to that kernel git repo a week or two ago - it'll take them a little while to make it into distro packages.


The click on the trackpad works just fine out of the box (to my slight surprise), I just don't have multitouch working on it yet.

---

### Post by tmpsantos on 2015-04-13
Thanks for the wifi fix.

I submitted a bug report about the 'fn' key issue:
[https://bugs.launchpad.net/bugs/1443370](https://bugs.launchpad.net/bugs/1443370)

---

### Post by tftfmacedo on 2015-04-16
I've managed to get the 'fn' issue solved by adding adding the new USB ids to my kernel. I'm not a Ubuntu user but the same strategy should work if you can patch+compile your kernel.

In case you're inclined to try this, adding the new ids to the trackpad driver doesn't work. 

[URL="https://gist.github.com/tmacedo/016a3d0fae9e3d87a1dd"]https://gist.github.com/tmacedo/016a3d0fae9e3d87a1dd
[/URL]

---

### Post by sicvolo on 2015-04-20
I got Kubuntu 15.04 running on 12,1 following this - [http://tech.ivkin.net/wiki/Linux_and_Unix_How_To#How_to_install_Ubuntu_15.10_on_an_early_2015_MacBook_Pro_.28Retina_12.2C1.29_with_full_disk_encryption](http://tech.ivkin.net/wiki/Linux_and_Unix_How_To#How_to_install_Ubuntu_15.10_on_an_early_2015_MacBook_Pro_.28Retina_12.2C1.29_with_full_disk_encryption)

It tells you how to fix WI-FI and Backlight issues the easy way.

The FN and the trackpad are still not working.

---

### Post by sicvolo on 2015-04-20
> **tftfmacedo said:**
> I've managed to get the 'fn' issue solved by adding adding the new USB ids to my kernel. I'm not a Ubuntu user but the same strategy should work if you can patch+compile your kernel.

In case you're inclined to try this, adding the new ids to the trackpad driver doesn't work. 

[URL="https://gist.github.com/tmacedo/016a3d0fae9e3d87a1dd"]https://gist.github.com/tmacedo/016a3d0fae9e3d87a1dd
[/URL]

The main chip in the new trackpad is different, so drivers/input/mouse/bcm5974.c does not work (confirmed myself). The new pad is a trio of Broadcom BCM5976 touchscreen controller for detecting the multitouch, Linear Technology LT3954 LED Converter with Internal PWM Generator for driving the haptic feedback (electromagnets) and sensing pressure at the four bend points, plus a ST Microelectronics 32F103 ARM Cortex-M based microcontroller to tie it all together. Creating a new driver from the scratch might be a b!7ch.

---

### Post by sicvolo on 2015-04-24
Ok, I've just created a proper distro for the keyboard driver that fixes the Fn issue, based on the patch referenced earlier. Works well on the official release of ubuntu 15.04. 

Get it here: [https://github.com/SicVolo/hid-apple-3.19]("https://github.com/SicVolo/hid-apple-3.19")

I'll try to push it upstream to the kernels 3.19 and 4.00 so you won't have to mock with compiling and tainting your system to get the basic functionality from MBP. The trackpad is the next.

---

### Post by arthur_dent3 on 2015-04-28
Hi all,

my Kernel is crashing under heavy WiFi load. Does anybody have the same issues?

---

### Post by knasher2 on 2015-04-28
> **sicvolo said:**
> The main chip in the new trackpad is different, so drivers/input/mouse/bcm5974.c does not work (confirmed myself). The new pad is a trio of Broadcom BCM5976 touchscreen controller for detecting the multitouch, Linear Technology LT3954 LED Converter with Internal PWM Generator for driving the haptic feedback (electromagnets) and sensing pressure at the four bend points, plus a ST Microelectronics 32F103 ARM Cortex-M based microcontroller to tie it all together. Creating a new driver from the scratch might be a b!7ch.

Luckily we can actually ignore all that.  By default the driver performs the basic level of haptic feedback, the pressing twice functionality probably doesn't make a lot of sense in Linux anyway.  So as it happens we can leave the default haptic feedback on, but still turn on the multitouch part.  Which is reasonable I think, and avoids the need for a whole new driver.  When the apple driver loads, it actually switches off the default feedback, and then tells the trackpad when to click, which unless force touch takes off in Linux, is more complicated that it needs to be.

---

### Post by knasher2 on 2015-04-30
Just to let people know, I have made quite a lot of progress in extending the trackpad driver to support this model.  At the moment pretty much everything works, though there is this weird dead area on the left and right side of the trackpad that if you start your finger off in there then no matter where it moves it isn't tracked.  Anyway I've posted a patch to the kernel bugzilla, though just a peliminary one, and when the code is tidied up and I've figured out what is causing that weird dead area, then I'll post the final version there as well.  

The bugzilla entry for tracking this issue is [https://bugzilla.kernel.org/show_bug.cgi?id=96771](https://bugzilla.kernel.org/show_bug.cgi?id=96771)

---

### Post by jhodapp2 on 2015-05-05
Any update on getting these changes tidied up? I'll be purchasing one of these this week and hope to get multitouch and generally close to full use of the trackpad. I'm also available to lend a hand with the efforts to fix the issues with this model. Just let me know if you have any specific ways that I can help you out right away.

---

### Post by george114 on 2015-05-10
I have an early 2015 MBP and have been extremely frustrated by this as well! I installed 15.04 Xubuntu, then applied your patches to 3.19.7 and compiled. On reboot the mouse didn't work at all. Is there a step I'm missing? Is there another driver I need to install as well? I tried bcm5974-dkms from mactel-support but it wouldn't even install (errors).

And thanks!

---

### Post by knasher2 on 2015-05-11
> **george114 said:**
> I have an early 2015 MBP and have been extremely frustrated by this as well! I installed 15.04 Xubuntu, then applied your patches to 3.19.7 and compiled. On reboot the mouse didn't work at all. Is there a step I'm missing? Is there another driver I need to install as well? I tried bcm5974-dkms from mactel-support but it wouldn't even install (errors).

And thanks!
Which patches did you apply?  There is a bug in the set that Henrik posted, which I mentioned in my last comment in the bugtracker, so until he fixes that you can use the patch I posted, called "second version of patch for trackpad".  If you are applying this, you shouldn't apply any of the other patches from the bugtracker.  The ones that Henrik posted are eventually going to be included in the kernel, but until that happens, the one I posted should work fine.

---

### Post by William_H._Jones_I on 2015-05-16
> **Sentynel said:**
> So I've got 15.04 installed and running successfully (future people Googling this: see footnote [1]). However, this version of the MBP has Apple's shiny new Force Touch trackpad, and surprising exactly nobody, it's not working particularly well. The basics work - I can move the mouse and left click - but nothing more than that. According to my Xorg.log (relevant section [here]("http://pastebin.com/Dyrg73Mb")), it's just getting the class "pointer" and the generic evdev driver - neither the Synaptic driver or mtrack (I have both installed) are picking it up.

I'm not sure whether there's a simple configuration change I can make to get mtrack to Just Work or whether this is going to be more complicated. Any ideas?

Also, possibly related, my keyboard doesn't appear to be registering the fn key at all. xev doesn't pick anything up when it's pressed, nor does it affect other keypresses when held down. But in OSX, fn+down generates page down, and so forth. I'm not sure if that's fixable by changing the keyboard layout (it's set to UK Macintosh at the moment, which is mostly right for the other keys, except that the `/~ and §/± keys are switched).


[1] I had the same issues getting started as the Macbook Air in [this thread]("http://ubuntuforums.org/showthread.php?t=2270613") - GTK apps weren't rendering their window contents in 14.10, but it works fine in 15.04. And the wireless drivers weren't working even with all updates installed, until I downloaded the [firmware]("https://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/plain/brcm/brcmfmac43602-pcie.bin") from the Linux firmware git repo and dropped it in /lib/firmware/brcm.
Warning: do not install the bcmwl-kernel-source package (the official Broadcom drivers), on pain of them freezing the kernel up upon loading.

Sentynel,

Thanks for your note on the wireless.  Were I to be able to get Ubuntu on my early 2011 MBP (non-retina), I probably wouldn've tried the bcmwl package.  Anyway, I was curious as to how you installed Ubuntu on your MBP.  I tried the rEFInd procedure, but was unable to get any video beyond the initial boot screen.  Apparently, both the thumb drive and DVD did not provide the correct video drivers.  I no longer use this particular laptop, as I have a newer retina MBP, so I was thinking along the lines of dual-booting or natively installing Ubuntu.  As it is, I can't install Ubuntu in a dual-boot scenario, and I want to do more research before I just install Ubuntu over the existing Mac partition.

---

### Post by sundragon2 on 2015-05-19
Just catching up. I managed to get the wifi working on my 2015 and I have been using a bluetooth mouse (HPx4000b) to get around the trackpad issues in the mean time. I had paired it with Yosemite and it automatically worked with Ubuntu (nice) but when I look at System Settings >Bluetooth its greyed out but it's definitely working how I have no idea how, haha.

This is what I found:

$ hcitool dev
Devices:
$ sudo service bluetooth status
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: inactive (dead)

I'll open another thread about this I figured I'd let you know :)

---

### Post by raywang2 on 2015-06-02
Hi [COLOR=#000000]sundragon2

could you please post the link of the thread you opened, i have the same issues that everybody has, and want to see if there is solutions to them\

Thanks a lot[/COLOR]

---

### Post by sundragon2 on 2015-06-14
> **raywang2 said:**
> Hi [COLOR=#000000]sundragon2

could you please post the link of the thread you opened, i have the same issues that everybody has, and want to see if there is solutions to them\

Thanks a lot[/COLOR]

Sure, here ya go:

[http://ubuntuforums.org/showthread.php?t=2282509&p=13303965#post13303965](http://ubuntuforums.org/showthread.php?t=2282509&p=13303965#post13303965)

Edit: Another post asking about Bluetooth: [http://ubuntuforums.org/showthread.php?t=2278361&highlight=Macbook+Pro+12%2C1+bluetooth](http://ubuntuforums.org/showthread.php?t=2278361&highlight=Macbook+Pro+12%2C1+bluetooth)

---

### Post by sundragon2 on 2015-07-21
From what I understood (I'm new to Ubuntu) some of the people who posted in this thread have found ways to make the trackpad and function keys work and pushed them to the new kernel. How do we install those changes? I have updated Ubuntu pretty much every week and no new functionality has trickled down.

---

### Post by sicvolo on 2015-07-21
You can get the working modules from [https://github.com/SicVolo/hid-apple-3.19]("https://github.com/SicVolo/hid-apple-3.19").
I've got 4.0.x kernel modules [here]("https://github.com/SicVolo/hid-apple-4.0.x") and 4.1.2 [here ]("https://github.com/SicVolo/hid-apple-4.1.2")

---

### Post by mj0g on 2015-07-22
@sicvolo what's the status of the fn keys and trackpad in your module - should they be working? I just tried it then (commit 593e69b) and had no luck.

---

### Post by vishal733 on 2015-07-22
@sicvolo: Same here. I tried it on Ubuntu 15.04 with kernel 3.19.0-22-generic. Multi-touch on the trackpad is still not working..

---

### Post by mj0g on 2015-07-23
FYI as of an hour ago @sicvolo's module for 15.04 makes the trackpad (and function keys) work perfectly: [https://github.com/SicVolo/hid-apple-3.19](https://github.com/SicVolo/hid-apple-3.19)

Thanks heaps!

---

### Post by webbgc on 2015-07-23
Hi,

Does anyone have the key combination for the right click working?

Everything else seems okay

---

### Post by TincoAndringa on 2015-07-29
Hi, just want to confirm the SicVolo DKM works perfectly for fixing trackpad and fn key.

We are experiencing kernel freeze also when WiFi traffic is high.

---

### Post by stephan_chrst on 2015-07-30
hi,
im new here, and i want to change my yosemite macbook pro 12,1 with ubuntu 15.04 cause java jdk not working properly on yosemite,
anyone have heat issue? or another issue?
Thanks.

---

### Post by Thatcher_Chamberli on 2015-08-05
Has there been any progress on the multitouch? I just tried SicVolo's program with no results. MacBook Pro Retina 12,1 Ubuntu 15.04 kernel 3.19.0-15. Should work right?

---

### Post by sicvolo on 2015-08-10
Many people reported that my modules worked fine. Even more people reported that the fixes that my modules are based on worked fine - [https://bugzilla.kernel.org/show_bug.cgi?id=96771](https://bugzilla.kernel.org/show_bug.cgi?id=96771)
It's likely something on your side. 

But to answer your question - yes there is progress, the fixes are already in the next RC for the 4.2 kernel. They should be in the latest stable when it goes out.

---

### Post by margot2 on 2015-08-13
SicVolo's path for kernel 4.1.2 was working, but it stopped working and I keep getting an error that says the synaptics backend is missing. It was working great until I rebooted....my kernel is now at 4.1.4. Maybe that's why? I'm running Arch Linux and Plasma 5 on an early 2015 12,1 13inc MBP.

---

### Post by JohnAtilano on 2015-08-17
I just installed sicvolo's fix and can confirm it works very well.  Fn works.  Two-finger right-click works. Two-finger scrolling works.

Some of the keymappings are off (the tilde key actually makes <> symbols. The screen brightness keys are registering but are not actually changing the brightness of the screen.

Some really great work!  Thanks sicvolo!

---

### Post by vishal733 on 2015-08-18
> **JohnAtilano said:**
> I just installed sicvolo's fix and can confirm it works very well.  Fn works.  Two-finger right-click works. Two-finger scrolling works.

Some of the keymappings are off (the tilde key actually makes <> symbols. The screen brightness keys are registering but are not actually changing the brightness of the screen.

Some really great work!  Thanks sicvolo!

Yes. Same problem with me. The tilda key is messed :)

Regarding the screen brightness key, it requires a separate fix. 
It has something to do with two display devices being shown in the directory > /sys/class/backlight/
Just google it, you should be able to find it. I do not remember the exact link I had used to fix it on my macbook 12,1. This link might be somewhat useful though:
> [http://itsfoss.com/fix-brightness-ubuntu-1310/](http://itsfoss.com/fix-brightness-ubuntu-1310/)

---

### Post by binaryanomaly on 2015-08-18
With 15.10 (wireless) and ppa:canonical-kernel-team/ppa (for trackpad and fn-keys)

This works without manual patches, just saying :)

---

### Post by Jethro_Borsje on 2015-08-31
I´m new to both Ubuntu and Mac so I'm sorry if I'm asking the obvious, but: is there a way to install these modules using apt-get at the moment or not yet?

---

### Post by vange on 2015-09-06
> **Jethro_Borsje said:**
> I´m new to both Ubuntu and Mac so I'm sorry if I'm asking the obvious, but: is there a way to install these modules using apt-get at the moment or not yet?

Running the latest kernel fixes fn keys and trackpad for me. You can download it here [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) and use instructions here [http://askubuntu.com/a/142000/12340](http://askubuntu.com/a/142000/12340)

If you are not happy with installing an unsupported kernel (which I can understand), you can wait for the next Ubuntu version, which hopefully ships with 4.2.

---

### Post by sundragon2 on 2015-09-16
> **vange said:**
> Running the latest kernel fixes fn keys and trackpad for me. You can download it here [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) and use instructions here [http://askubuntu.com/a/142000/12340](http://askubuntu.com/a/142000/12340)

If you are not happy with installing an unsupported kernel (which I can understand), you can wait for the next Ubuntu version, which hopefully ships with 4.2.

Thank you!

I updated the kernel a few months ago to: 4.1.3-040103-generic #201507220129 SMP Wed Jul 22 01:31:38 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux with no affect on the function keys, and trackpad. I'll look into updating the kernel to 4.2 or just waiting till October 22nd when Ubuntu Willy drops.

---

### Post by mj0g on 2015-09-17
> **sundragon2 said:**
> Thank you!

I updated the kernel a few months ago to: 4.1.3-040103-generic #201507220129 SMP Wed Jul 22 01:31:38 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux with no affect on the function keys, and trackpad. I'll look into updating the kernel to 4.2 or just waiting till October 22nd when Ubuntu Willy drops.

The fix is indeed in 4.2, which will be the default in Wily. I'm currently running a standard Ubuntu GNOME Wily beta, and it Just Works™.

---

### Post by sundragon2 on 2015-09-17
> **mj0g said:**
> The fix is indeed in 4.2, which will be the default in Wily. I'm currently running a standard Ubuntu GNOME Wily beta, and it Just Works™.

That's fantastic! Does the Bluetooth and WIFI work properly (currently, WIFI only works on 2.4 Ghz, and Bluetooth somehow works with my mouse but all attempts to access it show that it's not working.

I'm now attempting to update the kernel to 4.2 unstable from August 30th.

---

### Post by molt on 2015-09-20
I originally had a 3.19.0-28 kernel, on which the built-in trackpad would at least let me move the mouse and click, but neither the function keys nor any networking at all would work.
I got Wifi working by following [this answer on AskUbuntu]("http://askubuntu.com/a/624746"), but the trackpad, bluetooth and the function keys remained unchanged.
After applying sicvolo's patch, the function keys were working, bluetooth remained unchanged, but the trackpad wouldn't respond at all anymore.
I'm now on a 4.2.0-040200 kernel, which behaves the same way as 3.19.0-28 with sicvolo's patch.
There is also a red light in the headphone jack, but unlike [this guy](https://discussions.apple.com/thread/3694502), I have no problems with audio at all (both over speakers and headphones).

Could anyone tell me in which log files I'd have to look for errors, or how to debug the issue in general?

---

### Post by sicvolo on 2015-09-20
@molt I have a suspicion something is intervening with kernel from your userland setup. Are you on ubuntu? What version? Do you have mtrack or synaptic trackpad module? Did you change your palm detection or other trackpad settings? 
Do you have any non-stock mods that could get in the way? 

There are a couple posts in the original bug [https://bugzilla.kernel.org/show_bug.cgi?id=96771](https://bugzilla.kernel.org/show_bug.cgi?id=96771) that could help you troubleshoot your issues.

For reference, I've tested and it works fine on Kubuntu 15.04 with 4.2.0-040200 and 4.2.0-8 without my modules. Others got it working on Arch.

---

### Post by Jethro_Borsje on 2015-09-22
> **mj0g said:**
> The fix is indeed in 4.2, which will be the default in Wily. I'm currently running a standard Ubuntu GNOME Wily beta, and it Just Works™.
Will the backlight and shutdown problems also be fixed in this kernel?

---

### Post by molt on 2015-09-22
@sicvolo:
Thanks, got my trackpad working with [comment 67]("https://bugzilla.kernel.org/show_bug.cgi?id=96771#c67") from the link you gave me. :)
For reference, I'm on Ubuntu 15.04 with a 4.2.0-040200 kernel and no mods.

---

### Post by jamosky on 2015-09-25
Hi guys 


I have an issue with 14.04 and 15.04 in which I can boot and then there is no log in screen, I can type a password and enter to get to the desktop but a lot of the application GUI elements are missing etc. I assume this is a resolution issue, have any of you guys experienced this ?

---

### Post by Jethro_Borsje on 2015-09-28
Does this patch effects anything written here about the Apple USB keyboard: [https://help.ubuntu.com/community/AppleKeyboard#Ubuntu_13.10_.28maybe_also_earlier.29](https://help.ubuntu.com/community/AppleKeyboard#Ubuntu_13.10_.28maybe_also_earlier.29). I am thinking about buying this keyboard but am reluctant because I am not sure if it will work or not with the new kernel.

---

### Post by vange on 2015-09-28
I have not experienced this behaviour on 15.04,using kernel 4.2. My computer does not have dedicated graphics, if that helps.

---

### Post by kouber on 2015-10-01
After upgrading the Kernel to 4.2 the trackpad scrolling started to work (no two fingers click a.k.a. right-click, or zoom etc. yet though) although the direction is the so called "natural". The Fn key is also now working, which is great.

I am using Kubuntu 15.04 with Macbook Pro 12,1.

So the things that are left seem to be:

- fix the direction of the trackpad scrolling & enable two fingers clicking, zooming, etc.
- fix the magic mouse gestures - currently it has only left and right clicking, no scrolling, but still it is the only way I can have right-click functionality for the moment
- fix bluetooth (it always complains for "No adapters found")
[COLOR=#a9a9a9]- remove the red light coming from the audio jack (fixed)[/COLOR]
- fix the camera

And of course awaiting for a real HiDPI support for KDE (Plasma), now some applications such as Viber or Sublime Text look really ugly.

Anybody has an idea how to configure the trackpad? In the System Settings GUI it says that "Synaptics driver is not installed (or is not used)".

```
[FONT=monospace][COLOR=#000000]root@teton:/etc/X11/xorg.conf.d# synclient -l[/COLOR]
Couldn't find synaptics properties. No synaptics driver loaded?

[EMAIL="root@teton:/etc/X11/xorg.conf"]root@teton:/etc/X11/xorg.conf[/EMAIL].d# xinput list  
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Broadcom Corp. Bluetooth USB Host Controller      id=11   [slave  pointer  (2)]
&#9116;   &#8627; bcm5974                                   id=13   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=9    [slave  keyboard (3)]
    &#8627; Broadcom Corp. Bluetooth USB Host Controller      id=10   [slave  keyboard (3)]
    &#8627; Apple Inc. Apple Internal Keyboard / Trackpad     id=12   [slave  keyboard (3)]
[/FONT]
```

---

### Post by Jethro_Borsje on 2015-10-01
To remove the red light:
```
echo '1' | sudo tee '/sys/module/snd_hda_intel/parameters/power_save'
```

[COLOR=#252525][FONT=sans-serif]If that works make it permanent make it permanent by adding to **/etc/rc.local** or, and this is a more proper way, create **/etc/modprobe.d/audio_powersave.conf** and add the following to it:[/FONT][/COLOR]
```
options snd_hda_intel power_save=1
```

---

### Post by kouber on 2015-10-01
> [COLOR=#000000]To remove the red light:echo '1' | sudo tee '/sys/module/snd_hda_intel/parameters/power_save'[/COLOR]
[COLOR=#252525][FONT=sans-serif]If that works make it permanent make it permanent by adding to /etc/rc.local or, and this is a more proper way, create /etc/modprobe.d/audio_powersave.conf and add the following to it[/FONT][/COLOR]
[COLOR=#000000]options snd_hda_intel power_save=1[/COLOR]

Nice, it did the trick, thanks man!

---

### Post by kmm3 on 2015-11-10
Hi,

I want to change the backlight and deactivate the red light after booting the system.

I have added the following lines to the rc.local:

```
echo 1 > /sys/module/snd_hda_intel/parameters/power_save

echo 0 > /sys/class/leds/smc::kbd_backlight/brightness

cp /sys/class/leds/smc::kbd_backlight/brightness /home/User/br.tmp
```

the file br.tmp shows 0 as supposed but the backlight does not switch off. When booting the system the backlight is on, than it switches off for a moment and than back on again.

I guess there is another process overwriting my values. Can you help me fixing this? Thanks!

---

### Post by MikeBraxner on 2015-11-12
@kmm3 ... *"When booting the system the backlight is on, than it switches off for a moment and than back on again."*

You might want to check if you have **tlp** running. If so, then tlp's default settings are overriding your rc.local ones, and [comment (1) offers a roadmap to simple fix]("http://ubuntuforums.org/showthread.php?t=2299760&p=13377327#post13377327") ... just look for the right hooks.

---

### Post by kmm3 on 2015-11-12
I am using tlp. That one also overwrote the setting for the audio module. I cannot find any setting in the configuration file of the tlp for the keyboard though:

```
# ------------------------------------------------------------------------------
# tlp - Parameters for power save
# See full explanation: http://linrunner.de/en/tlp/docs/tlp-configuration.html

# Hint: some features are disabled by default, remove the leading # to enable
# them.

# Set to 0 to disable, 1 to enable TLP.
TLP_ENABLE=1

# Operation mode when no power supply can be detected: AC, BAT
# Concerns some desktop and embedded hardware only.
TLP_DEFAULT_MODE=AC

# Seconds laptop mode has to wait after the disk goes idle before doing a sync.
# Non-zero value enables, zero disables laptop mode.
DISK_IDLE_SECS_ON_AC=0
DISK_IDLE_SECS_ON_BAT=2

# Dirty page values (timeouts in secs).
MAX_LOST_WORK_SECS_ON_AC=15
MAX_LOST_WORK_SECS_ON_BAT=60

# Hint: CPU parameters below are disabled by default, remove the leading #
# to enable them, otherwise kernel default values are used.

# Select a CPU frequency scaling governor:
#   ondemand, powersave, performance, conservative
# Intel Core i processor with intel_pstate driver:
#   powersave, performance
# Important:
#   You *must* disable your distribution's governor settings or conflicts will
#   occur. ondemand is sufficient for *almost all* workloads, you should know
#   what you're doing!
#CPU_SCALING_GOVERNOR_ON_AC=ondemand
#CPU_SCALING_GOVERNOR_ON_BAT=ondemand

# Set the min/max frequency available for the scaling governor.
# Possible values strongly depend on your CPU. For available frequencies see
# tlp-stat output, Section "+++ Processor".
#CPU_SCALING_MIN_FREQ_ON_AC=0
#CPU_SCALING_MAX_FREQ_ON_AC=0
#CPU_SCALING_MIN_FREQ_ON_BAT=0
#CPU_SCALING_MAX_FREQ_ON_BAT=0

# Set Intel P-state performance: 0..100 (%)
# Limit the max/min P-state to control the power dissipation of the CPU.
# Values are stated as a percentage of the available performance.
# Requires an Intel Core i processor with intel_pstate driver.
#CPU_MIN_PERF_ON_AC=0
#CPU_MAX_PERF_ON_AC=100
#CPU_MIN_PERF_ON_BAT=0
#CPU_MAX_PERF_ON_BAT=30

# Set the CPU "turbo boost" feature: 0=disable, 1=allow
# Requires an Intel Core i processor.
# Important:
# - This may conflict with your distribution's governor settings
# - A value of 1 does *not* activate boosting, it just allows it
#CPU_BOOST_ON_AC=1
#CPU_BOOST_ON_BAT=0

# Minimize number of used CPU cores/hyper-threads under light load conditions
SCHED_POWERSAVE_ON_AC=0
SCHED_POWERSAVE_ON_BAT=1

# Kernel NMI Watchdog:
#   0=disable (default, saves power), 1=enable (for kernel debugging only)
NMI_WATCHDOG=0

# Change CPU voltages aka "undervolting" - Kernel with PHC patch required
# Frequency voltage pairs are written to:
#   /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
# CAUTION: only use this, if you thoroughly understand what you are doing!
#PHC_CONTROLS="F:V F:V F:V F:V"

# Set CPU performance versus energy savings policy:
#   performance, normal, powersave
# Requires kernel module msr and x86_energy_perf_policy from linux-tools
ENERGY_PERF_POLICY_ON_AC=performance
ENERGY_PERF_POLICY_ON_BAT=powersave

# Hard disk devices; separate multiple devices with spaces (default: sda).
# Devices can be specified by disk ID also (lookup with: tlp diskid).
DISK_DEVICES="sda sdb"

# Hard disk advanced power management level: 1..254, 255 (max saving, min, off)
# Levels 1..127 may spin down the disk; 255 allowable on most drives.
# Separate values for multiple devices with spaces.
DISK_APM_LEVEL_ON_AC="254 254"
DISK_APM_LEVEL_ON_BAT="128 128"

# Hard disk spin down timeout:
#   0:        spin down disabled
#   1..240:   timeouts from 5s to 20min (in units of 5s)
#   241..251: timeouts from 30min to 5.5 hours (in units of 30min)
# See 'man hdparm' for details.
#DISK_SPINDOWN_TIMEOUT_ON_AC="0 0"
#DISK_SPINDOWN_TIMEOUT_ON_BAT="0 0"

# Select IO scheduler for the disk devices: noop, deadline, cfq (Default: cfq);
# Separate values for multiple devices with spaces.
#DISK_IOSCHED="cfq cfq"

# SATA aggressive link power management (ALPM):
#   min_power, medium_power, max_performance
SATA_LINKPWR_ON_AC=max_performance
SATA_LINKPWR_ON_BAT=min_power

# PCI Express Active State Power Management (PCIe ASPM):
#   default, performance, powersave
PCIE_ASPM_ON_AC=performance
PCIE_ASPM_ON_BAT=powersave

# Radeon graphics clock speed (profile method): low, mid, high, auto, default;
# auto = mid on BAT, high on AC; default = use hardware defaults.
# (Kernel >= 2.6.35 only, open-source radeon driver explicitly)
RADEON_POWER_PROFILE_ON_AC=high
RADEON_POWER_PROFILE_ON_BAT=low

# Radeon dynamic power management method (DPM): battery, performance
# (Kernel >= 3.11 only, requires boot option radeon.dpm=1)
RADEON_DPM_STATE_ON_AC=performance
RADEON_DPM_STATE_ON_BAT=battery

# Radeon DPM performance level: auto, low, high; auto is recommended.
RADEON_DPM_PERF_LEVEL_ON_AC=auto
RADEON_DPM_PERF_LEVEL_ON_BAT=auto

# WiFi power saving mode: 1=disable, 5=enable; not supported by all adapters.
WIFI_PWR_ON_AC=1
WIFI_PWR_ON_BAT=5

# Disable wake on LAN: Y/N
WOL_DISABLE=Y

# Enable audio power saving for Intel HDA, AC97 devices (timeout in secs).
# A value of 0 disables, >=1 enables power save.
SOUND_POWER_SAVE_ON_AC=1
SOUND_POWER_SAVE_ON_BAT=1

# Disable controller too (HDA only): Y/N
SOUND_POWER_SAVE_CONTROLLER=Y

# Set to 1 to power off optical drive in UltraBay/MediaBay when running on
# battery. A value of 0 disables this feature (Default).
# Drive can be powered on again by releasing (and reinserting) the eject lever
# or by pressing the disc eject button on newer models.
# Note: an UltraBay/MediaBay hard disk is never powered off.
BAY_POWEROFF_ON_BAT=0
# Optical drive device to power off (default sr0).
BAY_DEVICE="sr0"

# Runtime Power Management for PCI(e) bus devices: on=disable, auto=enable
RUNTIME_PM_ON_AC=on
RUNTIME_PM_ON_BAT=auto

# Runtime PM for *all* PCI(e) bus devices, except blacklisted ones:
#   0=disable, 1=enable
RUNTIME_PM_ALL=1

# Exclude PCI(e) device adresses the following list from Runtime PM
# (separate with spaces). Use lspci to get the adresses (1st column).
#RUNTIME_PM_BLACKLIST="bb:dd.f 11:22.3 44:55.6"

# Exclude PCI(e) devices assigned to the listed drivers from Runtime PM
# (should prevent accidential power on of hybrid graphics' discrete part).
# Default is "radeon nouveau"; use "" to disable the feature completely.
# Separate multiple drivers with spaces.
RUNTIME_PM_DRIVER_BLACKLIST="radeon nouveau"

# Set to 0 to disable, 1 to enable USB autosuspend feature.
USB_AUTOSUSPEND=1

# Exclude listed devices from USB autosuspend (separate with spaces).
# Use lsusb to get the ids.
# Note: input devices (usbhid) are excluded automatically (see below)
#USB_BLACKLIST="1111:2222 3333:4444"

# WWAN devices are excluded from USB autosuspend:
# 0=do not exclude / 1=exclude
USB_BLACKLIST_WWAN=1

# Include listed devices into USB autosuspend even if already excluded
# by the driver or WWAN blacklists above (separate with spaces).
# Use lsusb to get the ids.
#USB_WHITELIST="1111:2222 3333:4444"

# Set to 1 to disable autosuspend before shutdown, 0 to do nothing
# (workaround for USB devices that cause shutdown problems).
#USB_AUTOSUSPEND_DISABLE_ON_SHUTDOWN=1

# Restore radio device state (Bluetooth, WiFi, WWAN) from previous shutdown
# on system startup: 0=disable, 1=enable.
# Hint: the parameters DEVICES_TO_DISABLE/ENABLE_ON_STARTUP/SHUTDOWN below
#   are ignored when this is enabled!
RESTORE_DEVICE_STATE_ON_STARTUP=0

# Radio devices to disable on startup: bluetooth, wifi, wwan.
# Separate multiple devices with spaces.
#DEVICES_TO_DISABLE_ON_STARTUP="bluetooth wifi wwan"

# Radio devices to enable on startup: bluetooth, wifi, wwan.
# Separate multiple devices with spaces.
#DEVICES_TO_ENABLE_ON_STARTUP="wifi"

# Radio devices to disable on shutdown: bluetooth, wifi, wwan
# (workaround for devices that are blocking shutdown).
#DEVICES_TO_DISABLE_ON_SHUTDOWN="bluetooth wifi wwan"

# Radio devices to enable on shutdown: bluetooth, wifi, wwan
# (to prevent other operating systems from missing radios).
#DEVICES_TO_ENABLE_ON_SHUTDOWN="wwan"

# Radio devices to enable on AC: bluetooth, wifi, wwan
#DEVICES_TO_ENABLE_ON_AC="bluetooth wifi wwan"

# Radio devices to disable on battery: bluetooth, wifi, wwan
#DEVICES_TO_DISABLE_ON_BAT="bluetooth wifi wwan"

# Radio devices to disable on battery when not in use (not connected):
# bluetooth, wifi, wwan
#DEVICES_TO_DISABLE_ON_BAT_NOT_IN_USE="bluetooth wifi wwan"

# Battery charge thresholds (ThinkPad only, tp-smapi or acpi-call kernel module
# required). Charging starts when the remaining capacity falls below the
# START_CHARGE_TRESH value and stops when exceeding the STOP_CHARGE_TRESH value.
# Main / Internal battery (values in %)
#START_CHARGE_THRESH_BAT0=75
#STOP_CHARGE_THRESH_BAT0=80
# Ultrabay / Slice / Replaceable battery (values in %)
#START_CHARGE_THRESH_BAT1=75
#STOP_CHARGE_THRESH_BAT1=80

# ------------------------------------------------------------------------------
# tlp-rdw - Parameters for the radio device wizard
# Possible devices: bluetooth, wifi, wwan

# Hints:
# - Parameters are disabled by default, remove the leading # to enable them.
# - Separate multiple radio devices with spaces.

# Radio devices to disable on connect.
#DEVICES_TO_DISABLE_ON_LAN_CONNECT="wifi wwan"
#DEVICES_TO_DISABLE_ON_WIFI_CONNECT="wwan"
#DEVICES_TO_DISABLE_ON_WWAN_CONNECT="wifi"

# Radio devices to enable on disconnect.
#DEVICES_TO_ENABLE_ON_LAN_DISCONNECT="wifi wwan"
#DEVICES_TO_ENABLE_ON_WIFI_DISCONNECT=""
#DEVICES_TO_ENABLE_ON_WWAN_DISCONNECT=""

# Radio devices to enable/disable when docked.
#DEVICES_TO_ENABLE_ON_DOCK=""
#DEVICES_TO_DISABLE_ON_DOCK=""

# Radio devices to enable/disable when undocked.
#DEVICES_TO_ENABLE_ON_UNDOCK="wifi"
#DEVICES_TO_DISABLE_ON_UNDOCK=""
```

---

### Post by MikeBraxner on 2015-11-13
@kmm3 ... Since systemd now runs everything but the coffemaker, try setting up an additional service, say, **/etc/systemd/system/kbdBacklight.service** along the lines of ...
```
[Unit]
Description=Switch off KBD Backlight
After=syslog.target

[Service]
Type=oneshot
ExecStart=/bin/sh -c 'echo 0 > /sys/class/leds/smc::kbd_backlight/brightness'

[Install]
WantedBy=syslog.target
```

and enable it with ...
**sudo systemctl enable [B]kbdBacklight.service**[/B].

NB: As far as I know, there are/used to be some udev/systemd rules enforced, that require(d) backlights to have a minimum value of 1 or 5% (whichever is higher) on reboots/resumes. If you simply want to re-set the brightness via a service you could use ...
```
[Unit]
Description=Reset KBD Backlight
After=suspend.target
After=hibernate.target
After=hybrid-sleep.target

[Service]
Type=oneshot
ExecStart=/bin/sh -c '/bin/cat /sys/class/leds/smc::kbd_backlight/brightness | sudo tee /sys/class/leds/smc::kbd_backlight/brightness'

[Install]
WantedBy=suspend.target
WantedBy=hibernate.target
WantedBy=hybrid-sleep.target
```

---

### Post by kmm3 on 2015-11-17
Hi,

Thanks for the help. I have tried that. But it is not working for me either. Is it possible to run your own script in tlp, to reset the power to 0?

km

---

### Post by MikeBraxner on 2015-11-18
@kmm3 ... I don't think tlp will be the way to go for that. Instead, have a look at /etc/pm/power.d

---

