---
title: "[SOLVED] dialup ppp not minimising after connection"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by fourscore on 2007-10-23
I am running Gutsy and have installed the sl-modem drivers for my laptop.    When I  try connecting to internet thru  gnome-ppp dialup   the  connection gets established but  the dialup window keeps showing  Authenticating.    There is no connection notification    but  i can browse the net.
The   options  Minimize and  Dock in notification area  do not work.       Tried adding the Modem Monitor applet to the  panel  but of no  use.
In  Feisty  the modem lights applet automatically came up once dialup connection was established.

Pls help

---

### Post by natehatewindows on 2007-10-23
I am having almost the same problem. Mine just keeps saying "dailing...." but i can still browse just not use apt-get or anything.....

maybe you should try to go into the options and click the "stupid mode"....it might help you.

:)

---

### Post by fourscore on 2007-10-23
Just found out  that this is  a bug in Gutsy-gnome-ppp.    
See link -   [https://bugs.launchpad.net/ubuntu/+source/gnome-ppp/+bug/121487](https://bugs.launchpad.net/ubuntu/+source/gnome-ppp/+bug/121487)

---

### Post by natehatewindows on 2007-10-23
:) thanks!

---

### Post by natehatewindows on 2007-10-23
so how do i compile that file? :)

thanks, ;)

---

### Post by fourscore on 2007-10-23
I have no clue about compiling the file.   Will wait for the bug to be fixed officially.
Meanwhile  I  have installed  the     K-ppp  dialer  as mentioned in the  bugpost  and it works  perfectly.

---

### Post by natehatewindows on 2007-10-23
see i try to do that and it wont let me ...give me an error that dependencies are not satisfied. how did you do it with no connection? :confused:

---

### Post by fourscore on 2007-10-23
There were no dependency errors.     I downloaded (thru a wifi connection)    Kpp and Kpp-logviewer thru Add/Remove programs. It was a 23 MB (approx) download which has some lib files also.

---

