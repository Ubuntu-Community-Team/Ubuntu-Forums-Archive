---
title: "need help installing ubuntu"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by kathera_lockhart on 2007-05-26
I have never reformatted before, how do you get the disk to start at boot up, I burned Ubuntu on a bootable disc, but it won't start when I reboot my computer. Are there any commands that I need to know about? if so what are they? if not then why isn't it working?

---

### Post by seetho on 2007-05-26
First thing to consider is whether you currently have anything in your hard disk that is important.  You may want to do a backup before going any further.

---

### Post by Cloudedbrains on 2007-05-26
Also did you burn the the Ubuntu file as an IMAGE to disk ??

---

### Post by kathera_lockhart on 2007-05-26
how do you do burn Ubuntu as an image file? yes i know its a major newby question, but I have never done this before.

---

### Post by gmjs on 2007-05-26
Hi,

When you start your machine, there may be a message telling you which key to press to choose which device to boot from.  Unfortunately it varies from manufacturer to manufacturer, but try pressing **F11 or F12** at startup.

You may be presented with a list of bootable devices so you can then pick 'CDROM' from this list and the Ubuntu Live CD should boot.

If this does not work, then it is likely that the system BIOS is not set up to boot from the CDROM drive.  You will have to edit settings in the BIOS to get your PC to read from the CDROM drive at bootup.  To do this, you usually press either **F2 or Delete** when the computer starts.

**Note: Please be careful when changing settings in the BIOS!**

When the BIOS opens you will then need to find the menu that lets you specify which drives to try and boot from.  Normally you either have to state the order that you want the drives to be checked for a bootable partition.  Make sure that booting from the CDROM is enabled and that it is placed above the hard disk in the boot order.

If you need more help, please do supply me with the make and model of your machine and I'll try to supply a more specific answer.

Thanks,

Graham

---

### Post by kathera_lockhart on 2007-05-26
> **gmjs said:**
> Hi,

When you start your machine, there may be a message telling you which key to press to choose which device to boot from.  Unfortunately it varies from manufacturer to manufacturer, but try pressing **F11 or F12** at startup.

You may be presented with a list of bootable devices so you can then pick 'CDROM' from this list and the Ubuntu Live CD should boot.

If this does not work, then it is likely that the system BIOS is not set up to boot from the CDROM drive.  You will have to edit settings in the BIOS to get your PC to read from the CDROM drive at bootup.  To do this, you usually press either **F2 or Delete** when the computer starts.

**Note: Please be careful when changing settings in the BIOS!**

When the BIOS opens you will then need to find the menu that lets you specify which drives to try and boot from.  Normally you either have to state the order that you want the drives to be checked for a bootable partition.  Make sure that booting from the CDROM is enabled and that it is placed above the hard disk in the boot order.

If you need more help, please do supply me with the make and model of your machine and I'll try to supply a more specific answer.

Thanks,

Grahamthank you, I really wanted to know if I was doing it right, now i know I was not, so I will reboot and do what the command promt tells me to do, I am sure mine says F12, I will do that now. Oh as for the make and model of my computer its an Acer, it has a nividia G-Force grafix card, I think its the 600turbo model, and it has a pentium4 processor, I hope thats enough for you to help me.

---

### Post by kathera_lockhart on 2007-05-26
Ok I am have some difficulties I have pressed F12 at startup, it took me to the systems configuration and then I ran into a snag where i had to type in a it looked like DR_DOS]\> or something like that, but I don't know what to type in there, can anyone help me out?

---

### Post by Happy_Man on 2007-05-26
Uh, I think you may have wandered into BIOS and not boot order. Reboot your computer, and watch the screen. Somewhere, it will say <key>=Boot order or something along those lines.

---

### Post by kathera_lockhart on 2007-05-26
> **Happy_Man said:**
> Uh, I think you may have wandered into BIOS and not boot order. Reboot your computer, and watch the screen. Somewhere, it will say <key>=Boot order or something along those lines.

