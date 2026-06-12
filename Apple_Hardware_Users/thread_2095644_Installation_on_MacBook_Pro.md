---
title: "Installation on MacBook Pro"
date: 2012-12-17
forum: Apple Hardware Users
---

### Post by gas0line on 2012-12-17
---HELP---

First of all, I must clarify, I am a noob. However, I have enough experience with computer systems to know what you are talking about/any advice you may give me.

So, here is my prob: I have my Ubuntu disk, I stick it in and boot from it, but then all that shows up is a flashing underscore. I can't even type commands in! The background is a purple/green screen. 

So, I restart my comp and try it again. Same thing. Restart, try again. Same thing. Restart, try again. Same thing. You get the point. ;)

---VERSION---

Ubuntu 12.04 LTS (32-bit)

---COMP SPECS---

Computer: MacBook Pro, Mid-2012
*Current* Operating System: OS X 10.8.2 

Disk: DVD-R 4.7 Gigs


---NOTES---

I followed [this]("https://help.ubuntu.com/community/BurningIsoHowto#Downloading_an_Ubuntu_ISO") guide in burning Ubuntu to my disk.

I'm desperate to try Ubuntu. :guitar:

---

### Post by papibe on 2012-12-17
Hi gas0line. Welcome to the forums ):P

I'd start by making sure your ISO was downloaded correctly, and you don't have a corrupt copy.

Take a further look at the section 'Verifying the ISO integrity' of that tutorial, jump to the HowToMD5SUM link, and go to the proper section (MD5SUM on Windows on presume).

Also it would be important to know what kind of machine and current OS are you trying to install Ubuntu on.

Let us know how it goes.
Regards.

---

### Post by gas0line on 2012-12-17
> **papibe said:**
> Hi gas0line. Welcome to the forums ):P

I'd start by making sure your ISO was downloaded correctly, and you don't have a corrupt copy.

Take a further look at the section 'Verifying the ISO integrity' of that tutorial, jump to the HowToMD5SUM link, and go to the proper section (MD5SUM on Windows on presume).

Also it would be important to know what kind of machine and current OS are you trying to install Ubuntu on.

Let us know how it goes.
Regards.

Hi Papibe,

Thanks so much for the response and welcoming. 

All my system information is in the "---COMP SPECS---" section. I am currently running OS X 10.8.2 on a MacBook Pro Mid-2012.

When I insert my Ubuntu disk while booted up into OS X, I get an error message saying "The disk you inserted was not readable by this computer". It gives me two options: ignore or eject. I'm not sure if that is normal or not. I am not able to verify the disk using MD5 because of this. Unfortunately, I had overlooked the verification! ](*,)

Is there any more work I can perform on this current disk, or must I download another version of Ubuntu onto a different disk? 

Thanks so much for your help.

gas0line

---

### Post by papibe on 2012-12-17
The installation process on a Mac may be a little different from a regular PC. Unfortunately, I don't have much experience on the subject.

Nevertheless, take a look at this links:
[LIST]
[*][Ubuntu on MacBook]("https://help.ubuntu.com/community/MacBook")
[*][[HOW TO] install Ubuntu (12.04) on a Mac.]("http://tech-devnet.blogspot.de/2012/05/running-ubuntu-1204-on-mac.html")
[/LIST]
Hopefully someone else will offer more useful tips.

Regards.

---

### Post by gas0line on 2012-12-17
Thanks for your help so far papibe.

EDIT: I downloaded the 32-bit version to the disk, if that matters.

---

### Post by gas0line on 2012-12-17
Hi everyone, 

I tried downloading Xubuntu using the same method. I did the MD5 thing but the hashtags didn't match.

I can't keep going through disks like this. :( Starting to get somewhat frustrated with this process. Are there any other linux distros easier to install? Any help is appreciated.

---

### Post by gas0line on 2012-12-29
Hi everyone. It is me... again! 

So, I tried this one more time, however with Ubuntu 10. Everything is successful, however I find the partitioning confusing. Do I need to make a partition in Boot Camp before installing, or will the installer guide me through partitioning right then and there?

Any help is appreciated, thanks. Merry Christmas & Happy New Year to all of these wonderful volunteers and staff helping newbies like me!

---

### Post by papibe on 2013-01-18
I'm not an Apple expert but I believe you can use Boot Camp only if you have Snow Leopard. Take a second look at the Howto that I linked on post #4.

Regards.

---

### Post by minsf on 2013-01-20
which macbook pro do you have? 13" or 15"? retina or non-retina?
(MacBookPro 9,1 9,2 or 10,1?)

> Do I need to make a partition in Boot Camp before installing
You probably do **not** want to use bootcamp to create the partition for ubuntu. Instead, you probably want to use Diskutility to create the partition before installing.
tip: if you care about keeping your OSX (and dual booting it with ubuntu), make sure you do not change the last partition (Mac recovery partition). that is, split the OSX partition into OSX+ubuntu partitions, but do not split or override the last OSX recovery partition. However, if you did that by accident, you will still be able to do OSX recoveries from the network (by holding cmd+R at startup), except that they will take a lot more time.

> I downloaded the 32-bit version to the disk, if that matters.
you probably do **not** use the 32bit. you want to use the amd64 iso to create it.

> but then all that shows up is a flashing underscore.
i had the same problem as you with the flashing cursor of the live CDs, even though I verified their hashes.
instead, I installed ubuntu 12.10 by creating an install USB stick (this will also save your CDs...):
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx)

a few more things: depending on your specific MBP model, you may need to use nointremap and/or nomodeset boot parameters (you can set them at the grub menu by pressing "e" and adding them at the end of the linux line). we can redirect you to a specific thread in this subforum which discusses your MBP model when we know it.

---

