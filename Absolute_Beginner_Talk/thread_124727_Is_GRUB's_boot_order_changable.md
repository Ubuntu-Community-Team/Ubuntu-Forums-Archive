---
title: "Is GRUB's boot order changable?"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by Leo_01 on 2006-02-02
Is GRUB's boot order changable?
If yes if there any guide to teach me how to change that?

---

### Post by steve.horsley on 2006-02-02
Of course it is. The file you need to edit is /boot/grub/menu.lst.

There are a group of several lines (starting with a **title** line) for each boot option. You can move there groups around to change the order. You can comment out or delete groups you don't want to see. You can add other groups if you want to triple-boot.

Beware that stuff inside the AUTOMAGIC KERNELS LIST will get overwritten every time the kernel is updated. But I usually comment out the recovery mode and memtest options after a few days, and change the title of the main Ubuntu entry, just to make the boot selection screen look neater. Mine just says
> Linux
Windows

You can change the defaut entry by changing the line **default 0** near the top, but I prefer to change the order and leave the top entry (0) as the default.

---

### Post by Leo_01 on 2006-02-02
great!
so after changing the order i presume GRUB will boot Windows unless i tell it to go to ubuntu?

---

### Post by TechSonic on 2006-02-02
[QUOTE=Leo_01]great!
so after changing the order i presume GRUB will boot Windows unless i tell it to go to ubuntu?[/QUOTE]


O.o What the heck.. You mean you want Grub to default to Windows?  BARF!

But yeah, you can do that.

---

### Post by Leo_01 on 2006-02-02
It is a family computer... (the rest of my system are ubuntu only...)
my dad is requires acess to websites that work on IE...
>_>
oh ya..
i see 2 diff type of ubuntu installation in the GRUB boot screen... (no diff actually just diff names)
why is that so? (i just installed all latest updates...)

i get :

Other OS :
Win XP Pro

Ubuntu,kernel 2.6.12-10-386
Ubuntu,kernel 2.6.12-10-386 ( Recovery Mode )
Ubuntu,kernel 2.6.12-9-386
Ubuntu,kernel 2.6.12-9-386 (recovery mode)
Ubuntu, memtest

why do i have 2 types of linux kernal?
btw can i get get rid of the 'other OS' text?
how do i do that?

---

### Post by aysiu on 2006-02-02
[QUOTE=Leo_01]It is a family computer... (the rest of my system are ubuntu only...)
my dad is requires acess to websites that work on IE...
>_>[/QUOTE] Is that the only reason you need to boot to Windows, or are there other Windows-only programs? [The User Agent Switcher extension](https://addons.mozilla.org/extensions/moreinfo.php?id=59&os=Linux&application=firefox&version=1.6&go=Go) usually works on Firefox for IE-only websites. Otherwise, you can actually [install Internet Explorer (through Wine) on Ubuntu.](http://www.tatanka.com.br/ies4linux/)

---

### Post by Leo_01 on 2006-02-02
nah...
my dad just need time to get used...
btw aysiu...
did you create the guide on how to dual boot with windows in your sig?
it is a great guide!
tks alot!
btw also check out my latest posted question... (i edited my previous post)

---

### Post by Leo_01 on 2006-02-02
btw...
should i be accessing Ubuntu,kernel 2.6.12-10-386 or Ubuntu,kernel 2.6.12-9-386?

---

### Post by Klaidas on 2006-02-02
You can access whichever you want, but if the updated kernel (2.6.12-10-386) is working fine, than access the new one :)

I have the same listing, so I think I'll remove the old kernel

---

### Post by Leo_01 on 2006-02-02
err so i am having 2 kernal in ubuntu?:confused:

---

### Post by aysiu on 2006-02-02
Yes, you have two kernels. Unless you're shy for hard drive space, you can just leave both in there. If you want to take something out of the Grub menu (*other operating system*, for example), just put a # in front of the line you want to take out.

If you want to uninstall the old kernel, do a Synaptic Package Manager search for the word *image*, and you'll see what you should uninstall.

And, no, I didn't write that excellent dual-boot guide. It's the only thing in my signature I *didn't* write, but it *is* excellent, and I love that it has screenshots.

---

### Post by Klaidas on 2006-02-02
Yes.

EDIT: Awww, I was too slow :)

---

