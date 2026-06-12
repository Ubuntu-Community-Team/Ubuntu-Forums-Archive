---
title: "Macbook Pro 9,2 with BroadCom 4331 wireless card - Intermitent Wifi on Ubuntu 14.04"
date: 2016-04-02
forum: Apple Hardware Users
---

### Post by kikedadddy on 2016-04-02
Hello.
I usually do not post questions on forums due to the fact that I always find the answers by searching around first. However in this case I feel like I have tried a lot of different proposed solutions without any success.

Main problem is that the internet is intermittent. By this I mean that it it connects and is stable for around 5-10 minutes and then can easily drop. It however does not show as dropped on programs that are internet related nor those it show as dropped on the wifi symbol on the top. It just does not connect when requested to do so (example loading a website just keeps on loading and finally said that the action could not be performed).

I have tried with:

firmware-b43-installer
bcmwl-kernel-source

and have had no success in keeping a stable connection. However the kernel driver wl seems to work better than the bcma-pci-bridge one.

Downloading large things, using skype, team viewer, or even facebook chat becomes impossible because it thinks it is still connected yet no information is passing by.

Any help would be highly appreciated. Thank you so much for your help. 

please keep in mind im rather new to linux yet fairly experienced with computing, so patience is also appreciated.

---

### Post by Hadaka on 2016-04-02
Your wireless card's PCI-ID is..[14e4:4331]

From a working wired connection,Please open a terminal ctrl/alt/t
Copy and paste the following commands one at a time.

*Ignore any errors or file not found for commands 2 or 3

```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo apt-get install b43-fwcutter firmware-b43-installer
echo "options b43 nohwcrypt=1" | sudo tee -a /etc/modprobe.d/b43.conf
sudo modprobe b43
```

 then do..
```
sudo iw reg set SE
sudo sed -i 's/^REG.*=$/&SE/' /etc/default/crda
```

remove wired connection,boot and test wireless
thanks.

---

### Post by QIII on 2016-04-02
*Moved to **Apple Hardware Users***

---

### Post by kikedadddy on 2016-04-02
Hi and thank you so much for your prompt response.

I have been working on the machine for a couple of hours and have not noticed any drops yet which is awesome. I will update in a couple of days regarding if it is solved or not.


As an attempt to learn a little more about linux and all its ins and outs could you please tell me what is the difference with what i had previously done?

like just installing:
firmware-b43-installer

