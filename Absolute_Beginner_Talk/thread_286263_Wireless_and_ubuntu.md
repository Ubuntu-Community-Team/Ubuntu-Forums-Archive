---
title: "Wireless and ubuntu"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by Redeyes on 2006-10-27
hi i am new to Linux i have tried Ubuntu and i liked it i really  want to switch to Linux, my only problem is my wireless internet i currently have a BT voyager 1055 USB adapter which i could not get working (i tried the ndis wrapper with no luck) any way i was just  wondering if any one has got this working or if any one know the best wireless card to get working with Ubuntu e.g. one the works out of the box. Thanx for the help in advance.

---

### Post by SomeGayDude on 2006-10-27
You should checl this document out.  I didn't see your voyager, but if you planed on purchasing one this page is a life saver.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by drainpipe on 2007-07-20
I successfully installed a BT Voyager 1040 PCI wireless network card today using the instruction provided in:

[http://ubuntuforums.org/showthread.php?t=504788&highlight=bcmwl5.inf](http://ubuntuforums.org/showthread.php?t=504788&highlight=bcmwl5.inf)

Follow it to the letter and there is a good chance you will achieve success.  The only difficulty I had was placing too much faith in the Network Configuration tool, which appears (maybe) next to the speaker icon at the top right of the screen.  Only once did it display wireless connections.  That was the at the first time of use.  After that it only displayed 'wired' and manual options.  Use the main System->Administration->Network tool instead.

To be safe, once you have finished the intall, setup your router for open (non encrypted) broadcasting.  My router needs a restart to make sure it is working properly, after any major operational change.  I suggest you turn off your PC completely, turn off your router and, if present turn of your broadband modem.

Wait for about 1 minute then power up the modem, wait for it to achieve its ready state.  Do the same with your router.  Finally, power up your PC.

Hopefully all is well.  Go back and set up WEP to secure your network (copy the HEX values from your router, don't use alphabetic).  Go through the power down/up cycle as before.

---

