---
title: "installed 6.10 and wifi still wont work =( help"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by da1nonlymikeo on 2007-03-14
hey guys,

 i just installed ubuntu 6.10 on my HP pavilion dv6000 lapy. and the wifi isent working.  when i go to network settings the wireless eth1 shows up and i enable it. but the internet dosent work. what should I do??

lspci:

mike@mike-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)
05:08.0 Ethernet controller: Intel Corporation Intel(R) PRO/100 VE Network Connection (rev 02)

---

### Post by airencracken on 2007-03-14
Ouch. You have the Broadcom 4311

Look at these threads and see if they help.

[http://ubuntuforums.org/showthread.php?t=362205&highlight=broadcom+4311](http://ubuntuforums.org/showthread.php?t=362205&highlight=broadcom+4311)

[http://ubuntuforums.org/showthread.php?t=381241&highlight=broadcom+4311](http://ubuntuforums.org/showthread.php?t=381241&highlight=broadcom+4311)

[http://ubuntuforums.org/showthread.php?t=315626&highlight=broadcom+4311](http://ubuntuforums.org/showthread.php?t=315626&highlight=broadcom+4311)

---

### Post by siciliancasanova on 2007-03-14
```
02:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)
```

That's your wireless card.  Have you used ndiswrapper for your driver yet?

---

### Post by da1nonlymikeo on 2007-03-14
im following the directions on this [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

and im on step 5 at the part that sais..

If all you see is the driver, but there is no message displayed about the hardware being present, then you need to tell ndiswrapper to use your driver with your device. You will need to determine what the device ID is by typing 'lspci -n' or 'lsusb'. Once you have the device ID, then use the driver:

when i do lspci -n i get..

mike@mike-laptop:~/bcm4311$ lspci -n
00:00.0 0600: 8086:27a0 (rev 03)
00:02.0 0300: 8086:27a2 (rev 03)
00:02.1 0380: 8086:27a6 (rev 03)
00:1b.0 0403: 8086:27d8 (rev 02)
00:1c.0 0604: 8086:27d0 (rev 02)
00:1c.1 0604: 8086:27d2 (rev 02)
00:1d.0 0c03: 8086:27c8 (rev 02)
00:1d.1 0c03: 8086:27c9 (rev 02)
00:1d.2 0c03: 8086:27ca (rev 02)
00:1d.3 0c03: 8086:27cb (rev 02)
00:1d.7 0c03: 8086:27cc (rev 02)
00:1e.0 0604: 8086:2448 (rev e2)
00:1f.0 0601: 8086:27b9 (rev 02)
00:1f.1 0101: 8086:27df (rev 02)
00:1f.2 0106: 8086:27c5 (rev 02)
00:1f.3 0c05: 8086:27da (rev 02)
02:00.0 0280: 14e4:4311 (rev 01)
05:08.0 0200: 8086:1092 (rev 02)


then the post tells me to do this.

run:
user@ubuntu:~/bcm4311$ ndiswrapper -a 14E4:4324 bcmw15

Make sure you fill in '14E4:4324' with YOUR device id, and 'bcmw15' with your driver.

wich one is my device id and driver?? im so confused.

---

### Post by siciliancasanova on 2007-03-15
14e4:4311 is the ID and the driver is the one you installed from the net

That's your device driver.  Also if it gets really hairy there is a GUI called NDISGTK to install your driver, it is less supported but it worked for me.

---

### Post by da1nonlymikeo on 2007-03-15
i get..

mike@mike-laptop:~/bcm4311$ ndiswrapper -a 14E4:4311 bcm4311
ls: /etc/ndiswrapper/bcm4311/: No such file or directory
driver 'bcm4311' is not installed (properly)!
mike@mike-laptop:~/bcm4311$ 


buttt i might of messed somthing up here..

Step 6 - Install the device and configure the network settings

Issuing an iwconfig command should reveal that your device is waiting to be configured, similar to this one:

user@ubuntu:~/bcm4311$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:11 Mb/s
          RTS thr:2432 B   Fragment thr:2432 B
          Power Management:off
          Link Quality:95/100  Signal level:-35 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

If your device shows up as wlan0 then you should be able to put your data in through the System-->Administration-->Networking applet.

(If your wireless device initially shows up as eth1, go back to step 2 and comment out the eth1 line in /etc/iftab. Then resume the rest of the instructions. If you don't comment out the eth1 entry, ndiswrapper won't be able to alias the device as wlan0.)


i get..

mike@mike-laptop:~/bcm4311$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.



It comes up as eth1? its supposed to be wlan0 rite?

---

### Post by siciliancasanova on 2007-03-15
Ok try this, this is what worked for me and it might work for you...

Install WINE from synaptic package manager

Then extract the downloaded driver to your desktop (if you right click it will say something about extracting with WINE)

Go back to synaptic and install NDISGTK

Then go to System > Admin > Wireless (I'm not on ubuntu right now, installing feisty fawn so I'm not sure what it's called at the end, it's Wireless Manager or something)

Then click "Install New Driver" and browse the driver you extracted on your desktop.  Locate the .inf file.  That's the file you want to install, then once you're there you can go back into the network admin and configure your wireless,

a good program to install for wireless is "wifi-radar" it detects networks that you're in range of.

I won't be back infront of ubuntu for about an hour so if anyone else wants to help that would be great, otherwise you will need to wait til I get on to help you out.

---

### Post by da1nonlymikeo on 2007-03-15
great. i just finished al that cr a p and rebooted and of cource it dident work and now that laptop dosent even work wile pluged into the modem. so no wifi, no ethernet. im about to say scre w ubuntu. is it possible to get any internet connection back?

---

### Post by da1nonlymikeo on 2007-03-15
if i get any internet connection at all i'll try your method by instaling wine and everything.

---

### Post by siciliancasanova on 2007-03-15
Reinstall ubuntu :)  No worries, if you reinstall it we will help you set it up right.  There's A LOT of instructions out there and some are faulty or irrelevant to you (as I found out, screwed up my graphics card, why I'm just going to feisty fawn)

---

### Post by siciliancasanova on 2007-03-15
Reinstalling is the easy way out, to fix your problem you will need to get even more hairy than you already were :(

---

### Post by da1nonlymikeo on 2007-03-15
haha dam n. what a pain in the a s s. this is going to be my 3rd time messing it up and reinstalling because i cant get any wireless connection. thanks for your help ill be back in about 3 hours after it finished reinstalling and doing all the fugin 21443 updates.

---

### Post by siciliancasanova on 2007-03-15
Ok see you then :)

---

### Post by da1nonlymikeo on 2007-03-15
okay im back and good to go. i downloaded wine. where do i get that driver from?

---

### Post by siciliancasanova on 2007-03-15
You get it from the site of the card, so if it's a linksys you would get it from linksys.com ... d-link, from d-link.  Search your product on the site and download the driver.

---

### Post by da1nonlymikeo on 2007-03-15
i followed this forum [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174) and i got it to work KIND OF?

 wifi radar finds my network now, but when i go to connect to it it sais couldent find ip.

 and when i right click on the network maniger in my top left screen, theres only eth0 and lo, theres no eth1 wich is my wireless card.

 what should i do?

---

