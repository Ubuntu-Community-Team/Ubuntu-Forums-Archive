---
title: "Accessing Serial port on virtualbox with OSX host"
date: 2014-09-09
forum: Apple Hardware Users
---

### Post by agusta2 on 2014-09-09
Hello All,

I am trying to access the serial console of my embedded board. I am using minicom on OSX Mavericks to access the console successfully. The port name on OSX is /dev/tty.usbserial-141B 
However i cannot access the serial console on my guest OS, Ubuntu 12.04. I have attached the serial device to the virtual OS and i get ttyUSB0, ttyUSB1, ttyUSB2 and ttyUSB3 on connecting the device. I cannot access the console using any of these ports. I read about configuring serial port in settings, but cannot get it to work. I have selected 'COM1' as Port Number and Port mode as 'host device'. Port/File Path as '/dev/cu.usbserial-141B' as '/dev/tty.usbserial-141B' threw me an error. Can someone please help me out?

---

