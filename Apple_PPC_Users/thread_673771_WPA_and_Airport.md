---
title: "WPA and Airport"
date: 2008-01-21
forum: Apple PPC Users
---

### Post by mariner8905 on 2008-01-21
Im running an Ibook G3 with PPC (odviously since im posting in the PPC section) and i would like to get WPA on my Ubuntu 6.06(dapper Drake) but i have had no success. been through a lot of other threads and they make it seem so simple but it doesnt seem to work for me. ive installed wpasupplicant and network manager and commented out a bunch of stuff in the interfaces file. looking in the running processes i dont see wpa supplicant running so i think that is one issue but i cant figure out how to get it running. any help would be greatly appreciated. i am also a newbie to linux so detailed instructions would be nice, at least for the coding sections.

---

### Post by Brian McConnell on 2008-01-21
I also spent hours trying to get my wireless connection with WPA2 up and running on Ubuntu Feisty for ppc. First, your card is recognized and functional, right? If so, open a terminal and type:
```
wpa_passphrase your_ssid your_psk
```

where the your_ssid is the name of the network and your_psk is the password you want to connect. It will spit out a big, long string of characters and numbers. It might look like this:
```
luca@laptop1:~$ wpa_passphrase mywlan thisisthepassword
network={
        ssid="mywlan"
        #psk="thisisthepassword"
        psk=**b22ec921c254c73f99b31b76ff876692ecde36839a1f2d92150829e6afcb5515**
}
```

now, click the network manager icon on the top right of your screen (assuming you use the gnome desktop) and select "connect to other wireless network" enter the proper information, but rather than use your "normal" password, use that big, long string of characters you got when you ran the wpa_passphrase command. It worked for me. If your card is not detected, I might not be of any use to you. Good luck!

---

### Post by stmiller on 2008-01-22
The original airport card (non-extreme) does not support WPA in Linux.

Someone has written a new driver for this original airport card (which is actually an orinico card) to do WPA in software with the wpa_supplicant. I haven't gotten it to work on my Tibook, but it should work.

For powerpc it requires compiling the new driver from source. Check out this [long] thread:

[http://ubuntuforums.org/showthread.php?t=304217](http://ubuntuforums.org/showthread.php?t=304217)

---

