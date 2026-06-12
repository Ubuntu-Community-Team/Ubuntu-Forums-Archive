---
title: "Connect my phone to internet"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by freddi on 2008-03-09
Hi!
There are some other threads like this, but they doesn't have the answer I'm looking for.
I want to connect my Sony Ericsson W810i too internet going through my computer.
SE W810i -> Bluetooth -> My Ubuntu 7.10 computer -> Broadband -> Internet (WAP)

I found this app, but it doesn't support my phone :(
[http://gnubox.dnsalias.org/gnubox/](http://gnubox.dnsalias.org/gnubox/)

Thank you very much!

---

### Post by diablo75 on 2008-03-13
[http://ubuntuforums.org/archive/index.php/t-500566.html](http://ubuntuforums.org/archive/index.php/t-500566.html)

Essentially, you plug your phone in (make sure it's in data connection mode, and not memory card mode)... and type "wvdialconf" into a terminal window.  This will autodetect your phone, test it's capabilities, and create a skeleton configuration file for you to modify, located at /etc/wvdial.conf

After editing and saving the file, you just have to type "wvdial" to start the program.

I have a blog about this topic located here:

[http://davestechsupport.com/blog/2008/02/28/how-to-connect-linux-to-your-cellular-internet/](http://davestechsupport.com/blog/2008/02/28/how-to-connect-linux-to-your-cellular-internet/)

But I personally only use T-mobile.  Could you please look at this blog after you've successfully connected and let me know if I should make any edits or corrections to the portion regarding your carrier?

---

### Post by hunter_te on 2008-04-01
Here is how u do it..... works for both, fiesty and gutsy

1.Connect the mobile via USB cable.

2. Open terminal and type "sudo su" to become root.

3. It will ask for the root password, type in there.

4. Then Issue this command
Code:

wvdialconf /etc/wvdial.conf

Phone wud b detected as Modem

5. Then to Edit this file, open it in a Text Editor

Code:

gedit /etc/wvdial.conf

When we issued command in point 4, it showed the address of ur phone that in which USB port it has been connected. note it down from there.
"Modem = /dev/***"

6. When Text Editor opens the file, erase everything from there and Paste the following:
Code:

[Dialer Defaults]
Modem = /dev/ttyUSB0 # <------- Replace it with the reading you got
Phone = *99# #<-----Replace this with service provider number
Username = abc
Password = xyz
Baud = 230400
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Carrier Check = No

The mOdem has been configured successfully.

To dial the internet conenction type
Code:

wvdial

If everything goes fine it wud say that connected successfully.
Press Ctrl+C to disconnect.


If it doesnt work, then call up ur cellphone provider and ask them the number to dial to get internet working from a PC. They may even require u to have unique id and password.

GoodLuck

---

