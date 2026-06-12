---
title: "Help with Employer"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by PhillD on 2007-03-23
Hi everyone,

This is probably not an average Linux question, or for the most part, hardly a Linux question at all, but please keep reading because I do need some advice.

I work for a medium sized oil & gas related company in Texas, USA.  I have worked here for approximately 5 months and have ended up questioning my move here.  I was employed, for the most part, to aid in a massive data migration to a new system that the company had purchased.  This was to be accomplished through my skills as a programmer and I was tasked with automating as much of the migration process as possible. Hence to say I was hired as a programmer but also for my computer tech skills when needed.

My manager has worked here for 3 years and has, what I would call an extremely lapse approach to IT.  To quote &#8220;I want you to find the quickest solution possible to every problem&#8221;.  Typical manager talk which some of you may not think is a bad thing.  However, I hope that as Linux users, I am addressing people who are generally more organized and like to do things properly when they do them.  This may not be the case but from what I have learnt from Linux, this principle is at it&#8217;s very core.  Anyway, moving on&#8230;&#8230;.

3 years of my managers running this company's IT has, in my opinion, left a really big mess in every aspect of I.T.  The wiring in this place is nothing short of &#8220;inventive&#8221;, when asked by our CFO why the wiring couldn&#8217;t be replaced, my manager said it was because he couldn&#8217;t distinguish between phone and data lines &#8211; so no color coding here then!.  The 2 sever rooms we have are a mess (there is no particular reason to have 2 server rooms other than the new one is in my managers closet & closer to him!)  It is an absolute jumble of wires, rack mounts not in racks, PC&#8217;s just located where it was convenient to put them.  It even has a patch panel (for when my manager can actually be bothered to patch wires instead of connecting directly into the hubs).  The file structures on the servers are an absolute nightmare, files are just dumped anywhere where it is convenient, for example, the folder we setup to hold information relative to the data migration is now filled with letters, word docs drivers, programs, reports all kinds of stuff not relating to the data migration.  The average spec PC is very out dated, shop floor = P2 450 MHZ with 128 Mb Ram Windows 95/98.  Office workers have Dell Dimension 2400&#8217;s with XP (never updated of course and in many cases no virus or spyware protection).  We do have some newer PC&#8217;s but these are reserved for the 2 IT staff and random office workers.  We have some users on the domain using exchange, others not on the domain with exchange, others not on the domain with pop3.  Our internal ip address begins 132.147.160 what is that about?  The approach to software licensing here is also what I would consider a joke, comments like &#8220;oh, those machines have a dell tag and dell would have the license number on file for the OS&#8221; are comments used every day and we all know that stuff won&#8217;t fly with an auditor.  We reuse keys over and over again, even use pirated software in our business (and lots of it, especially Office 2003).  It appears the only consistent thing in this business when it comes to I.T. is that things are done inconsistently.

Since I started employment I have created a system to keep track of PC&#8217;s and licensing, but my manager won&#8217;t use it.  I spent several weeks turning our computer lab into a computer lab so we actually have a space to build and work on PC&#8217;s.  I am trying my best to turn things around but I can&#8217;t win.  When ever I raise a comment about the mess things are in, all I hear is that &#8220;It works&#8221;.  I can&#8217;t tell you how many times I have heard that!  Also &#8220;If it ain&#8217;t broke, don&#8217;t fix it&#8221;.  My manager is also the kind of guy who knows everything and is never in the wrong (typical manager), granted he knows some things but he knew very little about the work I have done in Linux recently but still claims to the CFO that he knows the solution to the problems I&#8217;ve been having.  He is one of these guys who talks a good talk, but really he often uses technical words to confuse people into thinking he knows what he&#8217;s talking about.  So I guess I&#8217;m starting to paint a picture of what our business is like.

