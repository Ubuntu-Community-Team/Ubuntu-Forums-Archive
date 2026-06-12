---
title: "Yet another newb printing problem"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by Gimbo on 2006-01-05
Sorry for the length of the post, but I've tried to included as much useful information as I can.

What I've done so far:

System>Administration>Printing

Right-click "New Printer">Click "Add"

Printer Type: Local Printer
Use a detected printer: HEWLETT-PACKARD DESKJET 720C

Manufacturer: HP
Model: DeskJet 720C
Driver: pnm2ppa (recommended) (Suggested)
Click "Apply"

System>Administration>Printing
Right-click "DeskJet-720C" (which has "Ready" in blue underneath it)
Click "Properties"
Click "Print a Test Page"
Information box pops up saying page has been sent to printer

Text under "DeskJet-720C" is now green and says "Printing 1 Jobs"
The printer is on, but nothing is happening
Right-click "DeskJet-720C"
Click "Jobs"

Name: Test Page
Job Number: 15 (I guess I've tried quite a few times)
Owner: andrew
Size: 150.0K
State: Printing: job-printing

I've already carried out the instructions at[http://www.linuxprinting.org/beh.html]("http://www.linuxprinting.org/beh.html") about beh (Backend Error Handler). My /usr/lib/cups/backend folder contains:
beh  bluetooth  canon  epson  hp  http  ipp  lpd  parallel  smb  socket  usb

The output of lpinfo -v is:
```

network socket
network **beh**
network bluetooth
direct hp:/no_device_found
network http
network ipp
network lpd
direct canon:/dev/lp0
direct epson:/dev/lp0
direct parallel:/dev/lp0
direct usb:/dev/usb/lp0
direct usb:/dev/usb/lp1
direct usb:/dev/usb/lp2
direct usb:/dev/usb/lp3
direct usb:/dev/usb/lp4
direct usb:/dev/usb/lp5
direct usb:/dev/usb/lp6
direct usb:/dev/usb/lp7
direct usb:/dev/usb/lp8
direct usb:/dev/usb/lp9
direct usb:/dev/usb/lp10
direct usb:/dev/usb/lp11
direct usb:/dev/usb/lp12
direct usb:/dev/usb/lp13
direct usb:/dev/usb/lp14
direct usb:/dev/usb/lp15
network smb

```

I've had a look at the man pages for cups, and using
```
lp ~/Desktop/test
```
produces
```
request id is DeskJet-720C-16 (1 file(s))

```

Any help would be **really** appreciated.

---

### Post by Sef on 2006-01-17
This post here is a 712c, but there solution may work for you:

> sudo gedit pnm2ppa.conf

found the line which was not commented out with "#" that said version with no other text and change that line to version 712. Note did not have to add the "c" in the printer's model line. saved the file and all is fine now.

Link: [http://ubuntuforums.org/showthread.php?t=116265&highlight=printer]("http://ubuntuforums.org/showthread.php?t=116265&highlight=printer")

---

### Post by Gimbo on 2006-01-31
Thank you so much for your help - it worked!

For anyone who comes across this thread and has a similar problem:

Follow the instructions in my first post and then do the following:

```
sudo gedit /etc/pnm2ppa.conf
```

Add 720 (assuming your printer is a 720c) to the line where it just says "version" (it should not be commented out)

Save the pnm2ppa.conf file

Try printing again

---

