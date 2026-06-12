---
title: "Touchscreen Problem !!!"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Dudutzu on 2008-02-01
Hy everyone !!  
Since this is my first post let me introduce myself !
I'm from Romania , I'm 21 years old and recently I got a sudden interest in UBUNTU OS
At work my boss took a peak in my computer and spouted the difference ( between mine and his ) After a short discussion he found out  that Ubuntu is a the most user friendly  OS ( Linux ) on the " market ".So he got the idea of using in his company (POS , cash registers)

And that is the way i got the task To make the touch screen working with Ubuntu...

AND NOW THE technical stuff

I have the Linux drivers ( the touchscreen is neither USB or RS232 or PS2 (it i integrated with the system with  special ( internal connector ) 

I have flowed the instructions in the GUIDE and failed to make the touchscreen work ,, 

copied the driver in :  /usr/lib/xorg/modules/input 
modified the xorg.conf like :

Section “ServerLayout”
  ...
       InputDevice                “EETI” “SendCoreEvents”
       
 ....
EndSection

And added  the device like this(in xorg.conf)

Section “InputDevice”
      Identifier       “EETI”
      Driver           “egalax”
      Option          “Device”           “/dev/ttyS0”
      Option          “Parameters”   “/etc/egalax.cal”
      Option          “ScreenNo”      “0”
      
 EndSection





         PLEASE TELL ME WHERE I'M WRONG 


Thank you for your time and effort !!!!

---

### Post by mike1821 on 2008-02-01
My friend, 

First of all we should eliminate the case that you have any hardware problems communicating with the controller.

Therefore do the following: 

Login in a console and execute the "sudo cat /dev/ttyS0", then touch the monitor... You should be able to see some random characters appear on your console output.

If this works, then post the output of the Xorg.0.log file, to see if the driver module is correctly loaded into the kernel.

Mike

---

### Post by Dudutzu on 2008-02-01
Hy , mike1821

Thanks for your answer , i will follow your instructions as soon as i get to work ( probably Monday morning )

I don't think there is a hardware problem the PC had window installed before Ubuntu and the touch worked perfectly ( anyway , I'll get back to you as soon as possible )

---

### Post by Dudutzu on 2008-02-04
**Monday morning  :**

Well first HY !

Now i got to work and try ed your command
Without sudo since for the install i used root account and the output was nothing ,
The console was just waiting for the next command (not the next event , the next written command !

Now the question i have is that "cat" is displaying the content of a file !! ?
So after my judgment the cat shod display the content of the file "ttys0" ...

Anyway i dident get any answer !

Thanks again for your time !

---

### Post by mike1821 on 2008-02-04
Apart from displaying the contens of a file "cat" command opens a serial port as a terminal program would do. Anyway you should be able to see some random output when you touch the screen. 

The fact that you do not means that, either that your touchscreen is using a different serial port, or that there is a problem with your hardware configuration. If you have more than one serial ports available in your PC, you can try the "cat" command test in all of them and see if you will get any output.

If you are have only one port you should post the output of the Xorg.0.log file. This file is located into the /var/log/ directory. Also execute the command "setserial -a /dev/ttyS0" and post its output.

Regards,
Mike

---

### Post by Dudutzu on 2008-02-04
Well , I'm starting to get tired ... Still trying !! :(:)


Now here is what happend to me today ... :confused: 

I've tried your suggestion with the cat command and failed again !
After a little tinkering it crossed my head to reinstalling the OS ... 
And now the wired thing !! 

IF I'M BOOTING FROM THE LIVE CD  the touchscreen is half working , meaning id dosen't move the mouse bat if i touch the screen it clickes on the place the mouse pointer is located !!! 
After the installation it completely dyes ( the touchscreen i mean ) !! 

How do i see how many serial ports do i have ?

I'll make a fresh install tomorrow and continue the learning :) 

Mike1821 thanks again for your help , and sorry for all the noobish questions , :( I Hope you'll don't lose your patience with me , I'm trying to get as many answers as i can from the internet , still a lot of them are blurry !!

---

### Post by mike1821 on 2008-02-06
In order to see how many serial ports you have available type

```
dmesg |grep ttyS
```

The output of the command execution will be something like the following:

serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

As you can see I have only one serial port available named as ttyS0. If you see also ttyS1, ttyS2... it means you have more than one ports.


If as you are saying you are able to operate the touchscreen using the LiveCD, why don't you try to copy the xorg.conf file that the CD uses and put it in your normal installation.

Mike

---