Things came to a head a few months ago when a really big screw up occurred with the new system.  It was my managers responsibility to oversee the project and ensure that the new system did everything it needed to do.  Due to his usual approach &#8220;minimum effort possible&#8221;, things were not done thoroughly and it was discovered that the system did not do the method of costing that it needed to do.  We ended up having to return the system for a partial refund.  It looked as though my manager would be fired, but he wasn&#8217;t.  Then it looked like he was leaving but he didn&#8217;t.  I was in prime position to take over his role and sort this company out.  But that never came to be.

So here we are, a few more months down the line and looking at more new systems (this is where Linux comes in).  During software analysis, we discovered that the outlying stores would have to be connected via terminal services/remote desktop as 1. there was too much data to be sent over the frame relay, and 2, the PC&#8217;s were not powerful enough to run XP and the new software.  Once the idea of terminal services settled in, my manager saw a golden opportunity, if we could use terminal services for everyone &#8220;I&#8217;ll never have to leave my desk again&#8221;.  Very convenient for a guy who spends the majority of his day playing EVE online.  The CFO also contributed &#8220;What about Linux&#8221;.  Naturally knowing a little about Linux, I voiced my concern about hardware/driver compatibility and the overhead with setting up Linux.  (Sorry guy&#8217;s, I just don&#8217;t think its as easy as windows to install hardware)&#8230;..Also the learning curve for employee&#8217;s would be massive.  After some discussion, the decision was made by the CFO to use Linux as a dumb terminal for windows by using a terminal services client (I hear the screams now from the Linux crowd, just know this was not my decision).  Anyway, for my contributions, I got tasked with learning Linux and setting it up as a windows terminal, my manager would also purchase a touch screen monitor (which our business wants to start using).  In his usual fashion (minimum effort possible), my manager did not check if the touch screen was Linux compatible and surprise surprise, when the monitor arrived it did not have a Linux driver, nor was one available from the manufacturer.  Finally after some searching, he found a driver which was 4 years old and was designed for the XFree86 x server.  Well all the newer versions of Linux run on Xorg.  Despite 2 weeks of trying to get the driver to work I finally just told my manager that he should look at it because he wouldn&#8217;t believe me that It wouldn&#8217;t work.  After 5 minutes of him looking he, couldn&#8217;t be bothered to work on it and agreed that it was not going to work.  At the same time I got a lecture how I shouldn&#8217;t come to him with problems, I should bring him solutions.  I said that the only solution I saw was to get a new monitor, one that would work with Linux.  Of course this was the wrong answer and his solution is to load an old version of Linux (suse version 9) that does run under Xfree86.  Despite trying to explain that this is against the very ethos of Linux, both the CFO and IT manager agreed this is the way forward.

So here we are again, about to create another mess.  We also have some brand new Dells (Dimension E520) that we were using to test Linux (and will eventually be rolled out to the end users)  I already have a good hunch that suse 9 will not load on them as an older version of suse 10 didn&#8217;t load either.  Of course, this is just me making presumptions and having opinions again (according to upper management) and we should wait and see until we get the suse 9 cd before we decide if it will load or not.  At this point I was very frustrated and explained that we are changing an operating system to troubleshoot a problem, and this is not the way to do things.  I was then asked why?  I explained that you can&#8217;t change an operating system every time that you have a problem because you would never have a consistent OS and considering that we still need to load a wireless card, I expect more problems to come up.  Despite the fact that my manager knows what I am saying makes sense, he won&#8217;t back me up because then it would be his screw up and the monitor would be useless.  I was then asked what would be wrong with running different versions of Linux, 1 for newer PC&#8217;s and 1 for older PC&#8217;s, I said nothing except that it makes the Linux even harder to manage and twice to potential for things not to work.  Obviously again, this was seen as me just being anti Linux which I am not.  It&#8217;s just that the experience I have had with Linux has not been a positive one so far.

