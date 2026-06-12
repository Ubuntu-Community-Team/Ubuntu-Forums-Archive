---
title: "Installation Woe"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by ibuntutoo on 2007-03-17
I am installing Ubuntu on a second computer. I boot from the disk, on the first screen where the choices for installation are I select the first option. It begins to boot Ubuntu and then the screen begins to alternate from working to not working. I reboot the computer and select the second option on the menu, safe screen mode. Now it boots without any problem. I set up the install it goes smooth and then near the end the computer just shuts down. 
The Hardware is the following:
[LIST]
[*]Duron 1.7 Ghz Processor
[*]40 gb Maxtor Drive
[*]ATI All-in-wonder AGP Card
[*]512 MB of Ram
[/LIST]

---

### Post by oilchangeguy on 2007-03-17
please advise the version of ubuntu you are using.

---

### Post by halitech on 2007-03-17
boot from the cd and run the memtest to see if you have a memory problem. also, if you can, as soon as it reboots, go into the bios and check the temp and see if maybe you have a heat issue.

---

### Post by oilchangeguy on 2007-03-17
if there were a ram issue the computer probably would not pass post. if the cpu were overheating the computer would shut down. and not all bios's have the option to check the cpu's temp.

---

### Post by halitech on 2007-03-17
not to argue but I've had systems that would pass POST but were still locking up and causing problems,

> 
Now it boots without any problem. I set up the install it goes smooth and then near the end the computer just shuts down. 

looks like it is shutting down

> 
also, if you can, as soon as it reboots, go into the bios and check the temp and see if maybe you have a heat issue.


I know, thats why I said if possible.

---

### Post by ibuntutoo on 2007-03-17
Ubuntu 6.10
will try both memory and cpu temp. What should be right temp for the CPU?

---

### Post by halitech on 2007-03-17
temp will depend on the CPU. is it AMD or Pentium? thunderbird, duron, p3, p4, celeron?

---

### Post by ibuntutoo on 2007-03-17
AMD Duron is the processor. Update I was able install from safe screen mode, however upon reboot I run into same on and off screen.
How do i boot bash promp only?

---

### Post by halitech on 2007-03-17
temp for a duron (least mine anyways) can run up to 70C although mine normally runs around 48C at idle and 55 under load.

I'm thinking video drivers now. may have to boot from the livecd and opena terminal there and run 
```

sudo dpkg-reconfigure xserver-xorg
```

---

