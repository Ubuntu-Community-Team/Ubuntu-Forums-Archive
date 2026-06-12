---
title: "Extreme trouble with LINKSYS WUSB54GC"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by d00derino on 2007-09-27
Ok, here's the deal. After days of trying, I gave up on using my old wireless adapter. So I looked on the site, and found one that said it should work right out of the box (with Ubuntu recongizing it). I went out and bought the Linksys WUSB54GC. 

Nothing was recongized. Hell, I don't even know HOW Ubuntu would let me know it was recognized. I searched through Networks, it found nothing. 

So I tried ndiswrapper:

```
travis@Travis:~/Desktop$ lsusb
Bus 001 Device 003: ID 13b1:0020 Linksys 
Bus 001 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 001 Device 001: ID 0000:0000  
travis@Travis:~/Desktop$ ndiswrapper -i rt73.inf
couldn't create /etc/ndiswrapper/rt73: Permission denied at /usr/sbin/ndiswrapper-1.9 line 146.
travis@Travis:~/Desktop$ 


```

How do I get rid of that error? Or alternatively, why isn't Ubuntu picking up the wireless adapter? It's THE one that works with Ubuntu, and moreover, the light on the adapter does flicker on and off occasionally, like it's looking for something to connect to. But the hell if I know what to do!

What is a Linux n00b like me to do? Please help...

---

### Post by linuxwizard on 2007-09-27
Check over this see if you can find something that will help.

[https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB54GC](https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB54GC)

---

### Post by d00derino on 2007-09-27
I got it to work, I apologize for making this thread. 

What I don't get is this whole 'sudo' command. What does 'sudo' do?

---

### Post by nb123 on 2007-09-27
Glad you got it to work, I have the same wireless adapter. 'sudo' is a command that allows you to execute a specific command that only the root user has permissions to. In many other distros, you normally 'switch' to a particular user permission mode in your terminal. In ubuntu though, you normally only use root permissions (i.e. sudo command) for specific tasks. This is an added feature that as a linux beginner myself I like a lot as it makes it much harder for me to make mistakes while working in the terminal. I know it may seem annoying at first, but bear with it, it's not that big a deal really and most of the time you shouldn't be working as root.

---

### Post by linuxwizard on 2007-09-27
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