So can any one see why I question my move to this company, they are not willing to see sense.  Obviously I didn&#8217;t have to post all this extra information about my company, but I wanted to demonstrate that decisions are not made poorly due to lack of knowledge, but due to a lack of willing to do things correctly.  So I guess the question now is why did I post?  Partly to vent? Yes, partly for sympathy? definitely but mainly to get opinions and good reasons why we should not go with an old version of Linux (I read somewhere that you shouldn&#8217;t use an old version of Linux).  I&#8217;ve also tried to explain that in buying into the Linux OS, there is a certain ethos or code of conduct which one should follow, but that doesn&#8217;t even register with management.  So thank you for reading this and hopefully I can get some help.

Thanks Again.

PhillD

P.S. I did post messages on the forum about the touch screen but no one was able to help, just thought I&#8217;d mention it before you thought to suggest it.

---

### Post by PhillD on 2007-03-23
Come on guy's I really need help with this.  I know if someone deosn't post, it will get lost in the void that is the next page.

---

### Post by eljalill on 2007-03-23
Oops, that's a threat!
What you write does not seem pretty I have to admit.

Well, I can't give you feedback on the technical side, except, that you might not be able to get support for older versions of any distro (which is pretty basic, I know.. ;) ).

But from what you write I am wondering what good technical support and advice will do you at all. If people at your employer's don't listen to reason, then why should they listen if you come with more/new arguments?

---

### Post by Zzl1xndd on 2007-03-23
I can feel your pain. The company I work for use Citrix terminals that are Emulating windows so its as to make it easy for people to use but the best part is it also runs a Unix emulator for our inventory system. Nice eh?

Really the point is that companies often do things in a backwards way because it cost them less right now and that gets the people like your manager promoted and the next guy probably you blamed for the mess. 

I Agree with your methods of doing things as I say it everyday "if its worth doing, Its worth doing right." Also speaking as some one that has done a great number of Linux installs Desktop Linux installs it can be as easy or more so. For me its broken about 50/50.

---

### Post by PhillD on 2007-03-23
Thats a good point, I guess in a sense I have blown my own argument for needing help, but I have to try something.  Usually If I can come up with something relating to money, additional costs in time/labor I can get the CFO to listen.  Thats why we are going with Linux, purse and simple reason - it's free.  It's all about the money

---

### Post by adam.tropics on 2007-03-23
Wow. What a mess! 

I am sorry to hear of your current woes, and in all honesty am not surprised your questioning your move to such a company. I am wondering how you see your future in that position? If it were me, I think I would be looking at doing whatever is required to get a decent reference, and quietly finding myself another job. Quickly. The thing you're gonna come up against pretty soon by the sound of it, is that if migration goes well, then your boss will get the credit, his job will be safe, and your chance of promotion will be gone. If on the other hand it all goes pear shaped, which I guess is entirely possible, then if you still have a job after taking the rap for your boss's mis-management, your chance for career progression with that company will still have gone, only at that point it may have longer lasting effects.

Sorry if that all sounds negative, but at some point, you need to consider the notion of self preservation! 

If you decide to stick it out however, be assured that the Linux community really is a vast resource, and is freely available to you. Also, you might want to point out to your boss that there is [paid support]("http://www.ubuntu.com/support/paid") available too! Though he may wonder why he needs you at all if you do!!

As for the touch screens, I have [read]("http://www.nautilus6.org/doc/tc-vaio-linux-bsd-20041221-KuntzR.txt"), though I haven't got one, (fed-ex it if you get bored!!) that they would want the evdev driver which is a standard Xorg driver. If you had problems with it at all, I would expect them to be with using wireless mouse at the same time.

---

### Post by justleen on 2007-03-23
Phill, You definitly have my sympaties!

Now, keep in mind that im definitly not an expert, by hope to inspire other readers (whats this guys, cant handle more then 10 line or what?) to post a reply
As to solid argument for not running an old version of linux... I;d say go with the security argument. The older version have more vurnabilties, which are fixed in the new ones. 
Offcourse, there a work around to that: upgrading an old version.. but you risk breaking your working old system if the upgrade has to fill to big a gap.. 
Plus, why bother with upgrading suse 9, if you can install 10.2?

