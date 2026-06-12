---
title: "Can linux do this?"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by kevin11951 on 2007-10-20
[http://www.extremetech.com/slideshow_viewer/0,1205,l=&s=200&a=172305&po=4,00.asp](http://www.extremetech.com/slideshow_viewer/0,1205,l=&s=200&a=172305&po=4,00.asp) 

have a look, and tell me, can linux do that, keep in mind im not attacking linux, i just want to know if it can do this?

---

### Post by Calash on 2007-10-20
No, and personally I am glad it cannot.  That is just a poor idea that will cause untold issues 3-6 months down the road.

Using USB to speed up your system....BLECH!!!.

---

### Post by regomodo on 2007-10-20
why would you want to. Flash isn't quicker than ram (and neither is usb2) and in any case Linux doesn't use anywhere near as much ram as vista.

Constantly writing and rewriting to a flash drive will kill it.

Swappiness to zero anyone?

---

### Post by shad0w_walker on 2007-10-20
Which thing specifically or all of it? I didn't look past the first couple of pages (Used Vista, couldn't stand it, not gonna read about its 'features')

The USB trick is just putting a swap file on USB. It's only real useful affect is that it's likely to burn through your write cycles alot quicker than normal usage but yes, Linux can quite happily do that and has been capable for years, just no fancy GUI to my knowledge.

---

### Post by n3tfury on 2007-10-20
> **Calash said:**
> No, and personally I am glad it cannot.  That is just a poor idea that will cause untold issues 3-6 months down the road.

Using USB to speed up your system....BLECH!!!.

um, actually it's a novel idea.  can you elaborate on how it will "cause untold issues 3-6 months down the road"?  what kind of issues?  where did you come up with those numbers?

*it's novel  for WINDOWS if you can't afford new RAM and have a usb stick laying around*

---

### Post by daverich on 2007-10-20
that's just a gimmick.

Whats more important is scroll down that page and theres a company selling a product to let vista start up "faster and smarter and safer than ever before!"

THAT said boatloads more about vista than using a usb stick for a little more RAM.

Kind regards

Dave Rich

---

### Post by raul_ on 2007-10-20
Yes it can. There is a thread about this.

EDIT: here you go [http://ubuntuforums.org/showthread.php?t=395435&highlight=readyboost]("http://ubuntuforums.org/showthread.php?t=395435&highlight=readyboost")

However, it ruins your USB pen faster, because pens have a maximum writing cycles, just as batteries have a maximum charging number (like 500 times or so)

---

### Post by daverich on 2007-10-20
> **n3tfury said:**
> um, actually it's a novel idea.  can you elaborate on how it will "cause untold issues 3-6 months down the road"?  what kind of issues?  where did you come up with those numbers?

He probably means that usb sticks have a limited Read/Write lifetime. I certainly wouldn't want to be using them as ram.

Kind regards

Dave Rich

---

### Post by Paqman on 2007-10-20
Couldn't you mount your swap partition on a USB?

Not sure why you'd want to, it'd kill the stick pretty quickly, and it'd only be of any use if you were using 100% of your RAM anyway. Which if you've got more than 512MB is pretty hard to do in my experience.

---

### Post by n3tfury on 2007-10-20
> **daverich said:**
> He probably means that usb sticks have a limited Read/Write lifetime. I certainly wouldn't want to be using them as ram.

Kind regards

Dave Rich

saw that after the fact, thanks :)

---

### Post by Calash on 2007-10-20
USB Limited read/write
Removal during cahing operation
USB Viruses
Faulty Key Design
Slow Access speeds (Current technology)
And, User Error.  How many people are going to have these hanging from the front of there systems?  How many with accidently hit it and snap off the may part?  It happens alot now, and this will only promote it more.

And I do stand corrected, Linux can do this type of setup.  I did not even think of putting the swap on a key.


]Solid-State caching is a good idea, using low-cost USB keys is not.

---

### Post by edoviak on 2007-10-20
If you absolutely need extra memory (e.g. for working with a large dataset), you can format a USB flash drive as swap, create an entry for it in **/etc/fstab** and reboot the computer (with the flash drive inserted). 

If you have a 2GB USB flash drive, that will give you an extra 2GB of memory to work with.

After you're done, remove the **fstab** entry (or comment it out) and shut down the computer, then remove the USB flash drive and boot to return to your computer's normal state.

