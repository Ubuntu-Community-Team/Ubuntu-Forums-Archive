---
title: "Ubuntu on mac No Network adapters"
date: 2012-02-14
forum: Apple Hardware Users
---

### Post by jessepage1989 on 2012-02-14
I have a macbook pro 13in from 2010. I installed ubuntu 10.04 on it and all went well except the fact that it says no network adapters present. I've played around with linux a little bit but I am still very new to this. How can I get the drivers needed to see my network hardware and how do I go about installing them. Playing with computers is fun except when the network adapter driver doesn't work -_- lol.

---

### Post by jessepage1989 on 2012-02-14
i hope someone can help me out I don't want this to end like my last post...  [http://ubuntuforums.org/showthread.php?t=834258](http://ubuntuforums.org/showthread.php?t=834258)   lol

---

### Post by varunendra on 2012-02-15
You shouldn't make multiple posts before 24 hours without getting any replies. It is harmful to your thread because it makes it look (in a general search) as if is getting help while actually it is not.

Having said that, I shouldn't have posted as well if I couldn't help. But I think I sometimes get lucky with networking issues :) (at least this one wouldn't go unanswered like the one you linked to ;))

Let us first see if Ubuntu actually detected any adapters or not. Please run the following commands in terminal and post back the outputs:
```
sudo lshw -C network
```

If it doesn't give any outputs, then-
```
lspci -nn
dmesg | grep -i net
```

While posting the outputs, please put them in 'Code' box like above ones by adding [noparse]```
..and..
```[/noparse] tags respectively at the beginning and end of the outputs (you can click on # at the top of edit box to auto generate them, then copy-paste the outputs in-between the generated tags).

Also, have you done these basic checks?-

[LIST]
[*]If there is a physical switch, make sure it is turned 'On'
[*]the adapter is NOT DISABLED in BIOS
[*]Is the adapter working on the mac OS part?
[/LIST]
I'm not familiar with macs, but I think these basic steps are same for any computer system.

---

### Post by jessepage1989 on 2012-02-17
the outputs are
```
  *-network UNCLAIMED      
       description: Ethernet controller 
       product: NetXtreme BCM57765 Gigabit Ethernet PCIe 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       version: 10 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi msix pciexpress bus_master cap_list 
       configuration: latency=0 
       resources: memory:a0400000-a040ffff(prefetchable) memory:a0410000-a041ffff(prefetchable) 
  *-network UNCLAIMED 
       description: Network controller 
       product: Broadcom Corporation 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       version: 02 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: latency=0 
       resources: memory:a0600000-a0603fff 

```

---

### Post by josephmills on 2012-02-17
how about a ```
lspci -nn | grep 14e4 
``` 


thanks

---

### Post by jessepage1989 on 2012-02-17
i get this

```
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4] (rev 10) 
02:00.1 SD Host controller [0805]: Broadcom Corporation Device [14e4:16bc] (rev 10) 
03:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4331] (rev 02) 

```

---

### Post by josephmills on 2012-02-17
last question ```
uname -a 
```

---

### Post by jessepage1989 on 2012-02-17
```
Linux jesse-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux 
```

---

### Post by varunendra on 2012-02-17
> **jessepage1989 said:**
> ```
Linux jesse-laptop [COLOR=Red]**2.6.32-33-generic**[/COLOR] #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux 
```
As per [this page]("http://linuxwireless.org/en/users/Drivers/b43#Supported_devices"), it looks like you either need to install a backported kernel/module, or would have to resort to ndiswrapper to try windows driver. But I'd wait for an input from *josephmills*, as he seems to have better experience about this.

---

### Post by josephmills on 2012-02-18
yes varunendra is correct if you look at that page you will see that you have to use the 3.2 + kernel in order for this thing to work with the b43 or you can do as he says and go after ndiswrapper. Its up to you. what would you like to do ?  I think that 12.04 has the 3.2 kernel in it. any ho let us know if you would like to upgrade your kernel or if you would like to try ndiswrapper. 
Joseph

---

### Post by jessepage1989 on 2012-02-18
i think i will upgrade my kernel then.

---

### Post by josephmills on 2012-02-18
> **jessepage1989 said:**
> i think i will upgrade my kernel then.

ok then open terminal 
```
cd ~/Downloads 
```
then 
```
mkdir kernel 
```
then download these three  files 

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc4-oneiric/linux-headers-3.2.0-030200rc4-generic_3.2.0-030200rc4.201112012035_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc4-oneiric/linux-headers-3.2.0-030200rc4-generic_3.2.0-030200rc4.201112012035_i386.deb)


[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc4-oneiric/linux-headers-3.2.0-030200rc4_3.2.0-030200rc4.201112012035_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc4-oneiric/linux-headers-3.2.0-030200rc4_3.2.0-030200rc4.201112012035_all.deb)



[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc4-oneiric/linux-image-3.2.0-030200rc4-generic_3.2.0-030200rc4.201112012035_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc4-oneiric/linux-image-3.2.0-030200rc4-generic_3.2.0-030200rc4.201112012035_i386.deb)




back to terminal 

```
cd ~/Downloads 
```

copy the three files into the dir that you made 
```
cp linux-* ~/Downloads/kernel/
```
then cd in kernel 

```
cd ~/Downloads/kernel/
```

now do a 
```
ls 
``` 

Do you see the 3 files in there ? this is important all 3 have to be in there. after you see that they are in there time to build 

```
sudo dpkg -i *.deb
```


then 
```
sudo update-grub
``` 

then 

```
sudo reboot 
``` 


Now boot into your 3.2 r4 kernel 

then open terminal 

```
sudo apt-get install bcmwl-kernel-source b43-fwcutter firmware-b43-installer 
``` 


then 

```
sudo reboot 
```

boot into 3,2 r4 

ddo you have wireless ?

---

### Post by jessepage1989 on 2012-02-18
no wireless but i have Ethernet. running updates now

---

### Post by josephmills on 2012-02-18
> **jessepage1989 said:**
> no wireless but i have Ethernet. running updates now

umm.. could we see a ```
dmesg | grep b43 
```
after update and upgrade thanks also a ```
rfkill list all && lsmod 
``` thanks

---

### Post by jessepage1989 on 2012-02-18
```
jesse@jesse-laptop:~$ dmesg | grep b43
[   13.290011] b43-phy0: Broadcom 4331 WLAN found (core revision 29)
[   13.290468] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 9, Type 7, Revision 1)
[   13.290505] b43: probe of bcma0:0 failed with error -95
jesse@jesse-laptop:~$ rfkill list all && lsmod
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17266  1 
fat                    55347  1 vfat
binfmt_misc            17258  1 
ppdev                  12900  0 
rfcomm                 37611  4 
bridge                 79297  0 
stp                    12811  1 bridge
bnep                   17749  2 
snd_hda_codec_hdmi     31547  1 
snd_hda_codec_cirrus    23281  1 
snd_hda_intel          32396  2 
snd_hda_codec          99529  3 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                76379  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
b43                   323010  0 
snd_seq_midi           13132  0 
mac80211              425736  1 b43
snd_rawmidi            25103  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              169184  2 b43,mac80211
snd_seq                51256  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24609  2 snd_pcm,snd_seq
mei                    36087  0 
joydev                 17313  0 
lp                     13349  0 
parport                36664  2 ppdev,lp
i915                  403227  2 
bcm5974                17223  0 
ssb                    46176  1 b43
drm_kms_helper         36749  1 i915
drm                   197071  2 i915,drm_kms_helper
sdhci_pci              18264  0 
applesmc               18920  0 
sdhci                  27687  1 sdhci_pci
bcma                   25387  1 b43
btusb                  17979  2 
snd_seq_device         14130  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13152  1 i915
snd                    55724  14 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
input_polldev          13648  1 applesmc
soundcore              12600  1 snd
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
apple_bl               13049  0 
bluetooth             153156  23 rfcomm,bnep,btusb
uvcvideo               66495  0 
videodev               86260  1 uvcvideo
video                  18792  1 i915
hid_apple              13082  0 
usb_storage            43811  1 
uas                    17587  0 
usbhid                 45614  0 
hid                    81147  2 hid_apple,usbhid
tg3                   140230  0 
jesse@jesse-laptop:~$ 

```

---

### Post by kaldor on 2012-02-18
Just a side note here, though I'm not extremely familiar with wireless (never had issues before).

I assume you're using Ubuntu 10.04.4 which came out a few days ago. This version has backported wireless drivers from Linux 3.x, so if your wireless isn't working right now then I doubt installing a new kernel would help much. Just thought I'd provide that bit of info just in case.

---

### Post by josephmills on 2012-02-18
> **jessepage1989 said:**
> ```
jesse@jesse-laptop:~$ dmesg | grep b43
[   13.290011] b43-phy0: Broadcom 4331 WLAN found (core revision 29)
[   13.290468] b43-phy0[COLOR="DarkRed"] ERROR: FOUND UNSUPPORTED PHY (Analog 9, Type 7, Revision 1)[/COLOR]
[   13.290505] [COLOR="DarkRed"]b43: probe of bcma0:0 failed with error -95[/COLOR]
jesse@jesse-laptop:~$ rfkill list all && lsmod
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
Module                  Size  Used by
[COLOR="Red"]
b43                   323010  0 

mac80211              425736  1 b43

cfg80211              169184  2 b43,mac80211

ssb                    46176  1 b43

bcma                   25387  1 b43[/COLOR]

jesse@jesse-laptop:~$ 

```



ummm. try this I dont get the error to do with PHY. I will also google. 
b43: probe of bcma0:0 failed with error -95 

```
sudo rmmod b43
```
then 
```
sudo modprobe b43
```

if not 
```
sudo rmmod b43
```
then reboot 
then 
```
sudo modprobe b43
```

---

### Post by jessepage1989 on 2012-02-18
same thing 

i get the same readout when i enter 

```
dmesg | grep b43
```

---

### Post by josephmills on 2012-02-18
> **jessepage1989 said:**
> same thing 

i get the same readout when i enter 

```
dmesg | grep b43
```


arghh 
alight I wrote a script called lastchance if this wont work then I am out of ideas  :)
open terminal
```
gedit ~/lastchance
``` 
then paste this into your text editor (gedit)
```

#!/usr/bin/env bash 
##
##   This script will install the b43 modual to you computer 
##   This is only for Kernels that are 3.2 and up 
############################################################
#
#Making Varibles 
clear 
kern=$(uname -r)
cb43=$(lsmod | grep b43);
cwl$=(lsmod | grep wl );
cbrcm80211=$(lsmod | grep brcm80211);
if $cb43;
 then
   sudo rmmod b43 && sudo apt-get remove --purge --assume-yes b43-fwcutter bcmwl-kernal-source firmware-b43-installer; 
 elif $cwl;  
 then
   sudo rmmod wl && sudo apt-get remove --purge --assume-yes  broadcom-sta-source broadcom-sta-common firmware-b43-installer;
 elif  $cbrcm80211;
 then 
 sudo modprobe brcm80211;
 else           
   echo "Cool"
 fi
clear
echo "Installing Dependency\'s "
sudo apt-get install --assume-yes linux-headers-$kern 
sudo apt-get install --assume-yes gcc 
sudo apt-get install --assume-yes make 
sudo apt-get install --assume-yes linux-libc-dev
sudo apt-get install --assume-yes notify-send
cd /home/$USER/
mkdir -p sandbox 
cd sandbox 
wget http://bu3sch.de/b43/fwcutter/b43-fwcutter-015.tar.bz2
tar xjf b43-fwcutter-015.tar.bz2
cd b43-fwcutter-015
make
sudo make install
cd ..
export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2
tar xjf broadcom-wl-5.100.138.tar.bz2
sudo b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" broadcom-wl-5.100.138/linux/wl_apsta.o
cd ..
sudo rm -r sandbox
clear
notify-send "Your Install Is Done Please Reboot"

```


then save and go back to the termianl 
```
cd ~/
```
then 
```
chmod +x lastchance
```
then 
```
./lastchance
```

then reboot 

if this does not work then I have no clue and everythign that I read here [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) is wrong (which I know that that is not the case)

any ho good luck

---

### Post by jessepage1989 on 2013-01-26
Thanks for the help guys. I never got 10.04 up and running on my mac successfully with wifi adaptors. However I did give 12.04lts a try a few days ago and I am pleased to say that everything works fine. Didn't mean to give this a bump but i thought I thought i would share for future searchers what I have found and that is 12.04 works perfect with 2010 MBPs

---

