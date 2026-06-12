---
title: "USB.s"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by donsoper on 2007-02-07
Hi 

I am new to this so bare with me ,after installing unbuntu I can no longer get my usb's to work 

Can some one help ,what am I missing

cheers

Don

---

### Post by muguwmp67 on 2007-02-07
What kind of USB devices are not working?  Are your keyboard or mouse USB?  Are they working?

---

### Post by donsoper on 2007-02-07
pci usb hub, motherboard usb ,bluetooth dongle, printer and mass storage device
whilst dongle and storage device show power lights, not recognised by system

Don

---

### Post by muguwmp67 on 2007-02-07
What do you see when you type 'sudo lsusb' from a command line?

---

### Post by donsoper on 2007-02-07
As I said I am new to this 

w-here do you find the command line to type  'sudo lsusb' 

you will have to run me through the proceedure

cheers 

Don

---

### Post by Sef on 2007-02-07
> w-here do you find the command line to type 'sudo lsusb' 

Applications > Accessories > Terminal

Then type 'sudo lsusb' with out the quotes.

```
sudo lsusb
```

---

### Post by donsoper on 2007-02-07
followed directions but after terminal comes up with 

donsoper@donsoper-desktop:-$

tried typing sudo Isusb ,no luck 
tried typing sudo lsusb ,no luck 

each time pressing enter afterwards 

what am I doing wrong

Don

---

### Post by rtmie on 2007-02-07
When you say no luck, what do you mean , i.e. what is displayed after you type lsusb in the terminal window?

Rob

---

### Post by donsoper on 2007-02-07
nothing ,just repeats the line donsoper@donsoper-desktop

Iam expecting to do something when I press enter ?

---

### Post by rtmie on 2007-02-07
try doing lsusb in the terminal window with out the sudo, i.e. at the prompt

donsoper@donsoper-desktop>lsusb

and then press enter. 
you should then see in the terminal window output something like this:

Bus 002 Device 003: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:c512 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000

---

### Post by donsoper on 2007-02-07
just checked back over my posts and command line should have read 

donsoper@donsoper-desktop:-$


but it came up with a smilie face at end 

I have tried  removing this end bit but no good 

Anyhow tried what you said but just repeats previuos line

Cheers 
Don

---

### Post by muguwmp67 on 2007-02-07
Are your keyboard or mouse USB?

It almost looks like USB support wasn't installed when you installed Ubuntu.  Does anyone know why/how this could happen?

---

### Post by donsoper on 2007-02-07
both keyboard and mouse are ps2 socket


Don

do you reckon I should reinstall and see what happens ,maybe download program again ?


Don

---

### Post by rtmie on 2007-02-08
I assume that either keyboard or mouse is working if you can open a terminal window.
When you type in the command , do you see it on the terminal? 

Maybe if you try typing some command that should definitely return something such as:
ls or uname -a

and see if you are getting any output from these, we could go from there

Rob

---

### Post by donsoper on 2007-02-08
Gave up ,have uninstalled ubuntu from my system

cheers foor your help anyway 



Don

---

