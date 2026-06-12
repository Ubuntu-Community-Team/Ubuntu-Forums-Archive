---
title: "Excruciattingly slow"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by jackmccaskill on 2007-12-07
Greetings,

	I have downloaded and installed the ubuntu 7.10 operating system.  It works, however it is excruciatingly slow..  It was down loaded to a Toshiba lap top, which is somewhat &#8220;long in the tooth&#8221; but has a 20 GB  hard disk and 512k of memory.  When I installed, I chose to partition the entire disk [selection 2]

	Perhaps my expectations are way too high but I did expect much faster response times. I am connected to the net with DSL.

	When I said excruciatingly slow this is what I mean:
		Power up to first appearance of the ubuntu logo = 5 minutes
		logo to log in Screen = 3 minutes
		login screen to Firefox = 3 minutes
		Firefox to yahoo mail =2 minutes 
		Total from power up to checking mail = 13 minutes!

	Surely this can not be right!

	Any suggestions, tips, corrective actions or explanations will be very much appreciated

	A secondary but important concern is how do I find this posting and any replies there to once I submit it?

---

### Post by rsambuca on 2007-12-07
> **jackmccaskill said:**
> Greetings,

	I have downloaded and installed the ubuntu 7.10 operating system.  It works, however it is excruciatingly slow..  It was down loaded to a Toshiba lap top, which is somewhat “long in the tooth” but has a 20 GB  hard disk and 512k of memory.  When I installed, I chose to partition the entire disk [selection 2]

	Perhaps my expectations are way too high but I did expect much faster response times. I am connected to the net with DSL.

	When I said excruciatingly slow this is what I mean:
		Power up to first appearance of the ubuntu logo = 5 minutes
		logo to log in Screen = 3 minutes
		login screen to Firefox = 3 minutes
		Firefox to yahoo mail =2 minutes 
		Total from power up to checking mail = 13 minutes!

	Surely this can not be right!

	Any suggestions, tips, corrective actions or explanations will be very much appreciated

	A secondary but important concern is how do I find this posting and any replies there to once I submit it?
There is definitely something wrong with your setup!  Can you post your computer specs?

---

### Post by sports fan Matt on 2007-12-07
Hi,

What I would do is in Firefox when next you have it open, I would go to "Bookmarks", then "Bookmark this page" and also bookmark under the "absiolute beginner section" to check and see for replies--note you may need to get through many pages on the bottom right hand side to find you question...

I agree--13 minutes is an insanely long time so once we get your computer specs someone will be able to assist further

---

### Post by DJiNN on 2007-12-07
> **jackmccaskill said:**
> Greetings,

    I have downloaded and installed the ubuntu 7.10 operating system.  It works, however it is excruciatingly slow..  It was down loaded to a Toshiba lap top, which is somewhat “long in the tooth” but has a 20 GB  hard disk and 512k of memory.  When I installed, I chose to partition the entire disk [selection 2]

Depending upon what CPU it has in it, it shouldn't be too bad. Is it PIII or P4? If it's a PIII then perhaps you'd be better off with a "Lighter" distro. 

>     Perhaps my expectations are way too high but I did expect much faster response times. I am connected to the net with DSL. 

Without knowing what CPU you're using it's hard to tell, but it doesn't sound like it. I would have thought, even on a somewhat old PIII, that it would have run a little faster than that. :)

>     When I said excruciatingly slow this is what I mean:
        Power up to first appearance of the ubuntu logo = 5 minutes
        logo to log in Screen = 3 minutes
        login screen to Firefox = 3 minutes
        Firefox to yahoo mail =2 minutes 
        Total from power up to checking mail = 13 minutes!



OUCH!! That's totally unacceptable! :) It could be that your UDMA settings of your Hard Drive are not "ON"..... that would certainly cause it to be slower for sure. 

>     Surely this can not be right!

    Any suggestions, tips, corrective actions or explanations will be very much appreciated 

Not really much i can say without knowing a little more, but what i would do is perhaps try another distro to see if the same thing happens. Xubuntu should work well, or something similar.  By trying a few distros you can at least get an idea if the problem's the same "Across" the distros, or if it's just Ubuntu that's the problem.  

