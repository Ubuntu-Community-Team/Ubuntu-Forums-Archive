---
title: "brightness control doesn't work. Why does documentation say it does?"
date: 2010-11-23
forum: Apple Hardware Users
---

### Post by itismike on 2010-11-23
According to the Community Documentation for a _[6,2 running Maverick]("https://help.ubuntu.com/community/MacBookPro6-2/Maverick#LCD")_, the LCD brightness just "Works." 
I have mbp-nvidia-bl-dkms and pommed installed, but this has never worked for me. 
Anybody know what's up with this?

---

### Post by lael on 2010-11-24
I have a MacbookPro6,1 and my backlight is working with the mbp-nvidia-bl-dkms module with pommed.  (the 6,1 is very close to the 6,2 in hardware)

Are you sure that the module is running?
```
lsmod  | grep bl
```
should reveal the kernel module.

---

### Post by itismike on 2010-11-24
Hi lael. Thanks for the reply. Just to clarify, the LCD/screen backlight brightness is on, but is non-adjustable using the F1 & F2 keys, so it is always full-bright. Which module are you looking for here?
```
$ lsmod  | grep bl
bluetooth              59245  9 rfcomm,sco,bnep,l2cap,btusb
```

---

### Post by vsh3r on 2010-11-24
Hi,

The brightness controls done via pommed.  The display is working on macbook pro 6,2 however the indicator or display that shows up on the screen seems to lag the actual brightness.

(see attached screen-shot)

Also, there has been some recent changes in the Ubuntu POMMED.  You might want to make sure you have the latest POMMED installed 1.35 - I believe.

I have the following installed: pommed, gpommed, wmpomme

All of them may be required.

V$H.

---

### Post by itismike on 2010-11-25
Hi V$H. pommed and gpommed were installed when I followed the [_steps in the documentation_]("https://help.ubuntu.com/community/MacBookPro6-2/Maverick#Package%20Support%20for%20Intel%20Macs"). wmpomme appears to be specifically for a panel dockapp, and since I don't need another applet in my toolbar I haven't installed it. But since this still isn't working for me I'll try to install it anyway. [I installed it, and now have an icon on my panel called "Power Manager Brightness Applet 2.32.0." But it has a red X through it which states: "cannot get laptop panel brightness."]

I didn't realize pommed needed to be launched manually. Now that I launched it, it does respond to the F1 & F2 keys (see screenshot.) But the brightness still doesn't change, nor does the brightness indicator move past about 5% (as displayed in the screenshot.) 

What bugs me is that some of these mactel documentation pages seem pretty inconsistent, and I'm curious how they got this way. Was this template copied from another architecture without confirming its accuracy? Or were the green checkmarks added because they look pretty?

---

### Post by wilee-nilee on 2010-11-25
Have you just tried the fn key held down and the left right arrows on the keyboard.

---

### Post by _mario_ on 2010-11-25
> **itismike said:**
> Hi lael. Thanks for the reply. Just to clarify, the LCD/screen backlight brightness is on, but is non-adjustable using the F1 & F2 keys, so it is always full-bright. Which module are you looking for here?
```
$ lsmod  | grep bl
bluetooth              59245  9 rfcomm,sco,bnep,l2cap,btusb
```

The module isn't loaded. Besides that, also consider [this thread]("https://bugs.launchpad.net/bugs/659780") for more information regarding your model and pommed in general.

> **itismike said:**
> 
I didn't realize pommed needed to be launched manually. Now that I launched it, it does respond to the F1 & F2 keys (see screenshot.) But the brightness still doesn't change, nor does the brightness indicator move past about 5% (as displayed in the screenshot.)

Pommed doesn't need to be started manually, but it usually relies on the driver operating correctly. 

> **itismike said:**
> 
What bugs me is that some of these mactel documentation pages seem pretty inconsistent, and I'm curious how they got this way. Was this template copied from another architecture without confirming its accuracy? Or were the green checkmarks added because they look pretty?

Usually people tried to install Ubuntu and then wrote/updated the documentation. You can add your notes if you like, further improving the site. But please consider, that your installation might be broken...

ciao,
Mario

---

### Post by acarlstein on 2010-12-14
> **itismike said:**
> Hi V$H. pommed and gpommed were installed when I followed the [_steps in the documentation_]("https://help.ubuntu.com/community/MacBookPro6-2/Maverick#Package%20Support%20for%20Intel%20Macs"). wmpomme appears to be specifically for a panel dockapp, and since I don't need another applet in my toolbar I haven't installed it. But since this still isn't working for me I'll try to install it anyway. [I installed it, and now have an icon on my panel called "Power Manager Brightness Applet 2.32.0." But it has a red X through it which states: "cannot get laptop panel brightness."]

