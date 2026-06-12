---
title: "USB Wi-Fi Connection Problem"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by kevCast on 2007-10-20
Hello. I'm having a problem installing Gutsy on a friends PC. He's using a USB Wi-Fi connector to connect to his router, and I have no idea how to get it set-up. It doesn't seem that Gutsy is recognizing it in the networking tools. It's an Encore 802.11 g LAN USB adapter. 

[http://www.encore-usa.com/product_download.php?region=us&bid=3&pgid=81_4&pid=293](http://www.encore-usa.com/product_download.php?region=us&bid=3&pgid=81_4&pid=293)

Any help is appreciated, thank you.

*Edit: Just noticed the source code is provided.*

---

### Post by Espreon on 2007-10-20
Find the Windows driver (its an .inf and a .sys file). (Look at the company's site for it)

Enter this in a terminal:

```

sudo apt-get install ndisgtk ndiswrapper ndiswrapper-utils-1.9

```

Then goto: System>Administration>Windows Wireless Drivers

Then drag and drop the .inf file on the empty space.

Then enter this in a terminal:

```

sudo modprobe ndiswrapper

```

Enjoy!

If it still does not work than IDK.

---

### Post by Pioneer5000 on 2007-10-20
If the above doesn't work you might want to try this.

I was just having problems with this but not with a USB wifi thing. What i did was i connected my laptop to the net using a wired connection (ethernet) and then i went system --> Administration --> Restricted Drivers and then you try to update the drivers for the device and then reboot. It should be working now if not make sure that the connections icon in the top right of your screen has been set to wireless connection the one you want. If still not working then im sorry i dont know what to do.

Good luck.

---

