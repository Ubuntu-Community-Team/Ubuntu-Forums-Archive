---
title: "boot trouble / file recovery"
date: 2009-06-26
forum: Apple Hardware Users
---

### Post by waznot on 2009-06-26
I have a Mackbook4,1 partitioned with rEFIt (OSX and Intrepid or Jaunty? 64-bit)

I would like help with one or all of the following
	**1)** Fix problem booting into Ubuntu
	**2)** Recover a file from a Ubuntu partition I cannot boot into
	**3)** The words to come out of my mouth when I try to talk to the hot girl at my local cafe.



**(1)** Fix problem booting into Ubuntu

After running into a few problems with Jaunty I decided to delete its partition and do a fresh install of Intrepid.

After installing Intrepid the update manager and Synaptic Package manager misbehaved. The update manager would only want to do a partial update and Synaptic wanted packages fixed (or something like that). It was for this reason, and not being able to add programs ("..needs so and so and this will not be installed..") that I decided to go back to Intrepid.

So I ran the update manager. During this process a dialog box for LILO popped up:


 **It seems to be your first LILO installation. It is absolutely necessary to run liloconfig(8) when you complete this process and execute /sbin/lilo after this. LILO won't work if you don't do this.**


I had no idea what LILO was so I copied the above message, marked it for my attention, let the update complete and hit the little restart icon that showed up in the notification panel.

I now know a little more about LILO after trying to work out why I couldn't boot into Ubuntu! After booting into Ubuntu from rEFIt I jotted the following down from the screen:



[B]Boot from (hd0,2) ext3 767f693f-8e4a-ba8c-e520e4ffa40d
Starting up [  1.257332] i8042.c: No controller found

Gave up wait  Common Problems:
	-Boot args (cat/proc/cmdline)
		-Check rootdelay=
		-Check root=
	-Missing modules (cat/prac/modules; ls /dev)

Alert! /dev/disk/by-uuid/ 767f693f-8e4a-ba8c-e520e4ffa40d does not exist. Dropping to shell!

BusyBox v1,10.2(Ubuntu 1:1.10.2-2ubuntu7)
	built-in shell (ash)

Enter 'Help' for a list of built-in commands

(initramfs)[/B]



I tried to type 'Help' but the keyboard was inactive.  I held down the power button until the computer turned off and tried unsuccessfully to boot again. I noticed this time there was a mention of booting into 9.04 Kernel. So maybe it decided to upgrade to Jaunty on it's own.

So I would like to boot into Ubuntu to recover an important file, or...




**(2)** Recover my file from a Ubuntu partition I cannot boot

Through the Intrepid LiveCD I was able to recover a folder and a couple files from the Desktop.  But the important file is in the folder 
/media/disk/home/wazent/Desktop/popbackonnewinstall250609
I foolishly cut and pasted this folder (rather than copy) from my external hard drive to the desktop of the fresh install.  I cannot access it.
 
I tried to use the terminal to look up how to change the folders permissions.  If you haven't guessed yet, I'm new to all this stuff.

The folder showed a crossed box emblem so I thought I would chmod it. At lest I think that is what I did. I really should have had a break at this point. I did something like
chmod -rw popbackonnewinstall250609
Then after a while I went huh what oh oops
chmod +rw popbackonnewinstall250609

After this the emblem disappeared and I could open the folder but could not see the contents.

The file I want is in OpenOffice format with a copy in pdf format.


**(3)** ....sigh..

Thanx

---

