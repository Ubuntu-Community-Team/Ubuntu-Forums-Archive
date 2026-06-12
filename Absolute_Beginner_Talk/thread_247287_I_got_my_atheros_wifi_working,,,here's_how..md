---
title: "I got my atheros wifi working,,,here's how."
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by whiteguysamurai on 2006-08-30
i've seen a few of these on this forum, but most of them are either buried under tons of other posts, or terribly incomplete.

Here's what i did.

(I did this with the DWL-AG530, your atheros wifi might have worked off the bat, but with the old madwifi drivers canonical packed, i doubt it.)

1. after boot, pop that dapper cd back in, you will need it.
   -sudo apt-get install build-essential
   -udo apt-get install linux-headers-`uname -r`
 #these should have been included, but for some reason were not.

2. i hope you have a sneakernet version of madwifi somewhere, the NG version.
 #pop it into an empty folder on your ubuntu desktop, and you might as well extract it..Don't bather with untaring it, let's make this as easy as possible.
   -ifconfig ath0 down (this will disable the screwed up wifi that the ubuntu team gave you)
   -go to your madwifi folder cd (space) then drag the folder into the teminal, so you don't have to write it out, then press enter.
   -cd scripts
   -./madwifi-unload.bash
   -./find-madwifi-modules.sh /lib/modules/
   -cd .. (takes you back to your madwifi folder)
3.Time to set up the wifi device, you need one last step to take out anything that's left..bare with me.
  -make
  -make uninstall (it will do some stuff, then ask you if you want to remove the old module, tell it you do, for good measure, do this twice..Don't ask me why, it just works better this way)
  -make install.
4.Yay it should have worked! you are not ready for the last leg of abusing your neighbors inability to configure wifi. Are you excited?
  -modprobe ath_pci
  -modprobe wlan_scan_sta
  -ifconfig ath0 up (wakes up your newly install wifi device)
  -wlanconfig ath0 list scan (and shows all available wifi connections in your area)

Close the teminal, and go set up your wifi via gnome, your cooking with gas now!

This is the part where i warn you that your state might look down on your possibly snarfing your neighbors internet, i'm not saying you will do this, but don't blame me if you do and someone gets a little more then pissed off if you do.

All the info i gave you can be gotten from other users (i snarfed the first part from IcemanV9) and from the madwifi page.
It might seem like greek to you(unless you're from greece) but if you just paste when i wrote, you will be on the internet in a few minutes. (well, it worked for me)

Now, go get automatix, go install the codecs and flash (if you have no sound in flash, do the following)
(snarfed from calx)
  -sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
  -sudo mkdir -p /tmp/.esd/
  -sudo touch /tmp/.esd/socket

Write back if you find an error!

---

