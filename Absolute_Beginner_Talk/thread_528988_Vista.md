---
title: "Vista"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by indie56 on 2007-08-18
Hello
I have bought a Acer 3680 with Vista Basic edition and have created the recovery discs (6). I installed 7.04 without resizing the drive. (Actually I was trying to make the laptop dual boot.) [http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2). By mistake I used page 2 instead of page 3. It now boots up in 7.04 ONLY. How do I make it boot in Vista or 7.04. I tried using the Vista recovery discs to reformat but to no avail.
Thanks.
indie56

---

### Post by kidcharles on 2007-08-18
When you installed Ubuntu, how did you do the partitioning of the drive? (Looks like step 6 under installing Ubuntu at the link you have provided.) It is possible that you wiped Vista from your machine during this process, which is a wonderful mistake to make, but not really what you were going for. :) If you had a factory setup on your Acer it is probable that you had no free space on the drive, so in order to install Ubuntu you would have had to resize or wipe the drive and start from scratch.

---

### Post by buzzmandt on 2007-08-18
not really helpful, but i have the acer 3680, bought it 1 week ago, It now has Ubuntu only, no dual boot and runs perfectly (wireless was a bia..tch though).

---

### Post by kidcharles on 2007-08-18
I am not familiar with the process of making recovery disks on an Acer, but it may be the case that it is the type of recovery disk that cannot be used for a fresh reinstallation of the operating system. Sometimes these types of disks can only be used on an already existing installation to restore original settings as a way to fix a major problem. Are you sure the recovery disks you made are able to install Vista from scratch?

---

### Post by the.phantom on 2007-08-18
don't know if the recovery disk can do a format of the drive
so it goes out there to write on one big hard drive and now it has just one partition small ntfs ( if you have one) or the two partitions of Ubuntu(ex3)
so my guess is it needs to be in the same as when the restore was made?

i have used ghost for backup on ntfs and it will not restore to a smaller partition

what do you show if you give it a 

> sudo fdisk -l


in the terminal of Ubuntu?

---

### Post by Rapidsnow on 2007-08-18
Well I don't quite know a lot about Acer's but I had a problem where I accidentally deleted Windows (clicked the wrong option when partitioning.) On my HP I used the recovery disk (A partition on my harddrive) and it reinstalled windows but wiped out Ubuntu. I then repartitioned my drive from windows and reinstalled Ubuntu just on the empty partition. It was a lot of hassle but now all is working. 

You may still have windows on your computer and it just might not be in your menu.lst file, although that would be strange. Check to see if that happened or not by going to the top directory and then change to the media directory to see if your windows partition is still there (On my laptop it is sda1). If it is, Change directory all the way back up and try this:

```
cd boot
cd grub
gksudo gedit menu.lst
```

After you have that opened up you can add in an extra boot option pointing to windows. Put it at the bottom... I am fairly new to GRUB so this could be just for my computer, but here is my section about loading windows vista.

