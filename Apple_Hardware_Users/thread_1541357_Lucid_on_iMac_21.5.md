---
title: "Lucid on iMac 21.5"
date: 2010-07-29
forum: Apple Hardware Users
---

### Post by ZeroLinux on 2010-07-29
Lucid on iMac 21,5 (10.1)

Solution of some problems:

**Sound** 
1) After Installing you need to unmute front speaker
Go to Terminal (Application -> Accessories -> Terminal) and there write alsamixer. Then go 3 times press right arrow key and press m
And then yo can press the key "Up" to set volume level you like

**Microphone**
2) You need to boost mic because it is muffled. 
To do it install "PulseAudio Device Chooser"
Write in Terminal 
sudo apt-get install paman (it was in my case)
or
sudo apt-get install padevchooser (may be it works also)

Start it from Application -> Sound & Video -> PulseAudio Device Chooser
Click on its the icon in the upper-right corner. Choose Manager... -> Tab "Devices" -> In the tree "Sources" -> alsa_input.pci-0000_00_08.0.analog-stereo Internal Audio Stereo -> Button "Properties". Set the Volume to 300% (I like this level. You can choose whatever). Close. Well done.

**Skype**
3) If you like Skype - it will set Volume of the mic to the 100% back or, in other word, reset it, and it again will be muffled. To avoid it, after installing Skype do this. Before calling, in Skype go to Options -> Sound Devices and UNCHECK "Allow Skype to automatically adjust my mixer levels". In such a way you will enjoy normal sound even after reboot.

**Reboot**
4) Yes, you cannot reboot out of box. The system hangs right before reboot, you can safely press turn off button behind your iMac and press it again. But shutdown works fine. System goes to Sleep and wakes up fine. 
Solution: 
in Terminal: sudo gedit /etc/default/grub
Change in the editor: (GRUB_CMDLINE_LINUX_DEFAULT="quit splash")to (GRUB_CMDLINE_LINUX_DEFAULT="quit splash reboot=pci")
Save and quit.
Make update grub in terminal: sudo update-grub

