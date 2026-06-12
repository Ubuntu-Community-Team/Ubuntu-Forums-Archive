---
title: "Company deployment - To Heron or Not To Heron?"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by tqprvn on 2008-03-02
hi all

So I am about to deploy Ubuntu company-wide very shortly.

My question, as a newbie to Ubuntu world, is whether I should deploy now, install 7.10 (which I have been using at work for a couple of months for testing, and has passed all tests quite admirably), or hold off a month or so for the forthcoming 8.04.

8.04 on paper has some cool new stuff, and obviously deployment day will be pretty much a productivity write off, so I would rather not do it twice (ie wheel the tech guys in to install 7.10 + whatever it needs, then wheel them back in a month later to do the upgrade), which has me leaning toward waiting an extra month before we go live.  

OTOH, being new to Ubuntu, I am not sure how reliable 8.04 will be at launchtime, and if my staff are going to be sitting there constantly installing patches and upgrades for the new system. In that case we are better to just install 7.10 right now, and hold off on the 8.04 upgrade til like June or July when it is pretty much stable and all the crinks have been ironed out.

So what do you guys think? Install 7.10 now as we know it works, is stable, and handles basically everything we can throw at it, then go to 8.xx in a few months; or just install 8.04 at launchtime and save ourselves a major upgrade in the near future?

Matt

---

### Post by Shazaam on 2008-03-02
As far as company wide deployment I would stick with the LTS (Long Term Support) releases.

---

### Post by Oldsoldier2003 on 2008-03-02
> **Shazaam said:**
> As far as company wide deployment I would stick with the LTS (Long Term Support) releases.
Agreed! A much better idea since hardy will have several patches right after it gets released, thats a certainty. Best to stick to a stable LTS release and upgrade to the next LTS when it becomes available

---

### Post by Whiffle on 2008-03-02
I'd hold off until Hardy, and then wait a bit after hardy comes out so you can see how well its running for people.  It'd suck to be down for a major bug that they might have missed.

---

### Post by keykero on 2008-03-02
Just wait the two months or whatever for Hardy.  I'm finding the latest alpha rather stable (at least as of this afternoon) and it's not sluggish like Gutsy is.

---

### Post by tqprvn on 2008-03-02
so the general consensus seems to be to hold off until Hardy launches, and then allow some buffer time....

ie. so if Hardy launches April 15, we should do the deployment around mid May, right?

---

### Post by Anduu on 2008-03-02
> **tqprvn said:**
> so the general consensus seems to be to hold off until Hardy launches, and then allow some buffer time....

ie. so if Hardy launches April 15, we should do the deployment around mid May, right?

I think the release is closer to the end of the month.

It would be wise to wait at least a couple of weeks after that to be sure no showstopping bugs get through.

---

### Post by jeffus_il on 2008-03-02
If 7.10 functionally satisfies you needs, why take a chance with the unknown?

---

### Post by Anduu on 2008-03-02
> **jeffus_il said:**
> If 7.10 functionally satisfies you needs, why take a chance with the unknown?

Well if you can't depend on the most recent LTS release to meets your needs its a sad day for Ubuntu.

Man all this upgrade talk has me itching again :p

---

### Post by jeffus_il on 2008-03-02
> **Anduu said:**
> Well if you can't depend on the most recent LTS release to meets your needs its a sad day for Ubuntu.

Man all this upgrade talk has me itching again :p
The most recent LTS is **Ubuntu 6.06,** Hardy is in the Alpha stage, not the right time to introduce it into a company where problems can boomerang on our poster, if there are tens or maybe hundreds of users, it may not be good for him and for Ubuntu in general. So if there is no need for extra functionality, why should he take the chance? I have great fun with Hardy on my desktop at home, but have to invest time on a regular basis, even the updates and changes are heavy in number and bandwidth, no I wouldn't chance it! Mistakes in this field have cost people there jobs, He has also spent months of his time testing gutsy. He knows what the status is.

---