oh, lol silly me, I will try again, I didn't know I was in BIOS, and not in Boot order :p.

---

### Post by Atomic Dog on 2007-05-26
> **Happy_Man said:**
> Uh, I think you may have wandered into BIOS and not boot order. Reboot your computer, and watch the screen. Somewhere, it will say <key>=Boot order or something along those lines.

Some but not all have this boot option.  Going into bios to just change the boot order is not that dangerous.

...well for some maybe it is :o

---

### Post by tgbrowning on 2007-05-26
I'm also new to the forum, but have been messing with laptops for a number of years.  Here's a couple of rules of thumb.

Be very careful on your replies. If you're unsure of your response, sit down, draw up a blank sheet of paper and write down exactly what you've got on the screen.  Do not answer "YES" to something without making sure you know what the result will be.  The Setup and BIOS sections of a laptop are not a good place to experiment unless you're willing to possibly screw things up royally. 

On the other hand, keep in mind that system setups almost always ask you to confirm a really enormous change. If you get asked twice if your sure, you're looking at something that is probably irreversible.

Keep paper around and make notes so you can ask your questions on the forum.  

Browning>>>

---

### Post by kathera_lockhart on 2007-05-26
well I did go to the boot order, but I think I need the proper command line to complete the installation, so I really need this command line, the command promt starts with a [DR_DOS] A\> then thats it, what do I type next?

---

### Post by kathera_lockhart on 2007-05-26
> **tgbrowning said:**
> I'm also new to the forum, but have been messing with laptops for a number of years.  Here's a couple of rules of thumb.

Be very careful on your replies. If you're unsure of your response, sit down, draw up a blank sheet of paper and write down exactly what you've got on the screen.  Do not answer "YES" to something without making sure you know what the result will be.  The Setup and BIOS sections of a laptop are not a good place to experiment unless you're willing to possibly screw things up royally. 

On the other hand, keep in mind that system setups almost always ask you to confirm a really enormous change. If you get asked twice if your sure, you're looking at something that is probably irreversible.

Keep paper around and make notes so you can ask your questions on the forum.  

Browning>>>

well mines a desk top and the reason for me to switch from windows to linux is that my windows XP is not genuine, its all I was able to get my hands on since my sisters fiance had given it to me so i would at least have it to start with, but I now have a rather nasty virus and my anti virus isn't removing it since the virus is one of those ones that runs and hides from your web security so i wanted an OS thats got so few active virii that you won't find them unless your actually looking for them, so I will try what you suggested I should do.

---

### Post by gmjs on 2007-05-26
Can I suggest something?

If you've not formatted a machine before and cannot afford to lose the information stored on your machine, I would strongly suggest not installing Ubuntu just yet.  I made a few mistakes the first time I tried installing Ubuntu.  Trying to remove it again isn't easy either!

If you just want to try installing Ubuntu without making any changes to your current configuration, I recommend creating a 'Virtual Machine' using VirtualBox.

