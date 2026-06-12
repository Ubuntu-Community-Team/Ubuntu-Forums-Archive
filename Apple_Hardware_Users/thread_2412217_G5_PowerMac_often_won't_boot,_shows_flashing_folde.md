---
title: "G5 PowerMac often won't boot, shows flashing folder / finder icon"
date: 2019-02-09
forum: Apple Hardware Users
---

### Post by conaljardine on 2019-02-09
I have a G5 PowerMac. 

It seemed to have died, but after removing OSX and installing Lubuntu/Xubuntu 16.04 as the only operating system it is working well again, once it boots. 

However, it usually won't boot on the first attempt. Instead I get the flashing folder/finder icon which tells me it is not recognising the hard drive.

It usually finds the hard drive after pressing the power button a few times, but I would like to fix this if possible. 

[COLOR=#000000]As far as I can remember (a few months ago), I zapped the PRAM/NVRAM and did a SMU reset. [/COLOR][COLOR=#000000]I did not do this through OpenFirmware, I did this by holding down key combinations at startup and by pressing a small button on the motherboard.

I [/COLOR][COLOR=#000000]replaced the battery on the logic board/mother board.

I have the HD on cable select (but have tried master).

---

Today I found this suggestion for OSX/MacOS users:

Boot into OpenFirmware and type the following:

reset-nvram (enter)
set-defaults [/COLOR][COLOR=#000000](enter)[/COLOR][COLOR=#000000]
reset-all [/COLOR][COLOR=#000000](enter)

MY QUESTION IS THIS: Should I do this? I think there are two parts to this question: 1. Could it make matters worse? 2. Is there any point (or will it do anything different)? 

Thanks in advance!

Conal 


[/COLOR]

---

### Post by gsahli on 2019-02-10
Short answer - it won't hurt.
But I don't think it will help. I think your hard drive is failing, causing a delay in finding the system (maybe a delay in spin-up?). You can partially test this "delay" theory by starting up with the option key held, then choosing the boot drive and booting. Does it ever fail to boot on the first try? Doing the option key is in effect delaying startup for the drive to get going.

---

### Post by conaljardine on 2019-02-11
I think you are right gsahli.

OpenFirmware makes no difference. When I start with the option key it doesn't find the hard drive, though I have used this method successfully in the past. However, it does sometimes boot on the first try when pressing the power button. I'll carry on pressing the power button as many times as it takes until I can replace the hard drive. 

Thanks for your help!

---

### Post by coralof on 2019-02-15
I had this same problem with a MacBook Pro. It turned out the drive wasn't seated all the way into the connector; it had jiggled loose, and so would lose connection when booting sometimes. It could also be a slow onset drive failure. I've had my fare share of those, too.

---

