---
title: "PPC Window Managers ........"
date: 2010-02-28
forum: Apple Hardware Users
---

### Post by noriek on 2010-02-28
Hi all,

Mightly impressed at the work gone in to Lenny over etch. Etch was forever giving me niggles on my G3 iMac DV 450 but Lenny is very smooth, 'featureful' and includes the best DVD and DivX playback I've ever had from this machine. However, with only 256MB ram, which I'm not prepared to upgrade unless the ram just falls in to my lap, I'd like to try lighter window managers to free up some memory, so,

Which window managers are still being actively developed for PPC, and which of these is the most refined?

I know plenty about the properties of each window manager, I'm just interested in which has active ppc support.

Thanks

---

### Post by linuxopjemac on 2010-02-28
all these window managers are ported to ppc too, not specifically made for ppc. You can install anything you like. I like fluxbox personally.

---

### Post by noriek on 2010-02-28
> **linuxopjemac said:**
> all these window managers are ported to ppc too, not specifically made for ppc. You can install anything you like. I like fluxbox personally.

Thanks for your reply,

I asked the wrong question really. I guess it was more about the nature of the port/compiling: Are some ports more successful than others; due perhaps to library dependencies for example? I guess it shouldn't be the case but it seems, in my experience at least, the same piece of software on i386 and ppc architectures can perform radically differently in terms of speed and stability. Is this an issue with window mangers? If yes, then my first question again: in essence, do any window mangers standout for ppc?

Thanks

---

### Post by linuxopjemac on 2010-02-28
I can't answer that one as I never use low memory window managers on x86. Just try it out I'd say. You can easily uninstall them too. I tried many under Lenny on my PPC PowerBook G3. I ended up with fluxbox.

---

### Post by oswaldkelso on 2010-02-28
[http://wiki.lxde.org/en/Debian](http://wiki.lxde.org/en/Debian)

This is the easy option for a light Desktop. everything is set-up and just works off the bat. 

Another is open-box and tint2 with rox-filer add halevt so you can mount CD's etc. Open box has been very stable on my boxes, as has tint2.  Make sure you install rox-filer separately as it pulls in zeroinstall-injector that has some but very limited PPC support and is generally "apita" rox-filer looks simple but is in fact very fast and powerful but needs a few weeks to tweak, to your own personal way of working.


# apt-get --no-install-recommends install rox-filer

The biggest concern/dilemma on my 333mhz 256mb imac is the browser. Download and compile dillo2 (note the 2) or add netsurf for light browsers, or try iceape for a suit. browser, email, irc, composer.  Arora is light but brings in qt depends as does konqueror. Midori, Kazehakase, epiphany, iceweasel non seem just right for low end machines, it's all a fudge depending on your needs.

---

