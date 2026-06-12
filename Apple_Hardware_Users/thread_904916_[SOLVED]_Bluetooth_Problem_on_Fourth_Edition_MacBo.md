---
title: "[SOLVED] Bluetooth Problem on Fourth Edition MacBookPro (Penryn)"
date: 2008-08-29
forum: Apple Hardware Users
---

### Post by tmdavis on 2008-08-29
I'm very confused.  I've followed the instructions of several forum postings now, and I'm not really getting anywhere.  I'd appreciate it if you would take a few moments to help.  I'm trying to pair any bluetooth device with a fourth edition MacBookPro (Penryn series), and I'm not having much success.  The curious thing is, my bluetooth mouse and keyboard seem to work, but they work before Ubuntu even starts.  I believe this behavior comes from pairing in OSX.  I've read in a few forums that EFI might be the culprit, but I don't know that for a fact.  I'd like to pair them properly, along with other bluetooth devices in linux.

If I'm to believe the rEFIt documentation ([http://refit.sourceforge.net/doc/c4s2_bluetooth.html](http://refit.sourceforge.net/doc/c4s2_bluetooth.html)), this doesn't look very promising.  I'm hoping that they are just talking about support in the rEFIt bootloader.
> 
Problem: An Apple Wireless Keyboard or another Bluetooth keyboard works in Mac OS X, but not in rEFIt, LILO, Windows, Linux, whatever.

Solution: As mentioned in the Boot Camp Requirements, Apple does not support the use of Bluetooth keyboards and mice with Boot Camp. They will actually work to some degree, but they will not work realiably. There is nothing rEFIt could do about this. If you have problems with your wireless keyboard, use a USB or built-in keyboard instead. 


