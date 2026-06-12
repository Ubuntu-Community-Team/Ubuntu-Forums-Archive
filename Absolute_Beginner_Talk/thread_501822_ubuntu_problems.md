---
title: "ubuntu problems"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by richie42 on 2007-07-15
ok, i've ran ubuntu and xununtu and both of them have done this wacky thing to one of my computers:

the screen is divided into thirds.

---

### Post by gn2 on 2007-07-15
Perhaps some more information concerning the problem hardware and the Ubuntu version may helpto identify the problem.....?

---

### Post by richie42 on 2007-07-15
Uhmmm. . . feisty fawn.

the comp is a dell inspiron notebook

---

### Post by gn2 on 2007-07-15
Does it have an ATI graphics adapter?

---

### Post by richie42 on 2007-07-15
how do I find out?

---

### Post by richie42 on 2007-07-15
bump

---

### Post by mdsmedia on 2007-07-15
I'm not at my Ubuntu machine at the moment, but in the system administration menu (at least in Dapper) there is a Hardware or Devices menu item. Click on that and it will list your hardware devices.

---

### Post by ReaderRat on 2007-07-15
Run this in the Terminal and post the output here
```
sudo lspci | grep VGA
```

---

### Post by richie42 on 2007-07-15
what's the terminal and everything?

i know nothing about computers

---

### Post by ReaderRat on 2007-07-15
At the top of the screen click on Applications>>>Accessories>>>Terminal to start the Terminal. enter the code I gave you at the command prompt ($) (you can cut & paste it from the post to the Terminal) Once it's entered press ENTER. Then cut & paste the output in your next post to us.

---

### Post by richie42 on 2007-07-15
> **ReaderRat said:**
> At the top of the screen click on Applications>>>Accessories>>>Terminal to start the Terminal. enter the code I gave you at the command prompt ($) (you can cut & paste it from the post to the Terminal) Once it's entered press ENTER. Then cut & paste the output in your next post to us.

it won't show that top thing

---

### Post by ReaderRat on 2007-07-15
Do you have Feisty Fawn (7.04) installed on your computer, or are you running the LiveCD?

---

### Post by richie42 on 2007-07-15
> **ReaderRat said:**
> Do you have Feisty Fawn (7.04) installed on your computer, or are you running the LiveCD?

i installed fiesty and i am running the live cd 4 the one with the long term support but it is xubuntu


it doesn't show for both

---

### Post by purplearcanist on 2007-07-15
You can try to boot to recovery mode to easily load the terminal.  To do so, select the option that says recovery mode from the GRUB menu, and it will be a command prompt.  Login.  From there, it is the command prompt.

Be sure to type the command: sudo lspci | grep VGA

and write down the results.  Use shift+page up to scroll up and shift+page down to scroll down through it.

---

### Post by ReaderRat on 2007-07-15
I'm sorry but I don't know much about Xubuntu; I run Ubuntu.

---

### Post by richie42 on 2007-07-15
> **ReaderRat said:**
> I'm sorry but I don't know much about Xubuntu; I run Ubuntu.

i have ubuntu installed.

It does the EXACT SAME THING for both of them

---

### Post by purplearcanist on 2007-07-15
> **ReaderRat said:**
> I'm sorry but I don't know much about Xubuntu; I run Ubuntu.
Xubuntu and Ubuntu are about the same, the only differences are that Xubuntu uses a XCFE interface, and Ubuntu uses a GNOME interface.

---

### Post by ReaderRat on 2007-07-15
OK< then boot up Ubuntu, enter your username and password, and wait til it gets to the screen with "Applications    Places    System" in the top left corner.
*Click on Applications (a menu will drop down)
*Click on Accessories (a menu will appear.)
*Click on Terminal (The Terminal program will start.)
Let me know when you have done this.

---

### Post by ReaderRat on 2007-07-15
Something that might be faster would be for you to tell me what Model Dell Inspiron you have(i.e- 1501, 6400,etc.) and I will look up the specs.


EDIT:  Sorry, I gotta hit the sack now....early day tomorrow....ReaderRat

---

### Post by AlexenderReez on 2007-07-15
i think op should read a bit tutorial in internet....there are a lot of them....

---

### Post by richie42 on 2007-07-15
> **ReaderRat said:**
> OK< then boot up Ubuntu, enter your username and password, and wait til it gets to the screen with "Applications    Places    System" in the top left corner.
*Click on Applications (a menu will drop down)
*Click on Accessories (a menu will appear.)
*Click on Terminal (The Terminal program will start.)
Let me know when you have done this.

i don't go there on UBUNTu.

