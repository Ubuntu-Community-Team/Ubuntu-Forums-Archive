---
title: "Configuring the web-Cam"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by pkj on 2007-06-14
Hi, i need to configure my D-Link web cam. Also, which program do i need to start using my web-cam

pkj

---

### Post by w4ett on 2007-06-14
Start by checking the results of lsusb in the terminal which will tell you if the cam is being recognized, and what series cam chipset it is.

---

### Post by w4ett on 2007-06-14
In the Synaptic Package Manager there is a app called Camstream.....select it and it should recognize your hardware.

---

### Post by pkj on 2007-06-14
I have installed camstream as per your advice. But i dont know from where to launch this application.

pkj

---

### Post by chemtut on 2007-06-14
open a terminal
type camstream      and press enter

---

### Post by pkj on 2007-06-14
i did exactly that. Camstream window opens but nothing after that. In FILE < OPENVIEWER i did not see my web-cam listed. Instead my TV tuner card is listed and its selection also produces nothing on the screen

pkj

---

### Post by w4ett on 2007-06-14
Hmmmmm.......give us the output of command LSUSB and see if the cam  appears

---

### Post by pkj on 2007-06-14
LSUSB on a terminal gives me "command not found"
CAMSTREAM presents the following output on the terminal

 Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0

pkj

---

### Post by sailor2001 on 2007-06-14
I don't believe there is an IM in linux that you can use the web cam on. unless it's jabber, but not sure about that one

---

### Post by w4ett on 2007-06-14
My bad Should have been in lower case....lsusb...SORRY

---

### Post by pkj on 2007-06-14
output of "lsusb" is as follows
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 2001:f115 D-Link Corp. [hex] 
Bus 001 Device 001: ID 0000:0000  

pkj

---

### Post by pkj on 2007-06-14
output of "lsusb" command is 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 2001:f115 D-Link Corp. [hex] 
Bus 001 Device 001: ID 0000:0000  

pkj

---

### Post by Songwind on 2007-06-14
> **sailor2001 said:**
> I don't believe there is an IM in linux that you can use the web cam on. unless it's jabber, but not sure about that one

You can use webcam in kopete, and I believe aMSN.

You can also use it in Ekiga for SIP based VOIP calls, but not for IM networks.

---

### Post by w4ett on 2007-06-14
If your camera does not appear in the output (I'm assuming it is a USB camera)  try changing it to a different usb port (i.e.: backplane I/O ports to front of case if you have them) .  Another question.....have you had any problems with your USB on your motherboard or hub that you are using?...just wondering

---

### Post by w4ett on 2007-06-14
> **pkj said:**
> output of "lsusb" command is 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 2001:f115 D-Link Corp. [hex] 
Bus 001 Device 001: ID 0000:0000  

pkj

Well, it does appear I see.....(I don't know why my last post didn't appear in a timely manner)  Camstreamer SHOULD be able to see it, but your Vid card capture is appearing in the streamer if I am reading your previous postings.   Click on the FILE tab on Camstreamer and see if your camera appears in the dropdown menu

---

### Post by pkj on 2007-06-15
No. The webcam does not appear in the drop down menu.
I have faced similar problem in windows XP earlier. There i had to disable the TV card for web-cam to work.
I am not sure what to do in ubantu

pkj

---

