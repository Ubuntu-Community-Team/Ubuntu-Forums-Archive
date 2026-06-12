---
title: "Using ndiswrapper to install drivers.... help :("
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by Network Nurd on 2006-06-16
I've tried to get help with this in multiple forums.  I know there is an easy solution - I just cannot find it no matter how many places I look.

"I'm trying to install a driver with ndiswrapper for my wireless usb network adapter. I put the driver on my desktop - go into the terminal and type:

sudo ndiswrapper -i ZD1211U.inf

It in turn replies

coulnd't copy ZD1211U.inf at /usr/sbin/ndiswrapper line 135

I am assuming I have to put the drivers folder path before the actuall driver name. I've searched for the driver folder without success. Can someone point me in the right direction?

Thanks."

---

### Post by Mikeynewbie on 2006-06-17
This may not help but you could try to install the driver with the GUI for ndiswrapper it is called ndisgtk.  Open it and you can install the inf file from it.  When I used breezy i tried ndiswrapper but it wasn't until I go t the GUI ndisgtk that I got it working.  However if you are using Ubuntu Dapper I have read that Ndis does not work or something.  This could be incorrect, you never know.  See if that helps.

---

