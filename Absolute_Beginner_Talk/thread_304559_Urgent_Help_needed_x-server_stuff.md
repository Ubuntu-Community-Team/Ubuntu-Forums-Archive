---
title: "Urgent Help needed x-server stuff"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by kiyometane on 2006-11-22
I cant access edgy when it boot. I get an blue error screen that says:
"Failed to start the x server(your graphical interface)
It is likely it is not set up correctly. Would you like to view the x server output to diagnose the problem?"

How do i solve that?

---

### Post by seshomaru samma on 2006-11-22
You need to reconfigure X
run this :
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by christian130 on 2006-11-22
i'm having the same problem but i was updating my ubuntu breezy badger after the package manager asked me for rebooting the pc, so i reboot. later when it was closing the screen shows up with the wallpaper i had in my desktop and it freezed. i continue to RESET the machine in order of solving the problem. after that the kernel shows up the same dawn error.

---

### Post by kiyometane on 2006-11-22
I'll try, but were do i run the command.

---

### Post by kiyometane on 2006-11-22
the comand work. But each time i reboot the system, i get the same xserver error.
What do i need to do to stop that

---

### Post by kiyometane on 2006-11-22
How do i stop x server from loadin each time i boot into edgy.
Also how do i set the graphics symilar to fresh install.
i have an nvdia card and each time i upgrade the driver, x serve shows up as well

---

### Post by tehdecoy on 2006-11-22
I'm running into the same problem here--getting the "Failed to Start X Server" message.  I have already tried to reconfigure X, but still no luck.  So far Ubuntu has been the only linux distro that has given me this problem.  I'm running a Radeon X800 if that helps any.  Oh, I have tried using the ati, vesa and even the vga driver sets.  Any help would be nice.

---

### Post by kiyometane on 2006-11-22
I tried both vesa and vga but i get same error. the only way i had to fix it was copy the xorg.conf file from life cd and past it to the hardrive were edgy is.(Thanks to Taurus who helped me).
But now each time i upgrade my graphic card drivers, i get the same error

---

### Post by dude420 on 2006-11-23
I am new to linux w/ only a couple of days experience and I am having same problems.  I have ran xserver config a couple of times using different settings with same results.  Running dimension 2600 laptop w/ Intel 830MG integrated graphics (Dell sux).  I installed ubuntu on desktop w/ no problems, but laptop is giving me a big headache.  I am downloading dapper now to see if I get different results.  Hopefully someone will come up w/ an answer to solve this question.  If not hopefully dapper will cure all.  Also since I'm new I have to say that this linux community is awesome.  It gives me new hope that there are good, descent people still out there.  If anyone comes up with an answer thx in advance.

---

### Post by dude420 on 2006-11-23
I have tried dapper w/ the same problem once again "Failed to start the x server(your graphical interface)
It is likely it is not set up correctly. Would you like to view the x server output to diagnose the problem?"  ](*,) 
Mabey I should try suse.  I really wish I could get this to work on my laptop.  Works great on desktop.  Dual boot w/ xp pro.  No issues w/ desktop yet except lack of knowledge about linux.  As a matter of fact I installed avast in linux and found 25 viruses in windows partion that N.I.S. 05 didn't find.  Linux rocks. If anyone can help fix this please, please, please help a noob.  thx

---

### Post by Griffongob on 2006-12-23
I get the same error too but I'm confused on what to put in for location of my PCI slot even though I use PCIe and also when I get to where u choose ur color whether its 1 -24 bit after I select 24 bit it kicks me out of the reconfig saying that that overwrites soem other info what can I do to fix this?

---

