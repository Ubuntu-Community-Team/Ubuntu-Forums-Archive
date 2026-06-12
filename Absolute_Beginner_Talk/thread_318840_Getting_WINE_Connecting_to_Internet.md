---
title: "Getting WINE/ Connecting to Internet"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by Tellisk on 2006-12-14
I recently downloaded and installed Ubuntu, after perusing alternatives to Microsoft (which I've grown utterly fed up with).

Installation went smoothly, and it seems the next step is to download WINE. But I appear to be caught in a kind of catch-22. To get WINE, I have to be online. But I can't get online without installing my wireless network adapter (Linksys WUSB54G). And I can't install said adapter because the Setup file is an .exe. ](*,) 

The only thing I can think of is to lug my computer (it's pretty large, making this option undesirable) to a friend's house and connecting it via wired ethernet to download WINE.

Does anyone have any other suggestions? Or will this idea even work? How do most people get around this "issue"?

---

### Post by meng on 2006-12-14
You don't need the .exe file to install drivers in Linux. You may yet need to download a file, but you don't need wine and .exe for the purpose of getting your wireless card to work. If it's not already recognized by your system (which I'm not sure, but you seem to suggest it is not) then you should search the forums here for that make/model and follow the advice you find. If it is recognized by your system already (which is possible, since quite a few are recognized out of the box) then you need to configure it with ESSID and encryption key.

One common way of getting the wireless card installed is with ndiswrapper. If you require this method, you need the .inf file that constitutes the Windows driver, but again, you don't need WINE!!!

---

### Post by scrooge_74 on 2006-12-14
Check in the System>Admin>Network and see if you have a wireless card there, if there is something you may have it install already.

also from command line you can do ifconfig, your lan card should appear as eth0 and any wireless card should come as eth1 or ath0 it depends on the model

Wine is only for using windows programs. For your card you may only need Linux drivers or worse case scenario use ndiswrapper

Good Luck

---

### Post by Tellisk on 2006-12-14
Okay. I'll try that. I assumed I needed Wine because the software for the wireless adapter I've been using is designed for Windows XP. Thanks for the replies.

---

### Post by Sefrin on 2006-12-14
Do a search for "wireless," "wusb54g," and "ndiswrapper."

Some people have problems with ndiswrapper, some have problems without ndiswrapper but it's good to know just FYI.

Also, if you need the .sys and .inf files from the setup.exe just use the command "unzip" on the .exe, it works.  ;)

---

### Post by Tellisk on 2006-12-14
Thanks for the help so far.

I see my wireless card when I open System->Admin->Networking.

But I still can't connect. The computer wired is hooked up via WRT54G v3 router and Verizon DSL. Any ideas?

---

### Post by scrooge_74 on 2006-12-14
open a terminal window and type ifconfig to see what config it says about it.

Also probably you have to enable the card in the network admin, just to be sure also disable for this test any security from your router,  so you can rule out any problem from there.  

Sometimes you have to start the card up so linux knows it has to use it, also if you are using dhcp to give ip address (which is most likely) you have to tell your PC to use it, unless you assign static ip addresses

---

### Post by meng on 2006-12-15
So if you can see the wireless interface, you don't need to install drivers. You should be able to enable the connection, then specify the ESSID and WEP key.

---

