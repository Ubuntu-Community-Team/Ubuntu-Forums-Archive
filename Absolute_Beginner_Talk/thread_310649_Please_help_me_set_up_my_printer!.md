---
title: "Please help me set up my printer!"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by Anoobiz on 2006-12-01
can sum one please help me setup my printer im using 6.06 lts and i need 2 know how 2 do the setup on the commandline :(

---

### Post by Anoobiz on 2006-12-01
sorry guys i forgot 2 mention that i need 2 share it over the network with my other ubuntu pc aswel and i need 2 detect it on that system :(

---

### Post by echo $USER on 2006-12-01
Who manufactured the printer?

---

### Post by wpshooter on 2006-12-01
Aboobiz:

All I can say is good luck with this.  I have given up on this until the programmer finally decide to work on and finish this part of this O/S.  You are going to find that if you can get this to work at all, it is going to be an effort paramount to re-inventing the wheel.  As I am sure you are probably aware this type of printer sharing on a M/S windows network can be accomplished with just a few clicks of the mouse on a very intuitive GUI in probably less than five minutes.  I will say that you will be lucky if you can figure out how to get this to work in five hours or maybe even five days.

But good luck in your effort.  Maybe if you figure it out, you can publish the results so the rest of the Ubuntu/Linux world can know how to do it.

---

### Post by Anoobiz on 2006-12-01
im sure i can make this work and im using a canon s200 sofar ive tried cups and the ubuntu serverguide i do have a little understanding on the sharing now but the only problem remains the setup

---

### Post by Henry Rayker on 2006-12-01
wpshooter, please don't spread this kind of foolishness. Setting up printers may be difficult, but it's not always THAT difficult. I have a printer hooked up to one Ubuntu machine sharing to a Windows machine and a laptop that dual boots Windows and Ubuntu.

The only time it is terribly difficult is when the printer doesn't have a driver. In that case, the problem lies with the company who produced your printer, not with the OS. Learn to place blame where it belongs.

Anoobiz, does the printer work from the machine that it is connected to?

If the printer will work under Ubuntu, then [try this guide]("http://occy.net/printing"). Remember to back up the first file (on the computer attached to the printer). The second file, try creating the client.conf file, if you don't have it.

---

### Post by Anoobiz on 2006-12-01
its detected on usb but now how do i set that up i had the same problem with my usbmodem phone but i figured out that it conected 2 ttyACM0 but isnt my printer suposed 2 be on a ttyS anyway thats why im lost and it does pickup when i use lsusb

---

### Post by Henry Rayker on 2006-12-01
If it detects the printer, have you tried the printer manager? It's in System/Administration/Printers, I believe. Open that, double-click the "new printer" icon and it will ask the manufacturer and ask you to select the proper drivers. See if you can even get it to print from the USB connected machine this way before trying to deal with networking.

---

### Post by Anoobiz on 2006-12-01
ok so now i have a test page but its unreadable im guessing i used the wrong module or cud it have something to do wit 'GS'?

---

### Post by Anoobiz on 2006-12-01
is there a setting missing somewhere or cud i have done something wrong and thanks 4 the guide i think i may be able to share it on the lan just one more thing do i have 2 setup access 4 the printer in the hosts.allow file aswell

---

### Post by wpshooter on 2006-12-01
> **Henry Rayker said:**
> wpshooter, please don't spread this kind of foolishness. Setting up printers may be difficult, but it's not always THAT difficult. I have a printer hooked up to one Ubuntu machine sharing to a Windows machine and a laptop that dual boots Windows and Ubuntu.

The only time it is terribly difficult is when the printer doesn't have a driver. In that case, the problem lies with the company who produced your printer, not with the OS. Learn to place blame where it belongs.

Anoobiz, does the printer work from the machine that it is connected to?

If the printer will work under Ubuntu, then [try this guide]("http://occy.net/printing"). Remember to back up the first file (on the computer attached to the printer). The second file, try creating the client.conf file, if you don't have it.

I don't think there is anything foolish about me stating what most Ubuntu/Linux users probably already know, i.e. that compared to setting up printer sharing on a M/S windows network, trying to setup what the poster is trying to do is extremely difficult, at best.  

I have done plenty of printer sharing on M/S windows networks and it is VERY easy as compared to the difficulty he is having setting this up.  

I know, because I recently attempted to do the same thing he is doing, i.e. share a printer hooked to a Ubuntu box with the other Ubuntu boxes on my network and no one on this forum or on Linux questions forum could give me proper instructions for accomplishing this and my printer is a fairly common model HP and yes it does have a driver and it still could not be made to be shared.

But if he has the time to spend on trying to get this to work, thats great.

---

### Post by STREETURCHINE on 2006-12-01
i actually agree with wpshooter i have been trying to set up a printer now for a month or so it is a hp deskjet f380,i have made many post to get help but to no avail,
i have followed the steps and tutorials in the forum here but i still have no printer in linux,
it is frustrating, and the only reason i have to keep windows on my laptop

---

### Post by Sef on 2006-12-01
> im using a canon s200

Sorry to tell you, but under [LinuxPrinting]("http://linuxprinting.org/show_printer.cgi?recnum=Canon-S200"), it says that your printer is a paperweight.   Canons and Lexmarks are often paperweights; while HP and Epson often work well.

For a printer that will work with Linux, check out LP's [Suggested Printers]("http://linuxprinting.org/suggested.html").

---

