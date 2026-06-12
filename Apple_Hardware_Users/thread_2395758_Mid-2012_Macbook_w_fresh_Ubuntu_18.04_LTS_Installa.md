---
title: "Mid-2012 Macbook w/ fresh Ubuntu 18.04 LTS Installation - no WiFi"
date: 2018-07-06
forum: Apple Hardware Users
---

### Post by neurotakuko on 2018-07-06
Hi there,

Under Settings --> Wi-Fi shows a message: "No Wi-Fi Adapter Found / Make sure you have a Wi-Fi adapater pugged in and turned on"

I don't have a wired connection available (no ethernet port adapter).

I followed instructions listed [here]("https://ubuntuforums.org/showthread.php?t=2082305&p=12350385&viewfull=1#post12350385") for running the wireless info script and the output is here: [https://pastebin.ubuntu.com/p/xDFcXQtr6G/](https://pastebin.ubuntu.com/p/xDFcXQtr6G/).

Thanks in advance for any advice. I tried searching for drivers to download and transfer but couldn't find the right information.

:KS

---

### Post by chili555 on 2018-07-06
Your device requires firmware. Hadaka's excellent post #2 here describes the off-line process:  [https://ubuntuforums.org/showthread.php?t=2316899&highlight=b43.zip](https://ubuntuforums.org/showthread.php?t=2316899&highlight=b43.zip)

Post back if you get stuck or need additional assistance.

---

### Post by neurotakuko on 2018-07-06
Hi chili555,

I followed Hadaka's steps and I see the b43 files correctly copied to /lib/firmware/b43. I entered the modprobe command and restarted a couple of times but I am still seeing the same message of 'No Wi-Fi Adapter Found'.

Thank you for your help.

---

### Post by chili555 on 2018-07-06
Let's see if there are any interesting messages that we can find. Open a terminal and run;```
rfkill list all
```Any hard blocked:yes?

Also:```
dmesg | grep b43
```Anything jump out at you? Anything about firmware??

How are the permissions in the file?```
sudo ls -al /lib/firmware/b43
```We hope you see:```
drwxr-x---  2 root root  4096 Jul  6 19:05 .
drwxr-xr-x 84 root root 36864 Jul  6 19:05 ..
[COLOR="#FF0000"]-rw-r--r-[/COLOR]-  1 root root   178 Jul  6 19:05 a0g0bsinitvals5.fw
[COLOR="#FF0000"]-rw-r--r-- [/COLOR] 1 root root   178 Jul  6 19:05 a0g0bsinitvals9.fw
[COLOR="#FF0000"]-rw-r--r--[/COLOR]  1 root root  1836 Jul  6 19:05 a0g0initvals5.fw
[COLOR="#FF0000"]-rw-r--r--[/COLOR]  1 root root  1992 Jul  6 19:05 a0g0initvals9.fw
etc.
```You don't have to copy and paste the whole thing; just tell us if the permissions are -rw-r--r-- for all the files.

---

### Post by jeremy31 on 2018-07-07
Moved to Apple Hardware

---

### Post by nofrills2 on 2018-07-08
Hi Chilli555,

I'm a new Ubuntu user experiencing the same wifi problems trying to install 18.04 LTS on a mcbook pro early 2011. Wireless card is a Broadcom 4331. I've tried following the instructions provided above but am having the exact same issues as neurotakuko. My terminal output is below:
```

phill@phill-MacBookPro:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
phill@phill-MacBookPro:~$ dmesg | grep b43
[   21.047141] b43-phy0: Broadcom 4331 WLAN found (core revision 29)
[   21.047547] b43-phy0: Found PHY: Analog 9, Type 7 (HT), Revision 1
[   21.047558] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2059, Revision 0, Version 1
[   21.047560] b43-phy0 warning: 5 GHz band is unsupported on this PHY
[   21.129283] b43 bcma0:1: Direct firmware load for b43/ucode29_mimo.fw failed with error -2
[   21.129305] b43 bcma0:1: Direct firmware load for b43/ucode29_mimo.fw failed with error -2
[   21.129326] b43 bcma0:1: Direct firmware load for b43-open/ucode29_mimo.fw failed with error -2
[   21.129338] b43 bcma0:1: Direct firmware load for b43-open/ucode29_mimo.fw failed with error -2
[   21.129341] b43-phy0 ERROR: Firmware file "b43/ucode29_mimo.fw" not found
[   21.129344] b43-phy0 ERROR: Firmware file "b43-open/ucode29_mimo.fw" not found
[   21.129347] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
phill@phill-MacBookPro:~$ sudo ls -al /lib/firmware/b43
[sudo] password for phill: 
total 300
drwxr-xr-x  2 root root  4096 Jul  8 22:40 .
drwxr-xr-x 82 root root 12288 Jul  8 22:39 ..
-rw-r--r--  1 root root   158 Jul  8 22:40 a0g0bsinitvals5.fw
-rw-r--r--  1 root root   158 Jul  8 22:40 a0g0bsinitvals9.fw
-rw-r--r--  1 root root  1840 Jul  8 22:40 a0g0initvals5.fw
-rw-r--r--  1 root root  2002 Jul  8 22:40 a0g0initvals9.fw
-rw-r--r--  1 root root   158 Jul  8 22:40 a0g1bsinitvals13.fw
-rw-r--r--  1 root root   158 Jul  8 22:40 a0g1bsinitvals5.fw
-rw-r--r--  1 root root   158 Jul  8 22:40 a0g1bsinitvals9.fw
-rw-r--r--  1 root root  2080 Jul  8 22:40 a0g1initvals13.fw
-rw-r--r--  1 root root  1840 Jul  8 22:40 a0g1initvals5.fw
-rw-r--r--  1 root root  2002 Jul  8 22:40 a0g1initvals9.fw
-rw-r--r--  1 root root   158 Jul  8 22:40 b0g0bsinitvals13.fw
-rw-r--r--  1 root root   158 Jul  8 22:40 b0g0bsinitvals5.fw
-rw-r--r--  1 root root   158 Jul  8 22:40 b0g0bsinitvals9.fw
-rw-r--r--  1 root root  2080 Jul  8 22:40 b0g0initvals13.fw
-rw-r--r--  1 root root  1840 Jul  8 22:40 b0g0initvals5.fw
-rw-r--r--  1 root root  2002 Jul  8 22:40 b0g0initvals9.fw
-rw-r--r--  1 root root   158 Jul  8 22:40 lp0bsinitvals13.fw
-rw-r--r--  1 root root   158 Jul  8 22:40 lp0bsinitvals14.fw
-rw-r--r--  1 root root   158 Jul  8 22:40 lp0bsinitvals15.fw
-rw-r--r--  1 root root  3618 Jul  8 22:40 lp0initvals13.fw
-rw-r--r--  1 root root  2064 Jul  8 22:40 lp0initvals14.fw
-rw-r--r--  1 root root  2052 Jul  8 22:40 lp0initvals15.fw
-rw-r--r--  1 root root   158 Jul  8 22:40 n0absinitvals11.fw
-rw-r--r--  1 root root   158 Jul  8 22:40 n0bsinitvals11.fw
-rw-r--r--  1 root root  2100 Jul  8 22:40 n0initvals11.fw
-rw-r--r--  1 root root  1320 Jul  8 22:40 pcm5.fw
-rw-r--r--  1 root root 29864 Jul  8 22:40 ucode11.fw
-rw-r--r--  1 root root 32232 Jul  8 22:40 ucode13.fw
-rw-r--r--  1 root root 31384 Jul  8 22:40 ucode14.fw
-rw-r--r--  1 root root 30488 Jul  8 22:40 ucode15.fw
-rw-r--r--  1 root root 22384 Jul  8 22:40 ucode5.fw
-rw-r--r--  1 root root 25160 Jul  8 22:40 ucode9.fw
phill@phill-MacBookPro:~$ 
```

I'll keep following this thread, I would appreciate any help you could provide.
Cheers, Phill.

---

### Post by neurotakuko on 2018-07-09
Hi chili555,

For 'rfkill list all' I only see Bluetooth comeup which shows 'Soft blocked: yes'.

The output of 'dmesg | grep b43' is identical to what **nofrills2 **posted above.

Finally, the permissions in the file are all -rw-r--r--.

Thanks for your continued help.

---

### Post by chili555 on 2018-07-09
Both of you, let's try more advanced methods, known here in the woods of South Carolina as a bigger hammer!

Please download this package on some other computer and transfer it on a USB key or similar. Drag and drop it to the desktop of the Ubuntu computer. Install it from the terminal with:```
cd ~/Desktop
sudo dpkg -i linux-firmware*.deb
```Reboot.

[http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.173_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.173_all.deb)

---

### Post by nofrills2 on 2018-07-10
Hi Chili555,

Ok, I've downloaded, run and installed the linux firmware package and rebooted. Still no sign of the wi-fi card :)

A critical detail I forgot to mention is that I am connected via ethernet, just no wifi. Apologies for failing to mention before.

Thanks for your help, Phill.

---

### Post by chili555 on 2018-07-10
May I please see:```
dmesg | grep b43
rfkill list all
```Thanks.

---

### Post by nofrills2 on 2018-07-13
Hi Chilli555

Thanks for the reply.

The output is:
```
phill@phill-MacBookPro:~$ dmesg | grep b43
[   10.618890] b43-phy0: Broadcom 4331 WLAN found (core revision 29)
[   10.619300] b43-phy0: Found PHY: Analog 9, Type 7 (HT), Revision 1
[   10.619311] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2059, Revision 0, Version 1
[   10.619312] b43-phy0 warning: 5 GHz band is unsupported on this PHY
[   10.619783] b43 bcma0:1: Direct firmware load for b43/ucode29_mimo.fw failed with error -2
[   10.619793] b43 bcma0:1: Direct firmware load for b43/ucode29_mimo.fw failed with error -2
[   10.619804] b43 bcma0:1: Direct firmware load for b43-open/ucode29_mimo.fw failed with error -2
[   10.619811] b43 bcma0:1: Direct firmware load for b43-open/ucode29_mimo.fw failed with error -2
[   10.619812] b43-phy0 ERROR: Firmware file "b43/ucode29_mimo.fw" not found
[   10.619815] b43-phy0 ERROR: Firmware file "b43-open/ucode29_mimo.fw" not found
[   10.619817] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
```

Cheers

---

### Post by chili555 on 2018-07-13
Please open a terminal and do:```
sudo -i
cd /lib/firmware/b43
wget https://github.com/LibreELEC/wlan-firmware/raw/master/firmware/b43/ucode29_mimo.fw
exit
```Reboot.

---

### Post by kevin160 on 2018-07-14
As I mentioned in the other thread, the b43 driver won't let your 4331 chip do 5GHz.  If you install the bcmwl driver via

sudo apt install bcmwl-kernel-source

and reboot, the b43 driver will automatically be blacklisted, and you should have access to 5GHz.  

Unfortunately, I just tried that on my 2012 mini, and the install crashed.   I had to reboot and try again.  Hopefully that won't happen to you.  Works fine for me under 18.04 after the second install and second reboot.

---

### Post by nofrills2 on 2018-07-15
Hi Kevin160,

Success! Installing the bcmwl-kernel-source worked! Thanks for your help! :P
Technically, what was causing the problem? I just want to gain a better understanding of how Ubuntu operates with the hardware.

Chilli555 - I really appreciate the help and effort. I can't wait to gain a more advanced understanding of Ubuntu and Linux in general so that I too can assist people where needed.

All the best, Phill.

---

### Post by planetphoebe on 2018-07-26
Hi Dr. Chilli I have been dealing with an Ubuntu 'install' Wifi issue that revolves around firmware, b43 & my Broadcom 43123 not showing up when I rfkill list.

I understand this may not be the right place to post about my issue, but YOU keep popping up everywhere I go on ubuntuforums in regards to the issues, so i am getting in where I proverbially fit in. 

This is my issue: I f'd up my Ubuntu 16.04 so I backed everything and reinstalled from the thumb I keep ready. First thing I do is run Updater, cause I know it comes in barebones, but it has a bug. Maybe specific to my hardware interfacing with the extension, but still it flags it, makes me acknowledge/report then finishes the update. After which I reboot.

And when I come back my issue has begun. 

I already tried this:

sudo apt-get purge bcmwl-kernel-source

After placing .deb files in “Home”:

sudo dpkg -i b43-fwcutter_019-2_amd64.deb
tar xfvj broadcom-wl-5.100.138.tar.bz2
sudo b43-fwcutter -w /lib/firmware broadcom-wl-5.100.138/linux/wl_apsta.o

And that doesn't do it.

Here's some more output from terminal from when I get to that stage in the process (Have done this 7 times now at least. I'm not very savvy in terminal. I have only used Ubuntu 4 years and am still; n00b AF. I don't code, I use Libre & GIMP and that's about it.)

dmesg | grep b43 – NO RESULT

irmware/b43

ls /lib/firmware/b43
::
phoebe@afx34:~$ sudo ls /lib/firmware/b43
a0g0bsinitvals5.fw lcn400initvals33.fw sslpn1bsinitvals20.fw
a0g0bsinitvals9.fw lp0bsinitvals13.fw sslpn1bsinitvals27.fw
a0g0initvals5.fw
lp0bsinitvals14.fw sslpn1initvals20.fw
a0g0initvals9.fw
lp0bsinitvals15.fw sslpn1initvals27.fw
a0g1bsinitvals13.fw lp0bsinitvals16.fw sslpn2bsinitvals19.fw
a0g1bsinitvals5.fw lp0initvals13.fw
sslpn2initvals19.fw
a0g1bsinitvals9.fw lp0initvals14.fw
sslpn3bsinitvals21.fw
a0g1initvals13.fw
lp0initvals15.fw
sslpn3initvals21.fw
a0g1initvals5.fw
lp0initvals16.fw
sslpn4bsinitvals22.fw
a0g1initvals9.fw
lp1bsinitvals20.fw sslpn4initvals22.fw
b0g0bsinitvals13.fw lp1bsinitvals22.fw ucode11.fw
b0g0bsinitvals5.fw lp1initvals20.fw
ucode13.fw
b0g0bsinitvals9.fw lp1initvals22.fw
ucode14.fw
b0g0initvals13.fw
lp2bsinitvals19.fw ucode15.fw
b0g0initvals5.fw
lp2initvals19.fw
ucode16_lp.fw
b0g0initvals9.fw
n0absinitvals11.fw ucode16_mimo.fw
ht0bsinitvals26.fw n0bsinitvals11.fw
ucode16_sslpn.fw
ht0bsinitvals29.fw n0bsinitvals16.fw
ucode16_sslpn_nobt.fw
ht0initvals26.fw
n0bsinitvals17.fw
ucode17_mimo.fw
ht0initvals29.fw
n0bsinitvals22.fw
ucode19_sslpn.fw
lcn0bsinitvals24.fw n0bsinitvals24.fw
ucode19_sslpn_nobt.fw
lcn0bsinitvals25.fw n0bsinitvals25.fw
ucode20_sslpn.fw
lcn0bsinitvals26.fw n0initvals11.fw
ucode20_sslpn_nobt.fw
lcn0initvals24.fw
n0initvals16.fw
ucode21_sslpn.fw
lcn0initvals25.fw
n0initvals17.fw
ucode21_sslpn_nobt.fw
lcn0initvals26.fw
n0initvals22.fw
ucode22_mimo.fw
lcn1bsinitvals24.fw n0initvals24.fw
ucode22_sslpn.fw
lcn1bsinitvals25.fw n0initvals25.fw
ucode24_lcn.fw
lcn1bsinitvals26.fw n16bsinitvals30.fw ucode24_mimo.fw
lcn1initvals24.fw
n16initvals30.fw
ucode25_lcn.fw
lcn1initvals25.fw
n18bsinitvals32.fw ucode25_mimo.fw
lcn1initvals26.fw
n18initvals32.fw
ucode26_mimo.fw
lcn2bsinitvals24.fw n1bsinitvals20.fw
ucode27_sslpn.fw
lcn2bsinitvals25.fw n1initvals20.fw
ucode29_mimo.fw
lcn2bsinitvals26.fw n2bsinitvals19.fw
ucode30_mimo.fwlcn2initvals24.fw
n2initvals19.fw
ucode32_mimo.fw
lcn2initvals25.fw
pcm5.fw
ucode33_lcn40.fw
lcn2initvals26.fw
sslpn0bsinitvals16.fw ucode5.fw
lcn400bsinitvals33.fw sslpn0initvals16.fw ucode9.fw

sudo apt-get install firmware-b43-installer b43-fwcutter
??? - $ sudo apt-get install firmware-b43-installer b43-fwcutter
Reading package lists... Done
Building dependency tree
Reading state information... Done
b43-fwcutter is already the newest version (1:019-2).
firmware-b43-installer is already the newest version (1:019-2).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Forget where I encountered this, but seemed pertinent:

"The following packages were automatically installed and are no longer required:
libllvm4.0 linux-signed-image-generic-hwe-16.04"

After “sudo apt-get purge bcmwl-kernel-source” -
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 8,064 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 211297 files and directories currently installed.)
Removing bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu1~1.2) ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu1~1.2) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.122ubuntu8.11) ...

After “ sudo b43-fwcutter -w /lib/firmware broadcom-wl-5.100.138/linux/wl_apsta.o” -
phoebe@afx34:~$ sudo b43-fwcutter -w /lib/firmware broadcom-wl-5.100.138/linux/wl_apsta.o
This file is recognised as:
filename : wl_apsta.o
version : 666.2
MD5
: e1b05e268bcdbfef3560c28fc161f30e
Extracting b43/lp0initvals14.fw
Extracting b43/lcn0bsinitvals25.fw
Extracting b43/n0bsinitvals25.fw
Extracting b43/n0bsinitvals17.fw
Extracting b43/ucode17_mimo.fw
Extracting b43/ucode16_lp.fw
Extracting b43/sslpn1initvals27.fw
Extracting b43/lp2bsinitvals19.fw
Extracting b43/sslpn3bsinitvals21.fw
Extracting b43/ucode16_sslpn.fw
ucode time: 01:15:07
Extracting b43/ucode25_lcn.fw
Extracting b43/ucode21_sslpn.fw
Extracting b43/lp0bsinitvals14.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/ucode20_sslpn.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/lp1initvals20.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/lp2initvals19.fw
Extracting b43/n2bsinitvals19.fw
Extracting b43/sslpn4bsinitvals22.fw
Extracting b43/ucode16_sslpn_nobt.fw
ucode date: 2011-02-23
Extracting b43/n1bsinitvals20.fw
Extracting b43/n1initvals20.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/ucode22_sslpn.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/ht0initvals26.fw
Extracting b43/ucode33_lcn40.fw
Extracting b43/sslpn1bsinitvals20.fw
Extracting b43/lcn400bsinitvals33.fw
Extracting b43/ucode14.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/lp1bsinitvals22.fw
Extracting b43/n16initvals30.fw
Extracting b43/lp0bsinitvals16.fw
Extracting b43/lcn1bsinitvals25.fw
Extracting b43/lcn400initvals33.fw
Extracting b43/n0bsinitvals24.fwExtracting b43/lcn2bsinitvals26.fw
Extracting b43/lcn1initvals26.fw
Extracting b43/n0bsinitvals22.fw
Extracting b43/n18initvals32.fw
Extracting b43/lcn2initvals26.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/lcn2initvals24.fw
Extracting b43/lcn0initvals26.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/ucode21_sslpn_nobt.fw
ucode time: 01:15:07
Extracting b43/ucode26_mimo.fw
Extracting b43/n2initvals19.fw
Extracting b43/sslpn3initvals21.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/sslpn4initvals22.fw
Extracting b43/pcm5.fw
Extracting b43/ucode22_mimo.fw
Extracting b43/ucode9.fw
Extracting b43/lcn2initvals25.fw
Extracting b43/lp1initvals22.fw
Extracting b43/sslpn1bsinitvals27.fw
Extracting b43/lcn0initvals24.fw
Extracting b43/ucode32_mimo.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/n18bsinitvals32.fw
Extracting b43/n0initvals24.fw
Extracting b43/n0initvals25.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/ucode24_lcn.fw
Extracting b43/n0initvals17.fw
Extracting b43/n0bsinitvals16.fw
Extracting b43/lp0initvals15.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/ucode20_sslpn_nobt.fw
Extracting b43/lcn1initvals24.fw
Extracting b43/sslpn0initvals16.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/lp1bsinitvals20.fw
Extracting b43/sslpn2initvals19.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/lcn1bsinitvals24.fw
Extracting b43/ucode5.fw
Extracting b43/lcn2bsinitvals24.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/n0initvals16.fw
Extracting b43/ucode19_sslpn_nobt.fw
Extracting b43/b0g0bsinitvals9.fwExtracting b43/ucode11.fw
Extracting b43/lp0initvals16.fw
Extracting b43/ucode16_mimo.fw
Extracting b43/lcn0bsinitvals26.fw
Extracting b43/ht0initvals29.fw
Extracting b43/lcn2bsinitvals25.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/ucode29_mimo.fw
Extracting b43/lcn0bsinitvals24.fw
Extracting b43/ucode19_sslpn.fw
Extracting b43/lcn1initvals25.fw
Extracting b43/ucode30_mimo.fw
Extracting b43/n16bsinitvals30.fw
Extracting b43/ucode25_mimo.fw
Extracting b43/ucode24_mimo.fw
Extracting b43/ucode27_sslpn.fw
Extracting b43/lp0initvals13.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/ht0bsinitvals26.fw
Extracting b43/ucode13.fw
Extracting b43/sslpn2bsinitvals19.fw
Extracting b43/ucode15.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/n0initvals11.fw
Extracting b43/lcn0initvals25.fw
Extracting b43/sslpn0bsinitvals16.fw
Extracting b43/sslpn1initvals20.fw
Extracting b43/lcn1bsinitvals26.fw
Extracting b43/n0initvals22.fw
Extracting b43/ht0bsinitvals29.fw
update-initramfs: Generating /boot/initrd.img-4.15.0-29-generic
W: Possible missing firmware /lib/firmware/i915/kbl_guc_ver9_14.bin for module i915
W: Possible missing firmware /lib/firmware/i915/bxt_guc_ver8_7.bin for module i915


Sooo since I have no back up means of getting my HP Streambook online except when its wifi is working , this is a frustrating cycle of going on Ubuntu sites, taking notes. Doing the update->Failing->reinstall whole OS-> more research-> 2 hour update->More failing. So any help you can give at this point is much appreciated!

---

### Post by chili555 on 2018-07-31
I apologize for the delay in my reply.> Hi Dr. Chilli I have been dealing with an Ubuntu 'install' Wifi issue that revolves around firmware, b43 & my Broadcom 43123 not showing up when I rfkill list.Please check here: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)  As you can see, b43 and firmware are not correct for your device. You need bcmwl-kernel-source.>  reinstalled from the thumb I keep ready.If you still have the install USB, then you need to find bcmwl-kernel-source and dkms on it and install them. Here is the process: [https://askubuntu.com/questions/553615/cant-enable-the-proprietary-drivers-for-broadcom-bcm43142-wireless-after-instal/553619#553619](https://askubuntu.com/questions/553615/cant-enable-the-proprietary-drivers-for-broadcom-bcm43142-wireless-after-instal/553619#553619)

Post back if you get stuck.

---

