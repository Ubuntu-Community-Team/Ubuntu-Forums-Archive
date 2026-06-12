---
title: "Hp s3220n and ubuntu"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by d3adp00l on 2008-03-24
Ok first a disclaimer, I am so new to this is far from funny. All I know is I hate windows, and want to try something else. I started with win3.1 and went until xp, and have been fairly adept at solving most problems I have ever had, never once in my life have I ever taken a computer in to have it fixed. I have had to trick machines into taking drivers and all kinds of fun stuff. But I am no coder, just a decent end user.

That said heres what I got, hp s3220n slimline (first actual commercial machine, everything else I have had has been built by me from components, and now I remember why). 

Now I didn't figure just popping in the ubuntu disk would get the system up and running and sure enough it didn't. I looked through the help section online and frankly its missing a step. How do I even install this os, I mean I know I am stupid with this but I am sure I am not the first to stick the disk in boot on it, and after it does all its stuff and the hd and cd drive are no longer active, I have a black screen. 

I through myself on your mercy, cause explaining this to me is proly gonna be like bouncin bricks on a wall, for a little while at least. 

If someone could just go over the basic proceedure, in some detail, of how to get this os up and running, that would be a great start.

Figuring out the driver issues as they come up will be another hurdle after that, as asus doesn't have drivers for download for this mobo, which is why I never bought a computer like this in the past, but its getting pretty pricey to piece one together vs just getting a run of the mill system.

Thanks in advance for anyone who takes this on, and my apologies for my ignorance also.

---

### Post by Squish on 2008-03-25
So to my understanding, you want to give ubuntu a shot, but you cannot boot up the install cd?

Well first off, good for you for trying something new. I am an HP Manufacturers rep, and with pretty good certainty, I can tell you that HP is a very linux friendly brand, along side Compaq of course. So I think that you did not neccessarely make a bad choice. I usually make my own pc's as well, however with lots of scattered parts, finding solutions sort of takes you all over the place... Anyways!

The first thing you want to make sure is that your BIOS (The stuff you see when you boot up your computer) is set to boot off a cdrom before the Harddrive. I am not sure what the bios button is for this machine, but it is usually esc/f8/f10... or maybe delete.
you should get to a screen like this:
[IMG]http://www.latenightpc.com/pictures/d/5028-2/phoenix-bios-main-screen.jpg[/IMG]
Go over to boot section, and find something along the lines of "Change Boot Priority"
Change it to cd first, and it should give you instructions.

Now f10 save that, pop the cd in, and restart!

It should load live of the cdrom. and you should see this:
[IMG]http://www.dailycupoftech.com/wp-content/uploads/2006/08/ubuntu02.png[/IMG]

Did you get that far?
this might help as well
[http://video.google.co.uk/videoplay?docid=-3644165467571075528&hl=en-GB]("http://video.google.co.uk/videoplay?docid=-3644165467571075528&hl=en-GB")

---

### Post by d3adp00l on 2008-03-26
yes I went through and set bios, I haven't bothered with updating the Mobo bios, as I am pretty sure the firmware is up to date. 
I get to that splash/loading screen sure enough, it goes through and the load bar eventually fills in from left to right till its all orange, and then that screen disappears and Thats about when I expect some kinda boot screen but it never comes, it just geos black and thats it, I will say this, there is some sound for about 10seconds when the screen first goes black, which between that and the fact that the cd and hd are active as all get out, I know its doing something. 

I would suppose it would be a video driver or something but at the same token I would kinda assume there would be a generic driver just for installation sake that would work with just about any card, I hate to say this given the context, but it is what my experience to date is so I have to say what I know, when windows first boots and doesn't have any driver for the card it just uses a simple generic set of code to operate it at minimal settings. Is this not the case for linux? Do I have to get a driver in there before the OS somehow?

I will sit back and let you do the talking as you know better than I, and I should have made it a bit easier by being more descript with where the load stopped, look forward to hearing more. And I am glad to hear that Hp is linux friendly, hate to have just bought the machine only to have it not jive with linux, as it is my goal not to ever have a vista machine.

---

### Post by d3adp00l on 2008-03-26
One thing I should mention, not sure if it makes a difference, but it is a 64bit amd  processor, and sata drives.

---

### Post by d3adp00l on 2008-03-26
ok so I dusted off an old monitor and plugged it in, and yes it loads, so its the monitor, which is really a lcd tv with pc input, so I guess the stock settings of ubuntu are out of spec for the lcd and I will have to change the settings with f4 I think it was, what to, not sure I will have to figure out what res, and refresh rate it supports and set it to that prior to the OS desktop loading, as that it when it stops. 

That video is very good, there should be a few of those on the ubunutu website, it would proly help a lot of us newbs, like they say a picture... so 60 pictures a second is worth a lot ain't it.

---

### Post by d3adp00l on 2008-03-26
even better news, my lcd is working, just wanted to be massaged a little while like so many machines do. I know I am proly the only one reading this, but for any one else who may be out, just cycle the input select after ubuntu loads, and when it gets back to pc it seems to be fine, apparently this lcd doesn't automatically track and adjust to it input, it only adjusts when it first enters pc mode. 

Alright now time to learn how to use this pretty looking desktop and everything else.

---

### Post by d3adp00l on 2008-03-27
So its up and running and I am still getting used to the environment, but that will happen with use and time.

Here's the status
amd 64 cpu
2g ram
400g hd (not being used right now)
8g usb stick running xubuntu in a 3g partition, 5g left over no swap)
              (if you want to know why I am running the above its simple really
               just wanted to see if it would work and how well, actually its very
               smooth and quiet, no hd noise at all ever.)
hp s3220n stock system
asus mobo (although asus website doesn't list it bn61 or something)
 
So no its time to install stuff to make it useful
I mainly use computers for only a few things, web (of course), and work.
Work is done with word and excel, mostly excel. I have a lot of speardsheets that I would need to convert to use with this system for it to be of any real use at all. Can this be done? If so how?

And in that search I was led to the whole package manger and library thing. And from what I can see off hand is this, all apps are downloaded and installed from online servers. Is that right? Everything for linux is all net based? Virtually no hard cds or other media for programs?

It also led me to find that the simple method of getting to apps, add/remove and synaptic, pretty much lists a bunch of stuff that doesn't jive with a 64bit processor. what do I do about this? Add other libraries I suppose, but which ones? I am sure there is a tutorial of how to do that, but how to find such things would be the trick. 

As I am the only one posting to this thread I figure it may take a while to get a response, so poke along I will. But other than being a neat novelty its not much use yet. I will say I was shocked at how easy the thing accessed the net. Three stinkin clicks of the mouse was all it took, THREE, I was blown away by that.

---

