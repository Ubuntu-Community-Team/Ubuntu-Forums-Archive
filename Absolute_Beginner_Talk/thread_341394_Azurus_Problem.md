---
title: "Azurus Problem"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by bman on 2007-01-18
I just installed Azurus and everytime I click on the file to open it up, it asks me if i want to view it in Terminal, run it, and some other things.

How do I make it so that it just opens up and runs?

---

### Post by meng on 2007-01-18
What file are you clicking on? A .jar file? How did you install it? From repositories?

---

### Post by davebgimp on 2007-01-18
The file you're clicking on is a script to launch it.

Go to a terminal, cd to the directory with the file and type:
**./azureus &**

You can make a custom menu entry for that process if you like.

---

### Post by bman on 2007-01-18
go to termial and I typed that, it didn't do anything, and how do I make a menu entry for it

---

### Post by gh0st on 2007-01-18
How did you install Azureus? I installed mine with Automatix and it set up the menu shortcuts and everything for me. You might wanna try it. [www.getautomatix.com](www.getautomatix.com)

It's cool for installing all kinds of stuff you don't get in the normal repos. You can just add the repos and install the stuff from Synaptic but I reckon Automatix is much easier for newbies. I certainly find it easier :D

Having said that azureus is pretty easy to run, just run ./azureus in the folder you extracted the files to if you want.

---

### Post by bman on 2007-01-18
thanks man, I totally forgot about automatix and it worked great, and alot of other stuff I was going to ask about was fixed up too.

Thanks.

---

### Post by Pobega on 2007-01-18
Keep in mind with Ubuntu Linux you always have repositories; Downloading from source is usually a last resource thing, for when downloading from aptitude, synaptic, automatix and finding a .deb download fail.

---

### Post by gh0st on 2007-01-19
> **bman said:**
> thanks man, I totally forgot about automatix and it worked great, and alot of other stuff I was going to ask about was fixed up too.

Thanks.

No problem, glad to hear it worked for you. :D

---

### Post by MaX on 2007-01-23
> **bman said:**
> thanks man, I totally forgot about automatix and it worked great, and alot of other stuff I was going to ask about was fixed up too.

Thanks.
Not to be an as or anything but... you didn't learn squat either...

---

### Post by gh0st on 2007-01-23
> **MaX said:**
> Not to be an as or anything but... you didn't learn squat either...

Yeah I take your point but I think you have to understand some people just want to use their PC to accomplish a goal they don't care how they get there. They just wanna check their emails or download some stuff.

To use an analogy, I know nothing about cars or motor engines but I am a driver of a car. I don't wanna have to learn to be a mechanic just to drive to the shops and buy some stuff. I'm not interested in that. Some people love cars and getting oil on them and thats cool we need people like that. We also need ordinary drivers. If everyone had to learn mechanics to drive a car, there'd be a lot less cars on road.

If you read the original post the guy just wants to load Azureus and do some downloading. He didn't ask how the program works or anything like that. If he had, I would have let someone more qualified than myself answer the question.

Just my opinion, I'm not starting a fight dude :D

---

### Post by MaX on 2007-01-25
> **gh0st said:**
> Yeah I take your point but I think you have to understand some people just want to use their PC to accomplish a goal they don't care how they get there. They just wanna check their emails or download some stuff.

To use an analogy, I know nothing about cars or motor engines but I am a driver of a car. I don't wanna have to learn to be a mechanic just to drive to the shops and buy some stuff. I'm not interested in that. Some people love cars and getting oil on them and thats cool we need people like that. We also need ordinary drivers. If everyone had to learn mechanics to drive a car, there'd be a lot less cars on road.

If you read the original post the guy just wants to load Azureus and do some downloading. He didn't ask how the program works or anything like that. If he had, I would have let someone more qualified than myself answer the question.

Just my opinion, I'm not starting a fight dude :D

Me neither, but the next time he'll ask the same question again, or when automatix fail to work he'll be lost.