Personally i wouldn't run Gnome on a PIII, and even on a P4 i would run either a cut down Gnome (Using OpenBox as a Window Manager) or preferably one of the XFCE distros (ie: Xubuntu etc)  Linux Mint has a really good XFCE version that may be worth trying, and if you're after some speed out of the laptop, then installing something like antiX could be worthwhile.

>     A secondary but important concern is how do I find this posting and any replies there to once I submit it?

I still have that problem with that, even now, and i've been here a few years. :)  I usually just either subscribe to the particular thread (under "Thread Tools") or just search for my posts and pick the ones that i am after. If there's a better way then i haven't found it yet. 

Let me know how it goes & what you decide to do, but i'm sure that you'll get it sorted out. The help on these forums is "Second to None!" :)

DJiNN

---

### Post by oldos2er on 2007-12-07
Please post your hardware details.

 To find threads, click Search, Find All Your Threads.

---

### Post by crosspicker on 2007-12-07
A secondary but important concern is how do I find this posting and any replies there to once I submit it?[/QUOTE]


Even though I'm a total NOOB the easiest way I've found to look up your posts and threads is in the search, click the arrow and in the drop down click either view your posts or view all your threads.

---

### Post by ryanVickers on 2007-12-07
well, first of all, if you only have 512k of memory, it might be a good idea to add some more until you have at least 256Mb lol - this could be why it's slow, it's using the swap for everything... :p

---

### Post by jackmccaskill on 2007-12-07
On the Toshiba lap top the only specifications I could find where from the “Dis Usage Analyzer as follows;

	file system capacity 17.5 GB
	Used; 2.0 GB
	Available : 15.5 GB

Previously, on Windows I used a program called Belarc adviser which listed all specifications, it will not, however, run on ubuntu and since I partitioned the entire disk for ubuntu I am somewhat at a loss as how to proceed.  Is there a ubuntu accessory that will list the processor, ram and whatever information you need to help me?

Someone used the term distros.  I have no clue as to what that refers to

---

### Post by DJiNN on 2007-12-07
> **ryanVickers said:**
> well, first of all, if you only have 512k of memory, it might be a good idea to add some more until you have at least 256Mb lol - this could be why it's slow, it's using the swap for everything... :p

LOL!!! I "Totally" missed that..... Well spotted! :-D

---

### Post by lswest on 2007-12-07
distros=short for distributions, or different versions of Linux.

To find out your CPU and RAM you can go to system --> administration --> system monitor and under the tab "System" is info about your computer.

for exact info about the cpu try running
```
acpi -V
```
in the terminal

---

### Post by jackmccaskill on 2007-12-07
Thanks, of course I made a mistake.  I have 512MB of RAM

---

### Post by DJiNN on 2007-12-07
> **jackmccaskill said:**
> Is there a ubuntu accessory that will list the processor, ram and whatever information you need to help me?

There probably is, but i'm afraid i'm not the person to tell you that as i don't know what it is. :)  Well done for finding the thread again though... :)

> Someone used the term distros.  I have no clue as to what that refers to

"Distros" is short for "Distributions"..... For example, Ubuntu is one Distribution, which also has several "Flavours" or "Sub-Distributions" if you like, one of those being "Xubuntu". There's also (in no particular order) Kubuntu, Edubuntu, Fluxbuntu etc etc, all offering various different things depending upon what you're looking for.  

