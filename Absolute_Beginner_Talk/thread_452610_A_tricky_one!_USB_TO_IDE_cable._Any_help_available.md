---
title: "A tricky one! USB TO IDE cable. Any help available???"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by Ganda_Melga on 2007-05-23
Well, this is a very old machine. It's a PII at 350 Mhz, 192 meg RAM, 32 mega graphics board, and a 4 Giga HD.
My problem is the very small HD. Just with xubuntu, some packages I downloaded, some video clips and musics the HD is almost full! So a bigger disk would be very nice.

It happens that I have a 40 giga HD in the shelves. So I tried to connect to 40giga HD to this computer using an IDE connection. No such luck. The computer doesn't recognise the drive, in fact it freezes in the BIOS boot trying to recognise it. Some older boards have a limitation and don't support drives bigger than 30 giga, or so it appears...

I have an weird cable, complete with power source, an USB to IDE cable. In theory you can connect any IDE device through an USB port using this cable. I've tried this cable under windows and the results are a bit weird. In a computer it recognised the hd. In another computer it doesn't, but it says there's a mass storage USB device, and gives a code 10 error. Results seems to vary from computer to computer.

However under Linux the hd isn't recognised at all! Not as an Maxtor HD, nor even as a USB mass storage device.

There is a small cd with drivers for windows 98, but no drivers for linux.

So, my question is: How on earth can I connect the 40giga HD to this computer? Does anyone had the same problem before? Where can I find the drivers to use the USB to IDE cable??


I also have a spare 10 giga drive. It belonged to an xbox games console who gave up the ghost. Now, this 10 giga drive is recognised by the BIOS. Problem is the drive is locked. Under windows i've tried dozens of programs attempting to unlock the drive but with no sucess. I've read a few hundred tutorial and still could not unlock the drive.

Question 2 - Is it simpler or even possible to unlock the xbox drive under linux? How?

---

### Post by sonicprogress on 2007-05-23
Assuming you have a free PCI slot...could you not buy an IDE controller card and plug it into that?

Am I wrong in saying that that would work?

---

### Post by lazyart on 2007-05-23
Your BIOS is flipping out because the HD is >32 megs.  There might be a 32GB jumper on the drive that you can set.  You will effectively lose 20% of the drive but it's better than a paperweight.

Another option is a DDO - Dynamic Drive Overlay.  This is software on the drive that does BIOS translation.  Not the best way, but a way.  EZBIOS is what I recall the name to be.

The best way to overcome this is to find a BIOS update that will let you use the drive to its fullest.  You'll have to open it up and see the make and model of the board... or maybe it's a brand name clone and you can get the info from the model of the machine.

Good look.

---

### Post by logos34 on 2007-05-23
I agree that a BIOS update may solve your problems, but it may be simpler than that.

Do you have the jumper set correctly on the 40gb disk?  I use a Vantec IDE to USB adapter and had to set the jumper to 'Master' on my Maxtor ata133 drive before Winxp or linux would recognize it.  The BIOS didn't even see it.  After that it was recognized in my bios after my main hard disk as 'USB-HDD0', and shows up in device manager as 'usb mass storage device'. (It's formatted ntfs so it also appears in My Computer as (F:) drive.  Fdisk sees it in linux and I added r+w using ntfs-config, mounts as sda1.

Some drives require the jumper for Master setting, others are Master without it.

You should only need a driver for windows 98.

---

### Post by smoker on 2007-05-23
> It happens that I have a 40 giga HD in the shelves. So I tried to connect to 40giga HD to this computer using an IDE connection. No such luck. The computer doesn't recognise the drive, in fact it freezes in the BIOS boot trying to recognise it.

some older motherboards can also be fussy about how the drives are set up in the same ide channel, eg, end of the cable to harddrive should be set to master, middle connector hard drive to slave. if this doesn't work, try setting both hard drives to CS (cable select), with the main OS hard drive still at the end of the cable. if this doesn't work, try attaching the 40GB drive to the other ide channel as a slave to the cd-rom (guessing you have only one cd-rom!). if the drive isn't recognized by trying the above, try attaching it as the only drive in the computer, if that works, then you could maybe install an OS on it, and slave the other drive.

as for the USB connector, depending on the bios, it may not show until the OS loads, though look for options in the bios setup to enable USB legacy support, infact, enable anything you see concerning USB, even, eg, usb keyboard/mouse support.

best of luck

---

### Post by Ganda_Melga on 2007-05-23
> **lazyart said:**
> Your BIOS is flipping out because the HD is >32 megs.  There might be a 32GB jumper on the drive that you can set.  You will effectively lose 20% of the drive but it's better than a paperweight.

Another option is a DDO - Dynamic Drive Overlay.  This is software on the drive that does BIOS translation.  Not the best way, but a way.  EZBIOS is what I recall the name to be.

