---
title: "access to printer connected to XP machine"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by paydaydaddy on 2007-02-17
:guitar: Noob to Ubuntu. I have been using it for several weeks now and have things running pretty smooth. Been taking baby steps. I have a HP 2210 PSC printer connected to my XP machine. The Linux machine sees the XP machine on the network, but the XP machine does not see the Linux machine. I don't have a problem with that as long as I can get the printer to work. I have done some research and know that the printer is supported for Linux, but have not downloaded drivers yet. I just want to know if I will be able to make this work before investing a lot of time trying to make it work. Would I be better off getting a print server or a new printer with built in networking cabability. Opinions and advice welcome.

---

### Post by Tilex on 2007-02-17
Hey paydaydaddy, nice seeing you again! :P
The XP machine should see you if you have a directory shared.  If you want to share a directory on the network (off your linux box) right-click on the directory, go in the properties, and click on the "sharing" tab, which will start the sharing service.  Once something is shared from your linux box, you should see it from Windows.

As for the printer connected to that XP machine, it should work fine.  When you want to add a new printer, in Settings -> Printer -> Add printer, click on "SMB Shared Printer", and it will get you to the step where you can scan the network and see the printer.  It is like if the printer were connected to a network hub, but the only difference is that you have to pass through the XP machine first before getting to the printer.  So if the scan returns no results, you can manually intervene and enter the workgroup, the server (the _network_ IP address of your XP machine like 192.168.0.103), and the name of the printer.

Don't worry, it should be quite easy...

---

### Post by paydaydaddy on 2007-02-17
What is a directory and how do I access one?

---

### Post by paydaydaddy on 2007-02-17
> **Tilex said:**
> Hey paydaydaddy, nice seeing you again! :P
The XP machine should see you if you have a directory shared.  If you want to share a directory on the network (off your linux box) right-click on the directory, go in the properties, and click on the "sharing" tab, which will start the sharing service.  Once something is shared from your linux box, you should see it from Windows.

As for the printer connected to that XP machine, it should work fine.  When you want to add a new printer, in Settings -> Printer -> Add printer, click on "SMB Shared Printer", and it will get you to the step where you can scan the network and see the printer.  It is like if the printer were connected to a network hub, but the only difference is that you have to pass through the XP machine first before getting to the printer.  So if the scan returns no results, you can manually intervene and enter the workgroup, the server (the _network_ IP address of your XP machine like 192.168.0.103), and the name of the printer.

Don't worry, it should be quite easy...

When you want to add a new printer, in Settings -> Printer -> Add printer, click on "SMB Shared Printer", and it will get you to the step where you can scan the network and see the printer.

Is this sentence refering to Ubuntu? I cannot find "Settings".

---

### Post by gh0st on 2007-02-17
Hi,

It sounds as though you just need to share the printer in Windows XP and Ubuntu will work fine as a client for it if you can already see the XP machine.

It's been a while since I used Windows but here are a few instructions, just keep in mind it's been a while for me :) 

1. In Windows, Go to Control Panel
2 Then go to printers (not sure the exact name of the control panel entry, it has a picture of a printer)
3. You should see your HP printer in the window so right-click on the icon
4. There should be an entry on the menu called "sharing" or "share this printer" something like that. That will launch a wizard and it should be straightforward from there.

Once Windows is sharing the printer you should be able to see it from Ubuntu. You don't need to get into setting up Samba or anything unless you wanted to share a printer plugged into your Linux machine with XP.

Hope that helps, my Windows instructions are a bit vague I know but I'm struggling to remember. If you need any more help or you get stuck let me know and I'll have a look on an old Windows machine and get you some proper detailed instructions :) 

Good luck.

---

### Post by paydaydaddy on 2007-02-17
I will check the settings on the XP machine but I am pretty sure that it is already set up to be shared. I can print from another XP machine on the same network.

---

### Post by gh0st on 2007-02-17
> **paydaydaddy said:**
> I will check the settings on the XP machine but I am pretty sure that it is already set up to be shared. I can print from another XP machine on the same network.

Ahh right it sounds like the printer is already shared in XP then, if you can print to it from other Windows PC's then it must be. In which case you just need to connect to it with Ubuntu.

If you go to "Places" on the main Ubuntu menu bar then choose "Network Servers". You should get a list of the PC's on the network. If you double click the XP machine with the shared printer you should get a list of the shared resources on that machine. Then I think you should see the printer and you can just double click it and it will ask you if you want to add it.

I'm not 100% sure on that so give it a go and let me know how you get on. If it doesn't work and you are confident that you're Ubuntu PC can definitely see your XP machine on the network you could try adding a network printer in Ubuntu. DO this by going to "System" / "Administration" / "Printing" and then choosing new printer, network printer and "Windows SMB Printer". You can then add the server and share name of the printer and connect to it.

See how you get on and let me know.

Good luck :)

---

### Post by paydaydaddy on 2007-02-17
> **gh0st said:**
> Ahh right it sounds like the printer is already shared in XP then, if you can print to it from other Windows PC's then it must be. In which case you just need to connect to it with Ubuntu.

If you go to "Places" on the main Ubuntu menu bar then choose "Network Servers". You should get a list of the PC's on the network. If you double click the XP machine with the shared printer you should get a list of the shared resources on that machine. Then I think you should see the printer and you can just double click it and it will ask you if you want to add it.

