---
title: "Help !! Grub Loading...Error 17"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-05-14
Hi,
 I have a dual boot with Ubuntu and Vista. And I wanted to reinstall Ubuntu for troubleshooting reasons, so I went into Vista (because of its disk management system) and simply reformatted the drive on which Ubuntu had been installed. I extended its volume and somehow, I reset the partition to be raw so Ubuntu could format it as ext3.

Things seemed fine, I ran the install, I had Ubuntu format its drive as Ext3, and set the mount as '/'. Then during the install it stopped midway and said there might be a disk error and to clean the disk. But I tried installing with a backup copy and the install stopped midway again; I didn't see if there was a message about the cleanliness of the disk or not. It just stopped the install and stayed there on the Ubuntu desktop, to where I had booted with the CD. 

Now when I reboot, I can't get Vista - and I see this: 

Grub (something)...1.5
Grub Loading ... 
Error 17

And it just stays there.  I ran a startup recovery from my Vista disk and it shows that Vista is still there, which is good, but I still can't get past this boot problem with Grub. 

How would I repair this? PLEASE be specific with instructions - I'm not a Coder. Many Thanks for any assistance,...Frank

---

### Post by freebird54 on 2007-05-14
If you are in the Vista recovery mode, you can type fixboot, and then fixmbr to return the boot sectors to 'Vista' mode.  If all you want is Vista to work, that should do it.  If you want a new Ubuntu install to work, just running it would work instead.

What has happened is that the boot record has been changed to point at grub files on the Ubuntu partition - where control could be handed back to Win if desired.  Now you don't have the Linux partition, grub can't find it (error 17) - and can't continue.

Hopefully that both explains it, and allows you to fix it whichever way you want..

---

### Post by Brightbelt on 2007-05-14
Thanks very much for helping....
I'm not sure how I'd enter 'Vista Recovery Mode' (?) but I'll look...Is that a Command Prompt you're talking about where I'd type 'fixboot'? 

>"If you want a new Ubuntu install to work, just running it would work instead."

I assume you mean that I should be able to reinstall Ubuntu successfully after I fix the boot issue. 

Thanks for any clarification,...Frank

---

### Post by Brightbelt on 2007-05-14
Hi,
I tried typing 'fixboot' (without quotations) at the command Prompt in the repair mode with the Vista boot CD and I got back that it was an invalid command;

I also tried typing 'fixmbr' and got the same message: invalid command etc etc. Or 'not a recognized command' or something like that. 

I even did a System Restore with Vista from the Repair mode - of course the Linux partition could not be restored because I had reformatted it.  And that STILL didn't work !!!

I still get this:

"Grub Loading ...Stage1.5
Grub Loading...
Eror 17"

Thanks for your help so far - I appreciate any further ideas on this,...Many Thanks, Frank

---

### Post by confused57 on 2007-05-14
> **Brightbelt said:**
> Hi,
I tried typing 'fixboot' (without quotations) at the command Prompt in the repair mode with the Vista boot CD and I got back that it was an invalid command;

I also tried typing 'fixmbr' and got the same message: invalid command etc etc. Or 'not a recognized command' or something like that. 

I even did a System Restore with Vista from the Repair mode - of course the Linux partition could not be restored because I had reformatted it.  And that STILL didn't work !!!

I still get this:

"Grub Loading ...Stage1.5
Grub Loading...
Eror 17"

Thanks for your help so far - I appreciate any further ideas on this,...Many Thanks, Frank
Hi Frank,  this might be what you're looking for to get your Vista booting again:
[http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)

Added:  I don't know if a filesystem check would help... the gparted live cd is a great tool for doing one:
[http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem)

---

### Post by Brightbelt on 2007-05-14
Thanks Confused,
I appreciate the resource... Unfortunately, I tried that and Nada. I could be missing a subtlety or two on the instructions as well. Those Microsoft documents are notoriously hard to understand. 

They are very poorly written, at least for the layman. 

The thing is: I've googled this problem as well and all the answers I find are so fractured and different from one another - and some are amazingly complex for my novice-level of understanding. 

I may have to call a Microsoft Professional...Or simply reformat and reinstall.

