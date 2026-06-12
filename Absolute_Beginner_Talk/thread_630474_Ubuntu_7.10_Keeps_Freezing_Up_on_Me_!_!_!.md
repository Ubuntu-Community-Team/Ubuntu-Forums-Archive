---
title: "Ubuntu 7.10 Keeps Freezing Up on Me ! ! !"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by 449 on 2007-12-03
So I've had Ubuntu on this computer probably a month and I never had the problems I did up till yesterday.

Problem #1: Dragging url links in Firefox cause the whole system to freeze. And I think caps lock light and the one to the right of it (scroll lock?) would blink simultaneously. I say I think because I'm not 100% sure it happened in this instance ,but if definitely did in others. I accidentally did this about 3 to 4 times yesterday (I was on for a good 10 hours) and every time same thing. 

Problem #2: After I just restarted my computer I let everything load and what not then I open three programs one after another. And when I do the system completely freezes and those two lights blink again.  When I say open I mean I click one after another because the computers specs are decent and I don't remember it being an issue.  The programs are Armorak, Deluge, and Firefox not exactly resource hogs. And this is after my computer has been started up. specs are:

Pentium 4 3GHz
512MB RAM
250GB external HDD (no internal)
Intel Graphics Media Accelerator 900

I'm mostly concerned about the first one and not so much the latter. If anyone can shine some light on these issues that be great!
**the zip is 3 posts down**

---

### Post by 449 on 2007-12-03
This should be in a different forum shouldn't it... :confused:

---

### Post by webdr on 2007-12-03
Please post the output received by running the 'dmesg' command from terminal.

This will allow us to review errors logged from debug. Often, hangups are related to 
incompatible hardware / software settings. As a for instance... I run mostly toshiba
laptops... If one runs the vanilla ubuntu install there are often freezes and lockups. 

Toshiba / Phoenix Bios implementation of the apic standard are well not actually standard, and 
as such I am required to append 'noapic' to my kernel config line in grub boot list.

Back to the topic at hand, if you will, please forward that output to here for review.

-webdr

---

### Post by 449 on 2007-12-03
I attached the file because the forum gave me an error saying I had too many image codes. It took me a while to get a format that will fit ,but I think I got it. :)


Completely off topic or, possible not but when I have Deluge open and downloading I can't use Firefox. I get the could not find server page. And it's not because I'm downloading a lot of stuff. The weird thing is I used the same port last night and didn't have this issue. The port I use is 6112. Yeah everytime I open it freezes everything and I get the blinking lights.

---

### Post by 449 on 2007-12-03
Ok, I'm pretty much able to confirm that when I on purpose or accidentally try to drag and drop anything thats not a actually file it locks up the whole desktop which makes me have to force shutdown. 

The Deluge issue is now in Azureus. I tried going back to it because I never had anything issues the few days I had it before ,but after a few minutes it locked everything up again. I do remember one thing that I could have done to mess things up. I changed the "max connections" in deluge and ever since it's been doing this freezing stuff. It could be totally unrelated ,but that's just the point I remember the freezes starting for my bittorrent client.

---

### Post by webdr on 2007-12-03
Try this fix...
add noapic to your kernel options..

howto:

sudo nano /boot/grub/menu.lst

make modifications...
ctrl +x to exit
answer prompts as needed in order to save changes
reboot system.
test

