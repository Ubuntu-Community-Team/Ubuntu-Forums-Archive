---
title: "Imon Vfd"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by barkerben on 2006-11-06
Hi,

I have been trying to set up the IMON VFD in an antec fusion case to display data froma  system running Ubuntu. 

I had no errors during setyp and now have a directory labelled /dev/lcd0 and a module loaded called imon_vfd.

However, if I try and use the device, for instance by doing the following:

echo "Hello World" > /dev/lcd0

I get an error message that there is no such device. But I can see it there in front of me in the dev directory... Can anyone suggest a solution?

Cheers,

Ben

---

### Post by po0f on 2006-11-06
barkerben,

Is it perhaps a permissions problem?  Make sure you have write access to the device.

---

### Post by barkerben on 2006-11-06
i - I thought of that. If I don't have enough permissions thought I get a "Permission denied" error. If I use superuser (Sudo -s -H) then I gen no such error, but it claims the device isnt there.

I can even get it to autocomplete the command for me, so something knows it is there...

Ben

---

### Post by piec2 on 2006-12-04
You may want to give this a try:
[http://www.ubuntuforums.org/showthread.php?t=306437&highlight=antec+VFD+fusion](http://www.ubuntuforums.org/showthread.php?t=306437&highlight=antec+VFD+fusion)

---

