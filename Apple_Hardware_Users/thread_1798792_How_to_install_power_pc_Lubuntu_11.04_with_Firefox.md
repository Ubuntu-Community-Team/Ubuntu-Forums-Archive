---
title: "How to install power pc Lubuntu 11.04 with Firefox 5"
date: 2011-07-06
forum: Apple Hardware Users
---

### Post by rsavage on 2011-07-06
**:arrow: Most of the information in this post has now been moved to the [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ) ****and the [https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues) ****pages. Please refer to them for the latest information. The only section that has not been moved across is the Install Lubuntu section.**
 
This post has grown somewhat from it's original idea - a simple set of notes to install [Lubuntu]("http://lubuntu.net/about") on PowerPC - to something that more likely resembles an updated PowerPC FAQ! However, it has never been by intention to replace the FAQ with this post, and in fact, I've tried not to duplicate information that is documented well elsewhere. So please do still check out the FAQ and release note links at the bottom of the post! 
 
A lot of the information really belongs in the PowerPC FAQ so that everybody has the opportunity to edit it and keep it up to date. If somebody would like to start updating the FAQ by cutting and pasting sections from here then please feel free to do so! I would be very pleased if you do! :-)
 
The post now also includes instructions to install Ubuntu, [Xubuntu]("http://www.xubuntu.org/"), [Kubuntu]("http://www.kubuntu.org/"), etc from the mini cd. The mini cd is a great way to install if there is not a live cd version available or if you can't get it to run correctly. There are various things you can try with the 11.10 live cd [http://ubuntuforums.org/showthread.php?t=1872733](http://ubuntuforums.org/showthread.php?t=1872733), although the severity of the symptoms change on different machines. I can highly recommend Xubuntu. It is not as light as Lubuntu, but it does have round window corners, transparency and shadows whilst still being fast! 
 
You can of course also install Ubuntu 11.04 or 11.10 by upgrading from a previous version of Ubuntu. It's pretty straightforward through the Update Manager, but if you require further info then there are instructions in the release notes. The 'Workarounds' section below is there if you run into any PowerPC specific problems. I should add you don't have to upgrade if you are happy with your current release and are still receiving updates for it. The current long term support (LTS) release is 10.04 and the desktop edition will continue to receive updates until April 2013. The server edition of 8.04 (LTS) will also be supported until April 2013.
 
The post is not intended as a beginners guide to linux, although I think it would enable a new user to install ubuntu successfully. The post may seem long and scary, but maybe it is less so when you are actually doing it? Just take one step at a time..... I'm pretty confident most of the information you need should be here or on one of the links, so make sure you check them out first before wasting your time and effort on needless google searches. Please do tell me if you think some instructions are unclear. 
 
PowerPC Ubuntu is not an island and I hope that people using other distributions can also make use of some of the information here. I have learnt a lot by reading the great documentation that has been generously made openly and freely available by other distributions. 
 
Please feel free to add your own comments/suggestions/fixes/problems.
 
 
[SIZE=3]**1. The Base Installation**[/SIZE]
[SIZE=3][SIZE=3][SIZE=2]**1.1 Install the CLI**[/SIZE][/SIZE][/SIZE]
[SIZE=3]**[B][SIZE=2]1.2 G4 iBook and AlBook[/SIZE]**[/B][/SIZE]
[SIZE=3]**[SIZE=2]1.3 Other Computers[/SIZE]**
 
[/SIZE][SIZE=3]**2. Install the GUI**[/SIZE]
[SIZE=3]**[SIZE=2]2.1 Install Lubuntu[/SIZE]**
[/SIZE][SIZE=3]**[SIZE=2]2.2 Install Ubuntu, Xubuntu, Kubuntu, etc[/SIZE]**[/SIZE]
 
[SIZE=3]**3. Workarounds**[/SIZE]
[SIZE=2]**3.1 General Workarounds**[/SIZE]
**[SIZE=2]3.2 Wifi[/SIZE]**
**[SIZE=2]3.3 CPU Frequency Scaling[/SIZE]**
**[SIZE=2]3.4 Multimedia[/SIZE]** 
**[SIZE=2]3.5 Flash[/SIZE]**
**[SIZE=2]3.6 Java[/SIZE]** 
**[SIZE=2]3.7 Screen Resolution/Black Screen/No GUI Problems[/SIZE]** 
**[SIZE=2]_3.7a General notes on display issues[/SIZE]**
**[SIZE=2]_3.7b Yaboot parameters for screen problems[/SIZE]** 
**[SIZE=2][B][SIZE=2]_3.7c Configuring an xorg.conf file[/SIZE]**[/SIZE][/B]
[SIZE=2]**_3.7d Load kernel module **[/SIZE]
[SIZE=2]**[B][SIZE=2]_3.7e Test your 3D graphics acceleration and beyond[/SIZE]** [/B]
[/SIZE]**[SIZE=2]3.8 Radeon Tweaks[/SIZE]** 
**[SIZE=2]3.9 Yaboot Config/BusyBox Error[/SIZE]**
**[SIZE=2]3.10 Sound Problems[/SIZE]**
**[SIZE=2]3.11 Trackpad and Right-click[/SIZE]**
**[SIZE=2]3.12 Power Preferences/Suspend[/SIZE]**
**[SIZE=2]3.13 Software Centre[/SIZE]**
**[SIZE=2]3.14 Booting from USB[/SIZE]**
**[SIZE=2]3.15 Security[/SIZE]**
 
[SIZE=3]**4. How To Help PowerPC Ubuntu**[/SIZE]
 
[SIZE=3]**5. Useful Links**[/SIZE]
 
 
[SIZE=3]**1. The Base Installation**[/SIZE]
**[SIZE=2]1.1 Install the CLI[/SIZE]**
Please read all of section 1 before trying to install.
 