Go take a look at [http://www.distrowatch.com]("http://www.distrowatch.com/") & you'll see literally Hundreds of different Distros available. :)

I'm sure that someone here will give you a way to find out what hardware you're running.

---

### Post by lswest on 2007-12-07
lol DJiNN thanks for basically ignoring my post lol, i answer both those questions XD

---

### Post by DJiNN on 2007-12-07
> **lswest said:**
> lol DJiNN thanks for basically ignoring my post lol, i answer both those questions XD

Whoops!! Apologies there.... in my haste i didn't read all the way to the bottom of the page.  Good answer too, nice & short..... i must be using the "Waffle Keyboard Drivers!" :)

---

### Post by jackmccaskill on 2007-12-07
Ok,

---

### Post by lswest on 2007-12-07
> **DJiNN said:**
> Whoops!! Apologies there.... in my haste i didn't read all the way to the bottom of the page.  Good answer too, nice & short..... i must be using the "Waffle Keyboard Drivers!" :)

lol it's no problem, pretty sure my system info ideas would work, but to be honest i had to think about it for a bit before replying:P  hardly use it, know all my specs off the top of my head XD  and lol @ the "waffle keyboard drivers"  a teacher of mine loves using the word "waffling" lol

---

### Post by jackmccaskill on 2007-12-07
O.K.,

     According to "System Monitor":

             ubutu:
                  Release 7.10 (Gutsy)
                  Kernal Linux 2.6.22-14-generic

              HARDWARE
                   Memory 376.7 MB
                   Processor Pentium III (coppermine)

              SYSTEM STATUS
                     Avaiable disk space 14.6 GB

---

### Post by DJiNN on 2007-12-07
> **lswest said:**
> lol it's no problem, pretty sure my system info ideas would work, but to be honest i had to think about it for a bit before replying:P  hardly use it, know all my specs off the top of my head XD  and lol @ the "waffle keyboard drivers"  a teacher of mine loves using the word "waffling" lol

Heehee...... I find it hard to write "Anything" without "Waffling"..... whereas others seem to be able to just answer the most difficult questions with just a few words. :)  

As for hardwar5e, i know what you mean.... I know all of mine, including the laptops, so never have to use anything to find out (Hence the reason why i don't know what the commands are!) ..... See? Waffling again! :-D

---

### Post by lswest on 2007-12-07
all right, i can do something with this^^  the memory then tells us a) it's SD RAM or earlier, as there is a larger chunk "missing" than usual, and its a PIII...so...it's probably best to use Xubuntu or install fluxbox on Ubuntu (i run that on my 18 year old compaq server).  Basically, you wanna go for the "sleek and light" linux distributions...cuz if my memory serves me the top speed of a PIII was...1.2GHz?  shouldn't really be that bad though once you change the window manager, or change the distribution.

and @ DJiNN...yea i'm a lucky kind of lazy person you usually answers questions efficiently:P  and waffling is a great word ^^.  I needed the commands once to find out the specs of the Compaq server i mentioned above:p never used it since then lol.

---

### Post by DJiNN on 2007-12-07
> **jackmccaskill said:**
> O.K.,

HARDWARE
                   Memory 376.7 MB
                   Processor Pentium III (coppermine)

              SYSTEM STATUS
                     Avaiable disk space 14.6 GB

Hi Jack.....

Well, i wouldn't run Ubuntu with a PIII (& it may be a Celeron - which would make it even slower) and that amount of RAM. I would look for a much "Lighter" distribution..... Zenwalk ([www.zenwalk.org](www.zenwalk.org)) is a nice & light distro that would be a LOT faster on that spec.  Or Wolvix perhaps. 

You could try "Xubuntu" and i'm sure that it would work, but i have a feeling that it may still be a little too slow. 

Good news is there's "Plenty of Choice!"..... :)

---

### Post by lswest on 2007-12-07
lol, always best to hide the bad news in good news, eh?  but i do honestly think that xubuntu would run on that...i mean my compaq server has a PII and runs Ubuntu 7.04 server with Fluxbox XD

---

### Post by rsambuca on 2007-12-07
You guys are missing the point here though.  There is no way that ubuntu should run that slow with that setup.

---

### Post by lswest on 2007-12-07
not necessarily...depends how much swap he gave it, and what kind of RAM that is...it's possible that it is running that slow...or that the hard drive is slowly dying...
there are hundreds of reasons why it could be so slow...anything from out-dated BIOS to a faulty hard drive

i do concede it is rather unbelievable though...however, with those specs taking a lighter distro would probably be best

---

### Post by rsambuca on 2007-12-07
Well swap has nothing to do with taking 5 minutes to boot.

---

### Post by lswest on 2007-12-07
no...but slow boot times can have other reasons, im not saying it would be ONE problem, it can be a couple of em which all sort of cause the slow loads at different parts of the booting process...  besides, to troubleshoot everything that could be wrong with it might be more work and ultimately ineffective, and he did ask for other ideas, we gave him our 2 cents, i mean if its hardware issues, no point in upgrading that laptop.

