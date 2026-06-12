---
title: "Help on an already wonderful guide, just having some noob problems..."
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Rapidsnow on 2007-07-03
I have an HP dv6258se laptop. That implies dual core AMD turion 64 bit processor and 2048 Shared RAM. I finally got Ubuntu working after using the noapic and nolapic flags on the installation (originally I did not use them and ubuntu loaded a grub loader that would not boot anything... bad situation.) Anyway everything is awesome and I love everything, except the wireless internet is not working.

I followed the help guide from the Ubuntu Feisty Desktop and it was awesome, I love messing around with the terminal (finally I have something I can program on.) I find it weird that an HP would have a dell wireless card, but that is what lspci tells me, and it matches exactly what this says. So here is the link to the page I was using: [https://help.ubuntu.com/community/WifiDocs/Driver/1390](https://help.ubuntu.com/community/WifiDocs/Driver/1390)

Alright, I ran through the whole thing, but I am having a few problems... 

The first command there: $sudo rmmod ndiswrapper
returns an error message saying something about it not being in proc/modules (could be the other way around, I am on Windows right now.)
Second error is when I try to blacklist the bcm43xx... it doesn't return anything at all.

Everything else works up until the final part of the thing before the last restart:
$sudo ndiswrapper -i ~/.driver/wifi/DRIVER/bcmwl5.inf

it says it is already installed.

Next the $sudo ndiswrapper -l says the driver is invalid (Twice even!)
Anyway, I would like any help you linux gurus can offer, thanks guys.

---

### Post by kevdog on 2007-07-03
You cant keep installing multiple drivers with ndiswrapper or you get errors.  You will have to remove every driver and then reinstall again.  There are a number of ways to do this but here is the easiest:

cd /etc/ndiswrapper
ls

What you will see are a bunch of directories or one directory.  You basically need to remove everything
sudo rm -R *

Check with ls, and the directory should be empty.  Then reinstall your windows driver.  Ive helped many people with the Dell 1390 wireless card, and in all cases it works with ndiswrapper!

---

### Post by Rapidsnow on 2007-07-03
Wow, thanks for the speedy reply, I will try that, if I get confused would you mind me PMing you later on?
Quick question, by reinstall windows driver, what do you mean exactly... on windows, or just in linux? The windows driver in windows is the bcm43xx

---

