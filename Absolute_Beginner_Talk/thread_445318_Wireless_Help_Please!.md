---
title: "Wireless Help Please!"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by dswhite85 on 2007-05-15
I just installed Ubuntu 7.04 last night, finally making the switch over to Linux!
However, my house is wireless and I've heard Linux isn't always too kind to wireless, but I also remember reading that 7.04 was more wireless friendly. I am having trouble though. I have a Linksys 2.4GHz (802.11g) Wireless-G PCI Adapter card (Model #: WMP54G). I don't know too much about wireless connectivity, but Ubuntu picks up my network, and I am able to type in the 10 digit password, and from there it just tries to connect and connect, but I am never able to get any internet activity. Any solutions would be much appreciated because I really want to use Ubuntu and toss Windows into the trash!

---

### Post by netwerx on 2007-05-15
one thing that screwed me up when i first started was the question it asks when it wants to connect.

I'm used to typing in my hex value from my pass phrase (windows).
The default entry for me was pass phrase, which my key was not.

Make sure at the screen that you enter your key on, is set right (ie. if its hex your typing in, use the drop down to set accordingly.)

Good luck.

---

### Post by esoterica on 2007-05-16
Linux isn't wireless friendly?

What an understatement that is, Linux is wireless awesome!

One of the main reasons I switched over to run Linux is because of the unbelievable things you can get it to do with wireless  that you absolutely can not do with Windows. Cool stuff like this which I'm still trying to figure out how to do myself and is a lot of fun and educational just trying to learn it all...

[http://www.ex-parrot.com/peter/upside-down-ternet.html](http://www.ex-parrot.com/peter/upside-down-ternet.html)

[http://www.kismetwireless.net/documentation.shtml](http://www.kismetwireless.net/documentation.shtml)

[http://monkey.org/~dugsong/dsniff/](http://monkey.org/~dugsong/dsniff/)

The actual software running inside your wireless router to make it work is probably Linux, so you've already been relying on Linux for your home wireless network this entire time and likely didn't even realize it.

It sounds like everything as far as your wireless card and configuration in Linux is already correct and working if you can see your wireless network and attempt to connect to it. I'd suggest opening up your admin control panel on your wireless router and check it to see if it's also seeing your wireless card on the Linux computer trying to connect. Most wireless routers let you do this with your web browser by typing in the IP address of the actual router in your web browser address bar.

See the documentation on the manufacturers web site for your specific router to learn how to do this if you don't already know how.

There are a lot of possibilities, sometimes when I have problems getting a new computer on my wireless network I reduce the security settings down as low as possible just to make sure that things do actually work, then I walk my security settings up 1 step at a time till I can identify the problem. For example, last time I had a problem I discovered it was because I was trying to use WPA2 security and the card I was trying to use for this didn't actually support it (even though the box said it would), I found a firmware update from the manufacturers web site solved the problem.

Something you may want to check is to see if your own security has been set to only allow specific MAC Addresses to use your wireless network, this is a pretty common security setting on many wireless routers. What may seem to be not working to you may instead be doing exactly what it's designed to do, prevent unauthorized connections to your wireless network.

I'm not trying to imply this as a fix for your problem, but it's certainly stuff you need to look into.

---

