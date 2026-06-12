---
title: "Macbook Pro 8,2 Wireless on Quantal 12.10 BCM4331"
date: 2012-10-25
forum: Apple Hardware Users
---

### Post by aChipmunk on 2012-10-25
I installed ubuntu 12.10 lest night and I have been unable to get wireless working using the directions here [https://help.ubuntu.com/community/MacBookPro8-2/Quantal](https://help.ubuntu.com/community/MacBookPro8-2/Quantal)
When I add the ppa mpodroid/mactel and run an "apt-get update"  I get 404 errors for the mactel repos.

I also tried just installing the packages 

sudo apt-get install b43-fwcutter firmware-b43-installer
sudo apt-get install linux-firmware linux-firmware-nonfree

because some bloggers have had success with that...  However, that had no effect.

Before I start trying to hand build the drivers and b43-fwcutter like what worked on 12.04 I wanted to come here so I don't end of messing things up.

Thanks!

---

### Post by jays241 on 2012-10-26
Give me more data?

lspci?

/etc/modules?

/etc/modprobe.d/blacklist.conf?

have you tried to manually load it? sudo modprobe b43

if this works just add b43 to your /etc/modules

cheers

---

### Post by mode7 on 2012-10-30
I have a MacBook Pro 8,1 with the 4331 as well.
The problem would appear to be that the mpodroid mactel PPA does not have a Quantal repository, so apt-get fails when it attempts to contact the nonexistent Quantal section.

I know you can manually download the packages, but when I visit the mpodroid launchpad page, the firmware-b43-installer package is not listed.
I have no clue why not, because if you do not have that PPA, the firmware-b43-installer package in the default repositories fails to identify the bcm4331 card while installing... and ends up actually doing nothing even though it is installed (Read terminal output).

Since I don't know how to obtain that package (Although I am sure there is a very easy way to do it that I don't know of), the best solution would probably be to manually extract the firmware.

I simply went back to 12.04 because I am super busy (Not to mention 12.10 completely fails to work with my desktop's ATI card), but I will probably manually install that b43 firmware myself too sometime.

---

### Post by giowck on 2012-11-01
I solved the issue on my macbook pro 8,2 with bcm 4331 by removing firmware-installer-b43 and fwcutter-b43 and then I installed the  linux-headers-generic and linux-firmware-nonfree packages.

The key package was the linux headers, only with this it is working after a reboot.

---

### Post by aChipmunk on 2012-11-11
Sorry it took me so long to respond, but I have been very busy...

However, I did finally get this working!
 
Anyway, I did a combination of all three posts.  I removed firmware-b43-installer and b43-fwcutter.  Reboot, no luck.  I installed linux-headers-generic and linux-firmware-nonfree and updated.  Again no luck.  
Then I tried sudo modprobe b43 and all is working!

Thanks everyone.

---

### Post by awm086 on 2012-12-07
If you do iwconfig, do you get something like "IEEE 802.11b/g " or b/g/n I am having a problem with n mode access points. It is because the drivers available do not support it. Any ideas?

---

### Post by trogdor1138 on 2012-12-07
> **awm086 said:**
> I am having a problem with n mode access points. It is because the drivers available do not support it. Any ideas?

If you're using the same MacBook Pro as in the thread's title, wireless N isn't supported yet. I have the same MBP and b/g is as good as it gets. You can see the status of the b43 drivers for various Broadcom chipsets at the project's homepage: [http://linuxwireless.org/en/users/Drivers/b43#Supported_devices](http://linuxwireless.org/en/users/Drivers/b43#Supported_devices)

---

### Post by lukeco11 on 2012-12-08
I am finding these drivers to be very flaky. They tend to disconnect often when I move the laptop around. They also prompt for wifi key often even though it has already been entered. This is the only thing keeping me from using Ubuntu full time on this and not sure how to improve the situation. Am I alone in this? Could be something else causing it?

---

### Post by kgunn72 on 2013-01-30
the key was the $sudo modprobe b43
I had already downloaded the b43-fwcutter firmware-b43-instal...and i did not uninstall them
also, I did not install  linux-firmware & linux-firmware-nonfree

I've been farting around with this for about 2+hours now....thanks for the tip

one admittance, I did follow the instructions about installing the backports here 
[http://askubuntu.com/questions/120143/macbook-pro-8-1-13-wifi-issues?rq=1](http://askubuntu.com/questions/120143/macbook-pro-8-1-13-wifi-issues?rq=1)
(note i used quantal packages of course, not oneric or precise)

---

