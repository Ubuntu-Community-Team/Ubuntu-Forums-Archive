---
title: "G4 Live CD Boot Problems"
date: 2008-07-27
forum: Apple Hardware Users
---

### Post by mmstone on 2008-07-27
Hello all!

I want to try out Ubuntu on my G4 Quicksilver 868MHz, with 1.5G RAM, and Radeon 8500 video card.

I have tried to boot from PPC Live CD for Heron, but splash screen just sits there (overnight!). I am now trying PPC Live CD for Dapper. I get to splash screen with progress bar and below it says "Loading Essential Drivers....ok" and that's it. It just sits there. I am using the video=ofonly kernal (if I remember right). I have tried with a couple different kernal options, but nothing works.

Is there any hope to try Ubuntu out on this machine?

Thanks in advance

---

### Post by tiresia on 2008-07-27
You should try with the Hardy alternate install CD, it should work smoothly
Here is the link: 
[http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)

If you have problems, when Yaboot start, press TAB to see the different options - your computer is a PowerPC 32 Bit

---

### Post by mkvnmtr on 2008-07-28
I have the same problem with 7.10 and 8.04.1 live disks. They get to the point I should have a splash screen and then nothing but black. I tried enter, live video=ofonly and many other keys and nothing happens. Then I booted the alt install disk for 8.04.1. The install went fine and then when I rebooted from the hard drive the same black screen an the same point as the live disk. I think if the live disk won't work the installation won't work. I am waiting for someone to help you before I try again.

---

### Post by stream303 on 2008-07-28
> **mmstone said:**
> I want to try out Ubuntu on my G4 Quicksilver 868MHz, with 1.5G RAM, and Radeon 8500 video card.

Does that machine work with OSX?  Reason I ask is that afaik, the quicksilvers only came with Nvidia cards as oem, and wonder if the Radeon you are using is specifically for ppc?  I think it should make a fine ppc machine, although one might have to put some time into it.

> I am using the video=ofonly kernal (if I remember right). I have tried with a couple different kernal options, but nothing works.

Now that it appears that you have Ubuntu installed, you may also want to try "nosplash" without the quotes, something like this:

```
Linux video=ofonly nosplash
```

Exactly what were the other parameters you tried? - that will help.

It is very likely you'll need to manually edit your /etc/X11/xorg.conf file as well, but first, are you able to get to a virtual-terminal with CTRL-ALT-F1 ?

Also, what external monitor are you using, and what are the horizontal and vertical frequency specs for it?

---

### Post by mkvnmtr on 2008-07-28
I finally got on the live disk. When it got to the point ready to load the kernal I pressed tab and some options came up. I choose the live=ofonly no splash powerpc. I typed it in and pressed enter and here I am on the live disk. It tells me that I need some drivers for my equipment. That is probably the reason we can't get the splash screen.I think I will check what is working on the disk and then install tonight. I learned how to get in without a splash screen.

Just to let you know. The install worked great. The only problem is the drivers I need to get for wireless. I am on a 4 year old IBook Powerpc.

---

### Post by mmstone on 2008-07-30
Thanks for all the suggestions. I tried the Hardy alt disc, but no go. Still hangs, no boot. I have not installed it on my machine yet as I am trying to see how it will run on the Quicksilver Mac. I know that the alt disc is to install, but it won't even do that.

My computer is basically a stock unit, standard 2001 Quicksilver 867MHz PowerPC that currently runs Tiger w/o problem, though a bit slow now. I have 1.5 GB of RAM, so memory shouldn't be a bottleneck. The only thing I have really changed on the unit was to add the ATI Radeon 8500 for the Macintosh. It has worked fine in for several years. I don't know if that is the deal killer or not. Nothing else unusual about the computer.

As I noted above, the tower is obviously looking long in the tooth, and it is a bit sluggish with Tiger. I thought it would be fun to try Ubuntu on it, and see if that worked a bit better/faster. My wife uses it mainly for email, websurfing, and casual games like solitaire and Mah Jong. 

Again, thanks for all the help, but it looks like it's just not going to work.

mms

---

### Post by stream303 on 2008-07-30
Don't give up just yet.  BTW, do you have an upgraded hard drive?  If so, that machine has a 128gb partitioning limitation that one needs to work around.

Also, have you tried a variation of the kernel parameters for the radeon framebuffer?

In addition to using nosplash, also try using something similar to the following on the same parameter line:

```
video=radeonfb:1024x768-24@60
```

Change the horizontal and vertical resolution values to fit your monitor.

Hopefully the combination of nosplash and this radeonfb parameter can kick-start that machine.  It would make a fine Linux box.

---

### Post by mkvnmtr on 2008-07-30
I finally got my Ibook to accept 8.04.1 live disk. Everybody says use live video=0fonly or other things. I am sure that is good advice but they never said when to hit the tab key and I waited to late. If you need to do something special to boot the live disk when it first comes up "this is the 8.04.1 live disk", before it begins to load the kernel is when to hit tab. Then a page comes up with many things you can use. At the bottom of the page is a prompt and if you type something this is where you will see it.When you finish press enter. Give it plenty of time. If it does not work you might have to start over and restart again to get to the point to press tab and type in something else. Take your time and read all the different options you can use. If the first one does not work try something else or ask for advise and try that. Good luck

---

