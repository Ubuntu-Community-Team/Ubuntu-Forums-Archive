---
title: "Help w/ Pre-install Troubleshooting"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by Peter108 on 2007-08-01
[FONT="Fixedsys"]Hello.

I'm a new Ubuntu user, and am trying to work through some issues prior to installing FF 7.04 i386 server on my Compaq r3000.  I have been running the Live CD on my machine for a week, with only a few hiccups.  Meanwhile, have pored over documentation. Using my dubious syslog reading skills I have extracted the most sinister looking messages, and would like some help in interpreting them.  Below are the log names, followed by the messages in question, followed by my interpretation, where possible.  Any help w/ further interpreting the messages greatly appreciated.  Thank you.  Peter.


**[COLOR="Blue"]From kern.log:[/COLOR]**

Aug  1 10:56:15 ubuntu kernel: [   38.262879] PCI: Failed to allocate mem resource #10:4000000@e4000000 for 0000:02:04.0 [two occurrences]
Aug  1 10:56:15 ubuntu kernel: [   38.262938] PCI: Failed to allocate mem resource #10:4000000@e4000000 for 0000:02:04.1
*[COLOR="Blue"]Interp: In searching the forums, I can't tell whether this is a known kernel bug and/or something I need to fix locally.  Doesn't seem to be causing any problems.  [/COLOR]*

Aug  1 10:56:15 ubuntu kernel: [  125.928000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.[multiple occurrences]
*[COLOR="Blue"]Interp: Am generally familiar with the issues around Broadcomm wireless support, so am guessing this message relates to those issues, and that I'll be learning a whole lot more about ndiswrapper in the near future. [/COLOR]*

[COLOR="Blue"]**From daemon.log:**[/COLOR]

Aug  1 18:04:58 ubuntu firmware_helper[8575]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:02.0' with driver '(unknown)'
Aug  1 18:05:02 ubuntu NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device eth1: No such device  [multiple occurrences]
*[COLOR="Blue"]Interp: As above re Broadcomm.[/COLOR]*

From wvdialconf.log:

Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

[I][COLOR="Blue"]Interp: I do have a functional (under WinXP anyway) internal modem, an Agere Systems AC'97 Modem.  Assume this is a “Win”modem, and that therefore incompatible. 
[/COLOR][/I]
From Xorg.0.log:

(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
*[COLOR="Blue"]Interp: ??? Help.[/COLOR]*[/FONT]

---

### Post by scrooge_74 on 2007-08-01
Hi there I can help with some of your questios.

The broadcom thing you are right, you need to install drivers and set it up, [here]("http://www.ubuntuforums.org/showthread.php?t=185174") is a giude for that.  

On the network manager message, it has to do with the above problem.

Your modem is probably a win mode which in that case is going to be a hard one, check this instructions[ here]("http://www.tldp.org/HOWTO/Modem-HOWTO.html").

Have fun

---