I didn't realize pommed needed to be launched manually. Now that I launched it, it does respond to the F1 & F2 keys (see screenshot.) But the brightness still doesn't change, nor does the brightness indicator move past about 5% (as displayed in the screenshot.) 

What bugs me is that some of these mactel documentation pages seem pretty inconsistent, and I'm curious how they got this way. Was this template copied from another architecture without confirming its accuracy? Or were the green checkmarks added because they look pretty?

:D :D Today, maybe is your lucky day! An actual answer!!! :D :D

sudo add-apt-repository ppa:mactel-support && sudo apt-get update

sudo apt-get install pommed mbp-nvidia-bl-dkms macfanctld btusb-dkms

do: 
lsmod | grep bl

if this line doesn't show: mbp_nvidia_bl           3359  0
That means the module is not loaded in the kernel.

To load the module do the following line:

sudo modprobe mbp_nvidia_bl

Check again to see if the module is working: lsmod | grep bl 

Now try to see if it works.
You may increase and decrease the brightness using fn-F1 and fn-F2

ENJOY!!! :popcorn:

---

### Post by itismike on 2010-12-14
> **acarlstein said:**
> :D :D Today, maybe is your lucky day! An actual answer!!! :D :D
...
sudo modprobe mbp_nvidia_bl
...
ENJOY!!! :popcorn:

You nailed it! Thanks acarlstein!!! 

:guitar:

You ROCK!!!

---

### Post by itismike on 2010-12-15
I've added your tip to the [_community documentation_]("https://help.ubuntu.com/community/MacBookPro6-2/Maverick#LCD%20Brightness%20Control").

---

### Post by itismike on 2010-12-24
Update: This is not a permanent solution. Looks like /etc/modprobe.d/nvidia-bl-dkms.conf is actively blocking mbp_nvidia_bl from loading:
```
#
# This file has been automatically installed by nvidia-bl-dkms. Do not edit.
# If you do, don't forget to run `update-initramfs -k all -u` after updating.
#

# blacklist mbp_nvidia_bl in favor of nvidia_bl
blacklist mbp_nvidia_bl

```
Can someone who understand how these pieces work together help with a work-around?

---

### Post by _mario_ on 2010-12-29
> **itismike said:**
> 
Update: This is not a permanent solution. Looks like /etc/modprobe.d/nvidia-bl-dkms.conf is actively blocking mbp_nvidia_bl from loading:
```

#
# This file has been automatically installed by nvidia-bl-dkms. Do not edit.
# If you do, don't forget to run `update-initramfs -k all -u` after updating.
#
# blacklist mbp_nvidia_bl in favor of nvidia_bl blacklist mbp_nvidia_bl

```
Can someone who understand how these pieces work together help with a work-around?

yepp. both drivers (should) support a common set of hardware. since, mbp_nvidia_bl is designed to work for Apple machines, while nvidia_bl supports a broader range including other vendors, I decided to favor nvidia_bl (which is better anyway). the reason for this is simple: you shouldn't run both drivers at the same time, but both drivers should auto-load if possible. hence, nvidia_bl disables auto-loading of mbp_nvidia_bl if installed. consequently, if nvidia_bl doesn't work, just deinstall it and mbp_nvidia_bl comes back to life again.

ciao,
Mario

---

### Post by itismike on 2011-01-05
Mario: what changes would you suggest on the [Community Documentation page]("https://help.ubuntu.com/community/MacBookPro6-2/Maverick") for a basic install to provide functional backlighting without the conflicting drivers? 

Should the suggested [Basic Installation Instructions]("https://help.ubuntu.com/community/MacBookPro6-2/Maverick#Basic%20Installation%20Instructions") include steps to manually remove nvidia_bl?

---

### Post by _mario_ on 2011-01-10
> **itismike said:**
> Mario: what changes would you suggest on the [Community Documentation page]("https://help.ubuntu.com/community/MacBookPro6-2/Maverick") for a basic install to provide functional backlighting without the conflicting drivers? 

Should the suggested [Basic Installation Instructions]("https://help.ubuntu.com/community/MacBookPro6-2/Maverick#Basic%20Installation%20Instructions") include steps to manually remove nvidia_bl?