another thing i would definutly keep mentioning to your "upper" managment is dhardware support. There is really no reason to have one touch screen working to find that loads of other hardware is not working! 
Yes, you could probably update everything to get stuff to work.. but again, what would be the point in that?


If they are manager, they must be vurnable to argument like "it will cost me more time to get the old version working, hence our project will be delayed and hence it will cost more money" ?
(money is _always_the way to convert them to your cause! the trick is to bend your argument to a cost/benefit question).

so.. i'd say you got security, compatabilty and time (=costs) as an argument..

I hope this helps you in your struggle!

good luck!

---

### Post by Zzl1xndd on 2007-03-23
Gotta agree to bring them over you are gonna have to point out the cost and that is going to be the big thing here. You might wanna ask where this ends I mean if they by more hardware without looking into if it works or not are you gonna have to learn to trouble shoot RedHat as well to solve the problem?

---

### Post by kgun2k1 on 2007-03-23
I would try to document all your suggestions in detail.  Instead of telling your manager or CFO why they should do something, email it to them.  Then when the eesh hits the fan, you have a nice paper trail of you warning them.

Also try to support your arguments as much as you can by means of money.  Compare cost now to costs later.  It is a huge pain and it is a bit of work, but it helps for people that only look at $$$.

Use resources such as this forum to back you up in arguments too.

---

### Post by PhillD on 2007-03-23
Oh trust me, if the data migration goes well, I'll be the one doing most of the work, my manager really doesn't have much of a clue other than, take data from one system and put it on another........I'll be taking care of the 'conversion' and I will be getting the credit for it.  Espcecially during the last data migration (for the system that didn't work out), I was automating processes that my manager insisted would have to be manual input by the users.... I got a lot of credit for the programming work I did during those few months and hopefully I'll be in a position to start working on the new data migration soon.

---

### Post by PhillD on 2007-03-23
Just wanted to make a quick note to say thanks and I guess I'm not going insane.  It's good to know that I am thinking along the right lines.

---

### Post by daxumaming on 2007-03-23
PhillD, I feel you man! I feel you!
Your manager shouldn't be in that position in the first place. Document everything that you've done for the company and make sure your Boss's Boss gets a copy.

As for your question:
1) Security
2) Delays
3) Money
It always is all about money!

Goodluck and get your well-deserved promotion.

---

### Post by PhillD on 2007-03-23
Thanks for that!

Phill

---

### Post by wpshooter on 2007-03-23
PhillD:

Here is some advice for you.

Get the *$@+#$), out of there.

