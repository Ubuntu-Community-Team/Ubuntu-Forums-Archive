---
title: "Connecting Windows XP to internet through Ubuntu 6.06"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by TotalRetard on 2007-01-31
Hi!

I've read these forums over and over again, but I always fail somewhere. 

The title says it all: I need to connect my Windows machine to the internet through the Ubuntu 6.06 machine. The computers are connected as follows:

Windows Machine -> Ubuntu Machine -> Cable Modem -> Teh Internets

I can get the Ubuntu machine to the internet easily, but I need step-by-step info on how to share the internet connection from the Ubuntu machine, and how to make Windows connect through it.

I am too puzzled, I've found alot of articles all saying different stuff etc.
I tried installing Firestarter, but the command "sudo apt-get install firestarter" fails, saying that there is no such package as firestarter. :confused: 

So please help, any links to good easy-to-understand step-by-step tutorials, or any posts here are appreciated. (I would hate to go installing Windows on the other machine to get it work, I don't want to give up on Linux).

---

### Post by TotalRetard on 2007-01-31
Anyone? :(

---

### Post by irish_flu on 2007-01-31
Is the Windows box hooked up directly to an extra ethernet port in your Ubuntu box?

---

### Post by irish_flu on 2007-01-31
OK, a few more thoughts.

You might not be able to find the "firestarter" package because you don't have the "Universe" repository enabled on your machine.



Let's do this through Synaptic Package Manager (under the System ---> Administration menu in Gnome) just to make it simpler.

One caveat: I have version 6.10 (Edgy), so holler if you see things differently from what I see.  These instructions might need modified for Dapper.  :)

Open up Synaptic, and enter your password.  Click on the "Settings" menu, then click "Repositories".

Under the first tab, make sure that "Community Maintained Open Source Software (Universe)" is checked.

Close that, then in Synaptic click "search" and search for "firestarter".

---

### Post by TotalRetard on 2007-01-31
Yep, the Windows box is directly hooked on the Ubuntu box.

I'll see what happens with firestarter now.

---

### Post by TotalRetard on 2007-01-31
So, I got Firestarter downloaded, but...

What am I supposed to do now? Sorry, I am a total noob :D

---

### Post by xopher on 2007-01-31
Open Firestarter, System -> Administration (in edgy at least), or gksudo firestarter in terminal.

Preferences > Firewall: Network settings: [x] Enable Internet Connection Sharing [x] Activate DHCP for the local network

That should do it, then just set the windows machine to use dhcp, and it'll automatically find an IP and connect to teh internet.

---

### Post by Charles2008 on 2008-01-06
I just tried the above method and it failed.

The error was failed to start the firewall an unknown error occurred.  Please check your network settings and make sure your internet connection is active.

I had to use ndiswrapper to configure my Linksys WUSB11v2.6 wireless access point.

Please advise,

Thanks,

Charles

---

