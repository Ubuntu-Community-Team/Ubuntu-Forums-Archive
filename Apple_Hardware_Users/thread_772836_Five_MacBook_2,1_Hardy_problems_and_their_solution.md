---
title: "Five MacBook 2,1 Hardy problems and their solutions"
date: 2008-04-28
forum: Apple Hardware Users
---

### Post by bluefish86 on 2008-04-28
I've finally got my hardy installation working the way I want it, so I figured I'd share what I had to do to get it to this point.  Note that these solutions are for a MacBook 2,1.  They may or may not apply to other MacBook revisions.  Run this command to see what revision you have:
```
sudo dmidecode -s system-product-name
```

Hopefully this information helps.

**Hardy refused to boot after installation**
I had to reinstall, this time changing the bootloader settings.  On the final confirmation screen of the installer before it begins its work, click on the "Advanced..." button.  Change *(hd0)* to *(hd0,**i**)* where i is the partition number of your Ubuntu install minus one.  For example, I installed Ubuntu on sda4, so I had to change it to *(hd0,3)*.

After the installation completes and your computer reboots to the rEFIt menu, use the keyboard to select and run the Partitioning Tool (if you don't already have rEFIt installed, find it [here]("http://refit.sourceforge.net") and install it from Mac OS X).  It should tell you it needs to do work to repair the damage the installer did and ask you for confirmation.  Hit y to let it do its stuff.  When it brings you back to the menu, choose Shutdown.

Next time you start your computer and choose Linux, hardy should boot fine.

**The sound is really quiet**
Run this command to open the mixer:
```
gnome-volume-control
```
Go to preferences and make sure that "Front" and "Surround" are enabled.  Close preferences and check that the "Front" and "Surround" sliders are all the way up and that mute (the little speaker under the sliders) isn't set.  Close the mixer.  You should now have full control over the volume with the keyboard keys and the panel volume applet.

**After I leave my computer inactive for a while, the screen goes black but the backlight stays on**
For some reason, the default in hardy is that the screensaver is set to black the screen after 10 minutes but the power manager is set to never turn it off.  Just change the settings in System->Preferences->Screensaver and System->Preferences->Power Management to something more logical.

**Wireless doesn't work**
Run the following commands to install working drivers:
```
sudo apt-get install build-essential autoconf automake
wget http://snapshots.madwifi.org/madwifi-trunk/madwifi-ng-r3358-20080215.tar.gz
tar -zxvf madwifi-ng-r3358-20080215.tar.gz
cd madwifi-ng-r3358-20080215
make
sudo make install
echo -e '#!/bin/sh\n/sbin/iwpriv ath0 bgscan 0' | sudo tee -a /etc/acpi/resume.d/99-madwifi-bgscan.sh
sudo chmod 755 /etc/acpi/resume.d/99-madwifi-bgscan.sh
sudo depmod -ae
sudo modprobe -r ath_pci
sudo modprobe ath_pci
```

If everything went well, running the command *iwconfig* should output something like this:
```
chris@chris-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:99153  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

chris@chris-laptop:~$ 

```
Network manager should also now work.  You can safely delete the madwifi archive and folder that these commands put in your home folder.

**Dual head doesn't work like the hardy page says it should**
See my replies in another thread [here]("http://ubuntuforums.org/showthread.php?t=768761").

The built-in command bound to the display key (F7) doesn't work very well.  You can bind the script I posted in the other thread instead by running these commands:

```
gconftool-2 --unset /apps/gnome_settings_daemon/keybindings/xrandr
gconftool-2 --type string --set /apps/metacity/global_keybindings/run_command_8 "XF86Display"
gconftool-2 --type string --set /apps/metacity/keybinding_commands/command_8 "vga"

```

---

### Post by cyberdork33 on 2008-04-28
> **bluefish86 said:**
> I've finally got my hardy installation working the way I want it, so I figured I'd share what I had to do to get it to this point.  Note that these solutions are for a MacBook 2,1.
Please add information to the wiki page:
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

---

### Post by buschi on 2008-04-30
hi! thanks a lot for the description! i have only one question... did you install the 64bit version?

---

### Post by cyberdork33 on 2008-04-30
> **buschi said:**
> hi! thanks a lot for the description! i have only one question... did you install the 64bit version?
it shouldn't make a difference

---

### Post by robsk3 on 2008-06-17
> **bluefish86 said:**
> 
**Wireless doesn't work**
Run the following commands to install working drivers:

Hi Bluefish! I tried this wireless handling but this was all I saw afterwards and no mention of the wireless that you are seeing. 
___________________________________
root@bubuntu:/# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@bubuntu:/# 
___________________________________

Maybe I did something wrong? I'm very very new to Linux!

This was the response it gave me here... and it didn't seem right.

___________________________________
root@bubuntu:/home/rob/madwifi-ng-r3358-20080215# echo -e '#!/bin/sh\n/sbin/iwpriv ath0 bgscan 0' | sudo tee -a /etc/acpi/resume.d/99-madwifi-bgscan.sh
#!/bin/sh
/sbin/iwpriv ath0 bgscan 0
___________________________________

After that each line just went in and the next command line came up, so I don't know whether it stopped having an effect there or not.

Any idea's on how to work this?

Thanks!!!
Rob

---

### Post by cyberdork33 on 2008-06-17
> **robsk3 said:**
> After that each line just went in and the next command line came up, so I don't know whether it stopped having an effect there or not.

Any idea's on how to work this?
You didn't seem to mention the last few commands which are the ones that actually load the driver:
```
sudo depmod -ae
sudo modprobe -r ath_pci
sudo modprobe ath_pci
```

---

