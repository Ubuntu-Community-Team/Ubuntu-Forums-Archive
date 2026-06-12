---
title: "Is it just me?"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by therunnyman on 2006-04-05
Hi all,

The way I learned to use Windows back in the day was to break it, systematically, if it wasn't already broken.

With Ubuntu, everything works - seriously, everything.  Didn't have to install third party drivers for the RAID, my onboard NIC was recognized, a USB sound device works fine, a USB printer I hooked up yesterday runs like a top.  Edited fstab and GRUB with no problems, have cron doing its thing, locked the machine down to the best of my ability, ran Nessus, and so on.  Granted, this is only my third week with Ubuntu...is anything ever going to break?  Or should I switch to the Beta?

I'm a little worried.  How am I supposed to learn anything about Linux if nothing breaks, and I can't break stuff?

therunnyman

---

### Post by taurus on 2006-04-05
If you want to break your Ubuntu, play around with root and eventually, something will go wrong and you will be sitting there figuring out what's wrong with it!!!  :twisted:

---

### Post by NeghVar on 2006-04-05
My personal favorite way of causing problems is liberaly placed explosives...

But ya if you really want to cause problems u will most likely have to root.

---

### Post by therunnyman on 2006-04-05
I thought about going root, but I've got that security paranoia thing.  Oh!  That's another thing!  I set up a bunch of dummy user accounts, the punji stick defense behind the firewall...

---

### Post by NeghVar on 2006-04-05
If your worried about security just disconnect it from the net, also if your only use root for a limited time and you have a firewall than it is unlikely to much can happen, there are only a handful of viruses for linux, no real spyware that im aware of and the odds of a hacker comming by at that time frame that knows how to get in is unlikely, I'd say your pretty safe for root so long as you dont run torrents, gaim, ff and a million other services that broadcast yourself to the world.

note: I do not endorse using root for anything even resembling routine tasks, that is just wrong unless you are totally sure in your own perfection and that of your backups.

---

### Post by mlind on 2006-04-05
You should definetly try doing *rm -rf* while root user on wrong directory or
removing someting essential like glibc with --force option. two of my favourites :mrgreen: 

Seriously, I've not had single major problem with Ubuntu stable releases.
Everything just works and it's great.

---

### Post by taurus on 2006-04-05
[QUOTE=mlind]You should definetly try doing *rm -rf* while root user on wrong directory or
removing someting essential like glibc with --force option. two of my favourites :mrgreen: 

Seriously, I've not had single major problem with Ubuntu stable releases.
Everything just works and it's great.[/QUOTE]
"sudo rm -rf /" is the classic one and actually, somebody did that!!!  ](*,)

---

### Post by halfvolle melk on 2006-04-05
[QUOTE=therunnyman]How am I supposed to learn anything about Linux if nothing breaks, and I can't break stuff?[/QUOTE]
A few days ago I tried to install a .deb for dapper, knowing this is generally a bad idea. Then it started to remove all kinds of stuff and told me that that I told it to remove the kernel as well and if I really wanted to do that being not recommended and all. Apt upgrade fixed it back to how it was, but if you want to break it, I'd recommend mixing repo's that shouldn't be mixed or install inappropriate packages. That's bound to break something.
Good luck! ;)

---

### Post by NeghVar on 2006-04-05
> sudo rm -rf /

sorry im a noob... wat does this do...

---

### Post by halfvolle melk on 2006-04-05
Delete your file system. All of it.

---

### Post by sn123 on 2006-04-05
[QUOTE=NeghVar]sorry im a noob... wat does this do...[/QUOTE]
rm removes a file -f switch makes it a force remove (i.e. it never prompts) and -r switch makes it recursive (recursively remove directory contents), / stands for the root folder. So it forcefully removes all the files starting from root folder. In simple terms:
*boys and girls please don't try it at home, it's very dangerous* :)

S

---

### Post by therunnyman on 2006-04-05
[QUOTE=sn123]*boys and girls please don't try it at home, it's very dangerous* :)

S[/QUOTE]

Great, now you tell me...

---

### Post by NeghVar on 2006-04-05
> rm removes a file -f switch makes it a force remove (i.e. it never prompts) and -r switch makes it recursive (recursively remove directory contents), / stands for the root folder. So it forcefully removes all the files starting from root folder. In simple terms:
boys and girls please don't try it at home, it's very dangerous

Ahh I knew it was remove something, totally forgot about root being /... that would seem to be a bad command... i so have to get my friends to switch to linux now...

---

### Post by sn123 on 2006-04-05
[QUOTE=therunnyman]Great, now you tell me...[/QUOTE]
never mind...if you want all the files back deleted by rm -f-r command, all it takes is to issue this command or is there any better command? :D
```

$ mr +fr \ 

```

PS: I was kidding, there's no reverting back so please don't try it at home!

---

### Post by therunnyman on 2006-04-05
[QUOTE=sn123] PS: I was kidding, there's no reverting back so please don't try it at home![/QUOTE]

I was kidding too, of course.  It may be wise to heed the admonitions not to erase your file system, just in case anyone's tempted.

---

### Post by NeghVar on 2006-04-05
Are you sure... im thinkin it could be a fun weekend activity...

quick questho... if i was to say theorectically use this would it also nuke my 2nd hd... cuz that would be bad lol

---

