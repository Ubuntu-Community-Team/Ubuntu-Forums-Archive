---
title: "Wireless Configuration"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by Eggsaregood on 2007-01-27
So I just installed Ubuntu 6.10 and its my first time using Ubuntu and Linux so it is complete noob talk here. I have a wireless card Linksys WMP11 Wireless-B card on my computer.  It does not have a native linux driver, when i go to System>Administration>Network (or something like that) I only get an option for modem, but no wireless.  (yes, i am using another computer right now with windows) I do not have acess to my computer now since someone is working on my windows OS...

---

### Post by riven0 on 2007-01-27
If I'm not mistaken you need the ndiswrapper and the driver cd. You'll install the windows driver through the ndiswrapper. Try installing the gui utility for ndiswrapper, Either search for it in Synaptic Package Manager or install it through the terminal:

> sudo apt-get install ndisgtk

But beforehand, try running **iwconfig** through the terminal, just to make sure it doesn't need some simple configuration.

---

