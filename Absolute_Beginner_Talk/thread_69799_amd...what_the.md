---
title: "amd...what the ****"
date: 2005-09-27
forum: Absolute Beginner Talk
---

### Post by sunrex on 2005-09-27
i just got a amd athlon 3000 1 gig ram, my first time with amd, its a 64 bit chip..

let me put this very simply...

i cant install ANY windows as far as i know...

suse 9.2 pro is **** wont even let me see the picture after install

kubuntu wont even get passed system install....

first try at ubuntu for amd failed on complieing.

second try i got server only working..but even that had some problems, and i want kde or gnome on it..

third try....both server and normal install wont work...says somthing like runtime erorr during the system install..

now i dont know about you, but this can piss  ANYONE off.

so im asking this as a last cry for help...can anyone tell me what to do?? please...HELP!!!

---

### Post by YourSurrogateGod on 2005-09-27
Could you pleaes post some error messages that you got (or describe them roughly.)

---

### Post by sunrex on 2005-09-27
basicly somthing like a big red box with could not somthing bootloader or somthing send erorr one...i cant really remember it, i just deleted the cd rw to try gentoo..but that looks horrible couse all the compling...as a matter of fact im still burning it.

all i want to know...is why amd keeps going OUCH.

its a amd64 sempron if that helps

---

### Post by Scuddie on 2005-09-27
It could be one of many things.  From your first description, it seems you have the CPU in 64bit only mode, and not 32bit compatibility.  However, it occurred to me that this is a new system, and there are some tricks of the trade that need to be told.  Two questions are likely to solve your problem.  First, is your AMD an OEM or retail chip?  Second, have you tried memtest86+ to test the integrity of your RAM?

Also, go into your BIOS to make sure 32bit compatibility is selected.

EDIT:  A sempron?  That is not 64 bit.

---

### Post by sunrex on 2005-09-27
eh..nope...none of em..accept i got the chip at frys electronics...i custom built the computer so i dont know what to do,


EDIT: A sempron? That is not 64 bit.

yes it is, its on teh bootup screen, the chip, and even comes up on the suse install menu when it checks hardware.

Also, go into your BIOS to make sure 32bit compatibility is selected.

how?

---

### Post by YourSurrogateGod on 2005-09-27
never mind

---

### Post by sunrex on 2005-09-27
i know MINE is, its a 3000 btw.

look i know mines a 64 bit Couse it comes up on EVERY install 64bit INCLUDING WINDOWS NT WHICH WONT WORK AFTER INSTALL. it comes up on the system editer...or whatever that is...it comes up on the computers at the store i bought it from...they wouldent fake this.

---

### Post by brentoboy on 2005-09-27
suse 9.2?
get their prerelease, 10.0 I tried it and it worked on my bleeding edge system, I just struggle with thier packaging system - give me apt-get any day of the week.

---

### Post by sunrex on 2005-09-27
somone please pitty me...and tell me what to do...this is annoying..i spent 150$ on a new power supply....another 100$ somthing on a dvdrw..another about 150$ on 300 gig hdd then 150 for the motherboard and the rest...total = about 800$ my point? i bought this and it wont work....and its really dumb...this is annoying....is there support at all for the prosseser here?

*edit*

brentoboy...great idea..but last time i tried that with 9.3 a few weeks ago, u have NO CLUE on how many freekin problems i had in install and then the real system, does ubuntu even work with my prosseser, chip, ect?

---

### Post by YourSurrogateGod on 2005-09-27
[QUOTE=sunrex]how?[/QUOTE]
Fiddle with the settings :) .

---

### Post by sunrex on 2005-09-27
i got nothing to lose really....i spent 3 days doing nothing but trying to reinstall it...btw what overclock speed can i use on 3000 64bit without damage?

---

### Post by Scuddie on 2005-09-27
[QUOTE=sunrex]accept i got the chip at frys electronics[/quote]I think we found your problem.> yes it is, its on teh bootup screen, the chip, and even comes up on the suse install menu when it checks hardware.No, it is not.  Semprons are nothing more than AMD64 chips with disabled 64bit extensions.  The reason it was so cheap is because it wasn't worth the box it came in.> Also, go into your BIOS to make sure 32bit compatibility is selected.  How?Read your board reference guide.  Most good boards will do it for you, but some of the earlier ones need configuration.

Also, I ask again, did you buy the chip as OEM, or did you buy it retail?  If it came in a plain white box, it was OEM.  If it came in a spiffy looking shiny retail box with a heatsync in it, it was retail.

---

### Post by sunrex on 2005-09-27
didint come in ANY box, it came with the motherboard...so my chip is cheep? and what do you mean by you found my problem

btw i cant change it to 32bit..

---

### Post by sunrex on 2005-09-27
if thats the case...and my chip is cheep...sould i just get the x86 version or what....


or sould i just go down to frys electronics and break a few damn bones...

---

### Post by brentoboy on 2005-09-27
I was really frustrated with my PC until I went to the motherboard manufacturer's website and got the latest bios and flashed my bios.

I wouldnt normally recommend that sort of thing - flashing bios's is not for people with no guts, but you sound like you'll try just about anything at this point, and I honestly think it might improve your situation.

I do offer one precaution, dont just up and do it, make sure you have all your ducks lined up before you start.  Get the disk, print off the instructions, dont jump until you are ready to commit, and then dont look back.

What have you got to loose?

oh - make sure and get the exact bios for your exact motherboard.  dont settle for _almost_ here.

---

### Post by sunrex on 2005-09-27
so what ubuntu version will work?

---

### Post by sunrex on 2005-09-27
yes...brentoboy...i am redy to do just about anything OR ELSE THE ENTIRE THING IS WORTHLESS TO ME! lol. no um how would i update it, just download the bios to a cdrom then update it?

---

### Post by sunrex on 2005-09-28
> Semprons are nothing more than AMD64 chips with disabled 64bit extensions.

..can i enable em..

---

### Post by Ubunted on 2005-09-28
No. Download the i386 version. You do not have a 64-bit processor. I don't care what they said at Fry's, if you bought a Sempron you bought a 32-bit chip.

There. Problem solved.

---

### Post by sunrex on 2005-09-29
eh, not really, i got the gui working, gnome working, but the second i press ANYTHING in gnome..bang. some kind of failer, could be sound or somthing, blablabla shutdown system.

---

### Post by elemental_silver on 2005-09-29
Oh man, poor fellah. You know, I had a choice between Simpron or the AMD64 for my laptop, but I took the Simpron for stability and longer battery life. However, you're dealing with a desktop computer, I'm guessing. By the by, I have problem with my chipset too. When I screwed up my MBR, I couldn't log into ubuntu cause it kept crashing away at me.

---

