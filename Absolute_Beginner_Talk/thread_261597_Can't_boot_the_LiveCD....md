---
title: "Can't boot the LiveCD..."
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by exer! on 2006-09-20
This is my first Linux ever, so I'm a total newbie. Sorry for any incorrect expressions.

I got Ubuntu and Kubuntu CDs (ShipIt, not ISOs) and wanted to try LiveCD. So, I inserted the Kubuntu CD into the drive, restarted the computer (PC), selected the CD-ROM as the first boot device in BIOS and booted from CD. I selected the Start and Install Kubuntu option. There was a black screen saying "Uncompressing Linux... OK, booting the kernel." for a sec or two, then a Kubuntu loading screen with progress bar showed up. It stopped loading after "Mounting the root file system". After two or three minutes, the screen with "Uncompressing Linux..." appeared again, with a blinking terminal cursor. And that's it! It won't go any further. I can only reboot the system.

So, I rebooted and read Help. I've tried to type numerous swithches in the prompt and none of them produced any progress. 

When I delete "quiet splash" option from prompt, the last message I get is:

```
[4294674.xxx000] udevd-event[1679]: run_program: '/sbin/modprobe' abnormal exit
```

(the number with xxx varies with every boot)

I tried the Ubuntu CD, and I get the exact same thing.

Can anyone help?

P.S. Sorry for my bad English...

---

### Post by gn2 on 2006-09-20
Have you tried booting using the "noapic" "nolapic" option?

Or any of the other boot options?

---

### Post by exer! on 2006-09-20
Yes, I've tried those. I've also tried a "nodma" option I saw in a similar topic, but it's the same...

---

### Post by gn2 on 2006-09-20
What are youre hardware specifications, do you have enough (256mb) RAM?

---

### Post by gn2 on 2006-09-20
And have you tried different disc eg Ubuntu or PCLinuxOS in this machine?

Have you tried non-working Kubuntu disc in another PC?

---

### Post by exer! on 2006-09-20
It's a bit old, but it meets the requirements. I've 512MBs of RAM, AMD Barton 2500+, DFI nF2 LanParty MB, 80GB HD (with Windows on it).

---

### Post by exer! on 2006-09-20
I've tried with the Ubuntu CD aswell, and I get the same problem. Unfortunatly, I can't try them in other PC.

---

### Post by exer! on 2006-10-01
I still cannot boot it... Does anybody have a different solution?

---

### Post by SirShaggy on 2006-10-01
Just a thought here.....
If you have any usb devices hooked up while you boot the live CD,
unhook them before you turn it on. Leave them disconnected until the desktop loads. I am not sure why, when I installed on my desktop, my external USB hard drive and my Mouse gave the CD fits. I hooked them up at the desktop and installed the system. Everything has been fine since then. I am just guessing, The CD must be trying to configure your hardware and is getting stuck looking?!?!?
Hope it helps a little,
SirShaggy

---

### Post by exer! on 2006-10-01
OK, I will try that... I only have a scanner hooked on USB. Can PCI cards be a problem while configuring...?

---

### Post by firebirdworks on 2006-10-01
well if that doesn't work, try geting xbuntu, I had the same problem a while ago, and I used that and it worked, even thought my laptop had the specks that yours did.

---

### Post by SirShaggy on 2006-10-01
I have heard a few people had troubles with some cards, I am not sure if it was while booting or just using them. RAID caused my friend some grief, he got it working though. He also has an XP2500+ with 2 512mb sticks of ram. It is much faster than what I use, faster than all three of my systems:( 
I know there will be somebody on here with better advice, mine is limited as I am a little new also. I just know that my USB drive/Mouse gave me trouble until I unhooked them, then rehooked them at the desktop. I was given that advice on this forum, somewhere??? If you look around for a while, you should see some more posts.
SirShaggy

---

### Post by exer! on 2006-10-02
Tried to unplug the scanner. In fact, I've left only keyboard and speakers plugged in. Nothing... Same problem...

---

### Post by CatKiller on 2006-10-03
> **exer! said:**
> Can PCI cards be a problem while configuring...?

Absolutely, they can.

I have no idea which of your devices might be causing you problems. You could try the [Linux Hardware Compatibility HOWTO]("http://http://www.tldp.org/HOWTO/Hardware-HOWTO/") or the [Hardware Compatibility List]("http://doc.gwos.org/index.php/HCL"), or search for other people with issues with NForce 2 motherboards, or... you get the idea.

---

### Post by exer! on 2006-10-05
I've spent the entire day plugging and unplugging devices and PCI cards. Not only that. I disconnected every single USB and Firewire device straight from my motherboard. And guess what... It didn't work... Yet again... I got so frustrated, that I wanted to quit the entire get-linux-on-my-pc idea.

Then, I decided to unplug the only thing that left unplugged during the whole test. I unplugged my hard drive. And guess what... It went pass that "Mounting root file sistem" thingy and started to load! I had a running Kubuntu LiveCD on my PC in minutes!

So, it was all cool. Everything works nicely. I've tried the Ubuntu LiveCD as well and it works smoothly. The only problem is: Where the hell am I going to install Kubuntu without the hard drive!!!

So does anyone have a clue now...? Is it RAID, maybe...?

---