I'm not 100% sure on that so give it a go and let me know how you get on. If it doesn't work and you are confident that you're Ubuntu PC can definitely see your XP machine on the network you could try adding a network printer in Ubuntu. DO this by going to "System" / "Administration" / "Printing" and then choosing new printer, network printer and "Windows SMB Printer". You can then add the server and share name of the printer and connect to it.

See how you get on and let me know.

Good luck :)

So far no luck. It must be something simple that I am missing in the setup. I have been working on this for about 5 hrs.

---

### Post by Maestro23 on 2007-02-17
> **paydaydaddy said:**
> So far no luck. It must be something simple that I am missing in the setup. I have been working on this for about 5 hrs.

Step away from the keyboard, get you a good stiff drink, and take a breather. :)

---

### Post by gh0st on 2007-02-17
> **Maestro23 said:**
> Step away from the keyboard, get you a good stiff drink, and take a breather. :)

Yeah this is good advice :)

I've done this loads of times spent hours going round in circles trying to fix something until I'm really worked up and getting nowhere. Have an hour break or whatever and come back and fix it in 5 mins. It's always the way.

Ok so when you do get back from your break try the following. Find out the network (or host) name of your Windows PC with the printer attached. If you don't know this you can get it by right-clicking on "My Computer" on the menu and choosing "properties" at the bottom of the menu. Then go to the tab that says "Machine Name" or "Network Name" I can't remember exactly which. Anyway you will see in there somewhere it will say "machine name" or something similar.

Make a not of the name and then try to connect to it from your Ubuntu machine by going to "Places" - "Connect to server". Choose "Windows Share" from the select box and enter the network name you made a note of earlier in the box marked server. Press connect and see what happens, if the network is setup properly and the machines can see each other fine then you should get some information in a windows of the shared services on the Windows box. One of which should be the printer.

Do you see anything?? Let me know. If you did then we can set the printer up easily, if not then your network might need some reconfiguration. Fingers crossed it wont come to that :)

---

### Post by paydaydaddy on 2007-02-17
currently the ubuntu machine sees the windows machine but the windows machine does not see the ubuntu machine. The ubuntu machane sees only shared documents and backed up files, not the printer.

---

### Post by gh0st on 2007-02-17
> **paydaydaddy said:**
> currently the ubuntu machine sees the windows machine but the windows machine does not see the ubuntu machine. The ubuntu machane sees only shared documents and backed up files, not the printer.

Right ok, so I know I've said this before but it really sounds like the printer isn't shared on the Windows machine. If you can read your shared folders and stuff on the Ubuntu machine then you should see any shared printers as well :-k

Here's the info on printer sharing I found on the Microsoft website, ignore all the rubbish and scroll down to the bit where it says "Share and Share Alike" (slightly ironic title I thought for Microsoft :) ):

[http://www.microsoft.com/windowsxp/using/networking/expert/honeycutt_july2.mspx](http://www.microsoft.com/windowsxp/using/networking/expert/honeycutt_july2.mspx)

Just check for me that the printer is set up and shared with a network name as it says in the article. It should be something like //mycomputer/printer

If it is setup properly and you have the network share name you can just use that to add the printer in Ubuntu.

1. On the main menu at the top go to "System" - "Administration" - "Printing" to get up the printers on your Ubuntu machine.

2. Double Click "New Printer"

3. Switch printer type radio button to "Network Printer" and change the box that says CUPS Printer to "Windows Printer (SMB)"

4. Put the network name of your Windows machine in the box marked "Host"

5. Put the share name of the printer in the box marked "Printer"

6. If you have security setup on your shared printer (this isn't the norm) then you may need to enter a username and password in the 2 boxes below, obviously this should be an account on your windows machine.

7. On the next screen select the driver for your printer from the options. There's bound to be one if it's a HP printer.

8. On the last screen you can change the name of the printer on you Ubuntu box if you want. You can also enter a description and location if you really want but there's no need.

That should be it. Provided the printer is turned on and shared correctly from the Windows machine it should work.

Another thing I noticed while playing with the printer settings tool was on the "Global Settings" menu in the main window there is an option that says "Detect LAN printers". It wasn't ticked on my machine so tick it if it's blank. I reckon that could be pretty important.

Hopefully all this info will help you in some way. I don't know what else to suggest if you can definitely connect to the windows box over the network and the printer is shared properly it should just work. Not much consolation I'm sure. You might wanna make sure the printer is turned on, I dunno if that makes a difference to whether it appears in the shares.

Good luck, hope that is of use.

---

### Post by paydaydaddy on 2007-02-17
I finally got it working, but only after really breaking things good. For a while I could no longer find other computers on the network. Then I figured out how to straighten out the network settings. A printer does not show up in the LAN but by carefully paying attention to all settings and trying several interpretations of what was being asked for, I finally entered the magic combination and I can now print from Ubuntu. Thanks to all who chimed in with helpful hints.

---

### Post by gh0st on 2007-02-18
Good news glad to hear you got it sorted. I don't know why it was so tricky on your network though, I print from my Ubuntu machine through a printer attached to an XP machine next door and shared in the normal way. It just worked first time.

Maybe I was lucky and found the right combination first time who knows. On the upside you've had a crash course in Ubuntu networking and you'll fly through it next time.

Nice work in figuring it out. I know who to ask when my network printer doesn't work now :) ;)

---

