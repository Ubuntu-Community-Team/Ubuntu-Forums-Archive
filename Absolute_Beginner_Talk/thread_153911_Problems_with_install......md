---
title: "Problems with install....."
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by tristan@msa on 2006-04-02
hello all i recenlty scored 2 older desktops, and decided to ditch win98 and try my hand @ linux. Well the first desktop that i'm trying to load ubuntu 5.10 on is hanging. Install the base sytem portion of the install and i get a message saying somthing about unable to find kernel system. then i get kicked back to the menu. 

system is pent celeron @ 500mhz 256mb ram

What to do?

thanks
Tris

---

### Post by steve.horsley on 2006-04-02
I don't think this is a common error, so people may have trouble understanding exactly where you are whenr the problem shows. I assume you are still in the installer. Can you tell what it's trying to do when you get the problem? Kicked back to what menu? 

I know it sounds lame, but since this is not a common error, it may be that the CD you are installing from is not burned perfectly. It may be worth checking the MD5 chechsum of your ISO download, and then burning the CD at a really slow speed.

---

### Post by tristan@msa on 2006-04-02
Yes this is all occurring during the install.
I'm burning @ 4x, but i'm going to try to get a new ISO recorder to make it happen. 

I will let you know how it goes
Tris

---

### Post by catlett on 2006-04-02
It sounds like your CD is no good. Did you download it and burn it to disc or did you get a copy from Ubuntu through Ubuntu's "Ship IT" site? Without knowing exactly what your error is, it sounds like the disc is corrupt. When you boot to the install disc it will uncompress the linux kernel to get things started. Your error "unable to find kernel" seems to point to the kernel not being on the disc. If you still have problems and you don't mind waiting a week you can get discs for free from Ubuntu at [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/). If you don't want to wait and keep getting errors, try to give more details about when in the process it happens and what the error says. Regards, Catlett.

---

### Post by tristan@msa on 2006-04-02
Ok so I used another program to do the burn (NERO) and now this is the message i get, This is all occorruing during the "installing base sytem" portion of the install "the debootstrap program exited with an error return value 1)
check /target/var/log/boostrap.log for details
 then once i click enter i get
the base sytem installation into /target/ failed 

check /target/var/log/booststrap.log for the details

then after another click it takes me back to the installer menu.


I guess my lack of linux skills are gonna kill me............

Tris

---

### Post by xXx 0wn3d xXx on 2006-04-02
[QUOTE=tristan@msa]Ok so I used another program to do the burn (NERO) and now this is the message i get, This is all occorruing during the "installing base sytem" portion of the install "the debootstrap program exited with an error return value 1)
check /target/var/log/boostrap.log for details
 then once i click enter i get
the base sytem installation into /target/ failed 

check /target/var/log/booststrap.log for the details

then after another click it takes me back to the installer menu.


I guess my lack of linux skills are gonna kill me............

Tris[/QUOTE]


Try the following.

1. Redownload the install iso. 

2. Get a fresh cd (never has been burned before)

3. Burn the image with nero at the SLOWEST possible speed. It is usually 4x.

4. Pop the cd in and install then enjoy ubuntu.

You don't need to do Step one but I would try it anyway :)

---

### Post by tristan@msa on 2006-04-03
I tried it and nothing. I even went to the extent of using another PC (work) to download and re-burn to CD. Still nothing same thing about the bootstrap or what ever. Maybe ubuntu and my PC arent to be..............

---

### Post by vejan on 2006-04-04
How big a hard drive is present?
is it formatted? partitioned?

---

### Post by mumushi on 2006-04-04
i had the same problem before and i found out that my cdrom was the problem. try redownloading the iso then burn it in the lowest speed possible then try using another cdrom. I hope it works. ;)

---

### Post by dvarsam on 2006-04-04
And make sure that the Blank CD-Rom you are copying the Ubuntu ".iso" is of a good/known brand name...

Do NOT use "unknown" (Blank) CD brand names.
NOT all "unknown" brands are bad, but there is always an exception out there...

And remember that Computer Stores want to sell/promote the CD brands that give them higher profit - and this means selling "unknown" brand names...

Good Luck!

---