VirtualBox is free software (for non-commercial use) that will let you run a 'computer' in a computer.  Download the Windows version from their website ([http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")) and install in your current Windows installation.  You can then create a new 'machine' and a new 'hard disk' (actually just a file on your machine).  You can then start the new machine, click the window, press F12 and select CDROM from the boot menu and install Ubuntu without any fear of overwriting anything - all from within Windows.

When creating the new virtual machine, specify Linux 2.6 as the OS type.
I'd recommend a virtual hard disk size of at least 5GB for your installation of Ubuntu.

Performance will suffer if you have a small amount of RAM, but that's a small price to pay for the piece of mind you gain knowing that all your data is safe!

Hope this is useful to you,

Graham

---

### Post by seetho on 2007-05-26
Hi kathera,

I noticed that you are truly a newbie to Ubuntu and to computers as well (No offense, we all started out this way).  What i recommend to you is to get someone at least familiar with PCs to sit with you and walk you through on how to changes your BIOS boot settings, how to burn ISO images and how to boot up your Ubuntu CDs.

Others may have different opinions but I think setting up Ubuntu is not really for someone with almost no knowledge about PC at all.  The answers and suggestions you get from here will help only if you know what you are doing.  Otherwise it is best to get help someone that that sit with you.  This is not meant to discourage you, but it is to save you time and frustration.

I hope you get my point when you see that after more than one page of posts we still do not know (no one bothered to ask) whether you have a desktop PC or a notebook and what is installed on it at the moment.  What kind of hardware do you have?  These are all very important considerations before you can proceed any further.

---

### Post by kathera_lockhart on 2007-05-26
well I have a webcam and a mouse from logitech, my printer and my keyboard are from HP and I have indicated that I have a desktop a few posts ago, and I have mentioned it is made by Acer and has a pentium4 processor and a nividia Gforce 600turbo grfx card, I just need to know what the command lines are, the one I have encountered was [DR-DOS] A:\> and I don't know what comes next.

---

### Post by kathera_lockhart on 2007-05-26
> **gmjs said:**
> Can I suggest something?

If you've not formatted a machine before and cannot afford to lose the information stored on your machine, I would strongly suggest not installing Ubuntu just yet.  I made a few mistakes the first time I tried installing Ubuntu.  Trying to remove it again isn't easy either!

If you just want to try installing Ubuntu without making any changes to your current configuration, I recommend creating a 'Virtual Machine' using VirtualBox.

VirtualBox is free software (for non-commercial use) that will let you run a 'computer' in a computer.  Download the Windows version from their website ([http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")) and install in your current Windows installation.  You can then create a new 'machine' and a new 'hard disk' (actually just a file on your machine).  You can then start the new machine, click the window, press F12 and select CDROM from the boot menu and install Ubuntu without any fear of overwriting anything - all from within Windows.

When creating the new virtual machine, specify Linux 2.6 as the OS type.
I'd recommend a virtual hard disk size of at least 5GB for your installation of Ubuntu.

Performance will suffer if you have a small amount of RAM, but that's a small price to pay for the piece of mind you gain knowing that all your data is safe!

Hope this is useful to you,

Grahamwell the thing is the reason I am switching is to get rid of a very stubborn  virus, and so I will never again be plagued by them, and I am pretty sure some of you know what thats like, once its in your system, it will not leave no matter how much you delete it with your anti virus.

---

### Post by gmjs on 2007-05-26
I've checked some forums about the DR-DOS prompt (it's stumped me to be honest - Acer must use DR-DOS to run their rescue program) and the general impression I've got is that it is due to the CD-ROM not booting correctly due to the settings used when it was burned.

In Nero, there is a 'Bootable CD' option, which apparently is not the option to use if burning .iso files.  ISO Mode 1 is the option to choose under Nero to burn the Ubuntu iso file successfully so that it boots.

If you're not using Nero, I'd suggest using ImgBurn.  It's free and the one I used to burn by Ubuntu .iso to CD.  It's available from [http://download.imgburn.com/SetupImgBurn_2.3.2.0.exe]("http://download.imgburn.com/SetupImgBurn_2.3.2.0.exe") (1.5MB).

After locating the downloaded Ubuntu ISO file, ImgBurn will burn it correctly to CD for you.

You should not get a DR-DOS prompt when using this new CD.  If you do, I'm afraid I'm stuck too!

Good luck.

Graham

---

### Post by seetho on 2007-05-26
It seems you are still booting into floppy disk (that what A:\ drives are normally assigned).  Remove any floppy disks you have in your drive.  Just insert the Ubuntu CD and see what happens.

If it does not boot your CD then you'll have to check your BIOS setting to see if you can indeed boot from CD.  To do this, when you reset your PC just press the Delete key (some PC's use F1 and some use F2).  It is safe to press all 3 keys if you are not sure.  This should take you into BIOS setup.

You are connected to this forum so I assume you have another working PC on hand.

---

