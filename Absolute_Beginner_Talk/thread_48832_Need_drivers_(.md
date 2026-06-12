---
title: "Need drivers :("
date: 2005-07-14
forum: Absolute Beginner Talk
---

### Post by Muk on 2005-07-14
I just installed ubuntu on my new computer that i build together a couple of hours ago. Their are some drivers Pci cards that ubuntu did not recognize and i don't seem to be able to find any drivers for them, less do i know how to install them onto the computer :P

well i have a D-Link wireless Dwl-G510 PCI card and it does not seem like that D-Link offers a linux driver for its card. 

I downloaded wine and tried installing it, but it does not look like i did it right. Could anyone give me a small tutorial on how to install new programs and drivers?

Thx

Muk

---

### Post by varunus on 2005-07-14
Wine can't load windows drivers on linux.  The program to load wireless card drivers on linux is called "ndiswrapper."  There's a howto in the "tips and tricks" section that is specific to broadcom chipsets, but you should be able to get the windows drivers (the .sys and .inf files) and install them using ndiswrapper in the same way.  Ignore the step dealing with RadioFrequencies and changing 0 to 1 however, that is only for broadcom chipsets.

The Ubuntu wiki also has information on how to set up ndiswrapper.

Good luck.

---

### Post by Nequeo on 2005-07-14
[QUOTE=Muk]I just installed ubuntu on my new computer that i build together a couple of hours ago. Their are some drivers Pci cards that ubuntu did not recognize and i don't seem to be able to find any drivers for them, less do i know how to install them onto the computer :P

well i have a D-Link wireless Dwl-G510 PCI card and it does not seem like that D-Link offers a linux driver for its card. 

I downloaded wine and tried installing it, but it does not look like i did it right. Could anyone give me a small tutorial on how to install new programs and drivers?

Thx

Muk[/QUOTE]
 Heya.

Most modern wireless cards need you to install a program called 'Ndiswrapper' to get them working. This isn't too hard, but I've been trying to work out a way to make it even easier. 

If you have a driver CD that came with your wireless card, you can probably use my automatic script to set everything up for you. 

Go to this address, 
[http://members.optusnet.com.au/~sger/ndiswrapper_wrapper.py](http://members.optusnet.com.au/~sger/ndiswrapper_wrapper.py) 
and save the file. If you don't have internet access on your Ubuntu computer, find some way of getting the file over. Floppy or USB drive, whatever. Put it in your home directory. 

Once the script is on your Ubuntu machine, mark it as executable (right click on it in the file explorer, click on properties--->permissions then tick 'executable).

Open a terminal, then type in 'sudo ./ndiswrapper_wrapper.py'.

Follow the prompts, and hopefully that will be that! I the script doesn't work properly for some reason, let me know and we'll walk through setting up ndiswrapepr automatically.

Cheers,

---

### Post by varunus on 2005-07-14
Nice Nequeo!  Have you posted that script in the "tips and tricks" section?  It would be a really nice addition.  (If you want to, that is.   :) )

---

### Post by Muk on 2005-07-14
ohh thx, i'll try this out once i get home.


[QUOTE=Nequeo]Heya.

Most modern wireless cards need you to install a program called 'Ndiswrapper' to get them working. This isn't too hard, but I've been trying to work out a way to make it even easier. 

If you have a driver CD that came with your wireless card, you can probably use my automatic script to set everything up for you. 

Go to this address, 
[http://members.optusnet.com.au/~sger/ndiswrapper_wrapper.py](http://members.optusnet.com.au/~sger/ndiswrapper_wrapper.py) 
and save the file. If you don't have internet access on your Ubuntu computer, find some way of getting the file over. Floppy or USB drive, whatever. Put it in your home directory. 

Once the script is on your Ubuntu machine, mark it as executable (right click on it in the file explorer, click on properties--->permissions then tick 'executable).

Open a terminal, then type in 'sudo ./ndiswrapper_wrapper.py'.

Follow the prompts, and hopefully that will be that! I the script doesn't work properly for some reason, let me know and we'll walk through setting up ndiswrapepr automatically.

Cheers,[/QUOTE]

---

### Post by Muk on 2005-07-15
Ohh i just noticed this script only works for i386
it does not work for amd64 version of ubuntu. it took me a long time to figure this out. it will go into an endless loop if trying to use the amd 64 ubuntu disc

---

### Post by Muk on 2005-07-15
another problem that i found out after trying to use i386

here is what it said:


root@muk:/home/jack # ./ndiswrapper_wrapper.py
Your wireless card and drivers have been installed successfully.
root@muk:/home/jack #
(network-admin:13737): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


know any solution to this problem?

---

### Post by clumsy1007 on 2005-07-16
I also tried to run that python script, but it didn't work. When I ran the program it opened the cd drive and told me to insert my Ubuntu disk and press enter when it showed up on the desktop. I put in the cd and closed the drive, but when I went back to the screen and pressed enter, it just opened the CD drive again. How do I get the script to continue?

[The full text of my problem is here](http://www.ubuntuforums.org/showthread.php?t=49096) 

Hope to hear from someone soon.... Thanks!

---

### Post by Nequeo on 2005-07-16
[QUOTE=clumsy1007]I also tried to run that python script, but it didn't work. When I ran the program it opened the cd drive and told me to insert my Ubuntu disk and press enter when it showed up on the desktop. I put in the cd and closed the drive, but when I went back to the screen and pressed enter, it just opened the CD drive again. How do I get the script to continue?

[The full text of my problem is here](http://www.ubuntuforums.org/showthread.php?t=49096) 

Hope to hear from someone soon.... Thanks![/QUOTE]
 Muk...

Do you have the AMD64 version of Ubuntu installed? If you do, and used the script to try and installed the i386 version of ndis-wrapper, that is probably going to cause some problems :)

But there's a simple solution. If you look on the AMD64 cd, there will be a file called md5sum.txt (or something similar). Just PM me the first line of that file, and I'll modify the script to work with AMD64 as well.

Cheers,

---

### Post by Muk on 2005-07-16
well i installed a i386 version of ubuntu onto my machine so my infinete loop is gone. but as i posted above i am getting another problem. it does not read the windows driver cd.

---

### Post by varunus on 2005-07-16
Muk,

That error occurs if you run certain programs using "su" instead of "sudo".  Try exiting root, and entering "sudo ./ndiswrapper_wrapper.py" instead.

Good luck.

---

### Post by Nequeo on 2005-07-16
Hi Muk,

The script reads your driver cd by searching for .inf files. On many CDs, such as Linksys, the windows drivers are all sitting in a seperate directory called 'Drivers'. However, there's always a chance some companies would package their drivers up in .cab files and insist you run the install program in order to get the drivers out.

Another problem I've had with D-link is that I once bought a wireles card, and the driver cd didn't have any drivers on it at all! They just simply left them off.

My first suggestion is to search the cd rom yourself, looking for .inf files. If you find some, it probably means my script is broken... But we can use those to install the card by hand.

If you don't, you'll have to get on-line to the card makers website and see if you can find a way to download the drivers and get them onto the Ubuntu machine. 

Cheers,

---

