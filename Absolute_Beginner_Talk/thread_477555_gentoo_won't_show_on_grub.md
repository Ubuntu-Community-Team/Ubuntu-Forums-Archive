---
title: "gentoo won't show on grub"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by Tyke91 on 2007-06-18
I'm trying to dual boot ubuntu and gentoo (ubuntu for work, gentoo so i can learn more about linux) and i've run into a problem. 

I can use the gentoo cd to make gentoo show on grub, but then ubuntu is gone. If i use the ubuntu cd, then it'l show on grub, but then gentoo wont.

is there a way i can have them both?

---

### Post by phr0ze on 2007-06-18
Use each to get grub working and get a copy of /boot/grub/menu.lst Once you have this, add the missing line into the menu.lst of the other.

---

### Post by coffeecat on 2007-06-18
And not forgetting that Gentoo calls menu.lst /boot/grub/grub.conf. Oh - and the version of Grub that Gentoo uses goes belly-up if you keep the "savedefault" line that Ubuntu puts in the menu.lst stanza for itself. Just take it out. That's what I do.

**Edit: Tyke91, ** post the contents of menu.lst from Ubuntu and of grub.conf from Gentoo (take out the commented lines from the Ubuntu file before posting otherwise you'll burst the forum server - they serve no useful purpose. :wink: ). Also post your partition layout and which partition(s) each distro has been installed to. Then I'll show you how to make a combined menu.lst/grub.conf and how to reinstall Grub from one or the other distro. You don't have to use a live CD to do this so long as you can boot into one of the distros. Lastly,  say which distro you are currently booting into - we'll use that one to reinstall grub and we'll edit that one's grub menu.

---

### Post by confused57 on 2007-06-18
You might try a configfile entry to boot Gentoo:
```
title        Gentoo
configfile   (hd0,5)/boot/grub/grub.conf
```

substitute your Gentoo root partition in place of (hd0,5)

---

### Post by Tyke91 on 2007-06-18
i've got grub to work, but now i've got another question. I've posted on the gentoo forums, but they seem kinda lazy and havent posted all day... so im going to try here :p

KDE won't display

to be more precise... nothing will display. all i get is the command promt (i actually get "Error, Display manager failed to load").

i know my video card is good enough because the live CD worked, but the installed version doesnt...

any way to fix this without a full reinstall? I  don't feel like compiling the entire thing from source... AGAIN (11 hours #-o)

---

### Post by confused57 on 2007-06-18
> **Tyke91 said:**
> i've got grub to work, but now i've got another question. I've posted on the gentoo forums, but they seem kinda lazy and havent posted all day... so im going to try here :p

KDE won't display

to be more precise... nothing will display. all i get is the command promt (i actually get "Error, Display manager failed to load").

i know my video card is good enough because the live CD worked, but the installed version doesnt...

any way to fix this without a full reinstall? I  don't feel like compiling the entire thing from source... AGAIN (11 hours #-o)
No, you definitely shouldn't have to recompile from scratch...you're just experiencing what it's like to use Gentoo.  There's not as much traffic on the Gentoo forums, but someone will probably see your post.  
I removed Gentoo a couple of months ago, mostly because of the compile times...about an hour to upgrade to the latest Mozilla Firefox, etc.   It's probably a configuration file or possibly recompiling kdm would work...I'd have to dig out my old notes, which I don't think I can find anyway.  A Gentoo forum search may turn up something.  I think that's the benefit of installing with the Gentoo minimal cd, you get a better understanding of tweaking & troubleshooting your Gentoo install.

One great thing about Gentoo is that it's well documented:
[http://www.gentoo.org/doc/en/kde-config.xml](http://www.gentoo.org/doc/en/kde-config.xml)

Another thing you might do is to press "Scroll-lock" when the error message appears at Gentoo boot...add this to your post in the Gentoo forums, someone seeing the exact error message may be able to help you.

---

### Post by Tyke91 on 2007-06-18
thx

---

