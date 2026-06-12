---
title: "[SOLVED] Dadgum IT !! Gutsy is blind,,,"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by Romin-1 on 2007-11-29
Here's my setup:

PC- Vista,,,Laptop, dual boot XP/Fiesty,,,Stand alone, Gutsy.

All are hard-wired into a DSL router/modem as is a purposely bought HP Printer.

The printer works fine with all BUT Gutsy.

All repos are installed, cups, HPlibs and so forth, yet this Abdominal Primate tells me "Printer not found, Make sure that the printer is plugged in and connected".

Well sir, it is plugged in, turned on and connected.

Have I missed something down the line or is Gutsy just being cantankerous?

I even tried plugging it directly into the PC with an USB cable, same results.

After three days of hair-pullin' and cussin I am here for any help you fine people can suggest.

Many thanks,

Jon  :confused:

---

### Post by llamakc on 2007-11-29
Try installing it from the CUPS web interface on your computer.

Open a browser to [http://localhost:631](http://localhost:631)

You do know the printer's IP, correct?

---

### Post by Romin-1 on 2007-11-29
Thanks for the reply IIamakc, 

No, I don't know the printers' IP. How does one find this info please?

BTW; The three PCs are not networked.

 Thanks again,

Jon

---

### Post by llamakc on 2007-11-29
I thought you said the printer was connected to the router?

---

### Post by cmnorton on 2007-11-29
If this is cabled into a router, this is a network printer. I don't know about network printers getting their ip addresses from dhcp. You'll need to know what range of addresses your router will serve (192.168.1.100 to 192.168.1.150); pick a very high address, and statically set that address in your HP printer. Or, if you router will let you reserve a permanent DHCP address, do that.

---

### Post by Romin-1 on 2007-11-29
What I meant was that they are connected to the internet through the router but not to each other. No file sharing or anything. In other words, no home network.

The HP 6300 Series comes with a ethernet port and a usb port. I have it connected to the router through ethernet and the Laptop and Vista machines recognize it but Gutsy does not

Will now look in the router, although two different PCs with different OSs can print, and see what I can find.

Thanks guys,

Jon

---

### Post by Romin-1 on 2007-11-29
I'm stuck on localhost:631 where it is demanding a user name and password. I entered my username and P-word a dozen times and got exactly nowhere! What gives?

Jon

---

### Post by llamakc on 2007-11-29
Did you determine the IP of the printer yet? If you have that you can use the Gnome printer applet also.

---

### Post by Romin-1 on 2007-11-29
Yep, I got the IP addy and and still no joy anywhere. I'm stuck in Cups 631 because it won't accept my password.

As an afterthought; is there some reason, or missing prog in Gutsy, that prevents itself from recognizing a piece of hardware? Not only through Ethernet but USB as well? Reason I ask is I had absolutely no trouble with the printer in Dapper or Feisty.

Jon

---

### Post by Romin-1 on 2007-11-29
Got it working, finally!!

What I did may not work for everybody in this situation, but here goes: Unplugged the machine from the modem/router, rebooted then I attached the printer using the USB2 cable. Opened the HP Toolbox and set it up. Now it's working. During another reboot I switched the cables back and now it sees the printer as connected through the router.

Now to find something else to vex me. HA!

Thanks for all the help guys,

Jon

---

