---
title: "Wireless and linux"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by Ca$h on 2006-04-08
Can i get my d-link wireless card to work with ubuntu? (i havent installed ubuntu, yet)

---

### Post by audax321 on 2006-04-08
You need to post the model number (as well as revision number, if applicable) before anyone can tell you if it will work. Some do, some don't. You could try downloading the Ubuntu LiveCD and see if you can get it working in there. The LiveCD won't install anything to the hard drive, it runs straight from the CD and memory.

---

### Post by Ca$h on 2006-04-08
Dlink Desktop adapter
dwl-g520 Version B

Edit: It works!!! :) (i am on the live cd)

---

### Post by audax321 on 2006-04-08
It looks like it should work. I checked the compatibility for the madwifi driver ([http://madwifi.org/wiki/Compatibility#DWLG520](http://madwifi.org/wiki/Compatibility#DWLG520)) and it says that the following should work:

```

Hardware	Firmware	Status
A1                 2.23              Works
B2                 3.1.6             Works
B3                 4.10              Works
B3                 4.11              Works
B3                 4.20              Works
B3                 4.30              Works

```

I've used a DWL-G650 on Ubuntu before (on Hoary Hedgehog - the second Ubuntu release) and the madwifi was included and worked out of the box. It should be the same for Breezy, or you might have to install the drivers using Synaptic... shouldn't be difficult at all. However, I've also read that some of the G520's use an acx100 chipset. I'm not quite sure if that would work or not. Safest bet in my opinion is to try the LiveCD and then go to System > Administration > Networking and see if it shows up in the list. If it does and you can get it running, you should be fine installing it.

EDIT: LOL, must have completely missed your edit above, good to hear. Oh well, the info above is here if anyone else needs it :)

---

### Post by Ca$h on 2006-04-09
Haha, its alright.

I should be installing ubuntu on a seperate hdd tomorro, can't wait!!!:cool:

---