I am a bit confused with your comment 
"Your wireless card's PCI-ID is..[14e4:4331]"
I was aware of this. because of this i had tried to follow these instructions:
[http://ubuntuforums.org/showthread.php?t=1966236](http://ubuntuforums.org/showthread.php?t=1966236)
or this
[http://askubuntu.com/questions/470153/no-wireless-when-install-14-04-on-macbook-pro](http://askubuntu.com/questions/470153/no-wireless-when-install-14-04-on-macbook-pro)

Like I mentioned before I had followed plenty of instructions and none worked.

Tx again for your help and help in advanced for any possible clarification.

---

### Post by Hadaka on 2016-04-02
> **kikedadddy said:**
> Hi and thank you so much for your prompt response.

I have been working on the machine for a couple of hours and have not noticed any drops yet which is awesome. I will update in a couple of days regarding if it is solved or not.


As an attempt to learn a little more about linux and all its ins and outs could you please tell me what is the difference with what i had previously done?

like just installing:
firmware-b43-installer

I am a bit confused with your comment 
"Your wireless card's PCI-ID is..[14e4:4331]"
I was aware of this. because of this i had tried to follow these instructions:
[http://ubuntuforums.org/showthread.php?t=1966236](http://ubuntuforums.org/showthread.php?t=1966236)
or this
[http://askubuntu.com/questions/470153/no-wireless-when-install-14-04-on-macbook-pro](http://askubuntu.com/questions/470153/no-wireless-when-install-14-04-on-macbook-pro)

Like I mentioned before I had followed plenty of instructions and none worked.

Tx again for your help and help in advanced for any possible clarification.
```

Hi, to help you with any confusion about my post of.."Your wireless card's PCI-ID is..[14e4:4331]"
it is something that comes from a script that i use for Broadcom wifi cards . Those numbers also
showed up in your wireless report.."Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331]"
In your case and as is with alot of Broadcom cards..your card BCM4331 matches your PCI-ID [14e4:4331]
Each wifi card manufacturing company gets assigned a product code..intel is [8080:XXXX] and of course
Broadcom is [14e4:XXXX]. So to determine the correct or best driver for a card the PCI-ID is used.
Yours is product code PCI [14e4:ID] and a product ID of [PCI :4331]. PCI-ID. Sometimes the card number
does not match the PCI-ID as in..."Broadcom BCM43142 [14e4:4365]" as you can see the card number is
totally different. in this case..the pci-id is [14e4:4365] the 4365 part determines the driver..and it is the WL
or broadcom-kernel-source driver. Yours 4331 is the b43 dirver. The PCI-ID codes for broadcom cards can be
figured out here..->  http://ubuntuforums.org/showthread.php?t=2214110  
I hope this explains it to you more clearly.

Would you like an explanation on the commands?
```

---

### Post by Hadaka on 2016-04-03
Explanation of commands..

*Ignore any errors or file not found for commands 2 or 3 <--In the event these files are not present.

**sudo apt-get update** <----Update the the os with the current security files
.........................and update applications and system functions.

**sudo apt-get remove --purge broadcom-kernel****-source** <---Remove the current incorrect driver

**sudo rm /etc/modprobe.d/blacklist-bcm43.conf** <---Remove this file that is atutomatically
.............................................generated when the broadcom-kernel-source driver
.............................................is loaded.It blacklists modules b43,ssb and bcma
.............................................This prevents the b43 driver from loading. The file
.............................................is normally removed when the broadcom-kernel-source
.............................................file is purged,sometimes this does not happen,therefore
.............................................this command insures the file is removed if present.

**sudo apt-get install b43-fwcutter firmware-b43-installer** <--Install correct b43 driver

**echo "options b43 nowhwcrypt=1"**** | sudo tee -a /etc/modprobe.d/****b43.conf** <--Disable hardware encryption
..................................................................as it often causes drops and slow connections.

**sudo modprobe b43** <---Insert,activate the b43 driver.

sudo iw reg set SE
sudo sed -i 's/^REG.*=$/&SE/' /etc/default/crda <-- Set the correct country code,yours was not set correctly.
............................................... incorrect or default value of 00 can cause drops,slow connections
............................................... and processor load of connection commands confusion.

---

### Post by kikedadddy on 2016-04-04
Hi sorry to bug again but Ive been trying the internet for the past 24 hours and its has been a rollercoaster. 

I  can say that at home it seemed to be a lot more stable and then it  started crashing again. Now its almost not usable (wired atm).

In  school is a whole other lvl of nightmware. The signal strength jumps  between full and none. It connects and disconnects. Then after 20  minutes it connects again (we have eduroam at school, dont know if that  says anything).

any help would be highly appreciated again.

---

### Post by kikedadddy on 2016-04-04
forgot to include the file:

[ATTACH=CONFIG]268176[/ATTACH]

---

### Post by Hadaka on 2016-04-04
Hi, somehow you managed to blacklist your b43 dirver again...
here...
```
[/etc/modprobe.d/blacklist.conf]
blacklist bcma
```
and here...
```
[/etc/modprobe.d/broadcom-sta-dkms.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb
```
sooo...let's fix it again..open a terminal ctrl/alt/t 
then copy and paste...
```
sudo sed -ie '/^blacklist bcma/ d' /etc/modprobe.d/blacklist.conf
sudo rm -rf /etc/modprobe.d/broadcom-sta-dkms.conf
sudo modprobe -rf b43
sudo modprobe -v b43
```
then please post back the results of...
```
cat /etc/modprobe.d/blacklist.conf | grep -i blacklist
cat /etc/modprobe.d/broadcom-sta-dkms.conf
```
thanks.

---

### Post by kikedadddy on 2016-04-05
Hey and thanks again for your help. 
Weird it got blacklisted again, I haven't touched anything.
Internet is at least connecting, however the signal is still dodgy (pages loading for a long time)

the results of the two commands are:

cat /etc/modprobe.d/blacklist.conf | grep -i blacklist

blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
blacklist amd76x_edac
blacklist brcmsmac

cat /etc/modprobe.d/broadcom-sta-dkms.conf
cat: /etc/modprobe.d/broadcom-sta-dkms.conf: No such file or directory

---

### Post by Hadaka on 2016-04-05
Ok, the only driver that will work correctly with your card is the b43.
any drivers in "additional drivers" or "proprietary drivers" while suggested
also will not work. I am glad you atleast now have a working wireless.
From a working wired connection please open a terminal and do..
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get autoremove
sudo apt-get autoclean
```
then do..
```
sudo sed -i '/^brcmsmac/ d' /etc/modprobe.d/blacklist.conf
sudo apt-get remove --purge firmware-b43-installer
sudo apt-get install firmware-b43-installer
sudo modprobe -rf b43
sudo modprobe b43
```
then remove wired connection,boot and test wireless.
*if the page load is still slow..post a wieless script using the wireless connection
thanks.

---

### Post by kikedadddy on 2016-04-07
Hi and sorry for the late answer. I hadnt noticed that there was a pg2 (feeling like an idiot).

The connection seems to be a lot more stable here at home. Although it has always been sort of stable. I will update tomorrow at school when I try their network.

At home i have a router which supports 5G for faster internet connections. I ran iwconfig and noticed im only on the 2.4 band. Any reason why I cant see the 5Ghz band?

---

### Post by Hadaka on 2016-04-07
Hi, give this a try..copy and paste..
```
sudo sed -i 's/options b43 nohwcrypt=1/#options b43 nohwcrypt=1/'  /etc/modprobe.d/b43.conf
```
boot and see if it will attach 5ghz
if it starts acting flakey on you and dropping or hanging up then put the option back with a value of 8..
```
sudo sed -i 's/#options b43 nohwcrypt=1/options b43 nohwcrypt=8/'  /etc/modprobe.d/b43.conf
```

Your school network...eduroam...is a totally different situation. If you are still having problems there, then run
the wireless script ...hopefully... from the eduroam network, there is nothing wrong at this point with your
computers network configuration.
thanks.

---

### Post by kikedadddy on 2016-04-07
Hi and tx again for the quick response.

No success on the command it still connects to 2.4 and no option for the 5G. Also when running the wireless-info script i noticed that all 13 channels say 2.4 Ghz so it does not even realize the card has 5G capabilities I guess. 

Booted OSX to make sure it recognizes the 5G frequency and it does and can connect.

The wireless capabilites while in ubuntu are still extremely slow. considering buying a wifi dongle just to get rid of this problem. It feels borderline ridiculous at this point to keep having the same issues.

Any recommendations? Should I shoot with the last resort of a wifi dongle or is there still hope?

Tx again for your help. 

I attach the info
.[ATTACH]268230[/ATTACH]

---

### Post by Hadaka on 2016-04-07
Hi, yeah it just doesnt want to fly on 5ghs, even though it does on the same card when
its an apple box. your dmesg from the wireless report shows this,,,
```
##### dmesg #############################

[   17.276347] b43-phy0: Broadcom 4331 WLAN found (core revision 29)
[   17.276722] b43-phy0: Found PHY: Analog 9, Type 7 (HT), Revision 1
[   17.276732] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2059, Revision 0, Version 1
[   17.276734] b43-phy0 warning: ***5 GHz*** band is ***unsupported*** on this PHY

```
I also noticed you attempted to get a usb wifi to work but it failed.
```
# USB device ***0x:0x*** (***rtl8192cu***)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

```
Let's see if we can get it to work.From a working wired connection, open a terminal then copy and paste..
```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -v rtl8192cu
```
boot with the usb module in and test.

---

