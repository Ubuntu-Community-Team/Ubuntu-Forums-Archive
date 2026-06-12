---
title: "I want to get rid of Windows on this Old Laptop"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by Amadeo on 2007-10-10
Hey gang,

I'm trying to get rid of Windows on this old Dell laptop I have.  It's a Dell Inspiron 5000 with a 600MHz Pentium 3 processor and 512MB RAM.  Here is the Dell specifications page:

[http://support.dell.com/support/edocs/systems/pblan/specs.htm](http://support.dell.com/support/edocs/systems/pblan/specs.htm)

The problem I'm having is that my laptop fan never turns on and the laptop overheats.  I've tried looking into i8kfan and such, but they don't seem to support my laptop.  Everything works fine in Windows, but I'd really prefer to run Linux on the laptop.

I've tried many different Linux distributions as well as various versions of Ubuntu, including the latest beta.  They all cannot seem to control my laptop fan.  The only other detail I can provide is that when I boot Ubuntu, I get a bunch of errors saying something like:

ACPI: [package] has zero elements (debD6cc0)

I hope that I can get rid of Windows for good on this laptop with your help!

---

### Post by kthakore on 2007-10-10
have you tried the SLAX livecd. It fixed a similar problem for me. If this CD doesn't do it your fan maybe broken or miswired. If the only problem with the laptop is heat try a cooling pad for the laptop.

---

### Post by Amadeo on 2007-10-10
> **kthakore said:**
> have you tried the SLAX livecd. It fixed a similar problem for me. If this CD doesn't do it your fan maybe broken or miswired. If the only problem with the laptop is heat try a cooling pad for the laptop.

I have tried a few distributions based on SLAX, I do not thing that will fix the problem.  My fan works in Windows, so I don't think it's the hardware itself.  I think it has to do with power management or perhaps something else.  I wish I knew more about this stuff!

---

### Post by kthakore on 2007-10-10
did u try replacing the normal power manager with powernowd.

---

### Post by Amadeo on 2007-10-10
I have read that this laptop BIOS is really APM with a little bit of ACPI support.  I'm not sure if the standard power managers work correctly.  I remember seeing powersave but I couldn't tell you exactly what was running.  I've put Windows back on the laptop for now so it didn't burn out.  I'm just trying to get a working method for when the next Ubuntu is released in a week!

---

### Post by kthakore on 2007-10-10
If you didn't install powerknowd then it was not on the system. Try this

-cool several cool packs over nights (I used about 7)
- get a cool pack and zip lock it twice and put it under the laptop seperated by paper towels (I know it sounds weird but don't skip this step especially if the laptop is dell) 
- now install linux and sudo apt-get powerknowd
- and install lm_sensors (monitors your fan) [GUIDE]("http://news.softpedia.com/news/How-to-Install-lm-sensors-on-Ubuntu-47205.shtml")
- if lm_sensors doesn't find you fan then try this forum post [http://www.sudhian.com/index.php?/forums/viewthread/98254/]("http://www.sudhian.com/index.php?/forums/viewthread/98254/")

thats how I fixed my laptop fan.

---

### Post by tgalati4 on 2007-10-10
A laptop of that vintage probably has non-standard power/thermal control.  You could try using apm instead of acpi.  Post relevant portions of dmesg right after boot.

Do you have any way of setting max fan speed in BIOS?  Is there a BIOS update from Dell?

I have an Inspiron 7500 (PIII, 500 MHz) and I don't have heating problems.  Fan comes on when it is supposed to.  I have a temperature monitor which shows 50-62C during operation.  These processors tend to run hot.  I'm currently running Dapper.

Try giving Dapper Live 6.06.1 a spin.

See if you can declock your processor in BIOS.  That might give you more working time to try different things.

---

### Post by Amadeo on 2007-10-10
> **kthakore said:**
> If you didn't install powerknowd then it was not on the system. Try this

-cool several cool packs over nights (I used about 7)
- get a cool pack and zip lock it twice and put it under the laptop seperated by paper towels (I know it sounds weird but don't skip this step especially if the laptop is dell) 
- now install linux and sudo apt-get powerknowd
- and install lm_sensors (monitors your fan) [GUIDE]("http://news.softpedia.com/news/How-to-Install-lm-sensors-on-Ubuntu-47205.shtml")
- if lm_sensors doesn't find you fan then try this forum post [http://www.sudhian.com/index.php?/forums/viewthread/98254/]("http://www.sudhian.com/index.php?/forums/viewthread/98254/")

thats how I fixed my laptop fan.

Thank you, I'll try all these next week when 7.10 is out.  I don't want to mess with it just yet.  The reason I said I thought  it was running previously is I've tried a lot of distributions now, so perhaps one of those was running it. I've used the following on this laptop:

PCLinuxOS
Wolvix
Zenwalk
Ubuntu
openSUSE
Fedora
Sabayon
Arch
...possibly more that I'm forgetting.

I do it for fun more than anything, but in none of them did my laptop fan ever turn on. :(

---

### Post by Amadeo on 2007-10-10
> **tgalati4 said:**
> A laptop of that vintage probably has non-standard power/thermal control.  You could try using apm instead of acpi.  Post relevant portions of dmesg right after boot.

Do you have any way of setting max fan speed in BIOS?  Is there a BIOS update from Dell?

I have an Inspiron 7500 (PIII, 500 MHz) and I don't have heating problems.  Fan comes on when it is supposed to.  I have a temperature monitor which shows 50-62C during operation.  These processors tend to run hot.  I'm currently running Dapper.

Try giving Dapper Live 6.06.1 a spin.

I've updated the BIOS to the latest that Dell offers, but it really has basic options.  It basically asks if I want power management on or not, and that's about it.  I've tried turning it off to see if the fan would just run permanently, but that didn't work either.  I'm not too experienced in Linux, but I have tried turning off ACPI and enabling APM at the GRUB boot loader.  I don't know if it actually did anything or not, but I know the fan still didn't come on.

I'll look for that version of Dapper and try it out as well.

Edit:
I forgot to add, I've also tried using antiX which is based on Mepis and I believe uses some Dapper packages.  I had no luck with it either, so I'm not sure if that means anything for using Dapper itself or not.

---

### Post by tgalati4 on 2007-10-11
I tried changing the default trigger temperature for the CPU fan on my Inspiron 7500.  I think it's set to go on at 70C which is toasty.  Mine only goes on intermittently under heavy load.  I get a boot error when trying to change the trigger temperature so it remains at the default value.

It could be that your processor is more sensitive to thermal cycles than the thermal cycle that triggers the fan.  Another possibility is that the fan is frozen (with dust) which causes the heat sink to get toasty.

---

### Post by kayvortex on 2007-10-11
The fans on my laptop (Dell Inspiron 9400) would stay on a low setting (if they were on at all), which meant that my laptop would hover at 50-60 deg C and push 70 deg C sometimes. I was running x86_64 Ubuntu, which meant that, apart from lm-sensors not detecting anything, I couldn't use i8kutils. If you are using a Dell Inspiron, try [this]("http://ubuntuforums.org/showthread.php?t=463590"): I don't know if it'll be of any use, but it might be worth checking out.

---

### Post by Amadeo on 2007-10-21
Alright everyone,

I've installed Xubuntu 7.10 on this laptop.  Lots of bugs this release I guess, but among other things, my fan still doesn't come on no matter how hot the laptop gets.  I have enabled APM instead of ACPI since it wouldn't even boot with ACPI enabled.  

i8kfan and dellfand don't seem to work on this laptop, but I appreciate the suggestions.  Also, to those saying my fan is stuck, I just want to reiterate that it is not, the fan works fine when I have Windows installed.

If I can get the fan to work properly, this laptop will be staying Xubuntu forever!

---

### Post by TygerTung on 2008-03-06
I have xubuntu on this laptop here it is a inspiron 5000. It tells me somthing about the acpi package having no elements like the fellow before described.

Now I have NO idea what this acpi buiseness is, but it would seem from reading this thread that it has somthing to do with a CPU fan? Well despite the acpi package having no elements, there still seems to be a whirring noise coming from the computer, sort of like a fan and it's been running for hours and hasn't blown up yet and no smoke has come out of it and no funny smells, so would it be fair to say that I can just ignore this acpi debarcle and keep computing as usual?

---

