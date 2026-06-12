---
title: "Linux Connecting USB printer with IP?"
date: 2017-03-12
forum: Any Other OS
---

### Post by mehrunisa on 2017-03-12
Hi all,
I have android tablet with USB port,
I have connected thermal printer with this USB port,
Now I can print receipts easily from many playstore programs having USB printer option but one of my program requires network printer ... means I have to put IP address ... what should I write in the IP address for USB printer ... Do I have to forward USB port to Localhost ... Is there any way?
Thanks.

---

### Post by howefield on 2017-03-12
Thread moved to the "*Any Other OS*" forum.

---

### Post by Bucky Ball on 2017-03-12
Welcome. You need to find out the IP address of the printer. Generally, this is served from the DHCP server on your router, but for a printer, you should set a static IP so it doesn't change whenever the router or printer is rebooted (it may not, but it might). 

To find the current IP of the printer and to change the IP to a static one, check the printer manual. On my printer, you hold the 'Go' button down until the printer launches into action and prints a page of its network details. No idea what the procedure is to get the IP from yours.

Know little about Android, so little idea how you would check for a network printer on that. At a guess, go to 'Settings> Wifi', switch wifi on and tap the word 'wifi' and that should open to all available networks. See if the printer shows up there. Failing that, if you can find any other way to do a search for network devices, it may just find it (if the wifi on the printer is actually switched on, another consideration as this is not always the case by default, and it is seen by the router, if that is providing your home network, i.e. your phone connects through the router to communicate with the printer). 

You've given few details of your setup so bit hard to add much more. If you are using a LAN (a home network) with everything connected to a wireless router, then the printer will need to be seen by the router before anything else happens. This can be achieved by plugging it in to the router with an ethernet cable. Wireless might be a bit trickier to get going. Once the printer is recognised by the router, it is on your network and your phone will (should) pick it up. 

Hope that helps and good luck. :)

---

### Post by SeijiSensei on 2017-03-12
If the printer is connected via USB, there is no option to assign that an IP address.

You could set up a CUPS server on the machine then print to it from the app that needs network access.

---

### Post by mehrunisa on 2017-03-14
> **SeijiSensei said:**
> If the printer is connected via USB, there is no option to assign that an IP address.

You could set up a CUPS server on the machine then print to it from the app that needs network access.

You mean that I have to install cups server on android machine?


How can I turn this USB printer to IP printer ... inside android  ... by some application or by some tweaking.

---

### Post by coffeecat on 2017-03-14
Let me see if I&#8217;ve got this right, so that we can clarify for people trying to help you. You have a USB printer which itself has no networking capabilities, connected to an Android device and you want to see if the printer-Android device combination can be set up as a network printer? And this is because, as you state in your first post, one of your programs requires a network printer? Is this network-printer requiring program on your Android device or on another machine on your network running a different operating system?

Although you are welcome to ask your question in this section on Ubuntuforums (you originally posted in the Hardware section, which is for the Ubuntu family of operating systems) this is not the best place to seek help with Android related questions. Ubuntu is very different from Android and vice versa. You would be better off finding a suitable Android forum.

---

### Post by SeijiSensei on 2017-03-14
I thought you were trying to print from an Android device to a printer connected to a PC.

A quick search for "android print server" brings me here: [http://appcrawlr.com/android-apps/best-apps-print-server](http://appcrawlr.com/android-apps/best-apps-print-server)

---