```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

---

### Post by indie56 on 2007-08-18
Hello
The result of the command  sudo fdisk -l  is
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          62      497983+  82  Linux swap / Solaris
/dev/sda2              63        4922    39037950   83  Linux

As for the commands by Rapidsnow I donot know how to proceed.

Alternatively can anyone help with the setting up of the wirelesss card?
Thanks

---

### Post by indie56 on 2007-08-18
Hello
Refer to my message above.
I opened System--Admin--Network and the card is there. From the properties menu I have filled in the Network Name, Password type and Password. Connection settings is to Auto config.
BUT THE CONNECTION IS NOT COMING ON.
Pl help
Thanks

---

### Post by kidcharles on 2007-08-18
I would say based on your 'fdisk -l' output that you have deleted your Windows installation. There are only two partitions, sda1 is a swap file (virtual memory) and sda2 is the linux partition on which Ubuntu is installed.

---

### Post by Sef on 2007-08-18
> I would say based on your 'fdisk -l' output that you have deleted your Windows installation. There are only two partitions, sda1 is a swap file (virtual memory) and sda2 is the linux partition on which Ubuntu is installed.

Agreed.  Check out [Trinity Rescue Kit]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12").

> I installed 7.04 without resizing the drive. (Actually I was trying to make the laptop dual boot.)

That was your error.   You need to resize the hard drive in order to dual boot.

---

### Post by indie56 on 2007-08-19
Hello
I have now installed 7.04 on the entire hard disc of my new Acer 3680.
Next step is to enable the wireless. Its got a Dell 1390. I followed the instructions in 
[http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html](http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html).
On the final command sudo iwlist scanning, I get
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      Interface doesn't support scanning : No such device

Can some body suggest a suitable link for instructions?

---

### Post by Arthur Archnix on 2007-08-19
Just so we're clear... you know that you've eliminated Vista from your computer, right?

Now are you still wanting to dual-boot vista and ubuntu? If so you're going to need to take those recovery discs you made and restore vista. After you've done that you can use vista to create a space to install ubuntu. 

Please advise what it is you want to do at this point. E.g., do you just want to get ubuntu working, or do you want to get the dual boot working.

Best,

---

### Post by indie56 on 2007-08-19
Hi
I just want to get Ubuntu working. I carried out the instructions in 
[http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated](http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated)
and for the commands     iwlist scan

I get
 Scan completed :
          Cell 01 - Address: 00:13:46:F2:90:4A
                    ESSID:"default"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=89/100  Signal level=-64 dBm  Noise level=-69 dBm
                    Extra: Last beacon: 36ms ago
          Cell 02 - Address: 00:18:E7:12:A5:8E
                    ESSID:"TRENDnet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=99/100  Signal level=-36 dBm  Noise level=-69 dBm
                    Extra: Last beacon: 20ms ago
          Cell 03 - Address: 00:13:46:EE:0C:64
                    ESSID:"bkg network"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=79/100  Signal level=-80 dBm  Noise level=-69 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 92ms ago
That means my wifi card is working. My router is TRENDnet at cell 02. What next. How do I make my laptop work on wireless?
Thanks

---

### Post by Arthur Archnix on 2007-08-19
Ok, so you're booting to you ubuntu desktop, and the only issue is that you want to get your wireless working?

Sorry, I'm just trying to understand exactly what it is you're trying to do here.

If it's what I said above, post the output of lspci here:
```
sudo lspci
```

---

### Post by indie56 on 2007-08-19
The output is

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

Pl refer to my last post also.
Thanks

---

### Post by kidcharles on 2007-08-19
Perhaps buzzmandt could chime in on the wireless issue:

> **buzzmandt said:**
> not really helpful, but i have the acer 3680, bought it 1 week ago, It now has Ubuntu only, no dual boot and runs perfectly (wireless was a bia..tch though).

For those of you for whom English might be a second language (and maybe even for some native speakers), "bia...tch" refers to the word "bitch" which in this case means "difficult."

My favorite thing about this thread is that indie56 wiped out Vista on the Acer, and his or her response seems to be "oh well, whatever." :)

---

### Post by indie56 on 2007-08-19
Hello
The wifi is working bang on. Next and last step getting the audio going. Checked youtube, audio cd-- no sound.
Any ideas?
Thanks

---

### Post by kidcharles on 2007-08-19
Good to see you have wireless working! Looking at your 'lspci' output it seems to have found your sound hardware just fine (00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)). It seems you have exactly the same sound hardware as I have in my Dell laptop, and my sound works, so I'm sure it is possible. I assume you have tried playing around with the settings in 'System->Preferences->Sound'?

---

### Post by jake16424 on 2007-08-19
> **indie56 said:**
> Hello
I have bought a Acer 3680 with Vista Basic edition and have created the recovery discs (6). I installed 7.04 without resizing the drive. (Actually I was trying to make the laptop dual boot.) [http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2). By mistake I used page 2 instead of page 3. It now boots up in 7.04 ONLY. How do I make it boot in Vista or 7.04. I tried using the Vista recovery discs to reformat but to no avail.
Thanks.
indie56

don't mean to be mean,, but,, vista tracks all of your keyboard input and tracks all of your website visits, then it send it all in an email about twice a week to microsoft then from there it goes to there affiliates to see what is legal and what is not.. + then they know what to support in the advertising industry...

---

### Post by indie56 on 2007-08-19
Hello
The sound is also working fine now. Used alsamixer in terminal. (This I got from one of the forums)

I do not care what microsoft gets in the email. Now it is Ubuntu all the way.

---

### Post by kidcharles on 2007-08-19
> **jake16424 said:**
> don't mean to be mean,, but,, vista tracks all of your keyboard input and tracks all of your website visits, then it send it all in an email about twice a week to microsoft then from there it goes to there affiliates to see what is legal and what is not.. + then they know what to support in the advertising industry...

I have no love for Vista but this sounds like a conspiracy theory to me. Unless you have some kind of proof that MS is doing this you should not make these kind of accusations, they make us look like a pack of loonies.

---

### Post by kidcharles on 2007-08-19
> **indie56 said:**
> Now it is Ubuntu all the way.

Congratulations! Come back here with any future problems you have and enjoy Ubuntu.

---

### Post by indie56 on 2007-08-22
Hello
I put the laptop to hibernate and the wireless card 1390 stopped working. I have reloaded 7.04 and am trying to install the wifi card using [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092) .
I am stuck at step 3  -- go to the directory where you extracted ndiswrapper. How do I do this. Please give me exact line commands so that I can copy and paste. 
In the file browser I can see the folder of ndiswrapper at --- Home--mname-ndiswrapper
Thanks

---

### Post by kidcharles on 2007-08-22
> **indie56 said:**
> 
I am stuck at step 3  -- go to the directory where you extracted ndiswrapper. How do I do this. Please give me exact line commands so that I can copy and paste. 
In the file browser I can see the folder of ndiswrapper at --- Home--mname-ndiswrapper
Thanks

You will need to open up a terminal, which is where you do things on the command line. One way to do this is to go to Applications -> Accessories -> Terminal from your upper toolbar on your desktop.

One of the most common commands on the command line is 'cd' which stands for change directory. It is how you choose where you "are" when you execute commands. To get into the directory you need to, use:

```

