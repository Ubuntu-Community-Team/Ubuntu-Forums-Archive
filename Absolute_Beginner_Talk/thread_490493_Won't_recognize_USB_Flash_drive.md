---
title: "Won't recognize USB Flash drive"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by eljoeb on 2007-07-02
Title self explanatory.  How do you usually make Ubuntu identify a flash drive?

I did find this thread, but it made it sound like it "just worked" 

[http://ubuntuforums.org/showthread.php?t=229463&highlight=usb+mass+storage](http://ubuntuforums.org/showthread.php?t=229463&highlight=usb+mass+storage)

Right now, I'm using an attache 512 mb flash drive.

Anything I need to download to make this work?

Thank you in advance,

ElJoeb

---

### Post by alanphil on 2007-07-02
What version of Ubuntu are you running? (System menu > About Ubuntu)

Also, tell us more about your computer hardware.

I have an old Dell desktop machine (Optiplex GX260) running Ubuntu 6.06 LTS (Dapper Drake), and for some reason this system will not recognize a USB flash drive. All of my other Ubuntu systems immediately identify a USB flash drive and mount it automatically on the desktop when plugged into the system.

---

### Post by lwh on 2007-07-02
First Try to run the command called ***lsusb ***in a console, to see if the system know that you have attached a USB device, 
if your divice is shown try to run ***fdisk -l*** in a console This vil list all the disk systems the system are aware about.

Note what device your usb drive is attached as .  ( /dev/sd? )
and mount this device from the console med ***mount /dev/sd? /mnt***

---

### Post by eljoeb on 2007-07-02
I am using Version 7.04.  The computer is an oldish Sony VAIO 3.2 ghz P4.

I had some issues with my nvidia drivers on install.  Could this be related?

---

### Post by matthewboh on 2007-07-02
What happens when you run```
lsusb
``` at the command prompt?

---

### Post by eljoeb on 2007-07-02
lsusb doesn't return anything. Something is there, but its definitely not the flash drive (it comes up when its not there)

---

### Post by matthewboh on 2007-07-02
It sounds like the usb ports weren't configured during the installation process.  You should have a directory called /sys/bus/usb/devices that lists off your devices.  How long ago did you install it?  There's a note that you have to turn "Plug and Play OS" to off in the BIOS, and that should make it work with a new install.

---

### Post by eljoeb on 2007-07-02
How can I turn off plug and play OS in BIOS?  The install is about 2 days old.

---

### Post by Mano_vardas_Tomas on 2007-07-02
I wonder could it be the same problem with my iPod (4gen)?
lsusb shows
Bus 001 Device 003: ID 045e:001e Microsoft Corp. IntelliMouse Explorer
Bus 001 Device 001: ID 0000:0000

---

### Post by eljoeb on 2007-07-02
Bus 005 Device 002: ID 054c:0174 Sony Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

hmm... I don't think its the same problem.

---

### Post by matthewboh on 2007-07-02
eljoeb

I don't think it is the same problem - it looks like the install did recognize your USB flash drive.  I'm just suprised lusb doesn't return anything.  What do you have plugged in?  What's the Sony item on Bus 5: Device 2?  A USB mouse?

---

### Post by eljoeb on 2007-07-02
I have no idea. The sony thing comes up whether or not the drive is plugged in.  There seemed to be something to change in BIOS.  How is that usually done?

Thanks

---

### Post by matthewboh on 2007-07-03
When you first turn on the computer, there's usually a quick flash that says "Press " whatever to get to your BIOS settings.  On a Sony Vaio Ithink it's either F2 or F3.  It will bring up a screen and there's instructions on how to change the settings.

---

