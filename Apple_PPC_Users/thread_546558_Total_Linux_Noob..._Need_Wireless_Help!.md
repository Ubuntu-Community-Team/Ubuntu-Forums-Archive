---
title: "Total Linux Noob... Need Wireless Help!"
date: 2007-09-09
forum: Apple PPC Users
---

### Post by rl1643 on 2007-09-09
Hey Every One!!!

so i have been using windows for my whole life, and mac since 2005... but now i want to get into the linux world...

i can totally install 7.04 fine and it seems to work pretty speedy on my iBook G4 1.33 GHz 1.5GB ram, and of course i came into the wireless issues right away

so knowing what i know i turned to google... i came to a couple sites and tried MANY different things... such as "http://www.speedyshare.com/214793933.html" and going through and doing some sudo aptitude stuff in terminal lol

after a restart i noticed now it shows wireless internet and i can see a TON of routers including my own... the only thing is i cant connect to any of them, protected or not... it just sits there with the blue thing going around in circles then goes back to no connection!

i saw on a website that it only works with B+G so i fiddled around with that but still nothing... i have a Netgear WPN824 and i cant connect worth a damn to it!!!

can anyone help me?! im realling into ubuntu and want to try it without being tied down to a cord!!! 

THANKS

---

### Post by jimrz on 2007-09-09
first go to Panel > System > Administration > Network > the DNS tab and make sure that it has the appropriate servers listed. if that is not it, please either post your wifi card info (make/model/chipset) or, better yet, search these forums for your Ibook model and learn how others have gotten their wifi working ( you might start [[COLOR="Sienna"]**_here._**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=201902&highlight=iBook+G4"))

---

### Post by rl1643 on 2007-09-09
Thanks, I have since switched back to os x... but this is what it says in system profiler about my wifi card

AirPort Card Information:

  Wireless Card Type:	AirPort Extreme
  Wireless Card Locale:	USA
  Wireless Card Firmware Version:	405.1 (3.90.34.0.p18)
  Current Wireless Network:	*****************
  Wireless Channel:	6

After reading more of the posts out there, i found many people have the same problem... and people make them go through pages of steps which lead to nothing...

anymore help?

Thanks

---

### Post by rl1643 on 2007-09-09
Sorry, the stuff i copied came out with a happy face on it... should say

 Wireless Card Firmware Version:	405.1 (3.90.34.0.p"1 8 )" <---- everything in the "" should be pushed together no spaces

---

### Post by jimrz on 2007-09-09
> **rl1643 said:**
> Sorry, the stuff i copied came out with a happy face on it... should say

 Wireless Card Firmware Version:	405.1 (3.90.34.0.p"1 8 )" <---- everything in the "" should be pushed together no spaces

no prob, that happens to folks all the time

yeah, there are issues with that broadcom chipset, although I beleive many have been able to get them working after jumping through a lolt of hoops. Fortunately I have never had to deal with one, so cannot offer any real assistance. Sorry it didn't work out for you, this time.

---

