---
title: "Need Airport drivers"
date: 2010-05-31
forum: Apple Hardware Users
---

### Post by jmagick07 on 2010-05-31
[SIZE="6"]iMac8,1[/SIZE]

The main problem is **I have no Internet at all, can't access the router with Ethernet because it's in another part of the house, therefore I can't download any packages in the Terminal or elsewhere when running Ubuntu**

How do I install drivers for Airport without downloading anything via Ubuntu?  Is there anything I can download on the Mac OS X side and then transfer to Ubuntu later?

---

### Post by jmagick07 on 2010-05-31
I'm guessing from the silence, that without Internet, I can't enabled Internet?  That's a paradox.


I have another problem:
My secondary display is fuzzy when using Ubuntu.  Connected via mini-dvi to vga adapter.

The main problem is more important than the new problem.

How to get my Airport working when I DO NOT have any way to download packages???

---

### Post by sha.goyjo on 2010-05-31
Alright, here's the problem. Due to licensing restrictions Ubuntu itself cannot package the firmware. I have it, in folders, and I can 7z it and send it to you. You can take it, uncompress it, and put it in /lib/firmware.

Just pm me an e-mail address and I'll get it to you.

---

### Post by jmagick07 on 2010-06-01
Thank you for your help, but for some odd reason it still doesn't seem to work.

I also tried [This driver from Broadcom]("http://www.broadcom.com/support/802.11/linux_sta.php") but it requires I download some tools via the Terminal to compile it.  No internet = no compiling.

---

### Post by sha.goyjo on 2010-06-01
Weird. After you copied those folders to /lib/firmware they should have been picked up by the b43 kernel driver

Can you give the output of 
```
dmesg | grep b43
```

That should allow us to see if its finding the firmware or not.

---

### Post by jmagick07 on 2010-06-01
```
[    0.796665] b34-pci-bridge 0000:04:00.0: PCI INT A -> GSI 16 (level, low) ->
IRQ 16
[    0.796672] b43-pci-bridge 0000:04:00.0: setting latency timer to 64
```


[http://i47.tinypic.com/1yio0.jpg](http://i47.tinypic.com/1yio0.jpg)

---

### Post by linuxopjemac on 2010-06-01
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by sha.goyjo on 2010-06-02
> **jmagick07 said:**
> ```
[    0.796665] b34-pci-bridge 0000:04:00.0: PCI INT A -> GSI 16 (level, low) ->
IRQ 16
[    0.796672] b43-pci-bridge 0000:04:00.0: setting latency timer to 64
```


[http://i47.tinypic.com/1yio0.jpg](http://i47.tinypic.com/1yio0.jpg)

Weird. Normally when it can't find those firmware files it displays an error message about not being able to find firmware. dmesg should have picked that up.

---

### Post by jmagick07 on 2010-06-07
I tried all of the solutions with no luck.  And apparently the "using the CD if no Internet" method only works if you have a mailed disc, because my downloaded one didn't work.  I even removed my 64-bit version and installed the 32-bit version, thinking that might help with any of the above mentioned solutions, it didn't.

In the end, I bought a 50-foot Ethernet cable and connected it to the router to get a wired connection, then downloaded the drivers via System -> Administration -> Hardware Drivers  Now I have a wireless connection.

Thanks everyone for all your help :)

---

