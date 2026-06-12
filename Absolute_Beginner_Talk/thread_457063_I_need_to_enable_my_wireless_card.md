---
title: "I need to enable my wireless card?"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by JediJames on 2007-05-28
I read the the wireless troubleshooting guide a few times. I skipped over the part about disabled cards on laptops at first, because my computer is not technically a laptop. At that point a figured it was the driver, it had to be the driver, so I found a fix for the driver that is supposed to be used for my D-Link DWL-650, [here]("http://sin613.blogspot.com/2007/02/i-win.html"). I followed the instructions there and the instructions on the [second page]("http://sin613.blogspot.com/2007/02/i-win-again.html") to the letter. Afterwards my device had the right driver associated to it but it became disabled. That's when I looked at the section on disabled cards. My computer is not really a laptop, it is a Sony PCV-W10, and I could find no information on how to enable the card. Does anyone know if I did something wrong? BTW I didn't feel like copying the output of lshw, but I thought it might help so I took a screenshot.
[IMG]http://i165.photobucket.com/albums/u60/MOMO-100/disabled.png[/IMG]

If anyone can help I would love them forever. I really love Ubuntu and would hate to have to use windows just for internet.

---

### Post by JediJames on 2007-05-28
Never mind, I got my boss to approve an advance on my pay and bought a new USB adapter that was listed as supported 'out of the box'. It worked! I just can't connect to my network :(

---

### Post by kevmore on 2007-05-29
best way to fix the problem is to install the older versions of network manager.  I know nothing about linux, that's why I went with this solution.  The end result is your wireless will work.  But you have to reboot to make it work.

---

### Post by JediJames on 2007-05-29
That might have been a good solution, if I didn't jump ahead. Problem with my network was using the network manager on roaming it wouldn't acquire in IP I just connected to my access point and used a terminal command which was listed in the wireless troubleshooting guide. It acquired me an IP and I'm connect, though network manager doesn't think I am. Personally I don't care what it thinks as long as I get results. Thanks anyways, I've noticed that Linux users are really helpful.

---

