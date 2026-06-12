---
title: "M3N78-EM Maiboard with GeForce 8300 Chipset"
date: 2013-01-13
forum: Asus Ubuntu Support (CLOSED)
---

### Post by broiler1985 on 2013-01-13
Hey guys!

My first post here, so I want to say a friendly "Hi @ all!" to y'all.

I have a problem.
My USB-Bus seems to hang itself up from time to time.. especially when I plug in a new device.. the device is recognized and -zapp- all my USB-stuff (like mouse and keyboard) stops working.
I've been able to solve it one time, but after flashing my bios to a newer version because of a cpu-change the problem's there again. I really can't remember what I did back then..
I already tried "Plug and Play OS" in the BIOS-settings and stuff like "acpi=force irqpoll" but none of those things work..
After googling a little I found out that this seems to be a common problem with the chipset but I can't find out how to solve this.. and using my favorite OS isn't as fun when the USB devices refuse to work at a random time.

Thanks in advance :)

---

### Post by save2 on 2013-04-18
Asus M3N78-EM and family has a known issue with Ubuntu and freezing (mainly when attaching a USB device).

the symptom is that if you run: cat /proc/interrupts
you will some usb device raise 1000 interrupts/sec. maybe more. this will eventually run your system crazy.
someone else thinks he solved it: [http://ubuntuforums.org/showthread.php?t=1148361&page=2&highlight=M3N78+usb+freeze](http://ubuntuforums.org/showthread.php?t=1148361&page=2&highlight=M3N78+usb+freeze)
but I doubt if that's a real solution.

I am thinking to order an internal USB card (with a Samsung chip set) ... will report if that helped

---

### Post by save2 on 2013-04-21
I managed to bypass the issue here:
[http://ubuntuforums.org/showthread.php?t=2136506&p=12612114](http://ubuntuforums.org/showthread.php?t=2136506&p=12612114)

---

