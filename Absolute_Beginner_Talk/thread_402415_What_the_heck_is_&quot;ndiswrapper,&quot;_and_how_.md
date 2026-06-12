---
title: "What the heck is &quot;ndiswrapper,&quot; and how do I use it?"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by ScooterDMan on 2007-04-05
Just installed Feisty Fawn on Sony Vaio laptop. I have a LInksys WPC11 ver. 3 card. It is not recognized by the system.

In another thread on this message board, someone suggested installing the Windows drivers for card with ndiswrapper.

I don't know what that is. Can someone explain in simple terms how I go about accomplishing this task?

---

### Post by drakazz on 2007-04-05
> **ScooterDMan said:**
> Just installed Feisty Fawn on Sony Vaio laptop. I have a LInksys WPC11 ver. 3 card. It is not recognized by the system.

In another thread on this message board, someone suggested installing the Windows drivers for card with ndiswrapper.

I don't know what that is. Can someone explain in simple terms how I go about accomplishing this task?

[http://www.ubuntuforums.org/showthread.php?t=9454](http://www.ubuntuforums.org/showthread.php?t=9454)
[http://www.google.com/search?q=ndiswrapper+using](http://www.google.com/search?q=ndiswrapper+using)

---

### Post by Happy_Man on 2007-04-05
Ndiswrapper is a program for Linux that allows the operating system to use native Windows wireless card drivers. There are numerous tutorials on how to use Ndiswrapper, use these to help you get started: 

[http://ubuntuforums.org/showthread.php?t=306421&highlight=LInksys+WPC11+ver.+3+card](http://ubuntuforums.org/showthread.php?t=306421&highlight=LInksys+WPC11+ver.+3+card)
[http://ubuntuforums.org/showthread.php?t=51490&highlight=LInksys+WPC11+ver.+3+card](http://ubuntuforums.org/showthread.php?t=51490&highlight=LInksys+WPC11+ver.+3+card)

hope this helps?

---

### Post by ScooterDMan on 2007-04-05
Thanks for the help, guys, but I need a bit more assistance.

From what I understand, in order to make this work, I have to download ndiswrapper, and point it to the .inf file within the Windows driver folder for my network card.

Problem is, when I try to install ndiswrapper (sudo apt-get install ndiswrapper-utils-1.8) it returns with this:

> Couldn't find package ndiswrapper-utils-1.8

In another thread, someone suggested making sure all the Repositories within Synaptics were checked, and I did that, but still no dice.

Any ideas?

And, is there a wireless card I can buy at Circuit City/Best Buy that I can just plug in and use without doing all this crazy stuff?

---

### Post by Maestro23 on 2007-04-05
What do you get with:

> apt-cache search ndiswrapper-util

If your Feisty repo's are correct, you should see version 1.9

---

### Post by ScooterDMan on 2007-04-05
Thanks for the quick response. I get the following:

> ndiswrapper-utils-1.9 - Userspace utilities for the ndiswrapper linux kernel module

---

### Post by ScooterDMan on 2007-04-05
So what do I do now?

---

### Post by Maestro23 on 2007-04-05
> **ScooterDMan said:**
> So what do I do now?

Follow your guide and use ver 1.9 where is says 1.8

Also there is a graphical frontend for ndiswrapper (ndisgtk) in the repo's. I saw that mentioned in one of the links someone provided for you.

---

### Post by ScooterDMan on 2007-04-05
OK. Thanks. When you say there is a graphical frontend (ndisgtk) in the repo's, what do you mean?

I assume that this program provides a GUI based way for carrying this stuff out, right?

How would I go about installing that program?

---

### Post by ScooterDMan on 2007-04-05
Nevermind. I see what you are talking about and the instructions are clear. Thanks again.

---

### Post by Maestro23 on 2007-04-05
> **ScooterDMan said:**
> OK. Thanks. When you say there is a graphical frontend (ndisgtk) in the repo's, what do you mean?

I assume that this program provides a GUI based way for carrying this stuff out, right?

How would I go about installing that program?

> sudo aptitude install ndisgtk

*Never used this myself, just went back and read the links that have been provided for you.  If you look it up in Synatpic(GUI), it will explain what it is.  Can also install from there as well.

---

### Post by ScooterDMan on 2007-04-06
OK, so I got the drivers installed. When I plug the wireless card in, it comes up under Network Settings.

I unplug the ethernet cord, I check the wireless connection button, I go to Properties and choose my wireless network (which by default is named linksys and is not password protected).

But, nothing. No Internet. It gives me a signal strength, but no connection....

---