$ cd /home/mname/ndiswrapper

```

Once you are in that directory, you can see a list of its contents using 'ls' which stands for 'list'. That should get you going again and enable you to continue following the instructions. Note the 'sudo' in front of many of the instructions. That is what you type before commands when you are doing something that requires administrative privileges (i.e. dangerous). Don't worry though, you can trust the commands in that howto. After typing in a command using 'sudo' it will prompt for your user password. Just enter that and you will be good to go.

---

### Post by indie56 on 2007-08-22
Hello
I have completed the actions till

unzip -a R151517.EXE  from the forum [http://ubuntuforums.org/showthread.php?t=297092&highlight=1390](http://ubuntuforums.org/showthread.php?t=297092&highlight=1390)

The next step is---
Now change directories to the DRIVER directory that was just extracted.
Which is this DRIVER DIRECTORY this is refering to?

The ls command generates the following---
AMD64                                  bcmwltry.exe    msvcp71.DLL
ATL71.DLL                              bcmwlu00.exe    msvcr71.DLL
bcm1xsup.dll                           data1.cab       ndiswrapper-1.47
bcm43xx-firmware_1.3-1ubuntu2_all.deb  data1.hdr       ndiswrapper-1.47.tar.gz
bcm43xx.tar.bz2                        data2.cab       preflib.dll
BCMLogon.dll                           DellInfo64.exe  R151517.EXE
Bcmnpf64.sys                           DellInfo.exe    README.rtf
bcmwlcpl.cpl                           dellinst.exe    setup.exe
bcmwlhlp.cab                           Desktop         Setup.ini
bcmwlhlp.chm                           DRIVER          setup.inx
bcmwliss.dll                           Examples        setup.iss
bcmwlnpf.sys                           ikernel.ex_     Version.txt
bcmwlpkt.dll                           is.exe          WLBCGCBPRO731.DLL
bcmwls32.exe                           launcher.ini    wltray.exe
bcmwls64.exe                           layout.bin      wltrynt.dll
bcmwls.ini                             MFC71.DLL       wltrysvc.exe

So which cirectory should I change to?  ie cd ???????
Thanks

---

### Post by indie56 on 2007-08-22
Hello
I presume that it is the DRIVER directory as listed in the ls output.
Furthur I did--

indie@indie-laptop:~$ cd DRIVER
indie@indie-laptop:~/DRIVER$ sudo ndiswrapper -i bcmwl5.inf
Password:
driver bcmwl5 is already installed
indie@indie-laptop:~/DRIVER$ sudo ndiswrapper -l
bcmwl5 : invalid driver!
Please help

---

### Post by kidcharles on 2007-08-22
I think it is very strange that your wireless was working, and now it is not. If it was working at all I think a usable driver must have been functioning.

At any rate, you might try what this user did:

[http://ubuntuforums.org/showpost.php?p=3099897&postcount=643](http://ubuntuforums.org/showpost.php?p=3099897&postcount=643)

Try:

```

sudo ndiswrapper -r bcmwl5

```

Which I think will remove (-r) the driver. Then try to install it again, starting from the DRIVER directory:

```

cd ~/DRIVER
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l

```

(The ~ is a shortcut for your home directory.) You should make sure that the bcmwl5.inf file is actually in that directory using:

```

ls ~/DRIVER

```

---

### Post by indie56 on 2007-08-23
Hello

I have been poking around and reinstalled 7.04 a couple of times.
I did--

ls /lib/firmware to get--
2.6.20-15-generic bcm43xx_initval06.fw bcm43xx_microcode4.fw
bcm43xx_initval01.fw bcm43xx_initval07.fw bcm43xx_microcode5.fw
bcm43xx_initval02.fw bcm43xx_initval08.fw bcm43xx_pcm4.fw
bcm43xx_initval03.fw bcm43xx_initval09.fw bcm43xx_pcm5.fw
bcm43xx_initval04.fw bcm43xx_initval10.fw
bcm43xx_initval05.fw bcm43xx_microcode2.fw

Does this means the drivers are installed? 
The network manager  icon is there. Right click shows Enable Networking and Enable Wireless ticked.
 Left click shows –Wired Networked enabled.
— Connect to other wireless network
— Create new wireless network
— Manual configuration
I have tried putting in the required data in all of them. The red light is still on.
I am missing something.

---

### Post by Dark Star on 2007-08-23
Cool its good to see a user solved his problem and happy with ubuntu :D

---

### Post by indie56 on 2007-08-23
> **Dark Star said:**
> Cool its good to see a user solved his problem and happy with ubuntu :D

The wifi is not working. The red light is on for the card.
My previous post refers. Pl help

---

### Post by indie56 on 2007-08-23
Helo
I do not know how but the wifi has started working now.
Thanks

---

### Post by kidcharles on 2007-08-23
There's a small chance your wifi problems are with your router, not with Ubuntu your wireless card. The next time your wifi goes out, try restarting your router, and see if that fixes it.

---

