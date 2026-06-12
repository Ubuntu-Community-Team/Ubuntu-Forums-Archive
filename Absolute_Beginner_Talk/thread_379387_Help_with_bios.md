---
title: "Help with bios"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by gettinoriginal on 2007-03-08
I am running Windows XP Pro and have burned a disk for ubuntu, but my bios will not give me the option of changing boot drives order and always boots to the hard drive.  I have also followed all the instructions I can find, but cannot seem to partition my hard drive.  HELP !!!!!!!!!!

---

### Post by taurus on 2007-03-08
What mobo (manufacture and model) do you have?

---

### Post by gettinoriginal on 2007-03-08
I am running an IBM NetVista

---

### Post by dstew on 2007-03-08
When you access your BIOS setup screen, is the boot order listed? Is the CD-ROM/DVD drive listed in the boot order somewhere? If it is not listed, you may need to enable booting from the CD first. Are you sure you are giving the setup program the correct input in order to change the boot order?

---

### Post by gettinoriginal on 2007-03-08
In the bios, it only gives this this option, Devices and I /O ports, then lists as follows without the option of being able to change anything:  Hard Disk Drive 0, Hard Disk Drive 1, CD-ROM Drive 2, and Hard Disk Drive 3.  But I do only have one HD in the computer!! Under Start Up, there are no options for boot order.  I should also note that my computer has an Intel 815 chipset, and bios upgrade is no longer available from Intel.

---

### Post by old_geekster on 2007-03-08
It certainly doesn't make sense that you can't set the boot order.  This is a very basic function of the BIOS.

I would check very carefully through all of the options.  Sometimes they hide things in strange places.

I would run a search on "Google" using the BIOS maker and version to see what you can find.  My guess is there will be an answer for you.  You can't be the only one with this problem.

---

### Post by dstew on 2007-03-09
Are you sure you are looking at your BIOS setup screen? Maybe you are looking at a Windows hardware or device manager screen. To get to the BIOS screen, you need to power off the computer completely (cannot simply restart), and press the F1 key when you see the System Configuration Utility prompt at startup. Here is a link to the Lenovo site that explains this.
[http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-52236]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-52236")

---

### Post by gettinoriginal on 2007-03-09
yes, I am definetly in the bios setup screen.  Under advanced set up, it gives my drives, but there is no option to change them, I have googled, yahood, and checked everything, but I cannot change the boot order.  :(  I have been to Intel.com, downloaded any files they have for this board, and still no change, so I really do not think it is a corruption problem.  I should state that my option screens on the setup are just basic blue, and do not look anything like the screens that many of the websites show as set up screens.

---

### Post by ben.s on 2007-03-09
On most IBMs I've used, there's a message like "Press F12 for boot options" on the first screen that comes up when you power up the machine.  F12 might be different depending on the model.

---

### Post by christhemonkey on 2007-03-09
Maybe you should update your bios?

But that can be a bit of a hassle.
Or maybe there are some sort of jumpers on the motherboard that dont let you change advanced options in your bios?

Also on some of my machines, there is a seperate menu for selecting boot order instead of the normal BIOS setup, something like press F10 for bios and F5 for boot order.
(these are just ideas off the top of my head)

---

### Post by gettinoriginal on 2007-03-09
Thanking you all for all your tips, and believe me, I have tried each and every one, but still no luck!!  Guess I am going to have to forget about unbuntu until I can afford a new computer :(.  I am just so tired of the windows problems, and was really wanting to try this.

---

### Post by gettinoriginal on 2007-03-10
I think I may have found a problem with my bios, but have no idea how to correct it.  In doing system checks, etc, I found that my computer will only support 4 devices, and in my bios it states the following:

Diskette Drive A  1.44MB 3.5
IDE HD Drive 0  30GB
IDE HD Drive 1  Not Installed
IDE CD ROM Drive 2  Installed
IDE HD Drive 3  Not Installed

How do I get these 2 HD's which occupy my bios off the list ???  Could the fact that I have 5 listed be the reason that I cannot change the boot order ???

---

### Post by gettinoriginal on 2007-03-10
Also, my system startup boot configuration reads as follows, can I edit this to change the boot order ???

[boot loader]
timeout=45
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

---

### Post by oilchangeguy on 2007-03-10
in the bios you should be able to cange the boot order by scrolling down the list, highlight what you're wanting to change, press enter, and be presented with a screen that allows you to move them up and down. or when highlighted use your up, or down arrow, or + -, you should see instructions on how to make changes after you highlight.

---

### Post by gettinoriginal on 2007-03-10
Thats the problem, I can highlight them, but no matter what I do, nothing changes !!! I think it is because there are 5 listed, and my system only supports 4  I need to get rid of the 2 that are "not installed", and that possibly will let me change the order.

---

### Post by oilchangeguy on 2007-03-10
ok try resetting the bios to the default settings, at the bottom theres a list of functions, press the f key that shows default, press f10 to save and exit, reboot and see if this makes a difference.

---

### Post by oilchangeguy on 2007-03-10
oh, and as for the list of things your bios shows as not installed, you can't remove those. they are possible slave drive positions, and this should make no difference if they're being used or not. you should still be able to change the boot order. what you are seeing is on the first bios page, not the page that allows you to change the boot order, keep looking.

---

### Post by gettinoriginal on 2007-03-10
well, default did not help, and as far as keep looking, I have been through every option in the bios, and tried every fkey, combination of keys, bios start up page, advanced options, etc, and still not able to change boot order that is why I thought maybe I could edit my startup boot configuration ???  
[boot loader]
timeout=45
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOW S
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Micro soft Windows XP Professional" /fastdetect /NoExecute=OptIn

---

### Post by oilchangeguy on 2007-03-10
1) Shut down the operating system and turn off your computer.
2) Press and hold down the F1 key, and then turn on the computer.
3) When an IBM or other logo is displayed or if you hear repeating beeps, release the F1 key. The IBM BIOS Setup Utility will start.
4) Select "Start Options" from the first menu.
5) From the Start Options menu, press <Enter> on the top bullet labeled "Startup Sequence" (it is above all the other options). This brings up a new "Startup Sequence" menu.
6) Change boot order as needed using arrow keys.

