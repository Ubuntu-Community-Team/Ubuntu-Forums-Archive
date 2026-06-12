---
title: "Bluetooth not connecting!?"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by Psychobiker on 2007-07-22
Hey,

Installed gnome bluetooth utility, the obex plugin, and bluez-utils, but still, my phone will NOT connect to the PC. I can see it on a scan, (both ways), but not connect!!

L

---

### Post by linuxwizard on 2007-07-22
Look over these maybe something will help.
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)


supported devices
[http://www.holtmann.org/linux/bluetooth/features.html](http://www.holtmann.org/linux/bluetooth/features.html)

---

### Post by Psychobiker on 2007-07-22
cheers - : the BT1300TP is listed alright, which confuses me! I want to be able to GUI into my phone..what kinda package would you recommend?

L:

---

### Post by volkswagner on 2007-07-22
same problem here.  this link does [https://help.ubuntu.com/community/BluetoothSetup]("https://help.ubuntu.com/community/BluetoothSetup") not seem to help

It seems to be dated or inaccurate.  For example

Connect Devices at Startup

    *
> 
      To connect the device at startup every time, use the following commands to edit the configuration file:

        sudo cp /etc/default/bluez-utils /etc/default/bluez-utils_backup
        sudo nano /etc/default/bluez-utils
        

for me this file seems to be /etc/default/bluetooth

is this written for version prior to fiesty?

It seems we should have better support for this problem.  If both device and pc can see each other why cant we get them to connect?

I see a few posts with zero or minimal replies.

this may be a back to windoze if i cant get BT to work. :confused:

anyone with a working system who can help with posting hcid.conf file and others to see where we a going wrong.

I think some file names changed and are not being referenced properly in fiesty

I have several posts in this matter

[http://ubuntuforums.org/showthread.php?t=460272]("http://ubuntuforums.org/showthread.php?t=460272")
[http://ubuntuforums.org/showthread.php?t=351131]("http://ubuntuforums.org/showthread.php?t=351131")
[http://ubuntuforums.org/showthread.php?t=403717]("http://ubuntuforums.org/showthread.php?t=403717")

---

### Post by volkswagner on 2007-07-22
i am now able to share files via bt in both directions

not sure if it was python or just following the steps to send files. ie right click>send>send via bt

i never tried any of this since i could not pair normally

try these steps in this thread [http://ubuntuforums.org/showthread.php?t=444233&page=2](http://ubuntuforums.org/showthread.php?t=444233&page=2)

thanks to fmaste

Today almost every cell phone, notebook comes with bluetooth. There are lots of bluetooth mouse, headphones, remote controls, etc. I believe it is important to have good bluetooth support.
I know people that goes back to windows because of this things.

At least having something in System->Preferences that automatically installs the needed packages and let you configure bluetooth and search for devices.
With the help of the Ubuntu community we can develop something.
This is what I did to have bluetooth on my DELL inspiron 9400 that may be useful, it can be done automatically.

On a terminal type:
sudo apt-get install gnome-bluetooth bluez-gnome python-bluez python-libbtctl bluez-utils bluez-gnome
Now "Bluetooth File sharing" will appear under Applications->Accesories, once activated a new icon will appear near the clock to identify it.
To execute it automatically at startup, go to System->Preferences->Session-> Startup Programs, click on new and type gnome-obex-server.
Restart your computer. (Maybe doing something else this won't be needed)
You will also have under System->Preferences->Bluetooth preferences some extra configuration to play with to make you cellphone, etc work.
To search for bluetooth devices:
Make the device discoverable (look for a "Connect" button on many keyboards and mice or look in the device's manual) and then search for the device with this command:
sudo hidd --search
If that command doesn't work, try this one:
hcitool scan
Hint: If no devices are being shown and you are using Edgy Eft (6.10), you may try
sudo hciconfig hci0 inqmode 0
See bug [[https://launchpad.net/ubuntu/+source...th/+bug/70718]](https://launchpad.net/ubuntu/+source...th/+bug/70718]) #70718. If this helps, you may add the hciconfig command (without "sudo") to your /etc/rc.local file for a permanent workaround.
To change the location that files are saved to when using bluetooth transfers
gconf-editor
Then navigate to
/apps/gnome-obex-server
where you can specify the save directory and also turn off that annoying dialogue box!

---

### Post by Psychobiker on 2007-07-22
> **volkswagner said:**
> i am now able to share files via bt in both directions

not sure if it was python or just following the steps to send files. ie right click>send>send via bt

i never tried any of this since i could not pair normally

try these steps in this thread [http://ubuntuforums.org/showthread.php?t=444233&page=2](http://ubuntuforums.org/showthread.php?t=444233&page=2)

thanks to fmaste

Today almost every cell phone, notebook comes with bluetooth. There are lots of bluetooth mouse, headphones, remote controls, etc. I believe it is important to have good bluetooth support.
I know people that goes back to windows because of this things.

At least having something in System->Preferences that automatically installs the needed packages and let you configure bluetooth and search for devices.
With the help of the Ubuntu community we can develop something.
This is what I did to have bluetooth on my DELL inspiron 9400 that may be useful, it can be done automatically.

On a terminal type:
sudo apt-get install gnome-bluetooth bluez-gnome python-bluez python-libbtctl bluez-utils bluez-gnome
Now "Bluetooth File sharing" will appear under Applications->Accesories, once activated a new icon will appear near the clock to identify it.
To execute it automatically at startup, go to System->Preferences->Session-> Startup Programs, click on new and type gnome-obex-server.
Restart your computer. (Maybe doing something else this won't be needed)
You will also have under System->Preferences->Bluetooth preferences some extra configuration to play with to make you cellphone, etc work.
To search for bluetooth devices:
Make the device discoverable (look for a "Connect" button on many keyboards and mice or look in the device's manual) and then search for the device with this command:
sudo hidd --search
If that command doesn't work, try this one:
hcitool scan
Hint: If no devices are being shown and you are using Edgy Eft (6.10), you may try
sudo hciconfig hci0 inqmode 0
See bug [[https://launchpad.net/ubuntu/+source...th/+bug/70718]](https://launchpad.net/ubuntu/+source...th/+bug/70718]) #70718. If this helps, you may add the hciconfig command (without "sudo") to your /etc/rc.local file for a permanent workaround.
To change the location that files are saved to when using bluetooth transfers
gconf-editor
Then navigate to
/apps/gnome-obex-server
where you can specify the save directory and also turn off that annoying dialogue box!

+1 ftw!!! :D cheers

---

