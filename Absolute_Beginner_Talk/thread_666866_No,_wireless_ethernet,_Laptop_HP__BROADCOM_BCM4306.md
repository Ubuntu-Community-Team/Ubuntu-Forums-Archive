---
title: "No, wireless ethernet, Laptop HP  BROADCOM BCM4306 802.11b/g Wireless LAN Controller"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by ctoaun on 2008-01-13
Ok, I started with this post ([click here]("http://ubuntuforums.org/showthread.php?t=663581&highlight=wireless")) because for the computer&#8217;s manufacturer and wireless hardware matched my own. Below is the output, so far, it would seen that the process succeeded in erasing eth1.

Help would be appreciated. Are they&#8217;re no list of dependencies etc?


The first try with cabextract produce an error that repeated itself like 20 times

Here is the output on the second try:

**Terminal Output:**

user100@user100-laptop:~$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklistblacklist 

bcm43xx
user100@user100-laptop:~$ 
sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-utils-1.9
 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

user100@user100-laptop:~$ mkdir ~/bcm43xx; cd ~/bcm43xx
mkdir: cannot create directory `/home/user100/bcm43xx': File exists

user100@user100-laptop:~/bcm43xx$ sudo apt-get install cabextract
Reading package lists... Done
Building dependency tree  
     
Reading state information... Done
cabextract is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.


user100@user100-laptop:~/bcm43xx$ cabextract /home/user100/Desktop/BCMWL5.SYS
/home/
user100/Desktop/BCMWL5.SYS: no valid cabinets found

All done, errors in processing 1 file(s)

user100@user100-laptop:~/bcm43xx$ cabextract    /home/user100/Desktop/sp29361.exe

Extracting cabinet: /home/user100/Desktop/sp29361.exe
  
extracting bcm43xx.cat
  extracting bcm43xxa.cat
  
extracting bcmwl5.inf
  extracting bcmwl5.sys
  extracting bcmwl5a.inf
  
extracting bcmwld2k.exe
  extracting bcmwlhom.exe
  
extracting bcmwlhom.ini
  extracting bcmwlntp.sys
  
extracting bcmwlu00.exe
  extracting data1.cab
  
extracting data1.hdr
  
extracting data2.cab
  
extracting ikernel.ex_
  
extracting layout.bin
  extracting Setup.exe
  
extracting Setup.ini
  extracting setup.inx
  
extracting setup.iss
  extracting sp29361.cva

All done, no errors.

user100@user100-laptop:~/bcm43xx$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed

user100@user100-laptop:~/bcm43xx$ ndiswrapper -l
bcmwl5 : invalid driver!

user100@user100-laptop:~/bcm43xx$ sudo depmod -a

user100@user100-laptop:~/bcm43xx$ sudo modprobe ndiswrapper

user100@user100-laptop:~/bcm43xx$ sudo cp /etc/network/interfaces /etc/network/interfaces.orig

user100@user100-laptop:~/bcm43xx$ echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces

auto lo
iface lo inet loopback


user100@user100-laptop:~/bcm43xx$ echo 'ndiswrapper' | sudo tee -a /etc/modules
ndiswrapper

user100@user100-laptop:~/bcm43xx$ echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

ENABLED=0
user100@user100-laptop:~/bcm43xx$ 

user100@user100-laptop:~/bcm43xx$

**Post that did not help:**


Posts that do not help are as follows:
[http://ubuntuforums.org/showthread.php?t=345793](http://ubuntuforums.org/showthread.php?t=345793)
[http://ubuntuforums.org/showthread.php?t=133303](http://ubuntuforums.org/showthread.php?t=133303)

Step 7 in the post below might work if I knew what the &#8220;working directory&#8221; meant.
[http://ubuntuforums.org/showthread.php?t=340689&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=340689&highlight=BCM4306)

Other post that did not help
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

---

### Post by Tekno_Cowboy on 2008-01-14
If you are running 7.10 'Gutsy Gibbon', there should be working drivers included. What version are you running?

---

### Post by Jake90 on 2008-01-14
Well the Broadcom cards are not supported, if you want to use it you will have to use ndiswrapper. I had the same problem and tried to use ndiswrapper and it didn't work anyway. Too late I found a thread about HP laptops and how Gutsy is terrible for them and how none of the hardware is supported. As of now I am in the process of switching to Feisty.

---

### Post by Hal Story on 2008-04-09
> **Jake90 said:**
> Well the Broadcom cards are not supported, if you want to use it you will have to use ndiswrapper. I had the same problem and tried to use ndiswrapper and it didn't work anyway. Too late I found a thread about HP laptops and how Gutsy is terrible for them and how none of the hardware is supported. As of now I am in the process of switching to Feisty.
Thanks!  I found that Gutsy does not work with my HP/Broadcom either.  What did you do ?  If it workes, I will try it as well.

---

### Post by GrandpaLeaman on 2008-04-09
> **Hal Story said:**
> Thanks!  I found that Gutsy does not work with my HP/Broadcom either.  What did you do ?  If it workes, I will try it as well.

I have used this how-to ([http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)) in both Feisty and Gutsy and it works for me every time. Granted, it says it is a process for getting wireless working on a Dell E1505 with a Broadcom 1390, but the steps should be the same to get wireless working on your HP. The only step that should change is downloading and installing the correct driver for your specific wlan card. Give it a try and let us know if it works for you.

---