Before I get started, I thought I'd list some of the threads that I've been using as a reference:
[LIST]
[*][http://ubuntuforums.org/showthread.php?t=786490&highlight=bluetooth](http://ubuntuforums.org/showthread.php?t=786490&highlight=bluetooth)
[*][http://ubuntuforums.org/showthread.php?t=860657&highlight=bluetooth](http://ubuntuforums.org/showthread.php?t=860657&highlight=bluetooth)
[*][https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)
[*][http://ubuntuforums.org/showthread.php?t=784223&highlight=bluetooth](http://ubuntuforums.org/showthread.php?t=784223&highlight=bluetooth)
[/LIST]

1. So, let's restart from a clean slate.  I think that the following command will wipe most of my bluetooth settings.
```

$ sudo apt-get autoremove --purge bluetooth bluez-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bluetooth* bluez-utils*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 979kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 118044 files and directories currently installed.)
Removing bluetooth ...
Removing bluez-utils ...
 * Stopping bluetooth                                                                                                                                                       [ OK ] 
 Purging configuration files for bluez-utils ...

```

2. Now I'm going to reinstall, so that I get the default settings.
```

$ sudo apt-get install bluetooth bluez-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  bluez-firmware
The following NEW packages will be installed:
  bluetooth bluez-utils
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/377kB of archives.
After this operation, 979kB of additional disk space will be used.
Selecting previously deselected package bluez-utils.
(Reading database ... 117989 files and directories currently installed.)
Unpacking bluez-utils (from .../bluez-utils_3.26-0ubuntu8_i386.deb) ...
Selecting previously deselected package bluetooth.
Unpacking bluetooth (from .../bluetooth_3.26-0ubuntu8_all.deb) ...
Setting up bluez-utils (3.26-0ubuntu8) ...
Creating device nodes ...
udev active, devices will be created in /dev/.static/dev/
 * Starting bluetooth                                                                                                                                                       [ OK ] 

Setting up bluetooth (3.26-0ubuntu8) ...

```

At this point I get a notification bubble from the gnome bluetooth manager that states:
> 
Bluetooth Device

Device has been made connectable.


At this point I set up my device for pairing (in this case an unpaired apple mouse.)  I can see it as a device on another machine running OSX, but not using the gnome bluetooth manager.  So, I drop to the command line to see what is going on.

3. I start by running the hidd search tool while my mouse is in "pairing mode".
```

$ sudo hidd --search
Searching ...

```

4. Since that seemed to fail, I run the hci tool (also in pairing mode).
```

$ hcitool scan
Scanning ...
Inquiry failed: Connection timed out

```

5. Same result, so I try to verify that a bluetooth device exists.
```

$ sudo lsusb -v | grep -i blue
  bDeviceProtocol         1 Bluetooth
  iProduct                2 Bluetooth USB Host Controller
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth
      bInterfaceProtocol      1 Bluetooth

```

I also checked with the hci tool (obviously my real MAC address has been replaced with a fake MAC address.)
```

$ hcitool dev
Devices:
	hci0	aa:bb:cc:dd:ee:ff

```

6. It seems to exist, so then I checked that I had all of the modules related to bluetooth installed.
```

$ lsmod | grep -i blue
bluetooth              61156  9 bnep,hidp,rfcomm,l2cap,hci_usb

```

7. That seems right to me, so I install another bluetooth manager to see what is going on.
```

$ sudo apt-get install blueman
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  python-bluez
Recommended packages:
  dhcp3-server
The following NEW packages will be installed:
  blueman python-bluez
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/337kB of archives.
After this operation, 1625kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package python-bluez.
(Reading database ... 118045 files and directories currently installed.)
Unpacking python-bluez (from .../python-bluez_0.14-1ubuntu1_i386.deb) ...
Selecting previously deselected package blueman.
Unpacking blueman (from .../blueman_0.5-0ubuntu1_i386.deb) ...
Setting up python-bluez (0.14-1ubuntu1) ...

Setting up blueman (0.5-0ubuntu1) ...
 * Reloading system message bus config...

```

It has a GUI with a big button that just says "Inquiry".  When I click it, it says:
> 
Failed to start inqury. Reason:  org.bluez.Error.Failed: Device or resource busy


8. At this point I'm willing to connect to my devices by MAC addresses via HIDD.  So, I enable HIDD by adding "HIDD_ENABLED=1" to my /etc/default/bluetooth file and restart bluetooth.
```

$ sudo /etc/init.d/bluetooth restart
 * Restarting bluetooth

```

9. However, I can't scan for the devices' MAC address (as you probably noticed above.)  So, I look up the device's MAC on another machine.  I then run the following (again, obviously replacing the fake MAC address with my real MAC address.):
```

sudo hidd --connect aa:bb:cc:dd:ee:ff

```

It just hangs.

I think I'm done for the night.  Please let me know if you have any suggestions.  I'd love to get this working.

---

### Post by tmdavis on 2008-08-31
So, I just read on another forum page ([https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)) about another way to scan for devices.  It doesn't seem to work for me.
```

$ sudo hciconfig hci0 inqmode 0
Can't set inquiry mode on hci0: Input/output error (5)

```

If I try it without specifying the device however:
```

$ sudo hciconfig inqmode 0
hci0:	Type: USB
	BD Address: XX:XX:XX:XX:XX:XX ACL MTU: 1021:5 SCO MTU: 64:1
	UP RUNNING 
	RX bytes:213 acl:0 sco:0 events:21 errors:0
	TX bytes:322 acl:0 sco:0 commands:19 errors:0

```

I at least get my bluetooth radio's MAC address (which I have replaced with X's here.)  Not that this is terribly helpful, but I thought that the information was interesting.  Again, any help would be appreciated.

---

### Post by hajk on 2008-09-01
I've just bought a Bluetooth Mighty Mouse and initially went through the same gyrations to make it work in GNU/Linux... it wouldn't. The "sudo hidd --search" command didn't show anything, I tried to configure /etc/default/bluetooth as various wikis said...no dice.

So, then I decided to start Mac OS X (Leopard) and clicked on the Bluetooth icon to get the mouse paired. I found the mouse slow to track, though, even after setting the tracking speed to maximum in System Preferences. By this time I was getting worried, and googled a bit more. I found that almost no configuration was needed in /etc/default/bluetooth:```

BLUETOOTH_ENABLED=1
HIDD_ENABLED=1
HIDD_OPTIONS="--master --server"
```
then I restarted with```

sudo /etc/init.d/bluetooth restart
```
grabbed the mouse (I guess I left-clicked) and it worked! What's more, it has better tracking speed than under Mac OS X. The only thing not (yet?) working is scrolling with the trackball (I did turn that off in Mac OS X, don't know whether that is the cause).

So, the moral of the story: get the mouse working (paired) in Mac OS X first, then you need only enable HIDD in /etc/default/bluetooth and restart (or reboot).

---

### Post by cyberdork33 on 2008-09-01
you should check that is lasts through reboots. I got my wireless keyboard working again working on startup and all, and not it doesn't work again... :(

It sure would be nice if the bluetooth applet in Ubuntu actually worked...

---

### Post by hajk on 2008-09-01
Yes it survived a reboot. I forgot to say that I did install the "gnome-bluetooth" package (but that should perhaps be in the standard install). The mouse only starts working after my Gnome desktop has come up and after I grab the mouse and left-click; even then it takes a second or so, ostensibly for the connection to start. Note also that this "bluez" stuff is no longer needed, just the "bluetooth" package and its Gnome wrapper. The Bluetooth reference in the sticky FAQ threw me off, it was completely useless (as it was for the OP apparently). Lack of action from the scroll-ball was not related to my Mac OS X settings, BTW.

(Also: I'm currently running Debian Lenny on the MBP, but I don't believe the setup in Ubuntu Hardy is any different.)

---

### Post by cyberdork33 on 2008-09-01
> **hajk said:**
> Yes it survived a reboot. I forgot to say that I did install the "gnome-bluetooth" package (but that should perhaps be in the standard install). The mouse only starts working after my Gnome desktop has come up and after I grab the mouse and left-click; even then it takes a second or so, ostensibly for the connection to start. Note also that this "bluez" stuff is no longer needed, just the "bluetooth" package and its Gnome wrapper. The Bluetooth reference in the sticky FAQ threw me off, it was completely useless (as it was for the OP apparently). Lack of action from the scroll-ball was not related to my Mac OS X settings, BTW.

(Also: I'm currently running Debian Lenny on the MBP, but I don't believe the setup in Ubuntu Hardy is any different.)
I think bluez stuff is the kernel driver and related packages. I think gnome-bluetooth is installed by default on Ubuntu, but I could be wrong.

For the scrollball I think you need to check the few threads about the mighty mouse that are here. You have to use a particular xorg driver I think and then setup the config appropriately. I haven't done this though so I can't help much more than that.

I guess your situation is OK for a mouse. a keyboard is required before gnome starts so that might be a deeper issue.

---

### Post by tmdavis on 2008-09-01
> 
So, the moral of the story: get the mouse working (paired) in Mac OS X first, then you need only enable HIDD in /etc/default/bluetooth and restart (or reboot).


hajk,

Have you been able to pair any other bluetooth devices?  I don't believe that Ubuntu has anything to do with your mouse or keyboard pairing in this case.  For instance, when I restart my machine, I can use my bluetooth keyboard in rEFIt before any OS is loaded.  I can't test the mouse before Ubuntu boots, but I'm guessing that it would work as well.  Like you say, I believe this due to the pairing within OSX.  Has anyone been able to pair a device under Ubuntu that they didn't pair in OSX?

> 
For the scrollball I think you need to check the few threads about the mighty mouse that are here. You have to use a particular xorg driver I think and then setup the config appropriately. I haven't done this though so I can't help much more than that.


cyberdork33,

I have run through a few of the forums that address what you're talking about.  Unfortunately, I don't have the scroll wheel Mighty Mouse with me right now (it's at work), so I can't retry that route quite yet.

---

### Post by hajk on 2008-09-01
> **tmdavis said:**
> hajk,

Have you been able to pair any other bluetooth devices?  I don't believe that Ubuntu has anything to do with your mouse or keyboard pairing in this case.  For instance, when I restart my machine, I can use my bluetooth keyboard in rEFIt before any OS is loaded.  I can't test the mouse before Ubuntu boots, but I'm guessing that it would work as well.  Like you say, I believe this due to the pairing within OSX.  Has anyone been able to pair a device under Ubuntu that they didn't pair in OSX?

....
No, my experience has been that the prior config in Mac OS X is needed. Of course, the "MAC" addresses of the Bluetooth radios in MBP and Mighty Mouse are unique, whether used under Max OS X or GNU/Linux, so one could imagine that the pairing info is stored in these devices by the Mac OS X installer. At least that would fit your and my observations that no further GNU/Linux config is required. There may also be other explanations. Whatever the right one, I'm not complaining about the situation: it works perfectly, also after a reboot; and I can switch it off to preserve battery life, then start it up again and get it connected with a squeeze.

---

### Post by pierrelux on 2008-09-02
I have the exact same hardware as you and I have been struggling around with this problem in the last weeks. So here what I found this morning.

By entering sudo hciconfig hci0 reset you should be able to do hcitool scan and then see you device. The applet will then work. 


A bug report seems to have been filled about this similar problem but with another device.
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/92111](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/92111)

---

### Post by hajk on 2008-09-03
I found a really useful Howto on the use of Apple Bluetooth Mighty Mouse and keyboard, [http://idebian.wordpress.com/2008/07/06/manage-hid-bluetooth-devices-in-linux/](http://idebian.wordpress.com/2008/07/06/manage-hid-bluetooth-devices-in-linux/). It explains why basic BT Mighty Mouse and keyboard functions operate in GNU/Linux without any configuration after having paired them once in Mac OS X. It also shows how to control these devices from Linux through the HID interface, for example to get the scrollball working. It worked like a charm. Well worth reading!

---

### Post by tmdavis on 2008-09-03
Thanks pierrelux and hajk!  Your posts look like they both address my problem.  Hopefully I'll get some time tonight after work to follow your advice.  However, I was able to get Ubuntu to recognize the mouse with pierrelux's reset trick.  I didn't play around with it for very long, but it at least tried to pair with the mouse, which I was unable to do before.

Thanks again!

---

### Post by cyberdork33 on 2008-09-03
> **hajk said:**
> I found a really useful Howto on the use of Apple Bluetooth Mighty Mouse and keyboard, [http://idebian.wordpress.com/2008/07/06/manage-hid-bluetooth-devices-in-linux/](http://idebian.wordpress.com/2008/07/06/manage-hid-bluetooth-devices-in-linux/). It explains why basic BT Mighty Mouse and keyboard functions operate in GNU/Linux without any configuration after having paired them once in Mac OS X. It also shows how to control these devices from Linux through the HID interface, for example to get the scrollball working. It worked like a charm. Well worth reading!
Excellent. Finally some documentation that seems to actually make sense and it targeted more toward a user rather than a developer. I will look through this later.

EDIT: Wow that was even better than I thought. It is even targeted to Mac users... The information there actually explains ALOT.

---

### Post by cyberdork33 on 2008-10-10
Well this seems to have broken again in the latest updates for Intrepid. hidd binary was removed (again) and bluez-gnome has had a major update. While I like the hardware setup wizard (finally they adding something that makes sense) it completely i not working for me and on top of that, gives to output to diagnoze the issue. wonderful.

---

### Post by hyperboloid on 2008-10-31
I have a Macbook Pro 4,1 (Penryn) with a fresh install of the new release of Ubuntu 8.10, with a single boot setup. Using ```
sudo hciconfig hci0 reset
``` I succeeded in pairing my Mighty Mouse and everything seemed to be working fine, including the scroll wheel. Very nice!

However, after a reboot I can no longer pair the mouse anymore, even after doing the above reset trick. The mouse shows up in the list upon scanning, but I get the error "Pairing with xxxx's mouse failed" from the last page of the Setup Wizard and can't seem to get past this.

Any suggestions?

[COLOR="Red"][EDIT: The workaround here [http://ubuntuforums.org/showpost.php?p=6086632&postcount=5]("http://ubuntuforums.org/showpost.php?p=6086632&postcount=5") solved my issue completely.][/COLOR]

---