---

### Post by jackmccaskill on 2007-12-07
Thanks to all.  I will try a "lighter version of linux if you could tell mer a way to download via web.  After that info is received I will probably stop posting to this thread until I have the different version and then only if I experience additional problems.  At least 10 days as I am out of town for the next week.

Again thanks again

---

### Post by rsambuca on 2007-12-07
[http://www.xubuntu.org/get](http://www.xubuntu.org/get)

---

### Post by lswest on 2007-12-07
well, there were some links given by DJiNN before for some good lightweight distros, and a link to xubuntu is [here]("http://www.xubuntu.org/")

---

### Post by gn2 on 2007-12-07
Try Xubuntu 7.04, I run it on a PIII 500mhz laptop with 192mb RAM.

There have been a few posts with people having slow performance with 7.10 on older laptops, I experienced this myself.

In all cases using Xubuntu 7.04 has cured the problem.

I believe the slow performance isssue is due to the bootsplash image size.

---

### Post by ryanVickers on 2007-12-07
I"m running **XP** on a PIII 1Ghz (I think... lol) 512Mb laptop, so any distro of Linux should be FINE! :p

---

### Post by Bigbird999 on 2007-12-07
I am running Gutsy on a PIII Coppermine 500Mhz 512 MB Ram and like rmsambucca  said it does not run slow.  So I don't think a different distro is the answer.  Also, he said he has 512 RAM but system monitor only sees 396 MB, so maybe the video card taking the difference.  This is sometimes adjustable in the BIOS.  I would bet that he either has a video card/driver issue or a bad stick of RAM.  

It shouldn't be that slow, if it installed it should run faster than the CD (if there is not enough memory it won't install).  Which begs the question, how did it run on the Live CD???   There might be some answers in the hardware and Laptop forum

BB

---

### Post by Wynne G Oldman on 2007-12-07
I had a similar problem running Gutsy on two different IBM Thinkpads. I installed it on a T42 (I think the spec was 1.6ghz cpu 512 mb memory) and it ran fine. I also installed it on a T43 with a 1.7ghz cpu with 1gb of ram and it ran like a dog. About three times slower than the lower spec machine. Had me baffled! I installed Freespire on my daughters T30 which only has 256mb of ram, and it flies, compared to XP. Feels like a new machine! I gave up on Ubuntu on this Thinkpad, after twelve hours of the  the installation process. I know this was due to lack of memory. I would try Freespire on your laptop, and see how you get on with that.

---

### Post by DJiNN on 2007-12-07
> **lswest said:**
> lol, always best to hide the bad news in good news, eh?  but i do honestly think that xubuntu would run on that...i mean my compaq server has a PII and runs Ubuntu 7.04 server with Fluxbox XD

I agree..... it probably will run OK, especially if Fluxbox is used. Trouble is, Fluxbox to the newbie can be a little bit of a struggle to deal with. Anyway, it's worth a try, and for sure XFCE would be a lot more responsive than Gnome on that spec. 

By the way, what's "Fluxbox XD"?  Is that some kind of "Special Edition" Fluxbox? :)

DJiNN

---

### Post by Dr Small on 2007-12-07
Fluxbox XD would mean, "Fluxbox :D", basically.
Also, if Fluxbox is too complicated to the user, one can try IceWM as it is very simple and easy to use, along with lightweight.

[https://help.ubuntu.com/community/IceWM](https://help.ubuntu.com/community/IceWM)

---

### Post by DJiNN on 2007-12-07
> **Dr Small said:**
> Fluxbox XD would mean, "Fluxbox :D", basically.

LOL!! Whoops!.... i missed that one. Thanks for the heads up. :)

> Also, if Fluxbox is too complicated to the user, one can try IceWM as it is very simple and easy to use, along with lightweight.

Yep, i forgot that one....  IceWM is great, lightweight, and a lot more straightforward than Flux/OpenBox. 

On a similar note, just been trying FVWM, and it's really fantastic..... very usable and looks great! :)

DJiNN


