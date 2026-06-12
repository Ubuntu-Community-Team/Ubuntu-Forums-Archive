---
title: "Trying to remove the games and it tells me in need to remove kubuntu-desktop"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by ovimunt on 2006-07-30
Hi,

I don't understand anything anymore!!! :confused: 

All i want to do is remove some of the games. Yet ***apt-get***, ***aptitude*** and ***Adept*** tell me that ***kubuntu-desktop*** will be broken so I need to remove it as well in order to satisfy the dependencies!? :shock: 

I actually tried to remove a number of random applications using the Add/Remove Programs option and I can't do it unless I also remove kubuntu-desktop !? :-s This can't be right!!!

Is there something I am doing wrong? :confused:

---

### Post by NotJustANewbie on 2006-07-30
You cannot remove packages which a dependant by other packages without removing the other packages as well.. In this case, kubuntu-desktop.

---

### Post by drosophyllum on 2006-07-30
prediction:

maybe killing the game would kill dependancys that are needed in kubuntu

think of it like pulling a tree and its roots off a slopeing sandy ground, if you pull the tree out you might destroy a root that was holding the slope (kubuntu) together?

---

### Post by ovimunt on 2006-07-30
This is THE most STUPID thing in linux!!!!!!

What do you mean I cannot remove parts of the package????????

This is absolutely outrageous!!!! 

If this is so I am afraid today was the last day I've been using linux, EVER!

---

### Post by drosophyllum on 2006-07-30
wow, dont get that angry, there is something called Removing a package manually.... ;)

---

### Post by Lord Illidan on 2006-07-30
> **ovimunt said:**
> This is THE most STUPID thing in linux!!!!!!

What do you mean I cannot remove parts of the package????????

This is absolutely outrageous!!!! 

If this is so I am afraid today was the last day I've been using linux, EVER!
Just go ahead and remove the package. Kubuntu-desktop is a meta-package, it doesn't mean you will lose kde too.

And if that is the last day you've been using linux, I wonder why I cannot remove parts of windows, like Windows Media Player or Internet Explorer...absolutely outrageous indeed!

---

### Post by ovimunt on 2006-07-30
I decided to try linux exactly because I thought it was NOT like Windows. What you're telling me now is that it actually IS quite a lot like Windows. 

Plus, trust me, I have been doing my outmost best to try and switch to linux but so far it hasn't happened simply because it's too damn difficult to get things to work! The main reason for this is EXACTLY that which is supposed to be the main advantage over Windows - it's FREE. 

As long as you don't PAY for something you'll never get the best of it! It's life mate, it's as simple as that: NOTHING COMES FOR FREE! Why should linux be any different?

So, if you could choose between an OS which you have paid for anyway and which works almost flawlessly but does have its limitations and another OS which is free and is supposed to work flawlessly but you have to spend half a day do get it sort of working but not really, which one would you choose?

That's just LIFE mate, and it's not just about Windows and Linux...

---

### Post by psycosmyth on 2006-07-30
Remove IE? That's a sin!!:P
This was my bump in the choice of DE's, I agree that it's crazy for KDE to have strange dependencies, but it helps to reduce the code that makes it. I simply learned to leave the things I did'nt want alone. I did remove the bulk of KDE but I will always be a couple of clicks from having it back. I have the unfortunate obsession to make everything I don't want go away and in the Linux world it seems a little easier. Maybe you could try a smaller distro such a DSL or Feather.

---

### Post by NotJustANewbie on 2006-07-30
lmao...DSL or feather as a hard disk install... for such a Linux n00b?!?:D

EDIT: ovimunt, if you think ubuntu is difficult, try slackware.:rolleyes:

---

### Post by ovimunt on 2006-07-30
I didn't say Ubuntu (which you have to praise for the effort that went into it) but Linux in general...

---

### Post by Lord Illidan on 2006-07-30
> **ovimunt said:**
> I decided to try linux exactly because I thought it was NOT like Windows. What you're telling me now is that it actually IS quite a lot like Windows. 

Plus, trust me, I have been doing my outmost best to try and switch to linux but so far it hasn't happened simply because it's too damn difficult to get things to work! The main reason for this is EXACTLY that which is supposed to be the main advantage over Windows - it's FREE. 

As long as you don't PAY for something you'll never get the best of it! It's life mate, it's as simple as that: NOTHING COMES FOR FREE! Why should linux be any different?

So, if you could choose between an OS which you have paid for anyway and which works almost flawlessly but does have its limitations and another OS which is free and is supposed to work flawlessly but you have to spend half a day do get it sort of working but not really, which one would you choose?

That's just LIFE mate, and it's not just about Windows and Linux...
What I am telling you is that everything has its flaws. Even Linux. Even Windows.

And Linux doesn't have flaws because its free. That pigheaded attitude won't get you anywhere.

Consider Apache, for example. It is free. It is opensource. It is used by 70% of the Internet's webservers.
Consider Firefox. It is free. It is opensource. It is rapidly swallowing IE's market share by the day.

Linux needs more developers,  that's a fact of life, and anyway I doubt your problems are really with linux, more likely they are with some app or other.

And does XP work almost flawlessly? I wonder...for many people, it doesn't, you know.

---

### Post by NotJustANewbie on 2006-07-30
Yes, linux is difficult to start with. You have to get into a rhythm with linux, at least that is the way I see it.  Once you have everything up and running (just the way you want it), you have to maintain it (if you update using the repositories).

