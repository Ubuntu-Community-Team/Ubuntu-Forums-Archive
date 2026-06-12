---
title: "installing XP on linux"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by parrisjoeyey on 2007-08-15
Hi, First I would like to say how much I love Ubuntu, I have been using it for a month now, and my allegiance is now with Ubuntu,
Unfortunately I jumped the gun a little to fast, and reformatted my drive and put Ubuntu straight  on my computer, but my computer has features that Ubuntu won't support at this stage. e.g. built in Web cam, blue tooth, memory card reader.
So as a result I would like to put XP on my computer as a Dual Boot, I tried this method 
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp) , but got to the section where I had to resize the partion to make room for XP installation, and I assumed it would be the amount of memory XP took up on the CD ( 400MB) so I resized it to that, then it said it would take 8 hours, I wasnt sure if this was normal so I cancelled. 

Any suggestions on what I can do would be great. Should I delete Ubuntu, install XP then do the dual boot? if so how? 
If anyone can help that would be great, 
Hope Ive explained everything properly. I am a beginner. 

Thank you

---

### Post by rdd on 2007-08-15
The 'XP first, then Linux' Method is the easiest one. Resizing a partition can take a long time depending on its size. If you do not need to run 3d graphics applications in Windows you may want to consider using a virtual machine for your windows. 

The advantage is that you can just start it from within Ubuntu, use the windows app you need and then get back to ubuntu straight away without a reboot. 

Virtualbox is an Open Source virtualization tool that is extremely easy to use. 

[http://www.virtualbox.org/](http://www.virtualbox.org/)

If you want to play games you will need a native installation, but if you don't this will probably be more comfortable.

regards

tom

---

### Post by shad0w_walker on 2007-08-15
You have two choices really, either start over fresh (Delete Ubuntu) or you can try the resize method.

If you don't have anything you would lose from reinstalling Ubuntu that is the way i would suggest.       

1. Reinstall XP as you would normally
2. Delete all the partitions it detects in the installer and create a new partition (XP requires alot more space than it does on the CD, i would suggest a few GB so you have growing space)
3. Follow your normal XP install through, setup XP with your drivers, etc.
4. Reinstall Ubuntu, the installer should give you an option to use the free space on your harddrive.
5. Follow the install through like normal.
6. Reboot your system and you should get grub popup.

This should give you a nice dual boot system to play with. You can backup any program settings, personal files you have by just copying your home folder BTW.

If you want to resize your partition i believe the best way to do this would be whilst you are running from the Ubuntu live CD so your root partition isn't mounted.

rdd: Not saying the a VM isn't a very handy tool but you don't seem to have understood what is getting at. Certain pieces of hardware are unsupported in his system so he wants XP back. VMs are good but they will not solve this.

---

### Post by teeceegee on 2007-08-15
I'm not sure about the length of time your resize would take so I can't help there but I have checked and the minimum disk requirement for Windows XP is 1.5Gb so you probably want to have an XP partition that is at least this size plus some space for any applications you want to run.

tcg

---

### Post by Paulmd on 2007-08-15
> **parrisjoeyey said:**
> Hi, First I would like to say how much I love Ubuntu, I have been using it for a month now, and my allegiance is now with Ubuntu,
Unfortunately I jumped the gun a little to fast, and reformatted my drive and put Ubuntu straight  on my computer, but my computer has features that Ubuntu won't support at this stage. e.g. built in Web cam, blue tooth, memory card reader.
So as a result I would like to put XP on my computer as a Dual Boot, I tried this method 
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp) , but got to the section where I had to resize the partion to make room for XP installation, and I assumed it would be the amount of memory XP took up on the CD ( 400MB) so I resized it to that, then it said it would take 8 hours, I wasnt sure if this was normal so I cancelled. 

Any suggestions on what I can do would be great. Should I delete Ubuntu, install XP then do the dual boot? if so how? 
If anyone can help that would be great, 
Hope Ive explained everything properly. I am a beginner. 

Thank you


XP wont install on 400MB of HDD space. That might be how much data is on the CD, but a lot of compressed files get expanded when the OS is actually installed.  3gb is really the *bare* minimum for XP, an antivirus,  and 1 or 2 major apps.  This allows for service packs and updates, as well as the pagefile. (People have been known to cram XP in under 2gb, but ... why? )