I realise this is in Absolute Beginner Talk, but people should be educated instead of shoved the solution.

Maybe I'll get a friend to honk the horn in my car since I'm not interested in learning how to do that :P

---

### Post by jackrobinson on 2007-01-26
> **MaX said:**
> Me neither, but the next time he'll ask the same question again, or when automatix fail to work he'll be lost
When Ubuntu releases a broken libc6 update, he will be lost too.

---

### Post by Ben Sprinkle on 2007-01-26
Just open it normal, not run in terminal.

---

### Post by Drakkor on 2007-01-26
There's always a complete image backup solution (preferred), or a wipe/re-install solution, (less preferred) !  :-({|=

---

### Post by xpod on 2007-01-26
I dont agree that you dont learn anything by using AX either.

No matter how you get the job done your learning something and even if someone does use AX etc to get their Ubuntu`s up and running  those first days & weeks it does not mean they cant learn the many other ways of doing things along the way.

As mentioned, some mabey just want things to work without knowing every single dependency it requires or what the source code mabey looks like and for them AX is the buisness.

From what i understand theres apparently  a lot of Linux users who actually frown upon Ubuntu itself because it`s not the "proper" way of doing things so to me the frowning upon AX is much the same thing.....strange:confused:

---

### Post by gh0st on 2007-01-26
Fair enough, as I say I think if people wanna get into complicated stuff like compiling Kernel source or whatever great but some people just wanna use their PC not take it apart. I agree that people should try and learn as much as they can about Linux but let them get their feet through the door first.

Criticizing new users for using tools that make their introduction to Linux easier is not going to help Linux at all. If you don't wanna answer stupid questions then cool, just leave it to people who are happy to do it.

This kind of elitism is exactly what puts non technical people off Linux. I thought the idea of these forums was to be friendly and help people. Isn't that what Ubuntu is about. I don't see how driving people back to windows helps anyone but Microsoft.

---

### Post by MaX on 2007-01-28
> **gh0st said:**
> Fair enough, as I say I think if people wanna get into complicated stuff like compiling Kernel source or whatever great but some people just wanna use their PC not take it apart. I agree that people should try and learn as much as they can about Linux but let them get their feet through the door first.

Criticizing new users for using tools that make their introduction to Linux easier is not going to help Linux at all. If you don't wanna answer stupid questions then cool, just leave it to people who are happy to do it.

This kind of elitism is exactly what puts non technical people off Linux. I thought the idea of these forums was to be friendly and help people. Isn't that what Ubuntu is about. I don't see how driving people back to windows helps anyone but Microsoft.

I am helpfull, it's just that Automatix is a non-supported way of doing things in Ubuntu and IIRC it could break stuff too.

I also want to just use my PC, that's why i switched from Gentoo to Ubuntu, I still think you should learn people how to solve stuff the "official "Ubuntu way instead of using a non-standard application that might break things. When Automatix is embraced into ubuntu, I'll support it.

We could continue this in PM if you'd like so that we don't clutter up the Beginner Talk forum.

---

### Post by gh0st on 2007-01-28
> **MaX said:**
> I am helpfull, it's just that Automatix is a non-supported way of doing things in Ubuntu and IIRC it could break stuff too.

I also want to just use my PC, that's why i switched from Gentoo to Ubuntu, I still think you should learn people how to solve stuff the "official "Ubuntu way instead of using a non-standard application that might break things. When Automatix is embraced into ubuntu, I'll support it.

We could continue this in PM if you'd like so that we don't clutter up the Beginner Talk forum.

Cool ok I see what you mean but you never said what the approved Ubuntu method was, you just told the bloke he hadn't learnt anything. Whats the approved Ubuntu method then? Add the appropriate repos and just install everything individually? I am honestly asking here.

I can't see many new users wanting to do that. PM me if you like, as you say it's not really fair to just hog this thread and clutter up the Beginners Area.

---

