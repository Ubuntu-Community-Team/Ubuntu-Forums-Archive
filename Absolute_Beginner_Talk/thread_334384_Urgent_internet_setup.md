---
title: "Urgent internet setup"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by KIFIKA on 2007-01-08
I really need step-by-step help setting up my internet, i have a research paper due tmw.

I am a compleat "noob" when it comes to linux, so sorry for my ignorance.

I am running ubuntu 5.10.
my modem is an ARRIS TM401B and uses the usb port. I have no idea what to do...pls help.

ps: sorry if this seems like its hard to read, i am using the wii for internet. 
also, i have no other computer, so i cant download or copy & paste.

thx in adv.

KIFIKA

---

### Post by ardvark71 on 2007-01-08
> **KIFIKA said:**
> I really need step-by-step help setting up my internet, i have a research paper due tmw.

I am a compleat "noob" when it comes to linux, so sorry for my ignorance.

I am running ubuntu 5.10.
my modem is an ARRIS TM401B and uses the usb port. I have no idea what to do...pls help.

ps: sorry if this seems like its hard to read, i am using the wii for internet. 
also, i have no other computer, so i cant download or copy & paste.

thx in adv.

KIFIKA

I'm assuming the modem we are speaking of here is a dial up modem, is this correct? If so, this would probably translate into a winmodem which probably will take more time than you have to give. 

Let's try this first...

If you go into "Networking," (under "System" and then "Administration,") highlight "modem connection" and click properties. Is Ubuntu able to auto detect it?

Best Regards...

---

### Post by KIFIKA on 2007-01-08
sorry, its a cable modem that uses the usb port. nothing came up on auto detect.

---

### Post by ardvark71 on 2007-01-08
> **KIFIKA said:**
> sorry, its a cable modem that uses the usb port. nothing came up on auto detect.

Ah, ok. My experiences with high speed internet connections through USB have been extremely spotty. I would recommend, if your modem supports it, a regular LAN connection. If it does, make sure your PC has an ethernet card or onboard port.

Someone else on here may have better instructions on how to set up and configure USB connections.

Best Regards...

---

### Post by KIFIKA on 2007-01-09
thank you for reading and giving your time.

is anyone else willing to help me? its kind of important.

thanks,
KIFIKA

---

### Post by doobit on 2007-01-09
> **KIFIKA said:**
> thank you for reading and giving your time.

is anyone else willing to help me? its kind of important.

thanks,
KIFIKA

Well, if you could submit your term paper with the wii and I was your teacher, I would give you an A for originality.
The spec sheet on your modem says it has an RJ-45 interface, unless you gave us the wrong model number.
Anything with a USB interface will most likely need device drivers, which may, or may not exist in Linux.
I agree with ardvark71 that you need to find a way to hook up to the RJ-45 if you want success.

---

### Post by KIFIKA on 2007-01-09
Thanks for all the help guys, After hours of staring at my screen i messed with it and i got everyhting working. Thanks so much, if it wasn't for your replies i wouldn't have even tried. 

best regards, 

Nick "KIFIKA" Padula

---

### Post by %hMa@?b&lt;C on 2007-01-09
> **KIFIKA said:**
> Thanks for all the help guys, After hours of staring at my screen i messed with it and i got everyhting working. Thanks so much, if it wasn't for your replies i wouldn't have even tried. 

best regards, 

Nick "KIFIKA" Padula
if you would not mind, please enlighten those of us here as to the steps that you took, so that others in your situation will be able to solve their problem.

---

### Post by KIFIKA on 2007-01-09
Well, it was actually quite simple. I first had to loose the whole USB cable, because i had not the slightest idea as to what to do with it. The cable modem i have has a ethernet port, so i searched for an old ethernet cable i had lying around. After setting it up, i still had no luck, i unplugged the modem, waited a little bit. Set everything back up using the ethernet this time, reboot and the such.  Then went to system > admin > networking set the properties of the DHCP  and everything this time worked. Which was kinda weird, because i had done it before but nothing at all happened...

---

### Post by ardvark71 on 2007-01-10
> **KIFIKA said:**
> Thanks for all the help guys, After hours of staring at my screen i messed with it and i got everyhting working. Thanks so much, if it wasn't for your replies i wouldn't have even tried. 

best regards, 

Nick "KIFIKA" Padula

You're welcome! Glad we could be of assistance 8)

---