When, (not if) the *@($ hits the fan, I'll give you one guess as to who is going to get the blame. 

And don't guess the IT manager (your boss).

Keep looking until you find a shop that has a better appreciation of how IT matters should be handled.

Good luck.

---

### Post by Zzl1xndd on 2007-03-23
> **wpshooter said:**
> PhillD:

Here is some advise for you.

Get the *$@+#$), out of there.

When, (not if) the *@($ hits the fan, I'll give you one guess as to who is going to get the blame. 

And don't guess the IT manager (your boss).

Keep looking until you find a shop that has a better appreciation of how IT matters should be handled.

Good luck.

This is some good advice, The tech sector tends to work this way. It's always the front line guys that take the brunt of the problems. I mean I'm just a tech in a retail store but no matter if its HP, Sony, Toshiba or our own service Depot that mess stuff up im the one that takes the Heat from the management and the customer.

---

### Post by PhillD on 2007-03-23
Thanks for the advice guy's, I'm taking it all on board.  I came up with an idea late this afternoon which may be able to allow us to continue to use ubuntu, I just got to put serial cards in the new PC's.

On another note, the Old PC's (Dell Optiplex GX1) are supposed to work on Ubuntu but so far we haven't been able to get them to fully work on any build of linux.  It appears that it cannot mount the CD drive or aceess the serial ports.  We thought ubuntu was working on the GX1's but I guess it's not.

If it's not one thing, its another.

Phill

---

### Post by Chopperman on 2007-03-23
Variation on a theme - 

I'm a linux/ubuntu noob, so I cant offer much there. But I have worked in the corporate IT biz for over a decade and I have plenty of experience with similar situations. 

First, your boss needs managing. All bosses need managing. The most valuable skill you can learn is managing your boss. Figure out what motivates him and how to get him to do what *you* need him to do. There are plenty of good essays on the subject on the net. The best lesson I learned - If at all possible, present something in a way in which he sees a win. Put a positive spin rather than a negative one on what you are trying to do, no matter how much of a toolbox you think he is. He is a programming problem, you just have to figure out how that undocumented API works :) 

Second, document *everything*. Times, Dates, Places, who said what. And if at all possible communicate in writing, email, etc. Even if it is just an email summarizing a hallway conversation. There is a very good reason that businesses conduct performance reviews and other HR related issues take place on paper. This will serve you in two ways: one, it becomes very difficult for someone to change the story if it is there to be dredged up again. two, it will help to refresh your memory months later if the issue arises again and you need to have a good recollection of what happened. 

Third, before you go making footprints on your immediate boss's scalp on your way to the head honchos office, give him every chance to properly deal with the situation (and document the effort). That way it becomes difficult to paint you as a troublemaker.

Fourth, legal, security and money issues are big motivators in this environment. It is often hard for an IT geek (like myself) to grasp those tools and to use them. 

So what I would do in this situation is rather than bailing out or bailing a leaky boat with temporary fixes, I would take on as a private side project documenting all the issues with the infrastructure and processes and then figure out the potential cost to: 1) continue without changing 2)update and repair each infrastructure and process and then I would associate a cost for each potential disastrous result in terms of time, effort, legal consequences and cash. 

Examples - 

You mentioned the wiring in a situation where you cannot discern the phone infrastructure from the data infrastructure. What would it cost to fix that? What would be the cost to the business if say one of those data lines malfunctioned and you couldnt readily identify it? 

You noted that licensing of major software components is slim to not at all. What would be the consequence in terms of financial, effort and legal if one disgruntled employee blew the whistle to the SBA? 

You detailed how many of these systems are older windows systems that remain unpatched or monitored for common issues. Detail the costs of updating/upgrading/policy establishment versus the cost of having Slammer or some other malware halt the entire network for a week. 

Put all of that into terms a businessman can understand - Dollars, lawyers and newspapers. But not in a threatening or squeaking wheel way. Play canary in the coal mine. Describe how you bring this up as a potential exposure for the company because you care and that if you didnt care you would just do the job and collect the check. Detail a proposed plan of action and timeline for bringing the IT infrastructure up to standards. Address every past excuse your boss has used in the past in an indirect fashion. 

If your boss ignores that, then take it up the chain of command. If your boss starts making things difficult for you and you dont get any backup from above; well you didnt want to be there when the SBA comes in with marshals/the feds come in with a SOX beef/it hits the news that someone nabbed several thousand customer records or it gets discovered someone is running a porn/warez ftp server on your network....did you? (holy run-on sentence batman)

Outcomes:

1) you get handed a pink slip. Keep your job contacts warmed up. I always do. 
2) Boss sees the error of his ways and becomes an angel (unlikely)
3) Boss sees you as trouble and sticks you with an impossible project to set you up for failure
4) Boss ignores you. But honchos wig flips and you get an audience with the headman (the first question always asked is "Well what should we do about this?" which you have already answered and are prepared to elaborate on) then you get a chance to fix one, some or all of the things. 
5) Boss ignores you, Honcho ignores you - see outcome 1. 

Of course do nothing, keep the resume warm is always an option :) 

Just my bucket of words. YMMV, IANAL, etc etc.

---

### Post by daxumaming on 2007-03-26
<applause> Standing Ovation for Chopperman.... </applause>
Now that's the way to handle this kind of situations!

