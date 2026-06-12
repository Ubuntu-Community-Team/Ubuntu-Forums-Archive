---
title: "USB ports"
date: 2005-07-24
forum: Absolute Beginner Talk
---

### Post by Error_Msg on 2005-07-24
I'm using gpstrans, a utility that allows you to interface with a handheld GPS receiver to up or download data from/to it.
The thing is that I need to identify the port for the utility so it can read the receiver but I have no idea how to do this.
The command is gpstrans -p <portID>
If I enter lsusb at the terminal, I get:
Bus 001 Device 001: ID 0000:0000
I tried entering many combinations of these, but no dice.

E_M

---

### Post by ShaneR on 2005-07-24
Try:

/dev/ttyUSB0 (that's a zero at the end).  Not sure how that particular device works...but, I have a feeling that port will work for you.

Hope it helps :)

---

### Post by Error_Msg on 2005-07-24
[QUOTE=ShaneR]Try:

/dev/ttyUSB0 (that's a zero at the end).  Not sure how that particular device works...but, I have a feeling that port will work for you.

Hope it helps :)[/QUOTE]

Thanks, Shane.
I tried, but it didn't work. It keeps telling me this:
Connected GPS [/dev/ttyS1] is: <GPS not responding>
I suspect that it's looking for a receiver connected to a serial port, not USB.

E_M

---

### Post by ShaneR on 2005-07-24
ahhh...

EDIT: or, ttys1 could be what it's looking for in your 1st post...I;m not sure what's going on at you end...so I;m guessing.
************************************************8

Well, ttyS1 is your serial port.  What happens, is that some devices that connect to USB use a usb to serial converter (as an example, I'm using an external modem right now connected to a USB to serial cable as my serial port died on my system).

In which case, the proper modules need to be loaded int he Kernel.  In my case, it's usbserial and pl2303 which Ubuntu load upon boot.  There is another module ftdi_sio as well.

So, connect your device, boot, and then type "dmesg" at the prompt to see if one of those 2 were loaded.

If not, go to the prompt and type "modprobe ftdi_sio".  That will load that module as well as the usbserial module if not already loaded.

If all that is loaded, the port it will be looking for should be ttyUSB0.

Let us know how that works.

I;m not an expert...but that may tell us something.

Good luck :)

---

### Post by Error_Msg on 2005-07-25
I loaded the three modules, and then tried to set the port to /dev/ttyUSB0, but the thing keeps trying to read ttyS1. I did go in /dev to take a look around, but I did not se USB0 in there.
In any case, I give up for now.
Thanks for the help.

E_M

---

