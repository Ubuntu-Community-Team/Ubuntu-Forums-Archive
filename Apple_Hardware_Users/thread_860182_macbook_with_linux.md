---
title: "macbook with linux?"
date: 2008-07-15
forum: Apple Hardware Users
---

### Post by Cew27 on 2008-07-15
hey guys the time has come for me to get a new notbook and i have been thinking about a macbook, however i am wondering how linux runs on it, i like to distro hop and hardware support is essential. i currently run slackware, arch and ubuntu. how would these run on a macbook? also can i boot live cd's and live usb's on a macbook and if so how?

---

### Post by Cew27 on 2008-07-15
oh and does anyone know if it will work with the webcam

---

### Post by flaggh on 2008-07-15
Everything on my macbook works, (bluetooth, webcam, wifi, etc.) and even though it is an older macbook 2,1 and there has been plenty of time for everybody to figure out how to get the hardware working, it still took quite a bit of effort to get everything working.  For example, I still have to reinstall madwifi everytime there's a kernel update and sometimes for no reason that I can see.  If you're going to get a NEW macbook, you may have to put in quite a bit of effort to get everything working since the hardware may not be as easy (<-insert slight sarcasm here) as mine.  Overall I'm extremely happy with the way it runs on my machine.  Aside from some quirks it runs great and I use Ubuntu 99% of the time on my dual boot.  If you are going to buy a macbook I would suggest buying a slightly older model.  Read through the ubuntu macbook wiki a few times and get an idea for what you'll need to do before you make any final decisions.

---

### Post by wepalm on 2008-07-15
> **Cew27 said:**
> also can i boot live cd's and live usb's on a macbook and if so how?

To boot a live CD hold down either the 'alt' key while starting up(right after you press power) and use arrow keys to navigate to cd and select it by 'enter'.  You can also hold down the 'C' key depending on your model.

---

### Post by Cew27 on 2008-07-15
i can only get a new model. is it worth getting a macbook over a normal laptop?

---

### Post by issih on 2008-07-15
Live cds are fine, newer macs really really don't like booting from usb, its nigh on impossible to make it work.

I'm on a santa rosa macbook (3.1 I think :s) and nearly everything works ok if you follow the macbook wiki advice, haven't really messed with the webcam, but plenty of people seem to have that working, everything else is fine, display, keyboard, wireless, touchpad (including two finger scrolling), bluetooth, all working fine. Sound works, but I'm not happy with the quality compared to osX at all, its really weedy, I have a suspicion that there might be a 3rd speaker not being activated, not sure about that though.

I'm not sure how well the newer penryn based ones work, but the macbook pro wiki might be a good place to look as the underlying hardware is very similar indeed now.

As to whether it is worth it, thats very subjective. I really like OS-X as something to use. Its soothing how well it works, but if I want to mess about I use ubuntu. For me OS-X is for using when I just want to browse the net, listen to music and write a few documents....Everything works, and the power management is so good it totally changes how you use your computer. If you are likely to use OS-X then its probably worth it, if not, then to be honest possibly not, they are overpriced.

Basically the pro's are OS-X, good battery life and style (if you like it :)), and the cons are the price. Linux wise its ok, but not great, something like a thinkpad probably has better supported hardware. In the end, its up to you I'm afraid....I like mine though...lots

P.S. I just realised that I'm sitting here writing this on my macbook dressed in blue jeans and a black long sleeved t shirt top :s Mr Jobs is clearly assimilating my brain somehow, my only saving grace is that I am currently running ubuntu...

---

### Post by cyberdork33 on 2008-07-15
> **Cew27 said:**
> i can only get a new model. is it worth getting a macbook over a normal laptop?Not for _just_ linux, imo. Get a mac if you want to use OSX (at least some of the time), otherwise it just makes sense to stick with something more compatible.

Here is the wiki for the newest MacBook:
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

---

### Post by Cew27 on 2008-07-15
what about student discounts i have been hearing about?, i really want a mac for the battery life and good hardware 
but i wont use osx much i dont think maybe for photoshop

---

### Post by issih on 2008-07-15
I think the current deal here in the uk is a free ipod, which will probably last until the new term starts. Plus if you are at university, access the apple store for education and you get about a 10% discount

[http://store.apple.com/Catalog/uk/Images/routingpage.html](http://store.apple.com/Catalog/uk/Images/routingpage.html)

Makes things a bit less pricey at least.

---

### Post by vegetali on 2008-07-15
I have quite a different feeling than the guys above. That's probably due to the fact that I was not a mac fan and just got my macbook from my company. I have the latest macbook. You can get more or less everything to work: audio (but you will have to do some tweaks), wifi (tweaks also required), touchpad (tweaks required), webcam (tweaks required, it works but not with skype).

I single booted debian and then ubuntu for a while, and the experience is not painless. Boot is slower, and it took about 15 seconds with grey screen before GRUB could load. Moreover I use skype intensively, and the output audio quality was certainly lower than my previous very cheap laptop. Since also I could not make the webcam work in skype, I decided to reinstall MacOS X and dual boot ubuntu. This is not completely painless; beyond a boot bug (easily resolved by updating partition in rEFIt), you cannot make too many partitions or the rEFIt stuff will go crazy. In particular, you should choose only one distro. I also dissugest you to creat a swap partition (not a problem with 4GiB). Just now, after a kernel update by the official hardy repo, rEFIt freezes when I chose linux (before loading GRUB, is not a kernel issue). So it is quite painful and you should really take into account some hours in troubleshooting.

I do not like MacOS X at all. While skype works much better here and webcam is ok, everything else sucks (but the touchpad, I love it and after minor tweaks it works even better in linux, as you can introduce some extra combos). I could give some reasons for this statement, but this is not a MacOS forum. Anyway, if you are used to linux, I hardly believe you can switch to MacOS for regular usage. It's just inferior.

The hardware itself is not bad. The laptop is reasonably light though quite sensitive. It misses microphone input (integrated mic is not bad, but certainly lower quality), and some extra USB plugs.
Battery has pretty good duration, but I never tried other new intel laptops.

If I were back, I would never accept a Mac from my company and rather go for a cheaper 13 inch laptop: I would have better hardware (for less money), and do not spend time fixing all these issues.

---

### Post by flaggh on 2008-07-15
Skype works with my webcam on my macbook.

I do not have a swap partition, but instead use a swap file.

I agree that my touchpad works much better in linux than it does in OSX.  It is very configurable and gives me all the functionality of a three button mouse with scroll wheel.

Like I said, I use linux 99% of the time.  It takes about 30 seconds for it to boot, which is about 15 seconds longer than it takes OSX to boot up.  I've always been a PC user and this is my first mac.  OSX is fine for simple stuff.  It's nice to have a conventional operating system when I need it and I've had enough of Windows.  If you want a computer that ubuntu will install flawlessly on and be up and running in 30 minutes, a macbook is not for you.  I run 64-bit Hardy and it took me a week to sort out all the kinks that come with running a 64-bit kernel and a macbook, but I'm very happy with the way it turned out.

---

### Post by Cew27 on 2008-07-15
ok cheers for the opinions guys, i think ill stick with a normal laptop

---