---

### Post by chewearn on 2007-03-10
> I think I may have found a problem with my bios, but have no idea how to correct it. In doing system checks, etc, I found that my computer will only support 4 devices, and in my bios it states the following:

Diskette Drive A  1.44MB 3.5
IDE HD Drive 0  30GB
IDE HD Drive 1  Not Installed
IDE CD ROM Drive 2  Installed
IDE HD Drive 3  Not Installed

How do I get these 2 HD's which occupy my bios off the list ??? Could the fact that I have 5 listed be the reason that I cannot change the boot order ???
This list is correct.  It is not the cause of your problem.  The first item is the floppy disk, sometimes marked as fd0.  The remaining 4 items are the possible IDE drives you can have in your system.  Basically, the first is IDE0 master (your harddrive), second is IDE0 slave (nothing is connected to it in your system), third is IDE1 master (your CD-ROM), and fourth is IDE1 slave (also nothing connected).


> **gettinoriginal said:**
> well, default did not help, and as far as keep looking, I have been through every option in the bios, and tried every fkey, combination of keys, bios start up page, advanced options, etc, and still not able to change boot order that is why I thought maybe I could edit my startup boot configuration ???  
[boot loader]
timeout=45
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOW S
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Micro soft Windows XP Professional" /fastdetect /NoExecute=OptIn

This is your XP boot.ini file, has nothing to do with the BIOS.  Changing this file will not help.  It will only borked your XP boot.


Now, then.  These things you mentioned are not the cause of your problem.  Instead, you need to find the option in BIOS setup that can change the boot order, but since you already look and look, then it's probably not there.  Having said that, it is extremely strange to have a BIOS, where you cannot set the boot order.  I have a hunch that ben.s is right:

> On most IBMs I've used, there's a message like "Press F12 for boot options" on the first screen that comes up when you power up the machine. F12 might be different depending on the model.
I have also seen some laptops, where the key you need to press to set boot order is different than the key you use to enter BIOS setup.  You just need to find out this key (or key combination).

---

### Post by gettinoriginal on 2007-03-10
OK, problem solved, called Lenovo Tech Support, and bios were incomplete, so they sent me new bios software which is now installed and boot order changed  :)    Thank you all so much for your attempts, sorry it was my computer and not your advice that was holding me back.

---

### Post by Patrick K on 2007-03-10
How old is this computer. Just about any computer of the last 5 or more years should be able to boot from a CDrom. IIRC, in my BIOS the option is on the integrated peripherals page. In my case there are three options 1st boot device, 2nd boot device, ...

As suggested, there may be a advanced section that you are not seeing. And you found nothing in your searches.  I looked around and found that if a password has been enabled only a limited number of options are presented. If you bought the computer pre-configured, a password could have have been set. On some motherboards, maybe yours, removing the battery for some period of time releases the password protection. 

I looked a a PDF user manual file of one of the NetVista computers, may not have been your particular model, but there wasn't much info on setting options in the BIOS or removing a password. it did show a start up page on the main menu page and another site stated that the boot order is set on that page. 



Found something else. Take a look here and let us know if it works:
[http://forums.devshed.com/motherboards-106/changing-the-boot-sequence-on-an-ibm-netvista-computer-163374.html](http://forums.devshed.com/motherboards-106/changing-the-boot-sequence-on-an-ibm-netvista-computer-163374.html)

EDIT: Glad you got it fixed.

---

