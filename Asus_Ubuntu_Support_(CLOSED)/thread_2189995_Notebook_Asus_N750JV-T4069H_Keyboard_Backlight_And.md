---
title: "Notebook Asus N750JV-T4069H: Keyboard Backlight And All Fn Keys"
date: 2013-11-25
forum: Asus Ubuntu Support (CLOSED)
---

### Post by aljosa2 on 2013-11-25
Hi all,
happy with 7 months Linux experience on old HP desktop, few days ago I deleted Windows from my brand new notebook Asus N750JV-T4069H (Intel® Core™ i7-4700HQ; Bit 64; Nvidia GeForce GT750M) and installed Xubuntu 13.10. I'm not sure but it seems to me that my problem is Xubuntu bug. If this is the case, I would be very grateful if someone can communicate the problem to the development team 'cause I get lost inside the more than complicated bug reporting procedure: 


- Keyboard backlight and all the function keys (fn) are not working
(i can turn on keyboard backlight with 
sudo chmod 777 /sys/class/leds/asus::kbd_backlight/brightness
echo 3 > /sys/class/leds/asus::kbd_backlight/brightness
but effect is lost after turning the computer off and on again).

---

### Post by Toz on 2013-11-25
There is some interesting information at [this link]("https://wiki.debian.org/InstallingDebianOn/Asus/N750JV/Jessie") that you might find helpful. The author has found that the kernel parameter **acpi=** seems to solve issue with brightness keys.

---

### Post by aljosa2 on 2013-11-25
ORIGINAL /etc/default/grub


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


Thanks for reply :)
I've tried 4 different scenarios, but nothing changes: 


GRUB_CMDLINE_LINUX="acpi= nolapic. 'acpi='"
GRUB_CMDLINE_LINUX="'acpi='"
GRUB_CMDLINE_LINUX=acpi= nolapic. 'acpi='
GRUB_CMDLINE_LINUX='acpi='

---

### Post by Toz on 2013-11-25
Try:
```
GRUB_CMDLINE_LINUX="acpi="
```
...and after you've saved the file, make sure to run:
```
sudo update-grub
```

On reboot, check with:
```
cat /proc/cmdline
```

---

### Post by aljosa2 on 2013-11-26
I have reinstalled Xubuntu once again. Don't know if it is of any importance, but in my computer ther'e no a single trace of Windows 8 (uefi/boot).
 
Nothing changes with different acpi= kernel parameter.
Please explain (step by step) what do you mean with: 


*On reboot, check with:*
*Code:*
*cat /proc/cmdline*

---

### Post by aljosa2 on 2013-11-28
Hi, 
thank you once again for your assistance.
"acpi=" and "acpi_osi=\"!Windows 2012\"" are useless, but with "acpi_osi=" we're almost there :)


**GRUB_CMDLINE_LINUX="acpi_osi="**


> pastebinit /var/log/dmesg