If I simply did a re-install of Ubuntu and wiped the whole drive clean, letting Ubuntu have the whole C:\ drive, would that fix this as well?

I appreciate any help...Thanks, Frank

---

### Post by Shazaam on 2007-05-14
Brightbelt...
We need to get a couple of questions answered first.
Is your pc a pre-built? Such as HP, Toshiba, or Dell?
Do you have a Vista CD/DVD? Or only a "System Rescue Disk"?

---

### Post by Brightbelt on 2007-05-14
Thanks for jumping in.....

My Laptop is a Gateway M674x Laptop, prebuilt. I have the Vista Home Premium Upgrade Disk, from which I already tried doing a startup recovery.

I also have 3 Recovery DVDs that I made the day I bought the computer. If I use these, they will put an Oem version of XP Pro back on.   

Are ya'll still there? I had to break for a while. Thanks for helping, Frank

---

### Post by Brightbelt on 2007-05-14
Sorry !! that's M 675x Gateway laptop....FB

---

### Post by oilchangeguy on 2007-05-14
looks like your best bet is to use the factory restore cd's, and reload xp. then upgrade to vista, and then reinstall ubuntu. i own an m675, darn good computer.

---

### Post by Brightbelt on 2007-05-14
Yes it's a very good laptop, but loud as hell with the processing fan. I don't know about yours ;) 
Frank

---

### Post by oilchangeguy on 2007-05-14
> **Brightbelt said:**
> Yes it's a very good laptop, but loud as hell with the processing fan. I don't know about yours ;) 
Frank

it's a little loud, but you've got a highpowered desktop cpu crammed in a laptop. gotta keep it cool.

---

### Post by Brightbelt on 2007-05-14
I have run a sudo fdisk -l, so I can tell you what I'm seeing in case there's some simple code I can run to help this. Here's what I have:

