---
title: "Networking inux and XP"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2006-12-06
I have my XP and linux machined connectednetworked to a belkin modem router and can access the internet without problems on both machines.  Would it be possible to use my printer which is connected to the XP machine from the Linux machine?

---

### Post by Iowan on 2006-12-06
Depending on whether Linux drivers are available for your printer...
[https://help.ubuntu.com/community/WindowsXPPrinter]("https://help.ubuntu.com/community/WindowsXPPrinter")

---

### Post by burek on 2006-12-06
> **a.v.l said:**
> I have my XP and linux machined connectednetworked to a belkin modem router and can access the internet without problems on both machines.  Would it be possible to use my printer which is connected to the XP machine from the Linux machine?

both are possible

try :
kprinter &

---

### Post by a.v.l on 2006-12-07
> **Iowan said:**
> Depending on whether Linux drivers are available for your printer...
[https://help.ubuntu.com/community/WindowsXPPrinter]("https://help.ubuntu.com/community/WindowsXPPrinter")

Linux drivers are available for my HP printer and I've used the printer connected directly to Ubuntu.  When trying to network the printer using the above link, I'm asked for a username and password, would these be the ones used to sign on to Ubuntu?  I've tried using "guest" for the username as suggested but it didn't work. I was also asked to allow a port to be opened on the Ubuntu machine, at which point I stopped trying because of security concerns:-k .  

Is opening a port, safe to do in Ubuntu, doesn't this compromise the security of my Ubuntu machine when networking it to an XP machine? (I'm afraid I can't remember the port I was asked to open) Do I need to allow a port to be opened and are there any securities issues in doing so?

---

### Post by Scorpuk on 2006-12-07
If the printer is connected to the windows machine try activating the guest account and see what happens.

---

