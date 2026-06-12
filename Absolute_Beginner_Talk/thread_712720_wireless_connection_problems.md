---
title: "wireless connection problems"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by dontpinch on 2008-03-02
hi there

i am an ABSOLUTE beginner, so be patient. i installed ubuntu and i haven't yet been able to connect to the internet. i use a belkin g notebook network card model no. f5f7010 on a dell inspiron 5100

 i have done as outlined in this page
[https://help.ubuntu.com/community/Wi.../bcm43xx/Gutsy](https://help.ubuntu.com/community/Wi.../bcm43xx/Gutsy)
in the restricted drivers the firmware for broadcom 43xx chipset family is in use but and when i troubleshooted this is what i got

iwconfig
lo no wireless extension
eth0 no wireless extension

and yet the wireless card lights are on and green, but no connection at all. 

any suggestions? thanks a lot in advance

---

### Post by anewguy on 2008-03-02
I assume you must have a wired connection available?  If so, go to this link and, depending on the version of your card, download the appropriate Windows driver.  Via CD/flash drive/whatever copy the exe file you just downloaded to a Windows machine and execute it.  It will unpack the driver and other files.  Change to the folder it unpacked to and look for the .inf and .sys files.  Copy these to CD/flash driver/whatever and then copy them to your Ubuntu desktop.


Then use synaptic package manager and be sure you have ndiswrapper and its' utilities installed.


When you've got that done, post back here and we'll go through the rest.  :)

---

### Post by dontpinch on 2008-03-02
thanks for your reply. i actually have the original installation disk and found the .inf files but i don't understand how to install them. they are saved to my desktop.

one is bcmwl5a.inf and the other bcmwl5.inf 

also, to top it off, when i plug the ethernet in, nothing happens. i just wanted to tackle an issue at a time and to plug the computer in is quite complicated since there would be two other working macs  without an internet connection. it would be disadvantageous. 

if you can tell me how to install those inf files i'd appreciate it. thanks a lot
lisa

---

### Post by anewguy on 2008-03-02
Well, having those files is a big step.  Now let's see if another piece is installed or not:

in a terminal window, type:

ndiswrapper -l (lower case "L", for list)

Please post back what the output of that is.  :)

---

### Post by dontpinch on 2008-03-02
thanks again

so what i get is 

drivername: invalid driver!
rt2500usb: invalid driver

i guess it's not installed....but yesterday i installed the following files 

ndiswrapper-utils-1.9_1.43-lubuntu2_i386.bed
ndiswrapper-common_1.43-lubuntu2_all.deb
ndiswrapper.utils_1.1-5_all.deb
bcm43xx-fwcutter_006-3_i386.deb

what's next?

---

### Post by anewguy on 2008-03-02
Actually, ndiswrapper IS installed - it's letting you know you have an invalid driver.  Here's what to try:

First, we need to get rid of the driver that is not working:

sudo ndiswrapper -e rt2500usb

Next, check to be sure no drivers are now know to ndiswrapper:

sudo ndiswrapper -l (lower case "L", for "List")

This should return nothing.

Now, assuming you have the 2 bcmwl* files on your desktop:

cd ~/Desktop

sudo ndiswrapper -i bcmwla5.inf (that's a lower case "I", for "Install")

sudo ndiswrapper -l (lower case "L")

be sure the device/driver show on the output

sudo depmod -a

sudo modprobe ndiswrapper

sudo ndiswrapper -m

Now we need to "remove" thedefault Broadcom driver:

cd /etc/modprobe.d

sudo gedit blacklist

to the end of that file add the following line:

blacklist bcm43xx

now save the file and exit


Next we need to be sure ndiswrapper starts at boot:

cd /etc

sudo gedit modules

to the end of the file add the following line:

ndiswrapper

save the file and exit

Now, you *MUST* reboot.

When the system is back up, check your network icon and see if wireless networks are showing.

Let me know how it goes!  :)

---

### Post by blakelives0312 on 2008-03-02
holy crap, you are amazing. sorry, that just had to be said. 
 I am having this same problem. But, i dont know where to get my driver, i think i know what version my wireless card is, but i cannot for the life of me find it. i went into vista's device manager thing ad found the .sys file but i cannot find the .inf file. so i am at a loss... is there a way to write this file so that i can use the .sys file? or do i have to keep searching?

---

### Post by anewguy on 2008-03-02
I think the first place to start is either with the manufacturer of your PC, or if you have added the device itself, the manufacturer's disk or the manufacturer of the device.  Go to their website and search for Windows drivers for your device - if possible, try non-Vista drivers first if they are available.  The file will probably be compacted - maybe a zip, maybe a self-extracting archive.  The absolute easiest way to unpack them and find the files you need is to do so on a Windows machine (if you're dual-booting, so much the better!).  Once you find the driver files, copy them to some media then boot Ubuntu and copy them to your desktop.  Then just follow the instructions above.

Do you know what type/model of adapter you have?  Try lspci in a terminal window and see what it says is your wireless device. 

If you need help or have questions beyond that, just post back!  :)

---

### Post by blakelives0312 on 2008-03-02
wells, i figured it out. idk how. ..but i stubled upon this article: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy) after figureing out that my modle was bcm4318

it works, that is all i am concerned about. 
thanks for the help :D

---

### Post by dontpinch on 2008-03-03
hey anewguy
i'm very grateful for your long response!! i have a little prblem though :-k
which is that the cd ~/Desktop i get the response no such file or directory...the bcmwl5.inf file is there and the original disk is in the disk drive. i feel so stupid i can't figure this out and stop bugging you about this...thanks!

---

### Post by anewguy on 2008-03-03
Well, not sure why that wouldn't work, but here's another way:

when you log on, you will be in your "home" folder.  type the following in a terminal window:

ls

This will give a non-detailed list of the non-hidden files and folders in your home folder.  In that list you should see your desktop.  Using your mouse, highlight it, copy it, then:

cd <paste here>

That should get you there!  :)

EDIT:  noticed you said your .inf file was there -> be sure all the .inf and .sys files that make up your driver are there - you'll be glad you did!

---

