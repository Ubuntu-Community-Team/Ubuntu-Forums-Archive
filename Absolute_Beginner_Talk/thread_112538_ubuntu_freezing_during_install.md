---
title: "ubuntu freezing during install"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by djlilyazi on 2006-01-04
Hi,

I tried the live cd it did not work it frooze my computer...

so i was like ok i am going to partion and everything and try the install..

so after it tries to detect all my hardware it totallllllyyyyy freezessssss

what can i do ?

i really want to install linuxxxxx so baddddddddddddddd:mad:

---

### Post by total numpty on 2006-01-04
I had a similar problem installing it on a spare machine and diagnosed it as a faulty CD ROM. I swapped it and it installed everything ok then...

Thats when the headaches started, learning how to use it! lol

---

### Post by djlilyazi on 2006-01-04
[QUOTE=total numpty]I had a similar problem installing it on a spare machine and diagnosed it as a faulty CD ROM. I swapped it and it installed everything ok then...

Thats when the headaches started, learning how to use it! lol[/QUOTE]


huh ? you did what i dont get it ...i did try the cd on my other mahcine it worked perfectlyyy

---

### Post by Star Solutions on 2006-01-04
Im haveing the same problem.  Trying a new cd now.

---

### Post by djlilyazi on 2006-01-04
[QUOTE=Star Solutions]Im haveing the same problem.  Trying a new cd now.[/QUOTE]


i made 3 copies at 4x speed they all do the same thing...freeze after hardware detection.....

---

### Post by byen on 2006-01-04
Then i would have to say it might be either 
1. corrupt downloaded cd iso
2. You need to turn off acpi function during install.

For 1:first after downloading the ISO make sure that yu check the integrity of the ISo by using a program like this:
[http://www.nullriver.com/index/products/winmd5sum](http://www.nullriver.com/index/products/winmd5sum)
(free and secure)
now...after doing this Go to [www.downloads.com](www.downloads.com) and search for the program "deepburner". its free and was developed by the developers with ISO burning in mind. It is really good and damn easy to use. Download it and burn the cd as an ISO project at a slower speed. Let me know if you have any probs. I might have some alternatives.

For 2- some people have better luck by -turning the ACPI feature off at the boot menu.And remember if you have windows or other Operating systems and wanna dual-boot.

Goodluck. Let us know if you have more trouble.

---

### Post by djlilyazi on 2006-01-05
Hahhaaaaaaaaaaaaaaaaaa

Dj Lil Yazi Does Not Neeeeeeeeeed Anyones Help Anymore

She Did It Allllllllll By Herselffffffffffff...

Umm Disabled Usb 2.0 Was My Soultionnnnnnnnn

Linux Is Allllllll Mine Nowwwwwwwwwww Lol

Mmuuuahahahhaaaaaaaaaaaaa

L8r Ppl

Thanks For Everyones Helppppppppppppppppppp

---

### Post by byen on 2006-01-05
lol. good to know you are all set. Let us know if you need anymore help.
Goodluck.

---

### Post by total numpty on 2006-01-05
Well Done

---

### Post by Bartender on 2006-01-05
LiveCD wouldn't go at all on my half-year old home-built machine - the DVD drive spun up and down a few times, the lights blinked, then the computer moved on to the hard drive.  These aren't the same symptoms as the original poster but I wanted to ask if anyone thinks I should try turning off ACPI and/or USB 2.0 in the BIOS?

---

### Post by byen on 2006-01-05
well...as stated in my first post. are you sure the iso you downloaded was not corrupted. and i would want to write the cd at lower speeds as well. Please follow the instructions that i have mentioned in this thread and then try the acpi-off option/usb (or better yet try turning acpi off or legacy support off(in boot options) and then go to download and install into another cd if needed. See if it works. If not let us know.
Goodluck.

---

### Post by djlilyazi on 2006-01-05
[QUOTE=Bartender]LiveCD wouldn't go at all on my half-year old home-built machine - the DVD drive spun up and down a few times, the lights blinked, then the computer moved on to the hard drive.  These aren't the same symptoms as the original poster but I wanted to ask if anyone thinks I should try turning off ACPI and/or USB 2.0 in the BIOS?[/QUOTE]

yeah do that...then just put it all on after it installs...its 100% working for me...

---

### Post by Bartender on 2006-01-08
The LiveCD's aren't downloaded, they're stamped.  I'll try changing the settings you suggested.  Are you saying that if LiveCD works with the changes and I decide to dual-boot Ubuntu, I can put the settings back afterward and everything oughta work?
The M$ machine works like a champ ad I sure don't want to screw it up..

---

### Post by djlilyazi on 2006-01-08
[QUOTE=djlilyazi]Hahhaaaaaaaaaaaaaaaaaa

Dj Lil Yazi Does Not Neeeeeeeeeed Anyones Help Anymore

She Did It Allllllllll By Herselffffffffffff...

Umm Disabled Usb 2.0 Was My Soultionnnnnnnnn

Linux Is Allllllll Mine Nowwwwwwwwwww Lol

Mmuuuahahahhaaaaaaaaaaaaa

L8r Ppl

Thanks For Everyones Helppppppppppppppppppp[/QUOTE]


I WOULD LIKE TO CORRECT MY SELF PLEASE...
I CHANGED MY BIOS Settings TO Native-Mode THEN ENABLED USB SINCE I NEED TO USE USB 24/7. THAT WILL SOLVE ALOT OF PROBLEMS FOR YOU GUYS....

L8R 

YAZZZZZZZZZZ

---

### Post by byen on 2006-01-08
[QUOTE=djlilyazi]Hahhaaaaaaaaaaaaaaaaaa

Dj Lil Yazi Does Not Neeeeeeeeeed Anyones Help Anymore

She Did It Allllllllll By Herselffffffffffff...

Umm Disabled Usb 2.0 Was My Soultionnnnnnnnn

Linux Is Allllllll Mine Nowwwwwwwwwww Lol

Mmuuuahahahhaaaaaaaaaaaaa

L8r Ppl

Thanks For Everyones Helppppppppppppppppppp[/QUOTE]

Sorry this is a little off topic but... I used to spend hours looking for answers and asking questions...just trying to get one-step closer to get my system up and running the way I wanted to... I eventually did manage to get that done thanks to so many users who helped me. And eversince Ive been trying to give a little (though very tiny) back to the community and to really tell you the truth djlilyazi. Your reaction just convinced me that I am doing that. Still get a smile everytime I see that reaction. I remember the moment I got my pc up and running .. there were actually over 50 users from over 10 countries (in various posts) who helped me along the way......there is not enough i can say or do to say thanks...I wonder...where would linux be without this community..

---

### Post by Bartender on 2006-01-09
Hi, guys -
I'm getting a little off-topic from the original post but you said to get back with results...
I disabled ACPI APIC, ACPI 2.0, and USB 2.0.  Left Legacy USB Support "ON".  Set boot to DVD 1st of course.  

With the LiveCD in the tray, I saved changes and exited.

Got the computer to act differently, but not quite what I was hoping for.  It looked at the CD again, just like before, then moved on to the HDD.  However, this time the computer just stalled out at the black screen where it says "Starting Windows".  The white bar filled in, then nothing.  

I'd like to dual-boot this machine, but it runs W2K flawlessly and I don't want to jeopardize the happy situation.  It feels like I'm trying to force the issue, which usually leads to regrettable consequences.  Anybody had luck running Ubuntu on the ASUS P5GDC-V?

---

