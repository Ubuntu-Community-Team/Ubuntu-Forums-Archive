---
title: "Continue problems with Ubuntu 6.06"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by rmaier on 2006-06-27
Have written to forum a couple of times. Took the suggestions from several response without success. So, back again. This time I have moved the computer to a house where I do have internet connection and can respond faster.

So here we go: I downloaded the upgrade off the internet 6.06, when i did I lost the internet connection. Tried several things and no results, tried to reload the 5.10 and now I can't get into ubuntu at all...i get the ubuntu screen, and then i get the 

Failed to start xserver (your graphical interface) etc.
further down, i get the message cannot open device xf86Openserial
/dev/wacom
fail to initialize core devices

x server is now disabled Restart GDM when configured correctly.

Goes to the next screen 

Ubuntu 6.06 LTS ubuntu tty1

ubuntu login:  (for me it is user)
password: ( for me it is password)

then to 

Linux ubuntu 2.6.15-23-386  #1
preempt TUE May 23 13.49.40 UTC 2006 i686 GUN/Linux

then the user@ubuntu:~$

I put in the sudu dpkg reconfigure xserver xorg  command but no result

said I need an action option.  if someone will respond...i should be able to enter it directly into and respond back if success...thanks......](*,)

---

### Post by LordRaiden on 2006-06-27
The command is 
 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
 
If it does not work then you will have to manually edit xorg.conf.
 
Post back if it does not work.

---

### Post by rmaier on 2006-06-27
posted the code

screen went to ubuntu configuration with message to select the desired X server driver.... with a list of drivers.....

vesa was highlighted, but the Motherboard book has an sis usb controller on the instruction pages about the PCI device....i tried changing it to both the
sis    and the sisusb    pressed enter,  got the command line, typed start x and got the failure to initiate

---

### Post by Apple 101 on 2006-06-28
You want to select your videocard driver.  For example: nVidia is nv.

---

### Post by FredB on 2006-06-28
Or nvidia if you installed the 3d accelerated server ;)

->[]

---

### Post by rmaier on 2006-06-28
okay I selected the nv  for the xdriver 
then it said select the video modes i want the X server to use
  already selected were  640 x 480 ,  600 x 800, and  1024 x 768

i pushed enter and it sent be back to the fatal server error
no screens found

X10 Fatal 10 Error 104

Can I try to reboot system with the Motherboard disc?  and if so...how do I get to a command line that is not a user@ubuntu  line..   i have that disc and the ubuntu 5.10 disc.... trying to avoid spending $165 dollars quoted to take it to the computer repair shop....

---

### Post by Apple 101 on 2006-06-29
Motherboard disc?  I don't understand what you are asking...

---

### Post by rmaier on 2006-06-29
The computer (AMD Athlon) came with a disc titled  Motherboard and the booklet says it has all the drivers and utility programs needed to properly run the bundled products.  

When I entered the code reconfigure, I selected vesa for the x driver and enter, then typed startx at the command, and it sent me back to the error message listed above , fatal error, and finally to the command line at user.

any ideas are welcome,  there must be a way to get back to the original setting. When rebooting it runs thru the ubuntu checks, the only system showed failed is the PCMCIA file....so it must be in there, just need the right configuration.....thanks for helping........................................

---