---

### Post by PhillD on 2007-03-26
Hey,

Thanks for that.  I really appreciate everyone’s comments on this problem.....I guess I will post a little update for you all as well.

The idea I had with the touch screen monitor (after much tinkering) actually worked!  I decided to load up ubuntu on another machine (one with a serial port) and try to configure it for a serial connection.  It didn't work, even though I was convinced it should (hey I may actually be learning about Linux).  I decided that I'd test the monitor on a Windows machine to rule out hardware failure.....Guess what, It didn't work either!.......By this time it was 5:00 and after trying a few things I gave up for the week.....

I came back Monday extremely tired after 2 hours sleep (wife in ER type situation, but she's ok now).  I tried the monitor again, still no joy.........I sat there and stared at it, and thought about how tired I was and how tired I was of this project, and then I wondered, is the monitor tired as well?  Does it need a little nap and a reset too?  I turned the monitor off and on again and I couldn’t believe it.....the touch screen was working (in Windows).  

As I was convinced it should have been working in Linux, I decided to swap it over and try it and..............................................................................................................................................................................................................................................................

IT WORKED:) 

So now we don't have to go to an old version of SuSe (or do we?).....Now I have to figure out how to calibrate the monitor because it’s off by quite a lot!  The calibration utility that comes with the driver is written for XFree86 and won’t load on Xorg.

I'm not going to go into the details of the problem with calibration here because I'm going to start a new post, but when I get it set up I will put a link here.

Thanks again for all your comments and suggestions, I have listened to everything you have said and I have taken note!

PhillD

---

### Post by PhillD on 2007-03-26
Hi All,

