---
title: "Please URGENT help!!!!!!-"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2007-05-05
a coouple of some BIG problems

My wireless card isn't working and no guide is useful for me ( it is a Broadcom Corporation Dell Wireless 1390 WLAN Mini-PC).
It is very important to mention I CAN'T CONNECT TO THE INTERNET so any information to downloiad something isn0t useful (the modem of the Laptop is not recognised by ubuntu)

I can't switch to Windows XP (so let's say my whole computher is withouth internet) because it says in the grub screen: Error 13: Invalid or unsupported executable format. I have Windows on the first partition, the second is empty and the third is Ubuntu (fourth is the other one created by ubuntu). and no guide has fucntioned with me.....

I am getting dispaired so please please please can anybody help me? PLEEASE!

---

### Post by srt4play on 2007-05-05
I'm sorry to say this but I think you're out of luck if you don't have another PC with internet access.

I have the same card in my laptop, and I had to download and compile ndiswrapper 1.39 to get it to work.  The version in synaptic is 1.38.

Good luck.

---

### Post by Happy_Man on 2007-05-05
Have you tried ndiswrapper?

---

### Post by Jorge32 on 2007-05-05
everybody had told me to us ndiswrapper but at one or other point there is one file that cant be installed or i dont know hwat is wrong
I have installed ndiswrapper 1.9 and I tried to install bcmw5.inf and bcmw15.inf files and it just open this message after ndiswrapper -l for both of them: Invalid driver!!

so please I need someone who has the same card (as you have so if you can help me ill be very grateful) so you can poass me the files you used and to tell me what to do in order to get it. please

---

### Post by srt4play on 2007-05-05
How did you install ndiswrapper?  Download from sourceforge.net?

---

### Post by Sef on 2007-05-05
Read [How to Restore GRUB]("http://doc.gwos.org/index.php/Restore_Grub").  That hopefully will get your Windows partition working.

This is what GRUB error 13 is > 13 : Invalid or unsupported executable format
    This error is returned if the kernel image being loaded is not recognized as Multiboot or one of the supported native formats (Linux zImage or bzImage, FreeBSD, or NetBSD).

---

### Post by Jorge32 on 2007-05-05
> **srt4play said:**
> How did you install ndiswrapper?  Download from sourceforge.net?

from the cd, via-synaptic package manager

---

### Post by GrueTamer on 2007-05-05
What I want you to do is

1. open up a terminal and type

```
gksudo gedit /boot/grub/menu.lst
```

2. Copy the windows boot options for grub

3. Paste the contents [here]("http://paste.ubuntu-nl.org/") and give me the link.

Maybe grub is configured wrong, that's what I'm thinking is wrong with it.

---

### Post by srt4play on 2007-05-05
> **Jorge32 said:**
> from the cd, via-synaptic package manager

Which is version 1.38, you need to download and compile 1.39 from sourceforge.net to get your card working.

---

### Post by liljoe76 on 2007-05-05
[http://ubuntuforums.org/showthread.php?t=384693](http://ubuntuforums.org/showthread.php?t=384693)
in my post you can click on the link to a wiki page for the broadcom 4311, plus some other relevant info. you will need an internet connection of some sort to dl the proper ndiswrapper and the driver. an internet cafe + usb stick.....
hope this gets you going.

---

### Post by Jorge32 on 2007-05-05
What else do I need to have at the moment of the installation? so i could download everything now from Windows and just install it on Ubuntu...


It's the Nwdiswrapper common 1.43, the nwdswrapper- utils 1.9 and....?

---

### Post by srt4play on 2007-05-06
Both the ndiswrapper driver and utils are included in the tar.gz package from sourceforge.  

Uninstall ndiswrapper and ndiswrapper-utils that you installed from the cd in synaptic.

Install build-essential from the cd in synaptic.

Open a terminal, then change directory to where the package was downloaded to then unpack ndiswrapper-1.43.tar.gz: 

tar zxvf ndiswrapper-1.43.tar.gz
cd ndiswrapper-1.43
make
sudo make install
sudo ndiswrapper -i /path/to/bcmwl5.inf

Be sure to blacklist bcm43xx in /etc/modprobe.d/blacklist and add ndiswrapper to /etc/modules

---

### Post by Jorge32 on 2007-05-06
I followed the steps and it didn't worked out :'(!!!
The only step that I did not followed (well except from all of getin through internet because I don't have internet in Ubuntu...) was the cabextract part, because in the guide it talks about a sp33008.exe and in HP webpage it said it was the sp34152.exe the one for this card.

at this point ```
user@ubuntu:~bcm4311$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"My_Essid"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:08:74:02:01:FC
          Bit Rate:11 Mb/s
          RTS thr:2432 B   Fragment thr:2432 B
          Power Management:off
          Link Quality:95/100  Signal level:-35 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

Wlan 0 didn't appeared, in fact it only appeared eth0 and eth1...
I tried to comment the eth1 with the "#" character and it still didn't appeared wlan

at this part ```
user@ubuntu:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
0.0.0.0         192.168.0.2     0.0.0.0         UG        0 0          0 wlan0
user@ubuntu:~$
``` only the life that says destination   gateway   genmask   flags   mss window   irtt iface   appears... nothing appears down.... any help? 
do you think that by changin the driver it will work?

---

### Post by srt4play on 2007-05-06
Don't follow the other guide anymore, I think it will just make it more difficult than following the steps outlined in this thread.

I've attached the broadcom wireless driver I used to get mine working.  Uninstall any driver you've installed:

sudo ndiswrapper -l

take note of the name of the driver it says is installed.

sudo ndiswrapper -e 'name of driver from above'

Then use the one attached to this post:

sudo ndiswrapper -i bcmwl5.inf

---

### Post by Jorge32 on 2007-05-06
It seems the problem is solved now, because when I entered the rescue mode in ubuntu in the screen appeared something as configuring network something and the button of the Wireless card turned on, I even now can switch it on or off during the login screen...
The problem is that after I enter my username and password the screen freezes and the welcome sound does not appear and after waiting a while a gray screen appears in the left side, but only a gray square I can't do anything and when I put the cursor over the square it changes as if it was a square where you can write or something like that...
So I pressed Ctrl+Alt+F1 and something like this appeared:```
starting up...
[    16.405802]  ..MP-BIOS bug:8254 Timer not connected to IO-APIC

Loadin please wait...
kinit: name_to_dev_t(/dev/sda4) = Sda4(8,4)
kinit: trying to resume from /dev/sda4
kinit: No resume image, doing normal boot

Ubuntu 7.04 ubuntu tty1

Ubuntu login:
```


I tried with ```
sudo /etc/init.d/gdm restart
``` and nothing happened, still the same problem again.
The problem is that since the beginning of the installation this ```
[    16.405802]  ..MP-BIOS bug:8254 Timer not connected to IO-APIC
``` appeared and still I had no problem.
Any ideas of what can be affecting me? any change from this guide can affect something?
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)?highlight=%28WifiDocs%2FDevice%29)


 Any ideas of how to fix it?

---

### Post by srt4play on 2007-05-06
Seems other have been affected by "bug:8254" as well..

[http://ubuntuforums.org/showthread.php?t=191355&highlight=bug%3A8254](http://ubuntuforums.org/showthread.php?t=191355&highlight=bug%3A8254)

---

