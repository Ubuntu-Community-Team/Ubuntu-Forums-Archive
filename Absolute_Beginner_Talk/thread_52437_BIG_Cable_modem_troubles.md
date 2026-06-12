---
title: "BIG Cable modem troubles"
date: 2005-07-27
forum: Absolute Beginner Talk
---

### Post by duke4e on 2005-07-27
hey there

i started exploring the world of linux a month ago. curently i really like the ubuntu distro. i have 2 problems, and both of them are related to my modem - Motorola SURFboard® Cable Modem SB5100

1st problem:
after installing any linux distro wich uses Grub as a OS loader, my modem stops to work in windows. that's really weird. after i remove linux+grub, my modem starts to work normally again.
i really don't know why it is happening. i'm not 100% that it's error because of Grub, but i'm assuming it because i had the same trouble with Mepis/Ubuntu (both use Grub) and with Yoper (wich uses Lili) i didn't have this problem.

2nd problem:
in all distros wich i managed to sucesfully install, i can't configure my modem. most of distros (including ubuntu) detect it and istall drivers for it. in ubuntu's networking propertys, it seems that modem sends/recives packages, so this explains that modem is working properly. BUT, when i run firefox (or anything other that is connecting to internet), there is not connection.

so the conclusion. after i install ubuntu i'm offline for both worlds - windows and linux.

few facts about my modem/connection:
-modem is connected to USB because i don't have Ethernet card
-(in windows) i don't have any connection stuff or anthing. after i installed the driver for my modem, i'm online forever.
-my IP adress: 193.19.222.175
-my Subnet Mask: 255.255.255.0
-Default Gateway: 193.19.222.1



PLEASE HELP ME

---

### Post by JonahRowley on 2005-07-27
Get an ethernet card.  They're cheap, they're easy to install, and they'll save you a world of trouble.

---

### Post by Omnios on 2005-07-27
Hio I have a Motorola Surfboard cable modem for a while now. I had it set up as usb to check out the difference for a while and switched back to the ethernet for certain security and performance issues. Never had it set up in Linux. Anyways with an ethernet card Ubuntu works right out of the box. I even have internet in recovery mode. Id get an ethernet card and become familar with ip reconfig as you will need it once and a while as there are minor issues once and a while pertaining to windows and Ubuntu set up at times, but rare. Then again a ip reconfig in windows may solve your connection problem.

 Edit: Actualy when Internet would not work in linux I would have to ip release and reniew in Windows till I learn't to do it in Linux which is funny because I had to do it this morning.

---

### Post by sonny on 2005-07-27
[QUOTE=JonahRowley]Get an ethernet card.  They're cheap, they're easy to install, and they'll save you a world of trouble.[/QUOTE]
Yes... that's my answer as well... buy a second hand ethernet card.

---

### Post by duke4e on 2005-07-27
[QUOTE=sonny]Yes... that's my answer as well... buy a second hand ethernet card.[/QUOTE]
 it's funny that all this time i didn't rememberd that i could get an ethernet card...
i'm a little "short" with money, but as soon as i'll have few extra bucks, i'll buy one!

thanks for a great advice!
you'll probably see me more on this boards, once i configure Ubuntu/Modem/Ethernet, cause i really don't know much about linux and i will need all the help i could get.


until then, have a good time

---

### Post by poofyhairguy on 2005-07-27
[QUOTE=duke4e]it's funny that all this time i didn't rememberd that i could get an ethernet card...
i'm a little "short" with money, but as soon as i'll have few extra bucks, i'll buy one!

thanks for a great advice!
you'll probably see me more on this boards, once i configure Ubuntu/Modem/Ethernet, cause i really don't know much about linux and i will need all the help i could get.


until then, have a good time[/QUOTE]

Get a realtek card. They are usually the cheapest, and they have AWESOME Linux support.

---

### Post by JonahRowley on 2005-08-01
[QUOTE=poofyhairguy]Get a realtek card. They are usually the cheapest, and they have AWESOME Linux support.[/QUOTE]

It's also worth noting that Realtek cards are the cheapest for a reason..  As long as you're not expecting them to perform very well, but if you're only using it for your cable modem, it'll be fine.  A new or used Ethernet card shouldn't set you back more than $10, even cheaper online (Froogle finds some for $5 and under).  Most, if not all, should be supported on Linux.

---

