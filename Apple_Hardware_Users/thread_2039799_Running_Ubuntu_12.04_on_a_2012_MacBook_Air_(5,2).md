---
title: "Running Ubuntu 12.04 on a 2012 MacBook Air (5,2)"
date: 2012-08-09
forum: Apple Hardware Users
---

### Post by sgarman on 2012-08-09
I recently obtained a 2012 13" MacBook Air (MBA) to use as a development laptop. The documentation on installing and running Linux on this year's model is fairly sparse and had to be collected and verified from numerous sources, so I'm summarizing it here in this post in the hopes it will be helpful to others. *Follow these instructions at your own risk, and acknowledge that I accept no responsibility for possible damage that could happen to your computer due to following these instructions.*

I will try to edit and maintain this post as I learn new information or others correct me for any misundertandings (which I highly encourage you to do). 

I have absolutely no interest in OS X (and to be honest feel more than a tad hypocritical for buying an Apple product, but that's a rant for another time), so my goal was just to wipe the default OS and install a Linux distro (Ubuntu 12.04, "Precise Pangolin") natively. Before doing this, however, you may want to boot OS X just to mute the audio, otherwise you'll be stuck with the Apple "bong" sound when turning the machine on. This sound and its volume level are apparently encoded in the MacBook's firmware, and I'm not aware that it's possible to mute it without doing so from OS X. 

[SIZE="4"]Installation[/SIZE]

If you want to dual-boot your system with Linux and OS X, I have no experience with that, but I've heard that you may need to use an OS X utility called rEFIt to set up your partitions before booting your Linux installer - more details can be found in this [Ubuntu Mactel Installation Guide]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation").

A number of people have reported problems trying to get the default Ubuntu 12.04 install CD or USB installation method to work. Thanks to [this blog post]("http://grigio.org/macbook_air_4_1_2011_ubuntu_linux_12_04_liveusb"), I learned that you can download an alternate Ubuntu 12.04 install ISO that is formatted differently to boot properly on UEFI-based Apple hardware. Additionally, this nightly image includes all of the package updates that have been released for 12.04, saving you time from having to download and install them. Download the **precise-alternate-amd64+mac.iso** file from [here]("http://cdimage.ubuntu.com/precise/daily/current/"), and then simply dd it to a 1 GB or larger USB key. Of course you'll want to dd this to the full disk device name, e.g, /dev/sdb and not /dev/sdb1. 

Now plug that USB key into your MBA and hold down the **Alt** key while powering the computer on. Select the "Windows" disk to boot from and the Ubuntu alternate installer should come up. After selecting my language, I hit **F6** and enabled the **"noapic"** boot option, which I've heard is necessary for stability. From there the install went smoothly - there was one warning about the broadcom wifi driver needing additional firmware, but that was safe for me to ignore, and on the first bootup the open source broadcom wifi driver seemed to work fine. 

[SIZE="4"]Post Install[/SIZE]

At this point you should be able to boot into 12.04 (*TODO: you still need to hold down the Alt key when powering the system on, I need to find out how to make it boot into Ubuntu automatically*). **You should be gentle with the system now, because the applesmc kernel driver that ships with 12.04 does not work properly with the 2012 hardware and your CPU fans will be locked at their lowest speed, 2k RPM.**

Most of the remaining information I gleaned from [this excellent guide]("https://help.ubuntu.com/community/MacBookAir4-2") and [post-install script]("http://pof.eslack.org/archives/files/mba42/post-install-precise.sh") which was written for the 2011 MBA.

I'm copying portions of this script that I was able to run verbatim:

```
# --- macfanctld
# It is highly recommended to use the fan controller daemon that is included in
# the mactel-support ppa called macfanctl. 
echo "Adding macfanctld ppa (fan control daemon)."
sudo add-apt-repository ppa:mactel-support/ppa

# --- lightum
echo "Adding lightum ppa (automatic light sensor daemon)."
sudo add-apt-repository ppa:poliva/lightum-mba

# --- broadcom-sta
echo "Adding broadcom-sta ppa (better wireless module)."
sudo add-apt-repository ppa:poliva/pof

# --- fix 30seconds wifi timeout using wl driver
sudo aptitude purge bcmwl-kernel-source

echo "Installing packages."
sudo aptitude update
sudo aptitude install macfanctld lightum lightum-indicator lm-sensors broadcom-sta-dkms
```

**Critically Important Note:** the mactel-support repo also has an updated applesmc kernel module that works with the 2012 MBA, so install that too and load the module:

```
sudo aptitude install applesmc-dkms
sudo modprobe applesmc
```

Back to that post-install-precise.sh script - you should be able to run these sections verbatim:

```
# The program lmsensors detects the sensors, however it does not know what they
# are yet. The module coretemp will allow lm-sensor to detect the others
# sensors, the rotation speed of the fan, and the GPU temperature.
sudo tee -a /etc/modules <<-EOF
	coretemp
	hid_apple
EOF

# make function keys behave normally and fn+ required for macro
sudo tee -a /etc/modprobe.d/hid_apple.conf <<-EOF
	options hid_apple fnmode=2
EOF
sudo modprobe coretemp hid_apple

# blacklist conflicting wireless module
sudo tee -a /etc/modprobe.d/blacklist-bcma.conf <<-EOF
	blacklist bcma
EOF

# configure macfanctld
tee <<-EOF
	Configuring macfanctld to ignore some sensors. On my system three
	sensors gave bogus readings, i.e.,
	    TH0F: +249.2 C                                    
	    TH0J: +249.0 C                                    
	    TH0O: +249.0 C
	Run 'sensors' to see current values; run 'macfanctld -f' to
	obtain the list of sensors and their associated ID.
	Applying this exclude: 13 14 15.
EOF
sudo service macfanctld stop
sudo cp /etc/macfanctl.conf /etc/macfanctl.conf.$(date +%Y-%m-%d)
sudo sed -i "s/\(^exclude:\).*\$/\\1 13 14 15/" /etc/macfanctl.conf
sudo service macfanctld start
```

At this point I recommend rebooting and ensuring that the system comes back up with the **coretemp**, **hid_apple**, and (most importantly) **applesmc** kernel modules loaded (lsmod will show you your loaded kernel modules). Also make sure that **macfanctld** is running - while on some systems this daemon is optional, I believe it is mandatory for the 2012 MBA.

I also will keep a terminal window open running *watch sensors* to keep an eye on the CPU temperatures and fan speed. The fan speed should start around 2k rpm and go up to 6.2k rpm when the CPUs heat up. If this doesn't happen, you could be damaging your system!

[SIZE="4"]Power Management[/SIZE]

By default, suspend to RAM works, but there are a number of tweaks you can make to reduce power consumption.

Again, from the post-install-precise.sh script:

```
echo "Fixing post-hibernate hang."
sudo tee -a /etc/pm/config.d/macbookair_fix <<-EOF
	# The following brings back eth0 after suspend when using the apple usb-ethernet adapter.
	SUSPEND_MODULES="asix usbnet"
EOF

# no password after resume (like mac)
echo "Disable lock screen after resume."
gsettings set org.gnome.desktop.lockdown disable-lock-screen 'true'


# --- Boot ------------------------------------------------------

echo "Setting boot parm (better power usage)."
sudo cp /etc/default/grub /etc/default/grub.$(date +%Y-%m-%d)
SWAP=$(cat /etc/fstab |grep "# swap was on" |awk '{print $5}')
sudo sed -i "s:\(GRUB_CMDLINE_LINUX_DEFAULT=\).*\$:\\1\"quiet splash i915.i915_enable_rc6=1 resume=${SWAP}\":" /etc/default/grub
sudo update-grub

echo "Ensuring bcm5974 loads before usbhid (editing /etc/rc.local)."
# update /etc/rc.local to ensure bcm5974 is loaded BEFORE usbhid
sudo cp /etc/rc.local /etc/rc.local.$(date +%Y-%m-%d)
sudo sed -i '$i modprobe -r usbhid\nmodprobe -a bcm5974 usbhid' /etc/rc.local

echo "Configuring extra power management options."
wget -Nq http://pof.eslack.org/archives/files/mba42/99_macbookair || wget -Nq http://www.almostsure.com/mba42/99_macbookair
chmod 0755 99_macbookair
sudo mv 99_macbookair /etc/pm/power.d/99_macbookair
# disable bluetooth by default
sudo sed -i '$i /usr/sbin/rfkill block bluetooth' /etc/rc.local
```

[SIZE="4"]Backlit Keyboard and Ambient Light Sensor[/SIZE]

lightum is a background program that controls your keyboard backlight and LCD screen brightness according to the ambient light sensor. It works just fine on my 2012 MBA:

```
# --- enable lightum
/usr/bin/lightum
/usr/bin/lightum-indicator &
gsettings set org.gnome.settings-daemon.plugins.power idle-dim-ac 'false'
gsettings set org.gnome.settings-daemon.plugins.power idle-dim-battery 'false'
```

For more lightum configuration options, check out the [lightum README]("https://github.com/poliva/lightum#readme").

[SIZE="4"]Touchpad[/SIZE]

The default settings the synaptic touchpad comes with in 12.04 were driving me nuts. I discovered I could even hover my finger a millimeter or so over the touchpad and make the mouse move, it was so overly sensitive. I owe a debt of gratitude to the author of [this blog post]("http://uselessuseofcat.com/?p=74") for clearly describing the problematic default settings and how to change them. 

[SIZE="4"]What Doesn't Work[/SIZE]

The Thunderbolt to Ethernet adaptor does not work, you'll want to pick up a USB to Ethernet adaptor instead. 

[SIZE="4"]Other Notes[/SIZE]

The iSight camera works with cheese. I haven't tried it with Skype yet.

I have not tested hibernate or using an external display yet, but I have heard they should work.

I've tried running some of the Ubuntu 3.4 kernels, but haven't seen any noticable improvements from them, and sometimes they have introduced new problems. For example, with kernel 3.4.7, I found that the graphical login screen wouldn't come up after booting, so I'd have to go to a virtual console, login, and *sudo service lightdm restart* to get it to come up.

Enjoy,

Scott

---

### Post by shivathreya on 2012-08-11
Works like charm.

I created BOOT USB and that's it. 

Total installation took 10 mins.

Also I am getting 7 hours battery!!!!

Shiva:)