After messing around with the xorg file and any kind of configuration script, I have run out of ideas and made a new post about the touch screen located here [http://www.ubuntuforums.org/showthread.php?t=394218](http://www.ubuntuforums.org/showthread.php?t=394218)

PhillD

---

### Post by H.E. Pennypacker on 2007-05-23
With all due respect PhilD, the way you talk about Linux demonstrates that you lack firm understanding of how different distributions work.  You talk about Linux in a way that suggests if one distribution does not work, another will not either.  You do not say this explicitly, but you say from your experience, Linux use has been somewhat unpleasant.  You have not, however, made a distinction between which distributions have been troublesome, and which ones have worked just fine.

It amazes me, and this is one of the things that I dislike about Linux, is that one distribution can work entirely different from another.  Now, I am not talking about something like the desktop environment.  I am talking real hardware support.  It is amazing how one may have trouble installing Ubuntu, but will be completely at ease with, say, Mepis.  The issue here is that gaining experience with one distribution does not at all say anything about how another distribution will work.  They are, albeit based on the same kernel, entirely different in many ways, including how they operate.

Having said this, I wanted to say your workplace is terrible, but you already know that.  Despite the financial woes they could lead themselves to if the SBA knew what they were doing, they also have to employ inefficient people like your manager (inefficiency is not his only problem).  Having things (wires, servers, etc.) organized is not purely for looks.  It actually affects how you work, and you guys could actually save money (by, for example, not having to waste time looking for something when you know where it is) through organizing properly.  
Also, it appears you guys don't really do homework.  As you said yourself, your manager did not look things up before buying the touch screen.  It is a good idea to sit down, figure out which distribution works the best, and pick hardware accordingly.  See which one has the best business support, and possibly, which one is most tailored to the type of work you do.  It is possible, for example, that there is a distribution which specializes in touch screens.

If Ballmer said developers are important, homework is an understatement.

---

### Post by blackspyder on 2007-05-24
Welcome to my life... well in a sense. The programs we use in the shop (Cumins InSite 07 and TMT) take up so much system resources that when combined with a 2 year old computer (read: 1.5 GHz Athlon Xp processors and 256 MB RAM) well lets just say I have plenty of time to drink a few cold ones and sober up again while waiting and I have been harassing our Techie (no he doesn't mind the title I gave him we actually laugh about it Techie vs Grease monkey) to switch to  a lighter OS (Xubuntu or Win 98 since Win 98 worked well before our old PC took a crap). Oh yeah and if you think your wiring is fun you should come see ours all white wire + 2 companies + 4 routers {our company alone} and 1/2 of the lines go no where [you start with 4 lines in the office  then up to 8 lines in the parking lot and then down to 2 lines in the shop].

Thank God i just fix the trailers not fix the PC's (oh yeah on saturday I use my Laptop with a less then legal version of the software too speed up the process...my laptop is a C600 Dell Latitude.. need I say more)

---

### Post by psyopper on 2007-05-24
Two questions:

0. Is this a publicly traded oil company?
1. Have you condiered a career change? I hear police work pays well...

Sorry, couldn't resist. I'm a 10 year veteran of the tech industry, I know your story well. You have my sympathy. 

As far as offering ideas - persistence is the key to solving something with Linux. As for the monitor - I once had a teacher that insisted "Data is data, the computer doesn't care what OS wrote it or what application is reading it, it's still a bunch of 0's and 1's that need to go in a particular order to make a specific thing happen" This is wisdom of the ages if you ask me. Figure out how the 0's and 1's line up and you can make things happen on any computer and in any OS, including Linux.

---

### Post by eentonig on 2007-05-24
There's only one sain thing you can do over there. Look for another job.

Hell, even if you do manage to get "EVE online"-boss out of the company and you in his seat. The other management doesn't seem to be more competent. You'll spent a lot of time and effort in something that will be thrown back in to your face.

---

### Post by wormser on 2007-05-24
> **eentonig said:**
> There's only one sain thing you can do over there. Look for another job.

Hell, even if you do manage to get "EVE online"-boss out of the company and you in his seat. The other management doesn't seem to be more competent. You'll spent a lot of time and effort in something that will be thrown back in to your face.

I 2nd it.  Obviously you are not happy in your current situation.  There are plenty of IT jobs out there and you have some good experience.

Look for a new job, give your 2 weeks and move on.

I worked for an IT company that makes your look good.  We developed software but had no software testers!!!  It was a tech support nightmare.  To make it worse they would push back bug fixes for months.  One customer sent us a list of 50 bugs they found.  Management said they would just fix the 7 major ones.  The customer was not happy about that.  Everybody was afraid to pick up the phone including sales because most of the calls were bad.  The funny thing is that they are still in business.  My lesson to everybody is test the products thoroughly before you buy.  BTW, I was not there long.

---

### Post by darkworld on 2007-05-24
If you are not prepared to leave then try this. Agree with your boss on almost everything, try to do what he wants. Always underline that you are working on an idea the boss gave you. ;)

Trying to do the impossible will be a challenge and you may learn much from this. Use the impossible situation to build your skills then leave and become a consultant for companies that are in this kind of mess. 

Its about ticking all the right boxes, where your boss is concerned. But what you are really doing is building up your skills whilst getting paid.

Your company and management will never change so just use them.

---

### Post by davarino on 2007-05-24
darkworld has the answer!

Either quit or use the situation as an education. And hang on for the ride of your life.

Quitting is quite normal, using darkworld's advice is quite "above normal".

Good luck

---

### Post by Cadoret on 2007-07-30
I'm not qualified to comment on the tech side of this (just moving from Windoze to Linux), but re your job situation, I would agree with other posts; look for another job & move on ASAP. You seem to have a good work ethic, and bad bosses very often take advantage of this - I speak from bitter experience!

I would also agree with one of the above posts - if you can stomach it, agree with everything your boss says, do what he asks for as well as you can, BUT don't make it too obvious that your attitude has changed while you look for another job. Also get everything in writing one way or another, document all your verbal discussions and actions in a diary, and store a copy offsite - bad bosses also generally buy into some form of blame culture!!

Good luck - and remember work to live, not the other way round :-)

good luck

---

