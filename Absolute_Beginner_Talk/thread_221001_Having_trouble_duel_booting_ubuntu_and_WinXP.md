---
title: "Having trouble duel booting ubuntu and WinXP"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by Atronite on 2006-07-22
Hi there,

I'm trying to make my satelite a15 toshiba laptop be able to duel boot ubuntu and winXP. 

Now, I've been using ubuntu for about 3 months now as a friend of mine really recommended it and I thought I'd take the plunge and try it out with my friend helping me out as needed.

Well, after daper drake came out, I decided (after backing up my files on an external drive) to reformat the computer and do a fresh install of daper drake. So I do that, and install it, and I partition my drive like so:

20 gigs into the ntfs partition (for win xp), (hda1)
5 gigs into the ext3 paritions (ubuntu)(hda2)
11 gigs into the fat32 partition (which is shared) (hda4)
the rest into the linux swap (hda5)

(its a 40 gig hard drive)

After doing a fresh install, I get the disk that came with my toshiba laptop to install windowsXP and restore the computer back to factory settings. 

So now I have both winXP and ubuntu installed, and the ubuntu side can even access the windows side and stuff.

The problem tho, is that it keeps booting the ubuntu side, and I'm just wondering, how do I make it boot into the windows side whenever I want to? What system configurations do I need to edit?

I apologize if this was talked about in another thread, but I tried googling the answer but the answers weren't all that helpful to me for my particular situation, and I'm still pretty new to ubuntu. Also, my friend who knew some stuff about linux wasn't sure either.

Any help is appreciated.

---

### Post by DSn0wMan on 2006-07-22
In my experience it solves alot of problems to install windows before linux on any dual boot setup.

---

### Post by PriceChild on 2006-07-22
Add the following:

# title        Windows XP
# root        (hd0,0)
# makeactive
# chainloader    +1

without hashes to your /boot/grub/menu.lst

---

### Post by Atronite on 2006-07-23
thanks a ton guys

works good now. Five Stars to you guys.

:KS :KS :KS :KS :KS 

:mrgreen:

---

