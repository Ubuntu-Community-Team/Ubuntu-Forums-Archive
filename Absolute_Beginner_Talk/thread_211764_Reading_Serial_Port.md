---
title: "Reading Serial Port"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by pvale on 2006-07-08
I have a GPS engine that I would like to see the output of in Ubuntu. Is there anything in the rpositories similar to Hyperterminal in Windows, or can I make the standard terminal window in Dapper display what is coming in the serial port?

---

### Post by compbrain on 2006-07-15
> **pvale said:**
> I have a GPS engine that I would like to see the output of in Ubuntu. Is there anything in the rpositories similar to Hyperterminal in Windows, or can I make the standard terminal window in Dapper display what is coming in the serial port?

Hi,

I suggest you check out 'gpsd', [http://gpsd.berlios.de/](http://gpsd.berlios.de/), it should be available in synaptic package manager. If all you want is to dump the NMEA data from the GPS, you should be able to plug in the gps, and if its plugged in via USB, do `sudo cat /dev/ttyACM0` in a terminal. If its plugged into a serial port, try `sudo cat /dev/ttyS0` or `sudo cat /dev/ttyS1`.

Good Luck!

---

### Post by byteme97 on 2007-04-28
`sudo cat /dev/ttyACM0`

Well I don't know if you solved pvale's problem but that one simple sudo solved mine.  I've had multiple community resources pointing me to /dev/ttyUSB0 or USB1 but all that gets me is the actual USB port in my laptop.

Thank you very much compbrain  for having the answer I needed.

---

