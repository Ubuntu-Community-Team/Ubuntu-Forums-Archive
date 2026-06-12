---
title: "Questions about upgrading to Gutsy"
date: 2007-10-18
forum: Apple PPC Users
---

### Post by rhetoric on 2007-10-18
I finally have everything (except flash videos inside the browser are buggy, and the wireless driver sucks) that I need/want working in Feisty. What will I gain by upgrading? What do I stand to possibly lose? How difficult is the process without breaking my current desktop setup? I apologize for the totally ignorant questions. Thanks :)

---

### Post by roazena on 2007-10-18
Tell us more about your system first. From what I can see so far, the stuff that was broken in Feisty is still broken in Gutsy, and some of it will have to be re-fixed post-upgrade.

---

### Post by rhetoric on 2007-10-18
I'm completely new to linux so... I don't really know what this upgrade involves. I'm wondering, generally, what will the process be like and what could potentially break?

edit: also how does being a ppc user factor into this, if at all?

---

### Post by Auria on 2007-10-18
Updates with ubuntu are often problematic... back up everything first

if you have everything working i'd say stay like that for at least now, anyway gutsy doesn't seem too stable

---

### Post by rhetoric on 2007-10-19
> **Auria said:**
> Updates with ubuntu are often problematic... back up everything first

if you have everything working i'd say stay like that for at least now, anyway gutsy doesn't seem too stable

Yea pretty much everything I need is working fine atm, and the glitches that exist are quite tolerable. If it can be problematic to upgrade, and I don't *need* to then I'm going to wait.

Thanks much :)

---

### Post by ag0g0girl on 2007-10-19
Unfotunately, my sound has never worked in Fiesty, and I was really looking forward to the gutsy release.  Too bad there isn't much good news about it on this forum.  

This PowerPC image isn't on the main alternate CD list from the main download page. Does that mean that the PPC isn't ready yet?

My Fiesty doesn't even boot anymore.  I need my ubuntu!!

---

### Post by rhetoric on 2007-10-21
> **ag0g0girl said:**
> Unfotunately, my sound has never worked in Fiesty, and I was really looking forward to the gutsy release.  Too bad there isn't much good news about it on this forum.  

This PowerPC image isn't on the main alternate CD list from the main download page. Does that mean that the PPC isn't ready yet?

My Fiesty doesn't even boot anymore.  I need my ubuntu!!

I think the alternate CD image should be on the ftp even if it isn't shown on the website.

---

### Post by z0mbix on 2007-10-23
Yes I would advise you NOT to upgrade to Gutsy on PPC. It's ******* terrible at the moment. I've abandoned it. Despite a successful dist-upgrade Gutsy was a mess so I did a fresh install. That didn't boot because of the ide_core problem. Fixed that, then GNOME takes about 3-5 mins to load. When it does a get a "gnome-settings-daemon" error saying it can't run so the interface looks shite. Network Manager no longer works. When I connect my USB hard drive to restore my data, the iBook hangs needing a powerdown.

I've ran Ubuntu on my iBook (G3, 800MHz) since I bought it before Warty was released and it's been great, but it seems like Ubuntu no-longer give a **** about PPC users. As soon as the new Macbook comes out after Leopard's release I'm getting one and sticking with Leopard.

---

### Post by Auria on 2007-10-23
> **z0mbix said:**
>  As soon as the new Macbook comes out after Leopard's release I'm getting one and sticking with Leopard.

but that one won't be a PPC so your claim no longer holds :)

---