### Post by spandon on 2006-04-04
Hi tristan@msa,
How are you burning the cd?
hope you aren´t copying the iso, the iso has to be converted.
Use Nero EXPRESS, on opening, the lower of the choices is burn an immage, choose this.
choose the at least 50% of the lowest speed (writer or cd) and choose to verify burn,
If you are burning the live cd, and this doesn´t work on your machine, then if possible, try it out on another machine, if it then works, it is a hardware problem and not the cd.
Hope this helps
don

---

### Post by felaktig on 2006-04-05
I get the same problem when I try to install Ubuntu, and I've tried to use several different configurations, both standard/expert, with acpi=off, noapic nolapic, different copies of the cd and using both of my cd-players...
 It worked one time(with expert pci=noacpi i think), but when in Gnome, not much worked correctly, especially not the networking.
 And I didn't burn the cd's myself, they were those you get when ordering "official" Ubuntu cd's.
 Besides those problems he listed, hardware identifying fails sometimes and something more that I don't remember right now. 

anybody got a clue?

---

### Post by Mustard on 2006-04-05
[QUOTE=felaktig]I get the same problem when I try to install Ubuntu, and I've tried to use several different configurations, both standard/expert, with acpi=off, noapic nolapic, different copies of the cd and using both of my cd-players...
 It worked one time(with expert pci=noacpi i think), but when in Gnome, not much worked correctly, especially not the networking.
 And I didn't burn the cd's myself, they were those you get when ordering "official" Ubuntu cd's.
 Besides those problems he listed, hardware identifying fails sometimes and something more that I don't remember right now. 

anybody got a clue?[/QUOTE]

I know how to fix the problem with your administrative tasks after an expert install.  Do you have it installed still?

When using the expert install option the first user is not setup with superuser privileges by default.  Being an expert install, it assumes you know how to do this via a root prompt in terminal.  The expert install sets up a root password for this purpose (the default install has no root password).  If you want to try again with expert install, then send me a PM and show me a thread where I can post the details of how to set up a superuser enabled account after an expert install, I'll show you the way.  Preferably start a new thread, so as not to hijack this one though.

---

### Post by jfreak on 2006-04-16
i've done a lot of reasearch on this problem,

i dont know the answer but i can assure you that it is not a bad burn or a bad iso.  half the people with the problem are using ordered pressed disks.

It's not a problem with your cd drive either becuase windows installs fine on all the computers i've tried with this problem.

I'm starting to think that ubuntu just smells like pits.  ](*,) 

i'm gonna call the ubuntu ppl today

---

### Post by mumushi on 2006-05-31
try using a new cdrom. just try. not with the same brand you are using.

---

### Post by Hachi-Roku on 2006-06-03
im getting the same debootstrap problem too dude.

i find it goes away and/or changes from return value 1 to 2 by choosing different partition formats. sounds weird.. i dont really get it, i just try stuff until it works.

im also usignthe 'shipped' ubuntu cd's.

J

---

### Post by sagarhshah on 2006-06-03
I had the debootstrap problem with 5 different shipit cds as well.
I then downloaded the iso and burnt it at 4x and everything installed fine.

So I am thinking that the shipit cds are suspect.

---

### Post by sagarhshah on 2006-06-03
[QUOTE=jfreak]
i dont know the answer but i can assure you that it is not a bad burn or a bad iso.  half the people with the problem are using ordered pressed disks.
[/QUOTE]
How can you assure us that its not a bad burn.
Just because they are ordered pressed disks can they not come out faulty?
I have encoutered many faulty pressed cds.

[QUOTE=jfreak]
It's not a problem with your cd drive either becuase windows installs fine on all the computers i've tried with this problem.
[/QUOTE]
I would have to agree with you here that its not the cd drives fault.

the problem is probably interconnected.
I have come on this problem with cd drives that are at least2-3 years old
and they dont seem to like cds which have been burnt at a high speed.

---

### Post by mumushi on 2006-06-03
[QUOTE=sagarhshah]How can you assure us that its not a bad burn.
Just because they are ordered pressed disks can they not come out faulty?
I have encoutered many faulty pressed cds.


I would have to agree with you here that its not the cd drives fault.

the problem is probably interconnected.
I have come on this problem with cd drives that are at least2-3 years old
and they dont seem to like cds which have been burnt at a high speed.[/QUOTE]

i agree with that. i once installed ubuntu using the pressed ubuntu cd. at first it gave me the error as you have encountered then i used another cdrom which is multi speed so it can read cds burned at low or high speed and it worked. my istallation has gone smooth using the pressed ubuntu cd.

---

