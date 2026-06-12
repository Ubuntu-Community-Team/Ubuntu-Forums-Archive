---
title: "Remove Ubuntu from Windows?"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Ginoxy on 2007-08-09
Hello 

I have a question, Can i Delete Linux Ubuntu manually from :

My computer : Manage : Disk Manage : and then delete OR format both Linux and grub ?

and btw i have windows on a different Disk (I have 2 Disks - Disk0 has C and D & Disk1 has L & Linux & Grub


Regards,

---

### Post by chewearn on 2007-08-09
Since you have linux and windows on different harddisks, simply unplug the linux harddisk from the computer, see if windows still boots.  If it does, then you can delete the harddisk with linux entirely without any problem.

---

### Post by lixy on 2007-08-09
You can format the Ubuntu partition from the hard drive. Removing Grub however involves writing off the bootloader.

---

### Post by Ginoxy on 2007-08-09
You are asking me to take the 2nd hard disk from the cpu ? i can not do that at all

Here is the pic of my current 2 hard disks

[http://ubuntuforums.org/attachment.php?attachmentid=40201&stc=1&d=1186633790](http://ubuntuforums.org/attachment.php?attachmentid=40201&stc=1&d=1186633790)
disk.PNG

Regards,

---

### Post by chewearn on 2007-08-09
> **Ginoxy said:**
> You are asking me to take the 2nd hard disk from the cpu ? i can not do that at all

By unplugging the second harddisk temporarily (sorry, I add "temporarily", in case you didn't realise this :)), it is a simple (all-in-one) check to see if you can immediately and safely delete ubuntu.

---

### Post by foxholeunder on 2007-08-09
> **Ginoxy said:**
> Hello 

I have a question, Can i Delete Linux Ubuntu manually from :

My computer : Manage : Disk Manage : and then delete OR format both Linux and grub ?

and btw i have windows on a different Disk (I have 2 Disks - Disk0 has C and D & Disk1 has L & Linux & Grub


Regards,

If I am reading this right both Grub and Linux are on the same drive .... In that case you can reformat the linux drive from within Windows.

However, this will delete the Grub bootloader and assuming you have Grub to ask you witch OS you wish to boot this could cause Windows to not want to boot after removing Linux. 

If this occurs you can fix Windows bootloader by booting from your Windows disc and repairing, after which you should be able to boot normally into Windows without losing anything in Windows.

Otherwise sorry to hear you are leaving Ubuntu and best of luck! Should you decide to give Ubuntu another go you can always find useful help here!

---

### Post by Ginoxy on 2007-08-09
foxholeunder

im not leaving Linux Ubuntu , im downloading Wubi and i know its unofficial ubuntu but i will give it a try .. regarding what you said 

I will delete Ubuntu it from windows (under disk management) then if anything goes wrong i will need to put the windowsXP cd then from there i can fix it right ?

---

### Post by ticklecricket on 2007-08-09
> **Ginoxy said:**
> foxholeunder

im not leaving Linux Ubuntu , im downloading Wubi and i know its unofficial ubuntu but i will give it a try .. regarding what you said 

I will delete Ubuntu it from windows (under disk management) then if anything goes wrong i will need to put the windowsXP cd then from there i can fix it right ?


May I ask why you're doing that? Wubi isn't any different from Ubuntu, it's just a tool that allows linux to reside in a file on a windows partition rather than on a seperate partition. Useful if you've got one disk that was pre-formatted to be all windows. But since you've already got a paritition set aside for linux, there shouldn't be a need for that.

---

### Post by foxholeunder on 2007-08-09
I was thinking of giving Wubi a shot inside Windows myself... I run Windows inside a Virtual Machine so I can have it handy when I need to trouble shoot questions friends/family have.

Otherwise, yeah if your Original bootloader for Windows is no longer there you will need to do a repair from the Windows installation cd.

If it is still in tact you may still be able to boot into Windows just fine with no need for repair. 

FYI: I use VirtualBox for my virtual machine to run Windows... I do a lot of server setup practices using virtual machines for my Ubuntu server boxes in a virtual environment before I implement them on my real hardware. If I screw up I just roll back the snapshot begin again.

---

### Post by Ginoxy on 2007-08-09
Well in this case i will delete all partitions regarding my linux and see what will happen

---

### Post by foxholeunder on 2007-08-09
Good Luck!

You should be just fine in doing this, you may just have to spend some extra time repairing the WIndows boot loader.

Alternately from Wubi you can install a virtual machine on Windows and install Ubuntu in it. Although I must admit I myself am curious about the development state of Wubi.

---

### Post by Ginoxy on 2007-08-09
Hi again, 

Seems that GRUB stock there and wont let me go to windows ! gave me the "error 17" ! 

now i installed linux ubuntu again everything is fine with me. 

and by the way i tried to go to MS-DOS and make fdisk /mbr

it is not recognized !

---

### Post by AlexenderReez on 2007-08-09
> **foxholeunder said:**
> Good Luck!

You should be just fine in doing this, you may just have to spend some extra time repairing the WIndows boot loader.

Alternately from Wubi you can install a virtual machine on Windows and install Ubuntu in it. Although I must admit I myself am curious about the development state of Wubi.

no..wubi already has its stable released

---

### Post by Ginoxy on 2007-08-09
im going to install Wubi on my laptop but i have to uninstall ubuntu from this PC first

---

### Post by duydaniel on 2007-08-09
> **Ginoxy said:**
> im going to install Wubi on my laptop but i have to uninstall ubuntu from this PC first

try this:
> 
Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.
Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer.

from: [http://www.techzonez.com/forums/archive/index.php/t-3975.html](http://www.techzonez.com/forums/archive/index.php/t-3975.html)

---

### Post by vexorian on 2007-08-09
yes, FIXMBR will fix your issues.

In case anyone finds this thread with google:
- go to control panel.
- Administration tools
- Disk management
- Select the Linux partitions, and format them as NTFS.
- Then insert the windows XP CD and reboot
- Enter recovery console (by pressing R when the installer is ready)
- type FIXMBR
- reboot windows

Now there is going to be a new drive in "my computer"

---

### Post by Ginoxy on 2007-08-09
i dont get it at all !!! im kinda lost now :(

okay !! now i have 2 Hard disks 

do i need to format first then boot from the CD or booting from windows XP's CD then formating later from computer management ?

---

### Post by duydaniel on 2007-08-09
> **Ginoxy said:**
> i dont get it at all !!! im kinda lost now :(

okay !! now i have 2 Hard disks 

do i need to format first then boot from the CD or booting from windows XP's CD then formating later from computer management ?

I believe so... format Linux hard drive as NTFS first (in windows). Then try to boot from XP CD keep going until you see something like fress R to reinstall or repair...

---

### Post by vexorian on 2007-08-09
You have already formatted the disk -.-

---

### Post by Ginoxy on 2007-08-10
THANKS A LOT GUYS 

ITS WORKING AGAIN :):guitar:

---

