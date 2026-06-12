---
title: "USB - Any way possible ?"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by Amped-Gaming on 2005-11-27
Hello.


Im new to Ubuntu, and generally linux.


Im using the LiveCD.


The problem is, i cant get passes the "install" because i need to press ENTER and my keyboard and mouse are both USB devices.



is there any way i can use USB on linux ?

---

### Post by aysiu on 2005-11-27
It's probably not a Linux thing. It's probably a Ubuntu thing.
Different Linux distros have different hardware detection.
Generally, Ubuntu gets stuff, but it doesn't always.
How new are your keyboard and mouse?

---

### Post by Amped-Gaming on 2005-11-27
Keyboard - 3 years old.

Mouse - Not sure, Razer diamondback LE plasma.

---

### Post by ssam on 2005-11-27
you might want to check your bios usb options. it might have a magic options that makes it work.

---

### Post by lcg on 2005-11-27
[QUOTE=ssam]you might want to check your bios usb options. it might have a magic options that makes it work.[/QUOTE]
That "magic option" might be called something like "USB legacy support". Try to enable it and see if you can then start the installer.

HTH,
Lars

---

### Post by Amped-Gaming on 2005-11-27
[QUOTE=lcg]That "magic option" might be called something like "USB legacy support". Try to enable it and see if you can then start the installer.

HTH,
Lars[/QUOTE]


I cant find that in my BIOs, any other way of doing it ?

---

### Post by megamania on 2005-11-27
[QUOTE=Amped-Gaming]Keyboard - 3 years old.

Mouse - Not sure, Razer diamondback LE plasma.[/QUOTE]

I have successfully installed Ubuntu two times:

- the first time (hoary) I used a three-year old USB keyboard/mouse from Logitech
- the second time (breezy) I used a new (5 months) USB keyboard/mouse, still from Logitech

I had no problems whatsoever, so you may want to check your BIOS settings, as others suggested.

Anyway, the easy way would be cheating: borrow a standard keyboard from a friend and install Ubuntu using that one.  :-)

---

### Post by Amped-Gaming on 2005-11-27
CAnnot find that in teh BIOs anywhere.


[Here is my pc](http://www.uktsupport.co.uk/advent/pc/3412.htm)


Although, it now has:

1gb RAM
Radeon 9600XT 256mb


Any help ?

---

### Post by Amped-Gaming on 2005-11-27
Also, i've tried KNOPPIX linux, and that has the same problem with keyboard.

---

### Post by ssam on 2005-11-27
maybe there is a bios update that allows this. or there is some documentation about the bios somewhere.

you may have to borrow an old school keyboard and use that for the install.

or you could try fedora, that has a very different installer and may work.

or if you can wait for [the Dapper Drake]("https://wiki.ubuntu.com/DapperDrake") to be released it will have a new installer, [UbuntuExpress]("https://wiki.ubuntu.com/UbuntuExpress").

i can't quite tell from your post, does the live cd work properly? is it just the install that you can't make work?

---

### Post by Amped-Gaming on 2005-11-28
The live cd works fine, all the way up until i have to choose language, but of course, my keyboard is not detected, so there is nothing i can do.

---

### Post by Bartender on 2005-11-28
Hi, Amped -
What kind of BIOS do you have?  Although the computer manufacturers confuse the issue by adding their own splash screens and such, there are only two basic BIOS programs that you're likely to be dealing with...Award and - er - whatever the other one is.  Somebody oughta be able to look in theirs and tell you exactly where to find USB support.  In my Award BIOS it's tucked under the "Advanced" sub-menu.
I enter that sub-menu then arrow down to "USB Configuration" and enter again...
In my BIOS (for an ASUS P5GDC-V) the BIOS tells me on this page whether it sees any USB devices.  That'd be a neat tool for your situation, but I don't think older BIOS'es have that feature.
 
I've got choices for:
- USB Function - Enabled or Disabled (pretty obvious there), 
- Legacy Support - Auto, Enabled, or Disabled (Auto only activates USB if the devices are detected at startup.  I set mine to Enabled because I wasn't sure what would happen if I plugged in my old card reader after the computer was already started)
- USB 2.0 Controller - Enabled or Disabled (I don't know what to suggest - are both of your devices 2.0?)
- USB 2.0 Controller Mode - HiSpeed or FullSpeed (Again, I don't know what to suggest)

---

### Post by Amped-Gaming on 2005-11-28
The BIOs i have are "Phoenix BIOS".


I cannot find USB config. in there.


Its strange, the only OSs that seem to work are Mandrake and Windoze.^^

---

### Post by Bartender on 2005-11-28
Hi, Amped -
Yeah, I visited the link you supplied after I posted and saw that the BIOS was Phoenix.  That's the "other one" I couldn't think of.  Speaking of not thinking... if your USB keyboard and mouse were working on this same machine under Windows, then your BIOS settings clearly are not crippling the devices.  And you say they worked under Mandrake.  Wonder if Aysiu hit the nail on the head when he said that it may just be a Ubuntu thing?

---

### Post by Amped-Gaming on 2005-11-28
Alot of other OSs dont work either, and i mean alot.


I've tried about 10 different OSs.


And i really like Ubuntu :(

---

