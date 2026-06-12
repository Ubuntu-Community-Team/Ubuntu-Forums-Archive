---
title: "how do i attach Prolific Serial port to usb port"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Steve Zodiac on 2007-06-17
My Tosh laptop does not have a serial port, i have acquired a convertor, what do i need to setup this convertor. ttyS1 to ttyUSB0 in terminal ?  Sorry if this is a dumb question i am new to UBUNTU Dapper.

---

### Post by dve on 2007-06-18
Hi,

Actually it is not a dumb question. I have a similar problem, but I think I got around it (if I am thinking the same thing as you). Basically you do not need to do anything, if you can modify the programs you use. Just change the /dev/ttyS0 to /dev/ttyUSB0 in the configuration files. This is the easy solution.

The more difficult option is to remove the file /dev/ttyS0 and link it to /dev/ttyUSB0. The commands are easy but I am not sure how to recreate the /dev/ttyS0 as its original form in the case you need the original COM port later (I hope the command "sudo /etc/init.d/udev restart" will do this).  

But if you are willing to explore follow this:

1. start two terminals, say "sudo tail -f /var/log/messages" in the first one and leave it background. Write the rest in the second one.

2. plug the usb cable to the computer. In the first terminal should be something saying "usb device registered". I get 

```
Jun 18 12:12:39 localhost kernel: [ 8503.840000] usb 1-2: new full speed USB device using uhci_hcd and address 13
Jun 18 12:12:39 localhost kernel: [ 8504.000000] usb 1-2: configuration #1 chosen from 1 choice
Jun 18 12:12:39 localhost kernel: [ 8504.004000] pl2303 1-2:1.0: pl2303 converter detected
Jun 18 12:12:39 localhost kernel: [ 8504.004000] usb 1-2: pl2303 converter now attached to ttyUSB0

```

note the device name "ttyUSB0"

3. now say

```
sudo rm /dev/ttyS0
sudo ln -s /dev/ttyUSB0 /dev/ttyS0
```

and you are finished. The first removes the serial port determined by udev and the second creates a symbolic link that points to the found usb device.

You can test the link by saying 

```
less -f /dev/ttyS0

```

and giving some data through the port (move your serial mouse, unplug the usb-serial adapter, etc). You should see some changes in the screen.

I get some odd problems with the ttyUSBX port number. If I plug and unplug many times it changes from 0 to 1. So watch your messages terminal.

Juha

---

