---
title: "[SOLVED] [Installation] MacBook madwifi problem"
date: 2007-09-20
forum: Apple Intel Users
---

### Post by PuckstopperGA on 2007-09-20
Hi,

I'm new to Ubuntu & Linux, but have extensive Windows experience. I installed Ubuntu on my macbook, but I'm having some trouble getting madwifi to install and work.
I followed the guide located here: [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
After madwifi is downloaded and I try to install it, I run into problems. Following the instructions, I typed "make install" but it came up with the following error:
```
WARNING:
It seems that there are modules left from previous MadWifi installations.
If you are unistalling the MadWifi modules please press "r" to remove them.
If you are installing new MadWifi modules, you should consider removing those
already installed, or else you may experience problems during operation.
Remove old modules?

[l]ist, [r]emove, [i]gnore or e[x]it (l,r,i,[x]) ? 
r
for i in ./ath ./ath_hal ./ath_rate ./net80211; do \
                make -C $i install || exit 1; \
        done
make[1]: Entering directory `/home/jfisher/drivers/madwifi-0.9.3.2/ath'
test -d //lib/modules/2.6.20-16-generic/net || mkdir -p //lib/modules/2.6.20-16-generic/net
install ath_pci.ko //lib/modules/2.6.20-16-generic/net
install: cannot stat `ath_pci.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/jfisher/drivers/madwifi-0.9.3.2/ath'
make: *** [install-modules] Error 1

```Does anyone have any ideas on how to move forward here? I apologize in advance if it has already been posted, but I've been searching through these (and other) forums for several hours and cannot seem to pull up the solution.

Thanks so much!!

---

### Post by cyberdork33 on 2007-09-20
Did you "make" before you "sudo make install" ? The error sounds like it cannot copy the module to the correct location because the modules doesn't exist yet.

---

### Post by PuckstopperGA on 2007-09-20
Wow thanks for the super-fast reply! 

I did before, but I figured I'd give it another shot, but this time as root. It seems to install correctly now (no error messages). But according to the MacBook setup guide, it should work now after a reboot. I tried, but to no avail. So I pulled up the Madwifi how to ([http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)). I got down to this step:
[INDENT]To load the driver module, type:

modprobe ath_pci
[/INDENT]I get no error message after this - it just takes me right back to a command line input (I don't know if this is bad or not). So I then continued ahead in the guide to this step:
[INDENT]Creating an Interface ¶

MADWiFi supports virtual access points, which means you can create more than one wireless device per wireless card. By default, a sta mode VAP is created, which is MadWifi talk for a 'managed mode wireless interface'.

If your svn snapshot is more recent than the 23rd January 2006, (r1407) than you can skip the following step:

If not, then follow these instructions to make a normal station mode interface. Type (as root):

wlanconfig ath0 create wlandev wifi0 wlanmode sta
[/INDENT]I tried run that command, but it gave me an error ```
wlanconfig: ioctl: No such device
```Iwconfig shows "lo" and "eth0" only. So I may be on the completely wrong track here - I'm not sure about the 'svn snapshot' date. Any ideas?

Thanks much!

---

### Post by cyberdork33 on 2007-09-20
Since a version of the module is included with the Ubuntu restricted modules package, you need to make sure you block the original module from loading to allow your custom module to load instead:
[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

If that doesn't help matters, you might try different versions of the source, it seems 2695 is working for most people.
[http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2695-20070829.tar.gz](http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2695-20070829.tar.gz)

---

### Post by PuckstopperGA on 2007-09-20
That took care of it! Thank you so much for your help!

---

### Post by cyberdork33 on 2007-09-20
> **PuckstopperGA said:**
> That took care of it! Thank you so much for your help!
Please mark as solved

---

