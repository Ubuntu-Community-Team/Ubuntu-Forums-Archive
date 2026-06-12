---
title: "Help with ubuntu on iBook G4"
date: 2007-01-06
forum: Apple PPC Users
---

### Post by bramo126 on 2007-01-06
I have an iBook G4 running Tiger (i don't think that matters), and i just cant seem to boot from a CD. I turn the computer off, turn it on, quickly put the ubuntu CD in and hold down C but nothing happens, it just goes to the normal Tiger startup. I have 2 ubuntu CDs, 1 I burnt myself, and another i got from the ubuntu shipit, neither of them work. I have tried Alt, or command-option-o-f, but they both ask for a password I dont know. Does anyone have a solution, I really want ubuntu on that laptop!?

---

### Post by trash on 2007-01-06
it's been a while and don't remember if it works but try selecting the Ubuntu cd in the startup disk in system preferences.

---

### Post by handylinux on 2007-01-06
1) If you insert the Ubuntu CD while running in Tiger (Mac OS X 10.4.x), does it appear on the desktop? If it doesn't appear, either the CD or the optical drive is bad. 

> ... try selecting the Ubuntu cd in the startup disk in system preferences.
This won't work, as Mac OS doesn't recognize Linux as a bootable System.

2) If the CD does appear, what is its title? Mine says "Ubuntu_PowerPC_Edgy". You need a **PowerPC** Ubuntu CD to work on a PowerPC Mac.

3) If the CD does appear, and it's a PowerPC Ubuntu CD, you should be able to restart with the C key to run the iBook from the CD. HOWEVER ...

> I have tried Alt, or command-option-o-f, but they both ask for a password I dont know.
A Clew! Sounds like the iBook may be protected by an Open Firmware Password. I have no experience of this myself, but a search on the Apple Support site found "[**Setting up firmware password protection in Mac OS X 10.1 or later**]("http://docs.info.apple.com/article.html?artnum=106482")", which informs:

"Open Firmware Password Protection:
Blocks the ability to use the "C" key to start up from an optical disc.
...
Blocks a reset of Parameter RAM (PRAM) by pressing the Command-Option-P-R key combination during startup.
Requires the password to use the Startup Manager, accessed by pressing the Option key during startup (see below).
Requires the password to enter commands after starting up in Open Firmware, which is done by pressing the Command-Option-O-F key combination during startup."

So, assuming you came by this iBook legitimately ;) you need to reset the OF Password function. From hints in the above document, plus a [forum at MacInTouch]("http://www.macintouch.com/securityfirmware.html"), seems like there are a couple ways to do so:

(1) Force a reset of the PRAM. You can't do it the normal way (opt-cmd-P-R during startup), but you can remove power from the PRAM chip. In most Macs this is done by disconnecting the internal battery, but the iBook doesn't have an internal PRAM battery, so you can simply disconnect AC power and remove the main battery and let it sit for an hour or so (probably even less time will do it). Then put the battery back in, connect AC, and start it up and check the date/time; if it's been reset to 1956 (or 197x) the PRAM has been reset, which apparently should remove the firmware password.

Or (2) Apparently removing a RAM card can do it? You can try removing the 2nd RAM card (if any -- the iBook has some RAM on its motherboard, and a slot for a second card); a take-apart manual can be found at [iFixIt]("http://www.ifixit.com/cart/catalog/").

Apple's [iBook support page]("http://www.apple.com/support/ibook/") might also be helpful.

Thanks for spurring me to learn some Mac lore I didn't know.

---

### Post by bramo126 on 2007-01-06
Thanks for your help:) , too bad i can't do any of that stuff because it is a school laptop, and i would get in trouble if i did any of that, but thanks a lot anyway, I would still be trying and failing, wasting my time without your research :). The administrator obviously blocked that, i just didn't know you could.

Thanks Again, Bram

---

### Post by handylinux on 2007-01-07
Um, well, I guess this is a good example of what Firmware Password Protection is for. Hope you find another computer you can use for Ubuntu; an Intel PC is probably preferable, as there are some limitations to using Ubuntu on PowerPC computers.

---

### Post by cvmiller on 2007-01-07
> **handylinux said:**
> Um, well, I guess this is a good example of what Firmware Password Protection is for. Hope you find another computer you can use for Ubuntu; an Intel PC is probably preferable, as there are some limitations to using Ubuntu on PowerPC computers.

What limitations are you thinking of? I am now running Ubuntu (Dapper & Edgy) on 3 PPC Macs, and aside from closed source solutions (such as Flash), it works pretty well.

Craig...

---

### Post by handylinux on 2007-01-07
> **cvmiller said:**
> What limitations are you thinking of? I am now running Ubuntu (Dapper & Edgy) on 3 PPC Macs, and aside from closed source solutions (such as Flash), it works pretty well.
Those are the limitations I was thinking of. In my so-far brief experience of Ubuntu on an iBook G4, it does indeed run well (though it's nowhere near as polished as Mac OS X), but the lack of such universally-used capabilities as Flash would prevent me putting it on a computer for a non-expert client, who just wants a computer they can use (like the Mac) without thinking about it.

I'm interested in learning more about Ubuntu so I can help PC-using friends -- who aren't likely to be interested in moving to the Mac, for whatever reason -- escape from their "previous condition of servitude" to Windoze. For that purpose it seems Ubuntu will serve well, but for PowerPC Macs certain key lacks like Flash, and other problems on "Old World" Macs that won't run OS X (e.g. PowerMac 8500) continue to relegate Ubuntu, like other Linuxes, to the hobbyist (a.k.a. "geek") community.

Not complaining, mind you; that's just where it stands. I'm not really looking for Linux to supplant Mac OS, but I would like to see it replace Windoze as the worldwide standard (someday? we can hope). Apple is a corporation, true, but it is still mostly about "insanely great" (and remaining a niche market is the best thing that's happened to Apple, keeping it honest); while Micro$oft is entirely about greed, and a very bad candidate for "absolute power". In an open-source, Linux computer world, Apple could still prosper by offering its traditional commitment to quality. And Microsoft would have to compete by offering a quality product, rather than its present, Tonya-Harding tactics (kneecap your opponent so you won't *have* to compete).

The new Intel-based Macs, OTOH, should run Ubuntu as well as other PCs -- once certain small problems are addressed -- but there's really no reason for the average user to do so, since it's safe to assume they got a Mac because they wanted a Mac. Five years from now Ubuntu might be a good choice for a then-aging Intel Mac no longer capable of comfortably running the latest OS X (Smilodon?).

---

### Post by aNTwNHs on 2007-02-04
The only problem I encountered by now was no official java support. But IBM Java worked just fine for me. Even for developing with netbeans:P
It's just a week since I switched the iBook to Ubuntu edgy,.. so maybe more problems will arise. I'm trying to keep track of them [here]("http://antonis.wordpress.com/2007/01/30/ubuntu-on-a-macintosh/"). Ok flash is a problem, but not so serious to prevent somebody from switching. I really hate flash based sites anyway:P

---

