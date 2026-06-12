---
title: "Im thinking about updating Bios.."
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2007-02-12
Hi,

I thinking about updating my BIOS. I have never done this before and my machine is 3½ years old.

Would this do any notable change for me? 
I have a Asus A7N8X Deluxe Gold Motherboard.

Would anyone help me where I can get the latest Bios for this board,
and howto install it?

And do you think I could feel the change?

Thanks a lot!

---

### Post by Maestro23 on 2007-02-12
Should be able to find out all info(drives, Bios, etc..) on your motherboard here:[http://support.asus.com/download/download.aspx?SLanguage=en-dk](http://support.asus.com/download/download.aspx?SLanguage=en-dk)

---

### Post by aktiwers on 2007-02-12
Thanks Maestro23..
All I can find there is this
[http://support.asus.com/technicaldocuments/technicaldocuments.aspx?root=198&SLanguage=en-us](http://support.asus.com/technicaldocuments/technicaldocuments.aspx?root=198&SLanguage=en-us)

Which is exactly what I need, but its Windows only?

I dont have windows installed. I dont use it.
How can I do update Bios with Linux? :confused:

---

### Post by oilchangeguy on 2007-02-12
a bios flash is one of those things that falls under the catagory of, if it ain't broke don't fix it. given your computers age, there's probably nothing to be gained from doing this. the main reason for a bios flash in an older computer is to enable large hard drive support.

---

### Post by FenrisAbraxas on 2007-02-12
> **oilchangeguy said:**
> a bios flash is one of those things that falls under the catagory of, if it ain't broke don't fix it. given your computers age, there's probably nothing to be gained from doing this. the main reason for a bios flash in an older computer is to enable large hard drive support.

Cuoldn't agree more, take into consideration that if SOMETHING happen WHILE the BIOS is updating the chip will be sent to /dev/null (and i can tell you, you don't want your BIOS to be there) and make your comp an expensive trash can.

Don't do it UNLESS IS ABSOLUTELY NECESARY.

---

### Post by aktiwers on 2007-02-12
This is actually also why I want to do this.
Since I got my Computer (3½ years ago), It really hangs when it comes to boot the hard drive. I think this is because I have a SATA hard drive. It hangs for like 2-4 minutes and Im really tired of it :)

Also I have an amd 2800XP+ processor, and it shows up as 1250mhz, and there is no place to change that in Bios.. (I really have looked everywhere!)

Thats my reason to do this really..  you dont think it will help?
I dont know.. as I said, I never done it before.

Thanks for the response :)

---

### Post by oilchangeguy on 2007-02-12
i looked at amd's website and they have no listing for a 2800xp. what series is it? athlon, etc.? as far as your computer hanging, it may be a hard drive problem. your cpu may be a model 2800xp, but there's probably a range of speeds in that model line.

---

### Post by rsambuca on 2007-02-12
Updating the bios is actually really quite simple, but one thing that needs to be stressed over and over:  FOLLOW THE INSTRUCTIONS TO THE LETTER

To update the bios most procedures require you to boot the computer into dos first.  If you try it from booting into windows first you will have a very large brick sitting on your desk.  Check with your manufacturer to see what updates are available, and what changes were made to them before you do it.  In any event, I don't think that it is too difficult.  Just make sure you FOLLOW THE INSTRUCTIONS FOR UPDATING THE BIOS!!!

---

### Post by rsambuca on 2007-02-12
Oh, and with regards to the clock speed of the AMD chips, it is different from the 2800+ conventions they stuck on the name.  The only reason they stuck those numbers on originally was so that people could have a rough idea as to what speed chip it would compare to in the Intel line.  So in this case, the AMD performance is roughly equivalent to an Intel 2800 MHz chip, eventhough the AMD clock speed is in your case 1250MHz.

---

### Post by Maestro23 on 2007-02-12
> **rsambuca said:**
> Updating the bios is actually really quite simple, but one thing that needs to be stressed over and over:  FOLLOW THE INSTRUCTIONS TO THE LETTER

To update the bios most procedures require you to boot the computer into dos first.  If you try it from booting into windows first you will have a very large brick sitting on your desk.  Check with your manufacturer to see what updates are available, and what changes were made to them before you do it.  In any event, I don't think that it is too difficult.  Just make sure you FOLLOW THE INSTRUCTIONS FOR UPDATING THE BIOS!!!

