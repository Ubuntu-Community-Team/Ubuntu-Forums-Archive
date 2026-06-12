---
title: "been thinking a lot lately..."
date: 2008-02-10
forum: Apple Intel Users
---

### Post by sethfc on 2008-02-10
So,
I have Ubuntu 7.10 on my quad core desktop.  I've used 32 bit and 64 bit, and I feel pretty familiar with linux now (well, familiar enough).  I really love how "different" linux is.

Anyway, I have a MacBook (C2D, 1GB ram, WIreless N, etc).  I upgraded to OS X Leopard.  It is merely 'OK' in my eyes, and I'm becoming more upset at how bloated mac is becoming.

I'm looking to be convinced that ubuntu for the macbook would be a good solution.  My only worries are below:

-Something easy like iMovie: i'm not an "advanced" video editor, but iMovie was WAY easy to plug in most any video camera and upload video.  I liked this.  Is there some proggy in linux/ubuntu that is almost as easy??

-Wireless network browser.  Is there an easy interface that i can install with gnome or something that makes it easy to browse networks/wireless networks/monitor the wireless signal, etc?

-I have the wireless N card in here, but i had to use a piece of software from the wireless N apple router to "unlock" it.  Will ubuntu automatically utilize it's "N" capabilities?

-I hear bluetooth for the mac/ubuntu kicks ***, so I wont worry about that.

LMK if you guys have answers to my questions.  I'd really like to be one of the few on my campus that is running an open source distro on my mac, for my sake, and for the :cool: factor =p

thanks!
-seth

---

### Post by bsantos on 2008-02-10
> **sethfc said:**
> So,
I have Ubuntu 7.10 on my quad core desktop.  I've used 32 bit and 64 bit, and I feel pretty familiar with linux now (well, familiar enough).  I really love how "different" linux is.

Once you change to Linux (and I'd say *BSD too) and get to know it, it's workings, how the development process happens, the community which can have a voice in how programs evolve and how/what distros package software, it really is something different. :)

> **sethfc said:**
>  Anyway, I have a MacBook (C2D, 1GB ram, WIreless N, etc).  I upgraded to OS X Leopard.  It is merely 'OK' in my eyes, and I'm becoming more upset at how bloated mac is becoming.

> **sethfc said:**
>  I'm looking to be convinced that ubuntu for the macbook would be a good solution. 

Some of us are mostly happy using Ubuntu natively. My only issue has been the sound card distortion, which is addressed by the newer alsa libs still needing packaging for Hardy, so you may get bitten by this issue in Gutsy.

> **sethfc said:**
> My only worries are below:

-Something easy like iMovie: i'm not an "advanced" video editor, but iMovie was WAY easy to plug in most any video camera and upload video.  I liked this.  Is there some proggy in linux/ubuntu that is almost as easy??

The cinelerra fork/rewrite is promising to change the video editing panorama, but it may be too advanced for your needs (too complex). I've been using Kino and have been pretty happy with it. It doesn't have that simple timeline gui, text and transitions aren't live at least as on iMovie, you have to re-render them if you need to change them, but feature wise I believe it is close to iMovie. Although it doesn't have multitrack video, it has chroma transitions, so you can even give a shot at green/blue screen work with it, among other goodies. [http://kinodv.org]("http://kino-dv.org")

It seems to take longer to convert the videos to dv than iMovie though.

> **sethfc said:**
>  -Wireless network browser.  Is there an easy interface that i can install with gnome or something that makes it easy to browse networks/wireless networks/monitor the wireless signal, etc?

I've been happy enough with the default NetworkManager, but ymmv, some people use other software, search in the forum if the default NetworkManager doesn't fit your needs.

> **sethfc said:**
>  -I have the wireless N card in here, but i had to use a piece of software from the wireless N apple router to "unlock" it.  Will ubuntu automatically utilize it's "N" capabilities?

You'de have to check N support on the madwifi driver. I think the developers focus is on dropping the binary hal, so for now adding features to the driver may be slower until the open source hal is usable on most chips. I don't know if the current trunk code supports the N specification for the MacBook card, I just use G, so you'd better check out in madwifi's site.

> **sethfc said:**
> -I hear bluetooth for the mac/ubuntu kicks ***, so I wont worry about that.

I also don't use bt for anything right now, so I can't tell how's the current support, but I believe there's an effort to better support bt, but that's something I don't follow, you'd have to check the blueprints for hardy and the roadmap for it or other distros with releases in the near future.

> **sethfc said:**
>  LMK if you guys have answers to my questions.  I'd really like to be one of the few on my campus that is running an open source distro on my mac, for my sake, and for the :cool: factor =p

I can't get by without Linux, even if osx has an underlying unix layer, it is not the same, I feel free using Linux, like I don't feel using any other OS (never got well into *BSD but they're are also a good alternative). It hurts when you're using a stable distro but want the next version of some software, but there are no packages available (situation partly solved by the wonderful work of backporters, getdeb and volunteer packagers around the web).

The most important is that you get your job done and feel good using your machine, if you can add to that using foss, it's even better!

And for those always asking why buy a MB to use Linux, in my case was to have contact with osx, and since the prices were close to similar bios laptops, for it's good looks, the magsafe connector, the magnetic lid...

> **sethfc said:**
>  thanks!
-seth

Good luck! :-)

---

### Post by steveneddy on 2008-02-10
> 
been thinking a lot lately...


Really?

---

### Post by sethfc on 2008-02-10
bsantos - thank you! good info, hopefully i can get some other POVs before I decide what to do!

steve - indeed, i have.

---

### Post by handy on 2008-02-11
Why not dual boot?

If you find that you are happy with Ubuntu (or whatever Linux based OS) then shrink your OS X partition down as small as you can (after you delete the unnecessaries) & just use your OS X for EFI firmware updates.

---

### Post by Salpiche on 2008-02-11
> **handy said:**
> Why not dual boot?

If you find that you are happy with Ubuntu (or whatever Linux based OS) then shrink your OS X partition down as small as you can (after you delete the unnecessaries) & just use your OS X for EFI firmware updates.

that's what I have always done, my iMac has OSX on a 20gb partition and Ubuntu on the other 230 gb,yet 95% of the time I use Ubuntu and the space taken by OS X does not hurt me

if you have the space I would say to do just that play it safe and keep it simple

---

### Post by russo.mic on 2008-04-21
I've got hardy rc installed on my MBP right now, and it pretty much kicks ***.

Just my 2 cents.

Russo

---

