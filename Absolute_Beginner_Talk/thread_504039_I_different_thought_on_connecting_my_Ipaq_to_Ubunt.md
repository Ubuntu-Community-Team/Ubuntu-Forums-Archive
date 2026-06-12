---
title: "I different thought on connecting my Ipaq to Ubuntu.."
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by clipse on 2007-07-18
I am more concerned with transfering files and I got to thinking. What would happen if I us a bluetooth dongle on my Ubuntu box and tried to connect with the bluetooth on my Ipaq?

clipse

---

### Post by clipse on 2007-07-19
No ones tried this?

clipse

---

### Post by scotty32 on 2007-07-19
yes, ive done this.

I have a iPaq RX3715, and it works best in KDE with bluetooth.

Also i did get it working on ubuntu with the usb dock by installing Raki, you may need Konqueror aswell.
it is overly complex to get working in ubuntu, but as i said, KDE seems to work best (atleast on bluetooth)

i'll post what i did when i get home

---

### Post by clipse on 2007-07-19
> **scotty32 said:**
> 
i'll post what i did when i get home

That would be a great help. thanks.

---

### Post by scotty32 on 2007-07-19
This may go wrong, as i cant remember what i installed / what you need, as it was a while ago.

but to start with, follow this How-To:

[http://ubuntuforums.org/showthread.php?t=86302&highlight=synce](http://ubuntuforums.org/showthread.php?t=86302&highlight=synce)

next install Raki, and Konqueror.

then put the PDA in, and do the following in the termainal:

```
raki
sudo synce-serial-config ttyUSB0
sudo synce-serial-start
```

the icon for Raki in the taskbar should go from grayed out to colourfull, if it doesnt, it wont work, if it has, you can left click on the Raki icon and select (mine says) Anoymous and select "rapip://active_connection/" or you can type this into Konqueror.

this "should" work and you should be able to see the PDA as a file system.

if it doesnt work let me know - as i "might" of installed something else.

---

