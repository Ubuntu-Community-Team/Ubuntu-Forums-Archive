---
title: "ubuntu doesn't detect my USB webcam"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by arjayes on 2007-10-22
HI 
When i plugin my Zerbonic USB webcam(ZEB-151WC)
nothing happens 
do i have to configure it or something
 i have a driver cd but it does'nt have ubuntu support
pls help 
                                                                        Absolute Beginner

---

### Post by philinux on 2007-10-22
Open a terminal and type [FONT="Times New Roman"]lsusb[/FONT]

---

### Post by arjayes on 2007-10-22
this is what i get 

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 17a1:0118  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000

what do i do with that

---

### Post by Samhain13 on 2007-10-22
Did you plug it into a USB hub or into its own port?
Mine would only work if plugged into its own port and not into a hub, but it's of a different make. But maybe the info would be helpful.

---

### Post by arjayes on 2007-10-22
i did plug it into a USB  Hub

---

### Post by Samhain13 on 2007-10-22
Ok, try plugging it into its own port and follow the instructions here:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

You'd probably want to install Camorama just so you can test your webcam. Installing it is mentioned in the link. When installed, you can launch it through Applications->Graphics->Camorama

:D

---

### Post by arjayes on 2007-10-22
when i try to run camorama i get this dialog
[B]"could not connect to video device ( /dev/video0 )"
[/B]
since my cam has only a USB connector i think it is connected to /dev/bus/usb/001/001)
how can i change this??
I am a abs noob .pls be patient .

---

### Post by Samhain13 on 2007-10-22
I have no idea. Perhaps someone else can help you with that.

---

### Post by philinux on 2007-10-22
I've a bad feeling this cam might be not supported.

You could try installing Kopete (IM client) from synaptic. Then select configure and then devices it correctly identifies my logitech cam in this way. Worth a try.

---

### Post by u01p2109 on 2008-01-17
17a1:0118
Intex PC Webcam IT-104WC SN:D9R1SWC10609270832 11.2006
I have only support disc with drivers for Windows OS`s....
[http://www.intexuae.com/webcam_102.htm](http://www.intexuae.com/webcam_102.htm)

Specification  	   	 
  	Feature 	Description 	 
  	  	DESIGNED FOR LAPTOP USER (BASE AND CLIP MOUNTABLE) 	 
  	Image Sensor 	1/5" CMOS sensor 	 
  	Image Resolution 	350 x 288 Pixels 	 
  	Frame Rate 	Upto 30 FPS 	 
  	

Image Control
	Brightness, Contrast, Hue, Saturation, Gamma, Edge Ratio 	 
  	

Image Flip
	

Horizontal and Vertical
	 
  	Monitor Type 	CRT and LCD 	 
  	AC Power Frequency 	50Hz, 60Hz 	 
  	Focus Distance 	5cm ~ Infinity 	 
  	Lens View Angle 	52 Degree 	 
  	I/O Interface 	USB 1.1 	 
  	Image Format 	RGB 24, I420 	 
  	Power Consumption 	160 mW Typical 	 
  	Operating System 	Windows 98, 2000, ME, XP 	Linux :confused:
  	RAM 	32MB or above 	 
  	Lens 	F=2.5, F=4.8mm 	 
  	Available Color 	sliver

Intex in UAE.
INTEX TECHNOLOGIES LLC.
P.O BOX - 44253
Khaleed Bin Al Waleed Road,
Bur Dubai
U.A.E
Tel No : + 971- 4 - 3596425
Fax No : + 971- 4 - 3591351
e-mail: [email]sales@intexuae.com[/email]
 
INTEX WAY GULF LLC (Retail and Export Divisions)
Office No: 3B
Al Raffa 1, Plot  P 92/1(316-420)
Al Raffa , Burdubai
Tel No : + 971- 4 - 3931991
Fax No : + 971- 4 - 3933731

---

