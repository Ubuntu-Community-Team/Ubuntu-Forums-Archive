---
title: "Old Computers"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by Jerry N on 2007-06-01
I have seen several queries here about installing UBUNTU on old machines so I will inject my experience.  I tried the XUBUNTU 7.04 live disk on a Pentium 233 with 128mb RAM without success - no error messages but it had not started after a couple of hours.  I then tried the alternate installation of XUBUNTU 7.04.  This took several hours but the installation was succesful.  Compared to the Windows 98SE that I normally run on the computer (on the very rare occasions that I have a need to run it) XBUNTU is glacially slow with a boot time in the neighbourhood of 5 minutes.  I didn't try editing any pictures!

This is not a complaint about XUBUNTU or a request for help but rather a comment on trying to use really outdated equipment.  My next step is to dig around through my junk and abandoned computers and try to find some more RAM to see if that helps the performance.  

BTW, I am writing this comment on an Athlon 2400 machine with 1gb RAM and UBUNTU 7.04.

Jerry

---

### Post by justin whitaker on 2007-06-01
You might want to look at BeaFantaIX, Puppy, and Damn Small for really old machines. All three are fine solutions for memory constrained systems. You can also do a 'Low-Mem" install of Ubuntu: directions are in the Official Documents.

---

### Post by stoneheart on 2007-06-01
I didn't choose Xubuntu 7.04 because of the many reports of problems given on this board.  Just a few days ago, I successfully installed Xubuntu 6.06 on a Dell Pentium II 550 mHz with 128 megs of ram.  It's not quite as obsolete as the OP's, but it's pretty old.  Works fine as a web-surfing machine and I've used the built-in ssh client to do quite a bit of work on some sites I maintain.

---

### Post by Feba on 2007-06-01
In addition to the suggestions above, SLAX might be worth looking into.

Even Xubuntu isn't going to work on very old computers. Anything before Win2000 should probably be running a very lightweight distro.

Personally, I'd rather use something like SLAX or Puppy and have it run smoothly than Xubuntu and have it be slow.

EDIT: If Xubuntu follows the releases of the regular Ubuntu distro, 6.06 is an LTS version, and will last until 2009, so it could work, if it's significantly less demanding than Feisty, which I kinda doubt.

---

### Post by alienexplorers on 2007-06-01
On my 450mhz computer with 384mb memory I run ubuntu, thou it is very slow.  On a older machine I am running puppy linux.  It has a 333mhz processor and 128mb of memory.

---

### Post by pbw on 2007-06-01
delilinux looks quite promising for old school boxes. The devs state their test machine is a 486 laptop with 16 MB RAM.

Here's an overview of it on distrowatch from a couple weeks ago -  [http://distrowatch.com/weekly.php?issue=20070521#feature](http://distrowatch.com/weekly.php?issue=20070521#feature)

-- pbw

---

### Post by ugm6hr on 2007-06-01
I am a fan of Puppy Linux, and only got hooked on (X)Ubuntu because Puppy (at version 2.14) wouldn't work on my new laptop.  Now I prefer Xubuntu, although the laptops I've installed it on have at least 256MB RAM.

With 128MB RAM, Puppy will be pretty quick, as long as you have at least 200MB swap (Puppy will actually create a "swap file" if you don't have a swap partition - but the latter is recommended) and do a full hard disk install (Puppy is usually run as a "Live" OS even from the HD - they call it frugal installation).

I have also installed LitePup2.14 (a cutdown PuppyLinux) on a 64MB laptop, with reasonable performance,  This was literally just for web browsing and basic word processing, where AbiWord and Opera did the trick.  It's networking and wireless GUI support is excellent, which is why I chose it.

In fact, my very first outing with Linux was on a 48MB desktop as a bit of an experiment.   It had Windows 98, but that is unsupported, and pretty useless for anything that involves internet or network now.  So I gave DamnSmallLinux a go, and that is definitely a good choice, and I was even able to install it with the LiveCD (with some difficulty).  It was definitely quicker than Windows 98 on that piece of hardware.  However, as a first foray into Linux, DSL seemed to have nothing of any use pre-installed (apart from Firefox, which was pretty sloooooooow), and I couldn't work it out.  So, after sorting Puppy out on some laptops, I went back to this and tried.  And it was unbearably slow.  Still not using it for anything.

So - for this machine, I was toying with UbuntuServer7.04/Fluxbox as an option, probably with Thunar, Opera and AbiWord:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
If you follow this, do you get the auto-mounting of Ubuntu?  This would be pretty important, because my family (who use these various machines) can't seem to get past the requirement to mount memory sticks and CDs.  Unmounting is OK, because even Windows requires you to "safely disconnect".

Anyway - sorry to hijack your thread - that wasn't my intention at all ;)  I was just trying to explain that it's worth trying different flavours of Linux, because some are deliberately designed for old hardware (DeLi specifically), and it is obviously unreasonable to compare a modern Linux OS with an obselete Windows one.

---

### Post by RedSquirrel on 2007-06-01
> **ugm6hr said:**
>  So - for this machine, I was toying with UbuntuServer7.04/Fluxbox as an option, probably with Thunar, Opera and AbiWord:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
If you follow this, do you get the auto-mounting of Ubuntu?  This would be pretty important, because my family (who use these various machines) can't seem to get past the requirement to mount memory sticks and CDs.  Unmounting is OK, because even Windows requires you to "safely disconnect".

To get automounting, either ivman or gnome-volume-manager might be worth a try. I prefer to mount things manually so I don't use either of these myself.

---

### Post by Harii on 2007-06-17
Thunar has a plugin that works.
thunar-volman-plugin

---

### Post by dhughes on 2007-06-17
> **Jerry N said:**
> ...BTW, I am writing this comment on an Athlon 2400 machine with 1gb RAM and UBUNTU 7.04.

Jerry

 That's what my main system is, more or less. :oops:

---

