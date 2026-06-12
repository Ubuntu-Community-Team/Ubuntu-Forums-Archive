---
title: "Please Help!!"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by Rabbitez on 2007-08-01
I have 2 partitions, one with windows on it, another is backup.

I need to take my backup files, and put them onto an external hard drive.

I am using the Ubuntu live CD

It says I don't have permission to put the files onto the external HDD, how do I do this?

my windows copy is broken. :P

---

### Post by BobCFC on 2007-08-01
Try moving the files as root.

On the live cd.. open a Terminal from Applications->Accessories->Terminal

and type **sudo -i** 


Then you could either move using the command line or even typing **nautilus** as root should let you drag & drop / copy & paste

---

### Post by mathewb on 2007-08-01
what filesystem does the external HDD use? If it's NTFS, you will need to manually mount the HDD using the command "sudo ntfsmount /dev/xxx /mnt/" replacing xxx with the device name (usually something like sda1 for a usb device).

---

### Post by lisati on 2007-08-01
Sometimes Ubuntu doesn't like "raw windows" disk formats, and needs a little help writing to disks formatted for/by windoze. You might want to check out NTFS-3G

---

### Post by Rabbitez on 2007-08-01
mm hmmm,

The hdd is NTFS, and using sudo -i didn't work, still denied for some reason.

How do I find out my drives name? As far as I know it's called "disk-3"


but when I try to mount it in terminal it says it does not exist :(

(You might want to know I tried to install Ubuntu onto the second partition, and doing so resulted in my windows installation not working, after the bios screen, it just says "No operatiing system found" or something similar, and Ubuntu doesn't seem to be installed anyway :confused:  After I have backed this up, I intend on re-installign windows, then letting Ubuntu afterwards to resize the partiton.)


Thanks for your help guys, appreciate it.

---

### Post by Rabbitez on 2007-08-01
The disk is read-only, how do I allow myself to edit it's contents then?

---

### Post by ugm6hr on 2007-08-01
I think GParted LiveCD has ntfs-3g included (and ? KNoppix too) - so that might work for you.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
[http://knopper.net/knoppix/knoppix51-en.html](http://knopper.net/knoppix/knoppix51-en.html)

Try one of those (from LiveCD) to mount your HD (internal and external), and then copy files across.

Having successfully done that - if you are serious about Ubuntu - set partitions with Gparted first, then install Windows, and then Ubuntu.

---

### Post by Rabbitez on 2007-08-01
Thanks, will do, but isn't it easier to install windows first then to just install Ubuntu after, ubuntu comes with the utilities to compress the windows partition and to install ubuntu...?

---

### Post by ugm6hr on 2007-08-01
> **Rabbitez said:**
> but isn't it easier to install windows first then to just install Ubuntu after, ubuntu comes with the utilities to compress the windows partition and to install ubuntu...?

Not really.  For data integrity (and speed) - it is better to set / resize partitions *before* writing any data to the HD.  

My suggestion: 
1. Create a primary partition for Windows (whatever size you want), and then an extended partition for Ubuntu (but do not create any logical partitions within the extended) in GParted LiveCD
2. Install Windows to primary partition.
3. Install Ubuntu with "Guided - Use largest continuous free space" option.  It will create 2 logical partitions within the empty extended partition - 1 for Ubuntu (/) and 1 for linux-swap.

Your method will work though, but is just a bit messier.

---

### Post by Rabbitez on 2007-08-01
Ok, thanks for that, I will try your method, cheers.

You said it was messy? what do you mean? does it make windows liable to break? not that it isn't liable to break all the time :tongue:

or is it more of Ubuntu not seperating the files properly?

---

### Post by ugm6hr on 2007-08-01
Messy... not a good choice of word.

But performing a resize procedure on a partition potentially puts the data contained within at risk - which is why it is recommended that you backup prior to resizing.  

GParted is pretty good - but there is always a risk.  It would be a real nuisance to have to reinstall Windows twice because of a corrupted file, given how long it takes.

Since you are reinstalling Windows anyway - it makes sense to create the partitions first, and then install, rather than the other way round ( a function which is made available for people who are installing on a computer that they have been using *successfully* with Windows :D ).

---

### Post by Rabbitez on 2007-08-01
ehe, ok


Ill say if I get stuck with gparted..

Well, before I burn it..  (stupid question.. sorry)

How do I run gparted? in windows? 

though I bet I just boot from it right?

BTW; I got windows working, I needed to change the boot flags.

yah, pretty stupid, I have been using windows all the time, I swear it makes your brain corrode.
Must be the colours of the blue screen you get :lolflag:

Anyway, with all my data succesfully backed up

I presume I just pop in the gparted CD? and go along from there?

---

### Post by ugm6hr on 2007-08-01
> **Rabbitez said:**
> I presume I just pop in the gparted CD? and go along from there?

Correct.  Easy-as-pie.

If it doesn't work - try some of the alternative boot options (I used 2nd option).

---

### Post by Rabbitez on 2007-08-01
Only easy as pie for someone who has a half idea what they are doing :confused:

ok, so, I have booted from the gparted disk, and I get a long list, use the arrow keys to select a entry, press enter to boot the selected os...

I presume you know what I am talking about..

Which do I choose? and what do I do from then on? I tried the first one on the list.. it asks for a keymap?
I did enter.. the default one..
then language or something.........


then it does some copying.. am I on the right track??

---

### Post by ugm6hr on 2007-08-01
> **Rabbitez said:**
> then it does some copying.. am I on the right track??

Yes.  I use the second option - but if the first works, that's OK.  They all arrive at the same place.  Selecting language and keyboard should be obvious (I use UK, but US is default).

---

### Post by Rabbitez on 2007-08-01
uh oh....

I got past all that, but when all the things have loaded or whatever they are doing, when it says [COLOR="Lime"][ok][/COLOR] at the right hand side, my screen says "MODE NOT SUPPORTED" does that  mean I have the wrong version? or the wrong option when it starts?

eep.

---

### Post by Rabbitez on 2007-08-01
No worries, I used an older tft monitor, I can see it now...

---

### Post by Rabbitez on 2007-08-01
What shall I enter for space preceding and space following?

I have a 180gb Hdd currently installed.

I am going to have 90gb for each OS.

I want the first partition as primary I take it?

and filesystem NTFS

Round to cyclinders checked?

---

### Post by Rabbitez on 2007-08-01
Ok.


I have two partitions, each about 93gb

I have a space between them of 23.53 mb That enough?

Each partition is NTFS, and is primary.

Everything ok?

---

### Post by ugm6hr on 2007-08-01
> **Rabbitez said:**
> Ok.

I have two partitions, each about 93gb

I have a space between them of 23.53 mb That enough?

Each partition is NTFS, and is primary.

Everything ok?

No.
1st partition - primary 93GB NTFS
2nd partition - extended 93GB (no file  system)

Round to cylinders - yes.
The space between is irrelevant.

---

### Post by Rabbitez on 2007-08-01
Done, I'll install windows xp, then Ubuntu after, and it should (hopefully) all be ok.


Sorry if I have wasted your time, I have only used Ubuntu once or twice before, but now I intend on getting to grips with it and moving on after to a more advance os...

Thanks a lot for your time, you have been a great help :D

---

### Post by ugm6hr on 2007-08-01
I'd recommend you allow Windows to format the primary partition NTFS (during the installation procedure) again prior to installing.  It is just a bit safer that way...

---

