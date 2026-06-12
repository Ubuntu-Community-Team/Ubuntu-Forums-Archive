---
title: "modem"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by ice.man on 2006-04-17
how to install a 56k modem???

---

### Post by big joe on 2006-04-17
You're going to need to be a bit more specific.
Internal or External? Is it a "Winmodem"?
Give the resident gurus  some info to play with and they will fix you right up.
I can't help you myself - I have a 56K Conextant winmodem installed in my box and it does not play nice with my Ubuntu.

---

### Post by ice.man on 2006-04-18
external netcomm simplicity 56

---

### Post by StefanoCole on 2006-04-19
Hello, the starting point is the following wiki:
[https://wiki.ubuntu.com/DialupModemHowto?highlight=%28modem%29]("https://wiki.ubuntu.com/DialupModemHowto?highlight=%28modem%29")

Anyway, since you own an external modem (a serial hardware modem I suppose), you should simply set it running "sudo pppconfig" from a terminal. Enter the information as needed. Use the name provider for your default connection. COM1 is /dev/ttyS0, COM2 is /dev/ttyS1, and so forth.
Add your user to the dip group using the advanced options.
Save and exit.
To connect:
sudo pon
If you get nothing or if you run into trouble, open another terminal and do:
sudo tail -f /var/log/messages

This may give you an up-to-the-second idea of what is going on. Post the result in your question to the forum.
sudo poff hangs up.
You need to log out and back in for your user/group settings to be updated. You can then pon and poff without the sudo. 

Stefano

---

