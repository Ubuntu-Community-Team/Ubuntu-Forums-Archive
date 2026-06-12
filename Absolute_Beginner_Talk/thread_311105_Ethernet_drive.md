---
title: "Ethernet drive"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-12-02
Hi everybody

I need to install the driver of the ethernet: the readme.txt file says that I need to make a new directory and download in it the driver. But I'm denied to download the driver in it because I haven't the permission to do it. :confused: :confused: 

What can I do? How can I change the permssion of the directory?

Thanks for any hint.

---

### Post by equal on 2006-12-02
Save the file to your Desktop.
Then go into terminal and type 
```
gksudo nautilus
```
it'll ask for your user password, and it will open up a folder browser window with Administrator permissions. Just navigate to the folder you need to put the file in, drag and drop the file in there. Should work!

---

### Post by taurus on 2006-12-02
What ethernet do you have and if you need to download it, download it to your own $HOME directory!!!

---

### Post by helphope on 2006-12-03
Thanks to everybody for replying.


> **equal said:**
> Save the file to your Desktop.
Then go into terminal and type 
```
gksudo nautilus
```
it'll ask for your user password, and it will open up a folder browser window with Administrator permissions. Just navigate to the folder you need to put the file in, drag and drop the file in there. Should work!

I've got this message when I prompted ```
gksudo nautilus
(Nautilus:5173):GnomeUI warning**:while connecting to session manager:autheticathion rejected reason none of the authentication protocols specified are supported and host-based authetication failed.
```


> What ethernet do you have and if you need to download it, download it to your own $HOME directory!!!

On the floppy disk there is written: Fast Ethernet Adapter 10/100 BASE-TX.

---

### Post by steve.horsley on 2006-12-03
But what makes you think you need to install an Ethernet driver? It's very rare that you find an Ethernet card that Linux doesn't already know how to use. What make is it?

---

### Post by helphope on 2006-12-03
Thanks for replying
Thanks for replying


> **steve.horsley said:**
> But what makes you think you need to install an Ethernet driver? It's very rare that you find an Ethernet card that Linux doesn't already know how to use. What make is it?


It's a heyDOIT; (PCI LAN Card 10/100Mbps 32-bit).

If I want to change it, where can I look to be sure to buy one that it is automatically supported.

When I installed Linux, I got the message, that there wasn0t any etherned card dectected (whereas in windows '98 it works and connects me to internet. The PC has a dula boot; win'98 and drapper).

---

