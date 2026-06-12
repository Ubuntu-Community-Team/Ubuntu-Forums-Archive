---
title: "Easiest way to switch b/t HDD's- xp and ubuntu on seperate hdd"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by maximo on 2006-09-19
Currently, I just change the settings in the bios to which drive I want to boot first. This isn't terrible for me but my wife doesn't need to be playing around with my bios.  I've been beta testing Vista and when I want it to boot, I only need to have the disc in the drive and it automatically boots off the HDD that Vista is on. Ubuntu doesn't do this so I've had to go into the bios each time I want to switch operating systems. I'm new to linux.

---

### Post by Brunellus on 2006-09-19
Shouldn't be a big deal.  Install Ubuntu onto the drive that you want to install it to, but be sure that GRUB (ubuntu's bootloader) is loaded onto the Master Boot Record of the primary IDE device.  Then, GRUB will boot first, and you should have a choice of which OS you boot into.

---

### Post by maximo on 2006-09-19
I've already got it installed and it's running great. But, I'm not seeing where it gives me an option to which to boot into. Like I said, I've been changing the primary boot drive in my bios to determine which HDD I want to boot from.

---

### Post by Brunellus on 2006-09-19
how did you configure the installs?

---

### Post by bulldog on 2006-09-19
> **Brunellus said:**
> Shouldn't be a big deal.  Install Ubuntu onto the drive that you want to install it to, but be sure that GRUB (ubuntu's bootloader) is loaded onto the Master Boot Record of the primary IDE device.  Then, GRUB will boot first, and you should have a choice of which OS you boot into.

I'm not sure if that goes for Vista.
I have to admit that I did it just once,and the fault could totally be mine,but I couldn't get Vista launched by GRUB.

Maybe it will work fine but I suggest that you install GRUB onto the hdd where your Ubuntu is.

And put the other drive [Vista} as primary boot-disk.
Now the Ubuntu user {you?} should make the choice which one to boot.

Edit:
Can't you press F11 or so [you can see at the bottom of your screen at boottime Del=Bios  F11 change bootdevice} to make a choice wich drive you will use to boot?
Most modern machine have that option,and it's really handy too.

---

### Post by maximo on 2006-09-19
I'm sorry, but I'm confused. Ok, let me clarify. I only mentioned Vista as an example of it being easy to boot into (I don't need to change any bios settings.). I actually formated my HD that had Vista on it and installed Ubuntu. So here's what every thing looks like. I have Windows xp professional installed on one HD and Ubuntu on a completely seperate HD all by itself. My primary boot drive was the one with XP and I couldn't get Ubuntu to boot with making the drive with Ubuntu installed my primary drive. So now, I simply change my primary boot drive to change operating systems. 

I would like it to just ask me when I start my computer which I would like to use, but it never does. Is there a way to have this happen or do I have to continue to change the boot priority.

---

### Post by maximo on 2006-09-19
I haven't tried the F11 thing. I'll try it when I get home.

---

### Post by confused57 on 2006-09-19
This may be an option for you:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by bulldog on 2006-09-19
Oeps my misunderstanding.

Well what you want to comply is very easy.
[The non booting thing of Ubuntu has something to do with counting hdd's]

I suggest you make your Ubuntu hdd the primary boot device and install GRUB on that device.
It will detect windows on your other hdd and will make an entry for it in your GRUB menu.

You need the live cd and need to boot from it.
When you booted into Ubuntu's live cd you have to do the following.

When you get to the desktop open a terminal and enter. (I am going to give you the commands and then I will explain them later)

Code:

sudo grub


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


find /boot/grub/stage1

This will return a location. 
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


setup (hd0)


Finally exit the grub shell
Code:

quit

If you have questions,just shoot.

---

### Post by bulldog on 2006-09-19
> **confused57 said:**
> This may be an option for you:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

Very nice HowTo, thanks.

[bookmarked]

---

### Post by confused57 on 2006-09-19
> **bulldog said:**
> Very nice HowTo, thanks.

[bookmarked]

Thank you for the compliment...at least with this method, grub isn't installed to the Windows mbr...you essentially have Windows and Ubuntu independently on 2 separate drives and it's easy to just reconnect the Windows drive as the primary master, if there's a problem with Linux...I think this is an ideal setup for beginners.  I know enough about Linux now, that I don't believe I'd have an issue installing grub to the Windows mbr, but I just prefer the method that I outlined.

---

