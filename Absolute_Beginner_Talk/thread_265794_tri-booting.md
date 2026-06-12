---
title: "tri-booting?"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by dillbertdabomb on 2006-09-26
is it possible to have ubuntu kubuntu and windoze on the same computer? and if so how?

---

### Post by Bachstelze on 2006-09-26
Ubuntu and kubuntu are the same. To install "Kubuntu" in an "Ubuntu", run *sudo aptitude install kubuntu-dekstop*.

---

### Post by dillbertdabomb on 2006-09-26
I want them both seperate. and I wonder if the installer can install grub over antother version?

---

### Post by maaronB on 2006-09-26
There is no reason you couldn't do that.  If you wanted you could create a new partion and place kubuntu on that.  You could even place your home directory on a seperate partion and share it between the two.

But it would probably be easier just to use your login screen to switch between KDE and Gnome.

---

### Post by Bachstelze on 2006-09-26
It would just be as pointless as installing two Ubuntus...

---

### Post by crossedout on 2006-09-26
HymnToLife and maaronB are both right, although for convenience sake it is certainly easier to switch between desktops and use aptitude to install kubuntu rather than partitioning for it and using grub to access it.
Just my opinion.


-Xout

---

### Post by ReaderRat on 2006-09-26
Just my experience, but tri-booting is a pain in the rear if you don't know what you're doing (are really a Newbie). Much better to do as these informed people say. Good Luck, whatever you decide.

---

### Post by jwbirdsong on 2006-09-26
Pointless or not aside..."Tri-booting" seems to work fine as I've got grub set to boot to any of 3 partitions....Dapper-Edgy-WinXp..
Works fine; have had no problems with it yet...been this way 5 or 6 weeks

---

### Post by Bachstelze on 2006-09-26
I do too, Dapper/WinXP/FreeBSD, it will certainly work but to me, it's just a waste of diskspace.

---

### Post by bodhi.zazen on 2006-09-26
Why limit yourself to just 3 ??? :)

Two versions of Ubuntu are great, use one a primary and the other for testing. Test before you upgrade, install, or compile new software.

If you trash your test box you still have your primary....

Of course you could VMWare as well, but it is not as fast.

The only limit you have is HD size and # of partitions.

And yes, it is very easy to tipple, quad, +++ boot. :cool:

---

### Post by dillbertdabomb on 2006-09-26
how would I do that? and could i put gnome and kde on the same os?

---

### Post by bodhi.zazen on 2006-09-26
> **dillbertdabomb said:**
> how would I do that?

Basic steps:[list=number][*]Partition your HD, 1 partition per OS, SWAP is shared no problem, use a large (shared) data partition rather then a /home partition.
[*]Install each OS from install CD.
[*]When the time comes, install GRUB/LIOL onto the [color=blue]ROOT[/color] partition and [color=red]NOT the MBR[/color].
[*]Update /Ubuntu_root/boot/grub/menu.lst.[/list]

Very easy. Here is an example:

[[color=blue]Boot 100+ Os[/color]](http://www.justlinux.com/forum/showthread.php?threadid=143973)

> **dillbertdabomb said:**
> and could i put gnome and kde on the same os?
Yes.
```
sudo aptitude update && aptitude install kubuntu-desktop ubuntu-desktop
```

I advise you try xfce, fluxbox, openbox, and IceWM. You will eventually settle into you favorite.

---

