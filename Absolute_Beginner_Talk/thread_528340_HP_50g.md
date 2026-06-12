---
title: "HP 50g"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by GranpaDan on 2007-08-17
I have recently purchased a HP 50g calculator. I haven't been able to get the conn4x communication software provided for the calculator to communicate with a PC to work on WINE. 

Anyone have any success stories out there ?

---

### Post by Alirio on 2007-09-26
Hello GranpaDan,

I have the same Problem, but I have reached the point where I can run the main program "Conn4x.exe" and the USB configuration programs "Usb2k.exe" and "Usb9x.exe".

In the normal Windows installation, as you shurely know, you have to run one of the USB configuration programs before you will find the "Connect trough USB" option in the main application "Conn4x.exe" 

When I run "Usb2k.exe" I get a "Install failed" message, but when I run the "Usb9k.exe" instead, I get "Install succesfull".  Nontherless the "Conn4x.exe" won't show up with the "Connect throug USB" option. :confused: 

Maybe someone else has more information?

Commandline:
```
env WINEPREFIX="/home/alirio/.wine" wine "C:\Programme\HP50g\USBDriver\Usb9x.exe"
```

```
 env WINEPREFIX="/home/alirio/.wine" wine "C:\Programme\HP50g\Conn4x.exe"
```

---

### Post by GranpaDan on 2007-10-06
I tried the same thing. I copied the installed files exactly how they are on the Windows side of my hard drive (I am currently dual booting Windows / Ubuntu) onto the same files in my .wine c directory. I can start the Conn4x.exe program, but it does not recognize a USB connection being present. 

Interesting, I did not find the file "Usb9x.exe".:confused:

GranpaDan

---

### Post by GranpaDan on 2007-10-30
Solution found. Please see my thread under Networking and wireless labeled "hptalx".:)

---