- Eric

---

### Post by dasunst3r on 2007-10-20
Typically, less than 512 MB of my 2 GB of RAM is really being used, so this feature really isn't necessary.

---

### Post by kevin11951 on 2007-10-20
ive been reading all your replies, and i see how a usb pen would die, taking your computer with it, bu what about an external laptop hdd, i got one of those

---

### Post by argie on 2007-10-20
> **kevin11951 said:**
> ive been reading all your replies, and i see how a usb pen would die, taking your computer with it, bu what about an external laptop hdd, i got one of those

Then you use this: [http://ubuntuforums.org/showthread.php?t=395435](http://ubuntuforums.org/showthread.php?t=395435)

Really, I don't see why you would want to do this. Hard drive access takes longer than RAM, and all you need to do is make your external hard drive a swap file. That's basically what the above thread does.

---

### Post by nrfool on 2007-10-20
From what I read, the idea of ready-boost is use the memory to information that will otherwise be displaced into hard-drive cache. The example MS gave was your open office documents when you have anti-virus scan running while you are away. Although USB is not a particular fast data lane, compared with, say IDE lines of hard drive, the fact that flash memory have no need to seek and very short read/write time will compensate the USB band width. Hence, access the information stored on the flash drive will still be faster than reading from hard drive cache.
However, HP seems to disbutes the effectiveness of this approach. [http://www.notebookreview.com/default.asp?newsID=3742](http://www.notebookreview.com/default.asp?newsID=3742)

linux uses system memory as cache and that is much faster than reading from usb flash drive. In this sense, if your system memory is large enough, ready-boost is unnecessary. I think this is actually true for both linux and vista, as both of them use memory for cache.

Another vista feature I have heard of is the pre-emptive read. I feel that should be playing a more important role in improving the responsiveness of the OS

---

### Post by raul_ on 2007-10-20
> **nrfool said:**
> Another vista feature I have heard of is the pre-emptive read. I feel that should be playing a more important role in improving the responsiveness of the OS

Isn't it preloading in linux?

---

### Post by gn2 on 2007-10-20
> **kevin11951 said:**
> [http://www.extremetech.com/slideshow_viewer/0,1205,l=&s=200&a=172305&po=4,00.asp](http://www.extremetech.com/slideshow_viewer/0,1205,l=&s=200&a=172305&po=4,00.asp) 

have a look, and tell me, can linux do that, keep in mind im not attacking linux, i just want to know if it can do this?

It simply doesn't have to. Linux is leaner and more efficient. Vista requires massive amounts of RAM just to run the OS, Linux doesn't.

I'm writing this using Firefox while downloading and installing 110 packages (don't ask) on my old Xubuntu PIII laptop which has192mb RAM. 

Which is about a gig less than Vista needs just to sit idle.

---

### Post by nrfool on 2007-10-20
ubuntu does provide a more responsive system under heavy load. However, using firefox while download and installing 100+ packages is not really an appropriate example. Since the packages only download and install one after another. Plus, Vista can do much more with 1G of ram. In fact, it work rather well.

---

### Post by gn2 on 2007-10-20
> **nrfool said:**
> ubuntu does provide a more responsive system under heavy load. However, using firefox while download and installing 100+ packages is not really an appropriate example. Since the packages only download and install one after another. Plus, Vista can do much more with 1G of ram. In fact, it work rather well.

But Vista won't run at all on my laptop.
Even W2kPro is painfully slow. 
Xubuntu 7.04 means I don't have to buy a new laptop.

I also have a Core 2 Duo desktop PC with 1Gb of RAM running Xubuntu and XP (dual-boot) and it can do an astonishing amount of tasks at the same time.

It would not be able to perform as well with Vista which is utter bloatware.

---

### Post by raul_ on 2007-10-20
> **gn2 said:**
> But Vista won't run at all on my laptop.
Even W2kPro is painfully slow. 
Xubuntu 7.04 means I don't have to buy a new laptop.

I also have a Core 2 Duo desktop PC with 1Gb of RAM running Xubuntu and XP (dual-boot) and it can do an astonishing amount of tasks at the same time.

It would not be able to perform as well with Vista which is utter bloatware.

You should try Arch and feel the boost of using an architecture optimized distro ;)

---

