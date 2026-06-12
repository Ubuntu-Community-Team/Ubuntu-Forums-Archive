---
title: "Completely revamping Ubuntu and Adding features- How would I go about this"
date: 2013-05-06
forum: Any Other OS
---

### Post by tehhh1337 on 2013-05-06
Hey everyone,

So this question is kind of a big one I guess. The goal of the project I'm working is to create an entirely new OS. Obviously writing one from scratch in this day in age is kind of a waste of time, so I thought I'd base it off Ubuntu. 
I'm pretty much planning on editing everything via the source code, (no customization programs, this OS needs to have an ISO file at the end that you can burn to a CD, without any of my personal files, but with all of the features and programs that I plan to write. No strings attached.) How would I go about doing this? I know many programming languages, so I think it's just a matter of getting the source code and editing it. I've done some preliminary research on this, but I can't quite figure out how to get it done. Secondly, I'd like to build new packages to have on the default OS (end product). These aren't just nifty programs, but actual OS features (like the unity bar, that's a prime example of a program I might make). How would I go about this?

Thanks.

---

### Post by Megaptera on 2013-05-07
Have you had a look here: [http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/) Quoted "Linux From Scratch (LFS) is a project that provides you with step-by-step instructions for building your own custom Linux system, entirely from source code."

Hope this helps?

---

### Post by tehhh1337 on 2013-05-07
Thanks for the reply. I've actually looked at that before and it looks extremely complicated, but I do agree it seems like the most viable (although not preferable =[ ) option.
If there's any other resources out there, feel free to let me know. I'll keep this thread open for replies.

---

### Post by user1397 on 2013-05-07
first you have to ask yourself, what is the end goal here?  Are you just doing this as a challenge for yourself or for fun?  Are you trying to add features to ubuntu that it does not already have?  Are you trying to make a new distro and plan to maintain it for other people to be able to download and update it?  

If you want to just base it off ubuntu, I don't think making a whole new distro is the best option.  Maybe instead you could focus on contributing to the code of any program, such as unity, or start a new program.

I'm not trying to be a buzzkill, but another ubuntu spinoff or another completely new linux distribution may not be the most prudent thing in the world right now...  Fixing bugs/adding new features or cleaning up code to already existing programs is time better spent in my opinion, or of course making your own new program if you've got a kickass idea :P

---

### Post by tehhh1337 on 2013-05-07
Well yeah in any other case you're 100% right, but in this scenario it's actually prudent that I my own written OS, simply due to the fact that the features I need to have do not exist, and as of my knowledge don't exist in the minds of any other developer either.
As for the end goal, it would be to create an entirely new OS and eventually, long from now however, distribute it.

---

### Post by lykwydchykyn on 2013-05-07
New OS, or just a new desktop environment?  

A system like Ubuntu is put together by selecting components from a vast pool of available open-source code, and fitting them together into a reasonably cohesive whole.  You don't just "download the source code for Ubuntu"; it's not just one monolithic program with a single set of source files.  Pick some component that you want to tinker with, and start there.  Then decide if it's simpler to modify something already written, or write the component yourself from scratch.

---

### Post by mastablasta on 2013-05-08
otherwise for starter install ubuntu minimal iso. add what you want and hten use remastersys or system imager or what is called now to cretae the iso. 

ofcourse you would still need to change branding and such...

---

### Post by tehhh1337 on 2013-05-08
I'm thinking an entirely new OS. If I just tinkered with Ubuntu, and called it my own I feel like that would be kind of ....lame...

---

### Post by iamkuriouspurpleoranj on 2013-05-08
At the level you're interested in Ubuntu, you should probably use Debian as a base.

---

### Post by lykwydchykyn on 2013-05-08
> **tehhh1337 said:**
> The goal of the project I'm working is to create an entirely new OS. Obviously writing one from scratch in this day in age is kind of a waste of time, so I thought I'd base it off Ubuntu. 


> **tehhh1337 said:**
> I'm thinking an entirely new OS. If I just tinkered with Ubuntu, and called it my own I feel like that would be kind of ....lame...

I'm confused about exactly what you are wanting to do here.

Can you be specific about what types of things you intend to change?  That might help us point you in the right direction.

---

### Post by tehhh1337 on 2013-05-08
Basically, I would take the base OS and revamp it entirely. For example, I would change the GUI around significantly, remove some packages, cover up all code that could ever show up, and change visuals.

I'd also have to write programs specific to new hardware that I will introduce. It will pretty much be an entirely different OS. Think about how advanced Ubuntu is in User-friendliness right now. That's my goal, except it can't look like Ubuntu.

---

### Post by lykwydchykyn on 2013-05-08
> **tehhh1337 said:**
> Basically, I would take the base OS and revamp it entirely. For example, I would change the GUI around significantly, remove some packages, cover up all code that could ever show up, and change visuals.


I don't know what you mean by "cover up all the code that could ever show up", but otherwise you're describing pretty much every Ubuntu remix or derivative ever created.  What you want to create is not properly called an "OS", you want to create a new desktop environment and build a derivative distro around it.

> 
I'd also have to write programs specific to new hardware that I will introduce. 

OK, can't fathom what that's about, but you must have something in mind.
> 
It will pretty much be an entirely different OS. 

Unless you ditch Linux and GNU, it's not really technically a different OS.   People debate about what the term "OS" actually encompasses, but (at least in the Linux world) changing the GUI around a bit doesn't make for a new OS.  Just a different distro.
> 
Think about how advanced Ubuntu is in User-friendliness right now. That's my goal, except it can't look like Ubuntu.

You've got the cart before the horse here; if your driving ethos is "Like ubuntu, but not like ubuntu", you're never going to get anywhere.  You'd be better off figuring out how you *want* the thing to look first, and not worry about how much or how little it looks like anything else.  

So here's my advice:  Get yourself a spare computer, put a minimal ubuntu install on it, and start trying different desktop environments.  Check out any you can lay hands on.  Customize them, break them apart, see how they work.  Learn about things like xdg, dbus, X11, etc.  Look at some code from smaller projects like LXDE or razor-qt.  There's a wealth of resources out there, but you need to learn to crawl before you fly.

---

### Post by Habitual on 2013-05-09
> **tehhh1337 said:**
> Obviously writing one from scratch in this day in age is kind of a waste of time.Epic Fail.
I am sorry, but you'll never get anywhere with this project with a defeatist declaration of a "why bother" attitude.

If it's a waste of your time, then it certainly gets a vote-down from me.
If you truly want to develop your "own" OS, then [Linuxfromscratch]("http://www.linuxfromscratch.org/")
If you simply want to "redecorate" the Ubuntu furniture, then [RemasterSys]("http://www.remastersys.com/")
It even has a GUI for those who like, (or need?) that sort of thing. 

Certainly all goes to waste if the replies have more vested interest than the Original "waste of time" post.

---

### Post by tehhh1337 on 2013-05-09
Yeah, your right. But the thing is, I don't even know how to customize them and break them apart. I do have a model of what I'd like it to look like, but I just don't know exactly WHAT to edit, so...
But yeah I'll follow your advice and do some research on some of those other elements.

By hiding the code I meant like when the machine starts up, it shows all of that init code that could possibly be scary to an inexperienced end-user.

Thanks

---

### Post by 2Stoned on 2013-05-31
> **tehhh1337 said:**
> 

By hiding the code I meant like when the machine starts up, it shows all of that init code that could possibly be scary to an inexperienced end-user.

Thanks

This can be fixed easily. Just install some plymouth script or write your own.

---

