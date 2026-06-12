---
title: "linux and wirless....."
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by zanarkand100 on 2006-08-02
howdy again folkes! i have a BT Voyager 1040 PCI Adapter wirless card and it appears linux doesnt like it very much.

i have searched but cant seem to find a linux driver for it....does this mean im gonna need to go and get a logn ethernet cable?? 

i have tried connecting to my wireless network in ubuntu and it says "activating" for a long time and then...nothing

any help would be much appreciated...or how ever you spell it :D

Zan

---

### Post by nalmeth on 2006-08-02
Can you find a windows driver for it?

If so you can use ndiswrapper to "wrap" the windows driver into ubuntu, which might make it work.

Open synaptic, and search for:
ndiswrapper
ndisgtk

Or open a terminal (applications - accessories - terminal)
sudo apt-get update 
sudo apt-get install ndiswrapper ndisgtk

Run ndisgtk, and find the .inf file you downloaded (the windows driver), and see if it makes it work.

EDIT: forgot to think you might be on a PC.. Are you able to hook up to ethernet for this process? Otherwise you might need a floppy or a cd-r to get the packages.

You can download packages from packages.ubuntu.com/

---

### Post by zanarkand100 on 2006-08-02
i must admit i took all that in and it just went into my brain and made it burn lol

atm im on XP because i cant connect to the net atall. can i search for this online and use it after being burnt to a disk or anyother way?

unless u can not guess i am a complete nub at linux *its my first day* ](*,)

---

### Post by nalmeth on 2006-08-02
Sorry about that :p

This might be easier/
[Ubuntu Plus Addon CD]("https://ubuntuplus.bountysource.com/")

Use Nero, or whatever you used to burn the Ubuntu ISO, to burn this CD.

Do you have a CD for your wireless that came with your card/PC/laptop? If not you'll have to hunt for a wireless driver, which likely will be found on the manufacturers website. They aren't very difficult to find.

When you have both, boot into Ubuntu.

When you're loaded, enter the Ubuntu Plus CD.
Then press ALT-F2. Enter:
gksudo synaptic

click on Edit -> Add CD… from the menu bar.
   	Then click “mark all upgrades,” and if you do a search for “ubuntuplus” you can find meta-packages, such as one that installs media programs and codecs, an internet one which upgrades firefox to 1.5, and others.

The packages you want are ndiswrapper-utils and ndisgtk

When you have everything installed, remove the Ubuntu Plus CD, and enter the floppy/CD that has your windows wireless driver on it.

The menu entry for ndisgtk should be in System - Administration - Windows Wireless, but since I'm not sure, just press ALT-F2 again, and enter:
ndisgtk

Browse to your floppy or CD (both should be mounted in /media), select the .inf file, and hopefully this should enable your wireless card with the windows driver!

Hopefully this is less confusing! :-k

---

### Post by eight. on 2008-02-22
Hi there! I'm new to linux, and I have this exact problem, of the BT Voyager 1040 card not being recognised.

I want to try this method with Ubuntu Plus Addon CD, but the website given doesn't seem to work. Does anybody have the .iso of Ubuntu Plus? I would really appreciate it if someone got back to me with this matter, and helped me get hold of this, so I can finally get off Windows!

Thanks

---

### Post by glennric on 2008-02-23
Ooops, I did this in the wrong tab of Firefox

---

