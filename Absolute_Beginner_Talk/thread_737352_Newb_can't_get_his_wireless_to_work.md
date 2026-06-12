---
title: "Newb can't get his wireless to work"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by benjaminitz on 2008-03-27
I just installed Ubuntu 7.10, and I'm not picking up any wireless connections. I tried using the troubleshooting guide and got stuck on:

[I]
Check device is on

   1.   Many wireless network devices can be turned on or off. Check to see if the device is turned on by opening a Terminal (Applications &#8594; Accessories &#8594; Terminal) and type the command: sudo lshw -C network.
   2.  If it is turned on then see the section called “Check for a connection to the router”.
[/I]


My wireless card is recognized, and it has a driver. However, it's listed as disabled. What does that mean? I'm a little annoyed that the troubleshooter only says what to do if it's turned on, but not if it's disabled. 

Any help would be appreciated.

---

### Post by zanjabeel5 on 2008-03-27
right click on the wireless icon on system tray then choose  "connection information" what driver does it show ?

have you tried "restricted driver manager" ?

---

### Post by benjaminitz on 2008-03-27
I can't click on Network Connections. The driver isn't listed under restricted drivers. I only know it's there because a driver is listed when I run "sudo lshw -C network"

---

### Post by wolfen69 on 2008-03-27
did you go to system>admin>network  ?

---

### Post by benjaminitz on 2008-03-27
ok, I'm in Network Settings. What would you like to know?

---

### Post by benjaminitz on 2008-03-29
Ok, sorry about my previous complete newbery. Three days and way too many hours on the computer later, I think I have a better idea of what's going on. So, first I tried to install linux compatible drivers for my card. There were none. Next, I tried to install and use ndiswrapper, but that didn't work. It seems I ran into the same problem a lot of people have, the problem of the recurring "ndiswrapper is not installed" message after I install ndiswrapper. 

So, after sifting through forums and following suggested protocols to no avail, I decided it might just be more cost effective (time wise) to get a linux compatible wireless card. So, tomorrow I'll be putting a Orinoco 11a/b/g wireless card in my machine, which is, I'm told, very much supported by the default drivers in Ubuntu 7.10. 

My question, then, is this: After I have a wireless card that definitely works, what other problems may/will I run into trying to connect to the internet?

---

### Post by heyho on 2008-03-30
I thinks that your final solution is probably the best - I have been messing about with ndiswrapper and windows drivers with moderate success, but I don't really relish doing so with every fresh install - which seems to throw different problems every time.

Supported hardware every time from now on.:)

---

### Post by benjaminitz on 2008-03-30
O.k. I installed the new wireless card, (which I got for half off 'cause the box was damaged. Score!) and everything's working perfectly. No more wireless problems. So, if you're one of the many of us who just can't get ndiswrapper to work, I highly suggest this wireless card. Thanks all.

---

