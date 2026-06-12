---
title: "Which Laptop Would Suffice?"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by FoggyMtn on 2006-03-26
Hey Ya'll,

Thanks to some help from the folks on the ubuntu-mac forums, I've got a live cd running on my emac.

I'm looking for a used (ie, cheap) laptop that I can setup with ubuntu to use for wireless net surfing, and an occasional word doc (my wifes a teacher and would do lesson plans and such online).  I've got two eMacs networked now that are our main systems.  I don't need a powerhouse, or ultra reliable, just cheap! :)  That way, she can sit on the porch while the kids play in the yard, and still get some work done....

What would be the minimum specs (hardrive size, ram, processor, ports) on a laptop that would allow:
a: Wireless DSL connections
b: USB ports (for keychain drive to move files to main mac)

I've looked at ebay, but most are pc's and I'm not up on the older (ie 333mhz) processors to know what's ok and what's too old.  

Can anyone give me some parameters that would help narrow my search?

Thanks to everyone

Rob

---

### Post by jpkotta on 2006-03-26
If you want USB and wifi, then look for a laptop with those features.  If the laptop has those features, then they are almost certainly supported.  WiFi might be a bit tricky for very old hardware on Linux, and unfortunately you won't know until you try or search around for others that have gotten it to work on a particular machine.

Beyond that, I'd recommend at least 5 GB harddrive and 128 MB RAM for Ubuntu.  It should run on anything that's 386 or better, but it will be agonizingly slow on such a machine.  Search the forums and the wiki for information on installing on systems with feeble hardware, e.g. [https://wiki.ubuntu.com/LowEndSystemSupport](https://wiki.ubuntu.com/LowEndSystemSupport).

---

### Post by IYY on 2006-03-26
You'll need to check if the specific hardware is compatible (so that you don't have to use ndiswrapper and other hacks). But in general...

I'm running Ubuntu on a 333 MHz CPU, with 64 MB of RAM, 10 GB HD. Gnome works, but is slow as hell. With Fluxbox or IceWM as the window manager, Epiphany as a browser (and Dillo for lighter things) and some other lightweight apps (like xpdf, xmms)... It works well enough for me.

However, I'd say that this is the minimum. Anything with lower specs will just be painful to use. Anyway, I think they are selling better computers at garage sales these days, so I don't think it's a problem.

---

### Post by FoggyMtn on 2006-03-26
Thanks for the quick replies!  That gives me a little info to help in narrowing my search.  The main thing is I just didn't know how old I could go!

Thank Ya'll, and if anyone's got anything else, I'm still listening!

Rob

---

### Post by Sef on 2006-03-27
With a laptop you wouldn't want to too old because if a part breaks, it is expensive to fix it.  I wouldn't get one more than 2-3 years old.

---

### Post by calx on 2006-03-27
I started with 128mb RAM in an old Dell Latitude CPx 500mhz laptop, however running GNOME was painfully slow, swapping one of the the 64mb chips for a 256mb brought that up to 320mb of RAM, greatly improved performance in GNOME, and it's a pleasure to use now. I highly recommend getting as much RAM in the machine as possible.
 
You wont find many laptops with built in wireless at the cheaper end of market. But PCMCIA slots are very common, and you can just buy a cheap Wi-FI card. Look up the model of the card your interested in first, just in case there is a known issue with it, but my cheapo D-link DWL-G630 worked right out of the box.

---

### Post by flammenwurfer on 2006-03-27
If you end up getting a real old laptop that is slow, you could always use Damn Small Linux, it runs very fast on really slow comps.  I used to have an old NEC laptop that with a 233 MHz proc  and 64 MB ram that ran Win XP acceptbably for web browsing and word processing.  So I think pretty much anything you can find will work.

---

### Post by meborc on 2006-03-27
for chosing laptop, try this page [https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam) as a reference before making your final decision... just to see if it 'just-works' or not... and see my sig for the laptop i'm using :)

---

### Post by aysiu on 2006-03-27
Don't forget to consider compatibility, too--not just minimal specifications.

[https://wiki.ubuntu.com/HardwareSupportMachinesLaptops](https://wiki.ubuntu.com/HardwareSupportMachinesLaptops)

---

### Post by evilgold on 2006-03-27
I run simply MEPIS on a dell inspiron 3500 which has a 300mhz cpu and 256mb ram. Its pretty much the same as kubuntu, but more newb friendly (yes even more so then ubuntu). Anyways it runs nicely, so should ubuntu, you probably only need 128mb of ram provided you dont do too much at once. 

For usb...pretty much any laptop with over 300mhz will have at least one usb port. If it has 2 ports then you can get a usb wifi card too. If you want a PC-Card wifi, again, any laptop over 300mhz should be able to run it. 

Check compatability lists for wifi cards. ndiswrapper gives pretty good compatabily for most cards, but linux native supported cards will of corse be a little better.

---

### Post by FoggyMtn on 2006-03-27
Thank's for all the input!  I've been watching on ebay, and it seems that quite a few go thru for $100-200 dollars, I'll just have to do a little more digging and see which ones are listed as compatible.

I've been on macs for a while now, so the old pc's are kind of foreign to me...

Thanks again to everyone, and if anyone has something old,  but still useful for sale, please let me know....

THanks so much

rob

---