/dev/sda3 is my Windows Vista   (which by the way IS still there...I just can't get to it in the boot)
/dev/sda2 is the Swap
/dev/sda1 is where Ubuntu used to be

There is other unallocated space I couldn't expand into, but those are what I have. If there's any way to run a simple command from this info, I'm game for trying !!

Thanks for helping,...Frnak

---

### Post by Shazaam on 2007-05-14
Using the LiveCD can you mount the old Ubuntu partition? And see if anything is still there?

---

### Post by Josey on 2007-05-14
Installing ubuntu off the live cd will fix grub.

---

### Post by oilchangeguy on 2007-05-14
if your vista disc is an upgrade disc it's useless. your restore disc's won't wotk either. do you have a true copy of xp only? if so you should be able to boot from that, and use the fixmbr command in the repair console.

---

### Post by Brightbelt on 2007-05-14
But that's what I was saying at the beginning of this thread... The install quits out in the middle and I still can't reboot properly.

Could I be setting something incorrectly in the install?

I set the Ubuntu partition as a '/' mount and the Vista partition as a '/windows' mount etc...

Any ideas,.. Frank

---

### Post by Brightbelt on 2007-05-14
I actually DO have a copy of XP Pro only. How would I run the Fixmbr from that? Thanks, Frnak

---

### Post by Shazaam on 2007-05-14
I dont know if this will work (or how hard it might be to do) since you are using the LiveCD but you might try to download and burn the SuperGrubDisk CD.
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Might work.

---

### Post by oilchangeguy on 2007-05-14
> **Brightbelt said:**
> I actually DO have a copy of XP Pro only. How would I run the Fixmbr from that? Thanks, Frnak

boot the computer from the cd. follow the prompts to get to the repair console. then at the command prompt type fixmbr and press enter. then at the command prompt type fixboot and press enter. then type exit, press enter. restart the computer w/o the cd in the drive. i'm not sure if this will work since you're running vista.

---

### Post by hessiess on 2007-05-14
try booting with the supagrub disk. thias ahould work

---

### Post by Brightbelt on 2007-05-14
It's worth a try...I'm also downloading SuperGrub, so we'll see how that goes...

Many Thanks for the suggestions !!!If these don't work, I'll be back...

Frank

---

### Post by Brightbelt on 2007-05-14
Ok,...Supergrub would not boot - and I tried 2 differently burned CDs with the ISO image. 

So I'm trying XP...and XP wants a Password !!!! I'm in the recovery console, right? It asks me what version of Windows I want to boot, so I type  '1' since it seems to want a number and it asks for a password, so I enter my Vista password and it won't accept it.

Crazy...I may just try wiping everything out and installing Ubuntu. But I haven't been able to get the Broadcom wireless card to work (Intel Pro (R) 1000 CT), so....And that's why I was trying to reinstall Ubuntu in the first place. IE, to clean the Ubuntu system and start over to configure the wireless.

Many Thanks - I appreciate all your help and any further ideas are still welcome,...Frank

---

### Post by Brightbelt on 2007-05-14
Just to clarify, I could not type 'fixmbr' at the repair console...There was only a single digit text field. 
Thanks, Frank

---

### Post by oilchangeguy on 2007-05-14
> **Brightbelt said:**
> Just to clarify, I could not type 'fixmbr' at the repair console...There was only a single digit text field. 
Thanks, Frank

well, that's because you don't have the administrator password. are you the only owner of this computer?

---

### Post by Brightbelt on 2007-05-14
Yes, I am the ONLY owner of this laptop....Frank

---

### Post by oilchangeguy on 2007-05-14
also try at the prompt to enter a password, just press enter. if no password has been set up you'll be able to get to the command prompt.

---

### Post by Brightbelt on 2007-05-14
And the Vista Administrator Password is the only password I know of,...Frank

---

### Post by oilchangeguy on 2007-05-14
please see post #27
and if that does not work it would seem your only option is to reinstall xp, then upgrade to vista. and then install ubuntu.

---

### Post by Brightbelt on 2007-05-14
I'm already at the command propmt. Let me re-tell this since I probably wasn't clear:

When I enter the recovery console, I get the question, "Which Installation of Windows would you like to log onto"

So there's only one (1) space in this field to type, so I type 1. (any other number like 2 or 3 gets rejected as invalid).

Then it asks for a password, which by the way, I can't see how it would have one, since this is a retail, full version of XP Pro.  How could one alter this CD and make a password?

The only password I can think of is my Vista Administrator passwor, so I enter that and it says it is incorrect.

I hope that makes things more clear,...Thanks, Frank

---

### Post by confused57 on 2007-05-14
If you have a Vista recovery DVD, it probably won't restore your mbr, but it might restore your Vista installation to factory conditions...if it is a recovery DVD, you might try contacting the pc manufacturer & ask for an installation cd/dvd.

What you might want to try is to download the gparted live cd:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)
it's only a 45 Mb download & see the link I gave earlier for doing a filesystem check.   What you might try is to use the gparted live cd & delete all your Ubuntu partitions, then make one large ext3 partition, then right click on the partition & select "check", which will check for filesystem errors(again, see the link):
[http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem)
scroll down a bit & in the yellow box is instructions for doing this.

This may not work, but it might be worth a try.

If it finds errors & corrects them, then maybe you can reinstall Ubuntu?

---

### Post by Brightbelt on 2007-05-14
When prompted to enter the password, I also tried just pressing the enter button and that did not work, Thanks, Frank

---

### Post by oilchangeguy on 2007-05-14
no you're not at the c:> yet. you've got to get into the repair console. when asked to enter a password, simply press enter. if no password has been setup you'll be able to get in. this is something you would have been prompted to do when you first got your computer out of the box, and were going thru the first use setup.

---

### Post by Brightbelt on 2007-05-14
OK, I came upon an idea with the Ubuntu Install that could fix this...

At the very end of the setup, there is an 'advanced' button, which (I'm paraphrasing - a noobie thing here) give you the ability to select the mountable boot target (I'm improvising a bit).

The default is set at (hd0). Now...seeing as how my devices are set up as sda1, sda2, sda3, what could I enter here that might help me?

It's just an idea,...Frank

---

### Post by Brightbelt on 2007-05-14
Well whatever I did wiped Vista out.  So I just did a successful, full Ubuntu install. The Error 17 is gone now at least. 

Anyone know how to make a Broadcom Wireless/Intel (R) Pro/1000 CT wireless card work on a Gateway M675x laptop?

Thanks, Frank

---

