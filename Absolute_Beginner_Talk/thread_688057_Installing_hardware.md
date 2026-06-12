---
title: "Installing hardware?"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by alfredo911 on 2008-02-05
Will installing a 3 1/2 inch floppy cause to OS to lock?

Is it ok to hot connect a printer through USB?

I ask because I did both but not at the same time.  I connected the printer hot, the system identified a need for a driver. Not having a driver I accepted the one offered by the OS.  I then shut down and installed the floppy. Restarted fine and the floppy was recognized. I inserted a disk and was able to open 
files without a problem.  

After use of the computer for a couple of hours it was shut off.  On restart this morning the start was not normal and after many hours I end  by reinstalling from the boot cd.  Your thoughts please.

---

### Post by Mogurijin on 2008-02-05
Both appear like they shouldn't have any problems...

I would search elsewhere for the cause of your problem. Like, problems with power or overheated parts.

---

### Post by alfredo911 on 2008-02-05
Mogurijin first thank you for your observation.  Next I should add that I am the internet with my old computer via window.  Next I had the new computer with the Ubuntu OS sitting in a reduced operating mode - screen black. When I read your message I tried to bring up the system and I got a white letters on black screen.  Error messages from top to bottom same type as  I got early today.

   16.8785321  BUFFER I/O error on device sr0, logical block 329305   
            .
            .
            .
  16.8786361  SQUASJFS  errpr: Unable to read director block 

No reaction the keyboard

---

### Post by alfredo911 on 2008-02-05
The computer does not have a reset button, no reaction to single key inputs. the combination
  Ctrl + Alt +Delete  adds four more line of error message.

How does one reset?  Power off and on?

---

### Post by lsmobrian on 2008-02-05
squashfs is the filesystem for a readonly filesystem (live CD)  
maybe reinstall went bad due to defect in install CD,  If you have the install disc, you might check the disk for defects and see if it has any

(just to check, you arent trying to start your computer with a 3 1/2 disk inserted, maybe it was trying to boot to that)

---

### Post by lsmobrian on 2008-02-05
> **alfredo911 said:**
> The computer does not have a reset button, no reaction to single key inputs. the combination
  Ctrl + Alt +Delete  adds four more line of error message.

How does one reset?  Power off and on?

typically push and hold power button till computer turns off, once off you can push power button to turn on again

---

### Post by alfredo911 on 2008-02-05
Thanks  the power button works as you said.

Applied power as you suggested - got this on the screen and holding at this point

     "  GRUB Loading Stage1.5.

        Grub loading, please wait ...
        Error  15  "

---

### Post by lsmobrian on 2008-02-05
when grub first shows up, can you hit escape and list the options you have.

error 15 means that it cant find the linux image to load in the /boot directory

---

### Post by alfredo911 on 2008-02-05
Ismobrian   Thanks for your patience. I am new at this board and still havent got the hange of the correct buttons.  Power off and on, got the same message and applied the Esc. button and nothing new occured.  Still sitting on the same location.

What does "it cant find the linus image to load in the  /boot directory"?
Further where do you find the key to the error messages?

---

### Post by alfredo911 on 2008-02-05
Using the three keys together got to a screen that gave me the choice of inserting the boot cd.
It loaded the OS and I have two icons showing in the upper left portion of the screen:
Top one is a Folder -" Examples"   -    The lower is a flat box like image with a vector comming out of the Ubuntu symbol and under the box "Instal  all"

I would like your guidence at this point.  If I have to guess I would say that I should exercise the Install which I think will load from the cd to the hard disk  -  as I typed it set off on it's own and asked for the useres name and then indicated in 10 seconds it would move on its own.

---

### Post by lsmobrian on 2008-02-05
When you first load the ubuntu cd, it has a list of options, the first is something like "install or load ubuntu"  There is another option on that menu "Check for defects"  you should try that before you re-install

---

### Post by alfredo911 on 2008-02-05
Did as you suggested.  Checked for defects from the menu.  It is fine. 
Now what is it I should do?  It seems to me I should do a couple of things.
First clean off the hard disk the old Ubuntu OS  - it has been on for about ten days - new computer and who knows what I may have done to it in my wandering.     STOP
While entering this message (old computer with internet connection  - new computer modem driver not available)   The new unit on its own or possibly because I moved the mouse the screen changed and showed a request for "username" with a 10 seconds count down - end of 10 sec. produces a new screen with  " Examples" folder icon in the upper left corner and below that the " Install" icon.   If you try to enter anything in the username box the cycle is repated, same for clicking "System" in the top bar.

      START back   Second if I am going to reload I would like to create a different partition of the hard disk, which I left as one unit of 160 gb.  Possibly as two at approximately 50%.
I don't know how to do that because I don't understand the terms used in the setup package.  Would like your advice. 

Before I forget - Thank you for all of the help.

---

### Post by lsmobrian on 2008-02-05
[www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon](www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon)

here is a nice step by step of install ubuntu.  This is for gutsy, but they also have the same kind of tutorial for feisty, edgy, and dapper (if you need another, goto link and search for other version)

So you have a 160 GB, and you want about 50% for another partition, this will add a few extra steps... It might be easier if you got your system setup with a normal install, where the installer does everything for you. and then you resize with gparted later.

Here is how to do multiple partitions (from memory only, sorry if not accurate)

In the setup in the step "Prepare disk space"
How do you want to partition the disk?

Choose manual

This will bring up a partition editor (gparted)

You might need to select and delete the current partitions (do it if you need to)

select the unused part and click new, choose how big you want and then select the filesystem

1.  you will need one partition for your / 
this is the bootable partition, will hold everything for your system
filesystem needs to be ext3

2.  you will need one partition for your other partition 
likely you will make this your home, to hold your documents
ext3 is a good choice for this partition

3.  you will need one partition for swap 
This should be 1.5 - 2 times the amount of RAM you have 
if you have 512Mb RAM - swap should be around 756-1024MB
linux-swap is the filesystem


so once you have 3 partitions (2 ext3 and 1 linux-swap) continue with the how to link

---

### Post by alfredo911 on 2008-02-07
Again I followed your instructions, including the safer path of not re-partitioning the hard drive until later, and the install went well.  Thank you and thanks for the link to the installation guide, and to the author of that guide. 
I am still working on trying to find a driver for the modem, which has proven to be a job. 
Thanks again to you and to all of the rest of the people that make Ubuntu work.

---

