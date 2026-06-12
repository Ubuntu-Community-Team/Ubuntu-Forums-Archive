---
title: "Another Firefox issue..."
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by MrJackdaw on 2007-01-12
Hi,

I have googled and read as many reports on slow firefox as I can, and still have the problem I am about to describe below...

I installed Edgy as my first introduction to Linux - alas in retrospect maybe it should have been Dapper, but if you don't know you go for the newest! - Firefox did not work. I managed to resolve my DNS servers - but still had a slow connection.

Recently this problem appears to have become worse. The time lag spent went Looking up a page is phenomenal.

I have tried disabling ivp6, both through Blacklist and Firefox and this had no effect. I have also stripped out all the add-ons from firefox except NoScript - which I never do without.

Does anyone have any new ideas?

James

PS If I can't resolve this I will have no choice but to... return to bleh windows - I was just on the verge of deleting that partition!

---

### Post by r4ik on 2007-01-12
You could try set pipelining maxreguest from default 4 to 40 (about:config)
Reversable if no cure.

Good luck !

---

### Post by x1a4 on 2007-01-12
Try this: 

1) With superuser priviledges add (or edit if exists) the file

/etc/modprobe.d/bad_list

to contain the line 

alias net-pf-10 off

2) Reboot.


Good luck.

---

### Post by obsidion on 2007-01-12
You could try swiftfox, it is a lot crisper on my system. I wouldn't give up on linux just because one program is not to your liking. Have you tried Opera or one of the many other browsers, do they have the same issues. If they do then there is possibly something in your network setup that is causing the problem.

If you want to try the swiftfox route add
deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free

To your /etc/apt/sources.list

---

### Post by MrJackdaw on 2007-01-12
Boy, Do I feel stupid ](*,) 

I was using the WRONG DNS settings - I had transposed two digits by mistake.

Sorry guys!

Hell, Thank you for your help - my main attraction to Linux is the amount of support - the feeling of community...

Thank you!

James

---

### Post by DougieFresh4U on 2007-01-12
Although you solved your problem, still take a look at Swiftfox. Great browser that snaps to attention when summoned, :)

---

### Post by MrJackdaw on 2007-01-12
Trying SwiftFox now!

---

### Post by DougieFresh4U on 2007-01-12
> **MrJackdaw said:**
> Trying SwiftFox now!

Curious to know your impression   :-k

---

### Post by MrJackdaw on 2007-01-13
It seems to be well... the same as firefox - which is nice but - a *little* faster. And speed is everything!

Is there any way to measure the speed of a web browser? :-k

---

### Post by k1001001 on 2007-01-13
I think its speed is due to a RAM cache. Does it load normally the first time, and then faster every time afterwards? If so, then it is probably a RAM cache.

---

