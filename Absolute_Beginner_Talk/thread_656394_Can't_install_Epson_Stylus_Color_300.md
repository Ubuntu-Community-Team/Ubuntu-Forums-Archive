---
title: "Can't install Epson Stylus Color 300"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by bajun on 2008-01-02
I have connected my printer Epson Stylus Color 300 through a "Parallel to USb" adapter. My mashine is HP Compaq 6720s Laptop with Ubuntu Gutsy.
In hardware manager i can see:

  82801H (ICH8 Family) USB UHCI Controller #1
  > UHCI Host Controller
     > IEEE 1284 Controller
        > USB Printer Interface
           > Stylus COLOR 300 

(printer.device - /dev/usb/lp0)

But when i started a CUPS GUI, my printer was not autodetected.

CUPS simply "don't know" about USB. There are only network backends in GUI. In the web interface localhost:631 is the same. After install "printconf" nothing has changed. If i use a custom line in conf file to connect a printer (usb://dev/usb/lp0) CUPS says, that printer is not connected.

Any help is needed!

---

### Post by philinux on 2008-01-02
Did you use System>Admin>Printing ?

Select add printer

---

### Post by bajun on 2008-01-02
Yes. But the printer was not autodetected, and there is no option to choose usb backend manuell.

---

### Post by bajun on 2008-01-02
There are only:
Windows printer via SAMBA;
App Socket/HP...;
ipp;
LDP/LPR;
Sonstiges (German Ubuntu)

If i choose "Sonstiges" and type USB://dev/usb/lp0, tray says "printer is not connected"

---

### Post by philinux on 2008-01-02
> **bajun said:**
> Yes. But the printer was not autodetected, and there is no option to choose usb backend manuell.

Can you not select manufacture and then select the 300 from the list. I can if I select add printer to my system.

---

### Post by bajun on 2008-01-02
I have selected 300 from list. CUPS says "printer is not connected"

---

### Post by bajun on 2008-01-03
First - I press ADD PRINTER button:

[ATTACH]55338[/ATTACH]


Nothing has detected, manually configuration is on the screen. As you can see, there are no backends for local printers, No USB-backend:

[ATTACH]55339[/ATTACH]


I select "Custom" section and type USB://dev/usb/lp0:

[ATTACH]55340[/ATTACH]


Searching in progress:

[ATTACH]55341[/ATTACH]


I can choose a manufacturer and modell:

[[IMG]http://img179.imageshack.us/img179/1938/bildschirmfotoneuerdrucrq5.th.png[/IMG]](http://img179.imageshack.us/my.php?image=bildschirmfotoneuerdrucrq5.png)

[[IMG]http://img179.imageshack.us/img179/9079/bildschirmfotoneuerdrucdp2.th.png[/IMG]](http://img179.imageshack.us/my.php?image=bildschirmfotoneuerdrucdp2.png)


Then:

[[IMG]http://img179.imageshack.us/img179/5340/bildschirmfotoneuerdrucvt9.th.png[/IMG]](http://img179.imageshack.us/my.php?image=bildschirmfotoneuerdrucvt9.png)


Result at the bottom of the screen - printer is not connected.

[ATTACH]55342[/ATTACH]

What can I make now?

---

### Post by bajun on 2008-01-09
After reinstall of Gutsy on clear installation with and without updates all works fine. My printer was detected and work completely with CUPS. I can setup USB printer. 
Something was broken. Maybe some backport or proposed packet was bad or something was uninstalled. Or some config file about USB permissions which was manually edited around VirtualBox installation caused this problem. I will probably test this again.

---

### Post by philinux on 2008-01-09
Glad you got it sorted.

---

### Post by Niniel on 2008-01-09
Yes, good that you managed to solve it, I was puzzled by your problem because I just installed my Epson Stylus 760 Colour the other day and it went without a hitch, it was impressed. 
It's weird though that you had to re-install the OS for it; imo, that's entirely too often the best fix; it's worse than Windoze :) .

---

### Post by bajun on 2008-01-09
I have reinstalled, bun not only to fix this :rolleyes: First i have upgraded to Alpfa Hardy to see if there a new kernel version exist in order to enable Native SATA support for my harddrive, Then i have installed Gutsy again.

And for another users: right URI for printer is usb://EPSON/Stylus%20COLOR%20300

---

### Post by bajun on 2008-01-22
But, after that, I have another strange problem with my printer. Now it's a connection method issue. 
Two lines on top of every print, which represent a service command that should not to be printed 

EJL 1284 4
EJL

Here is the topic [http://ubuntuforums.org/showthread.php?t=662796&highlight=EJL+1284]("http://ubuntuforums.org/showthread.php?t=662796&highlight=EJL+1284")

Please help

---