Little things such as removing a few games aren't that important. So what if it takes up a few more megabytes on your precious hard disk..:-( ... It's not the end of the world.

K/X/Ubuntu all come with a minimalistic package selection as default (in being that there is only one program per job - i.e. word processing is openoffice.org and not koffice and kate etc...)

Ubuntu as default is very uncluttered as linux distros come.

You just have to learn to live with these minor inconveniences but don't get too wound up over something this little.  You will come across many other problems when you will want to throw your box out of the window (like when you buy a piece of hardware where no drivers exist for linux... yet).

Good luck with whatever you do and I hope you continue to use linux as it will make you more aware of what computers were really invented for (if you haven't tried any BSD yet ;-) )

---

### Post by jimmygoon on 2006-07-30
You do realize now that the games are completely seperate and that removing kubuntu-desktop literally means nothing... its just there so that if you screw something up... it can make sure that all the packages are related by that "meta-package"

basically kubuntu-desktop is like a container package, when you remove the games its no longer "kubuntu-desktop" but everything else is still installed.

Don't get so worried man, you were really freakin out... jeez

---

### Post by Lord Illidan on 2006-07-30
And understand this. Feel free to go back to windows. None of us will stop you. If you prefer Windows, use it. There is no shame.

---

### Post by ovimunt on 2006-07-30
I've been at the point of throwing my computer out the window many times when using Windows so don't worry, I've had the bitter taste of it as well. 

And I guess the truth is that I really am angry at those people who don't care unless they make money out of it i.e Adobe, ATI, and other companies like these who don't really give a s**t whether their products are supported on linux or not. 

Yet for some reason I think they would put a hell of a lot more interest in linux if there was any money in it for them...

---

### Post by Kilz on 2006-07-30
> **ovimunt said:**
> So, if you could choose between an OS which you have paid for anyway and which works almost flawlessly but does have its limitations and another OS which is free and is supposed to work flawlessly but you have to spend half a day do get it sort of working but not really, which one would you choose?

That's just LIFE mate, and it's not just about Windows and Linux...

The problem with this thought is that windows (the paid for OS)is less than flawless. It has tons of problems. Security holes, viruses, spyware, etc. You don't really think about all the time you spend each week cleaning out the garbage that's in windows. If you don't it slows to a crawl within a month of install. 
Also , have you ever taken a Microsoft windows install disk( not a restore disk that comes with a computer) and tried to get everything working? If you haven't, I think you should try it. Then think about handing that disk to someone who has never used windows before. 
On the other hand Linux may take a little bit to learn. It may take a little longer to setup. But once it is it runs , and runs, and runs, like the energizer bunny. 
I can remember the last time I worried about updating my anti virus and anti spyware. The last time I worried about deleting temp files and other garbage that accumulates in Windows.
The day I deleted my Windows partition. 
I think the time trade off is in Linux's favor. After all if I have to reinstall, now that I know how , it takes the same amount of time installing a windows setup did.

---

### Post by psycosmyth on 2006-07-30
"Hello, I'm a Mac" "and I'm a PC" 
"and I'm the almighty penguin that can jerk both of your puppet strings!!"

I think I thought I heard that somewhere:rolleyes:

---

### Post by Lord Illidan on 2006-07-30
> **ovimunt said:**
> I've been at the point of throwing my computer out the window many times when using Windows so don't worry, I've had the bitter taste of it as well. 

And I guess the truth is that I really am angry at those people who don't care unless they make money out of it i.e Adobe, ATI, and other companies like these who don't really give a s**t whether their products are supported on linux or not. 

Yet for some reason I think they would put a hell of a lot more interest in linux if there was any money in it for them...

Don't worry, there is money to be found in Linux. Why else do IBM, Redhat and Novell all support Linux? And Redhat turns over a profit, too. Dunno about Novell.

Nvidia's drivers work too, for example.

They would put more interest in Linux if there were more users.

---

### Post by ovimunt on 2006-07-30
And another thing, I go to work, I do my job and I expect to be paid for it.

It's not because I like to see a few more digits in my account every month or for those filthy bits of paper and metal I carry around. 

It's because I need to eat, to pay my rent, to buy my girl flowers of her birthday...

If what I did was for free how would I be able to do all these?

It's not difficult to understand why there aren't enough developers for linux...

Anyway, I don't have anything against linux, I just think that it's never going to be available to the masses unless someone invests propper money in it and the masses pay for it, at least a little.

---

### Post by Lord Illidan on 2006-07-30
> **ovimunt said:**
> And another thing, I go to work, I do my job and I expect to be paid for it.

It's not because I like to see a few more digits in my account every month or for those filthy bits of paper and metal I carry around. 

It's because I need to eat, to pay my rent, to buy my girl flowers of her birthday...

If what I did was for free how would I be able to do all these?

It's not difficult to understand why there aren't enough developers for linux...

Anyway, I don't have anything against linux, I just think that it's never going to be available to the masses unless someone invests propper money in it and the masses pay for it, at least a little.

That's true. Many devs work on Linux as a hobby. Not that it's bad, because they tend to work more effectively, seeing it as a work of love, rather than plain work. But, then some projects get abandoned due to lack of time.

If you want to pay for Linux, there is Linspire, Suse, Mandriva.
IBM and Novell do invest proper money in it. Novell also hires dozens of programmers to work on Linux stuff full time, good for them.

---

