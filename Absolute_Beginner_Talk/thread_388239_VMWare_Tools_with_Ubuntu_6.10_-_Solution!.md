---
title: "VMWare Tools with Ubuntu 6.10 - Solution!"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by AaronD on 2007-03-19
Hello all - I have been having a heck of a time with VMWare Tools under VMWare Workstation 5.5.3 and loading Ubuntu 6.10 as a guest.  The included VMWare tools will allow you to run in 800x600 resolution but will not allow you to switch to 1024x768.  If you switch, the VM will not boot.  Also, the mouse driver isn't seemless (meaning you have to enter and exit the VM to get mouse control - Ctrl-Alt to get back out).

I finally found a solution last night that took some doing so I wanted to share in case anybody searches on this topic.

You can load the VMWare Tools from the latest VMWare Workstation 6 Beta (Build 39849) over top of the 5.5.3 Tools and so far everything has worked great.  I have my 1024x768 resolution and seamless mouse.

If anybody has any questions, let me know!  Thanks!

Aaron

---

### Post by hyper_ch on 2007-03-19
AaronD: Thx for that input :)

Another option is not running vmware workstation but vmware server. It's free available for download (although you first need to install a few additional packages).
With the server you can then create your own VMs :)

---

### Post by AaronD on 2007-03-19
Cool - Can you run the Server on XP?  Last time I checked (when VMWare still charged for GSX Server) you couldn't load it on XP.  It did a version check and wouldn't let you load it.  I will download the free server and check it out.  Thanks!

---

### Post by hyper_ch on 2007-03-19
Yes, you can run it on windows... however you must register to obtain serials...

[http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)

---

### Post by AaronD on 2007-03-19
Downloading now...  :)

---

### Post by AaronD on 2007-03-20
So, I tried VMWare Server 1.02.  Ubunutu went well and the VMWare Tools installed.  The video worked and you were able to change resolutions and run in 1024x768 without a lock up unlike Workstation 5.5.3.

But, the mouse was not seamless.  I had to load the Workstation 6 VMWare Tools to get this to work.  Again, I have to recommend the latest VMWare Tools.

Thanks for all the information, I like VMWare Server and I'm glad you can run in on XP!

Aaron

---

### Post by hyper_ch on 2007-03-20
The mouse runs fine for me in VmWare :) good that it works out for you :)

Btw, what I also recommend is when you setup your first basic windows.. I mean just after the install (before having altered anything) you could make a copy of that VM... so in the case you want to re-setup the windows again a later time you can just use that backup that you made :)

---

### Post by in_flu_ence on 2007-03-20
Remember to install the vmtools after you have installed windows in your vm so that your mouse can go seamless between host and vm.

Good luck

---

### Post by AaronD on 2007-03-20
Thank you again to everyone!!

I have been using VMWare for years but this is my first plunge into Linux and I am very happy to get over this first "hurdle".

Looking forward to learning Ubuntu!

---

