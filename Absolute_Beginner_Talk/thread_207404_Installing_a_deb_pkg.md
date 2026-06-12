---
title: "Installing a deb pkg"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by mackinax on 2006-07-01
I am trying to install the music player "Aqualung" from a .deb package (from [here]("http://aqualung.sourceforge.net/index.php?tab=download")) with gdebi. The package is in my Home directory. But I get the following error:

*Failed to open the software package The package might be corrupted or you are not allowed to open the file. Check the permissions of the file.*

the permissions are '' -rw-r--r-- '' : Am I doing something wrong or is it corrupted?

---

### Post by reacocard on 2006-07-01
try doing it from a terminal (Applications -> Accessories -> Terminal). type in:

sudo dpkg -i 
(put a space after the -i)

then drag the file onto the terminal (it's path will be entered into the terminal)
hit enter

---

### Post by mackinax on 2006-07-01
> Selecting previously deselected package aqualung.
(Reading database ... 78166 files and directories currently installed.)
Unpacking aqualung (from .../aqualung_0.170.0-1_i386.deb) ...
dpkg: dependency problems prevent configuration of aqualung:
 aqualung depends on libcddb2; however:
  Package libcddb2 is not installed.
 aqualung depends on libjack0.80.0-0 (>= 0.99.0); however:
  Package libjack0.80.0-0 is not installed.
 aqualung depends on liblrdf0; however:
  Package liblrdf0 is not installed.
dpkg: error processing aqualung (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 aqualung


... I thought gdebi was supposed to:> If you have a missing dependency, it will inform you of that. It will also inform you if there's a newer version available from the repositories!

---

### Post by az on 2006-07-01
It is telling you that libjack0.80 is not available (libjack0.100.0-0 is available in Dapper - this package was not built for Dapper)

cddb2 is in universe.

---

### Post by mackinax on 2006-07-01
yeah, i got libjack0.100.0-0 ...
> dpkg: dependency problems prevent configuration of aqualung:
 aqualung depends on libjack0.80.0-0 (>= 0.99.0); however:
  Package libjack0.80.0-0 is not installed.
dpkg: error processing aqualung (--install):
 dependency problems - leaving unconfigured

I reckon i need to find an older version

---

### Post by mackinax on 2006-07-01
Ok, i have it installed now ... just have to figure out how to use it

Thanks!

---