---

### Post by chippechanga on 2012-08-11
This guide looks great! I'm on a mba 3.1 with ubuntu 12.04 and thinking about upgrading to an mba 5, because my garantie has run out, but also because I hope the hardware will support ubuntu better. Flash, minecraft, and basicly everything that uses my graphic card causes the computer to heat up more than i think it should. How is that on the mba 5?

---

### Post by asting on 2012-09-19
Thank you so much for that post. I have it all up and running on my macbook air. I do have one issue, and I'm not sure what is the cause. The function keys seem to be remapped. I can hit the function key and change the volume, display brightness, etc, however hitting them normally does not do the actual shortcuts. For instance, hitting f11 opens and closes a tab in my browser instead of togging full screen.
Does anyone have any clue on what I can configure to correct this?

EDIT: just reran the above script by copying into gedit and running it through the terminal. all seems well now. I copied it all line by line earlier, so I'm not sure what was different, but it worked.

---

### Post by mlux on 2012-09-26
I have a question about the following text:
> You should be gentle with the system now, because the applesmc kernel  driver that ships with 12.04 does not work properly with the 2012  hardware and your CPU fans will be locked at their lowest speed, 2k RPM.
Should I update to the current packages during installation with Wlan (internet) to the current packages (flag in installation on Ubuntu setup) or should I better wait after loading the fan control module and kernel module (for more fan speed) to start the update manager??
I don't want to destroy hardware during installation/update process.

