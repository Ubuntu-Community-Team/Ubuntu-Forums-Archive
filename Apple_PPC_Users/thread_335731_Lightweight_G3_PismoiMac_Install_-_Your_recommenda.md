---
title: "Lightweight G3 Pismo/iMac Install - Your recommendations, please"
date: 2007-01-10
forum: Apple PPC Users
---

### Post by gurnemanz on 2007-01-10
Getting ready to try dual-boot installation again with my Pismo Powerbook, I'd like to hear what other users install on their G3/500/500 meg Macintoshes. My iMac is also of this vintage and speed.

Ubuntu or Xubuntu? Server or Desktop or Alternate?

Desktop environment?

SOHO business suite, if not OOo?

Audio editor (equal to Amadeus II or better)?

Screenplay software (equal to MovieMagic or Final Draft)?

Clever hacks/apps for use with Getting Things Done?

Thanks for your thoughts and ideas!

---

### Post by ssam on 2007-01-11
give xubuntu a try.

a lot can be gained from using lighter applications
see [http://ubuntuforums.org/showthread.php?t=62650](http://ubuntuforums.org/showthread.php?t=62650) [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

i'd recommend epiphany instead of firefox, but you might find dillo or lynx (run in a terminal) even lighter.

try abiword, not as fancy as openoffice, but may have all you need.

for writing scripts in openoffice see [http://www.oooforum.org/forum/viewtopic.phtml?t=989](http://www.oooforum.org/forum/viewtopic.phtml?t=989) i am pretty sure it still works in openoffice 2.

also there is a thread about light email programs [http://www.ubuntuforums.org/showthread.php?t=332781](http://www.ubuntuforums.org/showthread.php?t=332781)

---

### Post by dpny on 2007-01-11
I run basuc Gnome on my Pismo. Once you muck with /etc/modules and xorg.conf to get Ubuntu to make the best use of the Pismo's limited VRAM, I find Gnome to be just fine. I have XFCE on my machine but don't use it much, as I find it lacks polish when compared to Gnome.

My only bit of advice would be to put as much RAM in the machine as you can.

---

### Post by handylinux on 2007-01-11
> **dpny said:**
> My only bit of advice would be to put as much RAM in the machine as you can.
This PowerBook will take up to 1GB RAM; Ubuntu requires [128MB]("https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/memory-disk-requirements.html") for a full install. Wouldn't 256MB be plenty, especially for this user's intended "lightweight" setup?

---

### Post by gurnemanz on 2007-01-11
Thank you for your replies so far - please keep 'em coming!

@handylinux, I have 500 meg of RAM. Not a huge pile, but not dinky, either. After a couple weeks of forum scanning, I understand - perhaps incorrectly - it's the older 500 mhz G3 PPC that I should consider my limiting factor. It would be nice to see the old thing move data quickly across its screen. This is the basis of my questions.

Any details of your own installations would be most welcome. 

g.

---

### Post by cwalk on 2007-01-11
I have Xubuntu 6.10 on my G3 366 clamshell. It works fairly well, with minimal laggyness, FF only takes a few secs to load, but once it is going it hogs the processor. OO is slow, but i need to use it for the spreadsheet. Actually, most of the time i use Gnome apps in Xfce without much problems, including Panel things. I had trouble with the sound modules, but that was easily fixed with  /etc/modules.Install  Advice: Use the alternate install CD, burn it at slow speed. Airport card works great for me! good luck

---

### Post by dpny on 2007-01-12
> **handylinux said:**
> This PowerBook will take up to 1GB RAM; Ubuntu requires [128MB]("https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/memory-disk-requirements.html") for a full install. Wouldn't 256MB be plenty, especially for this user's intended "lightweight" setup?

It depends on what he's using it for. I always, always get as much RAM in my machines as possible. But, yes, Ubuntu does have a smaller memory footprint than OS X.

---

### Post by gurnemanz on 2007-01-12
What I'll use Ubunto to accomplish . . . in large part will be to orient myself to a more hands-dirty under-the-hood computing experience. I married into a family of heavy iron programmers, app and system designers. It might give me more understanding of the tech side of their experience.

I'm a writer and a print/electronic media producer. It doesn't look as though sound design and print production are Ubuntu strong points - I'd be glad to be wrong about that.

@cw, forgive my ignorance -  what's 'ff'?

I just recalled it's 628 meg of RAM already on board. Later in the year I may well go for 1 gig, the keyboard is easy to remove.

Tell me more, please, about the apps you use and whether you find K/X/Ubuntu a better OS experience, a more involving technical exercise, or, perhaps, something else entirely.

And what's the deal with these fonts?

g.

---

### Post by dpny on 2007-01-12
> **gurnemanz said:**
> Tell me more, please, about the apps you use and whether you find K/X/Ubuntu a better OS experience, a more involving technical exercise, or, perhaps, something else entirely.

And what's the deal with these fonts?

g.

Personally, I use Gnome. I tried Xubuntu, but I find XFCE to be lacking some polish. A friend of mine nailed it for me. He said XFCE is great for monitoring servers but not great for a daily desktop. As for the fonts, check out my reply [here](http://www.ubuntuforums.org/showthread.php?p=2001789#post2001789).

---

### Post by handylinux on 2007-01-12
I'm new at Linux, so can't speak from much experience, but am gathering information like you.

> I have 500 meg of RAM. Not a huge pile, but not dinky, either. After a couple weeks of forum scanning, I understand - perhaps incorrectly - it's the older 500 mhz G3 PPC that I should consider my limiting factor.
512MB (RAM comes in binary numbers) should be plenty for anything this PowerBook is comfortably capable of doing, in OS X as well as Linux. I wouldn't put anything past OS X 10.3.9 on this PowerBook. (I have one myself, it was my primary computer for a couple years; I tried upgrading it with a G4 CPU and put 10.4 on it, but it was clearly pushed -- very unpleasant fan running all the time -- so I returned it to G3 and 10.3.9.) If there's anything you want to do for which 500MB RAM is insufficient, what you really need is a faster computer. If you're serious enough about Linux that you find you need more than this, you should probably get a new(er) x86 computer instead to run Linux without limitations. (I have a new MacBook Pro arriving today, and plan to put Ubuntu on a partition there.)

> I have Xubuntu 6.10 on my G3 366 clamshell. It works fairly well, with minimal laggyness, FF only takes a few secs to load, but once it is going it hogs the processor. OO is slow, but i need to use it for the spreadsheet
Just as I wouldn't put Mac OS X 10.4 on a 500MHz G3 (though some do; I presume they don't mind slow performance), I'm guessing (again, though I don't yet have the experience to back it up) that a rule of thumb might be to use Xubuntu rather than Ubuntu on a Mac under 500MHz. However, this poster doesn't note how much RAM his iBook has; since less RAM = more pageouts to disk, amount of RAM has a decided influence on performance, especially on slower computers. Again, however, more than 512MB would probably be pointless.

"FF" = Firefox, I presume. AbiWord is a word processor, OO is an office suite (WP, SS, presentation, draw). I think I've seen another office suite available (in the Kubuntu package?), but OO is definitely the standard.

For dual booting, most convenient to install Ubuntu on first partition, set OS X in System Preferences: Startup Disk; then you can switch easily: press D during startup for Ubuntu, press nothing during startup for OS X.

---

### Post by samden on 2007-01-15
I run Xubuntu dapper on my 500Mhz iMac G3 with 192Mb RAM. I dual-boot this with OSX 10.3.9, which runs fine with most things although MS Word crashes a bit (fine with me, I can stick with OpenOffice.

I am still having problems, new install and I am not used to Linux. But I like Xubuntu. I have tried the Ubuntu live cd on my G4 and didn't like the feel of it at all, I like how in Xubuntu you can right click on the desktop and bring up the applications menu, quicker than finding it on the panel.

Out of interest, I deleted the top panel and set up the bottom panel similar to a Windows panel, with the applications menu on the left. Then I made it automatically show and hide, like the OSX dock - taking the best of both worlds from Windows and OSX and putting them into Linux! I assume you can do the same with Gnome, but I like how this allows me to optimise the small amount of screen space on my iMac.

Xubuntu can be easier to install on a low-spec machine than Ubuntu - in my case the Ubuntu live cd won't run on my G3 but the Xubuntu one will. You can then download the Ubuntu desktop as well if you prefer Gnome.

Just my impressions as a new user....

---

