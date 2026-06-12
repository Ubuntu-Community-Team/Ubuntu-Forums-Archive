---
title: "Problem Logging In"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by BillA1016 on 2006-09-11
Hi. I finally got into Ubuntu but now I get a message on a blue screen that says "Failed t start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose your problem?" There are also lines of code scribbled in the back. I don't know what to do. Thanks for any help!

---

### Post by blakesmith on 2006-09-11
Type sudo dpkg-reconfigure xorg 

this has always worked for me

or  sudo dpkg-reconfigure xserver-xorg

---

### Post by BillA1016 on 2006-09-11
When? In the beginning I type "live video=ofonly" or I get nothing (with that code I get a white line along the bottom but its farther than I've gotten before). Is that what I should type in the beginning and then your code later by using ctrl option F1? Thanks.

---

### Post by blakesmith on 2006-09-11
When you start up the PC and that error shows up there should be a command line... just type in the command I gave you. I have no idea what "live video=ofonly" is.

---

### Post by BillA1016 on 2006-09-11
It says sudo dpkPackage 'xorg' is not installed and no info is available. I don't know what that means... Thanks for your help though, I do appreciate the effort!

---

### Post by blakesmith on 2006-09-11
Did you try sudo dpkg-reconfigure xserver-xorg ?

---

### Post by BillA1016 on 2006-09-11
Yeah it said the same thing (except it mentioned xserver)

---

### Post by Najand on 2006-09-11
What version of Ubuntu are you installing?

---

### Post by BillA1016 on 2006-09-11
Nevermind- it worked. Now its asking for teh desired x server driver. Does it matter? there are lots of choices

---

### Post by BillA1016 on 2006-09-11
6.06 (Dapper Drake) Should I pick ATI? that name sounds familiar...

---

### Post by Najand on 2006-09-11
What type of Graphic Cards are you using?

---

### Post by blakesmith on 2006-09-11
What kind of video card do you have?  
Don't know? Type **lspci** in the terminal and paste it in a reply.

---

### Post by BillA1016 on 2006-09-11
I don't know what kind of graphics card it is. Its an iMac G3 (I'm using a diff comp to talk here) and its not a terminal choice- there are actually options to highlight and pick one.

---

### Post by BillA1016 on 2006-09-11
Ok I just googled- its an ATI standard in G3's so I'm choosing that.

---

### Post by BillA1016 on 2006-09-11
Darn! I pressed enter over ATI (first choice in the list, I didn't move at all) and it did nothing. Its still on the same selection screen. I wonder if its locked up... The CD is going crazy in the drive- I can hear it.

---

### Post by blakesmith on 2006-09-11
Hit the spacebar to enable/diable selections, enter will go to next screen.

---

### Post by BillA1016 on 2006-09-11
That didn't do anything either. The disk is being read like crazy- do you think its just backed up and will respond eventually if I wait?

---

### Post by blakesmith on 2006-09-11
It must have, wait it our or just reboot if you are impatient.

---

### Post by BillA1016 on 2006-09-11
it just beeped and says at the bottom: Killed and then sudo dpkg-reconfigure xserver-xorgati

---

### Post by blakesmith on 2006-09-11
Well, all I can reccommend is to try sudo dpkg-reconfigure xserver-xorg again and see if you have more luck.

---

### Post by Najand on 2006-09-11
Hmm if it fails again try to edit
> /etc/X11/xorg.conf
manually.

---

### Post by BillA1016 on 2006-09-11
I'm rebooting from the disk without entering the command live video=ofonly and just doing your command after Ubuntu loads and I'll see what happens...

---

### Post by BillA1016 on 2006-09-11
Now I'm entering commands and its just not doing anything at all

---

### Post by blakesmith on 2006-09-11
Are you booting off the harddisk or a CD?

---

### Post by BillA1016 on 2006-09-11
CD- that seemed to not be working so I'm doing it again with the command live video=ofonly again- I got farther with that.

---

### Post by blakesmith on 2006-09-11
Is Ubuntu installed on your system or do you just use the live CD?

---

### Post by BillA1016 on 2006-09-11
LiveCD for now until I'm able to install it once in Ubuntu. I would like to partition my hard drive but its only 6GB, so I think that would be sort of useless. I do have the original OS9 restore disk for it, so I could always go back to that if I want MacOS again.

---

### Post by blakesmith on 2006-09-11
You use the install CD to put Ubuntu on your system.  The Live CD is just for "test driving".  So none of the commands for configuring your system will work with the Live CD.

---

### Post by BillA1016 on 2006-09-11
it configured it- I went through the entire process, now I'm back to command lines though and idk what to do.

---

### Post by blakesmith on 2006-09-11
If it configured then you should be able to reboot and have the problem solved... but I am pretty sure it didn't and can't.

---

### Post by BillA1016 on 2006-09-11
it says it can't rewrite it because there isn't enough memory on the device- I'm booting one more time to see if it works- if not I'm quitting for the night and I'll work on it again tomorrow. Thanks for all your help! Its greatly appreciated. You got me farther than I would have gotten myself.

---

### Post by blakesmith on 2006-09-11
It's no problem, I feel obligated to give back to the Ubuntu community because I have received a lot of help here as well.  Good luck! :)

---