Ditto.:)

---

### Post by aktiwers on 2007-02-12
Sorry..  this is my CPU:     			    AMD Athlon XP 2800+ 2083 Mhz
The only guide I could find is the one above, that is WINDOWS ONLY.

I dont have, and havent had Windows for more than 1½ year, and I really dont want it. Do I really need windows to do this then? Is there some, that requires windows to do it?

And do you think it would fix my 2 problems stated above?
1) Slow boot (2-4 minutes when booting from hard drive, this is not the case when I do it from CD-ROM or Floppy)

2)My CPU shows up as 1250mhz, and I can find no place in BIOS to change this. I even tried changing it to "Aggressive" (its the highest it can be set, but this changes nothing).

Any Ideas? I would rather not do this, but I thought it might sort out my problems.

---

### Post by oilchangeguy on 2007-02-12
i've got a small collection of computers (5), and 2 of them run different flavers of linux. ubuntu 6.06lts on one and xandros 3.0 oce on the other one. and both seem to take longer to boot than their windows counterparts. it dosen't bother me, i just turn them on and walk away for a minute or two. if you purchased your computer new, your paper work should show the speed of the installed cpu. and unless you're a serious gamer, 1250mhz is plenty of cpu for most tasks. as long as the computer is running normally, after the seemingly slow boot, leave it alone.

---

### Post by rsambuca on 2007-02-12
OK, what version bios do you have?  A 2 to 4 minute boot up time can be a pain, but it is more likely something with your setup as to an old bios.  Have you booted up in verbose mode to see where it is hanging up?

---

### Post by aktiwers on 2007-02-12
> **rsambuca said:**
> OK, what version bios do you have?  A 2 to 4 minute boot up time can be a pain, but it is more likely something with your setup as to an old bios.  Have you booted up in verbose mode to see where it is hanging up?

Nope.. how do I do that?
It has always done this.. also on Windows. Its when I boot from the hard drive. It hangs at the "verifying dmi pool...." thing. And it does it on Linux, Windows and you name it. But when I do it from a Floppy or CDROM.. BANG! It boots right away.

How do I run i Verbose mode?
For me it seams like it just does NOTHING for 2-4 minutes, and then start booting, even though the hardrive is set to be the first thing to boot. :confused:

EDIT: How can I check my BIOS Version..  ahh ok.. I guess I have to reboot :D

---

### Post by Big_Croc7 on 2007-02-14
I had a very similar problem a long time ago, when ATA100 was new and it needed special drivers... this may be something similar.  I can't remember exactly what I did to fix it, but it certainly didn't involve flashing the bios; it may be that you need to update the SATA controller driver somehow, rather than the bios itself, but I don't know.

As for the cpu speed, there is one thing that springs to mind:  is the FSB set correctly? some motherboards will run at e.g. 100MHz even if the cpu is expecting a higher speed.  I suspect this could be happening in your case - 100 clock speed with a 12.5 multiplier gives 1250MHz reported speed, as opposed to 166.66 MHz x12.5 = 2083.25MHz.  Try to find a setting somewhere in the bios where you can set the clock speed, and set it to 166MHz (if it's at 100 to start with).  Make sure you can locate the CMOS reset jumper first though, in case you can't boot your system afterwards.

---

### Post by aktiwers on 2007-02-14
The thing with setting it to 166mhz actually worked like a charm!
My system is now back to the 2083.25MHz! Thanks!

Would you have any links to howto update the SATA controller driver?
Then I would give it a shut also :)

---

### Post by Big_Croc7 on 2007-02-15
That's great! Glad I could help with the cpu :-)

I don't know that much about SATA drives I'm afraid (I'm still using IDE ones); the drivers are probably integrated into the kernel (I think), so if you are using the latest kernel you should have the latest drivers - the kernel is updated automatically when your system updates, unless you specifically reject it.

Will have a think and get back to you!

---

### Post by aktiwers on 2007-02-15
Oh okay..  But I dont think its a driver problem when I come to think about it.
Because I also had the problem on windows.. its something with my BIOS.
I found a link about it, but havent had time to test it yet. I will update.

---

### Post by muhsinzubeir on 2008-06-03
for linux bios:
[http://http://www.coreboot.org/Welcome_to_coreboot]("http://http://www.coreboot.org/Welcome_to_coreboot")

have fun...

---

