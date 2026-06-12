---
title: "Macbook Pro 15&quot; Retina (Model 10,1) graphics switching at boot"
date: 2013-05-16
forum: Apple Hardware Users
---

### Post by ksatta1 on 2013-05-16
I now have a working setup to choose nvidia or intel at boot time. Thank you gschwnd for all the work, and all others too.

The main differences in Ubuntu are:
- Couldn't get nvidia to work when efifb is disabled, but when efifb is enabled, nvidia works with just modprobe nvidia. (It should work like in gschwnd's wiki with apple-gmux 0/1 etc, but might be some difference between Ubuntu and Gentoo that I couldn't figure out. Also I tested before updating SMC in OS X, don't know if it changes things).
- So I use two kernels, one with efifb enabled, one with efifb disabled (CONFIG_FB_EFI in kernel's .config).
- With the /etc/init.d/.. method I couldn't get the script to run before X, I found a diff way to do it by editing lightdm.conf.

Versions:
- Kernel 3.8.0-19 (ubuntu default in raring), compiled another copy of it without efifb. Now updating to -21, should work the same. In the normal kernel version terms it is kernel 3.8.8.
- Nvidia driver 310.51 from nvidia.com (couldn't get brightness to work with newer, also kernel must be 3.8.8 for brightness to work (didn't work in 3.9.2 atleast)).

Other notes:
- I have updated the SMC in OS X (don't know if it improves anything, but it doesn't mess up gfx linux).
- I have GfxCardStatus set to "Dynamic" in OS X now.
- I'm running XFCE (Xubuntu), but I think lightdm is default in Ubuntu too? so all scripts etc should work the same.
- Switching GLX between intel/nvidia is really slow now.. Especially when you switch to nvidia. I didn't spend much time to find a better way. Anyway the script does it only when you switch intel/nvidia, not when you just reboot using the same adapter. More notes in the switch_nvidia script.
- You have to suspend/resume after booting. With nvidia it fixes the brightness controls, with intel it stops the screen from flickering occasionally.

**The instructions _(at your own risk)_ (advanced users only)**

Links: gschwnd's wiki for gentoo: [http://www.hzog.net/index.php?title=Linux_on_MacBook_Pro_Retina_15%22_%282012%29](http://www.hzog.net/index.php?title=Linux_on_MacBook_Pro_Retina_15%22_%282012%29)

1. Blacklist modules like in gscwnd's wiki.

2. Edit /etc/init/lightdm.conf (changes in bold):
```

...
emits login-session-start
emits desktop-session-start
emits desktop-shutdown

[B]
pre-start script
  /root/switch_nvidia
end script
[/B]

script
    if [ -n "$UPSTART_EVENTS" ]
    then
        # Check kernel command-line for inhibitors, unless we are being called

...

```

