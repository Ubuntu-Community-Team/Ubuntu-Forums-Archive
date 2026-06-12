---
title: "Bluetooth messed up"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by DonBucknall on 2007-07-25
Hello,

I was trying to get this bluetooth thing* to work and tried what I could find, one of the things I found was this:

> I simply removed all bluetooth/bluez and obex packages from my system using symantic.

Then I deleted any bluetooth stuff from /etc/init.d and /etc/default.

Then using this guide, I set up bluetooth again and it all works properly.


Then I follwed the guide he mentioned [Guide!]("https://help.ubuntu.com/community/BluetoothSetup").

It says
> Open up a terminal window, and install the requisite packages and their dependencies:

  sudo apt-get install bluez-utils
  

Then, connect your Bluetooth device if you are using one. Restart the Bluetooth services by doing:

  sudo /etc/init.d/bluez-utils restart (On some machines it may be sudo /etc/init.d/bluetooth restart)
  

But the bluetooth files didn't come back so I get the error

> sudo: /etc/init.d/bluetooth: command not found

Can anyone help me?

It might have been stupid what I've done but I just started using ubuntu a few days ago!! I used it last year but support for what I wanted wasn't enough but that is totally different now!! Microsoft lost another customer and ubuntu linux got a new one :D

Thanks,

Don


* Bluetooth thing is a little adapter where you can plug a normal speaker/headphone jack into so you can use it via bluetooth.

---

### Post by timothyM on 2007-07-25
Hello,

coincidentally I just did exactly the same as you, and found myself without a /etc/init.d/bluetooth.

This file is provided by the package bluez-utils but I found that just reinstalling it, or reconfiguring it did not recreate the file.

To get it to recreate the file, open synaptic (System -> Admin -> Synaptic Package Manager) and search for bluez-utils. Once you have  found that right click on it and select "Mark for complete removal". After you have done this, click apply on the toolbar.

Now after fully removing it, use synaptic to install bluez-utils, and it will recreate /etc/init.d/bluetooth.

Now I have my file back, but I still can't get my bluetooth working, I'll post back here when/if I do!

Timothy

---

### Post by DonBucknall on 2007-07-25
Thanks for you awnser that worked for me.

I also haven't got the audio thing working, i tried the guide, but didn't get me further..

If I come across something I'll post it here. 

Thanks for your help.

Don

---

