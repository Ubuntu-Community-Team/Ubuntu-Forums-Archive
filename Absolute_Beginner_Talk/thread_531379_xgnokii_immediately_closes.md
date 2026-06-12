---
title: "xgnokii immediately closes"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by mrtheduke on 2007-08-21
I'm trying to run xgnokii.  It installs fine, however when I try and run it I get a splash screen and the xgnokii windows appears for a second then disappears.  Does anyone know how to resolve this?

UBUNTU 7.04
0.6.14-3 (gnokii)

---

### Post by ddrichardson on 2007-08-21
run it from the terminal and post any output

---

### Post by Jose Catre-Vandis on 2007-08-21
Or try KMobileTools, this works when Xgnokii did much the same with me

---

### Post by filiberto on 2007-11-05
Same problem here with Ubuntu 7.10 and Nokia 6125; please also note that bluetooth devices are perfectly connected and Phone Manager's only function (send SMS) perfectly works.

Here is my command line response:

(xgnokii:6142): Gtk-WARNING **: horizontal scrolling not implemented

(xgnokii:6142): Gtk-WARNING **: horizontal scrolling not implemented
Gnokii serial_open: tcgetattr: Input/output error
Couldn't open FBUS device: Illegal seek
Gnokii serial_open: tcgetattr: Input/output error
Couldn't open FBUS device: Illegal seek
Gnokii serial_open: tcgetattr: Input/output error
Couldn't open FBUS device: Illegal seek
Telephone interface init failed: Command failed.
Quitting.
Failed to open the phone. Quitting.



Any suggestion? :confused:

---

### Post by Haak on 2007-11-07
Hi,

Just decided to search around for this problem. I found that you have to edit the gnokiirc file:
sudo gedit /etc/gnokiirc
 Read through the file and change to your needs.
then save is as 
$home/.gnokiirc

try with:
 gnokii --identify 
if your settings are correct. More information can be found on the gnokii project page. I was able to get my adress book from my Nokia 7390. That's about it.

---

### Post by ericsp on 2008-01-25
I get a connection but the phone asks for a password. where can I found it/change it???

---