in general, there's no right answer. for the macbook pro 6,2, however, the page you referenced does not seem to suggest the installation of nvidia_bl. hence, you don't have to remove it.

ciao,
Mario

---

### Post by itismike on 2011-01-10
> **_mario_ said:**
> in general, there's no right answer. for the macbook pro 6,2, however, the page you referenced does not seem to suggest the installation of nvidia_bl. hence, you don't have to remove it.

ciao,
Mario

It looks like the [Mactel PPA]("https://launchpad.net/~mactel-support/+archive/ppa") installs nvidia_bl_dkms. Is that different than nvidia_bl? If not, then I don't know how nvidia_bl got onto my system unless it is added when "Additional Drivers" are offered right after the base installation. I probably accepted the suggested drivers, and found the Community Documentation pages afterward. If someone can verify this I'll update the documentation to explicitly remove any additional drivers before enabling the Mactel PPA.

---

### Post by apfejes on 2011-01-21
I have a strange variant of this problem - the controls don't work, though I've followed all of the advice above.  HOWEVER, the slider for screen brightness does work on the power management applet.  

Has anyone else come across this before, and if so, is there any way to associate the F1/F2 keys with the slider settings for the power management applet?

(I've already tried modifying the settings in the gestures panel, to no avail.)

Yes, it's weird,  I know.

---

### Post by singlebinary on 2011-01-29
I have followed the instructions of acarlstein however I do not get the result as expected. Below are the details: 

MacBookPro6,2

Doing lsmod |grep bl gives me the following: 

mbp_nvidia_bl           2707  0 
bluetooth              50500  7 rfcomm,sco,bnep,l2cap,btusb

Here is the version of Ubuntu I am using: 

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick

I also have pommed installed. Please let me know how to get the brightness to work. 

Thanks!

---

### Post by itismike on 2011-01-29
I'm curious why your filesize (2707) is different than mine:
```
$ sudo lsmod |grep bl
mbp_nvidia_bl           3359  0 
```

Did you install the [MacTel PPAs]("https://help.ubuntu.com/community/MacBookPro6-2/Lucid#Package%20Support%20for%20Intel%20Macs")?

---

### Post by singlebinary on 2011-01-29
Is this because I am running Ubuntu using Bootcamp, perhaps? Do you need any more information to solve the problem of brightness? Please let me know. Thanks!

---

### Post by itismike on 2011-01-29
singlebinary, you didn't answer my question about the MacTel PPAs in the link above. Assuming the answer is yes, then I am not sure why it's not working for you. Maybe you could ask _mario_, as he seems to be one of the developers that is very familiar with the nVidia driver situation.

I'm also using bootcamp on a 6,2 MacBook with Ubuntu 10.10 (64-bit), and after running the command below, LCD dimming works fine for me:

```
sudo modprobe mbp_nvidia_bl
```
:popcorn:

---

### Post by singlebinary on 2011-01-29
Oops! Sorry. Yes indeed I have installed Mactel PPA.

---

### Post by Alejandro Castanaza on 2011-01-31
Hi.
I also have the macbookpro 6,2 and followed all the instructions of the documentation and brightness control works, using F1 and F2.
What does not work in my case, is the automatic dimming of the display depending on the ambient light, like it does in mac os x.

---

### Post by itismike on 2011-01-31
> **Alejandro Castanaza said:**
> What does not work in my case, is the automatic dimming of the display depending on the ambient light, like it does in mac os x.

Same for me.

---

### Post by _mario_ on 2011-02-01
Hi,

if you installed the package mbp-nvidia-bl-dkms from the Mactel PPA, there should be a diagnostics script /usr/src/mbp_nvidia_bl-0.25.4/scripts/mbp-nvidia-bl-diagnostics. please report back its output.

ciao,
Mario

---

### Post by Alejandro Castanaza on 2011-03-12
Hi.
Sorry for the delay :(

Here is the output of the diagnostics script:

----------=[ verifying mbp_nvidia_bl ]=----------
* Kernel version: 2.6.35-27-generic
* Graphics drivers loaded: nvidia 
* Driver installed as: /lib/modules/2.6.35-27-generic/updates/dkms/mbp_nvidia_bl.ko
* No old options in xorg.conf: OK
* Setting brightness to: 0
sudo
* Setting brightness to: 7
* Setting brightness to: 15

After supplying the credentials for sudoing, the script changed the screen brightness to the levels specified in this output automatically.
But, as I said earlier, in my case brightness adjusting with F1 and F2 has worked ok since the begining. The auto dimming based on ambient light is not working, though.

Thank you.

---

### Post by titaniumlou on 2011-06-14
Greetings, I'm currently unable to alter the LCD brightness on my MacbookPro running Ubuntu 11.04

Currently I have to manually load the nvidia_bl module and after doing that I can see the LCD brightness meter change in the upper-right-hand corner when I press the F1 and F2 keys but I don't see the actual brightness of the LCD change.

Here is the lsmod output verifying that the module is loaded and the output of running the diagnostics script if it helps any:
```

user@computer:~$ sudo lsmod | grep nvidia
nvidia_bl              17704  0 
nvidia              10709116  43 
user@computer:~$ sudo /usr/src/nvidia_bl-0.17.3/scripts/nvidia-bl-diagnostics 
----------=[ verifying nvidia_bl ]=----------
* Vendor:  Apple Inc.
* Machine: MacBookPro6,1
* Kernel version: 2.6.38-8-generic
* Graphics drivers loaded: nvidia 
* Driver installed as: /lib/modules/2.6.38-8-generic/updates/dkms/nvidia_bl.ko
* No old options in xorg.conf: OK
* Setting brightness to: 0
* Setting brightness to: 1023
* Setting brightness to: 2047

```

---

### Post by beaufils on 2011-06-15
I get the same behavior with Natty (11.04). I just reinstalled my laptop to encrypt some partitions, before doing that I just upgraded from Maverick and everything worked fine.

root@watney:~# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.04
Release:	11.04
Codename:	natty

root@watney:~# /usr/src/nvidia_bl-0.17.3/scripts/nvidia-bl-diagnostics 
----------=[ verifying nvidia_bl ]=----------
* Vendor:  Apple Inc.
* Machine: MacBookPro6,2
* Kernel version: 2.6.38-8-generic
* Graphics drivers loaded: nvidia 
* Driver installed as: /lib/modules/2.6.38-8-generic/updates/dkms/nvidia_bl.ko
* No old options in xorg.conf: OK
* Setting brightness to: 0
* Setting brightness to: 1023
* Setting brightness to: 2047
root@watney:~#

Any idea how to fix that ?

---

### Post by MacHackers on 2011-06-17
Hey Ubuntu Users. I have an eMac and was wondering why the brightness can't be controlled by the specified buttons on the keyboard. Any Suggestions?

---

### Post by beaufils on 2011-06-19
I found a fix : **do not install nvidia-bl-dkms** from "PPA for Mactel Support" (available in the Natty serie), remove it (apt-get --purge remove nvidia-bl-dkms) if already installed ; but **install mbp-nvidia-bl-dkms** (apt-get install -t=maverick mbp-nvidia-bl-dkms) from the same place but in the Maverick serie.

Do not know why, and do not know the difference between the two, the fact is just that with the old one backlight is working.

---

### Post by danger89 on 2011-07-16
> **beaufils said:**
> I found a fix : **do not install nvidia-bl-dkms** from "PPA for Mactel Support" (available in the Natty serie), remove it (apt-get --purge remove nvidia-bl-dkms) if already installed ; but **install mbp-nvidia-bl-dkms** (apt-get install -t=maverick mbp-nvidia-bl-dkms) from the same place but in the Maverick serie.

Do not know why, and do not know the difference between the two, the fact is just that with the old one backlight is working.

This works for me:
[http://www.addictivetips.com/ubuntu-linux-tips/fix-laptop-brightness-toggle-issues-in-ubuntu-10-10-and-11-04-tip/](http://www.addictivetips.com/ubuntu-linux-tips/fix-laptop-brightness-toggle-issues-in-ubuntu-10-10-and-11-04-tip/)

---

### Post by rea11ity on 2011-08-29
> **beaufils said:**
> I found a fix : **do not install nvidia-bl-dkms** from "PPA for Mactel Support" (available in the Natty serie), remove it (apt-get --purge remove nvidia-bl-dkms) if already installed ; but **install mbp-nvidia-bl-dkms** (apt-get install -t=maverick mbp-nvidia-bl-dkms) from the same place but in the Maverick serie.

Do not know why, and do not know the difference between the two, the fact is just that with the old one backlight is working.

Hey

I'm trying your approach and I'm getting this:

~#apt-get -t=maverick install mbp-nvidia-bl-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package mbp-nvidia-bl-dkms

Did you do something else?

BR,
p

---

### Post by montchr on 2011-09-05
i'm getting the same message.

---

### Post by itismike on 2011-09-05
Found a permanent solution: upgraded to 11.10 beta.

---

### Post by itismike on 2011-09-09
> **itismike said:**
> Found a permanent solution: upgraded to 11.10 beta.

Ironically the backlight for the screen now works, but the backlight to the keyboard does not. I did an in-place upgrade (not sure why I bothered - it has NEVER been successful in ten years of Linux desktop use!) and am planning a fresh install. Hopefully things will be harmonious then.

---

### Post by beaufils on 2011-09-19
> I'm trying your approach and I'm getting this:

~#apt-get -t=maverick install mbp-nvidia-bl-dkms
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package mbp-nvidia-bl-dkms

Did you do something else?


Did you add support for mactel PPA (sudo apt-add-repository ppa:mactel-support ; sudo apt-get update) before trying to install it ?

---

### Post by mistermrf on 2011-09-26
If you've started out with 11.04 you won't have the PPA for Maverick available.

Add the following and you'll have access to the older mbp_nvidia_bl driver which has restored the backlight on my MBP 6,2

```
deb [http://ppa.launchpad.net/mactel-support/ppa/ubuntu](http://ppa.launchpad.net/mactel-support/ppa/ubuntu) maverick main
```

---

### Post by Freek07 on 2011-12-02
I can't get it working, too...and it's crazy working at 100% non-stop.

So, here are the details:
MBP 5,1.
Oneiric, uname
root@Mac:/sys/class/backlight/nvidia_backlight# uname -a
Linux Mac 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux


As the kernel bl module didn't work I installed both BL modules (from official repo and from mactel):
root@Mac:/home/may# dpkg -l | grep nvidia
ii  nvidia-bl-dkms                           0.17.3~natty                             Supplementary Nvidia laptop display backlight support
ii  nvidiabl-dkms                            0.71                                     nvidiabl driver in DKMS format.

Of course not loaded at the same time!
I have both "nvidia_bl" and "nvidiabl" modules.

When I try loading nvidia_bl it crashes:

  361.214240] nvidia_bl: MacBookPro 5,1 detected
[  361.214279] nvidia_bl: Nvidia graphics adapter 10de:0863 (106b:00ac) detected
[  361.214318] ------------[ cut here ]------------
[  361.214327] WARNING: at /build/buildd/linux-3.0.0/drivers/video/backlight/backlight.c:314 backlight_device_register+0x1bd/0x200()
[  361.214331] Hardware name: MacBookPro5,1
[  361.214333] nvidia_backlight: invalid backlight type
[  361.214335] Modules linked in: nvidia_bl(+) michael_mic arc4 hidp bnep rfcomm parport_pc ppdev dm_crypt snd_hda_codec_realtek binfmt_misc nls_utf8 hfsplus nls_iso8859_1 nls_cp437 vfat fat joydev snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi btusb snd_rawmidi lib80211_crypt_tkip bluetooth uvcvideo videodev bcm5974 wl(P) v4l2_compat_ioctl32 snd_seq_midi_event snd_seq nvidia(P) lib80211 snd_timer snd_seq_device snd shpchp soundcore snd_page_alloc apple_bl applesmc input_polldev i2c_nforce2 coretemp lp parport hid_apple usbhid hid firewire_ohci firewire_core crc_itu_t ahci libahci forcedeth [last unloaded: nvidiabl]
[  361.214391] Pid: 4105, comm: modprobe Tainted: P        W   3.0.0-13-generic #22-Ubuntu
[  361.214394] Call Trace:
[  361.214401]  [<ffffffff8105e8af>] warn_slowpath_common+0x7f/0xc0
[  361.214406]  [<ffffffff8105e9a6>] warn_slowpath_fmt+0x46/0x50
[  361.214412]  [<ffffffff813ce569>] ? dev_set_drvdata+0x39/0x50
[  361.214416]  [<ffffffff8134562d>] backlight_device_register+0x1bd/0x200
[  361.214422]  [<ffffffffa10ad000>] ? 0xffffffffa10acfff
[  361.214428]  [<ffffffffa10ad351>] nvidia_bl_init+0x351/0x1000 [nvidia_bl]
[  361.214434]  [<ffffffff81002042>] do_one_initcall+0x42/0x180
[  361.214439]  [<ffffffff8109ffee>] sys_init_module+0xbe/0x230
[  361.214446]  [<ffffffff815f27c2>] system_call_fastpath+0x16/0x1b
[  361.214449] ---[ end trace 70933a28fca00caf ]---


(and it obviously doesn't work).

And when I try the other, nvidiabl, it seems to be loaded OK:

[  419.494204] nvidiabl: loading driver version 0.71
[  419.494213] nvidiabl: Apple Inc. - MacBookPro5,1 model detected in DMI tables
[  419.494252] nvidiabl: Supported Nvidia graphics adapter 10de:0863:106b:00ac detected
[  419.494319] nvidiabl: backup register value 0x3ff
[  419.494321] nvidiabl: autodetecting maximum
[  419.494323] nvidiabl: using value 0x3ff as maximum
[  419.494325] nvidiabl: autodetecting off
[  419.494327] nvidiabl: using value 0x0 as off
[  419.494329] nvidiabl: autodetecting minimum
[  419.494331] nvidiabl: minimum is 5% of maximum
[  419.494333] nvidiabl: using value 0x64 as minimum
[  432.477186] nvidiabl: restore register value 0x3ff
[  453.616854] nvidiabl: loading driver version 0.71
[  453.616862] nvidiabl: Apple Inc. - MacBookPro5,1 model detected in DMI tables
[  453.616902] nvidiabl: Supported Nvidia graphics adapter 10de:0863:106b:00ac detected
[  453.617553] nvidiabl: backup register value 0x3ff
[  453.617556] nvidiabl: autodetecting maximum
[  453.617558] nvidiabl: using value 0x3ff as maximum
[  453.617560] nvidiabl: autodetecting off
[  453.617562] nvidiabl: using value 0x0 as off
[  453.617563] nvidiabl: autodetecting minimum
[  453.617566] nvidiabl: minimum is 5% of maximum
[  453.617568] nvidiabl: using value 0x64 as minimum


but it doesn't work!
The F1/F2 shows brightness dialog but the brightness doesn't change.

If I try changing it manually it changes the value in "brightness" and "actual_brightness" files but it's still working at 100%:

root@Mac:/sys/class/backlight/nvidia_backlight# cat max_brightness 
127
root@Mac:/sys/class/backlight/nvidia_backlight# cat brightness 
127
root@Mac:/sys/class/backlight/nvidia_backlight# cat actual_brightness 
127
root@Mac:/sys/class/backlight/nvidia_backlight# echo "15" > brightness 
root@Mac:/sys/class/backlight/nvidia_backlight# cat actual_brightness 
14
root@Mac:/sys/class/backlight/nvidia_backlight# cat brightness 
15
root@Mac:/sys/class/backlight/nvidia_backlight# 

(still working at 100%)

I tried putting "Option" "RegistryDwords" "EnableBrightnessControl=1" in Xorg.conf but it doesn't work, too (it actually breaks graphics- the screen gets distorted).

Any ideas? :(

---

### Post by itismike on 2011-12-02
I threw it all to the wind and installed a nightly build of 12.04. Seems to be working there! :)

---

### Post by Freek07 on 2011-12-06
> **itismike said:**
> I threw it all to the wind and installed a nightly build of 12.04. Seems to be working there! :)

I don't have guts to install prerelease on development machine :)
Could you tell me:
kernel version ("uname -a")
dkms version if any ("dpkg -l | grep dkms")
and X version ("Xorg -version")

Maybe I can make it work on Oneiric with right versions :-p

---

### Post by fouad_jh on 2012-01-25
Hi Guys

I am running Ubuntu 11.04 on my MacBook pro 6,2.

As many mentioned that you have to do the following:
1- Uninstall nvidia-bl-dkms

2- Install mbp-nvidia-bl-dkms (in my case, I couldn't install it from the command line as it kept throwing -unable to locate...- so I downloaded it as .deb file and installed it on my system.

3- Just to make sure that your mbp-nvidia-bl-dkms works fine, run the command: sudo modprob mbp-nvidia-bl
then try to change the brightness, if it works then the package is fine and working.

4- Here is what made all this work:
    A. Go to /etc/modprobe.d directory.

    B. if you do ls, you will find file called "nvidia-bl-     dkms.conf" which I assume it was created by nvidia-bl-dkms and it blocks mbp-nvidia-bl-dkms

    C.Change the file extension: sudo mv nvidia-bl-dkms.conf nvidi-bl-dkms.bak

    D. Restart your system

---