Your machine is new enough to include a webcam ( by which I can tell it's a laptop :) ) and a card reader, and bluetooth.  Therefor you SHOULD have the hard disk space to spare, probably at least 40gb. Given the extra whizzbang stuff, I'd guess closer to 80gb or more. 

XP would be more comfortable with 10gb.

An 8 hour install is NOT normal.

---

### Post by parrisjoeyey on 2007-08-15
So it shouldn't take 8 hours to resize?

---

### Post by shad0w_walker on 2007-08-15
It definitely shouldn't take 8 hours to resize.  Did you let the resizer run for a minute or two first? Its possible that th 8 hour thing was just a guess whilst it was calculating the time properly.

---

### Post by parrisjoeyey on 2007-08-15
yeah I let it run for a while

---

### Post by shad0w_walker on 2007-08-15
Im not sure what to suggest on the resizing side of things, I haven't seen a resize take 8 hours before and i can't think of any reason it should take that long. If there isn't anything important/difficult to get setup again on your Ubuntu system it might just be easiest to go with the reinstall option. Also  have you asked around on the gparted forum? They might be more help for partition related things.

[http://gparted-forum.surf4.info/](http://gparted-forum.surf4.info/)

---

### Post by parrisjoeyey on 2007-08-15
btw, one of you guys sent me an email, I accidentally deleted it, please feel free to email me again. thanks.

---

### Post by Paulmd on 2007-08-15
> **parrisjoeyey said:**
> So it shouldn't take 8 hours to resize?

Yes.  1 hour, MAYBE, if a lot of data needs to be moved, on  slower machine. 

Most newer hard drives are capable of moving (at least) 40mb/sec of data.  So carving off a 4OOmb should only take about 10 seconds (give or take). There would be overhead in the seek time, so maybe that might work out to a few minutes, vs a few seconds. Worst case.

Carving off a few GB may take longer. But not 8 Hours longer.

---

### Post by MQMike on 2007-08-15
No question in my mind – Windows XP first (on (hd0,0)), then Ubuntu after that.
The dual-boot setup is very easy, especially if you do XP first.

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)
(aka Qqmike)
Bigpond, GRUB:   [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)
(the classic)

---

### Post by parrisjoeyey on 2007-08-16
Just wanted to say thanks to everyone for their help

I thought Id wait the 8 hours for the repartion, and it worked, wierd hey, but then XP didnt pick up a hard drive, 

So I reformatted, started  again, first with XP, then Ubuntu, all went smoothly, 

Ubuntu works great, 
XP unfortunatly didnt pick up sound device, in my device manager it doesnt have a sound device, funny how Ubuntu picks it up, but Windows doesnt, just proves how good Ubuntu is, 
So now I need to put sound on XP ? any ideas anyone ?
Even if you tell me how to get my motherboards name would be great, without opening my notebook.

---

### Post by vexorian on 2007-08-16
provided you don't need 3d acceleration in windows, I must say virtualbox would be your best friend, it is easier to set up than dual boot, and it is much less annoying than it, and it is simply useful, for example I use windows XP in a virtual box to enable my scanner in Linux.

---

### Post by shad0w_walker on 2007-08-16
Goto this website and download Hwinfo32 (For windows), it will give you all the details you should need to find your drivers.

[http://www.hwinfo.com/](http://www.hwinfo.com/)

---

### Post by pdlethbridge on 2007-08-16
I installed ubuntu on my computer after I installed XP. I split my 80 gig hd in half for each system. In the XP setup, you can set how many gigs you want for XP. Just leave the rest for ubuntu.

---

### Post by Paulmd on 2007-08-19
> **parrisjoeyey said:**
> Just wanted to say thanks to everyone for their help

I thought Id wait the 8 hours for the repartion, and it worked, wierd hey, but then XP didnt pick up a hard drive, 

So I reformatted, started  again, first with XP, then Ubuntu, all went smoothly, 

Ubuntu works great, 
XP unfortunatly didnt pick up sound device, in my device manager it doesnt have a sound device, funny how Ubuntu picks it up, but Windows doesnt, just proves how good Ubuntu is, 
So now I need to put sound on XP ? any ideas anyone ?
Even if you tell me how to get my motherboards name would be great, without opening my notebook.


With a notebook, it's pretty easy. Goto  the manufacturer's website, enter your model# , and download the XP drivers for your sound. If you have an older model, and XP isn't listed as a choice, then choose the windows 2000 drivers.

---

### Post by antharr on 2007-08-19
I run a XP/Ubuntu dual boot and I use VMware in Ubuntu when I just don't feel like rebooting my machine. The easiest way I have found to dual is to install XP on the drive first letting Windoze have the whole drive. Next I use Partion Magic to create a swap partion and a ext3 partion that I will use to install the Linux root file system. After you have created those partions, just install Ubuntu on the ext3 partion and Grub (which allows you to choose the OS to boot into at startup) should be installed with the Unbuntu installation. Take out the Ubuntu CD and it the system should reboot into the GRUB menu allowing you to select XP or Ubuntu.

---

