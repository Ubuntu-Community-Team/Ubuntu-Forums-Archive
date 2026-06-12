---
title: "Ubuntu on MBP, no wireless or Firefox"
date: 2008-07-21
forum: Apple Hardware Users
---

### Post by ddeadserious on 2008-07-21
[COLOR="White"]Installed Ubuntu on my Macbook Pro(2ghz Core Duo(not core 2), 2GB or RAM, 100GB HD). Running OSX Tiger(no boot camp). I'm not all that experienced with this kind of stuff, I know computers, but I've not messed with linux before, so take it easy on me.

I had Kubuntu installed and decided I didn't like it, but it had this same wireless issue.

I used Drive Genius 2 to make a 7GB partition for Ubuntu. I'm using rEFIt as a bootloader which is working nicely.

Install went smooth and it runs really well.

But there's no wireless internet, no matter how I configure my router, and whether I turn the WEP/WPA key off or not. Ubuntu sees the wireless port, as well as some of my neighbors as well. So I know Ubuntu is seeing my wireless card and being somewhat functional, but it just won't connect.[/COLOR]

Also, Firefox will not open under any circumstances. It gives me the cursor loader, and a "Starting up Firefox..." in the taskbar opens up for about 10 seconds, but I never see any Firefox and it never opens.

Any ideas?

Thanks for the help in advance.

---

### Post by ddeadserious on 2008-07-21
No ideas?

---

### Post by cyberdork33 on 2008-07-22
> **ddeadserious said:**
> No ideas?
your firefox install is broken. it might start again if you delete the firefox info in your home folder, otherwise it probably needs reinstalled.

I don't know why your WiFi isn't working. What happens when you try to connect to an AP? does it connect but not get an IP? how did you enable the WiFi card? What is the output of 'ifconfig'?

---

### Post by kdb424 on 2008-07-22
Streight fron the wiki ([https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook))

Wireless

If you have a first generation MacBook (Core Duo) then your wireless should just start working, though you may want to update to the latest version as illustrated below for better power efficiency and signal strength. Second generation MacBooks (Core 2 Duo) have a newer version of the Atheros Wifi chipset which requires the installation of the latest Atheros MadWifi drivers. bug #122703

Please note that the current MadWifi drivers depend on a proprietary binary, the Atheros HAL, and therefore are not open-source software. A free software implementation, OpenHAL, is currently being developed by the Madwifi devs, but unfortunately it does not support the Atheros chipset in the MacBooks yet.

The following commands compile and install the prerelease MadWifi driver and insert it into the kernel.

First you will need an alternative connection to the Internet, such as wired ethernet. If this is the first time connecting your MacBook to the Internet, make sure to update your package lists before continuing so that Ubuntu can find the appropriate packages:

sudo apt-get update

For installation, you can choose to use daily snapshots or Subversion.

Method 1: Using daily snapshots:

sudo apt-get install build-essential autoconf automake
wget [http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz](http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz)
tar -zxvf madwifi-trunk-current.tar.gz
cd madwifi-trunk-r*
make
sudo make install-modules

Method 2: Alternatively, using Subversion (be patient with the checkout, it may take a while):