It just loads amd I see a brown screen with a messed up word UBUNTU and some gears that say options at the bottom.

---

### Post by richie42 on 2007-07-16
bump because i need help and i will never stop bumping unless i find an answer

---

### Post by gn2 on 2007-07-16
> **richie42 said:**
> how do I find out?

Google the make and model number or visit the manufacturer's website..

---

### Post by richie42 on 2007-07-16
this is what it has

The Inspiron is a 7.5lb notebook PC that runs PIII 850MHz using Intel's i815 chipset M/B with 128MB SDRAM. Also, the notebook features an IBM ATA 66/32GB/5400rpm HD, ATI Rage Mobility 128, integrated 8x DVD, a firewire port, and a 15" LCD display with 1400x1050 res.

---

### Post by alex_anthony on 2007-07-16
> **richie42 said:**
> i don't go there on UBUNTu.

It just loads amd I see a brown screen with a messed up word UBUNTU and some gears that say options at the bottom.

I think you're on the log in screen...
you need to type in the username and password you created when you installed

---

### Post by richie42 on 2007-07-16
> **ReaderRat said:**
> OK< then boot up Ubuntu, enter your username and password, and wait til it gets to the screen with "Applications    Places    System" in the top left corner.
*Click on Applications (a menu will drop down)
*Click on Accessories (a menu will appear.)
*Click on Terminal (The Terminal program will start.)
Let me know when you have done this.

i did that

---

### Post by richie42 on 2007-07-16
> **ReaderRat said:**
> Run this in the Terminal and post the output here
```
sudo lspci | grep VGA
```

it said this

bash: sudo: command not found

---

### Post by richie42 on 2007-07-16
bump

---

### Post by richie42 on 2007-07-16
bump because i need help

---

### Post by richie42 on 2007-07-16
bump

---

### Post by gn2 on 2007-07-16
Try "sudo dpkg-reconfigure -phigh xserver-xorg" in a terminal which will allow you to change hardware configuration and select a different graphics driver.

---

### Post by richie42 on 2007-07-16
> **gn2 said:**
> Try "sudo dpkg-reconfigure -phigh xserver-xorg" in a terminal which will allow you to change hardware configuration and select a different graphics driver.

it says this

> sxserver-xorg postinst warning: overwriting possibly customized configuration file; backup in /etc/X11/xorg.conf.20070716181130

---

### Post by gn2 on 2007-07-17
Does it give the option to continue? Take it if it does.

Perhaps consider text-based installation of Xubuntu 7.04 from the "Alternate CD" using these instructions: [https://help.ubuntu.com/community/InstallingXubuntu](https://help.ubuntu.com/community/InstallingXubuntu)

---

### Post by richie42 on 2007-07-17
> **gn2 said:**
> Does it give the option to continue? Take it if it does.

Perhaps consider text-based installation of Xubuntu 7.04 from the "Alternate CD" using these instructions: [https://help.ubuntu.com/community/InstallingXubuntu](https://help.ubuntu.com/community/InstallingXubuntu)

it says, attempt to autodect video hardware?

---

### Post by richie42 on 2007-07-17
bump

---

### Post by AlexenderReez on 2007-07-17
> **richie42 said:**
> bump

bump..bump..hahah...lol..

> [http://ubuntuforums.org/showpost.php?p=3033579&postcount=5](http://ubuntuforums.org/showpost.php?p=3033579&postcount=5)

---

### Post by richie42 on 2007-07-17
> **reez0105 said:**
> bump..bump..hahah...lol..

will that fix the thirds thing?

---

### Post by richie42 on 2007-07-18
bump bump bump bum bum bum


(to the tune of La Grange)

---

### Post by richie42 on 2007-07-22
bump

---

### Post by richie42 on 2007-07-28
bump

---

### Post by ugm6hr on 2007-07-28
Sounds like you had the same problem as me (on my other laptop).

It would have been helpful if you gave more details:
[http://ubuntuforums.org/showthread.php?p=2682710#post2682710](http://ubuntuforums.org/showthread.php?p=2682710#post2682710)

Given things can't get any worse - just copy the text from the .txt linked there, and paste into xorg.conf (/etc/X11/xorg.conf)

Have you managed to login?  You need to boot and then login (with username / password).

Double-click my xorgDell5000.txt (open) and copy all text there (don't close window).

Then Alt+F2
```
gksudo nautilus
```
Go to /etc/X11/xorg.conf and make a copy of the file (to e.g. xorgbkp.conf)
Double-click xorg.conf
Delete everything there
Paste text from my .txt to this file, and save.

Then Ctrl+Alt+Backspace

Then keep your fingers crossed.

---

