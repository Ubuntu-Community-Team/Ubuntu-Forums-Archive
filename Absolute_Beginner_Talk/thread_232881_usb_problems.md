---
title: "usb problems"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by mrvgarg on 2006-08-09
Hi

After some time the usb ports turn off and no usb stuff works. This usually happenes when amarok is launced and is updating library from external hardrive. I am kubuntu. Thanks.

---

### Post by arjun.shankar on 2006-08-09
You connect your external drive through a USB port right? I think if it drains too much current, USB ports get shut off.

---

### Post by arjun.shankar on 2006-08-09
try:

**cat /var/log/syslog.0 | grep "over-current"**

I'm out of depth here actually... But no harm trying. Maybe someone smarter than the both of us will turn up!

---

### Post by mrvgarg on 2006-08-09
The hardrive is connected to a usb hub. It has it own power supply. The hub has a bluetooth adaptor and logitech mouse connected to it. The thing is the hardrive gets randomly disconnected from usb. An if I attach any other devices such as 4gb usb stick in another usb port it also dose not work. However I can see the mouse still in settings.

---

### Post by arjun.shankar on 2006-08-10
Well, the hub still connects to the computer and drains some current from it right? So too much current could still be the problem.
I think you should try out the command from my last post, and post the output here.

One more thing. Have you tried connecting directly to your computer instead of through the hub, and  observing how it behaves?

---

### Post by mrvgarg on 2006-08-10
I tried the command in konsole but no output is produced.

---

### Post by Raistlin355 on 2006-08-10
Have you tried switching the ports that the hard drive, mouse and keyboard are plugged into? Maybe you have a bad hub?

---

### Post by arjun.shankar on 2006-08-11
Try with syslog, kern.log and kern.log.0 also. They are in the same directory.

---

