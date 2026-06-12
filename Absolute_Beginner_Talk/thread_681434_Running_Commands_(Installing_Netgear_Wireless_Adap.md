---
title: "Running Commands (Installing Netgear Wireless Adapter)"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by the1calledbubba on 2008-01-29
I don't know one thing about Ubuntu. I have just installed it and a new wireless networking card that doesn't work. After looking on the internet for the whole day, I found this url:
[http://www.jimbo7.com/wiki/index.php?title=WG311v3](http://www.jimbo7.com/wiki/index.php?title=WG311v3)
Which seems to have the answers I want, only one problem...
I have absolutely no idea what it's talking about, expescially when it says to run a command. Where do I run the command? How do I run it? 
I know this is a lot to ask, but:
Can someone translate this forum into step by step instructions? 
I tried for hours but I guess I'm just not smart enough. I really would appreciate any and all help provided.
Thanks! :)

---

### Post by IamJohnHayes on 2008-01-29
[https://help.ubuntu.com/7.10/internet/C/index.html](https://help.ubuntu.com/7.10/internet/C/index.html)

This was helpful for me.  As far as commands run them in the terminal

Applications > Accessories > Terminal

---

### Post by the1calledbubba on 2008-01-29
Thanks man! I'll check it out right now!

---

### Post by the1calledbubba on 2008-01-29
Okay, Checked it out and found my way to
[https://help.ubuntu.com/7.10/internet/C/ndiswrapper.html](https://help.ubuntu.com/7.10/internet/C/ndiswrapper.html)
but when I go under Synaptic Package Manager there is no 
ndisgtk 
listed there. What can I do?

---

### Post by tizza10 on 2008-01-29
Which version of ubuntu are you running? I have ndisgtk available in synaptics in 7.10. Try a manual install from [http://packages.ubuntu.com/dapper/net/ndisgtk](http://packages.ubuntu.com/dapper/net/ndisgtk) and open it with GDebi Package Installer but it is better to use synaptics, in general.

---

### Post by the1calledbubba on 2008-01-30
I have the latest version, I think. I downloaded it last week. I haven't connected to the internet to download updates. Should I? If so, How do I? Again, thank you for your advice. I'm totally new to the Linx operating system besides working with Macs a very small bit and I thank you for your help

---

### Post by the1calledbubba on 2008-01-31
Okay, it worked, but I have one problem. Whenever I shut down my computer and restart it, it says the driver is still installed and the hardware is present, but Ubuntu's network tool bar doesn't show wireless network connection and I have to uninstall and reinstall the driver every time I turn on the computer. Any ideas?

---

### Post by tizza10 on 2008-01-31
Have you followed the advice from the jimbo7.com website 100%? I am sorry to say but wireless cards are possibly the hardest item of hardware most Linux users have to deal with, along with graphics cards. 
Go back to the Jimbo7 website and pay particular attention to the last few paragraphs? It sounds like the module is not being loaded at start up, but this is easily fixable.
Also you might want to check out the ndiswrapper home page.

---

