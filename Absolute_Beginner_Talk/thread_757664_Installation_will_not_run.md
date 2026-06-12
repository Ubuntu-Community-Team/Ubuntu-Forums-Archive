---
title: "Installation will not run"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by mattywarr on 2008-04-17
Hello!

I'm a Linux n00b, and have been trying to install Ubuntu for some days now but can't seem to get it installed. I cant even get the installer to run!

When i Boot to the CD I get the Boot menu. Whenever I try and boot the live CD it gets the splash screen with the logo and the sliding status bar but then just eventually takes me to a black screen with a flashing cursor.

So I tried to download the 8.04 Beta and managed to attempt the installer launch in safe graphics mode, just in case. And this time it actually started throwing me errors - which I have no clue about! The error kept repeating that It couldn't load the driver or needed a firmwareupdate for my wireless adapter and referred me to Linuxwireless.com to get the updates.

But I have no clue how I'm meant to get the installer working.

Ideally, I'd like it to just skip the wireless device altogether and see if I can get it working without it (I have an on board lan too). is it possible to do this?

Its an
Acer Aspire 5020 Laptop
120gb Drive
1gig Ram
Already running windows XP - Trying to get a dual boot going.

I've tried 2 mirrors of 7.10, bothe the live and alternate versions, and have also tried both the live and alternate beta 8.04

Any ideas? Any help is greatly appreciated.

Matt

---

### Post by sharks on 2008-04-17
Do u have any Ubuntu distros installed in your system?

---

### Post by mattywarr on 2008-04-17
Hi, no this is my first attempt. 

The only Ubuntu software I have is the ISOs i've downloaded in Windows.

---

### Post by northern lights on 2008-04-17
Since you're running XP and posting from it also, an option worth a try might be to install from the net, i.e. without a CD.

Download one of the two (depending on whether you have/want a 32 or 64 bit system) .exe files from [here]("http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=243411"), run it and reboot. A bootmenu should appear with the option or either booting Windows or installing Ubuntu. If you now have a wire connected to your ethernetport, it should install happily from there and you can worry about wireless from within Ubuntu.

If you choose to opt for this, just make sure to select to install "Ubuntu Desktop" at the end of the installation, otherwise you'll be left with commandline only. Anything else, can be added from within Ubuntu, again.

---

### Post by mattywarr on 2008-04-17
Brilliant - great idea. I'll give that a go :)

---

### Post by northern lights on 2008-04-17
Good. Report back with further issues or to simply testify that it worked.

Ever since I found this option, I've never touched a CD again, though I installed Ubuntu on a good number of comps since...

---

### Post by mattywarr on 2008-04-17
Definitely will ;)

Its a very neat way of installing, especially as I've spent the past week downloading ISO after ISO after ISO!

I'm keen to move all my operations to Linux and learn a lot about the OS in the meantime. Hopefully my next post will be from Ubuntu!

---

### Post by mattywarr on 2008-04-17
I'm not having a lot of luck...

The setup is great and easy - Its a fantastic way to install an OS.

But it reaches 82% "Installing the Kernel - Retrieving and installing linux-generic" then my machine crashes. And by that stage the MBR is ruined so when I boot it tells me Missing Operating System. I then have to fixmbr to get things going again.

Seen this happen before?

---

### Post by northern lights on 2008-04-17
Wicked.

Your machine crashes without any error message?

To the point where you have to do a hard reboot?

---

### Post by mattywarr on 2008-04-17
Crash might not be the best word for it. This time I spotted some black text at the bottom of the screen. Thats there for a second then the machine powers off completely.

Running the install again now to try and get the detail.

---

### Post by northern lights on 2008-04-17
I hope there is some message, otherwise I'm dumbfounded.

I've literally done this twenty times, on about fifteen different comps around campus. It has never failed.

Really sorry to hear you're having such bad luck.

---

### Post by spiderbatdad on 2008-04-17
try adding some special boot parameters to the kernel line from the grub menu. Press F6 from the live cd at the grub menu...delete 'quiet splash' from the end of the line, and replace with 'noapic nolapic vga=791' (no quotes.)

---

### Post by mattywarr on 2008-04-17
I'll give that a try later.

It seems that it jumps from the 82% screen, then the black screen appears with a line of text which (I think) says Starting Sigterm to end processes or something like that.

I'd be half tempted to say its the machine, but it crashes at the same point every time - its very weird.

---

### Post by mattywarr on 2008-04-18
Ok, well I tried the option with the boot parameters - same thing happened.

Is there some sort of boot parameter which will allow eth0 to be ignored and skip straight to eth1?

Matt

---

### Post by mattywarr on 2008-04-18
OK, I've found a boot parameter disables the network completely "nonet" - This was from a different distro of Linux but i'm hoping it'll still work? 

Will basic ubuntu install from the CD as is or will it need to connect to an online repository during it?

Thanks,
Matt

---

### Post by mattywarr on 2008-04-18
> **spiderbatdad said:**
> try adding some special boot parameters to the kernel line from the grub menu. Press F6 from the live cd at the grub menu...delete 'quiet splash' from the end of the line, and replace with 'noapic nolapic vga=791' (no quotes.)

Yes! That did the trick :)

Now just to install it successfully... My ISO was corrupt...

---