3. New file /root/switch_nvidia, make it executable by root. (For security it's good to set chown root:root too etc..):
**NOTE:** Will delete /etc/X11/xorg.conf when intel is used, so back it up first if needed. More info in the script.
```

#!/bin/bash

# Modified by Kimmo Satta from http://www.hzog.net/index.php?title=Linux_on_MacBook_Pro_Retina_15%22_%282012%29
# Original script license info:
# Copyright 1999-2012 Gentoo Foundation
# Distributed under the terms of the GNU General Public License v2

# uncomment to enable logging
#logfile=/home/user/temp/switchnv.log
#exec >> $logfile 2>&1

# you can change this to install diff ver of nvidia driver
NVIDIA_INSTALLER="/root/NVIDIA-Linux-x86_64-310.51.run"

# this is just used to check which glx is already installed, so it isn't reinstalled on every boot, if not needed..
INSTALLED_GLX_FILE="/root/installed_glx.txt"

# could improve this check if needed.. now "#CONFIG_FB_EFI=y" would be detected wrong..
if grep -q "CONFIG_FB_EFI=y" /boot/config-`uname -r`
then
  # efi fb in use, use nvidia
  echo "NVMODE"
  
  ln -sf /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf

  if [ x`cat $INSTALLED_GLX_FILE` != "xnvidia" ]
  then
    # TODO: very slow (/overkill) for just changing glx, but works..
    # The part that takes longest is probably compiling the dkms kernel module, couldn't find any option to skip that, keeping the old module.
    # Should also be possible by switching some symlinks in /usr/lib/.. glxfoo, but haven't used time to figure it out.
    # Could check how "eselect opengl set..." works in gentoo, or figure out a way to install glx-alternative-nvidia etc packages in Ubuntu
    # (they have been broken in the repos for years apparently).

    # switch to nvidia glx
    sh $NVIDIA_INSTALLER -as
    
    echo "nvidia" > $INSTALLED_GLX_FILE
  fi
  
  # when efi fb is enabled, apple-gmux binary (apple-gmux 0/1 etc) doesn't work, but nvidia seems to be connected to gmux by default, so just modprobe nvidia is enough.
  modprobe nvidia
  
  # I use this little and simple (:D) command to set the current graphic adapter name in the xfce clock.
  # sed -i 's/property name="digital-format" type="string" value=".*"/property name="digital-format" type="string" value="\&lt;span color=\&quot;#FF0000\&quot;\&gt;NVIDIA\&lt;\/span\&gt; %a, %d %b %Y %H:%M"/g' /home/ksatta/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml

  # X didn't start every time, seems to work now with this sleep
  sleep 1
  
else
  # no efi fb, use intel
  echo "INTELMODE"
  
  # you could use the ln if you want, usually no xorg.conf needed for intel..
  # ln -sf /etc/X11/xorg.conf.nouveau /etc/X11/xorg.conf
  rm /etc/X11/xorg.conf
  
  /root/apple-gmux 0
  modprobe i915
  modprobe nouveau
  if [ -e /sys/kernel/debug/vgaswitcheroo/switch ]
  then
    echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
  fi
  
  if [ x`cat $INSTALLED_GLX_FILE` != "xintel" ]
  then
    # TODO: not the best/fastest way to just change glx, but works..
    
    # switch to intel glx
    # might not need all these, haven't tested much. This works anyway.
    apt-get install -y --reinstall --no-download xserver-xorg-core libgl1-mesa-glx libgl1-mesa-dri
    dpkg-reconfigure xserver-xorg      
    
    echo "intel" > $INSTALLED_GLX_FILE
  fi
  
  # I use this little and simple (:D) command to set the current graphic adapter name in the xfce clock.
  #sed -i 's/property name="digital-format" type="string" value=".*"/property name="digital-format" type="string" value="\&lt;span color=\&quot;#00FF00\&quot;\&gt;INTEL\&lt;\/span\&gt; %a, %d %b %Y %H:%M"/g' /home/ksatta/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml

  # X didn't start every time, seems to work now with this sleep
  sleep 1
fi

echo "EXITING.."

exit 0

```

4. /etc/X11/xorg.conf.nvidia: like in gschwnd's wiki (default nvidia xorg.conf with Option "UseDPLib" "no" in device section).

5. Put NVIDIA-Linux-x86_64-310.51.run in /root/ (from nvidia.com) (No need for exec perms, but for security chown root:root etc..).

6. Now when you choose a kernel with efifb in grub, nvidia is used. When you choose a kernel without efifb, intel is used.

---

### Post by MikeBraxner on 2013-05-17
\\:D/ VERY nicely done ... my compliments.

> **ksatta1 said:**
> You have to suspend/resume after booting. ... with intel it stops the screen from flickering occasionally.

Unless I'm mistaken, the 'fluttering screen' after a clean boot with Intel-only is caused by the wireless going active. You might want to try and confirm that, i.e. just boot up, and once the screen starts to dance, switch the wireless off/deactivate it via GUI, whichever you prefer ... should do the trick.

---

### Post by ksatta1 on 2013-05-18
Actually I noticed recently it always starts fluttering when Wifi goes active, I tried now to just disable and enable again wifi, let's see if that fixes it. Then I wouldn't have to go to standby always after booting :)

EDIT: it was still fluttering I think, less though. Anyway back to standby/resume after boot :)

---

### Post by ksatta1 on 2013-05-25
X still doesn't start always (happens very rarely). I'm now testing sleep 2 in the script.

Also, each time the glx packages are updated in the repo the apt-get foo doesn't work with --no-download. Really have to find a better way to switch glx, one day :)

---