And a second question: How about 12.10? Is it possible to make a distribution-upgrade from 12.04 to 12.10 when 12.10 is officially released??

---

### Post by sgarman on 2012-09-26
> **mlux said:**
> I have a question about the following text:
Should I update to the current packages during installation with Wlan (internet) to the current packages (flag in installation on Ubuntu setup) or should I better wait after loading the fan control module and kernel module (for more fan speed) to start the update manager??
I don't want to destroy hardware during installation/update process.

And a second question: How about 12.10? Is it possible to make a distribution-upgrade from 12.04 to 12.10 when 12.10 is officially released??

I'd recommend waiting to update your packages until after getting fan control working, just to stay on the safe side.

As for distribution upgrades, I never do them, even on my non-Apple hardware. Been burned too many times, and I maintain a text file of most of my OS customizations so it's a bit more convenient for me to run though those changes at all once after doing a full install from scratch.

Scott

---

### Post by mlux on 2012-09-27
Thank you very much Scott. I will get the hardware next week!
So I try to install 12.04 and wait for a HowTo before installing 12.10.

One other question: 
I purchased an i7 CPU on my MacBook Air 13". Is there any difference for the scripts to an i5 (common - most people have) => e.g., in view of the fan control....

---

### Post by sgarman on 2012-09-27
> **mlux said:**
> I purchased an i7 CPU on my MacBook Air 13". Is there any difference for the scripts to an i5 (common - most people have) => e.g., in view of the fan control....

