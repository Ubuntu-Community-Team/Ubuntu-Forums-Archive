---
title: "does any one managed to run MS office in ubuntu 7.04"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-06-13
Hi
Thank you for reading my post
Does any one managed to run ms office in ubuntu 7.04 ?
Open office is not good for me yet and i prefer to use MS office 2007 or MS office 2003, is there any way to do this?


thanks

---

### Post by pardesi on 2007-06-13
by running ms office do you mean running ms ofice in wine or .doc files

---

### Post by whizbaby on 2007-06-13
Get VMware and search on this forum howto use it (e.g. this howto [http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware+howto](http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware+howto)).
But believe me, the only reason you should do this is not to use msoffice (its only a matter of habits. use oo a while and it will be much easier to use), but to be able to use VMware :P

---

### Post by legolas_w on 2007-06-13
Hi
I mean runnign ms office (installing it and running it)
Thanks.

Using vmware is not an option for me because i do not want to be in windows env i just can not be good with OO yet and i am looking to find a way to use ms office inside ubuntu 7.04


thanks

---

### Post by pardesi on 2007-06-13
well one thing there is nothing that oo can't do and MS-office-X, X<2007 can do...i haven't tried MS-office 2007 so no comments

---

### Post by HotShotDJ on 2007-06-13
Best bet is [Crossover Office]("http://www.codeweavers.com").  But it costs money.  You can try WINE, but probably won't be very good.  Best option, learn how to use OpenOffice.  You'll never learn it if you don't start using it.  The only special skill you'll need is a willingness to learn.

---

### Post by starcraft.man on 2007-06-13
> **legolas_w said:**
> Hi
I mean runnign ms office (installing it and running it)
Thanks.

Using vmware is not an option for me because i do not want to be in windows env i just can not be good with OO yet and i am looking to find a way to use ms office inside ubuntu 7.04


thanks

Well thats unfortunately "tough luck" as they say. [WINE lists MS Office here.]("http://appdb.winehq.org/appview.php?iAppId=31") As you can see it works very bad... and I don't see it improving any time soon (would render Windows a bit moot). You can try CrossOver but thats paid and it won't run either 2003 or 2007 well from what I've heard. The best you can probably get is office 2000 in WINE/CrossOver and that version is so old OO might just be better.

Edit: Lol, yes hotshot, Linux takes lots of new learning but there are so many resources that if you do it right you don't even notice :D.

---

### Post by whizbaby on 2007-06-13
If you dont want VMware better forget about running MSoffice from inside linux or be prepared to write a lot of C code...
The point in time where microsmurf opens their dll's to the world is far far in the future. Perhaps even, when we are extremely unlucky, only in a parallel universe.
Why is VMware so bad? Just only open MSoffice in your VMware window...

btw, is there any parallel_universe repository?

---

### Post by HotShotDJ on 2007-06-13
> **starcraft.man said:**
> Edit: Lol, yes hotshot, Linux takes lots of new learning but there are so many resources that if you do it right you don't even notice :D.Yes indeed. :D  Personally, I think using Linux and native Linux applications is as easy as falling off a log.  But for others, the instant things are not EXACTLY (including color scheme) like Windows, they act like their world has come to an end.  I've considered writing a daemon to put in /etc/init.d that randomly reboots Linux so that newbie will feel more at home.
:lolflag:

---

### Post by legolas_w on 2007-06-13
> **HotShotDJ said:**
>  I've considered writing a daemon to put in /etc/init.d that randomly reboots Linux so that newbie will feel more at home.
:lolflag:

;)  you burned MS with that suggestion :)  :popcorn: :D

---

### Post by starcraft.man on 2007-06-13
> **whizbaby said:**
> If you dont want VMware better forget about running MSoffice from inside linux or be prepared to write a lot of C code...
The point in time where microsmurf opens their dll's to the world is far far in the future. Perhaps even, when we are extremely unlucky, only in a parallel universe.
Why is VMware so bad? Just only open MSoffice in your VMware window...

btw, is there any parallel_universe repository?

Theres [Virtual Box]("http://www.virtualbox.org/") too ya know, and its partly open source. I really like that. Its also completely free.

> **HotShotDJ said:**
> Yes indeed. :D  Personally, I think using Linux and native Linux applications is as easy as falling off a log.  But for others, the instant things are not EXACTLY (including color scheme) like Windows, they act like their world has come to an end.  I've considered writing a daemon to put in /etc/init.d that randomly reboots Linux so that newbie will feel more at home.
:lolflag:

ROFL! Oh man that's funny... if just a bit mean :p.

---

### Post by whizbaby on 2007-06-13
> **starcraft.man said:**
> Theres Virtual Box  too ya know, and its partly open source. I really like that. Its also completely free.

No, me dint know, thanx, will taka look.

> I've considered writing a daemon to put in /etc/init.d that randomly reboots Linux so that newbie will feel more at home

youll get sewed by Bill 'rusty angles' Gates for copying his product.

---

### Post by starcraft.man on 2007-06-13
> **whizbaby said:**
> No, me dint know, thanx, will taka look.

It's a great product, I think its almost matched VMware for features (Workstation still has a few but Virtual Box still young).

Best of all, you can add it as a repo that they maintain and install/upgrade without worrying about deb files. Check in the downloads section.

---

### Post by floke on 2007-06-13
AFAIK MSWord 2000 runs fine under Wine, as does Excel. I haven't road tested them thoroughly myself, but have installed them under Wine for others and haven't heard of any issues (maybe they're using OOo instead ;)).

---

### Post by NewJack on 2007-06-13
Why not try using OpenOffice?  It's in the repos and it does pretty much everything M$ Office does.

---

### Post by AlanR8 on 2007-06-13
I run Office 2003 under Crossover with NO problems.

I do agree with earlier posts about using OO and agree its a competent bit of kit. However, I am working with one of the U K's leading banks at present doing training design work, and their WP of choice is MS Word with some "tricky" templates and style sheets.

I decided to go with the flow and installed Office 2003 without a hitch.

Works well.

---

### Post by brharri1 on 2007-07-08
I use MS Office 2003 under crossover 6. I can't copy a chart from excel into word. I can copy and paste everything else but not a chart/graph. Does anyone know if this is a bug or fixable?

OO.org is fine for word. If someone could tell me how to do a simple linear regression in calc then I might consider using it. The linear regression line isn't all that much good without the ability to display the equation.

---

### Post by Old Pink on 2007-07-08
If it's just Open Office you dislike, try Abiword. :) 

It's in the repositories, which means you can add it via Applications > Add/Remove :D 

Alternatively, run **sudo aptitude install abiword** in a terminal window. ;) 

Loads a bit faster. Worth a look. :)

---

### Post by mihaimm on 2008-01-17
> **brharri1 said:**
> OO.org is fine for word. If someone could tell me how to do a simple linear regression in calc then I might consider using it. The linear regression line isn't all that much good without the ability to display the equation.

[http://www.openofficetips.com/blog/archives/2005/04/regression_anal.html](http://www.openofficetips.com/blog/archives/2005/04/regression_anal.html)
[http://www.openofficetips.com/blog/archives/2005/04/regression_anal_1.html](http://www.openofficetips.com/blog/archives/2005/04/regression_anal_1.html)

---

### Post by tigerplug on 2008-01-17
Open Office is all you need!

---

