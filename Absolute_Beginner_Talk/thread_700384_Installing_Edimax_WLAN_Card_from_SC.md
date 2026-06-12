---
title: "Installing Edimax WLAN Card from SC"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by burns863 on 2008-02-18
Hey Guys,

After a good few hours of searching through the forums and the rest of the net, I'm still not getting very far with the installation of my Edimax EW-7728ln 802.11n compatible PCI Adapter.  I really do think that my lack of Linux knowledge is the obvious answer, so I really need to get up to speed with things.

Firstly, I know that I can use ndiswrapper to use the Windows driver, but I want to avoid this if I can.  Seems that by doing it that was I'm not really going to learn anything about the Linux OS!  

So... I have downloaded the Linux Source Code from the Edimax website, and have tried several commands and step by step how to's but I'm really not getting anywhere.  While Im reading, I have the most basic of questions still unanswered in my head.  What are repositories and where are they found?  What is the 'sudo' command?  And what is 'apt-get'?

Attached is a screenshot of the contents of the .zip from the edimax website, I have expanded most folders.  I dont even understand what the folders are... for example I have a Web UI folder and what appears to be a driver folder?  I guess the WebUI is some sort of WLAN monitoring app?  Just to add... the screenshot is on my Mac, as I downloaded it here first due to the Linux machine now having internet access currently.

I would greately appreciate it if anyone could help me and get me going.  This is my final year project at Uni, and I want to learn as much as possible :)

Thanks guys!

Dan

---

### Post by knattlhuber on 2008-02-18
I'm not familiar with the WLAN card you want to install, but if the forums suggest that ndiswrapper is the best way, I would go with that. And don't worry, you'll still learn A LOT about Linux by doing so.
Compiling stuff from source is quite a task for a beginner, and if something goes wrong, you'll learn more about Linux than you ever wanted to know.. :)

As for your questions:
Repositories are collections of software projects maintained by the Ubuntu community. You can view the list of repositories under Applications > Add/Remove > Preferences or by typing[FONT="Courier New"] gedit /etc/apt/sources.list[/FONT] in the terminal.
The [FONT="Courier New"]sudo[/FONT] command is used to execute commands as 'super user' ('Administrator' under Windows and OSX).
The[FONT="Courier New"] apt-get[/FONT] command is used to manage packages (list/install/remove) on your system.

HTH a little bit.

---

### Post by burns863 on 2008-02-18
> **knattlhuber said:**
> I'm not familiar with the WLAN card you want to install, but if the forums suggest that ndiswrapper is the best way, I would go with that. And don't worry, you'll still learn A LOT about Linux by doing so.
Compiling stuff from source is quite a task for a beginner, and if something goes wrong, you'll learn more about Linux than you ever wanted to know.. :)

As for your questions:
Repositories are collections of software projects maintained by the Ubuntu community. You can view the list of repositories under Applications > Add/Remove > Preferences or by typing[FONT="Courier New"] gedit /etc/apt/sources.list[/FONT] in the terminal.
The [FONT="Courier New"]sudo[/FONT] command is used to execute commands as 'super user' ('Administrator' under Windows and OSX).
The[FONT="Courier New"] apt-get[/FONT] command is used to manage packages (list/install/remove) on your system.

HTH a little bit.

Thanks for your reply :)

Well with your answers I'm one step closer to understanding Linux :lolflag:  However, the reason that I was going with the Linux source code is that I gathered it is more efficient to do so this way, rather than using a driver not meant for Linux?  From what your saying though, maybe I should just use ndiswrapper?

I would really like some insight into the actual files in the screenshot I attached?  Are there any significant files in there that will help me understand things a bit more?

Another question just popped off the top of my head... Ubuntu, and Gutsy, what is Gutsy?  All I know is that I have Ubuntu 7.10.  Is this Gutsy?  Confused :confused:

Thanks again guys! :guitar:

Dan

---

### Post by knattlhuber on 2008-02-18
The files in that directory won't really help you to understand Linux better. It's the source code of the driver written in the programming language C (as can be seen by the file extension .c).
If I were a beginner, I would only compile a program from source code if I really really had to.
Installing the driver through ndiswrapper and getting the WPA encryption up and runing usually isn't a walk in the park either if you are an absolute newbie to Linux. You will still learn a lot about Linux in the process.

W.r.t your other question: Ubuntu uses animal names for the different linux versions. There was Dapper Drake, Edgy Eft, Festy Fawn, Gutsy Gibbon (which is the same as Ubuntu V7.10) etc. The next version (V8.0) is gonna be called Hardy Heron.

---

### Post by burns863 on 2008-02-19
> **knattlhuber said:**
> The files in that directory won't really help you to understand Linux better. It's the source code of the driver written in the programming language C (as can be seen by the file extension .c).
If I were a beginner, I would only compile a program from source code if I really really had to.
Installing the driver through ndiswrapper and getting the WPA encryption up and runing usually isn't a walk in the park either if you are an absolute newbie to Linux. You will still learn a lot about Linux in the process.

W.r.t your other question: Ubuntu uses animal names for the different linux versions. There was Dapper Drake, Edgy Eft, Festy Fawn, Gutsy Gibbon (which is the same as Ubuntu V7.10) etc. The next version (V8.0) is gonna be called Hardy Heron.

Ah.. well that explains the 'Gutsy' issue to me then :)

OK, I think I am going to go with ndiswrapper.  I realised that the source code was in C, as I have done a moderate amount of C programming at Uni.  I just presumed that drivers were usually written in C?

Hopefully I wont have to bother getting WPA up and running, as my project is focusing on media streaming and wont need encrypting with anything more than WEP.:)

---

