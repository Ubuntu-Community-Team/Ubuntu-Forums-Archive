---
title: "os not detecting usb device"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by bear1959 on 2008-03-08
When I plug my usb cable (MP3 player) it doesn't pop up on the screen telling me it has found my device. I even tried different cables and devices.
Thisis a new problem for me it has only been happing in the last week or so.:confused:

---

### Post by buntu_Geek on 2008-03-08
Type the following command in your terminal and post me back the result.

```
 lsusb
```

---

### Post by Papa-san on 2008-03-08
It did work before, though? I was running 6.06 and it wouldn't detect it. Tried everything and had to upgrade to 7.10. Still no workee... Ended up installing Gnomad2 and updating it, and it finally worked.

---

### Post by bear1959 on 2008-03-08
I am really sorry, I am new to command lines? don't even know where to go to type what you told me????

---

### Post by Papa-san on 2008-03-08
The terminal is where you enter command lines. You get to it bu going to Applications > Accessories > Terminal. 

The lsusb command can just be typed in.

Some commands require you to be 'Super User' so, 'sudo' is typed first. That stands for 'super user do'. Seriuosly... Then it will ask you for your password.
 As you type it in, you will NOT see any characters or dots or asterisks. Don't worry, it's reading them...

---

### Post by bear1959 on 2008-03-08
Hey I found the terminal WOW!
When I typed in what you asked I ended up with" 

karented@karented-desktop:~$ lsusb
Bus 002 Device 002: ID 045e:00e1 Microsoft Corp. 
Bus 002 Device 003: ID 1267:0103 Logic3 / SpectraVideo plc 
Bus 002 Device 004: ID 03f0:3a02 Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
karented@karented-desktop:~$ 
????

---

