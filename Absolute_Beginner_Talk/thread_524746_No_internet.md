---
title: "No internet"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by jambutties on 2007-08-13
I installed Ubuntu 7.4 on a Hi-grade laptop.I was previously running vista on it  and could use the internet via the Belkin wireless G router.Now I cannot get it to work and when I tried to run the disc again I got "Cannot open /media/cdrom0/setup.exe.No appplication suitable for automatic installation is available for handling this kind of file."
I also cannot play any media files but assume this will be resolved when I can access the internet.
Please bear in mind that although I hope to come back in the next life as a geek for the moment I'm stuck with this puny brain.
Thanks in advance.

---

### Post by jspangler on 2007-08-13
It would help a lot if you could get access through an ethernet cable. Is that a possibility?

Also, linux isn't set up to automatically run .exe files. It wouldn't know what to do with them anyway. The windows drivers on that disc wouldn't work, unless you use a program called ndiswrapper, which is probably the best way to install the drivers. 

But if you can get any internet access, it would be a whole lot easier to get your system up and running :)

---

### Post by nvrpunk on 2007-08-13
In linux .exe are not executable.  I assume you are trying to install a windows driver on a linux system?  Further explain what steps you have taken.

---

### Post by stchman on 2007-08-13
> **jambutties said:**
> I installed Ubuntu 7.4 on a Hi-grade laptop.I was previously running vista on it  and could use the internet via the Belkin wireless G router.Now I cannot get it to work and when I tried to run the disc again I got "Cannot open /media/cdrom0/setup.exe.No appplication suitable for automatic installation is available for handling this kind of file."
I also cannot play any media files but assume this will be resolved when I can access the internet.
Please bear in mind that although I hope to come back in the next life as a geek for the moment I'm stuck with this puny brain.
Thanks in advance.

What type of chipset does your wireless card have?  Give us an lspci output here.

---

### Post by anewguy on 2007-08-13
Okay, in case this is your first experience with Linux and Ubuntu in particular, let me try to backup a step or two.  As already mentioned above, the CD you have contains files that are made to run in Windows.  Windows and Linux are 2 different "animals" and you can't run a program from one in the other.  So Ubuntu can't do anything with your CD.   So now you're at a point were you don't have a clue as to what you have to do, right?  Don't feel bad - we've all been there!:)  So where do we go from here?

(1) Most wireless adaptors, at least in my limited experience, are not supported "out of the box" by Ubuntu.  One way to make them work has been hinted at -  actually using the Windows drivers is Ubuntu with a process called ndiswrapper.  Don't worry what it all means right now - just keep the idea in the back of your head for later.

(2) In order to get an idea of what wireless adaptor you have, so we can try to give you more specifics, we normally ask you to run the "lspci" command as mentioned in the previous reply.  "lspci"  is a command to tell Linux to list all of the PCI devices is knows about on your computer.  So, how do you run it?  Try this:
-
- move your mouse to the top bar and click on "Applications"  move your mouse down to "Accessories" and then over to and click on "Terminal".  This opens a window into which we can enter commands - sometimes you will see this called the command line interface.
-
- once that window has opened,  type "lspci" (without the quotes) and press enter.
-
- if you are used to copy/paste from Windows, that's what we need you to do with the output from that command:  highlight (select) ALL of the output, right click and say copy, then open up a reply here and right click and say paste.  This will "copy" the text from the terminal window over into the reply window here.
-
- submit the reply

Hope this wasn't too simple for you, because I wouldn't want to offend you.  I just figure with a new user it's better to start easy and then move up a level if the user already understands.:)

---

### Post by jambutties on 2007-08-14
Huh?
Huh?
Huh?
Oh

Don't worry about offending me ,unfortunately this is just about the right level of complicatedness (is that a word?)for me.
I typed in the command and I got-

XXXX@XXXX-desktop:-$ispci
bash:ispci:command not found
XXXX@XXXX-desktop:-$

This doesn't sound good but I'm sure I did it right.Any further assistance would be greatly appreciated.

---

### Post by jspangler on 2007-08-14
Hi jambutties,

The command you need to type is "lspci" (with a lowercase L at the beginning). Also, know that linux is case sensitive. :)

---

### Post by jambutties on 2007-08-14
Whoops
Will try again.Thanks for your patience.

