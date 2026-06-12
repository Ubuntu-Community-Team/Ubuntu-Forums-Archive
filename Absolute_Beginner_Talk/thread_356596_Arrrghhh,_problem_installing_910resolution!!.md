---
title: "Arrrghhh, problem installing 910resolution!!"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by Ki11ah on 2007-02-08
I have a display running OOo presentations but the screen keeps shutting down and throwing up a no rgb signal error. I presumed this was because of the refresh rate being stuck on 60hz.

I searched the forums and found out about 910resolution so I duly downloaded it with synaptic package manager but now can't see what i need to do next.

Any idea's?

ps.Linux n00b so please be gentle

---

### Post by teaker1s on 2007-02-08
if it's a pc you should be able to find monitor specification of the internet and 
[COLOR="Red"]sudo dpkg-reconfigure xserver-xorg[/COLOR]
failing that you will need to manually edit your xorg file

---

### Post by Ki11ah on 2007-02-09
Well, I ran through the dpkg-reconfigure like you suggested and thought it had fixed my problem but I was wrong:(   within 10 minutes of running my slideshow the screen has shutdown with the 'No RGB SIGNAL INPUT ERROR'.

The screens are AMW M159A 15" LCD, I have a test machine beside me running on a 17" AMW and it is running absolutely fine so I can't understand why the 15" screens keep shutting down.

For reference, the screens have been running MS .ppt displays 24/7 with no problems whatsoever for the last 6 months!

All idea's welcome.

p.s. I am using 6.06 Dapper

---

### Post by teaker1s on 2007-02-09
you could alter power management so screen is never put to sleep, if ubuntu is having a problem with it. it's under the system tab on desktop either in administration or preferences 
 power management.

reason I can't be more specific is I'm using feisty and gnome is different to dapper and edgy version

---

### Post by Ki11ah on 2007-02-09
Thanks m8, I have checked power management and all is fine. I have somehow managed to get one screen running fine and have set the second to the same settings but still no joy:(

---

### Post by Ki11ah on 2007-02-11
Think I got it sorted, not sure how I did it but got both screens running sweet. Just got another 4 to sort out now. Wish me luck:)

---