### Post by wickstopher on 2007-10-30
I would have to agree with z0mbix.  Gutsy is pretty decent on my desktop PC, but I tried doing a fresh install on my G4 Titanium PowerBook (after a failed attempt at a network upgrade) and ran into nothing but problems.  For starters, the installation from the alternate install CD took about 2 hours.  The liveCD for Gutsy simply doesn't work.  You get a white screen with some rainbow highlights and that's it.  Things that worked OUT OF THE BOX on a clean Feisty PPC install (such as my Airport card, suspend/hibernate with laptop closed) weren't working, and on top of that GNOME was excruciatingly slow, and I had to mess around with busybox just to get GNOME/X to start up.  The sound issue is still not fixed, so you'll still have to roll-back to an older kernel if you want sound.  It looks like Ubuntu may actually be giving up on PPC, because for a release as anticipated as Gutsy to have such poor implementation on the PPC platform is simply unacceptable.  For now, I'm reinstalling Kubuntu Feisty PPC from scratch.  Tried YDL and didn't like it.  Maybe I'll give Debian Etch a shot.

---

### Post by sulobanks on 2007-10-30
I'll have to agree with the others on my disappointment with Gutsy.  However, I was equally as disappointed with Feisty on my ibook G4.  But after the first few months, the updates fixed the problems.  I expect the same to happen with Gutsy.  I did a dist upgrade to Gutsy after a clean install of Feisty, since the Gutsy live cd wouldn't boot.  It failed with all sorts of warnings that I might have an unusable system.  Most things have been perfect since.  Very weird, but I'll take it for now.  Compiz fusion definitely outperforms the compiz that came with Feisty, And my main motivation was to check out OpenOffice 2.3.  One of my jobs requires me to make cool charts from research data.  So far so good for me in most areas, but there are a few things.  Sleep doesn't work at all, and gnome seems a little more sluggish than it has in the past, even with desktop effects turned off.  Still tinkering with those things, and I'm still not convinced I'll stick with Gutsy.  May go back to Debian Lenny for 3 or 4 months and try Gutsy again then.

---

### Post by vijaym on 2007-11-02
my attempt at upgrading using the livecd failed totally. 
discovered and went beyond the white screen problem, the ide_core problem etc.
But it supposedly installed it did all the things, like what keyboard, time zone etc, then froze. Tried this about 10-15 times. 

Freezing was erratic as it happened at different places. Damn thing even reformatted my partitions and then froze!! 
Even tried the network install. That failed ...

lucky that my data was backed up. But lost all the settings and other software on the system. 
Then went back to Feisty and reinstalled it. That worked like a dream. Just had to go back to updating all the Feisty software - chowed my bandwidth. 
So back on Feisty which seems not to have the ide_core or the white screen problems.

so i am a tried to install gusty user. 

Vijay

---

### Post by sportjunkie on 2007-11-07
Just want to give my2cents here and give Gutsy PPC some credits.
I used Debian on my iBook G4 for more than a year and after upgrading from stable to testing I good a hole bunch of problems (freezing X, second screen got to light and couldn't be adjusted, ...)
So I decided to give Gutsy a shot. The installation took a while but I had no errors. 
- Wireless with NetworkManager works out of the box.
- After I disabled compiz X is reasonable fast.
- To activate sound I had to load the snd-powermac module

The only issue I have right now and that is a big one for me, is that my keyboard doesn't work reasonable. I have no brackets or "at" symbol. Hope to find a solution today.

---

### Post by ulissesroc on 2007-12-01
I wanted to install ubuntu just to have battle for wesnoth working on my ibook .The mac version wasn't working. Too bad, it works on my older powermac, and I have to be in Italy for one month, this meaning I can't take the powermac, but just the ibook. So, ubuntu was needed.

I have upgraded from feisty to gutsy, just because the gutsy cd was corrupted. So I used my old feisty cd, and then did distro upgrade.

Everything seemed so fine, thanks also to

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

But....the sleep doesn't work. That's unacceptable, I have to downgrade to feisty, since I really need a computer to be able to go to sleep and to wake up reasonably.

I hope that time will fixed it (or, I hope that with time someone will fix it).

---

### Post by fpuhan on 2007-12-03
> **rhetoric said:**
> I finally have everything (except flash videos inside the browser are buggy, and the wireless driver sucks) that I need/want working in Feisty. What will I gain by upgrading? What do I stand to possibly lose? How difficult is the process without breaking my current desktop setup? I apologize for the totally ignorant questions. Thanks :)
This is probably more of a rant than a reply, so I apologize in advance.

