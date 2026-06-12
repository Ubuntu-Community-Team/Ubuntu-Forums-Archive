---
title: "new battery, done, help me set the time and date on a g3"
date: 2006-10-22
forum: Apple PPC Users
---

### Post by eddieboyinla on 2006-10-22
just installed the battery, new, and the time and date still shows 1904, how do i reset the time and dtae? it's apple g3, bubble green, open firmware, applepowermac2, and its already loaded with linux, ubuntu, witch follows my previous thread, help, peace out people.:p

---

### Post by jaradronald on 2006-10-22
Hey eddie. Can u run the Live version of Ubuntu on your system? If so you could boot up the system to the shell and run the following:
 
==========
Login: root
Password:
 
date --set="10/23/2006"
init 6
 
==========
 
When you reboot the date should be saved to your Firmware (as long as there's not another dead battery somewhere on your motherboard...).

---

### Post by eddieboyinla on 2006-10-24
just wanted to tell you thank you for helping me set my time and date, now ive lost my internet capabilitys, so im am attempting to ramefy my current situation, wish me luck, both my "root" and "username" have the same password, was wondering why i need to change one, and how to do this, i've tried this many times, with no success yet, any advice?

---

