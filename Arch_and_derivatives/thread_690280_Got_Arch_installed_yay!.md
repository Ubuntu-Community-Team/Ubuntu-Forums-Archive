---
title: "Got Arch installed yay!"
date: 2008-02-07
forum: Arch and derivatives
---

### Post by Sunflower1970 on 2008-02-07
Last night, at 11:30pm I had a full working Arch system with XFCE running and wireless. After two minor hiccups--creating a user, and an xorg problem both which were very quickly solved (to my delight and surprise) I was staring at the XFCE desktop at the right resolution. Installed Firefox and I was browsing for a few minutes.

I was expecting a huge headache with wireless. In fact, getting wireless to work on Debian Lenny was much more of a hassle than Arch. :shock:

Still need to set up my settings the way I want them, and install the nVidia drivers.

I can't wait to play around with it more to see if it really is speedier than Lenny, or Ubuntu. This is on my old PII

I'm absolutely ecstatic that I got this up and running in just a few hours.(instead of a few days which is how long I expected it to take) Tried to tell a co-worker about it and my hubby...Both looked at me as if I was crazy....I just had to tell someone...figured everyone here would understand :cool:

---

### Post by Rumor on 2008-02-07
Congrats and welcome to Arch :)

I think Arch should be the distro of choice for old PII's. I have three of them, one a desktop, one a server (with dual PII's!) and one an old Dell laptop. 

Arch + Fluxbox feels very nimble and responsive on these older machines and makes them every bit as useful as hardware with more oomph.

---

### Post by finferflu on 2008-02-07
Welcome aboard, you'll be hooked, if you aren't yet. So be warned :P

As you say, one of the most amazing things with Arch is that it actually works. You set it up and it does the job. That's because of the transparence of the KISS principle. 

I have also found out that Arch performs better than Debian in terms of configuration. I am home now :P

---

### Post by pelle.k on 2008-02-07
> Tried to tell a co-worker about it and my hubby...Both looked at me as if I was crazy....I just had to tell someone...figured everyone here would understand 
We do understand!
Arch is fun, because you get to piece it together, without doing the *really* dirty work. It's not as hard as some people say, just different - if you're used to say, ubuntu.
You also get a better picture of how a modern distro is put together.

About slower hardware. The only thing is that even if you run openbox (or whatever), applications like firefox still makes your system crawl. But i have heard good things about khazekaze (is that how you spell it?), and i also imagine epiphany would make a good lightweight alternative to firefox as well.

As long as you've got enough ram, gnome as well as kde should be quite snappy on arch, even with a p2/p3.
Some icon/gtk themes can have huge impact on the snappiness of the desktop as well. Even on a core2duo.

---

### Post by Rumor on 2008-02-07
> **pelle.k said:**
> 
About slower hardware. The only thing is that even if you run openbox (or whatever), applications like firefox still makes your system crawl. But i have heard good things about khazekaze (is that how you spell it?), and i also imagine epiphany would make a good lightweight alternative to firefox as well.

Kazehakase - [http://en.wikipedia.org/wiki/Kazehakase](http://en.wikipedia.org/wiki/Kazehakase)
It's in the AUR, I think. I have it installed on a couple systems. It is very light and responsive. The thing that surprised me most is that Opera runs very smoothly on these lower end systems. it has become my browser of choice for a slower system.

---

### Post by finferflu on 2008-02-07
To be honest I don't find Kazehakase much faster than Firefox, and I don't find any of the Gecko based browsers to be light at all. Except for Conkeror. I don't know what they did, but it's light, even though it's almost feature-less. I love a keyboard-driven browser, and that's pretty much all I want from a browser. Perhaps I miss Ad Block, even though Conkeror can block stuff based on regexps... I'm not really familiar with regexp in a web browser...

Anyway, give Conkeror a try, otherwise stick with Opera. That's what I do. Elinks is the text-only alternative.

---

### Post by Sunflower1970 on 2008-02-08
Thanks everyone :)

I've tried Kazehakase and not too sure I really like it. I used the ones in the Ubuntu repos and had freezing problems. My two main browsers are Opera and Firefox. Firefox 3 beta to be exact. It feels faster and lighter than FF2 for some reason. 

Had a chance to play around with Arch last night and even on the PII 400Mnz, 384MB RAM using Firefox 3beta, it was very responsive. Much more than Ubuntu with pure Xfce or Debian w/Xfce. (which are both on this compute too) I was impressed with the boot time. By tweaking Ubuntu, I had been able to go from around a 2 minute boot time, to about 1:20 boot time. Arch feels faster, although I have not had a chance to time it. I'd say it's probably about 45 seconds to a minute (a bit faster than my laptop and my other desktop--untweaked Ubuntu. Both have P4's in them) Still have to install the nvidia drivers so I can use Compiz on it (Compiz actually works. Very well on this computer. Shocking, I know :D)

I did run into a complication last night, that I wasn't able to figure out. After having Arch installed and running the night before, when I had turned it on last night, my wireless refused to work. Almost as if the madwifi drivers had uninstalled themselves. Very odd. I had not upgraded the kernel, nor did anything with the nvidia drivers since I wanted a working system before I attempted to install them....I ended up reinstalling the entire system last night, turned it on and off a few times and madwifi seems to be okay, now...Ran into a few other minor problems (like trying to log in and my .dmrc and .bashrc was being ignored) but it's all be smoothed over now.

Tried installing yaourt last night, but it wouldn't makepkg...after a day of thinking about it though, I don't think I had all the tools necessary to have it work...gonna have to look at it again tonight :)

---

### Post by Odd-rationale on 2008-02-08
You can do it the easy way!

Edit your /etc/pacman.conf and include the followin lines:
```
[archlinuxfr]
Server = http://repo.archlinux.fr/i686
```

Then
```
# pacman -Sy yaourt
```

Here's the link:
[http://www.archlinux.fr/yaourt-en/](http://www.archlinux.fr/yaourt-en/)

---

### Post by bwtranch on 2008-02-08
I was really surprised about how well it went also. I'm used to getting hangups that take hours to fix (or days). The only time I was a little worried was with the nvidia driver and the xconf. But, it worked itself out. Really, I don't think I had that much to do with it! I'm using a 64-bit processor and don't want to use any 32-bit stuff if possible. Just to see how things go. Well, anyway, I just got into it yesterday and I don't know a whole lot. Gee, I sound like a noob! Well, I guess I am, sort of:)

---

### Post by din on 2008-02-09
I want to add one thing - for me Arch is a top, top distro.
It's fast, flexible, cool. It's give u feel of real power. I think i found 
what i looked for... 

Simply the best !!! :cool:

---

