---
title: "Ubuntu 11.04 on iMac - issues...."
date: 2011-06-23
forum: Apple Hardware Users
---

### Post by ishueli on 2011-06-23
Guys,
 
I have a 2.4 Ghz iMac from 2007 with Core II Duo processor and ATi 2600 HD graphics card. I had OSX (SL) and Windows 7 installed earlier. To avoid pressing ALT key to get OSX started, I installed rEFIT which gave me the idea to triple boot system with LINUX. So I repartitioned the system and installed Unity (Ubuntu 11.04) on it. The installation was smooth but somehow bluetooth did not work. I am using the proprietary ATi/AMD driver from Hardware Extra in Unity and the system works great (even 3D cube works fine).
 
I though of upgrading Kernel to 2.6.39.0 but the system gives an error while loading the files. The error is promarily with flgrx driver. Keeps giving**[COLOR=red] [Fail][/COLOR]** result. When I had replaced the proprietary driver with ATi open source driver, I could upgrade the kernel to 3.0. The bluetooth gat "ENABLED" but would not connect to Magic Mouse. 
 
Now I have reinstalled the system with 2.6.38.8 Kernel and keeping it simple as the earlier efforts required 6-7 reinstallations of Unity. Please offer solutions if bluetooth can be enabled with present Kernel or how to safely upgrade the kernel without loading the Open souce ATi driver.
 
I have already tried "sudo service bluetooth restart" and it work but I have to do it every time I reboot the syatem, hence not desired.

---

### Post by LtPitt on 2011-06-24
Hello, my friend...

Probably my solution is not very elegant but I think you'll find it fine because it should work.

Open a terminal window and once in it digit:

sudo nano /etc/rc.local

In this moment you are editing a particular config file (all config files are stored in etc folder): rc.local
Everything written in this file is executed by root user when the personal computer boots.
So all you have to do is add to rc.local rows this one:

service bluetooth restart

and save (press control + x to exit and then press y to save your file and then enter)

Reboot and you should be happy.

Have fun!

---

### Post by ishueli on 2011-06-24
Many Thanks LtPitt,

It surely was a working solution. It surely got the bluetooth working. Now I am left with a very minor problem - 

I wanted to get the bluetooth to work so that I could connect Magicmouse. I tried with the default Bluetooth and it would connect only for a second and disappear again. Hence I installed Blueman and managed to pair the mouse. Even got it "trusted" to secure the connection. 

However when I restart the system, magic mouse does not connect. It only connect when I do the following - 
- connect a wired mouse
- open blueman bluetooth manager 
- click on "device" tab
- click on "input service"

This now defeats the purpose of enabling bluetooth. Are there any commands that I can add to rc.local file to have "input services" activated during startup?

Once again "THANKS FOR AN EXCELLENT SUGGESTION"

I like Linux even more now....

---

### Post by johnmurrayvi on 2011-06-24
I have a setup working for my 8,1 iMac with a Mighty Mouse and bluetooth keyboard. I never boot into OS X, though. The last time I used OS X I had to setup my keyboard and mouse again in Ubuntu afterwards. However, I have the mouse and keyboard working after sleep and reboots, I just have to click once and press one key to wake the mouse and keyboard.

Give this a try:
```
gksudo gedit /etc/default/bluetooth
```

Insert:
```
HIDD_ENABLED=1
HIDD_OPTIONS="--master --connect XX:XX:XX:XX:XX:XX --connect YY:YY:YY:YY:YY:YY --server"
```

Replace the addresses with your devices' addresses
XX:XX:XX:XX:XX:XX is the address of my keyboard
YY:YY:YY:YY:YY:YY is the address of my mouse

---

### Post by ishueli on 2011-06-24
Thanks johnmurrayvi,

Do you use default bluetooth applet or blueman or both. I am using blueman to connect to magicmouse. 

One more question....can you have both bluetooth manager & blueman working together?

---

### Post by ishueli on 2011-06-24
I tried the command....The output is as below

(gedit:2048): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2048): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.Q19XXV': No such file or directory

(gedit:2048): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

However I see the bluetooth file in /etc/default directory and the commands are saved as well. Still no luck with magicmouse. Had to connect wired mouse to connect the magicmouse in blueman.

