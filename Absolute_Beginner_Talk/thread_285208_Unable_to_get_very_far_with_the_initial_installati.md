---
title: "Unable to get very far with the initial installation"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by normanc on 2006-10-26
Hello all,

I used linux (Debian Woody IIRC) around 4 years ago, for 6 months or so, but I always kept switching back to windows to play games, and eventually just stuck with windows for one reason or another.

Now I don't play games really, and wanted to go back to linux, as apart from that, I liked the flexibility and control it gave me.

Anyway, looking at the linux distro rating site, I saw Ubuntu was the most popular distro these days, so I downloaded the x386 DVD .iso last night, burned it tonight and tried to install.

I booted from DVD, got to the first splash screen, chose the first option (install Ubuntu) and then the problem came. After the kernel and a few modules loaded I get a screen that says that X cannot start and do I want to view the logs, then do I want to view a detailed server log. The log ends with "Device not found (EE)" (can't remember the exact words) and "No screens found".

Looking in forums, I saw someone with a similar problem (it never said how he resolved it in the end) and so this led me to try "sudo dpkg-reconfigure xserver-xorg". Going through all the steps my graphics card (ATI X850), monitor (Panasonic plasma - for watching films and such like), keyboard were detected through the process. I also use a bluetooth mouse ,although when I ctrl-alt-del out I see that the bluetooth services module gets stopped, so I'm assuming that linux supports bluetooth fine. I think I have an old PS/2 mouse somewhere in the house if that is the problem I can go hunt it out.

I then got dropped back to the prompt. (or shell or whatever the correct terminology is) 

In the recesses of my memory, I remember the command "startx" so I tried that and get the same thing, "Device not found (EE)" and "No screens found". 

I'm at a bit of a loss what to try next. When I do "ls" all I see is "desktop".

Any advice or pointers would be appreciated. I used to be able to figure things out myself when I was younger, now I'm lost without google, hehe. 

Thanks a lot for reading and even more if you can help me.

---

### Post by ReaderRat on 2006-10-26
How much system RAM do you have? Your graphics card will have to be configured after installation, so you need 256M-512M RAM to install Dapper.

---

### Post by normanc on 2006-10-26
I have 2 gigs of system ram, I think my graphics card has 512 Mb.

---

### Post by ReaderRat on 2006-10-26
Some people have trouble with ISO burning. Did you burn the ISO file as an image (not data), and did you burn it slooowly (4X).

---

### Post by normanc on 2006-10-26
I did burn it at 8x, never had any problems before with that, I guess I can try burning it again at 2.4x, but the DVD is booting fine and loading  the kernel modules. The whole process falls down when x tries to initialise. 

Got me thinking that x didn't like something in my video setup, but when I did the reconfigure and everything was autodetected I was left at a loss. I guess I'll try burning again and see what happens, if not I can always download slackware and try that tomorrow. I did read one of the links in the stickies that said keep trying different distro's til you find one that will detect your hardware. Maybe I just need to do that.

Thanks anyway for the replies.

---

### Post by ReaderRat on 2006-10-26
You might download the Alternate CD and installing it in text mode.

---

### Post by benjaminwr on 2006-10-26
Hi! I have an Ati X800Xl. The problem is that the ati driver that Xorg has by default does not support the really new graphics cards that are availlable. There is an option to install in safe mode... this installs X using VESA as a driver... that should get you into your X session to be able to install the ati propietary driver from the repos... from there on... you have Ubuntu!

If you have already installed your system, try and change the diver in Xorg.conf to vesa and it should load up properly.

Cheers
Ben

---

### Post by normanc on 2006-10-27
I did suspect the graphics card was the problem, but when it was autodetected it threw me off.

Thanks for the heads up.

One more question, if anyone can oblige. What drawbacks (if any) are there to installing in safe mode? Based on my windows experience I'd imagine that this installs the system with generic bare bones drivers and then I will need to manually update the system to my hardware config at the end of installation? I've no problem with doing this, just want to ensure I head off on the right track.

Or, alternatively, would I be better to run the x-configure utility again and choose "vesa" as my video card driver as opposed to "ati" then I'd only need to apt the appropriate ati driver?

Thanks in advance.

---

### Post by IYY on 2006-10-27
> 
Or, alternatively, would I be better to run the x-configure utility again and choose "vesa" as my video card driver as opposed to "ati" then I'd only need to apt the appropriate ati driver?


If I were you I'd just use the command-line editor Nano to edit the xorg.conf file manually:

```
sudo sed -i s/'"ati"'/'"vesa"'/g /etc/X11/xorg.conf

```

should do the trick.

---

### Post by normanc on 2006-10-27
Using text mode install, I finally managed to get Ubuntu installed. Was a nightmare, had to open up PC and swap around CD ROMs and IDE hard disks as I had an IDE HDD on a PCI card that was unable to be detected ,then i learned that linux can only be installed if IDE drive is master (not slave) on my CD RDOM, but I finally got it installed!

I manually went into the xorg.cfg file using "sudo nano xorg.cfg" in /etc/X11 and edited out all the "ati"'s to "vesa"'s (I'm assuming the command you listed would have done it automatically, but I had no access to internet as I was at shell prompt and never wrote it down) and still I can't load x-windows. I still get an error message and dropped to prompt but this time (VESA) appears in the error message, so it seems I have managed to change the driver to VESA.

I also have ran the "sudo dpkg-reconfigure xserver-xorg" command and tried changing my driver to "vga" and "vesa" but both don't seem to write to the file. I get dropped out with an error message along the lines of "can't write to file /etc/x11/xorg.conf please run the command dpkg-reconfigure xserver-xorg to configure".

Well, this is the command I was running (as SU) and this is why I manually went into the file and changed it.

Could it be that linux simply isn't compatible with the ATI X850 graphics card? I'd love to hear from anyone who has managed to use linux with this card and how they have done it.

Or, failing this, how can I update my graphics card drivers from the shell bearing in mind I can't load x?

Any help would be aprreciated, it's been 2 nights now I've struggled on what should be straightforward process, but I'm making progress. Nothing like learning to walk again!

Thanks in advanec for anyone that can offer any advice.

---

### Post by normanc on 2006-10-27
I found this thread
[http://ubuntuforums.org/showthread.php?t=190133&highlight=x850](http://ubuntuforums.org/showthread.php?t=190133&highlight=x850)

which describes exactly my problem and after reading through it, it seems I did the right thing by changing the "driver "ati" " line to "driver "vesa" " but it seems I just needed a reboot with the system set to vesa mode. Sweet. Final straight now.

So you'd think anyway. Rebooted, crossed the fnigers hoping for x to finally start. 

This time I wrote down the error code I get. It seems like the OS is using the vesa drivers, but I get the error message "set VBE mode failed".

Last time I installed Linux I had none of these problems, it installed pretty easy, so I'm on totally new ground here. I really don't know what to do. Won't load with "ati" as the driver ,nor "vesa" nor "vga". 

Anyone suggest anything? I downloaded Slack yesterday, but I'm sure that x will balk at my card if I reformat my IDE HDD and install that too, so I'm at a dead end now.

---