### Post by handy on 2006-06-29
What hardware graphics card / chipset (if it's onboard) do you have?

---

### Post by rmaier on 2006-06-29
good question and not being really sure i type in what the manual says about the chipset and maybe you will understand....Chipset on this motherboard includdes the SIS741Gx Northbridge combined with SIS964L Southbridge . 

Supports AMD Athlon XP/Sempron/Athlon Duron CPU with FSB up to 333MHz
Supports DDR 333/266DDR SDRAM
Compliant with Universal AGP 3.0 supports 1.5V AGP interface only
Supports AGP 8x/4X interface w/fast white transaction
buildt in high quality 3D engine
supports PCI power management configuration registers for suporting ACPI power down controller

SIS964L  SB
compliant with PCI 2.3 specification
supports full duplex 10base-T 100base-TX 1MB's & 10Mb's Home networking
 under graphics it says includes AGP 3.0

if you check out my other threads, you will see I have tried several ideas without much luck

---

### Post by confused57 on 2006-06-29
Deleted...you've already tried what I'd suggested.

---

### Post by handy on 2006-06-30
Can you give us the make & model of the Motherboard please?  

Does your monitor plug directly into the motherboard (usually next to a serial plug) or into card that sits at 90 degrees to the motherboard?  Further away from where most other things plug in?

Sorry, I'm not feeling too succinct today! :rolleyes:

---

### Post by rmaier on 2006-06-30
Make and Model of the motherboard is: 741GX-M Motherboard. "This motherboard is designed to fit the advanced AMD processors in the 462-pin package. This motherboard is based on micro-ATX form factor featuring the SIS741GX Northbridge and SIS964L  Southbridge chipsets. It accommodates AMD Athlon  SP/Senorib/Athlon/Duron Processors supporting Front Side Bus (FSB) upto 333/286/200 Mhz. In addition the motherboard has 2 built in 184 pin DIMM slots and the main memory is expandable to a max of 2GB

Processor: uses an AMD-462 pin Socket A that supports 333/286/200 MHz FSB  

I can type more out of the manual...but this is the info listed in the description section o the manual......

thanks

---

### Post by handy on 2006-06-30
I have just downloading the manual.

I will be off-line now for 12 hours or so. (Bed time here!)

Will continue tomorrow if still required.

Goodnight...

---

### Post by bobpur on 2006-06-30
Earlier you referred to a "Motherboard CD" and "Booting from a motherboard CD"
I don't believe you can boot from a "Motherboard CD" as it only contains drivers to enable SATA, RAID, and onboard audio and Graphics as well as some utilities and apps for a Windows install. 
You might be "choking the penguin" with this disk. As Ubuntu comes with loads of drivers and more available in other places, I'd forget the Motherboard CD, Do a full install (Not an upgrade) and see what happens.

---

### Post by rmaier on 2006-06-30
The Motherboard CD i was guessing from reading from the manual was like a restore disk  since the error messages kept saying devices not found, etc.

I tried to put in the CD install and CD live ubuntu 5.10 disc, neither would load, the system kept going straight to ubuntu load and then error messages.

I can get to Bios by hitting delete as the system starts, but I don't really know where to go once I am in there.

I can get to the restore kernel lines, 
GNU GRUMB version .95  638K  lower   228288k upper

Ubuntu, kernel  2.6.15-23-386
           kernel   2.6.15-23-386(restore)
           kernel   2.6.12-10-386
                        same           (restore)
           kernel   2.6.12-9-386  
                         same          (restore)
which after I highlight and enter one of these it runs through several setup screens, but ends up with the error messages again..... 

when the error for the xserver window displays it has the following printed on it

X window stystem Version 7.0.0
Release Date
X Protocol Version 11, revision 0. Rlease .7.0
Build Operating System Linux 2.6.2 i686
Current operating system Linux ubuntu
2.6.15-23-386


Module Loader Present
Marker:  followed by markers
(==)log file "/var/log/Xorg.0.log"
(==)using config file : "/etc/X11/xorg. conf
(EE)xf860penserial -
      no core pointer
      fatal server error
      fataled to initialize core devicfe



So is there any hope of getting the system up and running without having to take it out to a repair shop....which like for many people is cash I don't have....thanks to everyone who has replied ..........

---

### Post by siccness on 2006-06-30
[QUOTE=rmaier]

I can get to Bios by hitting delete as the system starts, but I don't really know where to go once I am in there.

[/QUOTE]

Search around there and try and find Boot Priority/Sequence, and select CD-ROM to be first.

---

### Post by rmaier on 2006-06-30
hey hey, found the boot priority , changed to cd-rom, 
put the ubuntu install CD in the drive  and

got

ubuntu screen says the default installation is suitable for most desktop.....
Press F1 for help and andvance installation options

To install only the base system type 'server' then enter
for the default system press enter

boot: 


what do you recommend? using the default says will lose existing software and data, which is okay as long as the system will run and can use internet, will it have a driver to connect to internet......

and if this does the trick, do I go back into Bios and change the priority to the previous setting or will this automatically change....probably a stupid question...but hey I have asked a bunch of them lately and used to it.....
thanks for responding

---

### Post by gr0kzer0 on 2006-06-30
You are better off doing the default installation.  This will install everything you need.  You can reset the BIOS settings after if you want to.

---

### Post by rmaier on 2006-06-30
thanks,  

using default install now, waiting for it to run thru the disc


thanks for responding.....

just finished , and have the 5.10 back and running...thanks....
now to take the computer to my house and see if I can connect to internet, and use my printer, may have to post back for help if i cannot use these as before......I will think twice before I try update to the 6.06...maybe the bugs will be worked out before I try to upgrade...thanks again....

---

### Post by dirtvoyles on 2006-07-01
I am getting this same output when trying to run startx on my Dell 233XT. Does anyone know how to setup/correct X to work properly with this?

I'm too new to know how to use CLI to check my onboard video. You guys seem to be helpful, so thanks in advance.

PII @ 233. 64MB RAM (Fluxbox is my friend)

---

### Post by bartbes on 2006-07-01
That error of "/dev/wacom" is that in your xorg.conf file the (probably not installed) wacom tablet is referred as plugged in, AND as essential, it's easy.
```

sudo apt-get install nano (or you can use vim or whatever you want)
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo nano /etc/X11/xorg.conf

```
there put a # in front of every referrer to a wacom device.
and that's it
NOTE: It's also possible to delete it, but be careful with that and be sure that you've backed up properly!

---

### Post by dirtvoyles on 2006-07-01
Hokay, when I comment the wacom lines out, it won't startx even with sudo.

I get the error: no screen (or display, I can't remember) found

I went back in and removed the comments, and now it will work with sudo startx.

---

### Post by enyaw on 2006-07-01
I'm sorry to ask this, but.  Is your computer set up with NVIDIA?   

I had a similar problem when installing dapper on an old Compaq DeskPro until finally I ran a program called EVEREST Home Edition [google it].  EVEREST gave me an eight page printout of hardware.  Everest listed Video Adapter make and model and named the 3D Accelerator.  With this information, I cleaned the hard drive and installed dapper.  Dapper is great:D 

The computer wiill need Windows to run Everest.   I know it's a lot of aggraivation, but it was worth to me:D 

Hope this helps:D

---