---

### Post by johnmurrayvi on 2011-06-24
I have the default bluetooth applet and installed bluez-compat and bluez-utils. The output into the terminal when using "gksudo" shouldn't effect anything, it usually, as in your case, mentions the root user's 'recently-used' file not being updated. 

This may be better help: 
[https://help.ubuntu.com/community/BluetoothSetup#Setup](https://help.ubuntu.com/community/BluetoothSetup#Setup) Devices

That was the basis for my setup, however I found the "--master" option inserted in a different guide. Not sure if it helped, but it's still in my '/etc/default/bluetooth' file.

---

### Post by ishueli on 2011-06-24
There was some progress done after I reverted back to default bluetooth manager. I could connect to magicmouse by using following commands - 

Opened "Bluetooth Applet" by clicking on the bluetooth icon on right (my right) top of the screen.
Selected mouse and clicked on "connect".
Mouse started to work. 

Earlier when I was connecting thru blueman, the mouse would not connect to OSX. I had to reconfigure the connection for it to work. However using default bluetooth manager and connecting the magicmouse, I could still maintain my connectivity on OSX side, which is a good help.

I installed bluez compat & bluez utils but still have to connect the mouse manually. Clicking on magicmouse does not establish connectivity. Need to use a wired mouse to "connect" magicmouse under bluetooth menu.

Any other ideas?

---

### Post by LtPitt on 2011-06-25
I am glad you're enjoying Linux! :)

Right now my focus is on Cannelloni I'm eating in minutes: as soon as I have a little time I'll get back to help...
I've just found this video in a minute I don't know if it can be helpful but check it out:
[http://www.youtube.com/watch?v=tUHxcDpe7nw](http://www.youtube.com/watch?v=tUHxcDpe7nw)

---

### Post by ishueli on 2011-06-25
Thanks. Your help will be most appreciated. The magic mouse works pretty good on Unity. However it will not auto connect after reboot. 

I ran a couple of commands in the terminal- take a look at them and advise -
[B]
Shows different address than magicmouse guess it is the internal bluetooth dongle address[/B]
shailesh@shailesh-iMac:~$ hcitool dev
Devices:
    hci0    00:1D:4F:9C:4A:1F

**No devices found on hcitool scan**
shailesh@shailesh-iMac:~$ hcitool scan
Scanning ...

**Nothing on hidd --search as well**
shailesh@shailesh-iMac:~$ sudo hidd --search
Searching ...
    No devices in range or visible

**shailesh@shailesh-iMac:~$ sudo bluez-simple-agent hci0 00:1D:4F:9C:4A:1F**
Creating device failed: org.bluez.Error.ConnectionAttemptFailed: Page Timeout

**shailesh@shailesh-iMac:~$ dmesg|tail**
[   17.746355] Bluetooth: RFCOMM ver 1.11
[   18.780522] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
[   25.504047] eth1: no IPv6 routers present
[   49.980554] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[   98.052303] usb 1-2.4: new high speed USB device using ehci_hcd and address 8
[  139.268341] usb 1-2.1: new low speed USB device using ehci_hcd and address 9
[  139.369138] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.1/1-2.1:1.0/input/input8
[  139.369459] generic-usb 0003:046D:C016.0007: input,hidraw4: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1a.7-2.1/input0
[  148.263582] input: Shailesh’s mouse as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/bluetooth/hci0/hci0:46/input9
[  148.263731] magicmouse 0005:05AC:030D.0008: input,hidraw5: BLUETOOTH HID v0.84 Mouse [Shailesh’s mouse] on 00:1D:4F:9C:4A:1F

How to get Magicmouse auto connect at startup?

---

### Post by ishueli on 2011-06-25
SUCCESS....SUCCESS.....SUCCESS

Managed to get Magicmouse auto connect on reboot to the iMac....

HIDD Search did not show any connections which prompted to think that the connection was not happening at the start. Added line to rc.local file....

at terminal gave the command

sudo nano /etc/rc.local
added following line to the bottom of the script

hidd --connect XX:XX:XX:XX:XX:XX (insert your bluetooth device ID)

Press CTRL + X
Press Y to save the file.

Reboot and magicmouse is connected.

---