sudo apt-get install build-essential subversion autoconf automake
svn co [http://svn.madwifi.org/madwifi/trunk](http://svn.madwifi.org/madwifi/trunk) madwifi
cd madwifi
make
sudo make install-modules

At this point the driver should be installed and will be enabled after a reboot. Alternatively, you can skip the reboot and use the following command to insert the driver into the running kernel:

sudo modprobe ath_pci

Historically, some users have had trouble with stability when background scanning is enabled on these drivers, as well as the use of Network-Manager (the applet used in Gnome to manage network connections). The problem seems to have been fixed as of 8.04 and the latest MadWifi -- but if you experience problems, try disabling background scanning by running these lines:

echo -e '#!/bin/sh\n/sbin/iwpriv ath0 bgscan 0' | sudo tee -a /etc/acpi/resume.d/99-madwifi-bgscan.sh
sudo chmod 755 /etc/acpi/resume.d/99-madwifi-bgscan.sh
sudo iwpriv ath0 bgscan 0

If you do have problems with stability and want to temporarily disable the drivers if you aren't using wireless, edit the /etc/modprobe.d/blacklist file and add "blacklist ath_pci" at the bottom. Additionally, you can deselect the Atheros HAL in the Restricted Manager (System-Administration-Restricted Drivers Manager).

To disallow replacement of just installed modules by installing linux-restricted-modules package update you can edit /etc/default/linux-restricted-modules-common and insert ath_hal into DISABLED_MODULES list:

sudo sed -i~ -e 's/^\(DISABLED_MODULES="\)\(.*"\)/\1ath_hal \2/' -e 's/ "$/"/' /etc/default/linux-restricted-modules-common

More information can be obtained at [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

If you need to connect to a channel that's not allowed in the regulatory domain in which you bought your laptop, you'll need to follow these instructions: [http://tumbleweed.org.za/2008/02/11/madwifi-regdomain-issues](http://tumbleweed.org.za/2008/02/11/madwifi-regdomain-issues)

---

### Post by ddeadserious on 2008-07-22
From what I read, since my MBP is first generation, the wireless should just work, but it doesn't.

I'll try the fix(s) above later on.

Thanks.

---

### Post by ddeadserious on 2008-07-23
I reinstalled Ubuntu over the old one and it solved my wireless issue.

My firefox is still broken.

I suppose I don't have the hang of installing things yet, where do I manually put the new firefox, where do I put all the associated files/folders?

And how the heck do I get rid of the "shortcuts"(firefox, that mail program, and the ? thing) from the top bar?

---

### Post by cyberdork33 on 2008-07-23
> **ddeadserious said:**
> I reinstalled Ubuntu over the old one and it solved my wireless issue.

My firefox is still broken.

I suppose I don't have the hang of installing things yet, where do I manually put the new firefox, where do I put all the associated files/folders?

And how the heck do I get rid of the "shortcuts"(firefox, that mail program, and the ? thing) from the top bar?
If you reinstalled from scratch again and you are having the same issue with firefox, I would say you have a bad disc or something. That doesn't make sense that it has issues after a fresh install without having done anything.

Try reinstalling firefox from the commandline like so:
```
sudo aptitude reinstall firefox
```

You don't manually put application files anywhere. apt/synaptic is your software gateway. Look in System > Administration > Synaptic Software Manager, find the application you want and install it. It will automatically get any dependencies it might have as well.

You can remove the launchers from the panel by right-clicking on them and seleting remove. You can add new ones by dragging the icon out of the Application menu onto the panel.

---

### Post by ddeadserious on 2008-07-24
> **cyberdork33 said:**
> If you reinstalled from scratch again and you are having the same issue with firefox, I would say you have a bad disc or something. That doesn't make sense that it has issues after a fresh install without having done anything.

Try reinstalling firefox from the commandline like so:
```
sudo aptitude reinstall firefox
```

You don't manually put application files anywhere. apt/synaptic is your software gateway. Look in System > Administration > Synaptic Software Manager, find the application you want and install it. It will automatically get any dependencies it might have as well.

You can remove the launchers from the panel by right-clicking on them and seleting remove. You can add new ones by dragging the icon out of the Application menu onto the panel.

Thanks.

I tried reinstalling Firefox as directed above, to no avail. It said it was doing everything and stuff, but Firefox still doesn't work.:(

hmmph.

---

### Post by cyberdork33 on 2008-07-24
> **ddeadserious said:**
> Thanks.

I tried reinstalling Firefox as directed above, to no avail. It said it was doing everything and stuff, but Firefox still doesn't work.:(

hmmph.
this is very strange.

When you click the Firefox icon, run this in the terminal:
```
ps -A |grep firefox
```If "firefox" is listed, then the process is running... 

If it is not running, then try deleting the firefox stuff in your home folder:
```
rm -R ~/.mozilla/
```Then try starting firefox again.

---

### Post by ddeadserious on 2008-07-24
> **cyberdork33 said:**
> this is very strange.

When you click the Firefox icon, run this in the terminal:
```
ps -A |grep firefox
```If "firefox" is listed, then the process is running... 

If it is not running, then try deleting the firefox stuff in your home folder:
```
rm -R ~/.mozilla/
```Then try starting firefox again.

Will do when I get home, thanks for your help.

---

### Post by ddeadserious on 2008-07-27
> **cyberdork33 said:**
> this is very strange.

When you click the Firefox icon, run this in the terminal:
```
ps -A |grep firefox
```If "firefox" is listed, then the process is running... 

If it is not running, then try deleting the firefox stuff in your home folder:
```
rm -R ~/.mozilla/
```Then try starting firefox again.

The first command returns with nothing, so I assume it's not running, regardless of the "Starting Firefox Web..." in the lower taskbar.

Running the rm command returned with "rm: descend into write-protected directory `/home/mforbush/.mozilla/'?", I hit enter, and Terminal went back to the "mforbush@mforbush-linux:~$"... So I'm assuming it did what it was supposed to. But firefox still didn't work...

I'm able to run Firefox through the one that I manually downloaded, just running with sudo via terminal out of the folder on the desktop.

Any other ideas?

---

### Post by ddeadserious on 2008-07-27
I also "completely removed it" via Synaptic Package Manager, and then Installed it, but it still doesn't function.:(

---

### Post by cyberdork33 on 2008-07-27
> **ddeadserious said:**
> "rm: descend into write-protected directory `/home/mforbush/.mozilla/'?"
Well that may be the problem. That directory should not be write protected, but it probably is since you have been running Firefox with sudo.

When you run the rm comamnd, you have to answer the 'yes' so that it will delete the folder.

---

### Post by ddeadserious on 2008-07-28
> **cyberdork33 said:**
> Well that may be the problem. That directory should not be write protected, but it probably is since you have been running Firefox with sudo.

When you run the rm comamnd, you have to answer the 'yes' so that it will delete the folder.

Here's the response to me saying yes:
mforbush@mforbush-linux:/$ rm -R ~/.mozilla/
rm: descend into write-protected directory `/home/mforbush/.mozilla/'? yes
rm: cannot remove `/home/mforbush/.mozilla/': Permission denied

The folder is locked:
[IMG]http://img.photobucket.com/albums/v25/trialbyashes/Screenshot-mforbush-FileBrowser.png[/IMG]

And here is the result of me telling it to be moved to the trash was:
"Error while deleting. The folder ".mozilla" cannot be handles because you do not have permissions to read it."

Ugh. Now what?

---

### Post by cyberdork33 on 2008-07-28
> **ddeadserious said:**
> Here's the response to me saying yes:
mforbush@mforbush-linux:/$ rm -R ~/.mozilla/
rm: descend into write-protected directory `/home/mforbush/.mozilla/'? yes
rm: cannot remove `/home/mforbush/.mozilla/': Permission denied

And here is the result of me telling it to be moved to the trash was:
"Error while deleting. The folder ".mozilla" cannot be handles because you do not have permissions to read it."

Ugh. Now what?Use sudo in front of the command. That uses the root permissions to delete the folder. This is realted though. Your user cannot delete the folder because that folder is likely now owned by root (since you have ran firefox as root). You should never need to run firefox as root, and if you do run an application as root, you should use 'gksudo *command*' to start the application to avoid strange issues.

---

