---
title: "2012 Macbook Battery Life?"
date: 2013-04-16
forum: Apple Hardware Users
---

### Post by d4m1r on 2013-04-16
Hey guys, so I just installed Ubuntu 12.04 LTS (x64) on my 2012 Macbook Pro but I am a little concerned about the battery life....Under OS X, I get the full advertised battery life about ~10 hours. I haven't had the opportunity yet to fully drain the battery but so far it doesn't look like I'd get the full 10 hours under Ubuntu :( 

Anyone have any direct experience with this and if so, how many hours of battery life do you get under Ubuntu? Also, any tips/tricks/applications you can recommend to extend battery life of a Macbook running Ubuntu?

---

### Post by d4m1r on 2013-04-17
100 views and no insights? Will I get 100% the same battery life under Ubuntu as I do under OS X? Can someone please tell me from experience....:(

---

### Post by philcolbourn on 2013-04-20
My experience suggests no.

I have a MBP 9,1 (mid 2012, non retina, 15")

Issue seems to be that nvidia driver is difficult to get working and if you use nouveau instead, power consumption is high.

For me on idle it consumes 20W. This is about 3 hours use.

Other say that they can get 13W with nvidia driver.

For me (and my setup is messy using raring pre-release 13.04) nvidia either works but will not resume from sleep, or does not work.

I get different results depending on kernel I use. With 12.10 and 3.7.5, nouveau works fine but nvidia does not resume.

I'd really like a fix but I am thinking that I can't get another MacBook because Apple make it too hard to get Linux running easily - so this may be my last.

---

### Post by d4m1r on 2013-04-21
Thanks for the reply. Although, my hardware is different since I have the 13" model, it only has Intel 4000 HD graphics. Also using 12.04.

But yes so far, I can confirm that under Ubuntu, you WILL get lower battery life than under OS X....Don't know about Windows 7 vs Ubuntu (which has better) though...

---

### Post by philcolbourn on 2013-04-21
Since my reply, I have manage 10W using Intel GPU only.

[http://ubuntuforums.org/showthread.php?t=2137538]("http://ubuntuforums.org/showthread.php?t=2137538")

---

### Post by d4m1r on 2013-04-21
So how many hours do you think that would give you roughly, under Ubuntu?

If you only used the Intel GPU.

---

### Post by philcolbourn on 2013-04-22
On train tonight, Battery history indicates I used 15% in 1 hour. So at this rate I would get 7 hours. My 10 month old battery seems to have 95% initial capacity. 7 times 0.15 is 95%.

UPDATE: tonight I would have got 4.5 hours (30% drop in at least 80 minutes)

---

### Post by yello_downunder on 2013-05-23
I have a 2011 Macbook Pro 8,1 (13").  When running powertop I see about 17-25Wh of power consumption, so with a ~60Wh battery that is about 3-4 hours of battery life.  In OS X I get the advertised 7-8 hours.  At one point I tested turning everything off (including X) and got it down to about 12Wh, but at that point the system is useless for web browsing. :)

If you are comfortable with command line stuff, try a tool called powertop.  It does a fairly good job of showing you what is consuming battery life.

My efforts to increase battery life yielded maybe an extra 30 minutes or so.  Not very much.  Apple has spent quite a bit of time making OS X work well on their hardware.

---

### Post by philcolbourn on 2013-05-24
> **yello_downunder said:**
> I have a 2011 Macbook Pro 8,1 (13").  When running powertop I see about 17-25Wh of power consumption, so with a ~60Wh battery that is about 3-4 hours of battery life.  In OS X I get the advertised 7-8 hours.  At one point I tested turning everything off (including X) and got it down to about 12Wh, but at that point the system is useless for web browsing. :)

If you are comfortable with command line stuff, try a tool called powertop.  It does a fairly good job of showing you what is consuming battery life.

My efforts to increase battery life yielded maybe an extra 30 minutes or so.  Not very much.  Apple has spent quite a bit of time making OS X work well on their hardware.

You have both an Intel GPU and ATI Radeon right?

Your high energy consumption is likely mainly due to having both GPUs running whereas OS-X switches between them and powers-off one when not used.

Turning off Radeon should get you down to 9W (my guess), but I don't know if methods I used would work in your case.

---

