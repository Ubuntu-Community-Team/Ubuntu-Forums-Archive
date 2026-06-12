---
title: "[SOLVED] Ubuntu 7.10 Installation Problem, Please Help"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by verkiel8 on 2007-12-15
I'm new to Linux, but I've searched around the net and eventually got a recommendation for Ubuntu.  So I came to the site and I d/l the Ubuntu 7.10 iso.  I did the checksum and it matched, I burned a cd on 1X.

When I reboot, I press F12 to go to boot options and select the CD drive.  It comes to a screen which gives me options to install and I've selected a couple different ones with the same outcome.  I even did the option for error checking and it came back with no errors.

Once I select the option to install it begins and then 4 lines of text come on the screen and it blinks a few times.  Afterwards, it has a cursor in the shape of an X.  Then a message is displayed saying that it has to go into low graphics mode, so I say Continue.  Then, it goes  back to the black command prompt type screen with the 4 lines of text and it just sits there with a blinking underscore _ .  I type things in and I hit buttons and they all work.. But it will never do anything else.

What am I doing wrong?

I have a 250 GB HD with partitions separated into 30GB
The first one (C) is system, the 2nd one (E) is XP Home, the 3rd one (F) is XP Pro, the 4 & 5 (G,H) are not formatted, the 6 7 8 ones (I,J,K) are for storage.

I want to keep the existing XPs because my wife uses the computer and she of course doesn't want anything out of the ordinary when she goes to use it.  And swapping drives would be a huge pain.

Help if you can please.

---

### Post by bcom on 2007-12-15
Maybe you should download the Alternate Install CD.

This is a tex-based install and might get you past the display problem you are experiencing.

---

### Post by ajgreeny on 2007-12-15
Obviously a graphics driver problem.  What graphic card do you have?  It may be that you have got to a console login point and could do just that, ie login with your username and password, then try to sort out the graphics problem.

If the last line on your screen says ubuntu 7.10 login, do so (remember, when you type your password, nothing shows on screen at all) and then type sudo dpkg-reconfigure xserver-xorg and go through the screens accepting all the defaults until you get to the graphics section, when you need to select the appropriate driver for your card, if you know it or just vesa if you don't, to at least get minimal graphics on screen, then we can try to get the right driver sorted properly for you.

---

### Post by verkiel8 on 2007-12-15
So after I posted this, I decided to keep trying and I rebooted and went through the process again.  Except this time I chose the option "Start in safe graphics mode" (or something like that).  

I guess it's running like a 'live cd' now?  Anyway, it's great and all, but it's really slow, and I still want to install it onto one of my unformatted partitions.

There's an icon that says "Install" and I go through this process, however I don't know which option to choose. 

Is there a tutorial or a message on how to do this somewhere?

ajgreeny:  I have an intel onboard graphics card (it's a dell dimension B110 system) and I also have an nvidia geforce 5200 in a pci slot

Also, it says nothing about login or password, so I'm not sure if that's it...

By the way, thank you both for responding so quickly!

---

### Post by Lvcoyote on 2007-12-15
Try disabling the onboard video in BIOS and just use the Nvidia card.

---

### Post by Ub1476 on 2007-12-15
The reason it's slow is because you're running of from a CD. It will go blazing fast when you get it installed. 

When you come to the partition manager, you should have about four options:

[LIST]
[*]Resize HDD (on top)
[*]Use largest free space available (this will choose a partition with no storage on)
[*]Use entire HDD
[*]Manually
[/LIST]

I usually either use "Resize HDD" or "Use largest (...)". They are very straightforward and I've never had any problems with them. But then again, I've never had 8 partitions on my HDD (I don't know what Ubuntu will do with two partitions which is not formated if choosing option two).

Before you install you'll get a list of options you have chosen. which you can look through. 

BTW, Grub will replace Windows bootloader, but I guess you know already (no problems with it of course).

Good luck:)

---

### Post by bcom on 2007-12-15
Yes, it sounds like you have the Live CD running.  The reason it runs slow is because the Live CD is loaded into RAM bypassing the hard drive entirely.   So, unless you have a massive amount of RAM, the computer will be a bit slow and jerky.

With regard to installing, the video card you have installed in the PCI slot could be problematic.  I  am not sure.   Before you install, it might not be a bad idea to take that video card out and try the Live CD again to see if you experience the same problem.
 
Rather than remove the nvidia card, you could disable the onboard video as suggested  -- then try the Live CD again.  The reason I recomend experimenting a little before doing the actual install is that you might be able to pinpoint a potential problem and research solutions before you do the install.   This could save you a lot of grief later on.

Remember, the fact that you had to use the safe graphics mode to get the live CD running tells you that there is a potential hardware or driver problem.

---

### Post by Duck2006 on 2007-12-15
This may help.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by verkiel8 on 2007-12-15
OK, so in the process of waiting for replies, I decided to throw caution to the wind and go ahead and try and install it myself.. (I'm impatient sometimes)..

I had to go with the manual install because the first option wanted to erase the whole disk, and the second option I had was to use free space, which it apparently doesn't recognize unformatted partitions as free space, and the 3rd option was manual.

Well, I went through and had NO problems at all, and I'm really excited to use ubuntu!

Thanks to everyone who gave their time to try and help me, it is and was very much appreciated!!

---