I first started using Ubuntu Edgy 6.10 on a dual-boot G4 Powerbook (1.2GHz, 80GB, 512MB) that I bought used, specifically to use as a "sandbox" computer.

After installing Edgy, I had to work a while to get my wireless WPA-PSK network working, which was critical for me. But finally it all came together, and I wound up traveling with the computer and using it at hotspots and Internet cafes (and even at the Apple Store in Las Vegas!). I upgraded to Feisty, and still had no problems.

Then came the day I upgraded my Mac OS X to Leopard, which wound up "breaking" my dual boot (see my threads about this in the same forum).  I wound up downloading and burning the Feisty CD. I did the same with the Gutsy CD.  Even the Alternate CDs.

Starting from "scratch," I installed Feisty, configured Yaboot (I like the Mac OS as the default) and started to re-configure.  While I was attached via wire I upgraded to Gutsy.

Since then, not only can I not get my Wi-Fi WPA working, even my Ethernet connections are slower than a dial-up connection.  I am getting messages about out-of-date repositories, and not being able to locate google.com.  WTF??

I've removed nm-applet, configured my network numerous times, and still my Ubuntu acts like a recalcitrant school kid being called in from recess.  Ugh.

I'll continue to play with this for a while (I'm probably going to attempt another "clean" install of Feisty), but right now there is no way I'm giving up my Mac OS X for Linux...

---

### Post by ulissesroc on 2007-12-04
Well, do you fetch the firmware for you airport? Then it works, at least in my ibook.

But, as I said, I ran back to feisty. There's nothing so important to justify the upgrade, now, and, plus, the sleep doesn't work!!!

---

### Post by wickstopher on 2007-12-05
I just wanted to say that I was having a lot of similar issues with Gutsy on my G4 TiBook.  I have downgraded to an earlier kernel, 2.6.17-11, and it seems to have fixed the problems.  This was the fix offered for Feisty on the TiBook to get sound working (it's still the only way to get sound working on these machines, as far as I am aware, even in Gutsy), and it seems to have fixed the sleep issues with the laptop as well.  I currently have a very functional installation of Kubuntu Gutsy (I even have some features of compiz-fusion working well), but as a previous post said...there's no way I'm completely giving up OS X for linux any time soon on that laptop.  It is fun to have both installed, but there are certain things that just don't work in linux, like S-Video out.  I'm sure there's a solution, but it's not worth the time, considering it works great in OS X.  And there are other things that just don't work that well, like Flash.  And, based on what I've seen deteriorate between the PPC releases of Feisty and Gutsy, things aren't getting any better for PPC Linux users.  Only time can tell that one, however.

---

### Post by rhetoric on 2007-12-05
Well, since my thread keeps getting bumped I guess I'll report on my situation.

I've decided to stick with Feisty indefinetely. At the moment I have a fully functional laptop (minus "hibernate" but suspend works), with all the software and functionality I need. With the amount of trouble people are reporting with Gutsy, why bother?

If I do decide to upgrade, I'll post my experience here for others pondering the jump.

---

### Post by Doctor J on 2007-12-07
> **wickstopher said:**
> Tried YDL and didn't like it.  Maybe I'll give Debian Etch a shot.

I have to agree that YDL isn't too useful.  The number of available packages was ridiculously small, Fedora repositories never worked for me, and i couldn't get SDL working...  Their support mail list was none too helpful, either.

Would installing Debian 4.0 be significantly different from Gutsy with backports turned on?  I though that Debian was upstream from Ubuntu.

Gentoo seems to be up to date, though not even slightly user friendly.  Rather than shielding us from the intricacies of the kernel, it encourages the user to wallow in them.  It also seems to be built on the principal of "eat your spinach, or else!".  I tried to create a non-administrative user for playing games and such.  The system kept rejecting all passwords i was likely to remember.  The whole procedure was just too fussy.

Has anybody here tried OpenSUSE?

---

