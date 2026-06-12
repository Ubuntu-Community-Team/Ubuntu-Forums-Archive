---
title: "problem with asus N55SF"
date: 2011-10-14
forum: Asus Ubuntu Support (CLOSED)
---

### Post by 7m7m on 2011-10-14
hi 
i have been using Ubuntu  more than 2 years now

recently i just bought asus N55SF and want to use Ubuntu.
so i downloaded ubuntu 11.10desktop 64 bit then create start up usb disk.  when ubuntu boot and showed me the option how to install ubuntu i chooses  "try Ubuntu without installing "and"install ubuntu" but i keep getting this screen .(aa.jpg)
i tried to install it with cd  but ended up with same screen .
tried 11.04 32 bit also the same screen .
finally i install ubuntu with 11.10 desktop 64 bit Alternate.
the installation  finished with no problem.
but when i reboot to start ubuntu another error showed up .(bb.jpg)

note: windows 7 comes with notebook and i installed ubuntu in D patition .

thanks :)

---

### Post by Bjens on 2011-10-17
Hi,

Had problems with installing ubuntu on a N55s too, from a usb stick with 11.04. After creating a new boot usb with 11.10 it is able to move past being unable to read disk? cache and/or modprobe errors, but I'm unable to boot Ubuntu afterwards unless chosing recovery mode. I guess it's "asus" though? not much to be done. If I try a normal boot the screen just go black as if it isn't able to support it.

---

### Post by vadimcaen on 2011-10-18
Hi everyone !

I had the same problem but I have a solution !

When you boot on the liveCD/USB and when you see the menu where you have to choose between Live mode or install; try F6 and choose acpi=off ! This should solve your problem ;)

---

### Post by Rutrus on 2011-10-24
Recovery Mode works on your laptops due to "nomodeset" option.

You can edit your GRUB and add "nomodeset" option to your kernel. [[HOWTO]("http://ubuntuforums.org/showthread.php?t=1613132")]

But this is not the only problem I had. Maybe there are some incompatibilities too with touchpad+wifi.

---

### Post by tachylyte on 2011-11-14
I'm running the 64bit version of 11.10 on an n55sf. This is how I got it working...

