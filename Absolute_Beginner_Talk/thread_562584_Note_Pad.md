---
title: "Note Pad"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by madmatrixz3000 on 2007-09-28
Hey where are the note pad files stored becase I need to goto Xubuntu however I have alot of notes that I need to transfer.

---

### Post by llamakc on 2007-09-28
Please clarify. You want to know where TO store your notepad documents (from Windows) or you want to know where you stored your notepad documents ON WINDOWS so you can move them?

---

### Post by madmatrixz3000 on 2007-09-28
I am currently using Ubuntu with Tomboy and want to know where to get my notepad files

---

### Post by llamakc on 2007-09-28
> **madmatrixz3000 said:**
> I am currently using Ubuntu with Tomboy and want to know where to get my notepad files

Oh my bad. Sorry. Look in ~/.tomboy

---

### Post by madmatrixz3000 on 2007-09-28
Better question will going to Xubuntu increase the speed much or should I spend the $30 to get 756mb ram into my laptop

---

### Post by llamakc on 2007-09-28
Xubuntu does run better on less resources. The second question really depends on how hard it is for you to part with $30. For some that's nothing, for some, alot.

For me, RAM is like beer. I can never have enough.

---

### Post by Skidpad on 2007-09-28
What are your current specs?

---

### Post by llamakc on 2007-09-29
My slowest machine is a 1.2ghz box with 384mb of RAM. My kid runs GNOME on it and it definitely could use more RAM, or for me to convert it to Xubuntu for  better use.

If you follow the howto here:

 [http://psychocats.net/ubuntu/xubuntu](http://psychocats.net/ubuntu/xubuntu)

You can easily get right back to pure GNOME if you're unhappy by following the other link here:

[http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)

---

### Post by madmatrixz3000 on 2007-09-29
256 ram on a Latitude C300 laptop with ATI card and a Pentium III processor.  I know the specs kinda suck but its my throw around laptop.  Soon I get an 1 year old HP pavilion as my nice laptop for gigs and business.


Dido on the beer thing.  My desktop has 1.5 Gb and a Pentium 4 processor and it still seems laggy.  I really need to get a vid card with dedicated ram though cause I bet that is sucking resources.

---

### Post by llamakc on 2007-09-29
Since I'm the one in the house that semi-knows what I'm doing with hardware I seem to get all of the castaways. Sigh. 

You'd notice a difference with xubuntu I think.

---

### Post by madmatrixz3000 on 2007-09-29
how long will the update to Xubuntu take and will all my home files still be there, aka are Tomboy and all my programs still supported.  Mainly I am worried about Tomboy as it is one of the reasons I switched to ubuntu.

---

### Post by madmatrixz3000 on 2007-09-29
> **llamakc said:**
> Since I'm the one in the house that semi-knows what I'm doing with hardware I seem to get all of the castaways. Sigh. 

You'd notice a difference with xubuntu I think.

Hey I'm the most knowledgeable and my parents get mad with some of the stuff I do with the handme down computers.  Thus I have to get Ubuntu working full force on my old laptop and my desktop before they will let me touch the HP.

---

### Post by llamakc on 2007-09-29
xubuntu-desktop (and ubuntu-desktop) are meta-packages that install a bunch of other packages. Neither will destroy stuff in your /home/USER directory.

I do not know if Tomboy works with XFCE though.

I do know that Tomboy can really slow a machine down, by my experience. If that's what got you to switch I'd spend the $$$ on more RAM.

---

### Post by llamakc on 2007-09-29
Oh yeah, it has a bunch of packages to install and the time it takes will depend on the speed of your net connection and the time to install the packages. It's definitely quicker than compiling glibc on Gentoo :)

---

### Post by madmatrixz3000 on 2007-09-29
Can I switch back to Ubuntu easily, and by the way I find firefox and such, especially open Office, much more demanding.  I think tomboy is the least demanding as it is open in background

---

### Post by madmatrixz3000 on 2007-09-29
> **llamakc said:**
> Oh yeah, it has a bunch of packages to install and the time it takes will depend on the speed of your net connection and the time to install the packages. It's definitely quicker than compiling glibc on Gentoo :)

What? Gentoo?

---

### Post by llamakc on 2007-09-29
> **madmatrixz3000 said:**
> Can I switch back to Ubuntu easily, and by the way I find firefox and such, especially open Office, much more demanding.  I think tomboy is the least demanding as it is open in background

Yes, you could remove all of the packages supplied by xubuntu-desktop if you use the link I posted above. Follow the directions and install it with aptitude, which makes the removal much, much simpler.

---

### Post by madmatrixz3000 on 2007-09-29
Dude i am a Linux noob so I am lost what?  Remove packages?

---

### Post by llamakc on 2007-09-29
Software in Ubuntu is delivered, installed, configured, and eventually (if needed) removed in 'packages' that are called "debs" as in packagename.deb.

When you search for stuff in Synaptic or see stuff to be upgraded in "Software Update" it is referring to these deb packages.

Xubuntu is installed by installing a single "meta-package" that is a placeholder that POINTS to all of the packages needed to install the XFCE environment on Ubuntu.

You asked if you'd be able to remove xubuntu and go back to Gnome. The answer is yes. But you have to install xubuntu-desktop via aptitude as explained in the first link I offered earlier. The second link in that same post explains how to remove the xubuntu (XFCE) environment.

Does that help at all?

---

### Post by madmatrixz3000 on 2007-09-29
Yeah that clarifies it.

I started following those instructions, my terminal says

"99% [5 Translation-en_BG bzip2 0]"

It has stopped at this line so now what?

---

### Post by madmatrixz3000 on 2007-09-29
Also, my desktop does not have internet connection as my wireless is not yet working do I need internet to install .deb files or are everything included.

This is about .deb's not the same issue as the laptop with Xubuntu

---

### Post by llamakc on 2007-09-29
I think you just wait. Go get one of them beers (if you're allowed to)!

---

### Post by llamakc on 2007-09-29
> **madmatrixz3000 said:**
> Also, my desktop does not have internet connection as my wireless is not yet working do I need internet to install .deb files or are everything included.

This is about .deb's not the same issue as the laptop with Xubuntu

You probably would need the Xubuntu install CD.

---

### Post by madmatrixz3000 on 2007-09-29
Nope i'll just go try to get envy working on my desktop and see if I can get my wireless working.

---

### Post by madmatrixz3000 on 2007-09-29
This a question about installing envy, I have saved the .deb to a CD

---

### Post by llamakc on 2007-09-29
I'm unfamiliar with it. Sorry. Good luck!

---

### Post by madmatrixz3000 on 2007-09-29
in general do .deb's include all the files needed or do you need internet

---

### Post by llamakc on 2007-09-29
Some debs depend on other debs, which may not be on the disc you currently have. When that happens, apt-get (synaptic, aptitude) will go fetch the debs from the repository (storage place for deb files either on a disk, online, or on a cd) to satisfy the dependencies.

---

### Post by madmatrixz3000 on 2007-09-29
ok

---

