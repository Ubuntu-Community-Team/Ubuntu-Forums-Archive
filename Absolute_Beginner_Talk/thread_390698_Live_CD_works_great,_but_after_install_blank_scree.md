---
title: "Live CD works great, but after install blank screen on startup"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by Jredrum on 2007-03-22
Hello, 

I tried out using Ubuntu and loved it. I used the live CD and everything worked very smoothly. I decided to install it off of the desktop install icon. I went through the steps and chose erase HD for the partitioning question. After the installation was finished I extracted the Live CD and rebooted the computer. Everything seemed to be going fine, but it then comes to what seems like a DOS prompt. I cannot figure out anything from there. Is there something wrong, because I though it should come to a login screen. Or do I need to type something? I am not at the computer now, as I am at work. 

It shows this

<root#joe-desktop> (or something very similar to that)

Thank you in advance as I appreciate any info on this.

---

### Post by chewearn on 2007-03-22
Pay close attention to what happened just before ubuntu dropped to text console.  It is likely you get xserver error, but you should see a xserver error box (if that is true).  It ask you if you will like to see the error message; which after you scroll down you see "no screen found"?

If the above is true, then in the text console, login into the user you have created when you install.  Then type in this:
```
sudo dkpg-configure -phigh xserver-xorg
```
You will then be asked questions about your video hardware.  Search the forum or google what you should select for your particular video card.

---

### Post by Jredrum on 2007-03-23
OK, now it's different. 

It will not load anything at all. I tried reinstalling the disc, but it starts up and gives me the 2 sec. to hit esc, and then goes to a blinking cursor in the top left corner, then nothing. Just a blank screen.

Again the Live CD is working fine, which is why it confuses me on why it wouldn't work when installed. I must be doing something wrong.

---

### Post by Jredrum on 2007-03-23
Here are some specs for my machine as well.

Description
Intel Celeron 2.5 GHz Processor
768 MB PC2100 DDR Memory
40 Gigabyte Hard Drive
48x CD-RW Optical Drive
Integrated AC'97 Audio
Intel Extreme 3D Graphics with 64MB Shared Memory
v.92 Kbps PCI Modem and 10/100 Ethernet
Six USB 2.0 Ports
Three PCI Expansion Slots (Two Available)
Windows XP Home Operating System

---

### Post by DennShin on 2007-03-23
I assume the 2 seconds to hit escape you mention is your grub.  Hit esc and select <safe mode>. 

that should drop you into the CLI as root.  Then do as "AstalaVista" stated. 

```
dpkg-reconfigure xserver-xorg
``` 

If you still receive a blank screen after setup.  During the resolution portion of the setup select 1024x768 as your max.  I know this solved my X problem the other day.  

HTH
-Eric

---

### Post by docshawnc on 2007-03-23
Is this an IBM Think pad by any chance?

---

### Post by Jredrum on 2007-03-23
> **DennShin said:**
> I assume the 2 seconds to hit escape you mention is your grub.  Hit esc and select <safe mode>. 

that should drop you into the CLI as root.  Then do as "AstalaVista" stated. 

```
dpkg-reconfigure xserver-xorg
``` 

If you still receive a blank screen after setup.  During the resolution portion of the setup select 1024x768 as your max.  I know this solved my X problem the other day.  

HTH
-Eric

Thanks, I will give it a go when I get home. 


To answer the other question, no it is not an IBM thinkpad, it's a shitty Emachines T2542. lol

---