### Post by Anduu on 2008-03-02
> **jeffus_il said:**
> The most recent LTS is **Ubuntu 6.06,** Hardy is in the Alpha stage, not the right time to introduce it into a company where problems can boomerang on our poster, if there are tens or maybe hundreds of users, it may not be good for him and for Ubuntu in general. So if there is no need for extra functionality, why should he take the chance? I have great fun with Hardy on my desktop at home, but have to invest time on a regular basis, even the updates and changes are heavy in number and bandwidth, no I wouldn't chance it! Mistakes in this field have cost people there jobs, He has also spent months of his time testing gutsy. He knows what the status is.

He specifically states he is waiting for Hardy to go LTS.He wants to know how long he should wait after that...

---

### Post by tqprvn on 2008-03-02
> **Anduu said:**
> He specifically states he is waiting for Hardy to go LTS.He wants to know how long he should wait after that...

I am actually pretty easygoing.  

The backstory to this is that I run a small company in Vietnam, and, as with basically all companies in VN, our software is all Of Questionable Legality.  The stores just preinstall whatever you want here at no extra charge.  The govt however is cracking down on such matters, and interestingly seems to be targeting foreign invested SMEs.  Basically a numbers game, we are an easy target, raiding us wont hurt the Battling Vietnamese Small Businessman (TM), and by hitting up as many of us as possible, the VN govt can go back to the WTO and declare that, having raided 300 companies with illegal software in the past X months, we are Serious About Piracy Issues.  Of course if they were actually serious, they would raid one local bank, find 5000 workstations with illegal software, and the net result would be far more impressive...but the banks have the connections...so I suspect I am in the firing line.

A couple of [cases]("http://vietnamnews.vnagency.com.vn/showarticle.php?num=04SOC151207") in [point.]("http://vietnamnews.vnagency.com.vn/showarticle.php?num=02SOC271007")

The punishment is pretty harsh too.  A fine of up to 3x the retail value of the software on the machines, seizure of the machines, which are returned only when you have purchased licenses for all the software on them.

Anyhow, looked into legalising, got told it would cost me something in the vicinity of 20k, which as an unbudgeted expense that I dont want to really fork out, hence the Ubuntu testing.

There are about 20 machines that will be done, including a file server, a 'backup box' (ie my old screen-dead laptop) and a bunch of workstations.  We will keep one machine on Windows for sanity-checking document formatting (OOo holds up ok for most things, but we occasionally need 'flawless') for client work, and for running the govt's tax reporting software (Win only).  I am looking around on eBay to try to find a good price on Office and Win 2k, as it is an older machine anyhow, and as I simply dont trust anyone here to sell me a 'real' copy...despite their insistence otherwise.  Always seems to be 'the other guy' that sells fake.  :)

I would rather make this a sooner-rather-than later thing, but I guess my biggest concern is downtime.  Install day will basically be a write off.  Upgrade day will likely be another write off.  For the most part Gutsy has served me well, and given the sooner rather than later feeling, and the sentiment upthread that it is going to be solidly 2 months before I should give the LTS Hardy a shot, I am leaning toward installing Gutsy company wide and waiting til mid year for an upgrade.  Sound reasonable?

Thanks all for the responses....

Matt

---

### Post by freebeer on 2008-03-02
Go with what your gut tells you.  If you've found that 7.10 is going to be reliable, then there's no reason to hold off.  That's what I did.  I'm running 7.10 in my small business as I wanted the goodness that is Ubuntu now.  I may upgrade later when 8.04 comes out, but not for several months after its release and I know it's stable.  (ie I'll be testing it in a non-production environment before I roll it out, and only then if I feel there's a gain to be had.)

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-03-02
do you have a high speed internet connection
if you do you can install now
and then upgrade 
upgrading will not be as much down time as you think it would be. Because you dont have to stop using ubuntu when it upgrades you just let it tell it too. Then go about your business. when its done you may have to do a restart. 

If you have a net work in you office. you may even want to host a local mirror for you computers to upgraded off of, so that you dont have to wait forever for all 20 computers to download the files LOTS OF BANDWITH wasted when there all geting the same thing. but  i have no idea how to do that last part

