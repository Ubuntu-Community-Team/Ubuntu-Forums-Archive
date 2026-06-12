---
title: "Boot questions"
date: 2012-07-18
forum: Apple Hardware Users
---

### Post by Hedgehog9597 on 2012-07-18
BOTH QUESTIONS HAVE BEEN RESOLVED IN THIS POST: [http://ubuntuforums.org/showpost.php?p=12115181&postcount=6](http://ubuntuforums.org/showpost.php?p=12115181&postcount=6)
Props to yentl.

***Original Post***

I have two questions:

Question 1.  For this question, refer to the first attachment for a screenshot.

When the rEFIt screen displays, I get three icons.  What is the far left icon (highlighted in the picture)?  Do I need it? When I press enter while it is selected, I get an error.  If I do not need it, how can I get rid of it? It is quite irritating.

Question 2.  For this question, refer to the second attachment for a screenshot.

After I select the penguin and press enter, I get this screen (see photo).  I do not get this screen after selecting the Apple icon, and it seems quite unnecessary to have a secondary boot selection screen.  Is this screen normal?  How do I get rid of it if it is not?

Thank you very much to anybody and everybody who takes the time to help me out; I appreciate it very much.

---

### Post by oldfred on 2012-07-18
That is the standard grub2 menu. It only shows a menu if the os-prober finds more than one operating system. You can turn off os-prober so it only finds Ubuntu or use Grub Customizer to change grub.

HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html)
The Grub 2 Guide - drs305 also link to grub customizer
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

Then 
sudo update-grub

---

### Post by Hedgehog9597 on 2012-07-19
So... I'm dumb

I just downloaded Grub Customizer and unchecked ALL the boxes, because I thought that's what I had to do to make the screen go away... now I can't boot into ubuntu :P

So... what do I do? I'm kind of lost at this point...

Also, CAN I even get that screen to go away?  Because I still get a command-prompt-esque Grub screen that comes up when I try to boot linux on the rEFIt screen.

---

### Post by nsicad on 2012-07-19
> **Hedgehog9597 said:**
> I have two questions.

Question 1.  For this question, refer to the first attachment for a screenshot.

When the rEFIt screen displays, I get three icons.  What is the far left icon (highlighted in the picture)?  Do I need it? When I press enter while it is selected, I get an error.  If I do not need it, how can I get rid of it? It is quite irritating.



Question 2.  For this question, refer to the second attachment for a screenshot.

After I select the penguin and press enter, I get this screen (see photo).  I do not get this screen after selecting the Apple icon, and it seems quite unnecessary to have a secondary boot selection screen.  Is this screen normal?  How do I get rid of it if it is not?

Thank you very much to anybody and everybody who takes the time to help me out; I appreciate it very much.

Q1.

It is partition of hard drive. I get this one as well in my usb install drive. I don't know how to get rid of it. 

Q2.

You can delete the second menu if you don't need. it is in grub.cfg file. This file is in the boot/grub directory.

Just to clarify this, I meant editing the file (i.e removing the entries of the old kernel) - the second menu . Not removing the file grub.cfg.

---

### Post by YannBuntu on 2012-07-19
> **nsicad said:**
> You can delete the second menu if you don't need. it is in grub.cfg file. This file is in the boot/grub directory

:o Are you sure Ubuntu will still be able to boot after that? have you ever tried on your own PC?


> **Hedgehog9597 said:**
> I just downloaded Grub Customizer and unchecked ALL the boxes, because I thought that's what I had to do to make the screen go away... now I can't boot into ubuntu :P

I think what you did with GRUB-Customizer is removing all entries to Ubuntu.
Please indicate your [BootInfo]("https://help.ubuntu.com/community/Boot-Info") URL.

---

### Post by yentl on 2012-07-19
1) The first icon probably indicates that GRUB has put its initial program loader in the EFI partition. I'm not sure how this might have happened though -perhaps you chose to install GRUB to the device rather than to the linux partition? You shouldn't need the initial program loader if you've got rEFIt, so if you want to keep rEFIt you can always just delete the file (although make sure you can boot into Ubuntu from the linux icon first!). Or you could bless the initial program loader from OS X to make the firmware launch GRUB by default. To do so, mount the EFI partition (should be /dev/disk0s1 in OS X) at /Volumes/mountpoint and run:
sudo bless --folder=/Volumes/mountpoint/EFI/ubuntu --folder=/Volumes/mountpoint/EFI/ubuntu/grubx64.efi
Check that you CAN reach the rest of GRUB and boot into both operating systems before blessing, though! :)

2) In Ubuntu (once you can boot into it) run
sudo nano /etc/default/grub
This helps you configure the grub file.
In this you'll find an option entitled GRUB_TIMEOUT. This is the length of time for which it displays the GRUB boot menu before booting into the default selection. If you want to keep rEFIt and get rid of this menu, simply set this to 0 and then run
sudo udpate-grub.
Then a new grub.cfg will be generated with that preference taken care of. There should be an option called GRUB_HIDDEN_TIMEOUT which is unset by default. If you set this to an integer value this is the amount of time, in seconds, where if you press the shift key you can bring up the GRUB menu. If you don't press then the default selection is booted and you don't see the boot menu. This is how I've set it up on mine and it seems to work!

---

### Post by Hedgehog9597 on 2012-07-19
Thanks everybody! I fixed both of my problems.

---

### Post by yentl on 2012-07-19
Amazing! Out of interest, how did you do it?

---