video of how to do this:
[http://www.markw.net/editbrubkernelopts.ogg](http://www.markw.net/editbrubkernelopts.ogg)

Hope this helps,
WebDr

---

### Post by 449 on 2007-12-03
> **webdr said:**
> Try this fix...
add noapic to your kernel options..

howto:

sudo nano /boot/grub/menu.lst

make modifications...
ctrl +x to exit
answer prompts as needed in order to save changes
reboot system.
test

video of how to do this:
[http://www.markw.net/editbrubkernelopts.ogg](http://www.markw.net/editbrubkernelopts.ogg)

Hope this helps,
WebDr

I think I messed something else and I'm not exactly sure what I'm doing so If you could walk me through this that be great. Terminal still scares me. :confused:

---

### Post by 449 on 2007-12-03
Anyone?

---

### Post by 449 on 2007-12-04
I really hate to bump again ,but if someone could just help guide me through this process I would greatly appreciate it. It nice to have my system at it's normal functionality.

---

### Post by 449 on 2007-12-04
Could someone help me out here?

---

### Post by ammarunta on 2007-12-05
I had the same prob after an X11 update, random freezes 

If you are using copiz try this, it worked for me 

Open compiz setting manager - go to the enable resize windox tab and choose "normal"  for your default resize mode 

I think its an X windows bug

---

### Post by 449 on 2007-12-05
> **ammarunta said:**
> I had the same prob after an X11 update, random freezes 

If you are using copiz try this, it worked for me 

Open compiz setting manager - go to the enable resize windox tab and choose "normal"  for your default resize mode 

I think its an X windows bug

I tried this and still no luck. I'm not positive ,but I think the problems might of started after the installation of Deluge. How would I go about completely removing this?

---

### Post by Papa-san on 2007-12-05
I am pretty new myself, but I'll see if maybe you aren't running into the same issue I was having.

My system would lock up fairly regularly, for no apparent reason. I discovered that it was my video card/ video drivers. 

What kind of video card are you using?

run this and see if it gives you any errors:```
cat /var/log/Xorg.0.log | grep EE
```

Post your results if it does.

Oh, don't be afraid of the terminal. Now that I'm getting the hang of it, I am actually turning to it sometimes before using a GUI (point n click) For a while, don't cut and paste, but actually type the commands you use. It does help you start figuring out what you are telling your comp to do. If you find you frequently make typing errors, then cut and past, but you will learn through your mistakes...

---

### Post by 449 on 2007-12-05
erik@erik-desktop:~$ cat /var/log/Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
erik@erik-desktop:~$

---

### Post by Papa-san on 2007-12-05
Try opening a few terminals and running```
glxgears
```

Get a few of those running, and see if it locks you up.

There aren't errors in your cat /var/log/Xorg.0.log | grep EE , so I'm not sure. I figured it was worth a shot...

---

### Post by Papa-san on 2007-12-05
> **449 said:**
> I tried this and still no luck. I'm not positive ,but I think the problems might of started after the installation of Deluge. How would I go about completely removing this?

try ```
 sudo aptitude remove Deluge
```

---

### Post by 449 on 2007-12-05
> **Papa-san said:**
> Try opening a few terminals and running```
glxgears
```

Get a few of those running, and see if it locks you up.

There aren't errors in your cat /var/log/Xorg.0.log | grep EE , so I'm not sure. I figured it was worth a shot...

I opening four and everything was completely fine.

---

### Post by Papa-san on 2007-12-05
OK... I just thought it might be the problem. I know how frustrating it is. I am sure that someone will be along to help. The people around here are great!

---

### Post by 449 on 2007-12-06
> **Papa-san said:**
> OK... I just thought it might be the problem. I know how frustrating it is. I am sure that someone will be along to help. The people around here are great!

The full removal of Deluge seemed to have had some effect because I can run Azureus without it freezing. As of right now solved. :)

---

### Post by 449 on 2007-12-06
I spoke too soon!! Soon after I thought I had it fixed it froze again...

BUT

Here's where it gets really interesting.

 The 'freezing' computer is connected wirelessly to a router. When I turned off the freezing wireless computer I immediately lost my connection to Xbox Live(also connects to router wirelessly.) And immediately after I had restarted the freezing wireless computer Xboxlive immediately connected. I also heard my dad complaining a few times about how he would always have to reset the router to connect with his laptop. 

If anyone has any clue to what is going on here I would appreciate it so much if you could help me out. Thanks!

---

### Post by 449 on 2007-12-06
Anyone?

---

### Post by 449 on 2007-12-06
This is driving me crazy! I'm really trying to avoid reinstalling, although I would if I knew it would fix the problem. The thing is the router is downstairs so that means I got to carry this computer down to connect to the router. Help... :confused:

---

### Post by philinux on 2007-12-06
What is the wireless card in your pc?

---

### Post by 449 on 2007-12-06
Dynex

---

### Post by philinux on 2007-12-06
ok what model number, 

[FONT="Courier New"]lspci [/FONT]should show it if you're not sure.

---

### Post by Vadi on 2007-12-06
Oh my ubuntu sometimes freezes up (for like a second) too, it's because of wireless for me though. The log files say some renewal is coming up, when it comes up, it hiccups but goes on.

Can you tell us the model of the card? And are you ndiswrapper, or it just worked out of the box or how?

---

### Post by 449 on 2007-12-06
Dynex® - 802.11g Wireless-G Desktop Card

---

### Post by philinux on 2007-12-06
Post the output of 

[FONT="Courier New"]**lspci**[/FONT]

---

### Post by 449 on 2007-12-06
Here you go: 

> erik@erik-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:01.0 Communication controller: Conexant HSF 56k Data/Fax Modem
06:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 03)
erik@erik-desktop:~$ 



---

### Post by philinux on 2007-12-06
Arrrgghhhh

The notorious **[COLOR="Red"]Network controller: Broadcom Corporation BCM4318[/COLOR]**

Think you need to search for this in the forum.

Broadcom are the worst for linux allegedly

---

### Post by philinux on 2007-12-06
[http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)

Maybe an update or something wrecked your wireless. Who knows

---

### Post by 449 on 2007-12-06
> **philinux said:**
> [http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)

Maybe an update or something wrecked your wireless. Who knows

I think I'll give this a try when I have a chance to move my computer. Thanks!

---

### Post by philinux on 2007-12-06
Do a forum search for Broadcom BCM4318

There are a few different approaches but most seem to suffer from random freezes, internet disconnects.

When I saw broadcom I though ohhh nooo..

Anyway good luck.

---

### Post by 449 on 2007-12-06
> **Vadi said:**
> Oh my ubuntu sometimes freezes up (for like a second) too, it's because of wireless for me though. The log files say some renewal is coming up, when it comes up, it hiccups but goes on.

Can you tell us the model of the card? And are you ndiswrapper, or it just worked out of the box or how?

Yeah I had to use the ndiswrapper thing.

---

### Post by 449 on 2007-12-06
Ok this is getting REALLY annoying. I searched around ,but everything I found was about getting the card working; not related to random freezes. I'm getting ready to just give up on this because it's not worth the effort. Could someone recommend me a desktop wireless card that works out of the box and doesn't cause random freezes?

---

### Post by webdr on 2007-12-08
Sorry for the response lag 449, anyway, did you watch that video?

Are you still terminal queasy after watching the video?

webdr

---

### Post by 449 on 2007-12-08
> **webdr said:**
> Sorry for the response lag 449, anyway, did you watch that video?

Are you still terminal queasy after watching the video?

webdr

It doesn't really explain anything and its very confusing what he's doing. :confused:

---

### Post by Papa-san on 2007-12-10
Don't even need to search! LOL
I have a link in my signature line!

The process of getting it functioning properly is what is prolly going to take care of the lock-ups. Just follow the procedures.  Don't let the terminal intimidate you. You will get used to it. Just try to remember what you do in it and why...

---

