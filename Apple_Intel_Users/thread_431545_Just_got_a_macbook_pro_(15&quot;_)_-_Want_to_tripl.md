---
title: "Just got a macbook pro (15&quot; ) - Want to triple boot"
date: 2007-05-03
forum: Apple Intel Users
---

### Post by The_Giver on 2007-05-03
So I want to triple boot with Ubuntu (with Beryl) , OS X,  and Windows XP.

My problem is knowing what "Software" I should have at hand.

1. What version of Ubuntu works? I'm currently downloading the desktop x86 edition (non 64 bit) (What does Ubuntu drapper live cd mean)


2. What do I need to do to be "ready" when it comes around to installing Windows XP? It seems as though I need to do something first on OS X ???? Get some drivers or something....


3. I know I will need bootcamp and rEdit but do I need to "update" bootcamp or anything in OS X before I begin?


I found this great guide but it doesn't seem to answer those questions: 

[http://ubuntuforums.org/showthread.php?t=198453](http://ubuntuforums.org/showthread.php?t=198453)


This is the guide I plan to follow to get Beryl up and running: [http://ubuntuforums.org/showthread.php?t=399643&highlight=x200m](http://ubuntuforums.org/showthread.php?t=399643&highlight=x200m)


4. This should all come after but I'm wondering how stable Beryl is in comparison to Ubuntu with Beryl on a PC?


5. Last but not least: is Feisty   just the name for the latest ubuntu?


Thanks in advance!

---

### Post by michaels on 2007-05-03
[http://www.cs.helsinki.fi/u/jzshen/install_feisty.html](http://www.cs.helsinki.fi/u/jzshen/install_feisty.html)

---

### Post by ronocdh on 2007-05-03
> **The_Giver said:**
> So I want to triple boot with Ubuntu (with Beryl) , OS X,  and Windows XP.

My problem is knowing what "Software" I should have at hand.

1. What version of Ubuntu works? I'm currently downloading the desktop x86 edition (non 64 bit) (What does Ubuntu drapper live cd mean)
Each version of Ubuntu has a version number and a (playful!) name. Dapper Drake was Ubuntu 6.06; the first number is the least place in the year, which was 2006, and the "06" is the month. So Dapper Drake was released in June 2006. Feisty, which is indeed the latest version of Ubuntu, is 7.04, or April of 2007.
> 2. What do I need to do to be "ready" when it comes around to installing Windows XP? It seems as though I need to do something first on OS X ???? Get some drivers or something....
Burn the drivers CD via Boot Camp.[/quote]
> 3. I know I will need bootcamp and rEdit but do I need to "update" bootcamp or anything in OS X before I begin?
Make sure you download the most recent version Apple provides on their website; after that, you should be OK.> 
I found this great guide but it doesn't seem to answer those questions: 

[http://ubuntuforums.org/showthread.php?t=198453](http://ubuntuforums.org/showthread.php?t=198453)
Try these guides:
[LIST]
[*][http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu)
[*][https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
[*][http://ubuntuforums.org/showthread.php?t=198453](http://ubuntuforums.org/showthread.php?t=198453)
[/LIST]
> 4. This should all come after but I'm wondering how stable Beryl is in comparison to Ubuntu with Beryl on a PC?
It's tricky. Beryl definitely works best on Nvidia cards due to the open drivers; with a Radeon, it's going to be a bitch. In fact, the latest Beryl builds don't even support our hardware, so you'll have to do some work to get the older versions of Beryl installed. I used this [slightly dated guide]("http://ubuntuforums.org/showthread.php?t=399643&highlight=x200m") to get Beryl up and running on my machine.
> 5. Last but not least: is Feisty   just the name for the latest ubuntu?
Indeed!

---

### Post by ronocdh on 2007-05-03
> **michaels said:**
> [http://www.cs.helsinki.fi/u/jzshen/install_feisty.html](http://www.cs.helsinki.fi/u/jzshen/install_feisty.html)
This is indeed a very helpful guide, just remember that: 

> [B]Note:
       My macbook pro is one of the first generation with 2.00 GHz CORE DUO processor and 1G memory! The following notes haven’t been test on the Macbook and the Macbook pro C2D![/B]

For instance, the **lpj** string shouldn't be necessary on The_Giver's Core2 Duo. But by and large, michaels's guide really is kickass! Print it out and keep it with you.

---

### Post by The_Giver on 2007-05-03
I guess I'm still confused about a few things... such as what "the live CD is"


**1. When I go to DL Ubuntu I get this options: **

a. Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM,
b. SempronTM)   64bit AMD and Intel computers 
c.   Sun UltraSPARC based

From: 
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

_I have ubuntu-7.04-desktop-i386.iso _ I assume I should be good to go.




**2. What does this mean:  "slipstreamed XP-SP2 CD"**

Is that just windows XP with the SP2 included.... what if my windows cd didn't come witht hat? I guess I might be able to "borrow" my friends CD..... I assume this is just XP prepackaged with SP 2?



**3. Michael's guide does seem to be pretty good.. however... you pointed out one difference... is there anything else I should watch out for (I know the Wireless is different from reading over one of the other guides provided).**

---

### Post by ronocdh on 2007-05-03
Your assumptions are correct. A live CD is a bootable CD that presents the user with a GUI and competent OS functionality without installing anything on the hard drive (the RAM is extensively utilized). Wireless will be an adventure, as several things will be. Just keep trying till it works. There is a post by widemos still active in this forum that has proved successful for a lot of users.

Keep the questions coming, they are welcome here.

---

### Post by The_Giver on 2007-05-03
[B]For those who have managed to triple boot on a_ macbook pro C2D_.... and got Beryl to work too... 

[/B]

1. Would you mind sharing some info as to what you are running.... Edgy?  Feisty? What guide should work? 
2. What guide did you follow to get wireless working? 
3. What about Beryl, what specific version should I use and what guide would you recommend?
4. I hear sound is a problem, has that been resolved?
5. What other issues will I face?
6. If I can afford to buy Windows Vista Ultimate... should I do that or is it not very well supported at all?

I mean.... its all the same identical hardware right...  so is Beryl not stable even when using the older version?

---

### Post by ronocdh on 2007-05-03
> **The_Giver said:**
> [B]For those who have managed to triple boot on a_ macbook pro C2D_.... and got Beryl to work too... 

[/B]

1. Would you mind sharing some info as to what you are running.... Edgy?  Feisty? What guide should work? 
2. What guide did you follow to get wireless working? 
3. What about Beryl, what specific version should I use and what guide would you recommend?
4. I hear sound is a problem, has that been resolved?
5. What other issues will I face?
6. If I can afford to buy Windows Vista Ultimate... should I do that or is it not very well supported at all?

I mean.... its all the same identical hardware right...  so is Beryl not stable even when using the older version?
[LIST=1]
[*]I installed Beryl using the guide I've linked to above, and used Feisty final.
[*]I hear wireless works great according to the how-to widemos has posted here recently; I myself haven't implemented his tips, but I'll get around to it sometime soon.
[*]The guide I've linked to above is very explicit about Beryl version numbers.
[*]I have never had a problem with sound in Feisty; IIRC I had to open the sound preferences pane in order to make the F4 and F5 keys adjust my speaker volume, but other than that, everything worked out of the box.
[*]You won't find anyone recommending you buy Microsoft products here. ;)
[/LIST]

---

### Post by The_Giver on 2007-05-03
Well let's say I can magically get windows vista on a cd..... I want to test it out really.... 

I found this guide but its not for ubuntu.. however it seems pretty good and covers Vista:


[http://tripleboot.is2.byuh.edu/](http://tripleboot.is2.byuh.edu/)

Is it a lot different if I want to isntall ubuntu?

---

### Post by ronocdh on 2007-05-03
> **The_Giver said:**
> Well let's say I can magically get windows vista on a cd..... I want to test it out really.... 

I found this guide but its not for ubuntu.. however it seems pretty good and covers Vista:


[http://tripleboot.is2.byuh.edu/](http://tripleboot.is2.byuh.edu/)

Is it a lot different if I want to isntall ubuntu?
There are people [who have done it]("http://ubuntuforums.org/archive/index.php/t-384449.html"). Keep searching and you'll find guides; just always make sure to back up your data, and keep tinkering until it sticks!

---

### Post by The_Giver on 2007-05-03
That thread you linked to is the only one on ubuntu that talks about it but it is a bit dated  =/.. still looking for a better guide.

---