As you maybe aware there is currently no ppc Lubuntu cd, but one is in testing for 12.04 [https://wiki.ubuntu.com/Lubuntu/Testing](https://wiki.ubuntu.com/Lubuntu/Testing) .There are also currently no ppc live cds for Ubuntu 11.04 or 11.10 (although copies were available when in testing). One solution is to install a simple command line only system and build up. You can do this via the mini iso (here [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD), where you will find iso's for 11.04 and 11.10) or using the alternate installer (follow the links here [https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)). 
 
You can burn these to a cd (use the lowest possible burn speed) or copy them to an unused usb flash drive and I have given instructions in section 3.14 '*Booting from USB*'. Instructions for net or hard disk booting, as well as, other general information about installing on PowerPC can be found here [https://help.ubuntu.com/11.04/installation-guide/powerpc/index.html](https://help.ubuntu.com/11.04/installation-guide/powerpc/index.html) (though it is a little dated). If you are multibooting then also see [https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot](https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot), as it has some additional information on this.
 
At some point (either when downloading the iso or running the cd) you'll be given a choice between the 32 bit or the 64 bit version. G3s and G4s use the 32 bit version, G5s use the 64 bit.
 
You'll need an ethernet connection to install from the mini iso.
 
Run the 'cd' and ***type "cli" or "cli64" when prompted***. Most of the install questions are fairly easy and straighforward. If you don't know the answer to a question, then you can usually go with the default option. Use Tab and the arrow keys to move between options and Enter to select the option you want. At the partitioning stage, if you want to use the whole disk for Ubuntu (and erase everything currently on the drive) choose the "Guided - use entire disk" option. The only difference I have noticed between the mini and alternate installs is that the mini gives you an automatic update screen. We want the 'No automatic updates' option and I hope this is the default on the alternate install. It's all described in a little bit more detail here [https://help.ubuntu.com/community/Installation/PowerPC](https://help.ubuntu.com/community/Installation/PowerPC) . Choose "cli-expert" if you want a greater level of control or can't get the "cli" option to work.
 
If you are having trouble with mirror repositories then you can use the manual option for setting the mirror and change it to "ports.ubuntu.com" with directory "/ubuntu-ports/". If you have a classic Airport wifi card then during the install you may be told you are missing the non-free firmware file "agere_sta_fw.bin". This can be ignored at this stage. The installer does appear to hang at one point with a black screen, please give it a couple of minutes as the download should kick in. Also, the screensaver (black screen) does come on during the installation just to confuse you more!
 
Following a cli installation and a reboot, if you just get a blank/black/white screen and no login prompt then see section 3.7 '*Screen Resolution/Black Screen/No GUI Problems*'. 
 
I have yet to try the 11.10 installer, but I gather there are problems with it for some computers. This is caused by developments to the ata controller drivers in the kernel: i.e. migrating to the driver pata_macio. There are numerous messages on the Debian powerpc mailing list relating to this. You may get some sort of message telling you that your hard drive has not been recognised. The appropriate module for you maybe missing from the installer, see [http://ubuntuforums.org/showthread.php?t=1898278](http://ubuntuforums.org/showthread.php?t=1898278) .
 
A confirmed workaround to install 11.10 is to initially install a 11.04 cli and upgrade to 11.10 cli. After installing 11.04 cli, login and then use the command "sudo do-release-upgrade -d" to upgrade (omit the -d if you are going from 8.04 LTS to 10.04 LTS). Reboot to make sure it is working correctly with the command "sudo reboot". See section 3.9 '*Yaboot Config/Busybox Error*' if you have a problem on reboot following an upgrade. When you have the 11.10 command line working you can then install a GUI.
 
Note, it is possible to install different desktop environments alongside each other to try them out (and this would be an alternative to starting from a cli install). This is beyond the scope of this post (and you'll want to do some more research for lubuntu), but some instructions which you may find useful are here [http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce) .
 
**[SIZE=2]1.2 G4 iBook and AlBook[/SIZE]**
If you are using a G4 iBook or AlBook then you need to be warned that the fan may not work during the above bit of the installation (it is the same when installing debian). This shouldn't be a problem because it is fairly quick (well around 40 mins), but you could run into overheating issues if you decide to do some CPU intensive thing like shrinking a large partition that's going to take hours! So don't do it! Use a live CD or an existing linux/mac install to do this from. The command that should make sure you have a working iBook and AlBook G4 fan in linux is "sudo modprobe therm_adt746x". This is automated in the file /etc/modules when you install linux. Maverick and natty should add "therm_adt746x" to the list for you, but lucid won't. You can check what you have with the command "sudo nano /etc/modules" (when you are logged in). You'll need to reboot before any changes take effect ("sudo reboot"). It's obviously a good idea to keep a good level of circulation around the *Book, and if you are cautious (sensible?) then during the base installation only you could maybe setup an external fan to blow on the *Book or maybe sit it on something cool (e.g. the freezer things that keep your picnic cool!)?
 
**[SIZE=2]1.3 Other Computers[/SIZE]**
I've only installed *ubuntu on my iBook and I know very little about other models. Please monitor your hardware (such as fans) to make sure it is working correctly.
 
If you have a 'Blue&White' G3 or a 'Yikes!' G4 machine and during the installation of 10.04 or 10.10 you get a message asking you to select a disk drive driver then you may be suffering from this bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/513131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/513131) . You may have to start with an install of 8.04 and upgrade to 10.04 or 10.10. The versions 11.04 and 11.10 have the module pata_cmd64x. See section 3.9 '*Yaboot Config/Busybox Error*' if this causes you problems. 
 
 
[SIZE=3]**2. Install the GUI**[/SIZE]
**[SIZE=2]2.1 Install Lubuntu[/SIZE]**
So now we have the base system installed we can start turning it into lubuntu! Login and we can continue...
 
Lucid (10.04) users can pretty much follow the lubuntu documentation [https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall) . However, I would miss out the line "sudo add-apt-repository ppa:lubuntu-desktop/ppa" at this stage because it won't work with it in. This is because the updated package for the file manager (pcmanfm) is missing for ppc. You could compile this yourself (there are instructions in the 'Workarounds' section below) or possibly download it from elsewhere to get around this. Also, you will still have the apt-xapian-index package which you may find you want to remove (see below). You'll probably also want to install a web browser, as well as, some of the recommended packages for abiword (such as the spell checker) [http://packages.ubuntu.com/lucid/abiword](http://packages.ubuntu.com/lucid/abiword) . 
 
Oneiric (11.10) users should also be able to follow the lubuntu documentation or (hopefully) use the tasksel command (see section 2.2 below) to install.
 
Maverick (10.10) and Natty (11.04) users read on....
 
The following is based on the lubuntu documentation, but it is a little more complicated because of the lubuntu-desktop dependency on the chromium browser. Lubuntu uses chromium as its browser, but there is no ppc chromium/chrome. In lucid and oneiric this dependency has been removed for PowerPC, but in maverick and natty it remains. lubuntu-desktop is just a meta package meaning it is just a collection of packages ([http://packages.ubuntu.com/natty/lubuntu-desktop](http://packages.ubuntu.com/natty/lubuntu-desktop)). My understanding is that installing the individual packages will have the same effect as installing the one big umbrella package. So this is what we have to do minus chromium (and a few others we don't need) and is what the lubuntu developers recommend for PowerPC [https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/718087](https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/718087) . The commands are long so I've written it as a script which you can save and run.
 
The first thing the script does is actually remove a package! This is the apt-xapian-index package which used to cause me a lot of grief with its update-apt-xapi process (surely I am not the only one?). Lubuntu does not have this by default. See the 'Quick search Synaptic' section of [https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/NattyNarwhal](https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/NattyNarwhal) .
 
In the script I've done a rough split between the application packages and the other desktop environment packages. This is so that you can easily remove or replace the applications installed to your own preferences. That's not to say you can't remove packages from the other list either. For example, if you haven't got bluetooth then you can do without gnome-bluetooth. If you are unsure about all this, then just leave it as it is. 
 
Cut and paste the script into a text editor and save it somewhere that you will be able to access from your new lubuntu system. If you copy it to the home directory of your account and it's called "lubuntu-installer" then to make it executable type "chmod +x lubuntu-installer". Run the installer with "sudo ./lubuntu-installer". When it finishes installing type "sudo reboot". You're installed! (You can also type out the commands in the script instead of saving it and running it. The lines starting with a # can be ignored. Linux is case sensitive. Press the up key to repeat the last command typed (usefull if you get an error from a mistype)) 
 
EDIT: If the script doesn't run (shows no output) then this is probably because some non-unix characters have crept in through the cut and paste process. You may need to use the command dos2unix to get rid of the 'MS Windows/dos' characters. Type "sudo apt-get install dos2unix" then e.g. "dos2unix lubuntu-installer".
 
EDIT2: I've added a couple of lines to install the package libx264-98 which is not in natty (we get it from maverick). This allows gecko-mediaplayer and gnome-mplayer to be installed.
 
```
#!/bin/sh
# A script for installing Lubuntu Natty on PowerPC
# ------------------------------------------------
 
sudo apt-get update
 
# This package shouldn't be in the default lubuntu
sudo apt-get purge apt-xapian-index
 
# Not sure if we need this or not, but it's in the lubuntu minimal documentation instructions
sudo apt-get install python-software-properties
 
# The lubuntu desktop environment packages
sudo apt-get install --no-install-recommends alsa-base alsa-utils anacron apport-gtk cron cups-driver-gutenprint desktop-file-utils file-roller gdebi gksu gnome-bluetooth gnome-disk-utility gnome-keyring gnome-power-manager gnome-system-tools gnome-time-admin gvfs-backends gvfs-fuse hardinfo jockey-gtk language-selector-gnome logrotate lubuntu-core lxappearance lxappearance-obconf lxdm lxinput lxkeymap lxlauncher lxpanel-indicator-applet-plugin lxrandr lxsession-edit lxshortcut lxtask lxterminal lzma mobile-broadband-provider-info modemmanager network-manager-gnome ntp obconf pcmciautils pm-utils policykit-desktop-privileges ppp scrot software-properties-gtk synaptic system-config-printer-gnome transmission ttf-indic-fonts-core ttf-kacst-one ttf-khmeros-core ttf-lao ttf-liberation ttf-punjabi-fonts ttf-takao-pgothic ttf-thai-tlwg ttf-ubuntu-font-family ttf-unfonts-core ttf-wqy-microhei ubuntu-extras-keyring unzip update-notifier usb-modeswitch wireless-tools wpasupplicant wvdial x11-utils xdg-user-dirs xscreensaver zip
 
# Get and install a package that is missing from Natty, but is in Maverick so that we can install gnome-mplayer 
wget -P/tmp http://ports.ubuntu.com/ubuntu-ports/pool/universe/x/x264/libx264-98_0.98.1653+git88b90d9-3ubuntu2_powerpc.deb
sudo dpkg -i /tmp/libx264-98_0.98.1653+git88b90d9-3ubuntu2_powerpc.deb
 
# The application packages
sudo apt-get install abiword ace-of-penguins audacious audacious-plugins evince firefox galculator gecko-mediaplayer gnome-mplayer gnumeric gnumeric-doc gpicview gucharmap guvcview leafpad mtpaint osmo pidgin pidgin-libnotify simple-scan sylpheed sylpheed-doc sylpheed-i18n sylpheed-plugins xchat xfburn xpad
 
sudo apt-get dist-upgrade
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove

```**2.2 Install Ubuntu, Xubuntu, Kubuntu, etc**
After installing the base installation and logging in enter the following simple commands:
 
```
sudo apt-get update
sudo tasksel
```Select the version of ubuntu you want from the list that appears. 
 
If for some reason the tasksel command doesn't work (you just get a black screen instead of the list), then first check you are not suffering from the udisks bug described at the top of the 'General Workarounds' section below. An alternative way to install the GUI is to install the appropriate 'meta' package. For xubuntu you would type "sudo apt-get install xubuntu-desktop" followed by the command "sudo apt-get dist-upgrade". If you are having problems with ubuntu-desktop in 11.10 then please see [http://ubuntuforums.org/showpost.php?p=11483024&postcount=11](http://ubuntuforums.org/showpost.php?p=11483024&postcount=11) .
 
When you have rebooted (the command is "sudo reboot") you can tidy up the installation by entering the following commands in a terminal:
```
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove

```Following a reboot, if you remain at a cli login or you have any other graphics issues then see section 3.7 '*Screen Resolution/Black Screen/No GUI Problems*'. 
 
 
[SIZE=3]**3. Workarounds**[/SIZE]
A lot of the following workarounds require the use of the terminal. See [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal) for a guide to this and some common commands. If you are new to linux then typing commands may seem unnatural and scary, but they allow instructions to be written with a greater level of precision and speed. Most of the commands given below can just be cut and pasted into the terminal. Press the Enter/Return key to execute the command. 
 
If you have installed Ubuntu you will have to ***replace the word "leafpad" with the word "gedit"***. If you have installed a version of Xubuntu before 11.10 then you will have to ***replace "leafpad" with "mousepad"***. These changes are necessary because different *ubuntus use different graphical text editors. The command line text editor used in this guide is 'nano'. For some help with this see [https://help.ubuntu.com/community/Nano](https://help.ubuntu.com/community/Nano) .
 
**[SIZE=2]3.1 General Workarounds[/SIZE]**
If you find things are inexplicably slow (or your fan is coming on a lot) then check your CPU usage by running the "top" command from the terminal. The command displays system resources and a list of processes currently being managed by the Linux kernel. If you see "0.0%id" (or a very low number) in the Cpu(s) line then your machine has no spare CPU time. If gvfs-gdu-volume and udisks-daemon are at the top of the processes list then you may be suffering from the udev/udisks bug described in this thread [http://ubuntuforums.org/showthread.php?t=1859152](http://ubuntuforums.org/showthread.php?t=1859152) . The thread also contains some extra xubuntu related fixes. If the process update-apt-xapi is being the CPU hog then you can remove it. See the Lubuntu install section above.
 
If you launch an application which requires root privileges (such as synaptic) and it keeps telling you that the password is incorrect then this is what to do: Open the terminal and type "gksu-properties". Change the authentication mode to 'sudo'. It should now work.
 
If Network Manager reports that your ethernet (wired) connection is un-managed, or you don't see the Network Manager applet icon at all, or your boot time is excessively slow then use the first fix on this page [https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall#Unmanaged_Wired_Network](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall#Unmanaged_Wired_Network) .
 
If the battery status is not displayed correctly then open up the terminal and type "gksudo leafpad /etc/modules". Add the line “pmu_battery”, save and it should work on reboot.
 
To change what the notifications bubble looks like you can open the terminal and type "notification-properties". I suffered from this bug [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/606825](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/606825) so I replaced notification-daemon with notify-osd (used in standard ubuntu). This should be fixed in oneiric.
 
Lubuntu's default screensavers are very CPU intensive so I recommend you change them. I use the gl ant spotlight screensaver to test my xorg.conf settings, but it is very unstable so don't use that everyday if you use your computer for serious work (it almost always freezes the computer when I select the preview button).
 
CD drive related fixes can be found here [http://ubuntuforums.org/showthread.php?t=1817971](http://ubuntuforums.org/showthread.php?t=1817971) .
 
To compile packages [http://ubuntuforums.org/showthread.php?t=1816161](http://ubuntuforums.org/showthread.php?t=1816161) . You may also like to read about backporting [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports) and apt pinning [https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto) .
 
If you don't have a trackpad, but would like your Caps Lock light back, then remove mouseemu ("sudo apt-get remove mouseemu").
 
If you need to adjust the fan limits, then this method [[COLOR=#444444]http://ubuntuforums.org/showthread.php?t=1358034[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1358034") may work (I have never tried this however). Make sure you are using the correct module for your computer first. Some modules are detailed here [http://sensors-applet.sourceforge.net/index.php?content=requirements](http://sensors-applet.sourceforge.net/index.php?content=requirements) .
 
If you want to reduce an oversized live cd [http://ubuntuforums.org/showthread.php?t=1335735](http://ubuntuforums.org/showthread.php?t=1335735) . You can also try 'over-burning' if it is only just too big, or write the iso to a DVD. Remember to use the lowest burn speed for writing to cds. You can also 'burn' an iso to a USB stick see section 3.14 below. 
 
Upon an upgrade if you get a message such as "E: Some index files could not be downloaded, they will be ignored, or old files will be used instead." or a 404 error, then check your sources.list file [http://ubuntuforums.org/showpost.php?p=11266820&postcount=11](http://ubuntuforums.org/showpost.php?p=11266820&postcount=11) .
 
Resetting a computer's PRAM or PMU can fix a number of symptoms (see [http://support.apple.com/kb/HT1379](http://support.apple.com/kb/HT1379) and [http://support.apple.com/kb/HT2183](http://support.apple.com/kb/HT2183)). If you can't boot a CD, your battery level is not correct, or you have video issues then resetting the PRAM/PMU may help. You should use this as a last resort and you may loose yaboot temporarily if you dual boot (see [https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot](https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot)).
 
**[SIZE=2]3.2 Wifi[/SIZE]**
If you have an airport extreme card then you need to download the firmware. Natty and Oneiric users should open the terminal and type "sudo apt-get install firmware-b43-installer" (see [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing_b43_drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing_b43_drivers) if you are having trouble with this). You should now see your wireless networks. Maverick and Lucid users should type "sudo apt-get install b43-fwcutter" in the terminal and then go to Preferences > Additional drivers and select the Broadcom b43 driver. 
 
When you connect to your network you'll be asked to enter a password for the default keyring. I always seem to get in a mess with these, but I think the recommended thing is to enter your account password for this so you don't keep having to enter it. I now make the connection available to all users to get around this. Click on the network applet icon and select 'Edit Connections...'. Go to the Wireless tab and select your network from the list. Click "Edit...". Enter your Ubuntu user account password if prompted. Make sure "Connect automatically" and "Available to all users" are ticked. Click Apply and then Close. If in the future you need to delete the keyring this is how: Open File Manager, click 'View' and select 'Show Hidden'. Double-click on .gnome2 and then keyrings. Delete the appropriate file.
 
If you have an airport classic card or airport extreme card and are suffering from bad password errors (or you require more troubleshooting advice) then have a look here [http://ubuntuforums.org/showthread.php?t=1705143](http://ubuntuforums.org/showthread.php?t=1705143) . In lubuntu natty I've found you don't need to check the privileges so you can probably skip that part for natty.
 
**[SIZE=2]3.3 CPU Frequency Scaling[/SIZE]**
CPU scaling reduces the processor speed when the computer is idle or not doing a lot. It saves battery power and reduces heat so you won't have the fan coming on so much. However, the 'ondemand' kernel governor for processor scaling does not work with G3 and G4 processors because a sensible value for the transition latency (the time taken to switch between processor speeds) has not been set in the kernel. To overcome this, I use the powernowd package to perform the same function as the ondemand governor on my G4. 
 
Unfortunately, powernowd has been removed from natty because somebody deemed it to be redundant. So it is another package that we have to manually download from here [http://ports.ubuntu.com/ubuntu-ports/pool/universe/p/powernowd/powernowd_1.00-1ubuntu5_powerpc.deb](http://ports.ubuntu.com/ubuntu-ports/pool/universe/p/powernowd/powernowd_1.00-1ubuntu5_powerpc.deb) . Save the file and use the command "sudo dpkg -i path_to_file" to install the package (where path_to_file will be something like ~/Downloads/powernowd_1.00-1ubuntu5_powerpc.deb). Then all you have to do is disable the ondemand governor being turned on by using the command "sudo update-rc.d ondemand disable". The Power PC Known Issues pages [https://wiki.ubuntu.com/PowerPCKnownIssues#Ubuntu_10.04_Lucid_Lynx](https://wiki.ubuntu.com/PowerPCKnownIssues#Ubuntu_10.04_Lucid_Lynx) advices you do other stuff, but I have found the extra instructions to be unnecessary. Finally, the file /etc/default/powernowd contains the startup options which you may like to adjust (if you know what you are doing because you don't want to set the polling interval too small). More information about powernowd can be found here [http://www.deater.net/john/powernowd.html](http://www.deater.net/john/powernowd.html) . 
 
Note, processor scaling is not available in linux for all PowerPC processors. Also, you may have to reinstall powernowd after an upgrade as it is likely to be automatically uninstalled.
 
**[SIZE=2]3.4 Multimedia[/SIZE]** 
The script leaves you with a system as if you have installed it from an official CD. However, this is probably not the end of what you want to do because there are packages that cannot be included into the Lubuntu/Ubuntu distribution for legal reasons (copyright, license, patent, etc). It is easy to install these however, this is how:
 
Open the terminal and type "sudo apt-get install ubuntu-restricted-extras". This will download a whole load of stuff (around 100MB) including codecs, Mircrosoft fonts, gnash (flash support), and openjdk (java). A license aggreement screen pops up for the MS fonts which you will need to accept (press the TAB key if you are having a hard time selecting the OK option).
 
To play encrypted DVDs you need to dowload a file from Medibuntu (Multimedia, Entertainment & Distractions In Ubuntu [http://www.medibuntu.org/](http://www.medibuntu.org/)). You can nolonger add medibuntu as a repository on PowerPC, but you can still download the files individually. Click on the link [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_powerpc.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_powerpc.deb) and select open with GDebi to install.
 
If you are still having problems with DVDs then check out the "Setting DVD Region Codes" section of [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) . This is what I had to do to get my DVD drive to work. When I ran regionset the 'type' showed up as NONE and I had to set the region to make it show SET.
 
More codecs can be downloaded from Medibuntu. The file is pretty old so I'm not sure what it adds that ubuntu-restricted-extras doesn't, but you can install it by clicking [http://packages.medibuntu.org/pool/non-free/p/ppc-codecs/ppc-codecs_20071007-0medibuntu1_powerpc.deb](http://packages.medibuntu.org/pool/non-free/p/ppc-codecs/ppc-codecs_20071007-0medibuntu1_powerpc.deb) and select open with GDebi. Lucid users should follow the advice in this thread [http://ubuntuforums.org/showthread.php?t=1385579](http://ubuntuforums.org/showthread.php?t=1385579) .
 
I couldn't get gecko-mediaplayer in Lubuntu to work with Firefox 5 so I installed totem instead. Gecko-mediaplayer is a plugin that allows Firefox to play videos and audio using gnome-mplayer. Totem is another mediaplayer with its own firefox plugin (it is the default player on normal Ubuntu). Gnome-mplayer is the better at playing DVDs and usually has lower CPU usage when playing videos, but occasionally totem can do something that gnome-mplayer can't. It's annoying to have two applications doing the same job (it feels like a bodge to my perfectionist mindset), but I can't get around it. Totem can play YouTube videos directly and there are country specific plugins for it that allow you to watch TV shows (you will have to do a search for these and install them).
 
To install totem movie player in lubuntu type at a terminal "sudo apt-get --no-install-recommends install totem gstreamer0.10-alsa totem-plugins gnome-codec-install". If you want to replace gecko-mediaplayer with the totem firefox plugin then type "sudo apt-get remove gecko-mediaplayer" followed by "sudo apt-get --no-install-recommends install totem-mozilla". 
 
The uber minimalist way to watch media is using the command line program mplayer. You can even use this without a GUI! See [http://askubuntu.com/questions/46871/how-can-i-play-videos-in-a-framebuffer](http://askubuntu.com/questions/46871/how-can-i-play-videos-in-a-framebuffer) . To play music the cool people use MPD [http://en.wikipedia.org/wiki/Music_Player_Daemon](http://en.wikipedia.org/wiki/Music_Player_Daemon) . MPC is a simple command line client for this, although you can use a web browser or mobile phone too!
 
**[SIZE=2]3.5 Flash[/SIZE]** 
There is *no* Adobe Flash for PowerPC. There are, however, two open source flash players still under development: gnash and lightspark.
 
From the Software Centre/Synaptic/Terminal install "Gnash SWF viewer" and "browser-plugin-gnash" (or "mozilla-plugin-gnash" depending on your ubuntu version). Lightspark (and it's firefox plugin browser-plugin-lightspark) is the latest flash player (see [http://lightspark.github.com/](http://lightspark.github.com/) and [http://allievi.sssup.it/techblog/](http://allievi.sssup.it/techblog/) ). Lightspark uses advanced OpenGL techniques that requires good support from video drivers. It will work best in newer versions of ubuntu (and with KMS on? see section 3.7b). Lightspark also uses pulseaudio as it's default audio backend. Pulseaudio is not installed on a default Lubuntu installation, so if you want sound you will have to install it (or compile a version of lightspark with alsa as the audio backend?). You can install gnash and lightspark alongside each other since lightspark likes to 'fallback' onto gnash to play old swf files, but don't enable both the gnash firefox plugin and the lightspark plugin at the same time. 
 
You may want install a browser extension that blocks flash content on websites because gnash CPU usage is high even for simple adverts. I hate my laptop fan coming on so I try to run my iBook as cool as possible at all times. Even if you haven't got gnash installed you will probably benefit from faster browsing by using an extension such as Ablock Plus (see [https://addons.mozilla.org/en-US/firefox/addon/adblock-plus/](https://addons.mozilla.org/en-US/firefox/addon/adblock-plus/) ). 
 
If you want to experiment with gnash in 11.10 (particularly if you are running other architectures with the adobe plugin) then you may have to run the command "sudo update-alternatives --config mozilla-flashplugin" and select the "/usr/lib/gnash/libgnashplugin.so" option. Lightspark does not appear in the list because it goes under the name of "flash-mozilla.so". Run "update-alternatives --query flash-mozilla.so" to check. This allows you to easily switch plugins in Firefox (goto Tools > Add-ons > Plugins and enable/disable plugins as required), but it means Lightspark will not be picked up in Midori (which handles plugins in a completely random way it seems to me) . However, as far as I can tell Lightspark does not work with Midori anyway because it uses Webkit and not Gecko. Gnash works with Midori, or to put it more precisely, adverts work, but strangely videos don't work even when they work in firefox with gnash. 
 
If you want to do debugging run the browser from the terminal. You can set the verbosity of gnash through right clicking on a flash object in the browser and selecting the Edit > Preferences menu entry. Use "firefox -verbose" to see the messages from the lightspark plugin. See [http://sourceforge.net/apps/trac/lightspark/wiki/Troubleshooting](http://sourceforge.net/apps/trac/lightspark/wiki/Troubleshooting) . To test the lightspark standalone player use the commands:
 
```

wget http://www.adobe.com/content/dotcom/en/devnet/flash/samples/drawing_1/_jcr_content/articlecontentAdobe/generic/file.res/1_coordinates[1].swf
lightspark 1_coordinates[1].swf

```You should see a disk spinning that you can move around with your mouse. It is the least impressive demonstration ever!
 
This thread offers more advice on watching YouTube, Vimeo, etc [http://ubuntuforums.org/showthread.php?t=1709156](http://ubuntuforums.org/showthread.php?t=1709156) . I like the firefox extension FlashVideoReplacer ([https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/](https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/)) since it allows you to watch YouTube videos 'normally'. Others may prefer minitube or Totem. 
 
Another way to watch YouTube etc is by using html 5 ([http://www.youtube.com/html5](http://www.youtube.com/html5)). This works quite well for videos coded in H.264. You'll need Midori or Epiphany browsers for H.264, but for YouTube most videos are delivered in WebM (unless you spoof it, see below). WebM can be played in Firefox 4 and beyond, Opera, Midori and Epiphany, but for me the playback is choppy (similar to gnash), although I think Firefox may improve with every new release. Vimeo uses H.264 to deliver html5 video clips.
 
To download and watch BBC Iplayer programmes there is get-iplayer. 
 
I've also recently started watching/listening to streams by finding the rtmp address used by the flash application. This youtube video [http://www.youtube.com/watch?v=8PuUnQCS7DQ](http://www.youtube.com/watch?v=8PuUnQCS7DQ) describes how to use wireshark to do this, but there are other ways which you can find by doing a search. I find wireshark quite addictive and find myself trying to crack the rtmp address even if I don't have to! You can download a stream using rtmpdump, or pipe the output to a media player, but gnome-mplayer will also accept the rtmp addresss directly in the 'Open location' menu item.
 
You can also change the user agent string of your browser so that you are delivered non-flash content. There is a firefox extension to do this [https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/](https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/), but it is probably best to use Midori to spoof an iPad/iPhone since they use H.264 to play video clips and Firefox cannot play H.264. Midori works really well on some news web sites and allows you to watch video clips that would be otherwise unwatchable. In Midori goto Edit > Preferences > Identify as > Custom... Copy and paste one of the following strings in:
 
```

Mozilla/5.0 (iPad; U; CPU OS 3_2 like Mac OS X; en-us) AppleWebKit/531.21.10 (KHTML, like Gecko) Version/4.0.4 Mobile/7B334b Safari/531.21.10
 
Mozilla/5.0 (iPad; U; CPU OS 4_3_1 like Mac OS X; en-us) AppleWebKit/533.17.9 (KHTML, like Gecko) Version/5.0.2 Mobile/8G4 Safari/6533.18.5
 
Mozilla/5.0 (iPhone; U; CPU iPhone OS 3_1_2 like Mac OS X; en-us) AppleWebKit/528.18 (KHTML, like Gecko) Version/4.0 Mobile/7D11 Safari/528.16

```Remember there is plenty of choice out there. Don't get hung up on the website that you can't use, but instead support the websites you can access. If you want GoogleEarth then try [http://www.bing.com/maps/](http://www.bing.com/maps/) as a substitute. There are ways of using Google Street View on PowerPC, see [http://ubuntuforums.org/showthread.php?t=1896625](http://ubuntuforums.org/showthread.php?t=1896625) . 
 
**[SIZE=2]3.6 Java[/SIZE]**
I don't use Java myself and even disable the plugin for security (there are firefox extensions you can use to automate this), but here is some info about Java....
 
If you want faster Java than openjdk then there is IBM Java [http://www.ibm.com/developerworks/java/jdk/index.html](http://www.ibm.com/developerworks/java/jdk/index.html) . You have to register to download, but all you have to give is an email address so nothing too taxing. There are old deb packages in medibuntu.
 
You could also try Java Virtual Machines such as Cacao and JamVM. The author of JamVM says of PowerPc "for many years my main platform, so this is well tested. Built and tested on G3 and G4 systems". In Natty and Oneiric there is a package ([http://packages.ubuntu.com/natty/icedtea-6-jre-jamvm](http://packages.ubuntu.com/natty/icedtea-6-jre-jamvm)) available for other architectures (so the source code is readily available), but I believe it doesn't exist for PowerPC (possible bug?)? See [http://jamvm.sourceforge.net/](http://jamvm.sourceforge.net/) and [http://draenog.blogspot.com/2011/02/...epository.html]("http://draenog.blogspot.com/2011/02/openjdkjamvm-git-repository.html") for more information:
 
> 
The easiest way to test the port is to build JamVM, and copy the libjvm.so file into an existing IcedTea/OpenJDK installation.
After cloning the git repository, do:
./autogen.sh --with-java-runtime-library=openjdk
This will generate the autoconf/automake files and configure JamVM to build support for OpenJDK.
Then do make, make install as usual. This will put libjvm.so into /usr/local/jamvm/lib.
This can then be copied onto an existing IcedTea installation (or a copy of one), e.g. on x86_64 (as root):
cd /usr/lib/jvm
cp -r java-6-openjdk jamvm-openjdk
cp /usr/local/jamvm/lib/libjvm.so jamvm-openjdk/jre/lib/amd64/server
For Cacao see _[http://packages.ubuntu.com/natty/icedtea-6-jre-cacao](http://packages.ubuntu.com/natty/icedtea-6-jre-cacao)_ . "The package provides an alternative runtime using the Cacao VM and the Cacao Just In Time Compiler (JIT). This is a somewhat faster alternative than the Zero port on architectures like alpha, armel, m68k, mips, mipsel, powerpc and s390." 
 
See the file /usr/lib/jvm/java-6-openjdk/docs/README.Debian and the other documents in that directory for information about how to use the alternative virtual machines. Note, the IcedTea Firefox plugin will use the default VM (which you can set). Technical detail about the IcedTea plugin can be found here [http://icedtea.classpath.org/wiki/IcedTea-Web](http://icedtea.classpath.org/wiki/IcedTea-Web) . 
 
Some general stuff about Java in Ubuntu [http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html) . Note, there is no oracle/sun java for powerpc linux.
 
**[SIZE=2]3.7 Screen Resolution/Black Screen/No GUI Problems[/SIZE]** 
**[SIZE=2]3.7a General notes on display issues[/SIZE]**
This is a massively daunting problem when you are new to linux/ubuntu. The key is not to panic, but take a methodical approach. Read the information below and if necessary the links. If you don't understand it then please ask. It is silly to suffer in silence.
 
Do a quick check of your hardware! Make sure that your video cables are plugged in correctly and also try them in different sockets! Ubuntu may be outputting on a different port to that which you normally use.
 
If you are at a 'Busybox' prompt or don't see a yaboot prompt at all then see section 3.9 '*Yaboot Config/Busybox Error*' below.
 
If you are trying a Lubuntu live cd then first check out the release notes which are linked at the bottom of this post.
 
If you are using the 'Unity' interface in 11.04 and are seeing awful colours, then this is a known problem with the unity-2d package and is not a graphics problem. See the 'General Workarounds' section to compile a newer version of unity-2d or upgrade to 11.10. The 'Classic' session (which you can select if you log out [http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)) is not affected by this problem. If you have awful colours in 11.10, then log out and try the Ubuntu 2D session!
 
If you think that fonts are blurred or not being displayed correctly then your monitor may not have the standard RGB sub pixel order. There is an option to change this. In standard Ubuntu goto System > Preferences > Appearance > Fonts > Details. You can also do it via an xorg.conf (see below).
 
Unfortunately, there are quite a few problems with essentially the same symptom - a blank screen. So it is a case of trial and error to see what works. There are broadly two approaches to solving the blank screen: adding a yaboot parameter and setting up an xorg.conf file. The yaboot parameter (see section 3.7b) could be seen as the "quick fix" approach, good to get something at least on the screen (e.g. a cli login or a simple graphics setup), but often you may need to make it permanent too. An xorg.conf file (see section 3.7c) gives greater control of your graphics setup and is used, for example, to adjust a bad resolution or when you can't get beyond a cli login. Increasingly, an xorg.conf file is not needed in new versions of ubuntu.
 
As strange as it may seem, on some computers (***not all*** - it could be the 'nv' driver?) if the date is set far back in the past (because of a flat internal battery) then you may get a blank screen. You can use yaboot parameters to temporarily overcome this, but the best permanent solution maybe to buy a replacement battery? More feedback is needed on this. My iBook with a radeon card has no problem with being back in the 1970s!
 
Note, Ubuntu evolves with every new release and yaboot parameters you may need for one release may not be required for the next release. To take advantage of improvements you should retest your graphics setup after an upgrade.
 
**[SIZE=2]3.7b Yaboot parameters for screen problems[/SIZE]** 
The first two yaboot parameters to try are "video=ofonly" (use only the openfirmware framebuffer - offb) and "nosplash" (disables on **some** computers the ubuntu splash screen i.e. the word ubuntu with the four dots). You add them after whatever you normally type at the second yaboot prompt. It is best to try all yaboot parameters separately first, but if you want to try them together, and you normally type "Linux" then you would type at the second yaboot prompt:
 
```

Linux nosplash video=ofonly 

```If these don't work, you can try further boot parameters, but these will depend on what graphics card you have. If you don't know what you have, you can look up your computer here [http://support.apple.com/specs/](http://support.apple.com/specs/) or here [http://www.everymac.com/](http://www.everymac.com/) . 
 
Modern open-source radeon and nouveau (nVidia cards) video drivers rely on kernel modesetting (KMS). KMS supposedly provides an improved graphical boot with less flickering, a built-in framebuffer console, seamless switching from the console to Xorg, and other features. To achieve this, KMS moves the responsibility for selecting and setting up the graphics mode from the Xorg to the kernel. See [https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting).
 
KMS can be problematic, however, so you can test if your computer will boot correctly without it. For nVidia cards use the yaboot parameter "nouveau.modeset=0" to disable KMS (see [https://wiki.ubuntu.com/X/Troubleshooting/Nouveau#Disabling_nouveau](https://wiki.ubuntu.com/X/Troubleshooting/Nouveau#Disabling_nouveau)). Please note, PPC ubuntu does not use grub/grub2 so disregard any instructions in the links relating to grub menus. For radeon cards use "radeon.modeset=0". See section 3.8 for more information about radeon settings. 
 
KMS conflicts with legacy framebuffer drivers (such as, radeonfb, nvidiafb, rivafb), so you should disable these if you want to try KMS. nvidiafb and rivafb which are the old framebuffers for nvidia cards are not 'complied in' to recent ubuntu kernels (and their modules are blacklisted) so they shouldn't cause a problem. radeonfb, aty128fb, and atyfb are, however, 'compiled in' to 10.04 and 10.10 kernels. radeonfb will stop radeon KMS working so you should disable it with the yaboot parameter [noparse]"video=radeonfb:off"[/noparse]. 
 
To force a nouveau mode (e.g. to enable a dvi connector and disable a non-existent tv out) see the bottom of [http://nouveau.freedesktop.org/wiki/KernelModeSetting](http://nouveau.freedesktop.org/wiki/KernelModeSetting) . This may solve problems with some nVidia cards? Gentoo have more on phantom outputs [http://en.gentoo-wiki.com/wiki/Nouveau](http://en.gentoo-wiki.com/wiki/Nouveau) .
 
You can force the mode of framebuffers aty128fb (ATI Rage 128 cards) and atyfb (Mach 64 and Rage cards) too, for example: "video=aty128fb:1024x768-24@75". See the bottom of [http://cgit.freedesktop.org/nouveau/linux-2.6/tree/Documentation/fb/modedb.txt](http://cgit.freedesktop.org/nouveau/linux-2.6/tree/Documentation/fb/modedb.txt) . The official guide suggests a different way, see the bottom of this page [https://help.ubuntu.com/11.04/installation-guide/powerpc/ch05s01.html](https://help.ubuntu.com/11.04/installation-guide/powerpc/ch05s01.html) . I struggled to find information on vmodes/cmodes, so I'm not sure if that is old fashioned (something to do with MacOS?), but there is quite a good guide here [http://www.jonh.net/lppcfom-serve/cache/1043.html](http://www.jonh.net/lppcfom-serve/cache/1043.html) . You will probably have to perform extra steps to use these framebuffers in 11.04 and 11.10. See section 3.7d below.
 
You can additionally try [noparse]"video=offb:off"[/noparse]. This will disable the openfirmware framebuffer and is used when offb conflicts with another framebuffer (see log files syslog/dmesg in directory /var/log/). If no other framebuffer is available at boot time then you may get a frozen or blank screen until the Xorg server starts. 
 
For background information on framebuffers see [https://wiki.ubuntu.com/FrameBuffer](https://wiki.ubuntu.com/FrameBuffer) , but again you'll have to filter out any details relating to grub as PowerPC does not use this. It describes adding "nofb" to the kernel line and you could try this as a yaboot parameter too? It also gives some information about the command fbset. This allows you to show or change framebuffer settings from the console [http://manpages.ubuntu.com/manpages/natty/man1/fbset.1.html](http://manpages.ubuntu.com/manpages/natty/man1/fbset.1.html) .
 
Note, yaboot parameters don't always work with the live cds, but you will still be able to install using the alternate or mini cds. If you do install from a live cd and you've used a yaboot parameter then that parameter should be automatically passed onto the install. 
 
To make a yaboot parameter permanent or remove a parameter from an installation, use the command "sudo nano /etc/yaboot.conf" and change the 'append' lines in the file. Add the desired parameter into the quotes, or remove the word 'splash' if you want to disable the splash screen. Every parameter inside the quotes should be separated by a space. Save (ctrl+o) and exit (ctrl+x), then type the command "sudo ybin -v" to copy the file across to the boot partition.
 
**[SIZE=2]3.7c Configuring an xorg.conf file[/SIZE]** 
If you have a distorted picture, a poor resolution, poor colours or can't boot past a command line login then you may need to setup an xorg.conf file....
 
The lubuntu FAQ gives some basic information on this [https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Workarounds#Screen_resolution_is_wrong.2C_no_matter_what_I_do.21.21](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Workarounds#Screen_resolution_is_wrong.2C_no_matter_what_I_do.21.21) . For a more comprehensive guide have a look here [https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config) or the xorg.conf manual [http://manpages.ubuntu.com/manpages/natty/en/man5/xorg.conf.5.html](http://manpages.ubuntu.com/manpages/natty/en/man5/xorg.conf.5.html) .
 
The information below this point ***only applies if you have installed a GUI***.
 
To setup an xorg.file you may find it more convenient (for example, if your picture is bad or black) to boot into single user mode. At the second yaboot prompt type "Linux single" (if this doesn't work then you may need to combine it with one or more of the other yaboot parameters above). This will boot into a menu (or take you straight to a root prompt). Choose 'continue boot' to take you into a command line login or you can choose one of the root options at the bottom of the menu list (in which case you can remove the word 'sudo' from the commands you type). 
 
Sample xorg.files for various machines can be found here [http://mac.linux.be/content/xorgconf-files](http://mac.linux.be/content/xorgconf-files) . These can save you reading all the documentation, but some of them are not the best setup (that's me being polite!). Download the file using the wget command at the bottom of the appropriate page. Then move it using the command "sudo mv file_name /etc/X11/xorg.conf" where file_name will be something like "ibook2.txt". Reboot using "sudo reboot".
 
It is not hard though to setup your own xorg.conf file, and if you have an external monitor then I would recommend you do so. Some instructions for setting up an xorg.conf and detecting your monitor resolutions are below:
 
Get to a console, for example via single user mode. Then type:
 
```
sudo Xorg -configure
sudo mv xorg.conf.new /etc/X11/xorg.conf
sudo nano /etc/X11/xorg.conf
```Note the capital 'X' in "sudo Xorg -configure". Also, you can probably ignore any errors from the command, such as "number of created screens does not match number of detected devices", as it will still generate an xorg.conf file. It just means you will have to delete some sections of the xorg.conf.
 
At this point you may be freaking out a bit because it does look complicated when you are new to this sort of thing! However, once you overcome your panic and approach it more with a “can do” attitude you’ll see it is not so hard.
 
An xorg.conf file is composed of a number of sections which may be present in any order. Each section has the form: 
 
```

Section "SectionName"
     SectionEntry
     ...
EndSection

```To solve graphics problems we are mainly interested in the "Monitor", "Device" and "Screen" sections. Assuming you have a standard single monitor setup, then you probably only want 1 of each of these sections so you may have to delete some sections if it gives you two (natty did this to me). If this is the case, examine the two “Device” sections and look at the Driver section entry. If you have an Apple computer then the section you want to keep will have radeon, ati, r128, nouveau or nv written in the Driver entry (what is written depends on your graphics card). There are *no* proprietary (non-free) drivers for ppc. Above the Driver entry will be the Identifier entry. This is a unique name given to the graphics device and will probably be something like “Card0”. 
 
(Note, if you are using the yaboot parameter "nouveau.modeset=0" then you want "nv" written in the Driver entry instead of "nouveau". Ammend the xorg.conf accordingly. "nv" is the old driver for nvidia cards.)
 
The “Monitor” and “Screen” sections also have Identifier entries. The “Screen” section has entries to reference the “Monitor” and “Device” sections as it's purpose is to bind the monitor to a graphics card. You want to keep the “Screen” section that references the identifier of the “Device” section that you are keeping. It will probably work out that you are keeping the sections “Card0”, “Monitor0” and “Screen0”. 
 
The highest level section is the “ServerLayout” section. When you delete sections you will have to change the “ServerLayout” section to reflect any changes. A shortened xorg.conf using r128 may look something like the one below. For clarity, the font and input device sections have been deleted which you can also safely do (if you are happy with their automatic setup). Note, the lines starting # are comments and don't do anything.
 
```
[COLOR=#222222]Section "ServerLayout"[/COLOR]
     [COLOR=#222222]Identifier     "X.org Configured"[/COLOR]
     [COLOR=#222222]Screen         "Screen0"[/COLOR]
[COLOR=#222222]EndSection[/COLOR]
 
[COLOR=#222222]Section "Monitor"[/COLOR]
     [COLOR=#222222]Identifier   "Monitor0"[/COLOR]
     [COLOR=#222222]VendorName   "Monitor Vendor"[/COLOR]
     [COLOR=#222222]ModelName    "Monitor Model"[/COLOR]
[COLOR=#222222]EndSection[/COLOR]
 
[COLOR=#222222]Section "Device"[/COLOR]
     [COLOR=#222222]### Available Driver options are:-[/COLOR]
     [COLOR=#222222]### Values: <i>: integer, <f>: float, <bool>: "True"/"False",[/COLOR]
     [COLOR=#222222]### <string>: "String", <freq>: "<f> Hz/kHz/MHz",[/COLOR]
     [COLOR=#222222]### <percent>: "<f>%"[/COLOR]
     [COLOR=#222222]### [arg]: arg optional[/COLOR]
     [COLOR=#222222]#Option     "NoAccel"               # [<bool>][/COLOR]
     [COLOR=#222222]#Option     "SWcursor"              # [<bool>][/COLOR]
     [COLOR=#222222]#Option     "Dac6Bit"               # [<bool>][/COLOR]
     [COLOR=#222222]#Option     "Dac8Bit"               # [<bool>][/COLOR]
     [COLOR=#222222]#Option     "DMAForXv"              # [<bool>][/COLOR]
     [COLOR=#222222]#Option     "ForcePCIMode"          # [<bool>][/COLOR]
     [COLOR=#222222]#Option     "CCEPIOMode"            # [<bool>][/COLOR]
     [COLOR=#222222]#Option     "CCENoSecurity"         # [<bool>][/COLOR]
     [COLOR=#222222]#Option     "CCEusecTimeout"        # <i>[/COLOR]
     [COLOR=#222222]#Option     "AGPMode"               # <i>[/COLOR]
     [COLOR=#222222]#Option     "AGPSize"               # <i>[/COLOR]
     [COLOR=#222222]#Option     "RingSize"              # <i>[/COLOR]
     [COLOR=#222222]#Option     "BufferSize"            # <i>[/COLOR]
     [COLOR=#222222]#Option     "EnablePageFlip"        # [<bool>][/COLOR]
     [COLOR=#222222]#Option     "Display"               # <str>[/COLOR]
     [COLOR=#222222]#Option     "PanelWidth"            # <i>[/COLOR]
     [COLOR=#222222]#Option     "PanelHeight"           # <i>[/COLOR]
     [COLOR=#222222]#Option     "ProgramFPRegs"         # [<bool>][/COLOR]
     [COLOR=#222222]#Option     "UseFBDev"              # [<bool>][/COLOR]
     [COLOR=#222222]#Option     "VideoKey"              # <i>[/COLOR]
     [COLOR=#222222]#Option     "ShowCache"             # [<bool>][/COLOR]
     [COLOR=#222222]#Option     "VGAAccess"             # [<bool>][/COLOR]
     [COLOR=#222222]Identifier  "Card0"[/COLOR]
     [COLOR=#222222]Driver      "r128"[/COLOR]
     [COLOR=#222222]BusID       "PCI:0:16:0"[/COLOR]
[COLOR=#222222]EndSection[/COLOR]
 
[COLOR=#222222]Section "Screen"[/COLOR]
     [COLOR=#222222]Identifier "Screen0"[/COLOR]
     [COLOR=#222222]Device     "Card0"[/COLOR]
     [COLOR=#222222]Monitor    "Monitor0"[/COLOR]
     [COLOR=#222222]SubSection "Display"[/COLOR]
          [COLOR=#222222]Viewport   0 0[/COLOR]
          [COLOR=#222222]Depth     1[/COLOR]
     [COLOR=#222222]EndSubSection[/COLOR]
     [COLOR=#222222]SubSection "Display"[/COLOR]
          [COLOR=#222222]Viewport   0 0[/COLOR]
          [COLOR=#222222]Depth     4[/COLOR]
     [COLOR=#222222]EndSubSection[/COLOR]
     [COLOR=#222222]SubSection "Display"[/COLOR]
          [COLOR=#222222]Viewport   0 0[/COLOR]
          [COLOR=#222222]Depth     8[/COLOR]
     [COLOR=#222222]EndSubSection[/COLOR]
     [COLOR=#222222]SubSection "Display"[/COLOR]
          [COLOR=#222222]Viewport   0 0[/COLOR]
          [COLOR=#222222]Depth     15[/COLOR]
     [COLOR=#222222]EndSubSection[/COLOR]
     [COLOR=#222222]SubSection "Display"[/COLOR]
          [COLOR=#222222]Viewport   0 0[/COLOR]
          [COLOR=#222222]Depth     16[/COLOR]
     [COLOR=#222222]EndSubSection[/COLOR]
     [COLOR=#222222]SubSection "Display"[/COLOR]
          [COLOR=#222222]Viewport   0 0[/COLOR]
          [COLOR=#222222]Depth     24[/COLOR]
     [COLOR=#222222]EndSubSection[/COLOR]
[COLOR=#222222]EndSection[/COLOR]

```Save, exit and reboot (type the command "sudo reboot") to see if it is working. You may have to do some more alterations, but these will change depending on your symptons and the xorg log (type "nano /var/log/Xorg.0.log" to look at it). Use the markers to quickly trace problems in the log:
 
> 
Markers: 
(--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
A description of some errors can be found here [http://www.x.org/wiki/FAQErrorMessages](http://www.x.org/wiki/FAQErrorMessages) . There are a lot of warning messages at the start so it may be easier to start at the bottom of the log and work up. Messages about fonts can just be ignored. Don't worry about an "Invalid ROM contents", "Failed to read PCI ROM!", or "Video BIOS not found!" message, they sound scary, but are normal (although there is probably a setting you can tweak to turn them off). 
 
If you get the error '(EE) Failed to load module "nv" (module does not exist, 0)', then you need to install the package xserver-xorg-video-nv. In 11.10 you may have to compile it as it is not in the repository ([https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+question/177231](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+question/177231)). Compile instructions are in this post [http://ubuntuforums.org/showpost.php?p=11493049&postcount=27](http://ubuntuforums.org/showpost.php?p=11493049&postcount=27) . Please try using the newer "nouveau" driver first.
 
If you see the following combination of errors
 
```

(EE) Unable to find a valid framebuffer device
(EE) R128(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
...
(EE) Screen(s) found, but none have a usable configuration.

```then it is likely you are using the openfirmware framebuffer with a ATI Rage 128 card. You should specify the correct framebuffer with a yaboot parameter (e.g. video=aty128fb) or disable the openfirmware framebuffer. See section 3.7b above. If you are using 11.04 or 11.10 then you will have to load the aty128fb kernel module first (see section 3.7d below). You may still have to make changes to your monitor section (see below). An alternative "fix" for the framebuffer error can be done through the xorg.conf, although it has been commented that this solution is inferior ([COLOR=#222222]see thread [/COLOR][[COLOR=#000000]http://ubuntuforums.org/showthread.php?t=1888881[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1888881")[COLOR=#000000])[/COLOR]. The alternate fix is to set [COLOR=#222222]Option "UseFBDev" "False" and possibly also [/COLOR]Option "NoInt10" "True" [COLOR=#222222]:[/COLOR]
 
```

[COLOR=#222222]Section "Device"[/COLOR]
     [COLOR=#222222]Identifier "Card0"[/COLOR]
     [COLOR=#222222]Driver "r128"[/COLOR]
     [COLOR=#222222]BusID "PCI:0:16:0"[/COLOR]
 
     [COLOR=#222222]Option "UseFBDev" "False"[/COLOR]
     [COLOR=#222222][COLOR=#222222]O[/COLOR][/COLOR][COLOR=#000000]ption "NoInt10" "True"           #you can also put this is the Screen section[/COLOR]
[COLOR=#222222]EndSection[/COLOR]

``` 
If your resolutions have been incorrectly detected (out of range message in the Xorg.0.log or displays incorrectly on the monitor), then you can use the cvt command to find your monitor setting for the resolution you want. You can then add a modeline into the "Monitor" section using the output from the cvt command. You can add as many resolutions/modelines as you like.
 
e.g. typing the following command for the resolution 800x600:
 
```
cvt 800 600
```gives the following output on *my* iBook:
 
# 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz 
Modeline "800x600_60.00" 38.25 800 832 912 1024 600 603 607 624 -hsync +vsync
 
Make a note of the modeline, open the xorg.conf again and copy the modeline into whatever "Monitor" section you have (add/uncomment the preferred mode bit if you want to set that): e.g.
 
```

[COLOR=#222222]Section "Monitor"[/COLOR]
     [COLOR=#222222]Identifier "Monitor0"[/COLOR]
     [COLOR=#222222]VendorName "Monitor Vendor"[/COLOR]
     [COLOR=#222222]ModelName "Monitor Model"[/COLOR]
 
     [COLOR=#222222]Modeline "800x600_60.00" 38.25 800 832 912 1024 600 603 607 624 -hsync +vsync[/COLOR]
     [COLOR=#222222]#Option "PreferredMode" "800x600_60.00"[/COLOR]
[COLOR=#222222]EndSection[/COLOR]

```You will get different numbers when you run the cvt command as modelines are monitor specific. The "800x600_60.00" is the identifier/name of the mode. You must use this exactly whenever you refer to the mode in the xorg.conf (for example in the "Screen" section). You often see people shorten the name to "800x600" in which case it overrides the built-in mode. For example:
 
```

     Modeline "1024x768"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
     [COLOR=#222222]Modeline "800x600"   38.25 800 832 912 1024 600 603 607 624 -hsync +vsync[/COLOR]
     Modeline "640x480"   23.75  640 664 720 800  480 483 487 500 -hsync +vsync
     [COLOR=#222222]Option "PreferredMode" "1024x768"[/COLOR]

```You may also have to adjust your "Screen" section, but hopefully the resolution(s) should be picked up automatically and you won't have to do this. An example "Screen" section where modes have been explicitly stated is below:
 
```

Section "Screen"
     Identifier "Screen0"
     Device     "Card0"
     Monitor    "Monitor0"
 
     DefaultDepth 24
 
     # 1024x760 will be the default mode because it is first in the list. 
     # The modes will apply to all colour depths because a 'Depth' entry has not been specified. 
     SubSection "Display"
          Viewport  0 0
          Modes     "1024x760" "800x600" "640x480"
     EndSubSection
EndSection
```You can also select the mode using the xrandr command (e.g. xrandr --output LVDS --mode 800x600_60.00). To find the current mode use the command "xrandr --current" and a * will indicate the current mode. If you are using KMS then you may find that your preferred mode has been ignored. For more information on how to use the xrandr command see [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) .
 
An alternative to adding modelines is to specify VertRefresh and HorizSync values for your monitor. See links at the start of this section (3.7c) for more information on these. You should find values for VertRefresh/HorizSync in the handbook that came with your monitor. You can also find them out using the ddcprobe command. To use this you will have to install a package first with the command "sudo apt-get install xresprobe". Then type "sudo ddcprobe". The monitor range is shown at the bottom of the output. For example:
 
...
monitorrange: 58-62, 75-117
...
 
The first pair (58-62 in this example) is your HorizSync rate and the second pair is your VertRefresh (75-117) rate. The Monitor section using these values would look like this:
 
```

Section "Monitor" 
     [COLOR=#222222]Identifier "Monitor0"[/COLOR]
     [COLOR=#222222]VendorName "Monitor Vendor"[/COLOR]
     [COLOR=#222222]ModelName "Monitor Model"[/COLOR]
 
     HorizSync 58-62 
     VertRefresh 75-117
EndSection 
```If you see repeated "insufficient memory for mode" messages on the resolutions you want in the Xorg.0.log then try adding a "DefaultDepth 16" line to the Screen section. This will also enable DRI on some low memory graphics cards. However, in the past DRI has caused instabilaties with some cards.
 
[COLOR=#222222][COLOR=#000000]People have previously disabled DRI with an r128 card by adding *Disable "dri"* to the Modules section or setting a high resolution/colour depth combination. However, without DRI, 3D effects will be software-rendered, which will be slow. An alternative maybe to disable AIGLX as outlined at the bottom of this Fedora page [http://fedoraproject.org/wiki/RenderingProject/aiglx#How_can_I_disable_AIGLX_and_the_compositing_extension.3F](http://fedoraproject.org/wiki/RenderingProject/aiglx#How_can_I_disable_AIGLX_and_the_compositing_extension.3F) . Gentoo recommend setting the option ForcePCIMode if you are having freezing problems with DRI [http://www.gentoo.org/doc/en/gentoo-ppc-faq.xml#glfreeze](http://www.gentoo.org/doc/en/gentoo-ppc-faq.xml#glfreeze) .[/COLOR][/COLOR]
 
[COLOR=#222222][COLOR=#000000]If you have configured your own xorg.conf then you'll have a full list of Device options you can tweak for your card. Look at the xorg.conf files people have used in the past for ideas on what to change. [/COLOR]Before you make any alteration to your Device section, check the relevant manual for your card because the option may not relate to your error/problem. Not all options are documented in the manuals:[/COLOR]
 
[http://manpages.ubuntu.com/manpages/natty/en/man4/ati.4.html](http://manpages.ubuntu.com/manpages/natty/en/man4/ati.4.html)
[http://manpages.ubuntu.com/manpages/natty/en/man4/radeon.4.html](http://manpages.ubuntu.com/manpages/natty/en/man4/radeon.4.html)
[http://manpages.ubuntu.com/manpages/natty/en/man4/r128.4.html](http://manpages.ubuntu.com/manpages/natty/en/man4/r128.4.html)
[http://manpages.ubuntu.com/manpages/natty/en/man4/nouveau.4.html](http://manpages.ubuntu.com/manpages/natty/en/man4/nouveau.4.html)
[http://manpages.ubuntu.com/manpages/natty/en/man4/nv.4.html](http://manpages.ubuntu.com/manpages/natty/en/man4/nv.4.html)
 
**[SIZE=2]3.7d Load kernel module[/SIZE]**
In modern versions of ubuntu, most framebuffers are blacklisted in the file /etc/modprobe/blacklist-framebuffer.conf. Therefore, if the framebuffer you want has been compiled as a module (instead of 'complied in' to the kernel) it will not be automatically loaded. To make ubuntu load the module open the file /etc/modules with the command "sudo nano /etc/modules" and add the name of your framebuffer on a new line. To make the module available early in the boot process (preferred for a framebuffer), add the name also to the file /etc/initramfs-tools/modules. Use the command "sudo nano /etc/initramfs-tools/modules" to open the file, add the name on a new line, save and then, importantly, run the command "sudo update-initramfs -u". Reboot ("sudo reboot") for the changes to take effect.
 
**[SIZE=2]3.7e Test your 3D graphics acceleration and beyond[/SIZE]** 
Following a reboot, you can test your graphics acceleration with the commands "glxinfo" and "glxgears -info". You'll probably have to install the mesa-utils package first "sudo apt-get install mesa-utils". See [http://askubuntu.com/questions/31488/how-to-test-if-my-video-card-has-3d-support/32344#32344](http://askubuntu.com/questions/31488/how-to-test-if-my-video-card-has-3d-support/32344#32344) for how to interpret the results. 
 
If you have a multi-user setup then you may need to add the following section to your xorg.conf (use the command "LIBGL_DEBUG=verbose glxinfo" to test):
 
```

Section "DRI"
     Mode 0666
EndSection

```See [http://dri.freedesktop.org/wiki/DriTroubleshooting#Userspace_setup](http://dri.freedesktop.org/wiki/DriTroubleshooting#Userspace_setup) for information on this, as well as, more troubleshooting tips. It has a good section on how to interpret Xorg.0.log messages. 
 
There is no 3D acceleration with the driver 'nv' (see [http://www.x.org/wiki/nv](http://www.x.org/wiki/nv)) and so you should try the newer 'nouveau' driver if you want this. If you can't get the version of nouveau that is in the ubuntu repositories working then there is a tutorial to compile the latest nouveau driver here [http://ubuntuforums.org/showthread.php?t=1046504](http://ubuntuforums.org/showthread.php?t=1046504) . You'll have to adjust some of the instructions for PowerPC.
 
If you have a radeon card then see section 3.8 below which has some more advice on improving performance.
 
Note, future releases of mesa will drop support for Mach64 and r128 cards, see [http://www.phoronix.com/scan.php?page=news_item&px=OTg0Mg](http://www.phoronix.com/scan.php?page=news_item&px=OTg0Mg), although it is hoped future releases of ubuntu will contain some sort of mesa-old-drivers package [http://www.phoronix.com/scan.php?page=news_item&px=MTAxMDE](http://www.phoronix.com/scan.php?page=news_item&px=MTAxMDE) .
 
**[SIZE=2]3.8 Radeon Tweaks[/SIZE]**
To get the best out of my radeon card (see [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) and [http://dri.freedesktop.org/wiki/ATIRadeon](http://dri.freedesktop.org/wiki/ATIRadeon)) I make a few alterations. With lucid (10.04) and maverick (10.10) I turn off KMS (kernel mode setting) by using the radeon.modeset=0 boot parameter (see section 3.7b above). If I don't do this then I have poor video playback (a strange vertical pixelation) and get low values in glxgears (you see "Software Rasterizer" written when running the command "glxgears -info"). In natty (11.04) I don't need this parameter because by default ppc radeon KMS is turned off in this version of ubuntu.
 
You can force a radeonfb mode by using, for example, the yaboot parameters: "radeon.modeset=0 video=radeonfb:1024x768-24@60". Forcing a mode may also fix splash problems? 
 
If you want to experiment with KMS you should turn it on with the radeon.modeset=1 boot parameter. In lucid and maverick you will also have to disable the radeonfb framebuffer [noparse]"radeon.modeset=1 radeonfb:off".[/noparse] Archlinux provide some more information on KMS with a radeon card [https://wiki.archlinux.org/index.php/ATI](https://wiki.archlinux.org/index.php/ATI) . Note, the KMS radeon framebuffer will be listed in logs as radeondrmfb.
 
If you experience choppy scrolling in firefox (can occur when you turn off KMS) then it is worth experimenting with the "AccelMethod" option in the device section of your xorg.conf file (see section 3.7c above). Under lucid and maverick I set this to "EXA" to fix the choppy scrolling. However, under xubuntu 11.04 I need to set it to "XAA". "EXA" uses less processor power but under natty especially there are a lot of rendering errors. It maybe worth investigating upgrading/downgrading drivers or checking out what framebuffers you have loaded (see sections 3.7b and 3.7d above) if you are bothered about this.
 
I also set the "GARTSize" option to "16" (half my graphics memory) because the default 8 causes silly colours (a blue tint) with the gl screensavers.
 
There are a lot of 'wonder' xorg.conf files knocking around the internet that claim to have the secret formula to fantastic 3d performance. I've only found two things that make a big difference. The first is to reduce the colour depth (for example put "DefaultDepth 16" into the screen section), but I prefer a greater colour depth so I don't do this. The second is to turn on HyperZ. This isn't done in xorg.conf, but in a ".drirc" file in your home folder. Install Driconf from the software centre/synaptic so that you can turn it on using the applet. I have no idea what this actually does, only it makes the numbers go up in glxgears!
 
You may also like to enable the "ClockGating" and "DynamicPM" settings as they reduce heat output and increase battery life.
 
**[SIZE=2]3.9 Yaboot Config/BusyBox Error[/SIZE]**
If you update to Oneiric (11.10) and instead of a login you face a 'BusyBox' shell then try the commands:
 
```

modprobe pata_macio
exit

```The boot should then hopefully resume. Once you login you can use these additional commands to make it permanent:
 
```

echo pata_macio | sudo tee -a /etc/initramfs-tools/modules
sudo update-initramfs -u

```The above is just a fancy way of adding the word "pata_macio" to the end of the modules file. You could alternatively type "sudo nano /etc/initramfs-tools/modules" to open the file and add the word on a new line yourself. You must always run "update-initramfs -u" for the changes to take effect. Reboot using the command "sudo reboot" to check that it is working.
 
If the boot didn't resume with the 'modprobe' command then you may have to perform some additional steps as detailed here [http://ubuntuforums.org/showthread.php?t=1861871](http://ubuntuforums.org/showthread.php?t=1861871) .
 
Following the ubuntu base installation, if you find you suddenly can't boot existing linux distributions (such as debian), then you may have to alter 
your yaboot.conf. I had to do this as detailed in this post [http://ubuntuforums.org/showpost.php?p=11039429&postcount=10](http://ubuntuforums.org/showpost.php?p=11039429&postcount=10) (although your setup/numbers will be obviously different). To open yaboot.conf type "gksudo leafpad /etc/yaboot.conf". When you've made and saved your changes use the command "sudo ybin -v" to copy it across to the boot partition. Use the command "sudo blkid" to print the details/attributes of your partitions. 
 
A typical yaboot.conf taken from a linux only natty installation is here [http://ubuntuforums.org/showpost.php?p=11108858&postcount=27](http://ubuntuforums.org/showpost.php?p=11108858&postcount=27) .
 
Info on dual booting with yaboot and what to do if you loose yaboot can be found here [https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot](https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot) . 
 
On some installations (e.g. onto a usb drive or with the new ata controller drivers in 11.10?) you may have to use the ofboot argument to specify the openfirmware path to the boot partition. Gentoo have an excellent quick guide to manually editing the yaboot.conf file which some people may find useful: _[http://www.gentoo.org/doc/en/handbook/handbook-ppc.xml?part=1&chap=10#manual_yaboot](http://www.gentoo.org/doc/en/handbook/handbook-ppc.xml?part=1&chap=10#manual_yaboot) _. It contains advice on the ofboot argument, as well as, adding a root delay. You can also look at the yaboot.conf manual by typing the command "man yaboot.conf". The more wordy debian guide is here [http://www.debian.org/ports/powerpc/inst/yaboot-howto/index.en.html](http://www.debian.org/ports/powerpc/inst/yaboot-howto/index.en.html) . This gives instructions on how to boot the system from openfirmware.
 
If something goes catastrophically wrong with your boot partition, then don't panic because you should always be able to use a ubuntu cd (mini, alternate, or live) to boot your installed system. Run the cd to the yaboot prompt. Instead of entering 'live' or whatever, use the openfirmware path to the kernel image. Some examples for the current and old kernel paths on partition 3 are below:
 
```

hd:3,/boot/vmlinux root=/dev/sda3 initrd=hd:3,/boot/initrd.img ro
 
hd:3,/boot/vmlinux.old root=/dev/hda3 initrd=hd:3,/boot/initrd.img.old ro

```The files vmlinux, vmlinux.old, initrd.img and initrd.img.old are links to other files. If you know those exact filenames (or another kernel image) you could use those too.
 
If you prefer the yaboot prompts to have a white background with black text (like openfirmware) add the following lines to your yaboot.conf:
```

fgcolor=black
bgcolor=white

```
 
Install grub2 if you have run out of things to play with [http://lists.debian.org/debian-powerpc/2011/04/msg00001.html](http://lists.debian.org/debian-powerpc/2011/04/msg00001.html).
 
**[SIZE=2]3.10 Sound Problems[/SIZE]**
To change the volume of the mac startup chime see [http://ubuntuforums.org/showthread.php?t=1701534](http://ubuntuforums.org/showthread.php?t=1701534) .
 
Sound should work 'out of the box' on the vast majority of machines. However, if you can't hear any sound then first check your channel volumes and mute settings. In Lubuntu, use alsamixer (from a terminal) or gnome-alsamixer to do this [http://lubuntu.net/blog/lubuntu-screencast-alsamixer](http://lubuntu.net/blog/lubuntu-screencast-alsamixer). The letter m toggles mute in alsamixer.
 
If this doesn't solve the problem then you may have to investigate the kernel modules used by your sound card. Check the various system logs or use the commands "lsmod" or "lspci -k" to see what is being loaded. Older Macs should use snd-powermac, whilst newer Macs use a combination of snd-aoa, snd-aoa-fabric-layout, snd-aoa-soundbus, snd-aoa-soundbus-i2c, snd-aoa-onyx, snd-aoa-tas and snd-aoa-toonie. See [http://alsa.opensrc.org/Aoa](http://alsa.opensrc.org/Aoa) or [http://johannes.sipsolutions.net/Projects/snd-aoa](http://johannes.sipsolutions.net/Projects/snd-aoa) for greater detail. 
 
Occasionally, the automatic setup does not work correctly and you may have to modprobe some modules. To automatically 'modprobe' a module on startup you should include it in the /etc/modules file. Open the file using the command "gksudo leafpad /etc/modules" and add either "snd-powermac" or "snd-aoa" etc on a new line (see [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=650588](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=650588)). 
 
To get sound working on a Powermac G4 Digital Audio (which should use snd-powermac) you may have to blacklist some modules (see [https://help.ubuntu.com/community/Loadable_Modules](https://help.ubuntu.com/community/Loadable_Modules) and [http://ubuntuforums.org/showthread.php?t=166624](http://ubuntuforums.org/showthread.php?t=166624)). See [http://lists.debian.org/debian-powerpc/2011/04/msg00063.html](http://lists.debian.org/debian-powerpc/2011/04/msg00063.html) for additional advice. Open/create the file /etc/modprobe.d/blacklist.local.conf (the command is "gksudo leafpad /etc/modprobe.d/blacklist.local.conf") and add
 
```

blacklist snd-aoa
blacklist snd-aoa-fabric-layout
blacklist snd-aoa-soundbus
blacklist snd-aoa-i2sbus
blacklist snd-aoa-codec-tas

```**[SIZE=2]3.11 Trackpad and Right-click[/SIZE]**
To change how a trackpad behaves see [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) . You can also use the program GSynaptics, edit your xorg.conf file (see section 3.7 above) or install powerprefs (see information about suspend in section 3.12). Another option, is to create a script which runs the commands you want at startup. 
 
Right-click is set to F12 by default. On some boots my 'fn' key seems to be set on, in which case I need to press 'fn' + F12. When this occurs, it also stops me switching to a console e.g. via ctrl+alt+F1 etc. 
 
Mouseemu is the daemon that emulates right and middle click and can also block the trackpad when typing [http://manpages.ubuntu.com/manpages/natty/man8/mouseemu.8.html](http://manpages.ubuntu.com/manpages/natty/man8/mouseemu.8.html) . You must prefix the mouseemu and showkey commands with "sudo". To change the default settings you can edit the /etc/defaults/mouseemu file.
 
**[SIZE=2]3.12 Power Preferences/Suspend[/SIZE]**
If you are trying to change the power preferences then open the terminal and type "gnome-power-preferences". You can change the settings so that the power icon is displayed at all times and then you can access the preferences from there.
 
In lucid and maverick you may have to install powerprefs (a graphical frontend to pbbuttonsd) to enable suspend when you close the lid. It doesn't setup a menu item automatically, but you can start it from the terminal by just typing "powerprefs" (for some options you might need to load it with root privileges: "gksudo powerprefs"). You may have to adjust your gnome power preferences settings so they don't clash. There is no guarantee that suspend or hibernate will work or be reliable!
 
To get suspend working with a radeon card in Natty and Oneiric you may have to compile a new kernel (see [http://ubuntuforums.org/showthread.php?t=1868664](http://ubuntuforums.org/showthread.php?t=1868664) and [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/779110](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/779110) ), although I wonder if this is actually necessary? Radeonfb should already be compiled as a module so it just needs to be loaded (see section 3.7d above)? Suspend should be available with KMS, but does it work with ppc radeon KMS??? The ArchLinux guys wrote something about suspend [http://www.archlinuxppc.org/news/10/](http://www.archlinuxppc.org/news/10/) . How to debug suspend can be found here [https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend) . See [http://lists.debian.org/debian-powerpc/2011/04/msg00092.html](http://lists.debian.org/debian-powerpc/2011/04/msg00092.html) for more info on pbbuttonsd. 
 
Suspending may mute sound channels or disable your wifi. See relevant sections.
 
To power on automatically after a power failure [http://ubuntuforums.org/showthread.php?p=11507097#post11507097](http://ubuntuforums.org/showthread.php?p=11507097#post11507097) .
 
**[SIZE=2]3.13 Software Centre[/SIZE]**
Lubuntu does not use the Ubuntu Software Centre by default. I used to think it was because the software centre was just slow on old machines, but I've found it actually works really well when the apt-xapian-index package is not installed. To install the software centre type "sudo apt-get install --no-install-recommends software-center". When using the software centre you have to be a bit careful so that you don't drag in anything that will spoil your lightweight distribution (such as pulse audio, although it is not the end of the world if you do). This is probably why the lubuntu developers try and encourage people to use Synaptic as it is easier to see exactly what is being installed.
 
See the official Lubuntu FAQ for information about the *Lubuntu Software Center* that you can install via the lubuntu ppa. 
 
**[SIZE=2]3.14 Booting from USB[/SIZE]**
There is a lot of confusion about booting from a USB device on a PowerPC machine. Here is what Apple have to say [http://support.apple.com/kb/TA25908?viewlocale=en_US](http://support.apple.com/kb/TA25908?viewlocale=en_US) . So if your model was introduced after August 1999 then there is a good chance you will be able to boot from USB.
 
To copy an iso to a USB stick:
 
First, find out the device name of the USB device. Look in the ubuntu disk utility program or something for this. Mine is /dev/sda
 
Then use the 'dd' command to copy the iso to disk. WARNING!! This will erase your USB stick so only do this if it hasn't got anything important on it! To return the USB stick to 'normal', you'll need to repartition and reformat it at the end! Also, double check you have the device name correct as you don't want to erase a hard drive or anything like that by mistake! The 'dd' command will do its thing even if you have the device mounted. The command you want will be something like this:
 
```

sudo dd if=~/Downloads/ubuntu.iso of=/dev/sda

```where ~/Downloads/ubuntu.iso is the path of the iso file and /dev/sda is the USB device. Please be extra careful if you have a G5 or are using 11.10 as it is likely your hard drive will be called sda.
 
Contrary to what you may have read elsewhere, it is possible to copy the iso from an intel machine running Ubuntu/linux. The dd command just copies raw data afterall. However, if you are having problems you could try adjusting some of the settings of the dd command? For example, set bs=512 or bs=4096? See [http://manpages.ubuntu.com/manpages/natty/man1/dd.1.html](http://manpages.ubuntu.com/manpages/natty/man1/dd.1.html) .
 
If you want to copy the iso to USB from Mac OS X then the instructions to do so are here [https://help.ubuntu.com/community/Installation/FromUSBStick#From_Mac_OSX](https://help.ubuntu.com/community/Installation/FromUSBStick#From_Mac_OSX) . These comments [http://ubuntuforums.org/archive/inde...t-1445659.html]("http://ubuntuforums.org/archive/index.php/t-1445659.html") suggest it can be done, although it maybe a little temperamental. 
 
Restart the machine holding the Option key. You should be able to choose your USB device to boot from. If you don't see your USB device (or it won't boot from it) then try holding down simultaneously Command-Option-Shift-Delete during start-up. This will bypass the internal hard drive and boot from an external drive or CD. If you want to force a particular SCSI device use cmd-opt-shift-delete-# where # = SCSI ID number.
 
If those don't work, restart the machine into openfirmware (hold down Command-Option-o-f while turning on). To boot the USB device type 
 
```

boot usb0/disk@1:2,\\yaboot 
 
(or something similar like "boot usb1/disk@1:2,\\yaboot" or "boot usb1/disk:2,\\yaboot")

```It can be very tricky to find the openfirmware path to yaboot. On some machines you can use "boot ud:2,\\yaboot". Use the openfirmare commands "dev / ls" and "devalias" to try and help you. If you can't see your usb device/files from openfirmware then you won't be able to boot from the device. 
 
I have given more information about booting from USB on this page [http://ubuntuforums.org/showthread.php?p=10993711](http://ubuntuforums.org/showthread.php?p=10993711) . There are some troubleshooting tips if you are trying to boot an 'alternate' iso. The first post in the thread contains a different method to create a bootable USB device and more tips on booting from openfirmware.
 
If you want to install a system onto a USB device (instead of a hard drive), then you may need to specify an ofboot argument in your yaboot.conf file. See section 3.9 above for more advice on this. 
 
**[SIZE=2]3.15 Security[/SIZE]**
Many would consider Ubuntu to be secure ‘out of the box’ due, in part, to the often quoted (but perhaps misleading) statement “Ubuntu comes with no open ports”. This is rather a simplified view and is challenged in the evolving security wiki (aimed at people new to Linux) here [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) , with further information in the sticky threads on the Security Discussion forum [http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338) . For more information about the security design decisions made by the Ubuntu Security Team see [https://wiki.ubuntu.com/SecurityTeam/FAQ](https://wiki.ubuntu.com/SecurityTeam/FAQ) . 
 
The wiki and sticky threads describe how you can enhance the security of Ubuntu above the default installation, although they take a rather paranoid view of security that I would imagine far exceeds that used everyday by most Ubuntu, Mac and Windows users. Nevertheless, it is worth reading the information as security is probably something that many Linux users can be complacent about. However, as you increase the security of your system the ease of use decreases, so you need to find a balance that you personally are happy with. For example, the idea of running NoScript may not sound appealing, but maybe there are features that you can turn on that don’t effect your web browsing experience? As I describe in section 3.6 above, I disable the icedtea Java plugin completely without any loss of function to me. Note, Java is not the same as the similarly sounding javascript. 
 
My own view is that if you are new to Linux then I would suggest getting to know Linux/Ubuntu before tackling any extra security features. Ubuntu can have a steep learning curve as it is. Many risks can be mitigated with common sense. 
 
Keep the system updated via the Update Manager. Only install/run software that you need and only install software from secure and trusted sources (e.g. the Ubuntu repositories). Whilst a person/website may provide a package or executable with good intentions, can you be sure their server has not been hacked and the binary swapped for something malicious?
 
If you are running ssh or vnc, possibly as part of a server setup, then you do need to learn to secure them properly. 
 
One of the main reasons I am keen to stick with *ubuntu is because they provide secure repositories with full traceability. Source code and build logs for every package are available in Ubuntu through [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu) .
 
 
[SIZE=3]**4. How To Help PowerPC Ubuntu**[/SIZE]
I 'stole' (based) most of the following from the sticky thread on the Ubuntu Studio forum!
 
Hopefully you're now enjoying your new PowerPC Ubuntu system. Maybe you've stopped to think 'I wonder how all these wonderful tools came to be... ...who packaged them... ...why these ones... ...what makes ubuntu such a success?' well, the answer to all these questions is the same: the development community. Having a large group of individuals to help build Ubuntu creates a network of checks and balances, not to mention lighter work for everyone.
 
GNU/Linux is a community effort, and because of this, we all hope that you too will get involved. Who me? Yes, You.
You may hold the common misconception that because you don't know how to program, you're no good to the development community, but nothing could be further from the truth. No matter what your level of expertise with Ubuntu you can lend a hand. Furthermore, in the field of PowerPC Ubuntu, we NEED your help. 
 
Every level of Ubuntu user can help the communiy in some way. Here's a few examples (please don't feel limited to these suggestions) just to get you started:
 
*1. The Absolute Beginner* (you're just finding your way around, learning, and noticing the layout):
* Stick around these forums and answer any questions you can (just reading the posts will help educate yourself)
* Even absolute beginners can help edit the community documentation. Many of the directions here suffer from a lack of eyes, leading to unclear instructions - if you find some please tell someone or even edit it for the better yourself. The PowerPC FAQ is at the time of writing crying out for a makeover.
 
*2. The Novice User* (this isn't the first version of ubuntu you've used, you're able to get most work done that you need to):
* Document, document, document; head on over to the community docs and start editing for the better (many sections of these documents need substantial work and we'd love all the help you can offer)
* Report bugs you find (actual bugs such as missing packages, not your configuration issues) at [http://launchpad.net](http://launchpad.net) (this is the official bug tracker and development portal for ubuntu). See [http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078) .
 
*3. The Advanced User *(given any howto and a terminal you can fix almost anything)
* Install a copy of the development release on another partition and report bugs/issues etc...
* Regularly test ISO builds. See [https://wiki.ubuntu.com/Testing/ISO/Procedures](https://wiki.ubuntu.com/Testing/ISO/Procedures) .
* Document, document, document!
 
*4. The Hacker* (you've compiled a kernel for yourself, don't need any directions for most system modifications, and generally prefer to use the terminal) 
* See 'The Advanced User' points.
* Join a dev mailing list and introduce yourself
* Log into irc.freenode.net and join some development channels.
* Learn to package software [http://developer.ubuntu.com/packaging/html/](http://developer.ubuntu.com/packaging/html/)
* Comment on bugs at [http://launchpad.net](http://launchpad.net)
 
 
[SIZE=3]**5. Useful Links**[/SIZE]
The official Lubuntu FAQ (including, for example, how to enable autologin) is here [https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ) .
 
The Lubuntu homepage is here [http://lubuntu.net/](http://lubuntu.net/) . There are a lot of good screencasts that show you how to to customize lubuntu.
 
The Ubuntu community documentation can be found here [https://help.ubuntu.com/community](https://help.ubuntu.com/community) . The offical documentation is here [https://help.ubuntu.com/](https://help.ubuntu.com/) .
 
The Oneric Lubuntu release notes are here [https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/OneiricOcelot](https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/OneiricOcelot) . The general Ubuntu release notes are here [http://www.ubuntu.com/getubuntu/releasenotes](http://www.ubuntu.com/getubuntu/releasenotes) . 
 
Links to the Ubuntu PowerPC FAQ and Known Issues pages can be found here [https://wiki.ubuntu.com/PowerPC](https://wiki.ubuntu.com/PowerPC) .
 
The Debian PowerPC mailing list is here [http://lists.debian.org/debian-powerpc/](http://lists.debian.org/debian-powerpc/) . This is an excellent place to look for information about new changes to the kernel.

---

### Post by linuxopjemac on 2011-07-07
This is a very well written guide to install Lubuntu. Good work!

---

### Post by Cyrus11 on 2011-07-10
I can confirm that the install worked on my powerpc 1.0Ghz iBook G4 14inch with ATI Radeon 9200 32mb. 256 RAM.  60GB hard drive.

Error encountered was wvdial.conf during setup from boot. It couldn't be configured. Setup suggested that the user configure wvdial.conf manually once logged in.

I tested internet. I'm not sure how to enable different codecs. Flash and whatnot is not working. What repositories do I add to get a media player for an iPod or streaming such as ubuntu restricted extras? Not sure if there is a software center for powerpc...(I doubt it.) I'm very noob to linux and this is the first major custom install I've ever done. I don't even know what wvdial.conf is. 

Also hardline internet connection does not work, but I can get the wireless to work according to instruction from above. I don't know what cpu scaling is. If someone could explain what that is I could try to troubleshoot. Help and contribution would be appreciated. My bro needs this iBook for school AP classes.

---

### Post by IsshoNi on 2011-07-11
Also, after installing the command line natty version is it possible to install the xubuntu desktop? Would I have to manually install the xubuntu packages? Where is a PPC repository for PPC software? I'm confused

---

### Post by rsavage on 2011-07-11
Hi, thanks for trying the instructions!  I think you are the first!

vwdial.conf from googling is something to do with the modem [http://en.wikipedia.org/wiki/Wvdial](http://en.wikipedia.org/wiki/Wvdial) .  I'm afraid I didn't get this message on my iBook.  Is the modem what you meant by a hardline internet connection?  My ethernet connection works fine once I carried out the fix I mentioned in the instructions.

You'll be able to install whatever media player you like and the restricted extras package once you have the libx264-98 package from maverick.  You can download it here [http://ports.ubuntu.com/ubuntu-ports/pool/universe/x/x264/libx264-98_0.98.1653+git88b90d9-3ubuntu2_powerpc.deb](http://ports.ubuntu.com/ubuntu-ports/pool/universe/x/x264/libx264-98_0.98.1653+git88b90d9-3ubuntu2_powerpc.deb) .  You'll then have to install it with the command "sudo dpkg -i path_to_file" where path_to_file is the path to the saved the file.  Note, I haven't tried this yet, I've just 'made up' the instructions for you.   *EDIT: The script now downloads and installs this package.*

Lubuntu does not use the software centre by default because it can be slow on old machines.  To install type "sudo apt-get install --no-install-recommends software-center".  Synaptic ([http://packages.ubuntu.com/natty/synaptic](http://packages.ubuntu.com/natty/synaptic)) is what's installed by default.  It is not so user friendly, but it does the job.

You can find and install the ubuntu-restricted-extras package in synaptic.  There are also other codecs you can download from medibuntu (e.g. for dvd playback), but you won't find a link on their website.  I'll give instructions later today, but you can find instructions if you do a search.

There is no adobe flash, but there are a few 'free' versions.  There are lots of ways to watch YouTube successfully on PowerPC  if that is your thing (e.g. there is even a plugin for Totem player I think).  Again, I'll add instructions when I have time or do a search. 

CPU scaling reduces the processor speed when the computer is idle or not doing a lot.  It saves battery power and reduces heat so you won't have the fan coming on so much.  Again, I'll look into it.  

I may have some time this afternoon to do some more troubleshooting.  Hope the above is useful for the moment!

---

### Post by rsavage on 2011-07-11
@IsshoNi if you've installed the base system then you have the ppc repositories enabled.  You can then select xubuntu with the command "sudo tasksel".  I'm not sure if this will work in Natty (but it definitly should in Maverick or Lucid) because of the missing package that the media players rely on.  If it doesn't then you'll have download the missing package before running the command, or install the individual packages like I've done for lubuntu or install maverick xubuntu and then upgrade to natty.

On the ubuntu website ppc versions of packages vary rarely get a mention, but they are there!  Honest!  There is a ppc repository in the uk and there must be others around the world!

---

### Post by rsavage on 2011-07-24
Just thought I'd let people know that Xubuntu, Kubuntu, etc can be installed easily using the tasksel command. Once you've done the base installation the only commands you need to type are:
```
sudo apt-get update
sudo tasksel
```and then select the desktop of your choice. It seems the libx264-98 package is only missed by mplayer which xubuntu/kubuntu/(ubuntu?) don't use.
 
Just to clarify too what I was saying about the repositories: the base installer should choose a suitable location to download from so you shouldn't have to worry about this. It would be good to hear from people outside the UK to see if it does this successfully?
 
A final thing, I've done a few tweaks to the end of the script. I haven't tried it with them in, but hopefully the script will still work!

---

### Post by jdix123 on 2011-07-25
How did you get the wireless working?  

I run sudo iwconfig and I see that my device is wlan0.  But when I open the network connections manager, I don't see anything.

My ethernet connection works, though it doesn't show up as a connection in the network manager.  Is this the fix you refer to in your first post?  I tried just copying the eth0 entries, substituting wlan0 but then the network daemon did not restart.

Ideas?

---

### Post by rsavage on 2011-07-25
I wouldn't do any of the iwconfig stuff, you will just mess it up.  What have you installed lubuntu/xubuntu/ubuntu?  What wireless device have you got airport classic/extreme/other?  What machine are you on?  Have you done a search for a fix (you often get a quicker answer this way)?  What is the problem exactly, you can't connect (bad password) or you can't see wireless networks at all when you left/right click on the network icon?
 
Your ethernet problem sounds like the problem I have already provided a fix for.  Use the first solution on the linked page.

---

### Post by rsavage on 2011-07-25
This is something I wrote a while ago [http://ubuntuforums.org/showthread.php?t=1705143](http://ubuntuforums.org/showthread.php?t=1705143) which may help you. In lubuntu natty you don't need to check the privileges.

---

### Post by jdix123 on 2011-07-26
The fix you posted works for the eth0, fantastic.  Then I just installed the b43 drivers and that took care of the wireless.  I thought since I could see the device in iwconfig that the drivers were installed already.  Guess not.

What about the touchpad?  Is there a driver for it?  I try to run synclient and I get "Couldn't find synaptics properties.  No synaptics driver loaded?"

12" Powerbook G4 867

---

### Post by rsavage on 2011-07-26
You are probably using ADB mouse as this explains [https://help.ubuntu.com/community/SynapticsTouchpad#Determine%20whether%20a%20touchpad%20has%20been%20detected](https://help.ubuntu.com/community/SynapticsTouchpad#Determine%20whether%20a%20touchpad%20has%20been%20detected) 
.  It is working though isn't it?

I'm a little confused myself about the synaptics driver as I've seen some guides for the iBook that tell you to use it.  My model comes up with the ADB mouse though.  There is meant to be a patch somewhere that lets you use synaptics on an ADB mouse, but I can't find it.  So no two finger scrolling for me....

---

### Post by jdix123 on 2011-07-26
The mouse does work, but I was hoping to get some increased functionality.

I did find the "trackpad tap" command to be useful, but would like to emulate left and middle clicks by tapping two or three fingers, and enable two finger scrolling too.

---

### Post by rsavage on 2011-07-26
You can change what keys on the keyboard are right and middle click.  That is all I know.

How is lubuntu comparing to mintppc as I see you recently installed that too!?!  I'm actually really liking xubuntu at the moment so could give that a go as well!

---

### Post by jdix123 on 2011-07-26
I tried the mint ppc for a week or so but I got frustrated with the Debian base and reositories pretty quickly, as I am a longtime Ubuntu user.  Lots of support out of the box for things like wireless and such.  I tried xubuntu for a bit too, but I'm digging LXDE a lot right now.

I just found a package that supposedly enables multitouch.  I'll let you know if it works and where to find it.

---

### Post by rsavage on 2011-07-26
I see now why you were confused with the wireless, as mintppc does indeed download the driver for you.  I tried it for a bit, but debian drives me mad after a couple of minutes of using it and the font rendering is awful (sorry linuxopjemac)!

I like the shadows and transparency of xubuntu and the applications load nearly (if not just as) fast.  I get the simplicity of lubuntu too though and it is really fast to boot.

Would be good to hear about the multitouch package.  Thanks

---

### Post by linuxopjemac on 2011-07-26
Interesting to hear why you think Debian is inferior to Ubuntu. I always take the positive information out of criticism. I never personally felt that font rendering was so bad in Debian and therefore also in MintPPC. But knowing this, I am willing to experiment a little on this subject. I will have a look if I can make the font rendering better in MintPPC, just like it's done in Ubuntu. Thanks for your honest opinion.

---

### Post by jdix123 on 2011-07-26
I think a live CD installation would be in your favor too.  I see on your website you are working on one.

Another interesting thing I found, running lubuntu the nouveau graphics driver works.  I had issues with this driver in mintPPC if you remember, and wound up using the NV driver.

---

### Post by linuxopjemac on 2011-07-26
I am working on an iso based installer, yes, but not a liveCD installer, that's beyond my knowledge at this moment.

Interesting that nouveau works for you...Do you know why it works under Ubuntu as opposed to MintPPC ?

---

### Post by linuxopjemac on 2011-07-26
Would you be willing to test the new MintPPC version in the future and see whether nouveau will work ?

Could you paste the output of:
```
sudo cat /var/log/kern.log
sudo cat /proc/fb
sudo cat /var/log/Xorg.0.log
```

---

### Post by jdix123 on 2011-07-26
No I don't, I guess I'm not that awesome.  I did use the xorg.conf file you linked for me, but I didn't have to change the driver to make it work.  Seems strange, that the same xorg.conf on the same machine with the same window manager produces different results.

I did have to jump through a few more hoops to get wireless networking and the trackpad working to my liking (though I think its too old to support multitouch), so kudos for having that taken care of :)

---

### Post by rsavage on 2011-07-27
> **jdix123 said:**
> I did have to jump through a few more hoops to get wireless networking and the trackpad working to my liking 

I think that is a bit of an exaggeration to be fair!  You only have to type in one command to get wireless working!  Any hoops were of your own making because you totally ignored the instructions I had written.....  ](*,)

I could of made the script do it all automatically, but that wouldn't help people using xubuntu etc.  Also, I imagine some people will type out the script so making it as short as possible was a good thing.

Linuxopjemac, I see from your forum that you've now made the changes to the fonts already!  :)

I still won't be going over to MintPPC I'm afraid.  I think I have a fundamentally different outlook to those using MintPPC/debian.  I wonder too if creating a separate distribution weakens the PowerPC architecture because of a reduced visibility in the general populous?  Just a thought, although I don't want to undermine all your hard work on MintPPC.  For most people the choice (between xubuntu/lubuntu/MintPPC etc) will probably come down to aesthetics, even though I think lubuntu is faster.  Beauty is in the eye of the beholder etc.

---

### Post by rsavage on 2011-07-27
Forgot to mention with regard to font rendering that some screens have a different sub pixel geometry to the standard RGB.  I think some of the apple screens did this (early ibook maybe, can't remember?) so you may have to change the settings to get it just right.

---

### Post by rsavage on 2011-07-28
Have corrected a mistake I had made with the installation instructions for powernowd.  I had linked to an old package.  I was having difficulty installing it in xubuntu and spotted the mistake.  Hopefully it will now work....will try tomorrow.

---

### Post by jdix123 on 2011-08-01
I'm noticing three issues at the moment with my particular machine.

First, the startup and shutdown splash screens do not use the full display.  Just a little section in the upper left.

Second, the display stays on when I close the lid.  I can't seem to find a setting that will suspend or hibernate when the lid is closed, just when I push the button.

Third, I am getting a mass of this on startup
```

udevd[worker54]: worker [93] did not accept message -1 (connection refused), kill it

```

The same line is repeated multiple times, with different values for "worker [93], worker [94], worker [96]" etc.

Ideas?

---

### Post by rsavage on 2011-08-01
udevd - I have no idea. Have you always had this or is it something that has just started?
 
Install powerprefs to fix the suspend when you close the lid. You may have to adjust your gnome power prreferences settings so they don't clash. It is what you will have had in mintppc. I haven't tried this in natty though. Hibernate doesn't work for me, have you had it working in the past?
 
Splash screen - adjust your yaboot parameters. Either remove the splash (nosplash) or you need a video=something (try video=nouveaufb:1024x768-24@60 or see section 3.7 of instructions for link to proper documentation) .
 
EDIT: suspend has always been a bit dodgy for me so remember to save any work before you suspend!

---

### Post by jdix123 on 2011-08-01
yeah the udevd thing has happened since the install, it just didn't seem to affect anything so I ignored it in favor of getting everything else setup like I wanted it.

Its not immediately obvious to me where to put those options in yaboot.conf

```

boot="/dev/disk/by-label/bootstrap"
device=/pci@f4000000/ata-6@d/disk@0
partition=3
root="UUID=9f62861c-645a-4b80-99b8-46ea300302e6"
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"

```

---

### Post by rsavage on 2011-08-01
You should be able to try them on the second yaboot prompt. e.g.
 
Linux nosplash
 
When you want to make them permenant you change the 'append' line. e.g.
 
append="quiet"
 
sudo nano /etc/yaboot.conf
then "sudo ybin" to copy it across to the boot partition.

---

### Post by Voldas on 2011-08-10
Hello, will this work on an imac g3 slot loader? Thank you. :confused:

---

### Post by rsavage on 2011-08-10
It has as much chance as anything else.

---

### Post by OriOs on 2011-09-01
I made this [Live CD]("http://alibabatimes.com/iso/or.iso") a few weeks ago when I stumbled upon a Powerbook with a malfunctionning hard drive. I'll try to implement your tutorial (at least the lubuntu core) to make a Lubuntu live for PPC, I think a few people might be interested :)

nb: this iso as no installer and starts in a spartan terminal. No fancy, no candy. However you can ```
startx
```
which will start flwm (fast light window manager)

To configure network
```
sudo wicd-curses
```

---

### Post by rsavage on 2011-09-02
A lubuntu live CD would be great! :P I think the lack of natty live cds generally has been a big loss to ppc ubuntu.  Hopefully they will return in 11.10.

I like the vertical title bars in flwm.  Very cool.  

I am also envious of your linux skills.  How did you make the iso?  Also, do you know how to backport/compile firefox 6 into ppc lucid/maverick?  I think this could really help people, but I don't know how to do it properly myself. EDIT: maybe a way of apt-pinning would be better so that fierfox security updates are installed automatically?  Again, I've never done this, but I'd like to get some instructions on the forum for people who are reluctant to continually update their version of ubuntu.

EDIT2: I've now compiled firefox using the instructions in the 'workarounds' section (pretty easy).  I'll probably write something about it later.

---

### Post by B_Free on 2011-09-02
I have asked this question before but did not get a satisfactory answer. rsavage, what would happen, after all your work, if your hard drive died? Did you back up the drive?  I am amazed at yourself, oswaldo, and linuxopjemac. I've been trying Linux, different versions on the old PPC machines. Not that happy. I am used to a Mac OS install, and works every time, perfect! 
These are my 2 questions
Not really sure which machine you are installing lubuntu, but once it is installed, and perfect, can you make a back up that would install on any machine that is the same as the one you are installing lubuntu? They are not making any new hardware for those machines.
Can a person disassemble an iso file? Delete what is not necessary, update the files you need for a particular machine, use the installer, .....? You are the smart guys, I'm the dummy!

---

### Post by OriOs on 2011-09-03
@rsavage

How to make a Live-CD...
Well, at the time I wanted one I was already scooping around at the LFS project ([http://www.linuxfromscratch.org]("http://www.linuxfromscratch.org/")).
then wandered around to gather specific informations for the PPC architecture so I've been mixing a lot of things.
As of now it will take me way more time to explain the process than to make it. I'll try to write a descent tutorial when I can. But seeing a bit of the work you produced, I think you have more than the skills necessary for this. :P



@B_Free

Not sur to understand what your asking. If your questions did not find answers yet, could you be a bit more specific... in general :)
What kind of computer do you have? What type of linux distros did you try? What went wrong with each one of them (I doubt it was the exact same probleme). 
There are many tools to backup your hard drive on Unix like system (whether Mac or Linux)
You've got the "cp", "dd" and "rsync" command to begin with, but I'm sure you can find some GUI Time Machine equivalent. A quick search gave me this [http://code.google.com/p/flyback/]("http://code.google.com/p/flyback/") but I have no idea what it worth. But if you want a lossless carbon copy of any drive, I don't think you can find anything better than the "dd" command.
Why would you disassemble an iso. I can't see your point. I feel like what you would need in this example is the mini.iso (and perhaps a thumb drive).

---

### Post by rsavage on 2011-09-03
OriOs, thanks for the link.  That could be just what I'm after.  I'm thinking of buying myself a FriendlyArm board off ebay and making myself an internet radio!  First I need to seriously improve my basic linux knowledge as currently embedded linux looks like gobbledegook!

Incidentally, if anybody wants any info on how to listen to flash radio streams on PPC then give us a shout.  The flash BBC streams are better quality than the non-flash BBC streams.

B_Free, I don't backup my hard drive I'm afraid.  This thread is sort of my backup.  I'm sure there must be backup/restore software available for linux if that is what you are after.  

As OriOs mentioned the dd command is pretty useful and powerful.  Once I had done the base install I cloned my partition using dd so I could install lubuntu, xubuntu etc without having to start from scratch everytime.  If anybody wants to do this then I could probably dig out the exact commands I used. When you copy a partition the UUID also gets copied so you have to generate a new random UUID and assign it to the new partition.  Otherwise the computer gets confused!  Then all you do is update the yaboot.conf so you can boot from the new partition.  Going a little off track there....

So you could use the dd command to copy a partition to an iso file.  That would then be pretty easy to roll out to many computers I should think (as long as they are exactly the same).  You need to be sure what you are doing as dd can also mess up your computer if you get it wrong!

I did try briefly editing an iso file but I kept being told it was read only.  Am sure it is possible though, I just haven't properly looked into it.

I think the alternate install cds are meant to be useful if you are installing on lots of computers.

---

### Post by B_Free on 2011-09-03
I've read the whole discussion here.
I have an Imac G3, 4 PPC G4, and a G5. All displayed different problems no matter what distribution I installed. 
Have you ever installed a Mac OS on these machines? There is no extra frameworks, etc., except maybe printer drivers. The Mac software is made specifically for that Mac. There are no fixes you must perform after installation.
As the dummy in this conversation, I am looking for simplicity. If you have an Imac G3 266, all hardware is exactly the same, computer to computer. The video cards are the same, the type of ram, etc. If you install 10.04 on one Imac G3 266, it should be the same on all Imac G3 266 machines.
Most all Mac computers have not been altered since it was purchased. At least PPC computers. If you install any version of Linux on these machines, if there was a back up for your machine, it should work on any machine of the same type. So, if rsavage installed the latest version on his say, Dual 1.8 GHz PowerPC G5, it should work on all of those machines.
Let me digress. Back when there were floppy drives, you could make your own floppy to restart your computer in case you had a problem. You would put a copy of the Mac OS ROM, utilities, etc. on the floppy, so you could start the computer to troubleshoot. This was a barebones start up.
What makes up a Linux OS, without Gimp, OpenOffice, etc.? rsavage says you don't need a piece of software, should substitute this for that, workarounds, .If you have gone through all this trouble, make it easy on everyone else, come up with an install version that would work (on the same machine) that you made this perfect installation. I hope I explained myself properly.
Remember, I am the lazy dummy!

---

### Post by OriOs on 2011-09-03
Just a quick reminder:

You do realize that, as of now, ubuntu ppc is supported by the community (i.e you, me, and everyone else), and that the main maintainers may not have the time nor the proper machine to test on, right?  Apple pays people to make it right, here we volunteer to make it work (by the way, if you donate one of your G3, I'll surely (try) to make ubuntu conveniently work on them :P


Honestly I think there are no dumb questions, only dumb ways of asking them (i.e the "my PC broke, HELP MEEE RIGHT FREAKING NOW" type). 

I've been able to boot the same ubuntu install on a Dell and a Mac-intel. As for PPC, the basic iso I made (ubuntu-minimal and X) worked on a powerbook G4, an ibook G4, and apparently rsavage could make it work too (by the way, could you tell us on what kind of computer?)
Since I'm sill not sure if I understood what you asked, my answer may not be fully satisfactory.

Anyway the fact that that you tried outside Mac and spinned different distros prove that you're not that lazy after all.

**Firefox back-porting and apt-pinning**

For those who don't know, apt-pinning is basically being able to install software from a more recent release than the one your working on. In our example: having firefox 6 on lucid (I can't see firefox 5 in the repo).

This  [_howto_]("https://help.ubuntu.com/community/PinningHowto") looks more than handy for this purpose. 

Beware that doing that might break some depandencies especially if you are building some software from source (for example, gphoto2 is pretty touchy with those, building it from source (it was required, on an ARM9 board) can be a real hassle)

---

### Post by B_Free on 2011-09-03
I've been trying Ubuntu for over 2 years now. I try to help when I know something for certain. I thought I explained I have multiple machines (Imac G3, 4 G4's, and a G5). So, I guess I'm not going to get an answer. I thought I went overboard on my explanation but I guess not. I'll leave you to your discussion.

Honestly I think there are no dumb answers, only dumb ways of explaining them (i.e the "my PC broke, HELP MEEE RIGHT FREAKING LATER" type).

---

### Post by rsavage on 2011-09-03
B_Free, I've read your post a few times to try and understand what you want.  Am I right in thinking that you want an iso producing for every apple model computer?

I've never used a Mac OS, but I should jolly well hope it installs flawlessly.  Apple have it easy in many regards because they have a very limited range of hardware.  (Yet they have still dropped PowerPC.)  Compare that with the vast number of computers ubuntu or windows potentially can be installed upon.  The PowerPC architecture is not alone in requiring tweaks.  For example, my Toshiba laptop needs some adjustments with ubuntu otherwise it melts from the fan not working.

It simply is not practicable for ubuntu or anyone else to make iso install images for every model of computer.  The generic install disks do a pretty good job anyway.  This thread was intended to sweep up any problems that the generic install does not fix.  I'd be disappointed if you were still having problems after reading it.  From reading the forum it seems the main issues are wifi and xorg.conf problems.  I hope I have covered both these things satisfactorily.  If you think there are more problems that should be included then please let me know.

As OriOs says ubuntu PPC is community supported.  I'm not really sure what that means, who compiles it (is it still canonical?) or finds the fixes, but we should be thankfull that somebody is doing so!  I do know it is down to everybody to keep the documentation/fixes up to date and this thread is my little attempt.  I don't consider myself a guru and so I've chickened out of updating the FAQ page!

My iBook G4 is in bits at the moment, suffering from a broken frame, a hard disk that is making worrying noises and some bodged soldering.  So I'm without PPC at the moment, sorry OriOs I haven't tried your iso yet....  I'm waiting for a suitable eBay purchase......

The only stupid question is the question you didn't ask.

---

### Post by rsavage on 2011-09-04
OriOs, thanks for the link on apt-pinning.  I think I'm starting to get my head around it.  There is some more useful information on the page about backporting [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports) .

Interesting on the link you gave that they don't recommend apt-pinning for ubuntu and say firefox won't work!!

Well I've just tried it by installing Firefox 7 from Oneiric into Natty and have had no problems.  They seem to be concerned about different versions of libc6 which I don't understand.  Firefox 7 only depends on libc6 >= 2.11 so even Lucid satisfies this.  The only package that had to be updated was libstdc++6.

I know there are a lot of doom and gloom merchants out there who don't recommend you mix ubuntu versions, but I honestly don't get what the worry is.  Can anybody explain?  It seems it should be really easy to get the latest Firefox into power pc lucid?  I can't believe nobody has tried it/is doing it?

---

### Post by B_Free on 2011-09-04
If you have never tried the Mac OS, you should. You'll know what I'm trying to say. 

As far as having an iso that would install on all PPCs, it's not what I said. Just the opposite. The machine you are installing Lubuntu, just that machine. 

I'm assuming dd means duplicate drive. If you were to solve all the problems and make your computer as perfect as you could get it, duplicate your drive and make that available to all. JUST your computer. That type.

If others out there in Ubuntu land, could install, make perfect, duplicate the drive, and make THEIR computer type available to all. I mean JUST the basics. One where their Wifi, CD drive, fans, video card works.

I don't know if any of what I just said is possible.

It seems no one knows who puts out the isos we download, and install. Do we know who maintains those sites?

Being into recycling, I thought I could help those with old PPCs get a more modern OS. One that they would not have to hassle with. One that could grow with the internet. The only discussion would be how to get a browser to work with your version of Ubuntu.

---

### Post by rsavage on 2011-09-05
B_Free, I think we are going to have to agree to disagree on this.  I'm not saying the installation process is currently perfect on every machine, but in my opinion the best solution is to create a good generic installer and have good documentation to overcome any problems. If people raise bugs with the developers and help them find the fixes then eventually those problems will be solved in the generic installer. Keeping documentation up to date can be done by anybody, it doesn't need any programming skills.

> **B_Free said:**
> The only discussion would be how to get a browser to work with your version of Ubuntu.

It probably should be pointed out that there is nothing wrong with firefox 3.6.21 that is in lucid and maverick.  Firefox 3.6.x will probably be coming to the end of its life soon, and when it does, lucid and maverick will switch to the latest stable version of firefox (currently 6.01).   

Firefox 6.01 is able to display html5 and is quicker to load.  If you want to try out 6.01 now then I can give instructions I think.

---

### Post by gp2x on 2011-09-07
Hi all

I realise this kind of question is probably pretty irritating, but I have an old G4 400Mhz powermac, and Im looking to install lubuntu on it (I gave up on morphos). Has anyone summarised the combined wisdom here into a wiki or similar?

Im a long-time ubuntu user, but to be honest I lack the headspace for in-depth hax0r right now.

muchos gracias.

---

### Post by rsavage on 2011-09-07
gp2x, just follow the instructions in the original post.  There is nothing hard.  If you want to create a wiki or update the general powerpc FAQ then that would be great.

---

### Post by rsavage on 2011-09-07
Forgot to say.... there are is now a powerpc lubuntu live cd for 11.10.  You can't get any easier than that!  Have a look at the power pc sticky thread for more info.

*EDIT: Well maybe not so straightforward as it should be - it is in testing afterall!  [http://ubuntuforums.org/showpost.php?p=11231249&postcount=24](http://ubuntuforums.org/showpost.php?p=11231249&postcount=24) and [http://ubuntuforums.org/showpost.php?p=11231851&postcount=30](http://ubuntuforums.org/showpost.php?p=11231851&postcount=30) .  It's important people report any problems or they won't get fixed!*

---

### Post by B_Free on 2011-09-12
I can't find the lubuntu live cd link.

---

### Post by rsavage on 2011-09-12
I don't understand.  You posted the link on the sticky thread.  It appears to be working?

---

### Post by Panchiron on 2011-09-14
Hello, rsavage and the rest of people at this thread.

I´m new here and have to say that, after months trying ubuntus, xubuntus, kubuntus and so many *untus I found, rsavage has open a new world for me and my oldie PowerBook Titanium! So, thank you very much for this.

My loved machine (667Mhz and only 256 M of RAM) had all kind of troubles to run decently any other distro of Ubuntu. But with this Lubuntu-made by rsavage everything is going right.

Well, not really everything. I´m concerned because the fan is getting crazy after a few minutes of working, and even when I stop working it does not stop running and running. If I reboot, the fan is still at the same revolutions.

I think I have tried properly the workaround you posted about the CPU Frequency Scaling because I guess that this is the problem. I even went to The Power PC Known Issues pages [https://wiki.ubuntu.com/PowerPCKnownIssues#Ubuntu_10.04_Lucid_Lynx](https://wiki.ubuntu.com/PowerPCKnownIssues#Ubuntu_10.04_Lucid_Lynx) and tried its trick, but I think the problem persists.

So I would appreciate any help here.

Thank you very much.

Greetings!

---

### Post by rsavage on 2011-09-15
Panchiron, welcome to the forum and thanks for the kind words (although all the credit really needs to go to the lubuntu developers!).
 
Unfortunately, I don't have lubuntu or a powerpc in front of me at the moment so these are going to be vague instructions I'm afraid. The first thing we need to do is work out if the fan is coming on because the temperature is indeed high (or is it coming on incorrectly at a low temperature)? 
 
You should be able to add to the bottom panel a system monitor applet. That will show how busy the processor is. If you are doing nothing then it should be practically registering nothing. If it is not then use the command "top" (in lxterminal) to see what process is running high. You should also be able to add an applet that shows the processor frequency. This will show if processor frequency scaling is working. It should scale up when the processor is busy (over 80%) and scale down when it drops below 20%. Is this working correctly?
 
Now for the bit I'm not sure of. Is there an applet that displays the temperature and does it work? What does the command "sensors" display? You may have to install it, as well as, install/run sensors-detect. 
 
Do you have the therm_adt746x module I mention in the ibook G4 section listed? I thought that was just for G4 iBooks (I did once look at the source code I think), but I see on the mintppc forum that they install it for other *books.
 
Ultimately, you may have to do a bit of detective work to solve your fan problem. This forum, the mintppc forum and the debian powerpc mailing list are good places to look as well as just a general search. Try and find recent information as things change in linux. Please post pack with the above info and I'll try and think of other stuff. Good luck!

---

### Post by TODDMAN on 2011-09-15
> **Panchiron said:**
> 

Well, not really everything. I´m concerned because the fan is getting crazy after a few minutes of working, and even when I stop working it does not stop running and running. If I reboot, the fan is still at the same revolutions.

Have you tried Windfarm?

---

### Post by Panchiron on 2011-09-15
Thank you (both) for the "proposals".

Well, I must confess I´m in "panic-mode ON". I mean, this is what happened:

- Doing nothing with the PowerBook, the CPU level was really high (almost 100% all the time, with the "gvfs-gdu-volume" on top with a 20% and two others with similar ranges) and the fan a-la Usain Bolt.

- The processor frequency showed only 677Mhz (so, no frequency-scaling).

- The temperature applet said N/A.

- Executing "sensors" said no sensors installed and "sensors-detect" showed too much information for being processing by an ignorant like me.

- Finally, adding the "therm_adt746x" module to /etc/modules didn´t work, because when I tried "sudo modprobe therm_adt746x" the result was something like "Fatal Error: No therm_adt746x detected".

The worst thing now is that, as a result of my "panic attack", I went back to Mac OSX 10.3.9 to check my fan into its "natural environment" and I think it´s getting crazy too.

So now I have to take a coffee, rest a while and think what´s going wrong on OSX. Then, when fixed, I´ll go back to Linux and break it again :D. Maybe in a couple of days, I´ll try Lubuntu again.

Thank you and greetings!

---

### Post by linuxopjemac on 2011-09-16
It's possible that this kernel module is not available in the stock Ubuntu kernel. It's available in Debian though. I cannot recommend using a Linux system without this module. It can harm your hardware if you let it become too hot.

---

### Post by rsavage on 2011-09-16
Linuxopjemac, I was hoping you'd come up with something constructive (like how to get a temperature readout), but instead you've reverted to type and come up with this scare mongering about Ubuntu.  Can I point you to this thread [http://mintppc.org/forums/viewtopic.php?f=10&t=322](http://mintppc.org/forums/viewtopic.php?f=10&t=322) .  See post 3, exactly the same error.  Maybe everyone should stop using MintPPC too???!!!

Panchiron, it seems your computer is getting very hot because the CPU is very busy.  You shouldn't have gvfs-gdu-volume taking up so much processor time.  It is to do with mounting storage devices not sound as you might expect.  Do you use a flash drive/external usb device?  Have you done anything out the ordinary?  Try to find out when these processes start.  You should be able to kill them using "sudo kill number" where number will be the PID number given by "top".

I am a little concerned that maybe your fan is kicking in too late now (since it seems to be taking a long time to cool down in OSX too) so we really need a temperature readout.

---

### Post by linuxopjemac on 2011-09-16
Ok, next time I will refrain from giving advise on this forum.

---

### Post by rsavage on 2011-09-16
Panchiron, I've had a quick (well quite a big actually) look for information about the TiBook, but haven't found much. This is some general information about what you need to read temperature [http://sensors-applet.sourceforge.net/index.php?content=requirements](http://sensors-applet.sourceforge.net/index.php?content=requirements) . You could try installing acpi and lm-sensors packages to make sure you have everything (just in case!). I'm not an expert though and don't want to come across as one. I only know about my iBook model. I think once you find out what is causing the high CPU usage you'll be sorted. You could try asking on the other ubuntu forums about gvfs-gdu-volume as I don't think this is a powerpc specific problem. It would be good to hear from other TiBook users as they will know the best about the fan in linux. If you need to adjust the fan limits, then this method [http://ubuntuforums.org/showthread.php?t=1358034](http://ubuntuforums.org/showthread.php?t=1358034) may work. Also, install powerprefs and run it from the terminal by typing "powerprefs". That might have some setting about the fan, but I can't remember.
 
> **linuxopjemac said:**
> It's possible that this kernel module is not available in the stock Ubuntu kernel. It's available in Debian though. I cannot recommend using a Linux system without this module. It can harm your hardware if you let it become too hot.
 
Just to allay any fears, the adt756x chipset is not used in every powerpc computer. Therefore, it can be entirely normal not to have this module loaded. The statement by Linuxopjemac is erroneous. The G4 iBooks and AlBooks use the chip, therefore they should have it loaded. Researching Panchiron's problem I've read that some people who have AlBooks actually don't load the module on purpose because they say the fan works better without it (EDIT: they were probably experiencing an unpatched kernel bug [http://ubuntuforums.org/showthread.php?t=1372506&page=2](http://ubuntuforums.org/showthread.php?t=1372506&page=2))! So it's up to people to use their judgment. They know their machines best.

---

### Post by OriOs on 2011-09-16
Hi Panchiron,

I was wondering, if your CPU runs havoc, can't you find out why with the "top" command? 
Maybe there's a mad killing process... :popcorn:

If you find sth that takes up the majority of the CPU ressources, then you could try to start searching if it's not an already resolve issue with the TiBook (PPC+name.of.the.process+linux for example).

Edit: Have you tried the CD from the Lubuntu Team (by the way thanks for the heads up rsavage, it looked a bit heavyweight compared to flwm but still, it ran quietly :) )

---

### Post by Panchiron on 2011-09-17
Hi!

I really appreciate all your efforts in trying to help me to solve this problem. As I said before, now I´m back to Mac OSX, beacuse I have to be sure about my fan working appropiately.

I have added 128 M of RAM and maybe in a short therm will come back to Linux. 

Just for information, I have to say that these issues about temperature and fan only appeared when running this Lubuntu approach, while with Ubuntu or Xubuntu installed through the respective Alternate Cd´s they worked as expected.

Thank you and greetings!

---

### Post by Panchiron on 2011-09-19
Well, now with 384 Mb of RAM, I have installed Ubuntu 10.10 through the Live CD for my testing purposes.

I can confirm that the fan behaviour is back to what is expected to be. So, if I can solve an issue with my Wifi PCI card, I think I&#7743; going to stay on Maverick for a while.

Greetings!

---

### Post by Panchiron on 2011-09-20
Still investigating!

I guess my cpu (667 Mhz) does not support cpu Scaling.

Greetings!

---

### Post by rsavage on 2011-09-20
Panchiron, what are you investigating!?!  I thought you had maverick installed?  If you have normal ubuntu installed you'll be able to add the CPU frequecy scaling monitor to your top panel.

---

### Post by Panchiron on 2011-09-21
> **rsavage said:**
> Panchiron, what are you investigating!?!  I thought you had maverick installed?  If you have normal ubuntu installed you'll be able to add the CPU frequecy scaling monitor to your top panel.

Yes, I had gone back to Ubunut 10.10, and when added the CPU frequency scaling monitor to my top panel, the result was that the frequency staid at 667 Mhz no matter what option I choosed (ondemand, powersave...).

And if I asked for the availiable frequencies via Terminal, it showed only 667Mhz. So, I guess my processor does not support CPU scaling or I&#7743; too newby for this issue.

Now I&#7743; giving a try to MintPPC. Soon I will be over there "complaining" :p

Greetings!

---

### Post by rsavage on 2011-09-21
If that is the case then I think you may be right about not having frequency scaling.  kernel.org is down at the moment, but I did have a look at a cached page on google and the 667 G4 is not listed under frequency scaling.

As I've said before I think your fan problem with lubuntu was caused by the runaway processes you had in "top".  The fan was working, it was just that your CPU was very busy so was getting hot, hence the fan.  A re-install or upgrade to 11.10 may have fixed this.  

I was happy to reply to your posts, it was nice to know that somebody had tried the guide!

Good luck with MintPPC!

---

### Post by Ms. Daisy on 2011-10-18
> **Panchiron said:**
> Yes, I had gone back to Ubunut 10.10, and when added the CPU frequency scaling monitor to my top panel, the result was that the frequency staid at 667 Mhz no matter what option I choosed (ondemand, powersave...).And if I asked for the availiable frequencies via Terminal, it showed only 667Mhz.
@ rsavage: Feel free to mount my avatar on your wall and throw darts at it if you're sick of seeing it  :tongue: It kinda seems like Panchiron is describing the same CPU problems that I had. The problem doesn't seem to be too terribly common. But because there doesn't seem to be a fix (that we could implement anyway), maybe it warrants a mention in your tutorial?  I'd be happy to take a crack at it if you'd like. (the mention in the tutorial... not the Emac). When I upgrade to 11.10, I'll let you know if it solves the CPU problem.

---

### Post by canhoto on 2011-10-20
Sorry for asking, but can't you just install with the [Oneiric]("http://cdimage.ubuntu.com/lubuntu/daily/current/oneiric-alternate-powerpc.iso") alternate CD?

---

### Post by rsavage on 2011-11-02
Just in case anybody hasn't noticed..... I've edited the original post and some of the links over the last few days to try and get them up to date with 11.10!

@Ms. Daisy - the udev bug is now top of my 'General Workarounds' section!

---

### Post by Ms. Daisy on 2011-11-02
> **rsavage said:**
> @Ms. Daisy - the udev bug is now top of my 'General Workarounds' section!Saw that- thanks! And I'm happy to report that upgrading to 11.10 solved the udev bug.

---

### Post by Cloudane on 2011-11-25
Many thanks for this tutorial.  Certainly breathed some life into my ageing G4 Powerbook that has been sat gathering dust for a few years!

As I'll be using wireless, is there any way to disable its attempts to bring the wired network up on boot?  It sits for ages waiting for an address that it's not going to get, then says it's going to wait another 60 seconds, then finally boots up.  That's pretty much the only thing I've noticed "wrong".  (Sleep doesn't work, but it never has on the 12" model AFAIK).  Great stuff.

---

### Post by rsavage on 2011-11-25
That's a new one on me! What are you running - Ubuntu 11.10?  What about Network Manager or Wicd?
 
You may be better asking on the Network & Wireless forum as I am pretty clueless at this sort of thing.  From a quick search I got this post [http://ubuntuforums.org/showthread.php?t=1844819](http://ubuntuforums.org/showthread.php?t=1844819) .
 
Let us know if you find the solution and thanks for the kind comments!

---

### Post by Cloudane on 2011-11-26
Thanks for that.  I'm using 11.10 (installed 11.04 CLI then upgraded then installed the desktop) and Network Manager.

Network Manager is definitely being a little weird - e.g. it's connected to the wifi fine but the signal indicator appears in the menu bar all grey as if it has no signal.

Anyway I commented out the eth0 lines in /etc/network/interfaces and that's worked around the problem.. it's rare that I have to use wired networking so I'll just put it back in if I need it.  (I think what's supposed to happen is that it stays disabled until it detects a cable being plugged in but maybe that's not working)

---

### Post by rsavage on 2011-11-26
> **Cloudane said:**
> Network Manager is definitely being a little weird - e.g. it's connected to the wifi fine but the signal indicator appears in the menu bar all grey as if it has no signal.

Yeah, others have mentioned this.  Sorry, not looked into it.  Glad you got the other problem sorted!

---

### Post by rsavage on 2011-12-04
Hello everybody, just to let you know post 1 has had a lot of tweaking over the weekend with many new sections added.  Hope you like it!

---

### Post by Ms. Daisy on 2011-12-04
> **rsavage said:**
> Hello everybody, just to let you know post 1 has had a lot of tweaking over the weekend with many new sections added.  Hope you like it!I LOVE it!!!!

---

### Post by rsavage on 2011-12-15
Thanks Ms D!

More editing of instructions has taken place.  Mainly to the screen troubleshooting section, but also some general tidying up has taken place.  As always, if you spot a problem with them or don't think they make sense then let me know.....

---

### Post by rsavage on 2011-12-18
Updated the flash section and added a USB booting section.  Check them out!

---

### Post by Rmurphy29 on 2012-01-11
> **rsavage said:**
> Updated the flash section and added a USB booting section.  Check them out!

Hello,

Thanks for all of the effort put in to explaining this. 

In regards to USB booting, I have an iBook G4 that I've been trying to get to boot from USB with no luck. It wont boot from the boot screen, so I went into OF and now it keeps giving me a "load size too small" message. I've tried 4 different usb sticks and have partitioned them several different ways to see if it's a read problem and still get the same message.

The main issue is that my CD drive doesn't work, this is a Frankenstein computer and to be honest, I don't feel like taking it apart for the 50th time to replace the drive....

I've read a bit about using fire wire to connect to my working Powerbooks CD drive, and booting from that, but I wanted to get some opinions before I waste money on fire wire and a lightning bolt adapter. Is there any other way to boot ubuntu LTS on an otherwise working iBook G4? 

I would give a more detailed description of the OF commands and results, but I'm work at the moment. I essentially followed your instructions word for word. It seemed to work up until the last boot step. 

Thanks for the help!

---

### Post by rsavage on 2012-01-11
That's wierd. I think maybe your iso is corrupt? Have you tried running the commands 'md5sum' and 'sha1sum' to see if the checksums are correct? Or trying a different iso?
 
How are you copying to the usb stick? There are some very vocal people who are adamant you can't do it from an intel machine. I have done it though without any problems whatsoever, but maybe there is a problem with some machines?
 
I agree the iBook is a total pain to take apart! I am quite expert at it now! An Oyster card (London underground card) is the perfect implement to split the plastic casing without damaging it!
 
You can do a boot over the network. Never done it, but this guy did it [http://ubuntuforums.org/showthread.php?t=1899469&highlight=imac](http://ubuntuforums.org/showthread.php?t=1899469&highlight=imac) . There are also instructions in the official guide [https://help.ubuntu.com/11.04/installation-guide/powerpc/index.html](https://help.ubuntu.com/11.04/installation-guide/powerpc/index.html) , or you can find more by doing a search.

---

### Post by Rmurphy29 on 2012-01-11
Thanks for the fast reply!

I'm installing it onto the usb stick using the instructions provided by Ubuntu on the download screen. It seems to work as described....From there after their boot instructions failed, I tried yours and several others to no avail. It seems that it just won't recognize the USB stick as a bootable drive....

thanks for those very detailed instructions from Ubuntu, it may be a bit over my head, but I think I'll give them a shot.

Do you have any experience using a firewire connection to utilize a working macs optical drive as a bootable device?

Thanks again!

---

### Post by rsavage on 2012-01-11
> **Rmurphy29 said:**
> Thanks for the fast reply!
 
Sad init!
 
Okay, I have to ask, but you are using the PowerPC iso's aren't you?  I get a bit concerned when people start mentioning the main Ubuntu website.
 
I think this maybe your problem:
 
> 
Execute sudo dd if=/path/to/downloaded.img of=/dev/rdiskN bs=1m (replace /path/to/downloaded.img with the path where the image file is located; for example, ./ubuntu.img or ./ubuntu.dmg).

If I'm reading that correctly, they are copying with a block size of 1megabyte.  I would try setting that to 512 bytes.  It will take longer to copy, but may make the difference?
 
Have no experience with firewire I'm afraid.
 
If you've got a working powerbook then why don't you burn a 10.04 live cd and boot that on the powerbook?  You can then copy to the USB stick from linux and can cut out the conversion which could be the other thing causing the problem.

---

### Post by Rmurphy29 on 2012-01-11
> **rsavage said:**
> Sad init!
 
Okay, I have to ask, but you are using the PowerPC iso's aren't you?  I get a bit concerned when people start mentioning the main Ubuntu website.
 
I think this maybe your problem:
 

If I'm reading that correctly, they are copying with a block size of 1megabyte.  I would try setting that to 512 bytes.  It will take longer to copy, but may make the difference?
 
Have no experience with firewire I'm afraid.
 
If you've got a working powerbook then why don't you burn a 10.04 live cd and boot that on the powerbook?  You can then copy to the USB stick from linux and can cut out the conversion which could be the other thing causing the problem.

You know, that may be the problem! I hadn't realized there were separate isos for the LTS version....I dl'd it straight from [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download). 

where can I find the PPC isos? I thought it looked strange as it contained an .exe file, but I'm also not super familiar with mac supported file types....

I've also read in cruising around the mac forums that only a few PPC's will boot from USB, and most wont. I guess that seems a bit odd too, why would it be hit or miss?

To be perfectly honest, all of this is quite new to me. I'm basically just following directions with no knowledge of what the commands are actually doing! I've learned a lot in the process, but it's still quite daunting....

Thanks!

---

### Post by Ms. Daisy on 2012-01-11
> **Rmurphy29 said:**
> I've also read in cruising around the mac forums that only a few PPC's will boot from USB, and most wont. I guess that seems a bit odd too, why would it be hit or miss?
I  used to know the answer to this but cannot find my source now. All I can remember now is a vague fact: Some of the apple USB ports have lower capabilities. They're powerful enough to use for accessories, but they aren't powerful enough to support booting.  Especially with lower capabilities are USB ports on a keyboard (which I trust you're not using).

> **Rmurphy29 said:**
> To be perfectly honest, all of this is quite new to me. I'm basically  just following directions with no knowledge of what the commands are  actually doing! I've learned a lot in the process, but it's still quite  daunting....
You're in good hands with rsavage  ;)

---

### Post by rsavage on 2012-01-11
Hi Ms Daisy, nice to see you back on the Apple forum!
 
Back in the day no computer could boot from USB.  It's just a feature that got introduced along the way.  If your model is old school then it won't boot from USB.  I think pretty much all NewWorld macs can actually boot from USB.  I included in the first post a link to the Apple website which gives you the Apple models when it was introduced.  Whether you can still boot models before that via openfirmware I have no idea, I suspect not.
 
Like Ms. Daisy says, some are USB1 so are slow to boot, but you can still boot from them.  When USB2 arrived that made booting from USB much quicker.  
 
Rmurphy29, I think we found the problem.  You need a PowerPC iso.  See [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ) .  I haven't finished writing it yet, it is still a bit rough around the edges!
 
Ms. Daisy, there is a security section with your name on it!

---

### Post by Ms. Daisy on 2012-01-11
Nice job on the wiki, rsavage! 
> Keep the system updated via the Update Manager. Only  install/run software that you need and only install software from secure  and trusted sources (e.g. the Ubuntu repositories). Whilst a  person/website may provide a package or executable with good intentions,  can you be sure their server has not been hacked and the binary swapped  for something malicious? 

If you are running ssh or vnc, possibly as part of a server setup, then you do need to learn to secure them properly.  Careful there, you sound a bit like a security guy ;)

---

### Post by Rmurphy29 on 2012-01-17
> **rsavage said:**
> Hi Ms Daisy, nice to see you back on the Apple forum!
 
Back in the day no computer could boot from USB.  It's just a feature that got introduced along the way.  If your model is old school then it won't boot from USB.  I think pretty much all NewWorld macs can actually boot from USB.  I included in the first post a link to the Apple website which gives you the Apple models when it was introduced.  Whether you can still boot models before that via openfirmware I have no idea, I suspect not.
 
Like Ms. Daisy says, some are USB1 so are slow to boot, but you can still boot from them.  When USB2 arrived that made booting from USB much quicker.  
 
Rmurphy29, I think we found the problem.  You need a PowerPC iso.  See [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ) .  I haven't finished writing it yet, it is still a bit rough around the edges!
 
Ms. Daisy, there is a security section with your name on it!

Thanks again for the help!

I've downloaded the ISO and now I get a message saying something like "can't boot file: install\yaboot" 

It actually changes to a black screen for a minute, so it wants to boot! I'm going to try a different version and see if that helps....

Any suggestions?

Thanks!

---

### Post by rsavage on 2012-01-17
> **Rmurphy29 said:**
> 
Any suggestions?

 
Nope!
 
Sorry, openfirmware is a total mystery to me! Sounds like it has found the yaboot file so I have no idea why it is not booting. Have you tried another iso?

---

### Post by swamp-rock on 2012-01-20
Thanks for posting these instructions. I got as far as installing Lubuntu (11.04) on my dual-processor 500 Mhz G4, and was having problems with 100% CPU load at idle, and bog-slow operation. Checking the kernel, I found that it installed the single processor kernel. I installed the SMP kernel and voila, took care of that problem. I was pleasantly surprised to see Firefox 9.0.1 was installed as well (I used your script; uploaded it to my webspace and wget-ed it). Now to install Xubuntu (although I do like the speediness of Lubuntu) and set up a dual-boot MintPPC/Xubuntu G4 box.

This is my first week in a looooooooong time (years; I last used Red Hat, then Mandrake from 1999 to 2001!) with linux and I'm having a blast learning and tweaking. It's definitely come a long way in a decade.

Thanks again!

---

### Post by rsavage on 2012-01-21
Wow, thanks for drawing my attention to this! It is something that had completely passed me by! I wonder how many dual-processor people are only running on one processor?
 
Could you expand a little on what you did? I started putting some notes together for the FAQ, but soon realized I hadn't a clue. I have no access to a linux machine at all at the moment so can't test anything.
 
Do you know if you can install a SMP kernel via the 'cli-expert' option?
 
I'm wondering if there is a difference between 64bit and 32bit regarding SMP?
 
If you (or anybody else) could add something to the PowerPC FAQ or tell me more here (and then I will add it to the FAQ) then that would be great! Thanks
 
p.s. I'm also wondering if you have the udev/udisks bug that a lot of people in 11.04 got. It might be worth sticking a CD in the drive to see if your processor use dramatically goes down!

---

### Post by rsavage on 2012-01-21
> **swamp-rock said:**
> I was pleasantly surprised to see Firefox 9.0.1 was installed as well 
 
Yeah, I wasn't thinking when I put 'Firefox 5' in the title of this thread!  If some friendly mod could delete '11.04 with Firefox 5' from the title I would be most grateful!
 
Regarding Xubuntu - you need to turn on compositing to get transparency and shadows and stuff.  If you need help with this (do you have a rage 128?) then give us a shout.

---

### Post by swamp-rock on 2012-01-23
> **rsavage said:**
> Wow, thanks for drawing my attention to this! It is something that had completely passed me by! I wonder how many dual-processor people are only running on one processor?
 
Could you expand a little on what you did? I started putting some notes together for the FAQ, but soon realized I hadn't a clue. I have no access to a linux machine at all at the moment so can't test anything.
 
Do you know if you can install a SMP kernel via the 'cli-expert' option?
 
I'm wondering if there is a difference between 64bit and 32bit regarding SMP?
 
If you (or anybody else) could add something to the PowerPC FAQ or tell me more here (and then I will add it to the FAQ) then that would be great! Thanks
 
p.s. I'm also wondering if you have the udev/udisks bug that a lot of people in 11.04 got. It might be worth sticking a CD in the drive to see if your processor use dramatically goes down!

I didn't install the kernel until after lubuntu was installed. I just used Synaptic from the default desktop and rebooted. I figured I should check this out since MintPPC 9 and 11 gives you a choice of kernels, but the lubuntu mini iso didn't. Sure enough- single processor kernel.

Not sure about cli-expert, but I suppose it's possible. I haven't messed with that option yet (still an "old newbie" just returning) but I'll somewhat assume it probably gives you a choice of kernels...?

I *do* have the bug, but it's not as noticeable with the SMP kernel. I haven't upgraded the installation to 11.10 yet, but will do so in the next few days. I had the bug on my Powerbook G4 as well and upgraded the install, but I've got other issues with that now (see below) that I need to work out. Time is a bit short for the next couple of days but I'll return to this on Wednesday (USA).


> **rsavage said:**
> Yeah, I wasn't thinking when I put 'Firefox 5' in the title of this thread!  If some friendly mod could delete '11.04 with Firefox 5' from the title I would be most grateful!
 
Regarding Xubuntu - you need to turn on compositing to get transparency and shadows and stuff.  If you need help with this (do you have a rage 128?) then give us a shout.

I have a Mobility Radeon with 16 Mb RAM in my TiBook: [http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_667.html](http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_667.html)

My DP500 Powermac G4 has a flashed Geforce 5200 with 128 Mb RAM. More details about OpenGL and other specs when I have time in a few days (gotta fire up the box)

Will give a shout, once I work out why xubuntu and xfce sessions won't log in and return to the login screen, why I get Xsession errors when I run an "openbox session" ("unable to launch "/use/share/xsessions/openbox.xsession"... says "not found; falling back to default session" and loads/works otherwise), and why "openbox" doesn't give me a desktop (but gives me a wireless connection dialog.... weird). This is all on my TiBook. More details in a few days. Thanks!

---

### Post by leetripper on 2012-01-24
I'm running Lubuntu 11.10 on my ibook g3 following the PowerPcFaq and almost everything runs. I had to switch to Wicd to get wireless working. I had to assign a static IP to make it work with my FritzBox. 
Minitube works fine, Totem also. Only Ubuntu Mplayer doesn't work on G3, but the one from the Debian wheezy repo does... so, could it be recompiled?

---

### Post by rsavage on 2012-01-25
@leetripper 
 
Yes you could compile it - there are instructions linked in the FAQ to do this. It is probably easier to try a previous version of mplayer though. The deb of the one from 11.04 is here [http://ports.ubuntu.com/pool/universe/m/mplayer/mplayer_1.0~rc4.dfsg1-1ubuntu3_powerpc.deb](http://ports.ubuntu.com/pool/universe/m/mplayer/mplayer_1.0~rc4.dfsg1-1ubuntu3_powerpc.deb) . I don't have any linux machine now so I can't give you precise instructions to install. I think synaptic gives you the ability to hold a package version or else you will have to apt pin it to stop it getting upgraded.
 
It might be one of the other packages causing the problem though?
 
Are you sure it works in debian wheezy as last I heard there was a problem there with non altivec?
 
If you fix it please add something to the PowerPC Known Issues page. If everybody using PowerPC Ubuntu can help out in just a small way it would really make a difference.
 
@swamp-rock
 
Can't help you with your errors I'm afraid! I've added stuff about SMP to the FAQ. If you find out if cli-expert works can you add something to the FAQ please? Thanks!

---

### Post by swamprock on 2012-02-08
> **rsavage said:**
> 
 
@swamp-rock
 
Can't help you with your errors I'm afraid! I've added stuff about SMP to the FAQ. If you find out if cli-expert works can you add something to the FAQ please? Thanks!

The problems were of my own doing. Installing desktops, then uninstalling others will screw some things up. I've since wiped the drive and was going to try again when I had time (work is taking up most of my time these days)...

BUT...

I've come into possession of a G5 (soon, two of them!) and want to use this guide to install Lubuntu/Xubuntu, as well as install the SMP kernel. I'll do this and report back as soon as I can (which should be soon since I'm off work due to a hand injury). Once I tweak the G5, I'll return to the G4 and work out some other issues I've come across...

---

### Post by knm on 2012-02-09
Hi, total beginner here in linux and lubuntu...

First of all, thank you so much for such a detailed instruction/explanations.
I have Gowerbook G4 12" with me and have successfully loaded 11.04 and then upgraded to 11.10.

But when after installing Lubuntu through the command line, and rebooting the system, I am still getting the CLI login instead of any GUI.

Am I missing something? like an edit to Xorg.conf? 

I'm a total newb so I'd greatly appreciate any advice.

Thank you.

---

### Post by rsavage on 2012-02-09
Very much depends on what machine you have and the graphics card.  If you have a  G3 iMac then yes you will have to setup a xorg.conf.  If you have a rage 128 then you may have to load some modules.  It's described in the configure graphics section (3.7) of the first post or take a look at the section of the FAQ [https://wiki.ubuntu.com/PowerPCFAQ#Configure_graphics](https://wiki.ubuntu.com/PowerPCFAQ#Configure_graphics) which maybe descibes it better.

---

### Post by rsavage on 2012-02-09
Sorry totally missed you have written what machine you have!  What's the graphics card?

---

### Post by knm on 2012-02-09
Hi rsavage,

I checked my graphics card using "lspci", and said the following.

VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200] (rev a1)

I was actually trying to read through the OP, but I couldn't find how my graphics card should be treated...
Again your guidance is very appreciated.

---

### Post by rsavage on 2012-02-10
Can you check the xorg server (the graphical environment) is trying to start.
 
Once logged in type
 
nano /var/log/Xorg.0.log
 
(Note the capital X.  Also the zero between Xorg and log)
 
That should give you a whole load of stuff. At the bottom of the page should be the problem. You'll probably have an error about no screens detected, but what are the errors/warnings above that?
 
You could also try at the second yaboot prompt
 
Linux nouveau.modeset=0
 
This should boot, but you'll have rubbish colours.

---

### Post by knm on 2012-02-11
****Hi rsavage,

Sorry couldn't get back to you sooner, but since I couldn't get to load the Lubuntu, I have re-started from the beginning and installed 11.04 and 11.10.

And what I have realized is that in the previous installation I have missed running the script that you have mentioned in the OP. 

And now I have my powerbook running with Linux, and am typing on this post using that very powerbook.

But now, I'm struggling with other issues, such as;
1) No battery status (i.e. cannot access power management, and the battery status always shows 0% whether i"m charging or discharging)
2) No menu available to change the mouse setting, in order to change the touchpad setting to disable click on touch.
3) Change screen brightness, and use brightness keys to control the level of brightness.

I went through the OP and tried several methods (like resetting PMU & NVRAM, etc) for #1 but have not been successful, and for #2, and 3, I couldn't find a right solution....

Please let me know if you have any specific approaches for the above issues.

Thank you.

---

### Post by rsavage on 2012-02-12
The op doesn't really cover 11.10 in detail because I have never used it.   The lubuntu power manager thingy changed in 11.10 so the command/instructions to get the applet going will be different.  Probably have a look at the lubuntu wikis - they are very good.
 
Battery [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_get_a_working_battery_indicator.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_get_a_working_battery_indicator.3F)
 
Touchpad [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_control_trackpad_behaviour.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_control_trackpad_behaviour.3F)
 
Brightness [http://www.mintppc.org/forums/viewtopic.php?f=15&t=773](http://www.mintppc.org/forums/viewtopic.php?f=15&t=773) (although there is probably a better/more correct way)

---

### Post by wayover13 on 2012-02-15
Hi. I've got an eMac G4 I'm working at. The 12.04 live CD boots fine. I'm actually inclining toward building up a system from a Debian netinstall, though. I've gotten partway through that process but have run into some issues I'd like to ask about.

First, I want a dual boot--OSX alongside Linux. This machine has a 40 GB hard drive. If I didn't want to dual boot, I'd be up and running by now. But I'm still trying to get this to work.

I started by shrinking the HFS partition using parted. Booted back into OSX afterward to confirm it still worked--it did, apart from the fact that the Mac partition was now completely full (7.5 GB--this is a fresh install of OSX [10.04], btw). Then I started the Debian installation process thereafter.

Things started to go wrong when Debian couldn't find the place to install yaboot--some kind of NewWorld boot partition, as I recall. I tried to straighten that out by making the two small initial disk partitions bootable, but still no joy. Now, moreover, I think I fapped up the partition table as OSX won't finish booting now.

But what I want to ask here to begin with is whether I can expect to dual boot Linux (either Debain or Lubuntu) and OSX on a HD of this size? I'll need to somehow acquire installation media to repair OSX--probably requiring a reinstallation. Will the NewWorld boot partition issue straighten itself out once I do that? Is OSX willing to install itself on a pre-sized partition, or does the OSX installation routine allow for partition sizing?

I've installed Windows/Linux dual boot systems numerous times. But this OSX thing is brand new to me. Input will be appreciated.

Thanks,
James

---

### Post by wayover13 on 2012-02-16
> **wayover13 said:**
> Things started to go wrong when Debian couldn't find the place to install yaboot--some kind of NewWorld boot partition, as I recall. I tried to straighten that out by making the two small initial disk partitions bootable, but still no joy. Now, moreover, I think I fapped up the partition table as OSX won't finish booting now.
I discovered what was the issue here on a subsequent installation attempt. You have to select a NewWorld boot partition as part of the disk set-up process, and I neglected to do that. I'm pretty familiar with partitioning and so forth, but had never before seen the option in a Linux install of selecting and using such a partition--not surprising since this is the first time I've ever tried installing Linux to a Mac.

But that doesn't explain how the partition table went awry: maybe because I didn't disable journalling in OSX prior to resizing the partition? Dunno yet.

James

---

### Post by wayover13 on 2012-02-18
> **wayover13 said:**
> But what I want to ask here to begin with is whether I can expect to dual boot Linux (either Debain or Lubuntu) and OSX on a HD of this size? I'll need to somehow acquire installation media to repair OSX--probably requiring a reinstallation. Will the NewWorld boot partition issue straighten itself out once I do that? Is OSX willing to install itself on a pre-sized partition, or does the OSX installation routine allow for partition sizing?
Yes, it will be possible (having done it, I can now state that with confidence). I did acquire installation media and performed a re-installation. I did things sort of backward in that I first installed Debian for powerpc, creating a 15GB partition alongside the Debian partition (ahead of the Debian partition on the disk, actually--not sure how important that is) as a place to later install OSX. The version of fdisk that comes with Debian for ppc allows easy creation of the NewWorld boot partition too, btw. Once that was up and running, I acquired and ran the OSX installation, which saw and was able to use the aforementioned 15GB partition. Having finished that, I was at first unable to boot again into Debian, since the Mac bootloader had sort of taken over. But it was very easy to restore the ability to boot Debian: just hold down the command-alt-p-r keys during boot, which restores the previous booting arrangement. Then, it was very easy to add OSX to yaboot--I used directions found on the Ubuntu wiki for that (see [https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot](https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot) ). So, I can report success at last.

James

---

### Post by Eudaimon on 2012-09-19
Savage, as an attempt not to cross-post, I'm going to transfer my comments from the [USB install thread]("http://ubuntuforums.org/ubuntuforums.org/showthread.php?t=2051337") to this one.   At this point I've got Ubuntu 10.04 up and running on my old Powerbook G4, and trying to switch over to Lubuntu.  

I tried using your script on page 1, to no avail.  After doing all the steps, and terminal finished, and rebooted, it started up in Ubuntu again.  Was I supposed to boot up in open firmware and open the new desktop or something?

Again, sorry for my ignorance (total newbie), but I don't quite understand how to switch over to Lubuntu.  I did all the terminal commands you wrote, and hoped that upon reboot it would say Lubuntu rather than Ubuntu.  Alas it did not! Any suggestions?

---

