---
title: "gnokii xgnokii install"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by mimsmall on 2007-03-26
Installed xgnokii using synaptic to communicate with my Nokia 3660. The installed program shows up in Applications->Accessories->Xgnokii mobile phone tool. Clicking on the icon loads the opening gnokii window, but it immediately disappears. I entered xgnokii in a terminal window with the same result, but got this print out.

donald:~$ xgnokii
LOG: debug mask is 0x1

(xgnokii:5867): Gtk-WARNING **: horizontal scrolling not implemented

(xgnokii:5867): Gtk-WARNING **: horizontal scrolling not implemented
Device already locked.
Lock file error. Exiting.
phone instance config:
model: 6510
port_device: /dev/ttyS0
connection_type: 0
init_length: 0
serial_baudrate: 19200
serial_write_usleep: -1
hardware_handshake: 0
require_dcd: 0
smsc_timeout: 100
connect_script:
disconnect_script:
rfcomm_cn: 1
sm_retry: off
Connecting
Serial device: opening device /dev/ttyS0
Gnokii serial_open: open: Device or resource busy
Couldn't open FBUS device: Device or resource busy
Error in link initialisation: 1
Serial device: opening device /dev/ttyS0
Gnokii serial_open: open: Device or resource busy
Couldn't open FBUS device: Device or resource busy
Error in link initialisation: 1
Serial device: opening device /dev/ttyS0
Gnokii serial_open: open: Device or resource busy
Couldn't open FBUS device: Device or resource busy
Error in link initialisation: 1
GSM/FBUS init failed! (Unknown model?). Quitting.
Serial device: closing device

---

### Post by decadude on 2008-04-27
bump i have the same problem

---

### Post by RicoD on 2008-06-13
Wammu worked better than Gnokki/xGnokii with my Nokia Series 40 even it's based on the same code at first

---

