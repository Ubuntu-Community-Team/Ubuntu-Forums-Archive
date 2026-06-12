---
title: "No Internet connection after changing netgear router to Zyxel"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Andy Aardvark on 2008-01-21
Hello everyone,

First post in this splendid community and obviously I am in trouble or else I wouldnt be asking for your much appreciated help!
Due to the failing of my Netgear Router (wired) I replaces this with a Zyxel model (also wired).
Having a dual boot system of XP and Feisty Fawn I was sinfully using the XP for quite a while as I am new to Linux, before I noticed the Internet problem, that being I cannot access the internet at all!

So any ideas would be very helpful so I can continue to build more user hours on this great OS rather than switching back to Windows!

Cheers, AA

---

### Post by mikeyphi on 2008-01-22
The obvious question back to you must be - Are you sure you've set up the new Router with your ISP's details?

I remember that when I first setup my Netgear Router I had to input details on the Router via a browser - if your new Router has a similar requirement (and I guess all routers must have some method of setting domains etc) then there ought to be some paperwork/CD with info re input method.

---

### Post by Andy Aardvark on 2008-01-24
Hi mikeyphi

Details have been entered into the router initially and these work perfectly with Windows (spit) so I am at a loss. I was wondering whether the system needed to "see" the new router and if a setting in Ubuntu must be changed?

Thanks for the comment!

---

### Post by Andy Aardvark on 2008-01-24
Edit - I did have to enter differnent details into the Zyxel router from the Netgear one, would this have an impact as I can still access the net in XP?

---

### Post by mikeyphi on 2008-01-24
The wired connection works in windows - so should work in Ubuntu.
Can you confirm that you have enabled the wired connection via the Network Manager?

---

### Post by Andy Aardvark on 2008-01-24
I believe I have, I also clicked on the network icon at top right of desktop which scanned and reported that network was found. I should probably explain that this is a newish problem, when I installed Ubuntu on my system I ha dthe Netgear and all was working fine until the bloody thing stopped working. Since then I have been unable to get onto the net in Ubuntu but have no problems with windows XP!

---

### Post by seventhc on 2008-01-24
can you open a terminal and enter this
```
ping 66.94.234.13
```
whats the output of that.

---

### Post by Andy Aardvark on 2008-01-24
Thanx seventhc

Not too hot on Ubuntu at the moment but will give it a go - probably tomorrow now (dual boot and am on windows at the moment), will let you know!

Cheers Andy

---

### Post by Pelham123 on 2008-01-24
Could you also paste the results of 'ifconfig' command?

---

