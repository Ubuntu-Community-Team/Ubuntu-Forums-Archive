---
title: "Error: Install Ubuntu 12.04 LTS in win8"
date: 2012-12-23
forum: Any Other OS
---

### Post by NingLiu on 2012-12-23
Dear All:
 
My computer is Asus G55, win 8 is installed in the SSD, and now I install the Ubuntu 12.04 LTS in a separated disc (NTFS), I've tried to install the 32 bit and also the 64 bit Ubuntu system, the installation is successed, and it want me to rebot the system. After I restart the computer and select the ubuntu. There are some error:
 
Windows Failed to start. 
"A recent hardware or software change might be the cause. To fix the problem:
1. Insert your windows installation disc and restart your computer. 
2. Choose your language settings, and then click "next." 
3. Click "Repair your computer." 
If you do not have this disc, contact your system administrator or computer manufacturer for assistance.
File: \ubuntu\winboot\wubildr.mbr
status: 0xc000007b
 
Info: The application or operating system couldn't be loaded because a required file is missing file is missing or contains errors.
 
Because I don't have a windows installation disc, how can I fix this error? it's really drive me crazy, thanks a lot in advance and Merry Christmas

---

### Post by verzx on 2012-12-23
There is your problem, wubildr try installing with USB or CD then it will most likely work :)

---

### Post by NingLiu on 2012-12-23
> **verzx said:**
> There is your problem, wubildr try installing with USB or CD then it will most likely work :)
 
So I'll try to use the USB for install it, thank you. But last time, I install ubuntu 10.04.4 on win 7, it's ok without any error.

---

### Post by oldfred on 2012-12-24
Is this a new computer with UEFI. With UEFI Windows uses gpt partitioning and wubi does not work with gpt partitioning.

Post this from liveUSB flash drive terminal.

       sudo parted /dev/sda unit s print

---

### Post by NingLiu on 2012-12-24
> **oldfred said:**
> Is this a new computer with UEFI. With UEFI Windows uses gpt partitioning and wubi does not work with gpt partitioning.
 
Post this from liveUSB flash drive terminal.
 
sudo parted /dev/sda unit s print
 
Thank you very much, this is a new computer, but I am not sure Asus G55 is using UEFI and gpt partitioning, and could you please tell me how can I check UEFI with my computer, where can I find liveUSB  flash drive terminal? 
 
Thank you and Merry Christmas
 I will try to use USB to install the Ubuntu.

---

### Post by oldfred on 2012-12-24
Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

    
After you download and install (not copy) the Ubuntu ISO to a flash drive, you should be able to boot it. And it should give two options UEFI or BIOS mode. Boot in UEFI mode and open terminal.  Also just test to see if Internet, video and other features seem to work ok with your system.

You will have to turn off Secure boot and should also turn off fast boot or quick boot as that often conflicts.

---

### Post by NingLiu on 2013-01-02
> **oldfred said:**
> Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
 
 
After you download and install (not copy) the Ubuntu ISO to a flash drive, you should be able to boot it. And it should give two options UEFI or BIOS mode. Boot in UEFI mode and open terminal. Also just test to see if Internet, video and other features seem to work ok with your system.
 
You will have to turn off Secure boot and should also turn off fast boot or quick boot as that often conflicts.
 
Thank you i have succesfully installed 12.04 on my laptop but I have a probem with lightdm..while booting the ubuntu i get "lightdm fail" and the tty promt is displayed.
 
I have a NVidia GEFORCE GTX 660M card in Asus G55 Laptop. Can you suggest me how to overcome this issue.

---

### Post by oldfred on 2013-01-02
I have a desktop with 9600GT nVidia card. I have to use nomodeset on first boot, so I can then install the nvidia driver. I assume the internal nVidia is the same.

If you can get to command line you can install nVidia from that also.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

    
       On first boot after install, press e on getting the GRUB bootloader menu. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

    
