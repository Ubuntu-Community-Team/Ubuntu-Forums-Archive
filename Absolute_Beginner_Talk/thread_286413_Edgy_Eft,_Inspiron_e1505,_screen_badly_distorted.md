---
title: "Edgy Eft, Inspiron e1505, screen badly distorted"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by Taigrr on 2006-10-27
I have no idea where i'm going here.

I installed Dapper, and it worked pretty well, but my Intel Pro Wireless 3945 wouldn't work. At all..

So I downloaded Edgy, burnt it, and installed. Installation seemed to work okay, but when it booted to X, the damn thing went sour! The screen is badly distorted, so bad that it's hard to describe how. It -MIGHT- be a super low resolution, but I don't even know. It's just a huge mess, can't see anything at all. Just alot of brown. However, I managed to log in, and it kinda corrected. The bars along the top and bottom seemed in place, at least, but everything was messed up. Buttons, icons, background image. It was all still horribly wrong.

Can someone please help? I bought this laptop spacificly because everything I read pointed that it would all work great, and it seems that it doesn't work at all.


--ATI Radeon x1300, 15.4 inch WSXGA+ Ultrasharp, Intel Core Duo (t2300?), Intell PRO/Wireless 3945a/g

---

### Post by John.Michael.Kane on 2006-10-27
You need to get the proper ati drivers installed.

Have you tried sudo dpkg-reconfigure xserver-xorg 


Your other option is.

log out hit ctrl f1 type sudo nano /etc/X11/xorg.conf 

look for this section,and make sure you using vesa

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia" this needs to say vesa
EndSection

---

### Post by Dual Cortex on 2006-10-27
I'm having a similar problem. In fact, in X i don't see anything, just a blank screen. I press CTR+ALT+F1 and it takes me to another screfen that is really trashed. It's full of horizontal lines.. not ecen straight lines... anyway the screen is realy messed up. When I type something in, I see like a white spot on the screen. When I press CTRL+ALT+F7 or F8 the screen again is blank, except it has turned gray.

This is just after installing EDGY. I haven't able to boot Edgy once until now.

BTW, I was having the same problmes with the liveCD but when I used 800*600 to boot up the live CD, it worked for me (Even though Im sure the resolution was a lot higher than that when it booted up to the liveCD's X)

I'm on a desktop, Using an nvidia 7300LE (](*,) )

---

### Post by Taigrr on 2006-10-28
I can't get into those files at all.

I sign in (Because it's already set to typing in the login box), and press alt F2 to get into a terminal, and the screen is still completely jacked.

I've abasolutely no idea what's going on. Apearently, other people are having hte same problems.

So is there a way to get my intel card working on Dapper? Because Edgy is a failure for now. Maybe wait 'till the next update.

---

### Post by John.Michael.Kane on 2006-10-28
This may help you get your wireless going under dapper [http://ubuntuforums.org/showthread.php?t=140085&highlight=Intel+Pro+Wireless+3945](http://ubuntuforums.org/showthread.php?t=140085&highlight=Intel+Pro+Wireless+3945)
[WifiDocs-WiFiHowTo]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo")


Aslo once you have dapper setup how you want you could try backing up your config files for xorg,and  try using those settings to get edgy going.

---

