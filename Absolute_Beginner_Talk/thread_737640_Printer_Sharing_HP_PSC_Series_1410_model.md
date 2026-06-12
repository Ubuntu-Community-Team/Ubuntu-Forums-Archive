---
title: "Printer Sharing HP PSC Series 1410 model"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by nemesis8601 on 2008-03-27
Hi everyone, I'm currently running Gutsy, and I'm having problem printer sharing through a router. I've read threads on printer sharing, and I'm able to follow the directions up until I choose the printer I want to share. The only model that resembles mine is the HP PSC Series 1400. Is there anything I can do? 

The computer directly connected to the printer is currently running XP; does this matter?

Thanks!

---

### Post by lswest on 2008-03-27
wait, are you trying to share the printer from XP, or from gutsy?  If you share it from XP you should be able to access it just fine from Ubuntu.

---

### Post by nemesis8601 on 2008-03-27
The printer is connected to an XP computer, and I'm having trouble connecting to the printer wirelessly, only when I'm running Gutsy. When setting up printer sharing, I can't find the exact model of my printer. When I selected PSC 1400 instead, the printer tried to print a test page but stalled. I had to restart the printer for it to work from the XP computer.

---

### Post by lswest on 2008-03-28
okay, so you're trying to connect to the printer from your Ubuntu install, but can't find the right model for it?  What model exactly is this?

Also, [http://www.hp.com](http://www.hp.com) actually has drivers for Linux, so you might have luck finding what you need there.  Lastly, you can set up and configure the printer to be shared from the XP computer, then just connect to the printer from Ubuntu and it should be recognized properly.

Oh, by the by, make sure you checked "show LAN Printers" or some such uption under the "preferences" menu of your printer menu (system-->administration-->printing)

And lastly, i'm still not entirely sure, are you setting up the actual printer share on linux, or on the XP computer?  Because after you set up the printer share in XP or Linux, you just have to connect the other computer to the printer using the URI (in windows it is: \\<computername>\<nameofprinter>, in Linux it's something like smb://<computername>/<nameofprinter>)

---

