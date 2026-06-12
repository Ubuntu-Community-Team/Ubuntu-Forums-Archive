---
title: "???ubuntu beating windows xp allready???"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by uk_sphinx on 2006-09-27
i installed ubuntu last night to try a dose of unix.
when i installed it i had instant access to the internet set up.
i figured ubuntu had leeched information off of the windows xp installation on the seperate partition of my hard-drive.
i had a bit of a problem logging on today (i deleted the oem default account and created a new one with no priveleges)so i decided to reinstall.
during this installation i chose to scrap the xp install and go for gold with ubuntu.
once again i have instant access to the net.

can someone please explain to me why i can get straight on to the internet without having to install ethernet drivers and my isp broadband setup cd?
this usually took 5 - 10 mins on xp with me having to find all my account information!

seems to me ubuntu has 1up over xp in my mind and i have only been on it for approx 3 hours.

ow yeah...
as i said earlyer about the login.
was i right to install again?
it said my new account hadnt created the home file and my ubuntu session couldnt get past 1 second.
it wouldnt let me use the failsafe either.(im guessing this is safe mode?)
on the install it told me to run SUDO OEM-CONFIG-PREPARE to change the user account.
is this the right way to do it?
i mean i shouldnt just delete the oem user and create a new named user???

THIS IS A VERY ACTIVE FORUM  >>>>  I LIKE

---

### Post by badactress on 2006-09-27
I had the same thing happen yesterday! I brought the live CD in to work to show a few people. They were sooo impressed when it logged itself straight onto the company's network. Network drives/printers and the internet were all accessible straight away without any messing around. I've had to give away all my Ubuntu disks to people wanting to install it at home!

---

### Post by Irony on 2006-09-27
You don't need a broadband setup cd for XP - it should just connect like Ubuntu (you may need to install an ethernet driver though).

Often the providers provide a 'broadband setup cd' and make out as though it is necessary when in fact it is just advertising.

For example the bt setup has a broadband setup cd which is actually just there own Yahoo browser - it doesn't set anything up.

---

### Post by uk_sphinx on 2006-09-27
well if that is so then why is it that when i format my drive and install a fresh copy of windows xp, you cant just click internet explorer and get going!
i provide all my internet setting during the install(which ubuntu dosnt ask for)and it dont work.
ubuntu never asked for anything and it knew my host name (custemer 416 etc) and as soon as i finished installing the mozzilla browser had instant access.

---

### Post by bulldog on 2006-09-27
> **uk_sphinx said:**
> well if that is so then why is it that when i format my drive and install a fresh copy of windows xp, you cant just click internet explorer and get going!
i provide all my internet setting during the install(which ubuntu dosnt ask for)and it dont work.
ubuntu never asked for anything and it knew my host name (custemer 416 etc) and as soon as i finished installing the mozzilla browser had instant access.

Your inlog information like username and password for your internet connection is stored in Flash memory in your modem.
Ubuntu can't read that :D 

But Ubuntu can recognize your ethernet card and install's a driver for it.
Windows will do the same in most cases but there are exeptions.

I myself installed a new ethernet card and Ubuntu recognized it on next boot and windows wouldn't get it going without a driver cd.

---

### Post by uk_sphinx on 2006-09-27
that sounds about right
do you know if xp is incapable of reading the flash or was it because i didnt do something right

---

### Post by bulldog on 2006-09-27
> **uk_sphinx said:**
> that sounds about right
do you know if xp is incapable of reading the flash or was it because i didnt do something right

In fact there should be no diference if you boot windows or ubuntu.
Your modem keeps a connection with your ISP,neither windows or ubuntu read this info,cause they don't need it.

The only thing that matters is your ethernet card and it could be you have to put a driver cd in windows.
In case of onboard ethernet it's possible the drivers are provided by the motherboard cd.

[it's always adviseble to install your motherboard drivers in windows]

---

### Post by Sgood1971 on 2006-09-27
> **uk_sphinx said:**
> on the install it told me to run SUDO OEM-CONFIG-PREPARE to change the user account.
is this the right way to do it?
i mean i shouldnt just delete the oem user and create a new named user???

If you did an OEM install, then yes, this is the way to do it. Then just restart.

---