you like 7.10 I would install now.
then when 8.04 comes out you test it your self and see how it is.
then upgrade to it.

---

### Post by Oldsoldier2003 on 2008-03-02
> **tqprvn said:**
> I am actually pretty easygoing.  

The backstory to this is that I run a small company in Vietnam, and, as with basically all companies in VN, our software is all Of Questionable Legality.  The stores just preinstall whatever you want here at no extra charge.  The govt however is cracking down on such matters, and interestingly seems to be targeting foreign invested SMEs.  Basically a numbers game, we are an easy target, raiding us wont hurt the Battling Vietnamese Small Businessman (TM), and by hitting up as many of us as possible, the VN govt can go back to the WTO and declare that, having raided 300 companies with illegal software in the past X months, we are Serious About Piracy Issues.  Of course if they were actually serious, they would raid one local bank, find 5000 workstations with illegal software, and the net result would be far more impressive...but the banks have the connections...so I suspect I am in the firing line.

A couple of [cases]("http://vietnamnews.vnagency.com.vn/showarticle.php?num=04SOC151207") in [point.]("http://vietnamnews.vnagency.com.vn/showarticle.php?num=02SOC271007")

The punishment is pretty harsh too.  A fine of up to 3x the retail value of the software on the machines, seizure of the machines, which are returned only when you have purchased licenses for all the software on them.

Anyhow, looked into legalising, got told it would cost me something in the vicinity of 20k, which as an unbudgeted expense that I dont want to really fork out, hence the Ubuntu testing.

There are about 20 machines that will be done, including a file server, a 'backup box' (ie my old screen-dead laptop) and a bunch of workstations.  We will keep one machine on Windows for sanity-checking document formatting (OOo holds up ok for most things, but we occasionally need 'flawless') for client work, and for running the govt's tax reporting software (Win only).  I am looking around on eBay to try to find a good price on Office and Win 2k, as it is an older machine anyhow, and as I simply dont trust anyone here to sell me a 'real' copy...despite their insistence otherwise.  Always seems to be 'the other guy' that sells fake.  :)

I would rather make this a sooner-rather-than later thing, but I guess my biggest concern is downtime.  Install day will basically be a write off.  Upgrade day will likely be another write off.  For the most part Gutsy has served me well, and given the sooner rather than later feeling, and the sentiment upthread that it is going to be solidly 2 months before I should give the LTS Hardy a shot, I am leaning toward installing Gutsy company wide and waiting til mid year for an upgrade.  Sound reasonable?

Thanks all for the responses....

Matt
That sounds completely reasonable and a prudent plan. Honestly I don't know where the realism comes in when people expect hardy to be flawless on release- hell the "other" OS has a huge staff of highly paid programmers and can't still cant release an os on time or that isn't need of patches. Giving Hardy a few months to get out of its initial growing pains before upgrading is a good idea.

---

### Post by tqprvn on 2008-03-13
deployment day.

gulp.

wish me luck!

---

### Post by Hendrixski on 2008-03-13
> **tqprvn said:**
> deployment day.

gulp.

wish me luck!

GOOD LUCK!

Like a few of us said, it's probably prudent to upgrade to Heron when it comes out, and then stay on that because it is a long-term-support release.  You'll be able to get support on it for a few years, whereas normal releases only stay supported for a year and a half.

We set up Feisty in our company when it came out, and we're still on it, but we'll be switching to Heron when it comes out. and then sticking with that.

---

### Post by sloggerkhan on 2008-03-13
You should be able to avoid downtime for employees by running the upgrade as a distributed install over the network at night. I don't know the details of this, but I think clonezilla is the sort of thing that's used.

---

### Post by Sef on 2008-03-13
Here is the [Clonezilla]("http://clonezilla.sourceforge.net/") site.

---

### Post by sports fan Matt on 2008-03-13
i tried herron..for about 15 mins..seems like the lib6 for herron was brokwn and it hosed my machine so i will wait

---

