---
title: "Dual-booting vista with multi-user computer"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by LingLing1337 on 2007-08-19
Hey all, I'm a very big proponent of the open source scene. But here's the thing, I share a computer with my family. I'd like to know if it's possible to make this work. My family doesn't really care about open source, etc, etc. So I'd like to know if it's possible for me to coexist this way with my closed source family without any major hassle. I'm completely new to Ubuntu and dual-booting. Any help is appreciated. Thanks!

EDIT: By this I mean I'd like to boot Ubuntu, while my family can log on to their respective Vista accounts without any real problems.

---

### Post by Hobo Joe on 2007-08-19
Yes, you can. However, I'd say it would be even better if you could make accounts for them in Ubuntu and convince them how awesome it is. :D

---

### Post by LingLing1337 on 2007-08-19
Sure, I'd set up accounts. My main question is, would I have to reboot every time my family wanted to log in after me? i.e, I'd boot into Ubuntu, then I'd have to restart the computer and boot into Vista every time they wanted to get on after me, right? Thanks.

---

### Post by Falcorian on 2007-08-19
> **Hobo Joe said:**
> Yes, you can. However, I'd say it would be even better if you could make accounts for them in Ubuntu and convince them how awesome it is. :D

You can set it up so that it default boots into Windows, and hides the Grub screen unless you hit esc. That way the Linux part won't confuse them.

You'd have to look up the settings for your grub though, I don't know them off the top of my head... :(



But yes, you'd have to reboot to switch OSes. Although I hear you can suspend them and start in the other one more quickly... I'm also not sure how to work that. ;)

---

### Post by Hobo Joe on 2007-08-19
> **LingLing1337 said:**
> Sure, I'd set up accounts. My main question is, would I have to reboot every time my family wanted to log in after me? i.e, I'd boot into Ubuntu, then I'd have to restart the computer and boot into Vista every time they wanted to get on after me, right? Thanks.

Yes, if you were logged into Ubuntu, and then wanted to get into Vista, they would have to reboot.

Like I said though, if you get them to like Ubuntu it's a win-win situation. You've convinced them that open source is awesome, and prevented constant reboots of the system. :)

---

### Post by LingLing1337 on 2007-08-19
Well, we do use OpenOffice and Avast! already, I don't know if they're open source (OpenOffice is I think) and we are extremely pleased.

To Falcorian, I'm not sure what a grub screen is, I'm completely new. And wouldn't hitting escape in another program bring it up? Thanks.

---

### Post by Falcorian on 2007-08-19
> **LingLing1337 said:**
> Well, we do use OpenOffice and Avast! already, I don't know if they're open source (OpenOffice is I think) and we are extremely pleased.

To Falcorian, I'm not sure what a grub screen is, I'm completely new. And wouldn't hitting escape in another program bring it up? Thanks.

If you install a dual boot, when your computer powers on, you'll get a screen that asks you:

"Linux or Vista?"

That's the grub screen. You can however set it from Ubuntu so that it doesn't display unless you hit esc when you're booting (just like accessing BIOS, same sort of hit key on start up thing), and so that it loads Windows by default.

More info: [http://en.wikipedia.org/wiki/GRUB](http://en.wikipedia.org/wiki/GRUB)

---

### Post by Aishiko on 2007-08-19
> **LingLing1337 said:**
> Well, we do use OpenOffice and Avast! already, I don't know if they're open source (OpenOffice is I think) and we are extremely pleased.

To Falcorian, I'm not sure what a grub screen is, I'm completely new. And wouldn't hitting escape in another program bring it up? Thanks.
the Grub is done before any OS is loaded (in this case windows and Linux) so there are no programs running but the grub.  Open Office is Open source as is Firefox, and thunderbird.  There are dozens of others, but I'm tired and blanking on them at the moment.

---

### Post by LingLing1337 on 2007-08-19
Oh, that sounds sweet. I'll probably just keep the grub screen then.

Thanks for all the help. I'll read the stickies. So is Ubuntu pretty user friendly at this point? I consider myself pretty handy with computers, but have never partitioned a drive or become any good at editing registries. But could I burn 7.04 to a CD and be able to install it myself? Again, I'll read the stickies, but any other tips are appreciated.


EDIT: Also, is there a guide to dual booting that you would really recommend? Thanks!

---

### Post by Aishiko on 2007-08-19
> **LingLing1337 said:**
> Oh, that sounds sweet. I'll probably just keep the grub screen then.

Thanks for all the help. I'll read the stickies. So is Ubuntu pretty user friendly at this point? I consider myself pretty handy with computers, but have never partitioned a drive or become any good at editing registries. But could I burn 7.04 to a CD and be able to install it myself? Again, I'll read the stickies, but any other tips are appreciated.


EDIT: Also, is there a guide to dual booting that you would really recommend? Thanks!

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) is the one I see being recommended the most.  As for burning the CD make sure if you use a program like nero you "burn a complation" other wise it won't be a bootable CD.

---

### Post by carloslosgrande on 2007-08-19
[FONT="Comic Sans MS"]Hi, check these sites;
> [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) and > [http://www.psychocats.net/](http://www.psychocats.net/)
for a very good tutorial and explanation[/FONT]

---

### Post by Falcorian on 2007-08-19
> **LingLing1337 said:**
> Oh, that sounds sweet. I'll probably just keep the grub screen then.

Thanks for all the help. I'll read the stickies. So is Ubuntu pretty user friendly at this point? I consider myself pretty handy with computers, but have never partitioned a drive or become any good at editing registries. But could I burn 7.04 to a CD and be able to install it myself? Again, I'll read the stickies, but any other tips are appreciated.


EDIT: Also, is there a guide to dual booting that you would really recommend? Thanks!

Ubuntu is pretty user friendly, but I'll warn you, you'll have to learn to solve problems differently than in Windows! It's a whole new OS after all. ;) Good luck!

---

### Post by LingLing1337 on 2007-08-19
I'm not worried about having to learn to solve problems, that won't be hard with the excellent community here. By the way, I found this guide, does it look to be good? It's pretty recent.

[How to dual boot Ubuntu with Vista installed first]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")

---

### Post by Falcorian on 2007-08-19
Looks good. I dual boot with Vista (before I was just Linux, but I built a new computer...) and that's the guide I used. :)

---