[https://help.ubuntu.com/community/IceWM](https://help.ubuntu.com/community/IceWM)[/quote]

---

### Post by Dr Small on 2007-12-07
Oh sweet. I never knew about that one :)

---

### Post by lswest on 2007-12-08
sounds like a plan. i've personally only used fluxbox or blackbox apart from GNOME and KDE and XFCE, so i'm not too knowledgable on all the other window managers out there :P i'll keep thinking about what might be causing the huge lag in booting, if i come up with anything concrete ill post it here

---

### Post by DJiNN on 2007-12-08
> **lswest said:**
> sounds like a plan. i've personally only used fluxbox or blackbox apart from GNOME and KDE and XFCE, so i'm not too knowledgable on all the other window managers out there :P i'll keep thinking about what might be causing the huge lag in booting, if i come up with anything concrete ill post it here

If you like Fluxbox, you may well like OpenBox, which is very similar and (for me anyway) somewhat faster.  OpenBox is also an excellent window manager for Gnome. 

FVWM-Crystal (The latest version is 3.3 i think) is a Fantastic DE. From what i can gather, the guy that put it all together, basically just took all of the things that he liked from various different places & kind of tied them together, which sounds a bit dodgy, but the end result is pretty impressive. Well worth a look.

IceWM is good as well, and on certain distros where it's well set up etc it's great, but as a standard install with the standard themes etc it's a bit plain looking. VERY fast though, and on lightweight systems it really makes a difference. 

BTW, you speak/write great English, and yet your profile says Germany.... Are you English/American etc & living in Germany? You don't have to answer that but i thought i'd ask anyway. :lolflag:

DJiNN

---

### Post by lswest on 2007-12-08
lol i should hope my english is rather above-average XD i'm Canadian/British/Irish/German, living in Germany atm:P  also lived in the states and in Canada, grown up with english and german all my life, so i should think that qualifies me to speak it well:P  and thanks for the compliment i guess^^  and yea, you're just a walking dictionary on window managers aren't ya? lol

---

### Post by DJiNN on 2007-12-08
> **lswest said:**
> lol i should hope my english is rather above-average XD i'm Canadian/British/Irish/German, living in Germany atm:P  also lived in the states and in Canada, grown up with english and german all my life, so i should think that qualifies me to speak it well:P  and thanks for the compliment i guess^^  and yea, you're just a walking dictionary on window managers aren't ya? lol

LOL!! Thanks for the reply.... Kudos to you for the languages! :)  Nice mixture of Countries you've lived in as well..... adds to your culture i think. :guitar:
I'm English, living in France, and my French is superb as long as you only want me to count to ten or tell you my name. :biggrin:

It's a compliment to be sure, and as for WM's, yep.... i know what ones are out there, but as to how best to use them...... Ahem!!! Pass the cheese & change the topic!!  :-\":lolflag:

---

### Post by philinux on 2007-12-08
Ubuntu runs fine on this old croc. 

1. Look at the link for gutsy known bugs.

2. Install startup manager and run it.

My start up to login screen is always 53 seconds. Shutdown 13 seconds.

Firefox starts up fairly quick too.

---

### Post by ryanVickers on 2007-12-08
Mine can startup to login in a good minute or less every time, and login 'till everything is done is about another just under 30 seconds.  Starting firefox takes about 3 seconds :p

I have an AMD Athlon 64 X2 3800+ Processor (in English: AMD, 2Ghz, duel-core, 939 socket type)
A 300Gb Seagate 7200rpm SATA II Drive, and 1GiB of RAM.

---

### Post by sports fan Matt on 2007-12-08
Ryan,

Can you please post hot to get those stats on your startup (what needs to be removed) and starting firefox..I seem to not remember how you can acheive that...

---

### Post by rsambuca on 2007-12-08
> **ryanVickers said:**
> Mine can startup to login in a good minute or less every time, and login 'till everything is done is about another just under 30 seconds.  Starting firefox takes about 3 seconds :p

I have an AMD Athlon 64 X2 3800+ Processor (in English: AMD, 2Ghz, duel-core, 939 socket type)
A 300Gb Seagate 7200rpm SATA II Drive, and 1GiB of RAM.

What is the point of your post?  The OP has a machine with much older specs.

---

