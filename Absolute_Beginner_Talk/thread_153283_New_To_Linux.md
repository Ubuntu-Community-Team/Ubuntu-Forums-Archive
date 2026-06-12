---
title: "New To Linux"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by Maria_Firewire on 2006-03-31
Hello,

So I bought a bunch of new hardware for my computer...I guess I bought a new computer really. I figured that it was also high time to say good-bye to Windows, as that relationship was getting more and more abusive, haha.

Here's the important stuff:

CPU:AMD Athlon 64
mobo: ASUS A8N5X
graphics: Geforce 6800GS
RAM: 2 GB

I tried installing ubuntu 5.10 and had some issues but worked those out last night thanks to some other people's post on the forum. My problem now is that on start up everything seems okay...Ubuntu is doing the whole 'loading thing' and then the screen just goes crazy: random colors everywhere. It basically tooks like a magic eye poster. **I tried staring at it but there were no cool hidden images, haha**

I assume this is a graphics card issue but how do i fix it when i can't even use  the OS? All the hardware detection was automatic but should i have changed something manually?

Any help would be much appreciated. I blew away Windows so I'm going to have to learn to love Linux.

---

### Post by christhemonkey on 2006-03-31
Type Ctrl+Alt+F1 to get into a terminal
then login.
Welcome to linux btw!
Next type
```
sudo dpkg-reconfigure xserver-xorg
```
then select the appropriate options, the important bit for you is the section on vertical refresh and horizontal sync (if you select advanced).  Then type in the correct range of values (see your monitors manual for what it can display)
Then when your done, type at the console;
```
sudo /etc/init.d/gdm restart
```

---

### Post by Maria_Firewire on 2006-03-31
Sorry I'm not at home right now so i can't test this till later tonight. An additional question, can you get into a terminal even before the 'OS graphical interface' has loaded? I'm going to say this in Windows terms because i know no other :( : The screen gets all screwy after the startup, loading bar screen but before i get into Windows.

---

### Post by Razorback on 2006-03-31
You can try hitting the esc key while grub is loading then choose to boot the kernel in recovery mode.  This will take you to a linux prompt - after alot of text scrolls by.  Then, reconfigure X.

---

### Post by steve.horsley on 2006-03-31
[QUOTE=Maria_Firewire]Sorry I'm not at home right now so i can't test this till later tonight. An additional question, can you get into a terminal even before the 'OS graphical interface' has loaded? I'm going to say this in Windows terms because i know no other :( : The screen gets all screwy after the startup, loading bar screen but before i get into Windows.[/QUOTE]
Yup. Alt-Ctrl-F1 should get you a textual login prompt, even when the GUI is all screwed up. It's white on black, just like the BIOS self-test before windows starts. Alt-Ctrl-F2 to F6 get you 5 more such screens, and Alt-Ctrl-F7 gets you the GUI (screwed up or not). You could log in as different people and have different things happening on all of them. There's even a way to get a second GUI (possibly logged in as someone else again) on Alt-Ctl-F8, but that's getting fancy, and eats up the memory a bit, so it's not common.

**sudo dpkg-reconfigure xserver-xorg** will ask some tricky questions about your video setup, and hopefully get a working GUI afterwards. If you have lots of trouble, I gather specifying the **vesa** driver as a last resort might get something going.

You may need to issue the command **sudo /etc/init.d/gdm restart** after reconfiguring, to get the GUI restarted.

Good luck.

---

### Post by Maria_Firewire on 2006-03-31
Thanks to everyone who helped answer my questions! You guys are so helpful. I finally got Ubuntu up and running...YAY!

---

### Post by Maria_Firewire on 2006-03-31
Okay, another question: How do I set up my wireless internet? I know this isn't a simple one so if you know of a website that would explain the basics, let me know...that way I don't waste anyone's time with questions that are too broad.

Thanks.

---

### Post by johnnymac on 2006-03-31
This question has many answers in linux....

Some cards are supported by default, others use ndiswrapper utilities, and others use madwifi.  So first off you gotta figure out what kind of card you have (driver that is).  

So......here's how to start - once you figure out your card you can query the forum for a bunch of how-to's

1.  from a terminal issue this command:
```
lspci |more
```
You should see something that mentions your wireless adapter (802.11a\b\g blah blah)

2.  Take what you find....and query the forum....trust me, there's a lot of how to's on this stuff.

Good luck.....or, if you post back here with what the results are I'll check back and tell you where to go.

---

### Post by trent dillman on 2006-04-01
johnnymac: less is more ;)

---

