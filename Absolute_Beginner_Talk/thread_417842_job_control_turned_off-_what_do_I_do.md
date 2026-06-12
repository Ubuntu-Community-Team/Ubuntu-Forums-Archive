---
title: "job control turned off- what do I do ?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by abrand888 on 2007-04-21
Hi,

I have a DELL GX110 computer with 512mb and Memtest verified my memory is good. It is a 

863.8MHZ speed.
chipset i810E


I get the screen BUSYBOX V. 1.1.3 (Debian1:1.1.3-3Ubuntu3 Built in shell (ash)
enter help for a list of built-in commands.

/bin/sh :can't access tty; job control turned off
(initranfs) [87.884900] SDC assuming drive cache: write thru
[87.892894] sdc: assuming drive cache: write thru

I tried 7.04 in my office and it loaded properly but not in my house. What can I try to get 

it loaded properly and if I get it loaded properly, will it find my Wireless Lan USB 2.0 

adapter I am using the Engenius adapter with a 12 dbi Cantenna connected directly to this 

device, I am giving it its own power through a external power supply and the output of the 

7-port device goes into my USB 2.0 card. In Windows it works well.
Thanks

---

### Post by leibowitz on 2007-04-21
I don't know about the Wireless device, and not sure about the installation error.

When do you see those messages. What CD did you used, and did you install it. Otherwise try to boot the live-cd desktop to see if it boots before installing it.

---

### Post by abrand888 on 2007-04-22
Hi,

I see the errors while it starts to boot up. Once it it sees these errors, it stops cold and suggest using HELP but I don't know which commands to use to continue the booting up. I am trying to use as a live cd. It worked without a problem in my office. I downloaded the iso file and burned the image to a cd which doesn't get to far in my house where I would like to use UBUNTU> If I can't boot up then wireless is superflous at this time. I even tried booting inside Windows and it would not boot.

How could I turn on tty job control ? I tersted the cd for integrity and it came out very good. 

Thanks for answering so fast. Appreciate it.

---

### Post by leibowitz on 2007-04-22
I don't know how you can turn on tty control. That's not a common error. If you see this, probably something goes wrong. My job is to find what is causing this. Focusing on this error may or may not help you.

As far as I understand, you are using the Desktop (Live install) CD. Is that right.

Can you give more details about your Hardware configuration, principaly your Hard Drives setup. I'm checking the "DELL GX110" details right now.

---

### Post by leibowitz on 2007-04-22
I learned that many people installed linux (many different distributions) on this hardware. So the default HW should not make this crash.

Do you have any additionnal video card installed in here. I know that you should have an Intel i810 (integrated chipset). But do you have one more, like an ATi or Nvidia or whatelse.

---

### Post by abrand888 on 2007-04-22
My GX110 has 512mb ram, the i810 chipset and the motherboard has built in video. The original drive is 9.5gb but I am using a USB 200 GB as drive F: and I try and place all programs on the 200 gb drive rather than the 9.5 gb drive because it is filling up and I don't feel like taking the unit apart and replacing it with a 60 gb drive. I use this old system for surfing and would feel more comfortable using Ubuntu rather than Windows XP.

Does  this help you in figuring out what I am encountering. As I stated before, my office is a old AMD system and Ubuntu loads and works on line but I can't take it home.

Arthur

---

### Post by leibowitz on 2007-04-22
Did you try to boot the live cd without the USB drive connected. It may be related to that. But I'm not sure at all.

---

### Post by abrand888 on 2007-04-22
I tried it with the USB drive turned off and got the same error. I forgot to tell you that my monitor is a LCD Optiquest Q9 monitor.

Perhaps the Dell doesn't like Ubuntu ? I find it hard to believe . Did you find out something about the GX110 computer.
My best

---

### Post by leibowitz on 2007-04-23
I don't think so. What I found is that some different people seems to have installed successfully on the same hardware. 

So maybe it's related to your monitor. But I can't be sure as I don't exactly get where it hangs.

Could you be more precise, like saying how many seconds separate the boot from the error message. Are you seeing any progress bar while it boots. Explain everything you see before the error.

---

### Post by abrand888 on 2007-04-23
It takes bout 45 seconds to see the error. When Ubuntu is loading the Kernel, a black line goes thru the blue bars and I also see some sort of a line broken in colors at the bottom of the screen.

I am using bios A09. I have the same Dell GX110 with a compaq monitor at work and it didn't load and I got different errors, never the errors I listed before. Evidently tty is very important and one needs to load somehow tty in order to get further.tonight I got different errors as far as numbers go. I got 72.033140 and 72.035009 and when I booted in regular mode I got 103.870527  and 103.878527. I think it might mean something.

busybox is multi channel something. It does not a difference if I boot is safe graphics mode or regular Live CD I get same lockups.

Arthur

---

### Post by ludatha on 2007-04-25
I cant be your moniter, the same problem happens to me, but I'm installing it on my Playstation 3

---

### Post by leibowitz on 2007-04-28
Some update. 

I managed to get the same error, but got it at the very beginning of the booting process. I had this with a semi-working DVD reader. That was causing I/O error messages. 

Anyway, please check your CD, and your CD/DVD reader/Writer. Check the .ISO file you downloaded with md5sum. And select "check cd for defects" on the CD boot menu. (I know you already did this, so adjust at your convenience).

When you are done, if you still have the problem then know that what you see as an error is just a warning message.

You should have a prompt like this.
```
(initramfs) 
```

Here you can start commands, but unfortunately there isn't many commands in this busybox environement.

Have I suggested to boot with an extra kernel option yet, that is **single**. Just press F6 when you see the boot menu from the Live-CD and add **single** at the end of the line.

Boot with this and report the results in here.

---

### Post by nitsthegame on 2007-04-28
the problem os with the motherboard 

intel boards have a jmicron contoller and hence  create a problem for live cd

either go for a usb cd rom or try ubuntu 7.04
 it worked for me

---

### Post by abrand888 on 2007-04-30
Hi,

I checked the disk and it states it is ok. It had to be ok because it recognized my AMD system in my office and I was surfing the Internet at this computer. My problem is with the DELL GX 110 computer.

I had the Firewire External Memorex DVD writer on and the USB drive on.I wasn't able to input F^ single. I did see right away ISOLINUX 3.11 Debian 2007-03-12 copywrighted 1994 -2005 H.Peter Anvin and then it started loading. As soon as it started booting I hit F^ and saw a number of options only once and then never again. I saw the screen casper initrd=/casper/initrd.gz quiet splash and typed in the word single and then it started loading.

With the USB drive on and the Memorex External DVD writer on, I go same screen 
BusyBox V1.1.3 (Debian1:1.1.3-3Ubuntu3(Built in Shell)
Enter Help for a list of built-in commands.
/bin/sh:can't access tty;job control turned off.
I got (initramfs but got [92.703760] sdb: assuming drive cache write through [92.705752] 
assuming drive cache:write through.

BUT If turned off both USB and Firewire DVD writer, I never gotthe brackets with the above numbers.

I didn't check the MD%sum because I don't have the number. I assume that this disc is good 

especially since it worked on my AMD system.

Hope all of the above gives you some clues. 

Arthur

---

### Post by leibowitz on 2007-05-01
Yes it does.

Could you please confirm that you are loading the Live CD, and if you do then are you using any external drive to load it.

Please try, if possible, to load the live Cd with an internal drive, and disconnect any USB/External drive before booting.

I want to be sure that no inside component are causing the problem.

---

### Post by abrand888 on 2007-05-02
Hi,

I selected F1 and it stated that it was a live cd for Ubuntu. As soon as Ubuntu is loading I get this screen :
start or install Ubuntu
Start Ubuntu in safe graphics mode
install with driver update cd  I don't have this cd.
check cd for defects
memory test boot from first hard drive which is drive C: inside the DELL

I am using the cd player inside the Dell.

If I turn off the external dvd writer and the usb drive, I don't get busybox.

Please tell me what else I could try. Maybe we will get it working after all.

I just realised that I never turned off the external 7-port USB power supply unit. Will try it now.

results same screen with all the units turned on

---

### Post by jonbartlam on 2007-05-02
I have just installed Ubuntu on my system (dual core, 7900 geforce, 2GB memory and the worst possible hard disk combo EVER for Ubuntu).

Here is my hard drive set up:

ON JMICRON CONTROLLER:
120GB seagate IDE - Various documents and the second drive for linux
Toshiba DVD rewriter - A cd rom drive

ON SATA:
74GB Raptor - Windows documents and office apps
Toshiba Hard drive 200GB - Windows partition, Games for windows, and Linux root and swap

ON USB:
Western digital 120GB Mybook

See what I mean? I installed everything FINE then on restart the error came up. The splash screen came up but the bar was frozen. after about 5 minutes this came up:

/bin /sh: can't access tty; jobcontrol turned off

I looked into fixing this to no avail. BTW, I'm very experienced in windows but am a complete 'noob' when it comes to linux. HOWEVER, from looking at other peoples possible causes I have found some answers.

If you have a hard drive on the JMICRON controller, you most probably have problems with most linux distributions (I tried SUSE and had to not install it ont he IDE, as it booted Micron controller AFTER it had booted). To solve my UBUNTU issue, sometimes if i turn off the external hard disk it boots. When in I can turn it back on again. if that doesn't work, for some reason if I go into my BIOS and alter the boot proirity of the hard drives (obviously, keep the one that is supposed to boot first!) it usually does the trick. Finally, if that doesnt work I have to disable the hard disk int he bios ont he second SATA channel and it works....its very bizare.

Hopefully, with this information some people might be able to boot more successfully. This is a shame because I have been using UBUNTU to replace windows on ym work laptop. I find it actually BETTER than windows.

---

### Post by abrand888 on 2007-05-02
Hi,

I changed the order from booting diskette to cd-rom, diskette and then hard disk-same errors 

like before.
I turned off in the bios USB emulation and controller in Bios-got same errors as before.
I turned off USB power supply, usb drive and firewire external writer-got same errors.

I now tried something very different I turned off the IDE controller and rebooted. I kept pressing F1 to continue but it would continue, so I went in to F2 setup, turned on the IDE controller and with all the USB devices and Firewire dvd writer, Ubuntu booted ever so slowly and there was a brown screen. Before it booted up it kept accessing my External DVD writer.It recognized my two hard drives, the internal and internal but only once. I then rebooted three times and could never get it to boot again.

So I tried a fourth time turned off the IDE controller, turned off the machine for a few minutes, rebooted in safe graphics mode, and it slowly booterd up but when I tried rebooting again, I got the same errors as in the beginning. As it was booting I got a screen of many colors and when I hit the enter button it kept loading. 

There was no way to replicate the boot process.

What is the driver update CD ?

I hope all of the above means something. The controller seems to be the culprit at this time. This DELL has only two slots and the first slot has the firewire card and the second slkot has the USB 2.0 ADS Tech card .

Look forward to your next reply.

Arthur

---

### Post by Cannaregio on 2007-05-07
Happened to me too once.
This different solution worked for me, so I'll bump it here as well. It may help.

This error "BusyBox /bin/sh can't access tty" and so on is mostly due to the fact that you have a XP partition and dual boot and you just pulled off a USB stick without due ejecting either in your XP partition or in Ubuntu itself.

Solution is to live boot from a feisty live cd, and then terminal, and then (not really necessary) check with system --> administration --> gnome partition editor, if you want to check it's a sda1 and see what happens, but the important life-saving command is:

```
sudo e2fsck -y /dev/sda1
```

the corrupted drive will be checked and healed.

It worked for me, your mileage may vary.

---

### Post by abrand888 on 2007-05-07
I have only one partition on my hard drive and I am booting off a live cd. I didn't install Ubuntu because I can't get past ther error. The only time I got it booting was trning off the controller on the motherboard, it wouldn;t boot up at all, gave up, turned the controller on and the live cd booted it. I tried it several times and couldn't replicate my initial success.

I don't understand what you are saying about I just pulled it off a USB stick. When I had one time success my USB drive was connected and Ubuntu recognized the USB drive.

Running the Live CD isn't successful yet. There is something on the Ubuntu cd that doesn't like the DELL GX 110 computer. I think it might be the controller but I don't know how to get around the controller problem yet. Is there a command when I get my error to get the cd to continue running ?

I would like to get into terminal mode but I can't get there yet.

---

### Post by abrand888 on 2007-05-08
I think my best solution to getting Ubuntu Live to work is to replace the motherboard with another motherboard that doesn't have jmicron controller built in. Without the present motherboard controller I was able to boot the live CD version once.

I have another issue even if I was to find and install another motherboard. I am using presently a Wireless Lan USB Adapter to a yagi antenna. The manufacturer is the Engenius USB adapter said he doesn't have a driver for Linux so I would need a lot of help in finding some kind of a generic Linux driver that will work with the new system .

At this time my access point is on my second floor of my house and my signal strength is quite decent. I tried the Live CD on my other system in my basement and it booted right into live Ubuntu cd. I tried the wireless Lan USB Adapter-EUB-362 EXT amplifier which is 200mw amplification, it picked up a signal but constantly faded in and out. If I could get the signal of my second floor down into my basement then I could forget replacing a motherboard on my DELL GX110 and have the best of both worlds.

I am not using a router at all.Although I have a router, I found out accidently that not connecting the router I gotr a signal  I just connect my 16 dbi yagi antenna to the WirelessLan USB adapter and the other side is a external USB 2.0 7-port USB  power supply and the output goes into my USB 2.0 adapter card. I turned off the USB connections in the bios. If I connected the wireless usb adapter directly to my 2.0 USB card, t couldn't hold the signal and faded in and out but with the external powered USB adapter, the siignal is rock solid.

I look forward to your thoughts. I believe my problem might be the same problem to others who would also like to try and evaluate Ubuntu.

Thanks

---

