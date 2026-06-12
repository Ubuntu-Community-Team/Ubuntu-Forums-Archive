---
title: "can't get usb printer detected"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by blazini on 2007-07-29
Im having a few problems installing my Epson CX6000 printer/scanner/copier, but first things first I guess it should probably at least show up before I do anything else.

>  lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 006 Device 008: ID 058f:6362 Alcor Micro Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 06a3:8020 Saitek PLC 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  

That's all that shows up. I dual boot XP on this mashine and the printer works perfecly

---

### Post by NewJack on 2007-07-29
First, try removing the USB plug from you machine, then reinsert it.  I have found that works sometimes.

Also, here is a link to your printer on linuxprinting.org

[http://openprinting.org/show_printer.cgi?recnum=Epson-stylus_CX6000](http://openprinting.org/show_printer.cgi?recnum=Epson-stylus_CX6000)

Hope that helps you.

---

### Post by blazini on 2007-07-29
I've tried plugging it into a different usb port and all, still doesn't show up.

---

### Post by sailor2001 on 2007-07-29
system/administartion/printing  and ADD PRINTER

---

### Post by jimbob on 2007-07-29
Unplug your printer.
Go to System->Administration->System Log and click on syslog.
Scroll all the way to the bottom of the log.
Now, while watching the bottom of the log, plug your printer into a USB port.
You should see several lines appear at the bottom of the log when your system recognizes the printer.

The CX6000 is in Ubuntu's driver database so it should work (at least partially).
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by blazini on 2007-07-29
I got the printer working earlier, don't ask me how. I've been trying to get the scanner going for a while. I'll make a new thread, thanks for the help.

---