With 12.04 the headers should already be installed, but with 12.10 I had to install headers first.
       [http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for current version:
sudo apt-get install linux-headers-generic
# only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available  versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current, use version you prefer
sudo apt-get purge nvidia*
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett*

---

### Post by NingLiu on 2013-01-02
> **oldfred said:**
> I have a desktop with 9600GT nVidia card. I have to use nomodeset on first boot, so I can then install the nvidia driver. I assume the internal nVidia is the same.
 
If you can get to command line you can install nVidia from that also.
 
How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
 
 
On first boot after install, press e on getting the GRUB bootloader menu. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu
 
 
With 12.04 the headers should already be installed, but with 12.10 I had to install headers first.
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for current version:
sudo apt-get install linux-headers-generic
# only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current, use version you prefer
sudo apt-get purge nvidia*
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett*
 
Thank you very much, finally I see the Ubuntu in my laptop, and last question can I upgrade the Ubuntu?

---

### Post by oldfred on 2013-01-02
What do you want to upgrade already. 

12.04 is a long term support version, so you can have the same version until 2017.
       [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
    

It will offer to update itself periodically with current fixes and minor updates on a regular basis. If you want to check you can use Software Updater.

---

### Post by NingLiu on 2013-01-18
> **oldfred said:**
> What do you want to upgrade already. 

12.04 is a long term support version, so you can have the same version until 2017.
       [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
    

It will offer to update itself periodically with current fixes and minor updates on a regular basis. If you want to check you can use Software Updater.

Hello,  after I install the Ubuntu 12.04 with pendrive, it works well but still have one problem, when I start my computer, there are two operations, one is windows the other is Ubuntu, but when I select Ubuntu, it still show the same error as shown in the 1st floor. If I want to launch Ubuntu, I have to select using other operations, then select using USB, in USB, there also have a Ubuntu, I can launch Ubuntu by select this one. Could you please me to fix this problem? Thank you very much.

---

### Post by oldfred on 2013-01-18
Are you just booting the live version from the install flash drive?

But you get a grub menu that lets you choose Ubuntu or Windows from your internal hard drive? Have you tried recovery mode? Second Ubuntu line.

What error do you get?

---

### Post by NingLiu on 2013-01-19
> **oldfred said:**
> Are you just booting the live version from the install flash drive?

But you get a grub menu that lets you choose Ubuntu or Windows from your internal hard drive? Have you tried recovery mode? Second Ubuntu line.

What error do you get?

   	 	 	 	 	 	   [COLOR=#000000][FONT=Monospace][SIZE=2]Thank you for you quick reply, when I start the computer, I can see[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Monospace][SIZE=2]Choose an opearting system
1. Windows 2. Ubuntu

when I click Ubuntu, it shows this error

Windows Failed to start. 
"A recent hardware or software change might be the cause. To fix the problem:
1. Insert your windows installation disc and restart your computer. 
2. Choose your language settings, and then click "next." 
3. Click "Repair your computer." 
If you do not have this disc, contact your system administrator or computer manufacturer for assistance.
File: \ubuntu\winboot\wubildr.mbr
status: 0xc000007b

Info: The application or operating system couldn't be loaded because a required file is missing file is missing or contains errors

If I want to launch Ubuntu properly, I have to choose 
1. Change defaults or choose other options
2. Choose other options[/SIZE][/FONT][/COLOR]
 
[LIST=1]
[*][COLOR=#000000][FONT=Monospace][SIZE=2]Use 	a device[/SIZE][/FONT][/COLOR]
[*][COLOR=#000000][FONT=Monospace][SIZE=2]Ubuntu[/SIZE][/FONT][/COLOR]
[/LIST]
 

 [COLOR=#000000][FONT=Monospace][SIZE=2]Is it normal? Or are there some solutions to solve this problems. And will I lose all the document and softwares if I choose recov[SIZE=2]er[SIZE=2]y mode?[/SIZE][/SIZE][/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Monospace][SIZE=2][SIZE=2][SIZE=2][SIZE=2]Thank you [SIZE=2]very much[/SIZE][/SIZE]
[/SIZE][/SIZE][/SIZE][/FONT][/COLOR]

---

### Post by oldfred on 2013-01-19
Windows has two recovery modes. One is just Windows and is for repairing Windows. And it has a Vendor recovery which restores the entire system to as purchased or erases all your data. Best to have good backups.

The Ubuntu recovery mode is also for repairs. It tries to boot without video to see it that works and gives options on trying to repair or go to command line to manually do repairs.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