No difference - I also have an i7 in my MBA.

Scott

---

### Post by mlux on 2012-10-05
edit2: now, all it is working

---

### Post by epikvision on 2012-10-09
Pure excellence. 

This is the standard post for struggling Ubuntu mac users to refer to.  After dealing with a rather clunky Mac, the post helped me improve my system from nothing to beyond miracles, as if everything works straight out of the box!  Thanks for this really useful post!!!  I mean, palm rest works!

It would be great if Canonical can implement these scripts for their next releases.  Is it possible?

---

### Post by mlux on 2012-10-21
Is there a "how-to" planned for the installation process for Ubuntu 12.10 ? This would be very helpful. :)

---

### Post by laurids on 2012-10-26
Hi guys, first thing thank you for sharing, this thread saved me a lot of time (:

I have a 5,2 MBA and everything works fine, **BUT** I'm experiencing tons of kernel panics - I would say one every two hours and then I have to force the machine to shutdown by holding the power button (both keyboard and mouse/trackpad are completely unresponsive)

[LIST]
[*]Kernel: 3.2.0-23-generic #36-Ubuntu SMP
[*]It doesn't look related to any specific program, last time it happend I was working on Emacs only (although I haven't tried to change DE yet)
[*]There are no error messages on /var/log/syslog of any kind
[*]The suspend function works falwlessly
[/LIST]

This behaviour is so frustrating though. Has anyone experienced the same issue? Any ideas about what I could look for?

Thank you!

---

### Post by NickGarvey on 2012-11-02
> **laurids said:**
> Hi guys, first thing thank you for sharing, this thread saved me a lot of time (:

I have a 5,2 MBA and everything works fine, **BUT** I'm experiencing tons of kernel panics - I would say one every two hours and then I have to force the machine to shutdown by holding the power button (both keyboard and mouse/trackpad are completely unresponsive)

[LIST]
[*]Kernel: 3.2.0-23-generic #36-Ubuntu SMP
[*]It doesn't look related to any specific program, last time it happend I was working on Emacs only (although I haven't tried to change DE yet)
[*]There are no error messages on /var/log/syslog of any kind
[*]The suspend function works falwlessly
[/LIST]

