---
title: "Dual Booting Win-XP and Ubuntu Question with Boot.ini"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by blakkinferno on 2006-12-03
Well, my computer broke down, NOT for ubuntu related reasons, im glad to report. Well, actually, im not, because its broken. My sister is letting me use her computer until i get a working one again, and she allowed me to create a partition on her existing Win-XP with Ubuntu on it, although she had no idea what she was talking about.

I am following the tutorial at this adress
[http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/](http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/)

and, it was all going to plan. This allows you to keep all your old Windows XP data, so my sister didnt mind, while i have a small partition for my self. However, i came to a part where it said to edit "Boot.ini" in the C:\ directory. [Go to link and see step 9, i believe, under "Installing Ubuntu" in the tutorial.] 

It said to edit the last line with C:\Ubuntu.bin, however, i am not sure if thats what i should do, because it doesn't seem to fit in with my file. This is what the inside of my "Boot.ini" says. What exactly should i type in?
```

[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

```

That is what it says in my Boot.ini file. Can anyone tell me the proper changes i should make? What was said in the tutorial did not seem to make sense with my Boot.ini

Help is extremely appreciated, because i have no hope for my old computer being fixed, which sucks.

Anyway, What should i put in? Thanks in advance, ;)

---

### Post by blakkinferno on 2006-12-03
I am sorry for my impatience, but i decided to bump this thread due to the fact that my sister's comp is open on Windows XP right now, and i would prefer to get it done tonight.

(I am on my Dad's Labtop)

I won't bump it again unless it ends up far down the page. Please reply soon ;)

-rubs hands together-
ME WANTS TO USE UBUNTU ;). Ive always wanted to try linux.

---

### Post by aysiu on 2006-12-03
I would not follow that tutorial. The boot.ini dual boot is too complicated. Just install Grub to the MBR.

Follow one of these tutorials instead:

**Desktop CD**
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

**Alternate CD**
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by blakkinferno on 2006-12-03
OOk, ill follow your advice. However....

If i install it to the MBR, does it do anything bad? Can i still dual-boot? I figured there was a reason it was bad. 

And, how do i get it to the point where i can install it to the MBR? Ive already installed it to the point where the setup has completed and im in Win-XP with boot.ini open and a Ubuntu.bin. What do i do so that i can reinstall it?

---

### Post by sardion on 2006-12-03
Using GRUB in the MBR is actaully much safer than trying to use the Boot.ini as far as potential data loss.  Micorsoft's code is somewhat buggy while GRUB is pretty solid.

The only downside to doing it this way is that when the computer  first starts it shows GRUB (with both Windows and Ubuntu options) but that can creep out Windows people.

I've dual booted both ways and the GRUB in the MBR approach is much better.

---

### Post by blakkinferno on 2006-12-03
Ok, thanks man. I have 2 questions, though, left. You are a big help, ill install it to the MBR ;).

Okay, this is the thing. I have it already installed, but because i followed that tutorial, im stuck in Win-XP without being able to boot straight into Ubuntu.

1) How do i get to the point where i can install Ubuntu again?

My other question is... i still have to follow the part in the guide about partitions, right? Because, the Edgy Eft install from the LiveCD has a slightly different setup... i can't automatically partition.

Summary ;)
----------
1) What do I do to get to the point where i can reinstall Ubuntu properly, with the MBR?
2) Do I still follow the part in the tutorial about partitions? Also, in the LiveCD setup, it asks in the "Install Overview" type page before you click Install. Do you leave it at the default "install GRUB to (hd0)" to install it to MBR?

Please answer these questions fast, i wanna get over to that computer and get Ubuntu working. ;) thanks.

---

### Post by aysiu on 2006-12-03
Yes, *install Grub to (hd0)* will install to the Master Boot Record. There is a way to install Grub to the MBR without reinstalling Ubuntu, but it may actually be easier to just reinstall Ubuntu, believe it or not.

In terms of Edgy's Desktop CD, there should still be an option to Automatically Resize and Use Available Free Space. But since you've already installed Ubuntu, you probably want to use the *Manually Edit Partition Table* option.

You won't actually be creating, resizing, or deleting any partitions, but you should choose / as the mount point for the Ubuntu installation from before and check the box to reformat it.

**Edit**: Turns out the "free space" option is gone in Edgy? Weird. In any case, you can still use the "manually edit partition table" option.

Skip over actually using the partitioning tool and go straight to the mount points.

---