[http://paste.ubuntu.com/6488928/](http://paste.ubuntu.com/6488928/)


> cat /proc/cmdline


BOOT_IMAGE=/boot/vmlinuz-3.11.0-13-generic.efi.signed root=UUID=737be188-c475-4521-a764-c484a80d404c ro acpi_osi= quiet splash vt.handoff=7


**NOT OK:**
Power Adapter shows not connected
No keyboard backlightng
FN (F3) Decreases keyboard backlighting
FN (F4) Increases keyboard backlighting
FN (F9) Enables or disables the touchpad


**OK:**
Battery shows 100%
FN (F1) Puts the Notebook PC into Sleep mode
FN (F2) Turns Airplane mode on or off
FN (F5) Decreases display brightness
FN (F6) Increases display brightness
FN (F7) Turns the display panel off
FN (F8) Activates the second screen
FN (F10) Turns the speaker on or off
FN (F11) Turns the speaker volume down
FN (F12) Turns the speaker volume up

---

### Post by Toz on 2013-11-28
> [    0.304692] ACPI Error: Method parse/execution failed [\_SB_.BTKL._STA] (Node ffff8804188ce7a8), AE_NOT_FOUND (20130517/psparse-536)
...looks like "acpi_osi=" is causing issues with the power handling on your system.

Can you the try "acpi_osi=\"!Windows 2012\"" kernel parameter again and this time post back the dmesg log file? Also post back what works and what doesn't. Lets compare. The relevant lines in /etc/default/grub should look like:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet rw"
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\""
```

---

### Post by aljosa2 on 2013-11-28
***GRUB_CMDLINE_LINUX_DEFAULT="quiet rw"***
***GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\""***

> pastebinit /var/log/dmesg

[http://paste.ubuntu.com/6489491/](http://paste.ubuntu.com/6489491/)


> cat /proc/cmdline

BOOT_IMAGE=/boot/vmlinuz-3.11.0-13-generic.efi.signed root=UUID=737be188-c475-4521-a764-c484a80d404c ro "acpi_osi=!Windows 2012" quiet rw


**NOT OK:**
Power Adapter shows not connected
No keyboard backlightng
FN (F3) Decreases keyboard backlighting
FN (F4) Increases keyboard backlighting
FN (F9) Enables or disables the touchpad
FN (F5) Decreases display brightness
FN (F6) Increases display brightness
FN (F10) Turns the speaker on or off / FN (F11) Turns the speaker volume down / FN (F12) Turns the speaker volume up (sometimes yes, sometimes no, sometimes strange opening of browser or text editor menu)
FN (F1) Puts the Notebook PC into Sleep mode (notebook returns from sleep mode with broken screen and strange vertical colour lines

**OK:**
Battery shows 100%
FN (F7) Turns the display panel off
FN (F8) Activates the second screen
FN (F2) Turns Airplane mode on or off

During startup now appears a new strange process, and later I have system internal error (cannot copy/paste, please see attached images)-

***GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"***
***GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\""***

> pastebinit /var/log/dmesg

[http://paste.ubuntu.com/6489580/](http://paste.ubuntu.com/6489580/)



> cat /proc/cmdline

BOOT_IMAGE=/boot/vmlinuz-3.11.0-13-generic.efi.signed root=UUID=737be188-c475-4521-a764-c484a80d404c ro "acpi_osi=!Windows 2012" quiet splash vt.handoff=7


**NOT OK:**
Power Adapter shows not connected
No keyboard backlightng
FN (F3) Decreases keyboard backlighting
FN (F4) Increases keyboard backlighting
FN (F9) Enables or disables the touchpad
FN (F5) Decreases display brightness
FN (F6) Increases display brightness

**OK:**
Battery shows 100%
FN (F1) Puts the Notebook PC into Sleep mode
FN (F2) Turns Airplane mode on or off
FN (F7) Turns the display panel off
FN (F8) Activates the second screen
FN (F10) Turns the speaker on or off
FN (F11) Turns the speaker volume down
FN (F12) Turns the speaker volume up

---

### Post by Toz on 2013-11-28
Okay, so it looks like **acpi_osi=** is your best bet. Can you see if there is a bios update available for your computer that might solve the power issue for you?

---

### Post by aljosa2 on 2013-11-28
In future, if any update available, which system should I choose: 

Windows 8.1 64bit
Windows 8 64bit
Others

BIOS 207
2013.08.29  update
[http://support.asus.com/download.aspx?SLanguage=en&p=3&s=540&m=N750JV&os=&hashedid=w7tr8rGDPtaGjY1O](http://support.asus.com/download.aspx?SLanguage=en&p=3&s=540&m=N750JV&os=&hashedid=w7tr8rGDPtaGjY1O)

My bios: 

> sudo dmidecode -s bios-version

N750JV.207


What do you propose, not only for power issue but also for keyboard backlighting problem? Should I contact directly official Asus support? Before doing so, is there a way we can easily check if some other problem exist on relation notebook-operating system?

---

### Post by aljosa2 on 2013-12-09
Not sure if something's wrong or something's missing, but definitely it's Xfce related (same technical troubles with LXDE).
If I remove Xfce from Xubuntu and install GNOME Shell or Cinnamon, everything ok except F5 and F6 buttons. If instead of Xfce I install KDE-Plasma into Xubuntu, there's an option in keyboard settings to assign to F5 and F6 functions of display brightness adjustment - in that way my machine becomes 100% ok. 

I'm not accepting Windows any more because of spying and similar things, but in almost 20 years never had a problem with using it. 
Problem is that I cannot (and don't want) adapt myself to mentioned Linux desktop environments. What's the point of using computer if it makes my life harder instead of easier? 

Thanks in advance for any idea how to repair Xfce malfunction...

PS: I have also tried to install Ubuntu 13.10 - for me it was impossible in UEFI mode (with Xubuntu no problem).

**Ubuntu 13.10**
*With Cinnamon, Unity completely removed*
Everything ok except F5-F6 buttons and impossibility to install Nvidia drivers.

> pastebinit /var/log/dmesg

[http://paste.ubuntu.com/6514260/](http://paste.ubuntu.com/6514260/)

**Xubuntu 13.10**
*Clean installation with all updates*

> pastebinit /var/log/dmesg

[http://paste.ubuntu.com/6521991/](http://paste.ubuntu.com/6521991/)

**NOT OK:**
[I]- Sound indicator icon malfunction
  (solved with Exec=/usr/lib/indicator-sound-gtk2/indicator-sound-service)
- Power Adapter shows not connected
- No keyboard backlightng
- FN (F3) Decreases keyboard backlighting
- FN (F4) Increases keyboard backlighting
  (I can turn on keyboard backlight with 
  sudo chmod 777 /sys/class/leds/asus::kbd_backlight/brightness
  echo 3 > /sys/class/leds/asus::kbd_backlight/brightness
  but effect is lost after turning the computer off and on again).
- FN (F9) Enables or disables the touchpad
- FN (F5) Decreases display brightness
- FN (F6) Increases display brightness
- FN (F2) Turns Airplane mode on or off
- FN (F1) Notebook returns from sleep mode with broken screen and strange vertical colour lines[/I]

**OK:**
[I]- Battery shows 100%
- FN (F7) Turns the display panel off
- FN (F8) Activates the second screen
- FN (F10) Turns the speaker on or off
- FN (F11) Turns the speaker volume down
- FN (F12) Turns the speaker volume up


[/I][img]http://cromalternativemoney.org/mediafiles/my_linux.png[/img]

---

### Post by Toz on 2013-12-09
An interesting observation: Cinammon install is using "vmlinuz-3.11.0-14-generic" kernel while Xubuntu install is using "vmlinuz-3.11.0-14-generic.efi.signed". Not sure how two different kernels were installed using basically the same base system. Although, I don't think this is the root of the problem.



I don't have any experience with Cinammon. What power manager does it use? I wonder whether the majority of your not-working Xfce components can be tied back to the power manager - in this case xfce4-power-manager (which btw, lxde uses as well):
- Power Adapter shows not connected (definitely)
- No keyboard backlightng (possibly)
- FN (F3) Decreases keyboard backlighting (possibly)
- FN (F4) Increases keyboard backlighting (possibly)
- FN (F9) Enables or disables the touchpad (probably not - but might be related to some sort of pointer settings daemon (if Cinammon uses one))
- FN (F2) Turns Airplane mode on or off (not sure what this is)
- FN (F1) Notebook returns from sleep mode with broken screen and strange vertical colour lines (possibly)

The others:
- FN (F5) Decreases display brightness
- FN (F6) Increases display brightness
...I believe are kernel and/or video driver related.



> (I can turn on keyboard backlight with
sudo chmod 777 /sys/class/leds/asus::kbd_backlight/brightness
echo 3 > /sys/class/leds/asus::kbd_backlight/brightness
but effect is lost after turning the computer off and on again).
Try adding:
```
chmod 777 /sys/class/leds/asus::kbd_backlight/brightness
echo 3 > /sys/class/leds/asus::kbd_backlight/brightness
```
...to **/etc/rc.local** above the *exit 0* command so that it gets run on each boot.



Are there any differences in the loaded modules for each install?
```
lsmod
```

---

### Post by aljosa2 on 2013-12-10
Very thanks for the trick. 
Modification inside /etc/rc.local applied successfully. 
I have also installed "Xfce4 power-manager-plugins" and now I'm able to adjust screen brightness through slider icon in system tray/notification area.

I have some important questions: 

1)
Yeah you right, Google "xfce4-power-manager fn keys" produces interesting results.
As I'm considering this tricks only as a temporary solution because ultimate goal is to eliminate all start-up errors, and as they are developing new Xfce 4.12, what would be the best way to communicate this bugs to Xfce Team? I've tried to get in contact with them, but unfortunately without success: 
[http://forum.xfce.org/viewtopic.php?id=8480](http://forum.xfce.org/viewtopic.php?id=8480)

2)
Should I try to install other power manager? 

3)
Is it possible in XFCE to assign via keyboard settings all this missing functions to Fn buttons like I did in KDE?

---

### Post by Toz on 2013-12-10
> **aljosa2 said:**
> Very thanks for the trick. 
Modification inside /etc/rc.local applied successfully. 
I have also installed "Xfce4 power-manager-plugins" and now I'm able to adjust screen brightness through slider icon in system tray/notification area.

I have some important questions: 

> 1)
Yeah you right, Google "xfce4-power-manager fn keys" produces interesting results.
As I'm considering this tricks only as a temporary solution because ultimate goal is to eliminate all start-up errors, and as they are developing new Xfce 4.12, what would be the best way to communicate this bugs to Xfce Team? I've tried to get in contact with them, but unfortunately without success: 
[http://forum.xfce.org/viewtopic.php?id=8480](http://forum.xfce.org/viewtopic.php?id=8480)
Probably best to create a bug report at [https://bugzilla.xfce.org/buglist.cgi?component=General&product=Xfce4-power-manager&resolution=---]("https://bugzilla.xfce.org/buglist.cgi?component=General&product=Xfce4-power-manager&resolution=---"). There might already be a related bug report that you could add to.

> 2)
Should I try to install other power manager? 
I don't know. I've never tried mixing another power manager with Xfce. What power manager does Cinammon use?
```
ps -ef | grep -i power
```

> 3)
Is it possible in XFCE to assign via keyboard settings all this missing functions to Fn buttons like I did in KDE?
I'm not sure how its done in KDE, but in Xfce you can assign shortcut keys via Settings Manager -> Keyboard -> Application shortcuts.

---

### Post by john_earley on 2013-12-10
Hi Aljosa2, I'm going to buy the same Notebook as yours, probably, but I wanna have some extra info on it, and considering you have already bought this, I would be very grateful if you could answer a few of my questions.

Can you specify:
Ethernet card model and manufacturer: Qualcom Atheros or BroadCom or Realtek and the exact model ?
Wifi card model and manufacturer: Qualcom Atheros or BroadCom or Realtek and the exact model ?
Blutooth card model and manufacturer: Qualcom Atheros or BroadCom or Realtek and the exact model ?

Thanks for your help.

---

### Post by aljosa2 on 2013-12-10
Hi Toz, 
sorry but I can't tell you nothing about Cinammon, I'am currently on original Xubuntu. 
Thanks for the link, I will report this bug in the next 2-3 days. 
Inside KDE, there were possibilities entitled "keyboard backlight", "screen brightness"... all you need is to click on them and press desired buttons. I dontt know how to do the same thing inside Xfce...


---------------


Hi John, 
here's my experience with notebook Asus N750JV-T4069H...

Shortly after this

[http://cromalternativemoney.org/index.php/en/forum/6-economics/2458-global-monetary-reform-and-the-transformation-of-society](http://cromalternativemoney.org/index.php/en/forum/6-economics/2458-global-monetary-reform-and-the-transformation-of-society)

I've decided to radically change my life. So I've started to work on this

[http://cromalternativemoney.org/index.php/en/media/news/notice-of-the-sovereign-freeman.html](http://cromalternativemoney.org/index.php/en/media/news/notice-of-the-sovereign-freeman.html)

It took me a whole year to write that 74-page document, but I did it :) 
As you can see, switching to Linux is just a small step towards realization of my idea. And here he comes, the N750JV, somewhere in the middle of the process of English and Italian translation of mentioned long document. I saw some of the notebook reviews, so I bought it together with black Thermaltake Massive23 GT. 
I didn't even try it with Windows 8. One second after booting machine for the first time, I've deleted everything inside and installed Xubuntu. 
17,3" Asus looks great with its keyboard backlight. Under Linux no heat problem at all, I have never switched on Thermaltake. My Blutooth is turned off all the time. Both wireless and wired connections are are functioning perfectly. I have also successfully tried to use USB mobile broadband stick. Don't know if it is related to software Guvcview, but the quality of webcam video is not what I've expected. PC speed? From my point of view 8,5 on a scale from 1 to 10. 

Instead of finishing my projects, now already a month I'm researching how to fix Linux compatibility issues on notebook that costs 1200 euro :(
Please give me commands with witch I can extract from machine informations you want to know.

---

### Post by Toz on 2013-12-10
> **aljosa2 said:**
> Hi Toz, 
sorry but I can't tell you nothing about Cinammon, I'am currently on original Xubuntu. 
Thanks for the link, I will report this bug in the next 2-3 days. 
Inside KDE, there were possibilities entitled "keyboard backlight", "screen brightness"... all you need is to click on them and press desired buttons. I dontt know how to do the same thing inside Xfce...
Maybe we can create some custom scripts and assign them to your function keys to get you the functionality you are looking for.

First, for brightness, we need to find your active backlight interface. Run this command:
```
for i in /sys/class/backlight/*; do echo $i;cat $i/brightness;cat $i/max_brightness;done
```
...and it will identify your backlight interfaces.

Secondly, run the following command:
```
xev | grep -A2 --line-buffered '^KeyRelease' | sed -n '/keycode /s/^.*keycode \([0-9]*\).* (.*, \(.*\)).*$/\1 \2/p'
```
...then press your non-working FN keys individually and note the codes that are displayed in the terminal window. Post those codes back.

---

### Post by aljosa2 on 2013-12-11
This time I will first make a backup, so later we can experiment as much as we want.
But before making backup, I need to know this things: 

- I have 2 hard drives, each one 750GB. When I'm browsing with file manager or looking with GParted, it shows 698GB each one. 100GB missing!?!

- Related to your keyboard backlight trick and new scripts, please explain me just one thing so I can decide how to make backup - with or without them... "In the next few days" new Xubuntu and XFCE updates and versions will be released. Let's say with bug fixes and improvements. How will my modificated machine react? In other words, is it better to make backup without tricks, in order to be able to restore original settings before applying important updates and upgrades?

---

### Post by Toz on 2013-12-11
> **aljosa2 said:**
> - I have 2 hard drives, each one 750GB. When I'm browsing with file manager or looking with GParted, it shows 698GB each one. 100GB missing!?!
Actually, it "looks" more like 50GB missing. I'm not sure about gparted, but thunar reports sizes in [Gibibytes]("http://en.wikipedia.org/wiki/Gibibyte") whereas hard drive manufactures report in [gigabytes]("http://en.wikipedia.org/wiki/Gigabyte"). As a test, try this:
...to get gibibytes, run:
```
df -h
```
...and to get gigabytes, run:
```
df -H
```
...and compare the results. The difference is a result of the method used to report drive space (byte = 1000 vs byte = 1024).

> - Related to your keyboard backlight trick and new scripts, please explain me just one thing so I can decide how to make backup - with or without them... "In the next few days" new Xubuntu and XFCE updates and versions will be released. Let's say with bug fixes and improvements. How will my modificated machine react? In other words, is it better to make backup without tricks, in order to be able to restore original settings before applying important updates and upgrades?
What I generally do is document any configuration changes/hacks that I make to the base system so that I can rebuild it exactly. Then as I rebuild, I review every one of these to make sure its still valid (note that I don't have too many of these). With respect to the keyboard brightness trick, all that those commands do is initially change a value in the keyboard brightness file. If this gets fixed in a later release, this command, although redundant) should not cause any issues.

---

### Post by john_earley on 2013-12-11
> **aljosa2 said:**
> 
As you can see, switching to Linux is just a small step towards realization of my idea. And here he comes, the N750JV, somewhere in the middle of the process of English and Italian translation of mentioned long document. I saw some of the notebook reviews, so I bought it together with black Thermaltake Massive23 GT. 
I didn't even try it with Windows 8. One second after booting machine for the first time, I've deleted everything inside and installed Xubuntu. 
17,3" Asus looks great with its keyboard backlight. Under Linux no heat problem at all, I have never switched on Thermaltake. My Blutooth is turned off all the time. Both wireless and wired connections are are functioning perfectly. I have also successfully tried to use USB mobile broadband stick. Don't know if it is related to software Guvcview, but the quality of webcam video is not what I've expected. PC speed? From my point of view 8,5 on a scale from 1 to 10. 

Instead of finishing my projects, now already a month I'm researching how to fix Linux compatibility issues on notebook that costs 1200 euro :(
Please give me commands with witch I can extract from machine informations you want to know.

Cool info, and thanks for your reply, though you haven't answered my question :)

Please, can you check those infos:
You can use: [http://hardinfo.berlios.de/Screenshots](http://hardinfo.berlios.de/Screenshots) to find out brand and models of the parts I asked you.

Thanks.

---

### Post by aljosa2 on 2013-12-11
Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)

Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)

I cannot find nothing about Blutooth (maybe because is disabled - will try tomorrow)

---

### Post by aljosa2 on 2013-12-12
Hi Johny, 
sorry but I cannot find a word about Blutooth. 


-------


Hi Toz, 
everything ok with partitions, sorry for my confusion: 
698 GiB = 750 GB

I've decided to create a backup without tricks. 
Well, it's not so easy to make a complete system partition backup. After 5-6 unsuccessfully attempts with different softwares, at the end I've found qt4-fsarchiver- 

Can you please tell me how can I change default user profile image? 

Before we proceed, do you understand this Xfce warnings in my machine:

> $ xfce4-power-manager --quit #
$ xfce4-power-manager --no-daemon #

(xfce4-power-manager:3494): xfce4-power-manager-WARNING **: Unable to create proxy for 'org.freedesktop.ConsoleKit'

(xfce4-power-manager:3494): xfce4-power-manager-WARNING **: could not map keysym 1008ffa8 to keycode

(xfce4-power-manager:3494): xfce4-power-manager-WARNING **: 'CheckAuthorization' failed with Action org.freedesktop.udisks.drive-set-spindown is not registered

Maybe we can fix this problems, and if not - maybe it would be better to change the power manager instead of intervene with scripts?

---

### Post by Toz on 2013-12-12
> **aljosa2 said:**
> 
I've decided to create a backup without tricks. 
Well, it's not so easy to make a complete system partition backup. After 5-6 unsuccessfully attempts with different softwares, at the end I've found qt4-fsarchiver- 

Can you please tell me how can I change default user profile image?
What do you mean by user profile image? IS it something that that program (qt4-fsarchiver) created? I'm not familiar with that program.

> Before we proceed, do you understand this Xfce warnings in my machine:
[QUOTE]$ xfce4-power-manager --quit #
$ xfce4-power-manager --no-daemon #

(xfce4-power-manager:3494): xfce4-power-manager-WARNING **: Unable to create proxy for 'org.freedesktop.ConsoleKit'

(xfce4-power-manager:3494): xfce4-power-manager-WARNING **: could not map keysym 1008ffa8 to keycode

(xfce4-power-manager:3494): xfce4-power-manager-WARNING **: 'CheckAuthorization' failed with Action org.freedesktop.udisks.drive-set-spindown is not registered 
[/QUOTE]
I'e never seen those messages, but it looks like [this bug report]("https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1116643") might be similar.

---

### Post by aljosa2 on 2013-12-13
Hi Toz,
as you suggested - I reported a bug here: 
[https://bugzilla.xfce.org/show_bug.cgi?id=10543](https://bugzilla.xfce.org/show_bug.cgi?id=10543)

New problem noticed: Power manager is set to reduce display brightnes to 20% after 120 seconds of inactivity, but nothing happens (my screen sarver is disabled).

Shall we start now with your scripts, or is better to wait 2-3 days for potential replies on submited bug report? 

By the way, User profile image successfully-changed by adding following line

> Icon=/home/myusername/pathtoimage

into

> /var/lib/AccountsService/users/myusername

---

### Post by Toz on 2013-12-13
I don't think the bug report that you created will be answered quickly because I think the issue you're facing is a kernel issue. You'd be better off creating a bug report at launchpad.net to get proper support in the Linux kernel for this laptop. It will take time though. You might also want to have a read of [this wiki page]("https://wiki.ubuntu.com/Kernel/MainlineBuilds") and consider trying updated kernel versions to see if you get better support for your laptop with one of the newer kernels. You're using 3.11 and 3.12 versions are available.

However, I thought that with the **acpi_osi=** kernel parameter, that you had control of your backlight. Is that still correct? If so, there should be no need for scripts because the brightness keys worked for you.

> New problem noticed: Power manager is set to reduce display brightnes to 20% after 120 seconds of inactivity, but nothing happens (my screen sarver is disabled).
Please confirm that you are using the **acpi_osi=** kernel parameter:
```
cat /proc/cmdline
```
...that you have one backlight interface:
```
for i in /sys/class/backlight/*; do echo $i;cat $i/brightness;cat $i/max_brightness;done
```
...and that your brightness function keys work.

---

### Post by aljosa2 on 2013-12-15
What a nightmare Toz, 
kernel 3.12 has messed up my efi partition...
1001-st clean installation, this time in normal mode - sayonara UEFI.
I have disabled in BIOS all related to EFI/UEFI + bluetooth and card reader.

So, now I'm on kernel 3.12

> pastebinit /var/log/dmesg

[http://paste.ubuntu.com/6578751/](http://paste.ubuntu.com/6578751/)

At the end I didn't change acpi_osi= kernel parameters.Here's why: It's a "solution" for only 50% of problems, all various tests with Ubuntu and Xubuntu (replacing Xfce, Unity, Cinnamon and KDE one with another) were made on clean installations where /etc/default/grub was original GRUB_CMDLINE_LINUX=""
I noticed some general improvements with the new kernel, but nothing related to my problems. Situation remains the same, with or without Nvidia drivers, with old and latest v3.12-saucy kernel versions- 

> for i in /sys/class/backlight/*; do echo $i;cat $i/brightness;cat $i/max_brightness;done

/sys/class/backlight/acpi_video0
100
100
/sys/class/backlight/acpi_video1
100
100
/sys/class/backlight/intel_backlight
5273
5273

Thanks for your advice to create a bug report at launchpad.net to get proper support. Remeber my first post? *"I'm not sure but it seems to me that my problem is Xubuntu bug. If this is the case, I would be very grateful if someone can communicate the problem to the development team 'cause I get lost inside the more than complicated bug reporting procedure".*
Can we please forget for the moment Fn keys? I'am not an expert so I don't understand well [http://paste.ubuntu.com/6578751/](http://paste.ubuntu.com/6578751/)

**1) **
If it's not a waste of time for you, would you please make me a list of all existing problems. What's impossible-to solve, I will add in detailed report which later will be sent to a Launchpad Team. 

**2) **
It seems to me that this numerous messages are not ok: 
gran_size: 2G  chunk_size: 2G     num_reg: 3   lose cover RAM: 1966M
mtrr_cleanup: can not find optimal value
please specify mtrr_gran_size/mtrr_chunk_size

**3)**
> dmesg | grep -i ath

[    0.977272] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: b2e0a36f82ff774516acdb89df2607487eb68366'
[    7.723768] ath: phy0: Set parameters for CUS198
[    7.723768] ath: phy0: Set BT/WLAN RX diversity capability
[    7.730148] ath: phy0: Enable LNA combining
[    7.731298] ath: EEPROM regdomain: 0x60
[    7.731298] ath: EEPROM indicates we should expect a direct regpair map
[    7.731299] ath: Country alpha2 being used: 00
[    7.731300] ath: Regpair used: 0x60
[    7.763580] ieee80211 phy0: Atheros AR9485 Rev:1 mem=0xffffc90006580000, irq=18

> $ ifconfig

eth0      Link encap:Ethernet  IndirizzoHW d8:50:e6:01:ef:1a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)


lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:215 errors:0 dropped:0 overruns:0 frame:0
          TX packets:215 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:34226 (34.2 KB)  Byte TX:34226 (34.2 KB)


wlan0     Link encap:Ethernet  IndirizzoHW 24:0a:64:94:47:7d  
          indirizzo inet:192.168.0.4  Bcast:192.168.0.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::260a:64ff:fe94:477d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1025 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1066 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:552564 (552.5 KB)  Byte TX:308639 (308.6 KB)

What are those errors? Can I fix them applying [http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/](http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/)

Thanks in advance for your help, regards..

---

### Post by Toz on 2013-12-15
> for i in /sys/class/backlight/*; do echo $i;cat $i/brightness;cat $i/max_brightness;done

/sys/class/backlight/acpi_video0
100
100
/sys/class/backlight/acpi_video1
100
100
/sys/class/backlight/intel_backlight
5273
5273 First of all, try the kernel parameters:
```
acpi_osi= acpi_backlight=vendor
```
...this should remove the two acpi_video interfaces.

> 1)
If it's not a waste of time for you, would you please make me a list of all existing problems. What's impossible-to solve, I will add in detailed report which later will be sent to a Launchpad Team.
These are the issues as you have identified them (with the acpi_osi= kernel parameter):
> _NOT OK:_
Power Adapter shows not connected
No keyboard backlightng
FN (F3) Decreases keyboard backlighting
FN (F4) Increases keyboard backlighting
FN (F9) Enables or disables the touchpad
_OK:_
Battery shows 100%
FN (F1) Puts the Notebook PC into Sleep mode
FN (F2) Turns Airplane mode on or off
FN (F5) Decreases display brightness
FN (F6) Increases display brightness
FN (F7) Turns the display panel off
FN (F8) Activates the second screen
FN (F10) Turns the speaker on or off
FN (F11) Turns the speaker volume down
FN (F12) Turns the speaker volume up 

To organize them, I see 4 main issues:
- power recognition (power adapter/battery) -> this is a kernel/acpi issue
- backlight -> this is a kernel/video issue
- keyboard backlight -> this maybe a kernel/acpi issue (not sure)
- hotkeys -> this is most probably a desktop environment problem except display brightness hotkeys, which might be kernel or even bios issue.

> 2)
It seems to me that this numerous messages are not ok:
gran_size: 2G chunk_size: 2G num_reg: 3 lose cover RAM: 1966M
mtrr_cleanup: can not find optimal value
please specify mtrr_gran_size/mtrr_chunk_size
[This thread]("http://ubuntuforums.org/showthread.php?t=1923058") (and solution) looks relevant.

> 3)What are those errors? 
I don't see any errors. Are you having issues with your network?

---

### Post by aljosa2 on 2013-12-17
Hi Toz,
when UEFI secure boot is disabled, my notebook can boot from CD drive even if this option is disabled in BIOS. It is something I cannot accept. 

I saw a notice that Xubuntu 14.04 Trusty Tahr will be released in less than 6 months, so I've installed testing version. Already tired of uninstalling and reinstalling, hope you can help me to write and send detailed bug report in order to help experts develope a software with which we will all be satisfied in the end. 

Related to my efi partition, good news is that I've successfully upgraded Kernel to version 3.12.5-trusty. 
After that, I made a backup of my ext4 System/Home partition. Unfortunately, I'am not able to do same with fat32 EFI partition. 


**Bug Report**:

Asus N750JV-T4069H (Intel® Core™ i7-4700HQ; Bit 64; Nvidia GeForce GT750M)
BIOS N750JV.207 (bluetooth, card reader and network stack disabled)

Xubuntu 14.04 LTS 64 bit
Kernel v3.12.5-trusty
Xubuntu session

> pastebinit /var/log/dmesg

[http://paste.ubuntu.com/6588075/](http://paste.ubuntu.com/6588075/)

- Numerous error messages:
  gran_size: 2G chunk_size: 2G num_reg: 3 lose cover RAM: 1966M
  mtrr_cleanup: can not find optimal value
  please specify mtrr_gran_size/mtrr_chunk_size

- Unable to install Nvidia drivers

- Power manager is set to reduce display brightnes to 20% after 120 seconds of inactivity, but nothing happens

- Power Adapter shows not connected
  (works fine in liveCD)

- No keyboard backlightng

- FN (F3) Decreases keyboard backlighting

- FN (F4) Increases keyboard backlighting
  (I can turn on keyboard backlight with 
  sudo chmod 777 /sys/class/leds/asus::kbd_backlight/brightness
  echo 3 > /sys/class/leds/asus::kbd_backlight/brightness
  but effect is lost after turning the computer off and on again).

- FN (F9) Enables or disables the touchpad

- FN (F5) Decreases display brightness

- FN (F6) Increases display brightness
  (I can adjust brightness only through system tray icon xfce4-panel-plugin-brightness)

- FN (F2) Turns Airplane mode on or off

- FN (F1) Notebook returns from sleep mode with broken screen and strange vertical colour lines


----------------------


Is it ok like this? Please feel free to edit or make any changes... 
I already have a Launchpad account, but don't have a clue where and how bug report can be submitted :(

By the way, Toz, when I change kernel parameters, I see many new errors in dmesg

> pastebinit /var/log/dmesg

[http://paste.ubuntu.com/6589909/](http://paste.ubuntu.com/6589909/)

> for i in /sys/class/backlight/*; do echo $i;cat $i/brightness;cat $i/max_brightness;done

/sys/class/backlight/asus-nb-wmi
10
10
/sys/class/backlight/intel_backlight
4845
4882

It seems to me that nothing changes with numerous error messages when I change iGPU to 256:

> pastebinit /var/log/dmesg

[http://paste.ubuntu.com/6590090/](http://paste.ubuntu.com/6590090/)

---

### Post by Toz on 2013-12-17
> I already have a Launchpad account, but don't have a clue where and how bug report can be submitted 
```
ubuntu-bug linux
```
...will get you started.

---

### Post by aljosa2 on 2013-12-18
Thanks Toz, 
with this (mainline 3.12.5) kernel version - it redirects me to Bugzilla... done: 

[https://bugzilla.kernel.org/show_bug.cgi?id=67271](https://bugzilla.kernel.org/show_bug.cgi?id=67271)

---

### Post by aljosa2 on 2013-12-20
I have contacted Ubuntu Support, but still no reply... 
In the meantime BIOS successfully flashed to N750JV.208 version, but can't notice any positive change.

I found (at least I hope so) some kind of solution how to fix numerous mtrr error messages, but don't have a clue which option to choose:


**GRUB_CMDLINE_LINUX_DEFAULT="nouveau.blacklist=1 quiet splash enable_mtrr_cleanup mtrr_spare_reg_nr=1 mtrr_gran_size=64M mtrr_chunk_size=64M"**

> pastebinit /var/log/dmesg
[http://paste.ubuntu.com/6606941/](http://paste.ubuntu.com/6606941/)

WARNING: BIOS bug: CPU MTRRs don't cover all of memory, losing 78MB of RAM.

> cat /proc/mtrr

reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x080000000 ( 2048MB), size=  512MB, count=1: write-back
reg02: base=0x0a0000000 ( 2560MB), size=  128MB, count=1: write-back
reg03: base=0x0a8000000 ( 2688MB), size=   64MB, count=1: write-back
reg04: base=0x100000000 ( 4096MB), size= 4096MB, count=1: write-back
reg05: base=0x200000000 ( 8192MB), size= 8192MB, count=1: write-back
reg06: base=0x400000000 (16384MB), size=  512MB, count=1: write-back
reg07: base=0x420000000 (16896MB), size=  128MB, count=1: write-back
reg08: base=0x428000000 (17024MB), size=   64MB, count=1: write-back

**GRUB_CMDLINE_LINUX_DEFAULT="nouveau.blacklist=1 quiet splash enable_mtrr_cleanup mtrr_spare_reg_nr=1 mtrr_gran_size=8M mtrr_chunk_size=64M"**

> pastebinit /var/log/dmesg
[http://paste.ubuntu.com/6606910/](http://paste.ubuntu.com/6606910/)

WARNING: BIOS bug: CPU MTRRs don't cover all of memory, losing 2MB of RAM.

> cat /proc/mtrr

reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x080000000 ( 2048MB), size=  512MB, count=1: write-back
reg02: base=0x0a0000000 ( 2560MB), size=  256MB, count=1: write-back
reg03: base=0x0af800000 ( 2808MB), size=    8MB, count=1: uncachable
reg04: base=0x100000000 ( 4096MB), size= 4096MB, count=1: write-back
reg05: base=0x200000000 ( 8192MB), size= 8192MB, count=1: write-back
reg06: base=0x400000000 (16384MB), size=  512MB, count=1: write-back
reg07: base=0x420000000 (16896MB), size=  256MB, count=1: write-back
reg08: base=0x42f000000 (17136MB), size=   16MB, count=1: uncachable

**GRUB_CMDLINE_LINUX_DEFAULT="nouveau.blacklist=1 quiet splash enable_mtrr_cleanup mtrr_spare_reg_nr=1 mtrr_gran_size=32M mtrr_chunk_size=64M"**

> pastebinit /var/log/dmesg
[http://paste.ubuntu.com/6606879/](http://paste.ubuntu.com/6606879/)

WARNING: BIOS bug: CPU MTRRs don't cover all of memory, losing 18MB of RAM.

> cat /proc/mtrr

reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x080000000 ( 2048MB), size=  512MB, count=1: write-back
reg02: base=0x0a0000000 ( 2560MB), size=  256MB, count=1: write-back
reg03: base=0x0ae000000 ( 2784MB), size=   32MB, count=1: uncachable
reg04: base=0x100000000 ( 4096MB), size= 4096MB, count=1: write-back
reg05: base=0x200000000 ( 8192MB), size= 8192MB, count=1: write-back
reg06: base=0x400000000 (16384MB), size=  512MB, count=1: write-back
reg07: base=0x420000000 (16896MB), size=  256MB, count=1: write-back
reg08: base=0x42e000000 (17120MB), size=   32MB, count=1: uncachable

**GRUB_CMDLINE_LINUX_DEFAULT="nouveau.blacklist=1 quiet splash enable_mtrr_cleanup mtrr_spare_reg_nr=1 mtrr_gran_size=32M mtrr_chunk_size=128M"**

> pastebinit /var/log/dmesg
[http://paste.ubuntu.com/6606847/](http://paste.ubuntu.com/6606847/)

WARNING: BIOS bug: CPU MTRRs don't cover all of memory, losing 18MB of RAM.

> cat /proc/mtrr

reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x080000000 ( 2048MB), size=  512MB, count=1: write-back
reg02: base=0x0a0000000 ( 2560MB), size=  256MB, count=1: write-back
reg03: base=0x0ae000000 ( 2784MB), size=   32MB, count=1: uncachable
reg04: base=0x100000000 ( 4096MB), size= 4096MB, count=1: write-back
reg05: base=0x200000000 ( 8192MB), size= 8192MB, count=1: write-back
reg06: base=0x400000000 (16384MB), size=  512MB, count=1: write-back
reg07: base=0x420000000 (16896MB), size=  256MB, count=1: write-back
reg08: base=0x42e000000 (17120MB), size=   32MB, count=1: uncachable

---