This behaviour is so frustrating though. Has anyone experienced the same issue? Any ideas about what I could look for?

Thank you!

Do you have the noapic option enabled in grub when booting?

---

### Post by laurids on 2012-11-02
> **NickGarvey said:**
> Do you have the noapic option enabled in grub when booting?

Thank you for you reply (:

Yep, I have noapic enabled. Those are my grub options though:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic i915.i915_enable_rc6=1 resume="
```

---

### Post by kayp8217 on 2012-11-12
Thank you Scot and everyone else for such a detailed and well written post.

I think this information should be added to the ubuntu wiki/documentation page like the ones below

Installing Ubuntu on Macbook Air 4,2 -- [https://help.ubuntu.com/community/MacBookAir4-2]("https://help.ubuntu.com/community/MacBookAir4-2")

and then it should be linked on to the main Macbook Air page -- [https://help.ubuntu.com/community/MacBookAir]("https://help.ubuntu.com/community/MacBookAir")

- kay

---

### Post by cowai on 2012-11-13
> **laurids said:**
> Thank you for you reply (:

Yep, I have noapic enabled. Those are my grub options though:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic i915.i915_enable_rc6=1 resume="
```

Please report here if you find a fix. This affects me too :/

I'm updating to 12.10 to see if a new kernel helps. I will keep you posted.

---

### Post by psigen on 2012-11-15
> **sgarman said:**
> At this point you should be able to boot into 12.04 (*TODO: you still need to hold down the Alt key when powering the system on, I need to find out how to make it boot into Ubuntu automatically*).

 You can set the default start-up volume by pressing Control-click on an arrow under the volume.

Reference:
[http://hints.macworld.com/article.php?story=20080919150504866](http://hints.macworld.com/article.php?story=20080919150504866)

---

### Post by psigen on 2012-11-17
Also, on my Air, the trackpad stopped moving after resuming from S3 suspend.  This seems to be fixed by adding the touchpad driver to the power management snippet from the setup script:

```
echo "Fixing post-hibernate hang."
sudo tee -a /etc/pm/config.d/macbookair_fix <<-EOF
	# The following brings back eth0 after suspend when using the apple usb-ethernet adapter.
	SUSPEND_MODULES="asix usbnet bcm5974"
EOF
```

---

### Post by N2G(bn#7+ on 2012-11-20
Hi, I am using this as a guide for installing Ubuntu 12.10 on a Macbook Air mid-2012 - thank you, it's amazing!

However, somewhere along the line with the changes to the wireless module it stopped working and I can't get it back again. I've taken the obvious steps to reverse what I did:
[LIST]
[*]Deleted the /etc/modprobe.d/blacklist-bcma.conf file
[*]Uninstalled (purged) the broadcom-sta-dkms package and removed ppa:poliva/pof from my sources.
[*]Used Software Sources to install the propriety bcmwl-kernel-source driver
[/LIST]
...but it still doesn't work. No other way to get on the net with this machine (I don't have ethernet at home) - help please!

EDIT: I gather the problems with the binary driver are basically fixed in 12.10, based on this post: [http://pof.eslack.org/2012/05/23/why-broadcom-80211-linux-sta-driver-sucks-and-how-to-fix-it/](http://pof.eslack.org/2012/05/23/why-broadcom-80211-linux-sta-driver-sucks-and-how-to-fix-it/) so there was no need for me to apply the changes anyway... but I have now, so...

---

### Post by epikvision on 2012-12-01
> **erlandh said:**
> Hi, I am using this as a guide for installing Ubuntu 12.10 on a Macbook Air mid-2012 - thank you, it's amazing!

However, somewhere along the line with the changes to the wireless module it stopped working and I can't get it back again. I've taken the obvious steps to reverse what I did:
[LIST]
[*]Deleted the /etc/modprobe.d/blacklist-bcma.conf file
[*]Uninstalled (purged) the broadcom-sta-dkms package and removed ppa:poliva/pof from my sources.
[*]Used Software Sources to install the propriety bcmwl-kernel-source driver
[/LIST]
...but it still doesn't work. No other way to get on the net with this machine (I don't have ethernet at home) - help please!

EDIT: I gather the problems with the binary driver are basically fixed in 12.10, based on this post: [http://pof.eslack.org/2012/05/23/why-broadcom-80211-linux-sta-driver-sucks-and-how-to-fix-it/](http://pof.eslack.org/2012/05/23/why-broadcom-80211-linux-sta-driver-sucks-and-how-to-fix-it/) so there was no need for me to apply the changes anyway... but I have now, so...
So it's fixed?

---

### Post by DLGandalf on 2012-12-13
other persons experiencing problems with the opensource driver? Doesn't seem to work very well.

Also, are other people experiencing very poor standby time? It's like 15% overnight.

---

### Post by twixta on 2013-01-27
Hi all, any luck with getting an external monitor to work? 

Won't work on my VGA output to a monitor at all.

---

### Post by maestrobwh1 on 2013-04-12
The only think I did not follow in this post is replacing the native wifi driver.  When I used the STA driver, my checking of my overall wifi speed was less than half than it was with the "native" driver.  I reversed that change.  Also, install pommed after adding the extra repos.  My Fn keys would not work without it.

Awesome info here and below where you can run Ubuntu off of the SD card or USB and not touch your internal drive at all.   I would suggest an SD card, no lower than class 10, or use a usb 3.0 flash drive that is capable of 50 MB/s write times.  Patriot makes one that is of decent small size.

[http://michaelevans.org/blog/2013/01/15/boot-ubuntu-from-an-sd-card-on-your-macbook-air/](http://michaelevans.org/blog/2013/01/15/boot-ubuntu-from-an-sd-card-on-your-macbook-air/)

I was helping out with some of the info and especially the resume from suspend read-only issue, so follow the tweak you have to do with fstab in order for resume/suspend to work.  It will resume from suspend without the tweak BUT with a read-only root file system.

If anyone knows a better workaround for the root USB/SD device gets flagged with an inconsistency on suspend whereby on resume, it is marked read-only because of the created inconsistency, that would be grand. Right now, the errors=continue in fstab for the root device  (rather than errors=remount-ro) seems to be a way of ignoring the error, rather than dealing with it.  Keep in mind if you do NOT do this tweak, you will not even be able to do "mount -o remount,rw /" to get the system writable again. It doesn't work and only rebooting lets you do much of anything about it.

Other than that, if one follows this post and the one I linked, you will have a decent working system from an external device.  I would make sure that all vital data is NOT kept on the root device and on another drive or on a separate partition (other devices seem to remount properly) until this issue is truly resolved.  I seem to be working fine with it but obviously, it has not been found whether it issue is just a quirk or if it could leave your file system in a bad state.

The external device is still slow to respond until a few things are used.  I.e. the FN brightness seems to take a few clicks then it finally responds and then responds well.  I think it would be better with one of the newer USB 3.0 faster drives.  Most of the ones that say USB 3.0 are not so stick with a name brand that publishes the write speeds.  My SD is only 20 MB/s

---

### Post by diafygi on 2013-04-19
Howdy all, I'm having an issue with my touchpad being unresponsive on restart or cold boot (12.04 on MBA 5,2). Here's my reproduction steps.

1. Restart computer.
2. At login screen, touchpad is unresponsive. I need to plug in my USB mouse, which works fine.
3. Log in, touchpad still unresponsive.
4. Log out, touchpad is now responsive and works fine on login screen.
5. Log in, touchpad is now responsive and works fine.

What can I do to troubleshoot this? Obviously some driver isn't getting loaded correctly on boot, but then gets re-loaded fine on logout. What log files can I look at to try and track down where this is occurring?

I'd prefer not to have to log out and log in everytime I boot up my computer.

---