The best way to overcome this is to find a BIOS update that will let you use the drive to its fullest.  You'll have to open it up and see the make and model of the board... or maybe it's a brand name clone and you can get the info from the model of the machine.

Good look.


I have no idea of what's a DDO. But I liked the ideia of setting the jumpers on the drive to limit it to 32 mega. Problem is I only have on jumper and for that it takes two jumpers. I'll try to find another jumper in the attic. But the real problem is there is no label to tell me where the jumpers must be. Even setting the hd as master or slave is a question of trying in the various positions, and see if it works.

The Bios upgrade seems nice, bur I suspect it wont be easy for a nerd like me. Also I would prefer not to opne the case again ans trip down all the components to see if it's anything written on the motherboard (in the last months i switched pieces more than 20 times and I would like to gave it a rest). I do however have little program for windows wich gave me the following indications:

Motherboard-

 [IMG]http://i15.tinypic.com/54cgx0g.jpg[/IMG]


Bios:

[IMG]http://i19.tinypic.com/5xqinnn.jpg[/IMG]


Based on this info, what should I do to upgrade the BIOS?

---

### Post by Ganda_Melga on 2007-05-23
> **logos34 said:**
> I agree that a BIOS update may solve your problems, but it may be simpler than that.

Do you have the jumper set correctly on the 40gb disk?  I use a Vantec IDE to USB adapter and had to set the jumper to 'Master' on my Maxtor ata133 drive before Winxp or linux would recognize it.  The BIOS didn't even see it.  After that it was recognized in my bios after my main hard disk as 'USB-HDD0', and shows up in device manager as 'usb mass storage device'. (It's formatted ntfs so it also appears in My Computer as (F:) drive.  Fdisk sees it in linux and I added r+w using ntfs-config, mounts as sda1.

Some drives require the jumper for Master setting, others are Master without it.

You should only need a driver for windows 98.


Well, like I said in the answer before, it's quite difficult to know how to place the jumpers since the label has gone. I suppose I could try all possible combinations... Will take me some time though.

---

### Post by Ganda_Melga on 2007-05-23
> **smoker said:**
> some older motherboards can also be fussy about how the drives are **set up in the same ide channel, eg, end of the cable to harddrive should be set to master, middle connector hard drive to slave. if this doesn't work, try setting both hard drives to CS (cable select), with the main OS hard drive still at the end of the cable. if this doesn't work, try attaching the 40GB drive to the other ide channel as a slave to the cd-rom (guessing you have only one cd-rom!). if the drive isn't recognized by trying the above, try attaching it as the only drive in the computer, if that works, then you could maybe install an OS on it, and slave the other drive.**

[COLOR="Blue"]as for the USB connector, depending on the bios, it may not show until the OS loads, though look for options in the bios setup to enable USB legacy support, infact, enable anything you see concerning USB, even, eg, usb keyboard/mouse support.
[/COLOR]
best of luck

I tried so many combinations, that i think I got them all covered. The hd is never recognised by the bios, even if it's the only drive


[COLOR="#0000ff"]As to that matter, I will check again the BIOS configuration, it was good of you to remember me.[/COLOR]

---

### Post by Ganda_Melga on 2007-05-23
All in all you all gave some good ideias. I will try them out to the best of my knowledge.

Thanks a lot for your kind replys! :popcorn:


Any other ideias will be welcome too...;)

---

### Post by lazyart on 2007-05-23
If you look up the manufacturer of the drive you might find a jumper diagram.

Also, not having slave/master set correctly would cause a hang at boot.  Even your existing drive might have a Master, Slave and Single drive setting.  To confuse things even further, some CDROMs don't play nicely if there is a HD posing as a slave device.

Best of luck to ya.

---

### Post by logos34 on 2007-05-23
> Based on this info, what should I do to upgrade the BIOS?

Do what lazyart said and search by make and model of your pc or open it up and look at the board for any identifier.  All we know from the system info screenshot you posted is that it's based on a Intel 440bx chipset.

If and when you find a bios update, the typical procedure is to download and copy it to a floppy (you might have to unzip it first), then restart your computer and enter the bios and flash it.  Be sure to consult beforehand any readme.txt or instructions.

---

### Post by lycopenehead on 2008-01-11
well i  just bought an asus lightscribe dvd/rw i was tying to connect it via the ide cable with no single success just like what you said,that jumber thing doesnt work by the way

its 7.10 on ibm r40e

---

### Post by eriqjaffe on 2008-01-12
Ganda_Melga:

You might want to download Belarc Advisor ([http://www.belarc.com/free_download.html](http://www.belarc.com/free_download.html)), which will tell you the manufacturer name and model number of your motherboard.  It's a Windows app, but it'll let you know where to go looking for BIOS updates.

---

### Post by madmagic on 2008-01-12
I dont know if this has ben suggested yet, but i had a computer simmiler to yours, and i had to format my new 40gig hard drive into sets of 2. may want to try it

---