**Bluetooth**
5) Out of box it doesn't work at all. System doesn't see it. Although, you can use keyboard and mouse in a limited way. But nothing else. 
At last I've made it working!
Solution:
I will not explain each step. Just do it. Install all necessary packages (like dkms, patch...) if you need from standard repos.
mkdir bt
cd bt
wget [http://launchpadlibrarian.net/49939125/btusb.patch](http://launchpadlibrarian.net/49939125/btusb.patch)
download and unpack this file - btusb-dkms_0.0.1_all.deb.gz - to the new made bt directory
sudo dpkg -i btusb-dkms_0.0.1_all.deb 
sudo cp btusb.patch /usr/src/btusb-0.0.1/
cd /usr/src/btusb-0.0.1
sudo mkdir bluetooth
sudo mv btusb.c dkms.conf bluetooth/
sudo patch -p1 < btusb.patch 
sudo mv bluetooth/* ./
sudo rmdir bluetooth/
sudo dkms remove -m btusb -v 0.0.1 --all
sudo dkms add -m btusb -v 0.0.1
sudo dkms build -m btusb -v 0.0.1
sudo dkms install -m btusb -v 0.0.1
sudo apt-get install blueman bluetooth
sudo /etc/init.d/bluetooth restart

Now you can start System -> Preferences -> Bluetooth manager
After that I could easy pair my Magic Mouse and Apple keyboard

Mouse code 0000. 

Keyboard code I used 1234. Just write on usual keyboard 1234 when it is asked for code and then on the Apple keyboard just type 1234 and press "Enter". After that keyboard successfully paired. And, Yes, Fn-key works, it can delete in a usual way. It has to be pointed thet it is input service. Just play a bit. It will work. Once and for all.

It opens the way to make Magic Mouse working with scroll with multitouch kernels in the best way possible. It works but I I find to use it a litle bit uncomfortble, because of second touch effect (I call it this way because scroll often start working only from second touch to the surface of Magic Mouse or some delay). I didn't have time to make it comfortable to use. May be you help me. I hope you appreciate my efforts. 

**Keyboard**
6) The key "fn" works - at least with "Delete" after pairing through bluetooth. Out of box it works without Fn-key. 
After pairing through bluetooth Fn-key works, for example with "Delete". Changing, muting Volume works. To press F11 you need to use Fn-key. But, for example, to increase volume you need use Fn+F11. Some additional functions like brightness doesn't work.

**Magic Mouse**
7) Out of box - If you press several times on it - it will work. You can move it. You will have left and right click, but there is no scrolling
I also installed before multitouch kernel from [here]("http://ubuntuforums.org/attachment.php?attachmentid=162544&d=1278369836attachmentid=162544&d=1278369836") It is without inertial scrolling. It works with both vertical and horizontal (horizontal scrolling didn't work with previous module) scroll (after implementing [this]("http://ubuntuforums.org/showpost.php?p=9596101&postcount=154") post and even with inertial scrolling) often from a second touch after making bluetooth working and pairing. At least my Magic Mouse. There were many experiments. Make it clear in your posts. I slowed down to the minimum pointer speed Acceleration and Sensitivity in the Mouse Preferences.


**Webcam**
8) iSight works out of box and works fine. Nothing to do. Install Cheese and use it.

---

### Post by macewan on 2010-07-30
You may want to consider adding information about fixing the keyboard not working in GDM. Even the virtual keyboard will not work for some folks.

---

### Post by ZeroLinux on 2010-07-30
> **macewan said:**
> You may want to consider adding information about fixing the keyboard not working in GDM. Even the virtual keyboard will not work for some folks.

Unfortunately, (or, probably, fortunately, for me) I don't have this problem, therefore cannot fix it ;)

---

### Post by chillyperson23 on 2010-08-01
Ive been trying to get bluetooth to work. 

Thank you. =] 

I cant seem to get the magic mouse scrolling to work. The first link you posted doesnt work, and when i run the second one, it says the module doesnt exist. Anyone get this working?

---

### Post by ZeroLinux on 2010-08-02
> **chillyperson23 said:**
> Ive been trying to get bluetooth to work. 

Thank you. =] 

I cant seem to get the magic mouse scrolling to work. The first link you posted doesnt work, and when i run the second one, it says the module doesnt exist. Anyone get this working?

Does bluetooth work at all? Is there an icon in tray? Does bluetooth manager start? Whar did you mean under "first link" and "second one"?

---

### Post by chillyperson23 on 2010-08-14
> **ZeroLinux said:**
> Does bluetooth work at all? Is there an icon in tray? Does bluetooth manager start? Whar did you mean under "first link" and "second one"?


Yes. there are 2 bluetooth applets in the tray. and bluetooth works perfectly. 


The first link under the magic mouse section doesnt work, and the second link doesnt build.



also, to make the bluetooth keyboard work after a reboot, you have to add "hid_apple" to /etc/modules

---

### Post by ZeroLinux on 2010-08-15
> **chillyperson23 said:**
> 
The first link under the magic mouse section doesnt work, and the second link doesnt build.

Fixed.

---

### Post by muzakman on 2010-10-09
> **ZeroLinux said:**
> Lucid on iMac 21,5 (10.1)
sudo dpkg -i btusb-dkms_0.0.1_all.deb 


returns:


```
make KERNELRELEASE=2.6.35-22-generic -C /lib/modules/2.6.35-22-generic/build SUBDIRS=/var/lib/dkms/btusb/0.0.1/build modules....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.35-22-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/btusb/0.0.1/build/ for more information.
0
0
ERROR: binary package for btusb: 0.0.1 not found
dpkg: error processing btusb-dkms (--install):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 btusb-dkms
```

using the maverick RC. anyone know why?

thanks.

---

### Post by yktoo on 2010-10-11
Hi ZeroLinux,

I have the same problem (Ubuntu 10.10 Maverick), the package will not install:

```

$ sudo dpkg -i btusb-dkms_0.0.1_all.deb 
Selecting previously deselected package btusb-dkms.
(Reading database ... 139730 files and directories currently installed.)
Unpacking btusb-dkms (from btusb-dkms_0.0.1_all.deb) ...
Setting up btusb-dkms (0.0.1) ...
Loading new btusb-0.0.1 DKMS files...

Loading tarball for module: btusb / version: 0.0.1

Loading /usr/src/btusb-0.0.1...
Creating /var/lib/dkms/btusb/0.0.1/source symlink...

DKMS: ldtarball Completed.
Installing prebuilt kernel module binaries (if any)
Building module...

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.35-22-generic-pae -C /lib/modules/2.6.35-22-generic-pae/build SUBDIRS=/var/lib/dkms/btusb/0.0.1/build modules....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.35-22-generic-pae (i686)
Consult the make.log in the build directory
/var/lib/dkms/btusb/0.0.1/build/ for more information.
0
0
ERROR: binary package for btusb: 0.0.1 not found
dpkg: error processing btusb-dkms (--install):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 btusb-dkms

```And /var/lib/dkms/btusb/0.0.1/build/make.log contains:
```

DKMS make.log for btusb-0.0.1 for kernel 2.6.35-22-generic-pae (i686)
Mon Oct 11 22:30:15 CEST 2010
make: Entering directory `/usr/src/linux-headers-2.6.35-22-generic-pae'
  CC [M]  /var/lib/dkms/btusb/0.0.1/build/btusb.o
/var/lib/dkms/btusb/0.0.1/build/btusb.c: In function ‘btusb_probe’:
/var/lib/dkms/btusb/0.0.1/build/btusb.c:945: error: ‘struct hci_dev’ has no member named ‘type’
/var/lib/dkms/btusb/0.0.1/build/btusb.c: In function ‘btusb_suspend’:
/var/lib/dkms/btusb/0.0.1/build/btusb.c:1073: error: ‘struct usb_device’ has no member named ‘auto_pm’
make[1]: *** [/var/lib/dkms/btusb/0.0.1/build/btusb.o] Error 1
make: *** [_module_/var/lib/dkms/btusb/0.0.1/build] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic-pae'

```Do you have any idea what might be the cause?

---

### Post by Ilssear on 2010-10-11
in Maverick I made the following changes to btusb.c

948:         // hdev->type = HCI_USB;
1076:        if (!( 0 && data->tx_in_flight)) {


Bluetooth is working now!

The pointers are referencing structures that do not contain the specified variables, so I commented one out and replaced the second with 0.

---

### Post by yktoo on 2010-10-15
Thanks all, I've finally managed to get Bluetooth and my Magic Mouse working (Apple iMac 27").

I incorporated all the necessary changes (including btusb.patch) into the package.
So now you only have to do the following:


[LIST=1]
[*]Download [ATTACH]172465[/ATTACH]
[*][FONT=Courier New]gunzip [/FONT][FONT=Courier New]btusb-dkms_0.0.1_all.deb.gz[/FONT]
[*][FONT=Courier New]sudo dpkg -i btusb-dkms_0.0.1_all.deb[/FONT]
[*][FONT=Courier New]sudo apt-get install bluetooth blueman[/FONT]
[*][FONT=Courier New]sudo /etc/init.d/bluetooth restart[/FONT]
[*]Start **System -> Preferences -> Bluetooth manager** and click **Search**:
[ATTACH]172455[/ATTACH]
[*]Right click the mouse device and select **Setup...**:
[ATTACH]172456[/ATTACH]
[*]Select use **Custom Passkey:** and enter **0000** as a passkey, then click **Forward**:
[ATTACH]172458[/ATTACH]
Make sure that your mouse is discoverable, you can simply turn it off and back on for that. In a case you see a request for pin code, enter **0000** once again.
[*]After the device is paired, you should connect it to the input service. Right click the mouse entry again and select **Input Service**:
[ATTACH]172462[/ATTACH]
[*]Voila! Your mouse is working now, including horizontal and vertical scrolling and middle click — you should now see orange/green/blue reception indicators to the right of the item. To make future connections automatic, right click the item again and select **Trust**.
[/LIST]

---

### Post by Old Codger on 2010-11-04
> **ZeroLinux said:**
> Lucid on iMac 21,5 (10.1)

Solution of some problems:

[excerpts]
**Bluetooth**
5) Out of box it doesn't work at all. System doesn't see it. Although, you can use keyboard and mouse in a limited way. But nothing else. 
At last I've made it working!
Solution:
I will not explain each step. Just do it. Install all necessary packages (like dkms, patch...) if you need from standard repos.
mkdir bt
cd bt
wget [http://launchpadlibrarian.net/49939125/btusb.patch](http://launchpadlibrarian.net/49939125/btusb.patch)
download and unpack this file - btusb-dkms_0.0.1_all.deb.gz - to the new made bt directory
sudo dpkg -i btusb-dkms_0.0.1_all.deb 
sudo cp btusb.patch /usr/src/btusb-0.0.1/
cd /usr/src/btusb-0.0.1
sudo mkdir bluetooth
sudo mv btusb.c dkms.conf bluetooth/
sudo patch -p1 < btusb.patch 
sudo mv bluetooth/* ./
sudo rmdir bluetooth/
sudo dkms remove -m btusb -v 0.0.1 --all
sudo dkms add -m btusb -v 0.0.1
sudo dkms build -m btusb -v 0.0.1
sudo dkms install -m btusb -v 0.0.1
sudo apt-get install blueman bluetooth
sudo /etc/init.d/bluetooth restart

Now you can start System -> Preferences -> Bluetooth manager
After that I could easy pair my Magic Mouse and Apple keyboard


**Magic Mouse**
7) Out of box - If you press several times on it - it will work. You can move it. You will have left and right click, but there is no scrolling
I also installed before multitouch kernel from [here]("http://ubuntuforums.org/attachment.php?attachmentid=162544&d=1278369836attachmentid=162544&d=1278369836") It is without inertial scrolling. It works with both vertical and horizontal (horizontal scrolling didn't work with previous module) scroll (after implementing [this]("http://ubuntuforums.org/showpost.php?p=9596101&postcount=154") post and even with inertial scrolling) often from a second touch after making bluetooth working and pairing. At least my Magic Mouse. There were many experiments. Make it clear in your posts. I slowed down to the minimum pointer speed Acceleration and Sensitivity in the Mouse Preferences.


You've shared some goods tips, some of which have helped, but when I tried copying and pasting the line commands you provided for bluetooth, it didn't work. I also can't get the mouse to scroll, etc. It would be very helpful for noobs like I am if you could provide either a step-by-step progression of line commands or a GUI alternative.

Thanks again for sharing what worked for you.

OC

---

### Post by Old Codger on 2010-11-04
Another issue I have is that when I rebooted after installing the updates from Update Manager, I was unable to use either the keyboard or the mouse. As a result, I've had to re-install 10.04 on the iMac twice. When I tried to upgrade to 10.10 using a live CD, the same thing happened. I'm running 10.04 and am waiting before I either install updates or try upgrade to Upgrade to 10.10.

Has anyone using the iMac 21.5 and Snow Leopard been able to update and upgrade to 10.10 successfully so far?

---

### Post by ZeroLinux on 2010-11-04
> **Old Codger said:**
> 
Has anyone using the iMac 21.5 and Snow Leopard been able to update and upgrade to 10.10 successfully so far?
I made successful upgrade to 10.10 without any problem
But, before it I decided not to use iMac mouse and keyboard - I don't like it anymore. But I like my iMac. Therefore I cannot help with bluetooth mouse and keyboard. But I use bluetooth with my HTC HD2 to send/recieve files from/to it.

---

### Post by Old Codger on 2010-11-05
yktoo, Thank you for providing both line commands and GUI windows, but when I get to step 6, I receive an error message:** Connection to Bluez failed **Bluez daemon is not running, bluemanager cannot continue. Any advice?

---

### Post by Old Codger on 2010-11-05
Yktoo,

I also had the following problem in terminal:

fred@fred-desktop:~$ gunzip btusb-dkms_0.0.1_all.deb.gz
gzip: btusb-dkms_0.0.1_all.deb.gz: No such file or directory
fred@fred-desktop:~$ 
fred@fred-desktop:~$ sudo dpkg -i btusb-dkms_0.0.1_all.deb
dpkg: error processing btusb-dkms_0.0.1_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 btusb-dkms_0.0.1_all.deb
fred@fred-desktop:~$ ^C
fred@fred-desktop:~$

---

### Post by ZeroLinux on 2010-11-05
> **Old Codger said:**
> Yktoo,

I also had the following problem in terminal:

fred@fred-desktop:~$ gunzip btusb-dkms_0.0.1_all.deb.gz
gzip: btusb-dkms_0.0.1_all.deb.gz: No such file or directory

Problem - you should have been in the folder where this file was
so...:
fred@fred-desktop:~$ cd ~/Downloads
and then 
fred@fred-desktop:~$ gunzip btusb-dkms_0.0.1_all.deb.gz

---

### Post by Old Codger on 2010-11-05
> **ZeroLinux said:**
> Problem - you should have been in the folder where this file was
so...:
fred@fred-desktop:~$ cd ~/Downloads
and then 
fred@fred-desktop:~$ gunzip btusb-dkms_0.0.1_all.deb.gz

Many thanks! The line command portion worked, but I still can't get into Bluetooth Manager when I go to System>Preference>Blue Tooth Manager. Yet, in the terminal, I see that bluettoth and blueman are already the newest versions. :confused:

---

### Post by ZeroLinux on 2010-11-06
What is happening when you try to start Bluetooth manager?

---

### Post by Old Codger on 2010-11-07
Nothing happens except "Connection to BlueZ failed"

---

### Post by arabis on 2010-11-28
Thanks Zerolinux,
I've used your instructions and my magic mouse and keyboard works in Maverick, on my Imac 21.5" mid 2010.

In the Mactel PPA, there is a package of btusb-dkms for Maverick: [btusb-dkms_1.0-maverick-mactel4_all.deb]("https://launchpad.net/~mactel-support/+archive/ppa/+files/btusb-dkms_1.0-maverick-mactel4_all.deb"). In this package, on lines 62-63 of btusb.c:

[B]/* Apple iMac11,1 */
	{ USB_DEVICE(0x05ac, 0x8215) },[/B]

Do you think that this packages will do the job instead?

---

