---
title: "Chrubuntu 12.04 - No ttyUSB# access"
date: 2013-05-28
forum: Any Other OS
---

### Post by ckuter on 2013-05-28
I am using an Acer C7 Chromebook that is running Chrubuntu 12.04. This is a  version of Ubuntu 12.04 LTS configured for running on the Chromebook.  The /dev/ folder in Chrubuntu does not have ttyUSB0, ttyUSB1 or ttyUSB2 files.  

I am trying to use it with a couple of pieces of ham radio accessories, that both plug into a USB port.  I installed the manufacturer's linux software, but these items are not found on the C7.  Both items work on a Windows machine, so there must be some kind of access rights issue related to Chrubuntu.  I did get one of these pieces to run on an old IBM T-22 running Ubuntu 8.04.  

Seems like I need to get the ttyUSB0, ttyUSB1 or ttyUSB2 files installed on Chrubuntu. 

TIA for any help.

Cal

---

### Post by oldrocker99 on 2013-05-28
Try this:

sudo apt-get install modem-cmd

and see if that works. 
Here's the file description:

send arbitrary AT commands to your modem
 
modem-cmd can be used to send arbitrary AT commands to a modem device over
a serial line.

This means it can be used as a phone dialer:

$ modem-cmd /dev/ttyUSB0 ATDT123456

BTW, I had never heard of ttyUSB. I fired up Synaptic (which you should install) and typed 'ttyusb' into the quick filter. It brought up modem-cmd. Just wanted to help. I hope this does what you want.

---

### Post by markvrablic on 2014-04-06
> **ckuter said:**
> I am using an Acer C7 Chromebook that is running Chrubuntu 12.04. This is a  version of Ubuntu 12.04 LTS configured for running on the Chromebook.  The /dev/ folder in Chrubuntu does not have ttyUSB0, ttyUSB1 or ttyUSB2 files.  

I am trying to use it with a couple of pieces of ham radio accessories, that both plug into a USB port.  I installed the manufacturer's linux software, but these items are not found on the C7.  Both items work on a Windows machine, so there must be some kind of access rights issue related to Chrubuntu.  I did get one of these pieces to run on an old IBM T-22 running Ubuntu 8.04.  

Seems like I need to get the ttyUSB0, ttyUSB1 or ttyUSB2 files installed on Chrubuntu. 

TIA for any help.

Cal

I am in the exact same situation as you.  I am trying to access my printer and am unable to do so.  I first thought it was Octoprint's fault, but then Repetier Host didn't work either.  All that is available is tty0-tty63.  There are not any ttyUSB* files nor any ttyS* files.  If anyone has any ideas, please chime in.  If I can't get this working by friday, I'll have to take my whole desktop across town with me :(

---

