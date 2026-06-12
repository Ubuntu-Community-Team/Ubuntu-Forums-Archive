---
title: "MacBookPro5,3 and Ubuntu 14.04.3 LiveCD - hangs"
date: 2015-09-27
forum: Apple Hardware Users
---

### Post by Carty_Ellis on 2015-09-27
[COLOR=#000000]I am trying to boot from a DVD. [/COLOR]MacBookPro5,3[COLOR=#000000] 4GB RAM OSX 10.10.5 with Bootcamp install of Windows 10.[/COLOR]
[COLOR=#000000]DVD has 14.04.3 AMD64 ISO. [/COLOR]
[COLOR=#000000]Used Disk Utility to burn the .iso to the DVD - used 2x speed. [/COLOR]
[COLOR=#000000]Holding down Option Key on computer start up - seeing two DVD's - Windows and EFI Boot and and three Hard Drives MacintoshHD, Windows and Recovery..[/COLOR]
[COLOR=#000000]Select EFI boot and screen comes up to allow Try without installing. Select that and enter.[/COLOR]
[COLOR=#000000]Ubuntu screen comes up, dots cycles, and eventually stop with all dots red. I let the computer sit an hour and nothing changed.[/COLOR]

[COLOR=#000000]MacBook Pro (15-inch, Mid 2009)[/COLOR]
[COLOR=#000000]2.8 GHz Intel Core 2 Duo[/COLOR]

[COLOR=#000000]4 GB 1067 MHz DDR3[/COLOR]

[COLOR=#000000]NVIDIA GeForce 9400M 256 MB[/COLOR]

[COLOR=#000000]Tried EFI boot and check disk - did a lot then stayed on checking file system 15 minutes.[/COLOR]

[COLOR=#000000]??[/COLOR]

---

### Post by este.el.paz on 2015-09-28
> **Carty_Ellis said:**
> [COLOR=#000000]I am trying to boot from a DVD. [/COLOR]MacBookPro5,3[COLOR=#000000] 4GB RAM OSX 10.10.5 with Bootcamp install of Windows 10.[/COLOR]
[COLOR=#000000]DVD has 14.04.3 AMD64 ISO. [/COLOR]
[COLOR=#000000]Used Disk Utility to burn the .iso to the DVD - used 2x speed. [/COLOR]
[COLOR=#000000]Holding down Option Key on computer start up - seeing two DVD's - Windows and EFI Boot and and three Hard Drives MacintoshHD, Windows and Recovery..[/COLOR]
[COLOR=#000000]??[/COLOR]

@C_E:

OSX boot manager sees linux as "windows" . . . put yr ubuntu 14 DVD in the optical drive and reboot, try your 'option key" method, but next time select the "windows" DVD image and see how that works.  Also, did you check the md5sum number of the file before you burned it?

e..

---

### Post by imattux on 2015-09-28
Pls disregard the previous response. If you're getting to the "Try Ubuntu without installing" screen - that is the Grub bootloader screen, btw - then you have made the correct choice. Este is either taking a completely wild guess or didn't read. Either way, his suggestion is not going to help you. 

I suspect the problem is your video card and there are ways to work around it temporarily and fix it permanently.

Here's what I'd try: when you get to the Grub screen that offers you the choice to install or try without installing you want to edit the "Try Ubuntu without installing" line. Do this by selecting that line, but instead of pressing Enter, hit the "E" key (for "edit" - very logical ;-))

This is the line of code that tells your Mac where to look for the files to startup in Ubuntu. The one we're going to edit is this one:

```
linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash
```

Use the arrow keys to navigate to the end of the line and replace "quiet splash" with "nomodeset", 

```
linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper nomodeset
```

then hit F10 and watch a few hundred lines of text fill the screen. "Quiet splash" suppressed all the output from the boot process and displays a splash screen (again, logical...). By passing the "nomodeset" argument (these are terms you'll become  familiar with if you run Linux) we are telling the kernel (the very core  of the OS) not to worry about video (don't set the video mode yet)  until it gets further in the boot process when we can load a better if  not ideal driver for your particular card. Hopefully after all the text, you'll get to the Ubuntu desktop and you can try it. If not, the last few lines of text will help to track down the problem.

LMK how that goes. That is a temporary fix. If you decide you're going to install and run Ubuntu, we'll need to try a couple of different drivers - there are both open source and proprietary drivers available - and see which works best. Assuming you do get to the desktop and you start trying things, remember that there are 2 things dramatically affecting your performance: 
1. You are running from a DVD - WAY slower than a hard dive and,
 2. You are running without any hardware acceleration from your video card, so everything draws slowly (a Youtube video might be choppy) and anything 3D will definitely be way slower.

---

### Post by imattux on 2015-09-28
> **este.el.paz said:**
> @C_E:

OSX boot manager sees linux as "windows" . . . put yr ubuntu 14 DVD in the optical drive and reboot, try your 'option key" method, but next time select the "windows" DVD image and see how that works.  Also, did you check the md5sum number of the file before you burned it?

e..

este - the OP is getting as far as the Ubuntu splash, EFI boot was the correct choice...

E ;-)

---

### Post by Carty_Ellis on 2015-09-28
Thanks!!  That worked!  I did not have the Ethernet Cable plugged in so it was offline, but LibreOffice worked, etc.  I did see reference to going to a website for new drivers during the boot process, but the screen went on before I could write down what that was about - Xcode maybe?

I will ask two more questions.  

1.  What do I need to change to make the wi-fi work?  I tried to add a wi-fi connection with the SSID, but it seemed I needed something more.  It did not work.

2.  I have a LaCie external HD that I can connect vis USB or Firewire.  Can I install Ubuntu 14.04.3 on that drive connected via Firewire?  Will it appear in the boot menu with the Option key held down?  I am hesitant to put Ubuntu on the internal HD because I have OSX 10.10.5 and Bootcamp setup.  I have Windows 10 in Bootcamp.

Thanks.

---

### Post by Carty_Ellis on 2015-09-29
I have connected the Ethernet Cable, re-booted, and am answering this on Firefox in Ubuntu 14.04 LTS from LiveCD on my MacBookPro5,3.  The video card - when I do About This Computer says:  Gallium 0.4 on llvmpipe (LLVM 3.6, 128 bits) and the disk 1.9 gb.

I assume the disk is actually RAM. 

I did video record the screen as it was booting, so I can pass along anything you want to know.

---

### Post by este.el.paz on 2015-09-29
> **imattux said:**
> este - the OP is getting as far as the Ubuntu splash, EFI boot was the correct choice...

E ;-)

@imattux:

I'm glad it worked out, just like with one of your posts that went unanswered for awhile, I was just trying to go with the simplest idea first.  It shouldn't take a whole lot of boot params just to boot a LiveDVD.  However, rather than stating "please disregard the previous post, that guy doesn't know what he is saying" . . . you could have simply posted your suggestion and let the OP work it out for himself . . . .  If you continue to post on the forum, you will begin to see that the same questions, problems repeat over and over, and the information provided doesn't always make sense, and often the problem is a simple one, with a very simple solution.  

e.e.p.

---

### Post by luciano.x on 2015-09-29
I suppose you're installing it so just a few hints.
Be careful when you create/resize partitions because you're probably using Hybrid MBR. I recommend using OS X disk utility to set up your partitions just to be on the safe side.
Ubuntu won't easily show up when you hold alt/option on boot after installing. No worries though. You should proceed to check how it works i mean maybe Ubuntu installer will set up GRUB as default boot manager so you'll have to hold alt whenever you want to boot OS X/Windows.
Oh back up your important data.
Good luck!

---

### Post by imattux on 2015-09-30
[QUOTE=Carty_Ellis]When I added Ethernet cable, Ubuntu runs fine and YouTube Videos work fine also.

You sound quite competent in this. Can you tell me simply how to install on an external Firewire Drive? I "assume" the option key trick will see the External Firewire Drive.

I have Bootcamp installed, and Windows 10 under Bootcamp, OSX 10.10.5 as MacIntoshHD (default boot). I am not sure I want to mess with boot sequences.

When I plugged in the firewire drive, I believe is became /dev/satc (the Macintosh HD and the Bootcamp partition were I believe /dev/sata and /dev/satb.

I started the install, and I had the feeling it sought out the external drive, but I stopped before I said use whole disk, because I could net see for sure that it was talking about that drive.

Thanks in advance.

Carty Ellis[/QUOTE]

"...simply install to the external firewire drive..." that's funny...

Ok. If I'm understanding you, passing "nomodeset" solved the problem with your video card. If you're ok with your video performance, we can forgo the installation and testing of various drivers. Booting from an external firewire drive will work just fine using the "option key at startup" method. Let's use the proper terminology and call it "EFI booting"

Assuming that your firewire drive is not the same size and brand of drive as the internal drive, it should be easy to identify which drive is which by size and manufacturer. I'm going to assume that you are going to use the whole firewire drive for Ubuntu. If not, everything applies to the partition you choose rather than the whole drive. Just be sure you know which partition is which and double-check before you move to the next step. As you've seen, Ubuntu does not name drives in the same way the OSX does. Size is the best way to know what is what.

So, booted into Yosemite, connect the firewire drive and open Disk Utility. You can either create a small transfer partition or not, but you want to erase and re-partition the drive one way or the other so that you have a clean, fresh GUID formatted drive (that will be default, but make sure to check the "options" button before erasing/partitioning. While you're there, you can note the manufacturer and size of each drive and partition so you're sure you choose the right one when you install. If you do want a shared partition, you should choose fat32 so that Ubuntu will be able to read and write to it. Name the Ubuntu partition Ubuntu and the other something like Shared or Transfer if you want it. It doesn't matter whether you choose Mac OS or Windows for the Ubuntu partition, it's gonna be overwritten.

At this point, I'm going to refer you to Jason Heeris' totally awesome instructions found [here]("http://heeris.id.au/2014/ubuntu-plus-mac-pure-efi-boot/#installing-ubuntu"). I had to make a few modifications, follow along and take notes ;-)

Reboot using the Ubu DVD (don't forget "nomodeset") and when you get to the desktop, choose install. The installer will tell you it's found multiple OS installed and ask you what to do. Choose "Erase and Install" - don't worry, it's just going to reformat and install on the firewire drive that we choose in the next step. At the next step, there will be a pull down menu that asks you where you want to install the bootloader. This is where you will actually be choosing the drive for the installation. It should be obvious which drive/partition is which when you look at the pulldown. Select the newly created Ubuntu partition and click continue. It's going to warn you that it's going to delete everything on /dev/sdc (that will be the most likely designation, but it may be different, like /dev/sdc2, depending on whether you have the shared partition or not and whether you put it at the beginning or the end.) Here's the important part: make sure that the next dialog says it's going to create 3 partitions in the one partition you have designated - one called /boot/EFI, a root partiton (/), and a swap partition. If not, something has gone wrong.

Proceed with the install, rememeber to select English/Macintosh when you choose your keyboard (not just English). **If it takes more than 30 minutes, something has gone wrong**. Reboot and start over. That happened to me several times, most times right near the end when Grub is getting installed. This is Ubuntu/Linux. It doesn't often "just work" the way that Macs do.

**(Below is different form Jason's instructions. Some things did not work for me.)**

When the installation is finished, minimize the dialog that asks if you want to restart or continue testing. Grab a pen and paper. Yep. You're gonna have to write some stuff down.

Click the very top button in the Launcher on the left side (Search). Type GParted. Open the GParted Partition Inspector app - this is the Ubuntu version of the Mac Disk Utility. You can choose different physical drives in the upper right pulldown. Choose the drive you just installed to. You may have other partitions, but the one we are concerned with is the one formatted "ext4" with a mount point of "/" (=root). If you don't see it, you've got the wrong dive. Right-click on it and select Information at the bottom of the popup menu. Carefully copy the UUID (Universally Unique ID). Double-check it before you close the window. There are 8-4-4-4-12 case-sensitive characters. like 3e45t568-rgth-4568-ed42-ft9p28fg1123.

Now you can reboot with option key. Leave the DVD in the drive and see what happens. If you have 2 different EFI boot choices, select the rightmost one, not the DVD. Edit the first option and change "quiet splash" to "nomodeset". You can eject the DVD and proceed to use Ubuntu.

If all you have is the DVD, go ahead and select that. When you get the Grub screen, you're going to have to boot manually, going back to Jason's instructions.

You've already gotten the UUID, so you can skip that part (his command did not work for me, that's why I had you get it the other way).

So, as you can see, this is not especially simple. If you're going to use Linux, this is the kind of thing that you're going to have to get used to. Things don't necessarily just work. Depending on what you do or try to do, you might break stuff and have to figure out how to fix it. The command line is your friend. You'll learn stuff that you never had to learn using OS X or Windows. Here are a few things to keep in mind:

1. Don't blindly follow instructions or install software or run scripts you find on the Internet. There are people out there who want to mess with people because they think it's fun. There are others who are trying to gain control of your computer for various reasons.
2. SUDO means "Super User says Do This". When you use it, you can do almost anything including things like giving someone else control of your computer or otherwise breaking it. Only use it when you know what you're doing.
3. Hopefully, there are at least as many people out there who want to be helpful as those who do not. As for help, ask "why", ask "how" and understand before you do what people tell you to do.
4. Remember that you're learning something new and that making mistakes is probably the best way to learn.

Cheers,

imattux

---

### Post by imattux on 2015-09-30
Apologies to e.e.p. I was being a bit of a ****. I understand that you were trying to help. However, I think it's a waste of both parties time if either does not read, ask for clarification and understand the question/problem before trying to help or provide a solution. I was very frustrated time and time again reading through these and other forums where people did not answer the question asked or offered outdated, inaccurate or otherwise unhelpful advice. Sometimes nothing is better than something that doesn't help. 

Peace, Love and Gerry Garcia ;-)

Carty - assuming you're able to get everything installed and running, WiFi is easy. Go to System Settings -> Software & Updates -> Additional Drivers. The system will search for a minute or so and then find the necessary Broadcom drivers for your airport card. Once the drivers are installed, you can either reboot to use your airport card or you can open your terminal and run
```
sudo service networking restart
```
to use it without a restart. 

That command is pretty clear. I promise it's safe to use SUDO ;-)

---

### Post by bartatubuntu on 2015-10-05
I have never managed, after many days, to boot and or install from 14.04.**3** Live CD or USB key on a MacBook Pro 5,1!  
But boot and install a 14.04.**1** Live USB key has worked for me without any problems. 
After the 14.04.**1 **install i have upgraded to 14.04.**3** with the Ubuntu build in System Upgrade. 


So, how it has worked for me: 

1 
Download 14.04.**1** 64 bit .iso


2 
Create a Live USB key on MacOS X exactly the way described here: 
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)
Important: 
# If MacOS X puts .dmg after the .img keep it like that! 
# You have to have administrator permissions. 
# The USB key have to be complete empty before you begin. To be sure format it. 
# The USB key has only one partition.


3 Install ReFind and then Boot with Alt key pressed and choose the hard disk with USB symbol. 
Important:
# If you see two hard disks with USB symbol choose the second one! Why i don't understand. 

4 
Wait until you see dark purple screen with at the bottom a "human" figure + keyboard. 

5
Press space bar

6
Press F6 and navigate in the menu with arrows to "nomodeset", press Enter to select, then press ESC to leave the menu

7
Press Enter again to "Try Ubuntu ..." 

8
Wait while Ubuntu starts up from the USB key. 

9 
In Ubuntu search for GParted Partition Manager and Create and or Format a partition with minimum 40GB as Ext4
Important: 
# This partition has to be maximum the fourth partition if you install along MacOS X! 


10
When finished quit GParted and start the Ubuntu Installer 

11 
Do what the Ubuntu Installer asks. I have chosen to install Ubuntu along MacOS X.

12
When install is finished you choose restart. When it works you can connect to internet and do in Ubuntu the system upgrade to Ubuntu 14.04.[B]3. 
[/B]
Works for me on a MacBook Pro 5,1 and 9,1.

---