---

### Post by jambutties on 2007-08-15
OK.I typed in the correct command and got loads of stuff up but have now found that if I try to put this onto my memory stick so I can then paste it into the forum I get a blank page.
To clarify.Laptop with Ubuntu in 1 room (no internet).PC with windows in another room (connected to internet).Memory stick is the only way I know of getting info from 1 to the other.This worked fine before when Vista was on the laptop.
I don't really want to have to type all the stuff in but I'd really appreciate someone telling me what I should look and what to do if I find it.
I really want to get this working 'cus I love the look of Ubuntu so far but nothing works.
Thanks again for any help.

---

### Post by sanderella on 2007-08-15
We need to know which laptop and which wireless card you are using. Can you post the info here?

---

### Post by st33med on 2007-08-15
> **sanderella said:**
> We need to know which laptop and which wireless card you are using. Can you post the info here?

What he means is post all the output from the lspci command we gave you and paste it here.

EDIT: My bad, you're on another computer. Can you type the last device in the list? Or at least identify the chipset name.

---

### Post by jambutties on 2007-08-15
Laptop is a hi-grade notino.Wireless card??

---

### Post by jambutties on 2007-08-15
Last item in list is:06.01.0 Audio device VIA technologies Inc Via high definition audio controller (rev 10)
Can't see anything that says chipset.

---

### Post by jspangler on 2007-08-15
Jambutti, on my system, the line for my wireless card is the following:

02:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

Its very possible that the line we need from your "lspci" command begins with "Network controller".

If you can't find any command like that, please tell us the output of the line beginning with "Ethernet Controller".

Also, if you cant find the network card on the list, it might be listed in the information that came with your laptop.

Hope that helps!

---

### Post by jspangler on 2007-08-15
About your memory stick, it should load automatically. When the computer finds it, it should automatically open a window (also, there should be a link, probably called "disk", on your desktop). Right click in the window of the usb disk, and click "Create Document > Empty File". You should be able to paste the information in there.

---

### Post by SkipBlue on 2007-08-15
Try running the commands (in a terminal) ```
lspci | grep network
``` and ```
lspci | grep ethernet
``` The "|" (vertical bar) is typed by holding down shift and hitting backslash, usually located on the right-side of your keyboard around the enter and backspace buttons. On the keyboard, it may look like a broken line, but it's really a straight line. Please give us the output of these commands (it should only be a line or two, so you should be able to copy it by hand).

---

### Post by jambutties on 2007-08-16
Thanks for the advice about using the memory stick.Finally got it to work, this is what I got.

00:00.0 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge (rev 80)
00:00.1 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. Unknown device 6364
00:00.7 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. Unknown device 3371 (rev 01)
06:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)

I tried to input the new command but I can't get that straight line on my laptop.I can see the key, it's in the top left corner under the Esc key but there are 3 symbols on it and I can only get the other 2.

Hope this helps.

---

### Post by jspangler on 2007-08-16
Hi Jambutti, have you tried connecting a physical network cable to your computer? I see that you have an "ethernet controller". Try plugging in a network cable from your cable/adsl modem or your home router. Does that do anything? Does an internet connection come up when you do this?

---

### Post by jambutties on 2007-08-16
Don't have a spare cable and am working today so don't have time to go and get one.Day off tomorrow.Will get a cable and try it then.
I'm assuming that I can't just take the router out of the equation and connect more than 1 computer to my broadband modem, right?
If worst came to worst would I be able to install Ubuntu on my desktop alongside windows xp running through my broadband modem, taking the router out of the equation.
I'm not giving up yet I'm just curious. 
Also if I installed Ubuntu on my desktop and got it online would I then be able to transfer program updates to my laptop offline?Then at least the media player etc would work on both.

---

### Post by jspangler on 2007-08-23
You could transfer updates but it's a bit complicated, because you have to install all dependencies as well. A better idea is to use the live cd that you installed ubuntu from. You can download and install packages from there. When you insert it, a prompt should come up asking if you want to use the package manager.

---

### Post by jambutties on 2007-08-26
Thanks for all the help guys.I did eventually manage to get connected and am typing this in Ubuntu.I have since hit another snag but am going to post this in a new thread.
Cheers

---