1. After installation, reboot and press 'e' at the grub2 menu.
2. Edit the grub entry prompt for Ubuntu, appending "acpi=off" to the kernel commandline.
3. When I do this the Touchpad isn't detected so I needed to use a USB mouse here.
4. Update the system.
5. Add 'blacklist nouveau' to /etc/modprobe.d/blacklist.conf
6. Reboot (you'll no longer need to set acpi=off)

This should disable the Nvidia graphics card and load the integrated Intel graphics chip. You can then explore options such as Bumblebee or Ironhide if you need to get the Nvidia card working.  

Thanks to the Arch Wiki page for the n55sf for help with this (I've got Arch working fine on it too).

---

### Post by Ruffman on 2011-11-21
i made a mix of what tachylyte suggest:
I installed 32-bit Version and during install-boot i set acpi=off 

So after that I was able to install and run it after. Because I set acpi=off during install I don't need to edit grub, it starts. I updated and added 
'blacklist nouveau' to /etc/modprobe.d/blacklist.conf. 
Now I want to disable acpi=off. I found this entry in /etc/default/grub:
GRUB_CMDLINE_LINUX="acpi=off"
and commented it out. I reinstalled grub2. Now I cannot reboot in normal mode again. I have to add at least nomodeset to the bootoptions, if I don't want to get black bootscreen. What can I do, to make it work?

---

### Post by Nephilim91 on 2011-11-22
Same issue here.
I've tried tachylyte's solution but it didn't work, I still have to keep acpi disabled on boot otherwise the system won't load.
The only thing that worked for me was installing Ubuntu (64bit) with acpi=off from USB, then disabling acpi in the grub config file.
I've also blacklisted nouveau as you suggested, don't know if it's needed or not.
Neither setting nouveau.modeset=0 as this post suggested [http://ubuntuforums.org/showpost.php?p=11298428&postcount=242](http://ubuntuforums.org/showpost.php?p=11298428&postcount=242) worked, it became even worse... that setting caused many graphical glitches instead of the harmless yet disappointing blank screen and forced me to turn off my laptop manually.

I'm quite inexperienced in Ubuntu and I would like to fix this issue since I really need it. Does anybody know why is this happening? Is it the graphics card, Ubuntu or the laptop? Does this affect other distros or is it an Ubuntu-only problem? I'm writing to Asus to see if they can help with this, N5SF is a quite new laptop and this is very unpleasant, I'm not likely to use it like this, especially if I can't use the touch-pad, any graphic application or if my laptop is getting much warmer than it should do.

EDIT: Installing Ironhide made those glitches happen even with acpi=off, now I can only boot with nomodeset, I hope that uninstalling it will be enough. 
I've also noticed that with nomodeset I'm not forced to set acpi=off so my touchpad works as long as the keys for volume, brightness...

---

### Post by @gu79 on 2011-11-23
[SIZE=3][B]Ubuntu 12.04
[/B][/SIZE]Just [install bumblebee]("https://wiki.ubuntu.com/Bumblebee") and everything should be fine.
The only issue I'm aware of is the subwoofer not working. This should fix it partially (more info [here]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/871808/comments/34")):
 ```
echo 'options snd-hda-intel model=asus-mode4' | sudo tee -a /etc/modprobe.d/alsa-base.conf
```
Install the 'GNOME Alsa Mixer' and regulate the volume of the subwoofer with the 'Bass Spe' lever.[SIZE=3][B]

Ubuntu 11.10[/B][/SIZE]
[SIZE=3]**Quick guide:**[/SIZE]

[LIST]
[*]Boot the Ubuntu LIVE-CD with acpi=off option (F6)
[*]Partially fix the subwoofer problem: ```
echo 'options snd-hda-intel model=asus-mode4' | sudo tee -a /etc/modprobe.d/alsa-base.conf
```
[*]Blacklist nouveau driver: ```
echo 'blacklist nouveau' | sudo tee -a /etc/modprobe.d/blacklist.conf
```
[*]Add video drivers repository and update the system: ```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates && sudo apt-get update && sudo apt-get upgrade
```
[*]Install bumblebee: ```
 sudo add-apt-repository ppa:bumblebee/stable && sudo apt-get [COLOR=Black]update && sudo apt-get install bumblebee && sudo usermod -a -G bumblebee [/COLOR][COLOR=Black]$USER[/COLOR]
```
[*]Restart and done! (Nvidida drivers will appear as not activated, it's OK)
[/LIST]
Have a look bellow for a workaround to the Fn + F9 issue (on/off touchpad), power saving and suspend problems.

[SIZE=3]**Full story:**[/SIZE]
Hi, everyone. I have the AsusN55SF working perfectly fine with Ubuntu 11.04 and (now) with 11.10. For 11.10 is a little trickier so I'll try to give a detailed explanation. I just formatted and tried this in a new partition to make sure it still works (22/01/2012). The problem is with the video drivers. This laptop has the Intel integrated graphics and a dedicated NVIDIA GT555M. In order to make the latter to work in linux, we will need [Bumblebee]("https://launchpad.net/%7Ebumblebee"). 

Follow this steps:
1 - Install Ubuntu 11.10 as explained above (Press “Esc” when the Asus logo appears to enter boot menu, choose the pendrive or CD/DVD accordingly, then “F6”, choose lenguage, “F6” again and choose nomodeset or acpi=off.  With nomodeset the touchpad works, but the resolution of the screen is quite ugly. With acpi=off you need a mouse, but the video looks good.

2- For the first boot and as explained above, boot with no modeset or acpi=off (on the grub menu, press "e" on the ubuntu line and manually add nomodeset or acpi=off to the linux line, then “Ctrl + x” to boot). 

 3- As explained above, blacklist nouveau (from terminal, Ctrl + Alt + t):[INDENT]```
sudo gedit /etc/modprobe.d/blacklist.conf
```(remember to paste in a terminal to press Shift + fn + insert/delete)
[/INDENT]And manually add the line "blacklist nouveau".

 4- To have the latest video drivers, add the next repository:[INDENT]```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

``````
sudo apt-get update
sudo apt-get upgrade
``` [/INDENT]It will install all updates, so be patient...
 For some reason, there are NO drivers in “Additional Drivers”, yet.

 5- Install  [bumblebee]("https://github.com/Bumblebee-Project/Bumblebee") and add yourself to the bumblebee group :[INDENT]```
sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install bumblebee
sudo usermod -a -G bumblebee $USER
```[/INDENT]After a restart, everything will work fine. Any application that has to be run with the dedicated graphics card must be run with 'optirun application'. For example, 'optirun firefox'.Try '**glxspheres**' and '**optirun glxspheres**' to test the difference between using the integrated card alone or also the GeForce GT 555M. At full screen I'm getting almost the double (~35 frames/sec vs 70). Tip: create custom launchers with the optirun command so you wont have to do it manually again ([guide]("http://askubuntu.com/questions/13758/how-can-i-edit-create-new-launcher-items-in-unity-by-hand")).

From version 3 of bumblebee, the power managment is working out of the box, so the graphic card is turned off when optirun is not running (saving battery, less heat, etc.). To verify this, use this:
```
lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep nVidia
```When ON, the output ends with: 
nVidia Corporation Device [10de:1247] (rev a1) (prog-if 00 [VGA controller])
When OFF, it finishes with:
nVidia Corporation Device [10de:1247] (rev [COLOR=Red]ff[/COLOR]) (prog-if [COLOR=Red]ff[/COLOR])

[SIZE=3][B]Fn + F9 workaround:
[/B][/SIZE]There is a bug and Fn + F9 combination doesn't work (Toggle touchpad). As a workaround (based on this [thread]("http://ubuntuforums.org/showthread.php?t=1460790")), go to **System settings / Keyboard / Shortcuts**. On the left panel select **Custom shortcuts** and add a new one with the command: **/etc/acpi/asus-touchpad.sh**
Then set a key combination for that command (e.g. Shift + F9, tried Fn + F9 but it doesn't work). That's all, works perfect.

[SIZE=3][B]Power saving (RC6):
[/B][/SIZE]Enabling the RC6 power management will save 40 - 60% of power ([RC6]("https://wiki.ubuntu.com/Kernel/PowerManagementRC6")).
To add "i915.i915_enable_rc6=1" to the default kernel options, open this file:
```
gksu gedit /etc/default/grub
```and add that option to the line "GRUB_CMDLINE_LINUX_DEFAULT". In my case:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.i915_enable_rc6=1"

[SIZE=3][B]Suspend/Hibernate:
[/B][/SIZE]Follow steps 1, 2 (the new) and 3 from [this tutoria]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug")l (thanks to [laoneo]("http://ubuntuforums.org/member.php?u=1516192") for bringing it). 

[SIZE=3]**Subwoofer:**[/SIZE]
This should fix it partially as the rear right channel only will be in the subwoofer. Add **options snd-hda-intel model=asus-mode4** to the file (as root) /etc/modprobe.d/alsa-base.conf and reboot.

Hope it helps, I was also really frustrated not being able to make it work properly with Ubuntu...

---

### Post by @gu79 on 2011-11-23
I have also used [this]("https://github.com/Bumblebee-Project/Bumblebee/wiki/ACPI-Removed") in order to turn it off (extends battery life) and I haven't had any issues. Nevertheless, I don't know how to test if it is really off, besides leaving it on battery so see how long it lasts (which I didn't try...). Used the calls for the N55S from [here]("http://hybrid-graphics-linux.tuxfamily.org/index.php?title=ACPI_calls").

---

### Post by Nephilim91 on 2011-11-23
Thank you so much @gu79, it worked well for me :)
Everything works fine now (except the touchpad disable fn, no big deal, I guess that's an unrelated problem).
It took me two days long but I'm quite happy now :P

---

### Post by info@energidirekt.se on 2011-12-10
](*,)I had such problem with my n55sf that I sent it back to shop. 

Problem with n55sf was to install any Linux distro. I tried Ubuntu, Mint 12 or Open Susue, with no luck.
 - Optimus graphic card did not work at all, tried to load different drivers
 - Wired network did not work , 
 - Panic stop with kernel on bootinstall.

This was to much for me:frown:

My Packard Bell, 3 years old can install any distro fluently.:P

Be carefull with n55sf if you are not really good to understand how to config the system.
I am sure that is possible to find solution if you have a lot of time ...

---

### Post by kahotik on 2011-12-10
I'm having the same problem, and I'm following @gu79's "tutorial", but here's the problem:
> **@gu79 said:**
> HRestart again with acpi=off.

 4- Note for testing: try in terminal “glxspheres” and then “optirun glxspheres” (the second won't work).
 In the dash home, open “Additional Drivers” and install the “NVIDIA accelerated graphics driver (version current)”. Restart normally, this time you don't need to modify anything in grub.

5- Note for testing: now “glxspheres” doesn't work but “optirun glxspheres” works. To make both work, keep reading...  
 This is the odd part: Remove the NVIDIA driver that we just installed from “Additional Drivers”.
I can't do this part, because there is no "additional drivers" folder, nor "NVIDIA accelerated graphics driver" to be installed...

What (and where) went wrong?

---

### Post by @gu79 on 2011-12-12
**kahotik**: Did you find the "Additional Drivers" program? (not a folder). See the screenshots attached. [This]("http://ubuntuforums.org/attachment.php?attachmentid=208959&stc=1&d=1323687060") it how it will look at the end (after installing, re-installing, etc.)

**info@energidirekt.se**: It's a pity you didn't wait enough, It is a really good machine (great sound and screen). Now that Ubuntu is working (only with bumblebee), I'm really happy with it. Actually, I bought it there, in Malmö  :wink: so I have the Swedish keyboard as a souvenir.
You scared me a little as I didn't try the wired connection before, but now I've checked and it's working!


Remaining issues: 

[LIST]
[*]Fn + F9 (to turn off touchpad) not working.
[*][Subwoofer]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/871808") not working
[/LIST]

---

### Post by TheForce61 on 2011-12-18
Hey, I have been trying to get my Asus N55S running Ubuntu and SUSE for almost two weeks now and have installed Bumblebee, etc. However, I can still only run in safe mode and the graphics tear and stay torn so bad I can't do anything at all. It will absolutely not boot and run the X server in normal mode at all.

I have done everything I can find, but one thing I have discovered, is that if you set acpi=off, it disables fans inside your machine and can damage it. That is why the machines get so much hotter, not good, not even sure why anyone is suggesting this setp, other than very temporary and with warnings...

I discovered that if you blacklist nouveau, install intel driver and do not install nvidia drivers and do not turn acpi off and fo not set nomode set in boot, you can at least get a running x server. I finally got that, and am not going to risk breaking it by installing nvidia drivers, though I will play with bumblebee to turn power off to nvidia card, since it still runs and consumes power and generates heat. Then, I will wait for the Linux developers to properly support Optimus. Running another X SW stack on top of another X is nothing more than a hack at best, imo, anyway.
Oh, you may need to turn acpi off long enough to accomplish the above, then turn it back on.

---

### Post by ariamir on 2011-12-20
It was a struggle to put ubuntu working decently with full resolution and everything but by searching I managed to get it working fine.:popcorn:

I do not have acpi=off only pcie_aspm=force in grub for bumblebee.

If you are going to use just the intel driver I had problems and had to use i915.semaphore=1 in grub to get full resolution,
then something fixed it, not sure if something I changed while installing bumblebee or an update. So I took that out of grub.

If you are having issues now that may or may not solve it, you should still try and install bumblebee it works very well, I followed this tutorial: [http://www.ivegotavirus.com/blog/2011/11/06/how-to-get-optimus-working-on-ubuntu-11-10-oneiric/](http://www.ivegotavirus.com/blog/2011/11/06/how-to-get-optimus-working-on-ubuntu-11-10-oneiric/)
(I didnt use the intel device tweaks, and used this calls: )
```
cardoff:
\_SB.PCI0.PEG0.GFX0._DSM {0xF8,0xD8,0x86,0xA4,0xDA,0x0B,0x1B,0x47,0xA7,0x2B,0x60,0x42,0xA6,0xB5,0xBE,0xE0} 0x100 0x1A {0x1,0x0,0x0,0x3}

\_SB.PCI0.PEG0.GFX0._PS3 
cardon:
\_SB.PCI0.PEG0.GFX0._PS0 
```I also managed to get the subwoofer working but only half the time I boot:confused:
I used what was in a bug report:

```
# /etc/rc.local

echo 0x16 0x99130112 > /sys/class/sound/card0/hwC0D0/user_pin_configs
echo 1 > /sys/class/sound/card0/hwC0D0/reconfig

# end
```Did someone get suspend and hibernate working? and also turn off touchpad?

---

### Post by laoneo on 2011-12-26
Hi
The graphics stuff is working fine with ironhide. Did somebody get hibernation work and the special fn keys? When I suspend the system I can't bring it back. I really hope somebody has a solution for this.

How is your battery life? How long is your laptop running in battery mode?

Thanks for any answers!!

Followed this simple tutorial and since then hibernation is working perfect
[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

---

### Post by aalopes on 2012-01-11
Following [@gu79]("http://ubuntuforums.org/member.php?u=1495046") instructions I was able to install and get both cards to work on Ubuntu 11.10 (Asus N55S). Step 6, however, wasn't necessary, as I was able to run **glxspheres** and **optirun glxspheres** after step 5.
With the intel card I get around 59.5 fps while with the GeForce GT 555 I get around 80 fps (windowed - using full HD resolution).

By using the ACPI calls in Bumblebee that [@gu79]("http://ubuntuforums.org/member.php?u=1495046") mentioned, the system runs cooler (around 3/4 °C in my tests, when idle) which means that less power is being used and so it should save battery. If not, it will at least spare your fan, as fan is now quieter while working!

---

### Post by aa_bb_cc_dd on 2012-01-14
Hi everyone ,

First , thanks to @gu79 for his tutorial .

Well , after installing Bumblebee on ubuntu 11.10 , everything worked fine .
But , gnome3 isn't working anymore as it was before installing  Bumblebee .

Even though , I tried to install gnome3 , so at the login screen , there's Gnome option but after logging in, there is the same old interface of Ubuntu (attached to this reply a screen capture to my ubuntu desktop ) . :confused:

Are there any solutions to activate Gnome 3 ??
Thanks for your help in advance .

---

### Post by @gu79 on 2012-01-24
Hi, everyone, thanks for the feedback. I've updated the "guide" as the  last steps are no longer needed ([aalopes]("http://ubuntuforums.org/showpost.php?p=11602830&postcount=17")  pointed that out). I've  formatted two days ago and reinstalled with  only three commands and  booting only once with acpi=off. Really fast. 
Also, with the latest version of bumblebee the power management is   working out of the box, so, the Nvidia card will be turned off   automatically when is not in use.

> **TheForce61 said:**
>  I have discovered, is that if you set   acpi=off, it disables fans inside your machine and can damage it. That   is why the machines get so much hotter, not good, not even sure why   anyone is suggesting this setp, other than very temporary and with   warnings...
At least in my machine, that's not the case. In acpi=off mode, the fans   keep working normally and I had no problem (I used the machine with   acpi=off for a couple of hours).

[aa_bb_cc_dd]("http://ubuntuforums.org/member.php?u=1526145"): I'm happy with Unity, so I haven't tried gnome 3. Nevertheless, [this thread]("http://ubuntuforums.org/showthread.php?t=1859626") shows problems with an Ati driver, so maybe there is a similar problem.

[]("http://ubuntuforums.org/member.php?u=1516192")

---

### Post by ephestione on 2012-01-27
The three quick steps were the killer ;)
WHat's not clear, even if I think the answer is obviously yes... after installing bumblebee and rebooting, do you still need to "activate" tne proprietary nvidia driver from "additional drivers" or not?
What I noticed, is that the laptop absorbs usually 40W in ubuntu, idle, while I get 20W under win7, so I suppose there's something off with the power management, am I wrong?

EDIT: Either with or without bumblebee, with or without proprietary drivers enabled, I still get 40W consumption in idle, against 20W under windows...

EDIT2: Even with almost all tunables as "good" in powertop, and pcie_aspm=force in grub, I always get 40W consumption. Reading about how kernel 3.0 is so bad with power consumption, I start thinking that just maybe it's not really the n55sf which isn't managed well, but it's ubuntu itself which is wasting power on this pc. Still, I got 24W on my previous 17" toshiba, so 40W in here, considering the nvidia card should be off right now, are quite strange.

EDIT3: for me, setting acpi=off kills all fn buttons, and does other funny things that in overall make the laptop pretty unuseable

---

### Post by @gu79 on 2012-02-11
> **ephestione said:**
> The three quick steps were the killer ;)
WHat's not clear, even if I think the answer is obviously yes... after installing bumblebee and rebooting, do you still need to "activate" tne proprietary nvidia driver from "additional drivers" or not?
Sorry for that, but the obvious wasn't right. You shouldn't install anything. The Nvidia drivers are shown as not activated and that is OK (I've got that from the bumblebee forum). I hope they fix the power comsumption problem. Did you try with the alpha version of 12.04?

I've just edited the guide to state that and also to add a simple workaround to the Fn + F9 problem.

---

### Post by Nephilim91 on 2012-02-23
Hi guys, it's been a while since I last checked this topic, unfortunately I still have big troubles, I just wanted to know if anybody knows how to fix this.
The problem is that I just can't boot properly. Almost every time I turn on my laptop, passed grub, I see a "nice" white and gray flashing screen with random moving stripes. The same thing occurs when it goes into standby mode (not always). The odd thing is that it seems to happen randomly since sometimes it just boots correctly. Once I see that beautiful screen the only thing to do is manually turn off the notebook (which isn't very nice at all, I have to run check-disk often), and neither keyboard nor the HD usage led seems to work, although I can't understand whether the OS keeps on loading or not.
After the second, third or fourth attempt I can usually login... I'm just getting bored with this.
I don't think it is an hardware problem, I have a dual boot with Windows 7 which perfectly runs heavy graphical applications, moreover Ubuntu works fine once it starts, so does bumblebee.
I tried to purge and reinstall bumblebee but it didn't work. I also tried to look into /var/log/boot.log and /var/log/syslog files but I'm not that skilled and all I could understand is that syslog stops roughly at IPv6 Ethernet driver loading though I suppose this just means that I press the power off button at the same time (as soon as I see the white screen).
I have found no answer to my question yet. Any advice? Thank you.

---

### Post by @gu79 on 2012-02-27
Hi, Nephilim91. That sounds really horrible. In my case everything is working fine, even the bluetooth started to work with the latest ubuntu updates. I never had boot problems. The only issue I still have is that when I leave the machine idle for too long, somehow the power saving fails and when I try to wake it up, I see a black screen with a white stripe. 

Is that your case? (In screen options, I've disabled "Dim screen to save  power" and changed "Turn of after" to "Never" to try to solve it). I'm  attaching a picture of what I see. But still, when that happens, I still  have control and I can force a reboot (totally blind), using **Ctrl + alt +t**, and then **sudo reboot** + password.

My advice, save time and try a fresh installation in another partition (I made a backup of the RECOVERY partition using [clonezilla]("http://clonezilla.org/"), and I'm using that for testing 12.04).

---

### Post by ravimannan2002 on 2012-03-03
Hi folks,
Unfortunately, I cant get past step 2
> 2- For the first boot and as explained above, boot with no modeset or acpi=off (on the grub menu, press "e" on the ubuntu line and manually add nomodeset or acpi=off to the linux line, then &#8220;Ctrl + x&#8221; to boot). 

I add the acpi=off line and ctrl-x to boot, but the screen is still blank.
Nothing happens.
What should I do?
When I installed, I did install with updates, should I reinstall?

EDIT:
I got Ubuntu to boot. I had to select the option to go into the terminal. You have to load all file systems first, that way you'll get read-write access. Then as root you can edit the blacklist.conf file. 
Hope this helps someone.

---

### Post by @gu79 on 2012-03-05
> **ravimannan2002 said:**
> I add the acpi=off line and ctrl-x to boot, but the screen is still blank
Strange. Did you try as well nomodeset?

Good news is that with Ubuntu 12.04, most of the issues are solved. It boots without problem, Fn+F9 works and the video hardware is recognised correctly (I haven't tried bumblebee yet). There is also a [fix ready]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/871808") for the subwoofer. I hope they add it soon.


I've updated the guide to enable RC6 power management.

---

### Post by Nephilim91 on 2012-03-12
> **@gu79 said:**
> Hi, Nephilim91. That sounds really horrible. In my case everything is working fine, even the bluetooth started to work with the latest ubuntu updates. I never had boot problems. The only issue I still have is that when I leave the machine idle for too long, somehow the power saving fails and when I try to wake it up, I see a black screen with a white stripe. 

Is that your case? (In screen options, I've disabled "Dim screen to save  power" and changed "Turn of after" to "Never" to try to solve it). I'm  attaching a picture of what I see. But still, when that happens, I still  have control and I can force a reboot (totally blind), using **Ctrl + alt +t**, and then **sudo reboot** + password.

My advice, save time and try a fresh installation in another partition (I made a backup of the RECOVERY partition using [clonezilla]("http://clonezilla.org/"), and I'm using that for testing 12.04).
Well, I haven't had any problem for many boots, I even thought it finally disappeared, but now it is back ._.
Actually what I see isn't similar to your screen, it is more like random lines and figures slowly moving... Usually there is a blank screen with colored horizontal and vertical lines crossing in the same area, and I can often see like a honeycomb pattern, especially on the bottom right corner... That's not always the same, it changes over time and it moves, that's not a static screen, it's weird, isn't it? :P I can't really understand how the video card can create such strange and "geometrical" patterns when it tries to boot.

By the way, I think I'll try to do a fresh install, that's the only thing to do. I guess I'll just format the root partition then install 12.04 beta over, hope it is quite stable by now, given that it is a LTS.
Thank you so much for all your help, I really appreciated it!
Before formatting I'll try to take a photo of my screen, just to let you see what happens :P

---

### Post by q5651331 on 2012-03-20
> **vadimcaen said:**
> Hi everyone !

I had the same problem but I have a solution !

When you boot on the liveCD/USB and when you see the menu where you have to choose between Live mode or install; try F6 and choose acpi=off ! This should solve your problem ;)

Had the same Problem solved with the model Asus n45/n45sf! Great solution! Thanks!

---

### Post by ephestione on 2012-03-29
Radom behaviour in my case is X restarting by itself.
Sometimes when it does and I log back in, I get the ugly unskinned X interface, with plan gray window frames and ugly menus.
I need either to reboot or to restart X with ctrl-alt-bksp (after enabling it).
This happens after you do something "conspicuous", like starting an app, last it happened just now after starting irfanview with wine and trying opening a file.

Another gripe is that no matter how you set the screen brightness, it always goes back to full brightness after each boot (or restore from sleep), and you need to decrease it manually with fn+f5

---

### Post by ajaustin on 2012-03-30
I installed using the guide in this thread about 2 weeks ago.  It all went very well - thanks!

Yesterday I updated to kernel 3.0.0.17 and I get black and white bars when I try to boot.  I have re-booted successfully to 3.0.0.16.

Any ideas what to do?

Tony

---

### Post by @gu79 on 2012-03-31
> **ajaustin said:**
> Yesterday I updated to kernel 3.0.0.17 and I get black and white bars when I try to boot.  I have re-booted successfully to 3.0.0.16.


Hi, I had the same problem like one week ago and for two consecutive boots (failed). The second time I could reboot totally blind (logging in first, and then rebooting from terminal). I don't know if it was caused by an update, but I haven't had the same issue again. Now I'm running the kernel 3.0.0-17.30-generic 3.0.22.

---

### Post by ajaustin on 2012-04-01
> **@gu79 said:**
> Hi, I had the same problem like one week ago and for two consecutive boots (failed). The second time I could reboot totally blind (logging in first, and then rebooting from terminal). I don't know if it was caused by an update, but I haven't had the same issue again. Now I'm running the kernel 3.0.0-17.30-generic 3.0.22.

On trying again I have had a couple of successful boots with kernel 3.0.0.17 and no failures so far.  Very strange.

---

### Post by hiproTn on 2012-04-19
Hello everyone
Thanks for this great post
I have recently bought an Asus n55sf-s1437v. 
I would like to install ubuntu on it (with windows naturally to play some video games) but i'm afraid of the many operations to do to have it installed because i'm a new user of linux (less than a year)
I have read that installing it with the option "acpi=off" could damage the computer. is it true ?:confused:
I have read also that, after installing it, some users couldn't boot on neither ubuntu nor windows because they had changed "something" in their hard drive partitions (sorry i don't have more details and i forgot where did i read that).
Finally, i would like to ask if cloning my actual hard drive with Clonezilla for example could help to have back my computer if i screw something. 
Thank you for your help.
(sorry if i made mistakes in my post but english is not my native language)

---

### Post by @gu79 on 2012-04-19
> **hiproTn said:**
> 
I have read that installing it with the option "acpi=off" could damage the computer. is it true ?:confused:
It could in some systems, but I haven't had that problem working for  several hours with this machine in acpi=off mode (fans worked, which is  the thing that could fail). The notebook will run hotter anyway, because  RC6 power managment is disabled and the dedicated video will be working  all the time (until bumblebee is installed and working). Don't panic if  the fans don't start immediately (do if the notebook is too hot)... Anyway, you have also the nomodeset option  (instead of acpi=off) so is not really an issue.

Another option, wait 5 days for the Ubuntu 12.04 and you won't have to do the acpi=off nor nomodeset...

> **hiproTn said:**
> I have read also that, after installing it, some  users couldn't boot on neither ubuntu nor windows because they had  changed "something" in their hard drive partitions Don't worry,  that "something" shouldn't happen unless you install ubuntu deleting the  windows or RECOVERY partition (ubuntu will boot anyway). To be sure, always choose the option  "Something else" during the install ([this screen]("http://www.ubuntu.com/sites/www.ubuntu.com/files/active/installation-type.jpg")) and make sure you have correctly selected the partition that you intend to use (ask if you need more help about that).

I have made several tests, including deleting the two critical  partitions (RECOVERY and OS). If you delete the OS partition (windows)  of course windows won't work, but you can restore it as it was from  factory using the RECOVERY partition (I think F8 while booting). Be  aware that when you restore the windows from factory, it will take 84 Gb  after the RECOVERY partition for windows. So, if you had a smaller  partition after recovery, it will destroy the next one in order to  gather enough space (I lost the ubuntu patition that way).
If you eliminate the RECOVERY partition, the problem will be that you  won't be able to use the Asus Music Now (I have a backup of that  partition so I can restore it anytime).

So, you won't have problems as long as you don't destroy the RECOVERY  partition (hidden from windows), which is the only thing you need to  restore it as it came from factory. Don't waste space making a backup of  the full drive, just use clonezilla to save the first partition (you  will use only 13 Gb of disk space and you are safe).

In your case, as you want to keep your current windows installation, I  would make a backup of the recovery partition with clonezilla (and of  course of your files). You could skip that if you made the DVD backups  (not available with all models, according to the manual).
Then, inside windows, defragment the drive and resize your windows  partition to a minimum. This way, you avoid to "touch" the windows  partition from ubuntu (which is your concern, not mine). You don't need to create a new partition in the  freed space. Then, install Ubuntu in the freed space. To avoid "wasting"  a primary partition in the swap, I install without swap and then use a  file for that (you need some extra steps in order to hibernate).

Feel free to ask, is better to be sure of what you are doing...

---

### Post by hiproTn on 2012-04-19
Thanks for your answer [@gu79]("http://ubuntuforums.org/member.php?u=1495046")
Unfortunately, i can't wait 5 days i must have it installed this weekend.
What is the difference between the nomodeset and acapi=off and which one is safer ?
Also, where can i choose one of them ? :oops: 
I already made the DVD backups so no need for clonezilla
In windows, i have 2 partitions (c: and d: ) i also diminished c: so i can have some space where to install ubuntu (around 60 Go). 
About the swap partition, can i take some memory from this free partition and use it as a swap ?

---

### Post by @gu79 on 2012-04-19
Please, follow [this steps]("http://ubuntuforums.org/showpost.php?p=11482967&postcount=8") (let me know if something is not clear, so I can correct it), there you will find how to select acpi=off or nomodeset while booting with the live CD/USB of ubuntu (I use acpi=off, because it looks better, but I guess nomodeset is safer).

[Here]("http://ubuntuforums.org/showthread.php?t=1613132"), you can read a little about acpi and nomodeset.

You can't have more than 4 primary partitions, and you already used 3 (RECOVERY, OS "c:" and "d:"). You could create an extended in the freed space, but I think that the "d:" is an extended (and you can have only one). So, install ubuntu without swap. Later you can [create swap as a file]("https://help.ubuntu.com/community/SwapFaq") instead of a partition or shrink the "d:" (if it is an extended partition) to create a new swap partition at the end.

---

### Post by hiproTn on 2012-04-19
Thanks for the answer 
It's clear now
I will not create a swap partition as i don't use the hibernate feature and even if i will use it in the future i will create a file for the swap
I will install ubuntu saturday, hope it will works
Thank you again for your help

---

### Post by @gu79 on 2012-04-19
Keep in mind that the swap is not only for suspend/hibernate, it is also  used when you run out of memory like the virtual memory in windows. If  you use memory consuming programs, you will need it (I have 8 Gb and I  never saw the swap used).

---

### Post by hiproTn on 2012-04-19
i know but i also have 6 Gb of ram so i think i will never use it
In addition using memory as ram, isn't so useful because the access to that is slower than the access to the RAM

---

### Post by samuele.mattiuzzo on 2012-04-20
Hi! I did all the procedures like told in this post: [http://ubuntuforums.org/showpost.php?p=11482967&postcount=8](http://ubuntuforums.org/showpost.php?p=11482967&postcount=8) but after the reboot, the computer hangs on "Checking battery state". I then entered the recovery mode and removed all nvidia drivers i installed and bumblebee too, but nothing is changed, now ubuntu hangs at boot. Checking on a terminal, it stops at "Starting Lightdm [OK]", so i tried reinstalling lightdm too, but it hangs at the same time.

With recovery mode, the system boots without problems (except i'm in 800x600 and can't change res) so what should i do to re-enable only the intel integrated and forget from now on of the nvidia card? I wanted to configure the HDMI out, but as far as i understood, it's still not useable, so i'll stick with the vga output from the intel

Thanks all!

---

### Post by ajaustin on 2012-04-21
A thought for anyone installing dual-boot Windows and Ubuntu:

My Ubuntu can read/write the Windows partition as standard and I installed Ext2Fsd [http://www.ext2fsd.com/?page_id=25]("http://www.ext2fsd.com/?page_id=25") which lets me read/write to my Ext3 /home Linux partition.  I have a swap partition, / partition and /home partitions all in an extended partition, so I don't need to worry about where any particular data file is and if I do a Windows recovery my Linux installation should be untouched.

Tony

---

### Post by hiproTn on 2012-04-28
Hello everyone !
So, i installed ubuntu last Sunday. Everything seems to work perfectly except bumblee.
i can run the command "optirun firefox" for example but my graphic cards fans turn very fast and my laptop is noisy !
Also it's heating a little bit.
Could you please help me !
Thank you

---

### Post by bigfas on 2012-04-28
done everything in ubuntu 12.04. glxspheres gets me ONLY 1 frame per second while if runed with optirun semms to work fine. Also I get the felling battery lasts way less then on win 7.

---

### Post by @gu79 on 2012-05-01
> **hiproTn said:**
> Hello everyone !
So, i installed ubuntu last Sunday. Everything seems to work perfectly except bumblee.
i can run the command "optirun firefox" for example but my graphic cards fans turn very fast and my laptop is noisy !
Also it's heating a little bit.
Thank you
It sounds perfect to me. The  machine should stays quite and cool when you are not using the Geforce card  (thanks to bumblebee that turns it off), but only until you put it to work using "optirun application". Why do you think is not working?

> **bigfas said:**
> done  everything in ubuntu 12.04. glxspheres gets me ONLY 1 frame per second  while if runed with optirun semms to work fine. Also I get the felling  battery lasts way less then on win 7.
I've got the same results. I don't know why the performance went down so  bad. The driver is the same. About the battery, I'm not using windows at  all, but ephestione reported 20 W in win7 (#[**20**]("http://ubuntuforums.org/showpost.php?p=11644398&postcount=20")), so the battery should last the same as I'm getting similar values. These are my results (in Watts):
                       ```

                NvidiaOff   NvidiaOn   glxsph.   ScreenOff
Ubuntu_11.10     16.24        22.12     52.82     -
Ubuntu_12.04     17.17        23.87     51.96    11.77
```In all cases the machine was idle, but in "glxsph." in which case I had glxspheres running. For more details, see the attached file (funny that I had to add the ".txt" extension to be able to upload it in an linux forum...).

---

### Post by @gu79 on 2012-05-01
Updated the guide with a fix for the subwoofer (to read more, [check this]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/871808"), specially comment [#34]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/871808/comments/34")).

---

### Post by ephestione on 2012-05-07
came to check in here before hitting the 12.04 upgrade... seems everything's fine, maybe better, with precise.
I'll be upgrading for the rest of the morning ;)

---

### Post by qwerty12 on 2012-05-09
> **@gu79 said:**
> 
[SIZE=3][B]Fn + F9 workaround:
[/B][/SIZE]There is a bug and Fn + F9 combination doesn't work (Toggle touchpad). As a workaround (based on this [thread]("http://ubuntuforums.org/showthread.php?t=1460790")), go to **System settings / Keyboard / Shortcuts**. On the left panel select **Custom shortcuts** and add a new one with the command: **/etc/acpi/asus-touchpad.sh**
Then set a key combination for that command (e.g. Shift + F9, tried Fn + F9 but it doesn't work). That's all, works perfect.


Hi,

I'm not running Ubuntu and I have the N55SL (but I believe it's pretty much the same as the N55SF) so sorry if this is noise, but:
 
Fn + F9 on my laptop sends a XF86TouchpadToggle KeyPress event (I checked with xev) which sounds pretty standard to me, and, indeed, after installing the ktouchpadenabler module in KDE, Fn + F9 works to disable my touchpad. (This is with kernel 3.3.5 and Xorg 1.12.1) If you're not using KDE, this thread sounds promising: [http://forums.opensuse.org/english/get-technical-help-here/laptop/473292-thinkpad-fn-f8-toggle-touchpad-working-os-12-1-a.html](http://forums.opensuse.org/english/get-technical-help-here/laptop/473292-thinkpad-fn-f8-toggle-touchpad-working-os-12-1-a.html)

Since I may as well ask: Do any of you sometimes experience the fan starting up (very lightly; I once had it do so just by running nano!) and then stopping after one second? This occurs consecutively for me and I do find it slighly odd. cpufreq is enabled (I'm using Granola) and i7z says that the CPU is running at 800MHz (same as in Windows according to Core Temp when I'm not doing anything heavy). The NVIDIA card is disabled; I checked, thanks to gu79's awesome guide.

---

### Post by ajaustin on 2012-07-20
> 
Originally Posted by ajaustin View Post
Yesterday I updated to kernel 3.0.0.17 and I get black and white bars when I try to boot. I have re-booted successfully to 3.0.0.16.> **@gu79 said:**
> Hi, I had the same problem like one week ago and for two consecutive boots (failed). The second time I could reboot totally blind (logging in first, and then rebooting from terminal). I don't know if it was caused by an update, but I haven't had the same issue again. Now I'm running the kernel 3.0.0-17.30-generic 3.0.22.

I was also having this problem when the computer suspended.  I have stopped the behaviour by disabling "Monitor power management control" in my XFCE power management options.  Not ideal but better than having to force a reboot.

---

### Post by p0l0us on 2013-01-31
I found this solution for HDMI output:

[http://www.webupd8.org/2012/08/get-hdmi-working-with-nvidia-optimus-on.html](http://www.webupd8.org/2012/08/get-hdmi-working-with-nvidia-optimus-on.html)

It works on my N55SF. Good for watching movies and office work, but not usable for playing games. Keyboard responce is slow.

---

