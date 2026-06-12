---
title: "Some help on installing programs."
date: 2005-09-19
forum: Absolute Beginner Talk
---

### Post by DAXP on 2005-09-19
Not sure if this is the right place. If it isn't, hopefully a mod can move it.

I'm really new to Linux, just installed it yesterday. And today I wanted to start putting some stuff I might want on it on it, such as Azureus, some games (namely the MMOs, I love those type of games >_>), and Wine/Cedega/something like that to run a few windows programs (Ultima Online, Razor, UO Auto Map, and UO Gateway are the only things I can think of that I'd want, and the actual game there came out in 1995, so.. >_>) However, when I went to download Azureus, and the MMOs, there was either multiple versions (with me having no idea which to download >_<) or instructions that are confusing. I also tried Wine, but I could not get the repositories thing to work.

I was also wondering if I should keep my brothers 6800 in this machine or use my card, a 5200FX. The 5200FX is much quieter, but the 6800 is more powerfull. >_> What would you recomend?

Thanks in advance to everyone who helps. Or attempts to help, it might be hard helping someone as dumb as me. >_> And also, there are probably many typos littered throughout my post. That's because I'm using a new(ish) keyboard for my Linux PC, and I'm not used to it at all. >_<

---

### Post by Xian on 2005-09-19
You really need to read up on the [Synaptic How-To Guide](https://wiki.ubuntu.com//SynapticHowto).

---

### Post by DAXP on 2005-09-19
Ok, I can download packages now. I downloaded the Wine packages, but I can't figure out how to use it. >_>

---

### Post by SilentCacophony on 2005-09-19
As for figuring out how to use things you've downloaded, you can generally find documentation in the /usr/share/doc directory. Each app should have it's own directory there. Or type *man name-of-program* in a terminal, making sure to know the exact name of the program. Look for docs on the website, too, if need be.

---

### Post by floppy on 2005-09-19
[QUOTE=DAXP]I was also wondering if I should keep my brothers 6800 in this machine or use my card, a 5200FX. The 5200FX is much quieter, but the 6800 is more powerfull. >_> What would you recomend?[/QUOTE]

The 6800 is way better for gaming. If you want to see some charts about it, check out the benchmark charts in this article from Tom's Hardware:
[http://graphics.tomshardware.com/graphic/20041004/index.html](http://graphics.tomshardware.com/graphic/20041004/index.html)

Hope this helps!

---

### Post by DAXP on 2005-09-19
Ok. Wine is having some trouble. I ran it in terminal, and it asked me if I wanted to install it, I i wanted to install it without Windows on the HDD, and where ?I wanted C:. Then it just exited. >_<

And I knew it was better for gaming, I was wondering if there are any games that might need the 6800 instead of the 5200FX.

---

### Post by mneptok on 2005-09-19
I say this with no malice nor derision. I swear.

But you're trying to run an operating system (Windows) in a virtual environment (WINE/Linux). This is not basic, it is intermediate to advanced Linux usage.

Linux has no conception of drive letters. At all.

I think you should slow down, stop trying to mmediately recreate Windows and just spend a few weeks or months getting familiar with Linux basics. It will be a lot less stressful and a lot more fun.

My $0.02.

---

### Post by DAXP on 2005-09-19
That is fine with me - I wanted to get Wine working so I could run Ultima Online, which one of my friends LOVES to play. The only thing I'd like to do now is find out how to install some of the games that are supposed to run on Linux working, as well as Azureus and a few other things.

And I'd also like to know why my resolution is changed upon booting. It's supposed to be at 1920x1200 at 60HZ, or something like that, which is the best my monitor can provide. When I boot, however, it's set to 73 or 74HZ, and the screen is extended too far to the right. Not too bad, as I just have to open the screen resolution thing to reset it, but it may get annoying after a while.

---

### Post by rajsarkar on 2005-09-20
[QUOTE=DAXP]That is fine with me - I wanted to get Wine working so I could run Ultima Online, which one of my friends LOVES to play. The only thing I'd like to do now is find out how to install some of the games that are supposed to run on Linux working, as well as Azureus and a few other things.

And I'd also like to know why my resolution is changed upon booting. It's supposed to be at 1920x1200 at 60HZ, or something like that, which is the best my monitor can provide. When I boot, however, it's set to 73 or 74HZ, and the screen is extended too far to the right. Not too bad, as I just have to open the screen resolution thing to reset it, but it may get annoying after a while.[/QUOTE]
 refer to [www.ubuntuguide.org](www.ubuntuguide.org) 

you'll get lot of information there.

-Raj

---

### Post by DAXP on 2005-09-21
It seems the site is down. >_>

---

### Post by aysiu on 2005-09-21
[QUOTE=DAXP]It seems the site is down. >_>[/QUOTE] [The mirror](http://www.frankandjacq.com/ubuntuguide/5.04/index.html) is up, though.

---

### Post by WetWilly on 2005-10-05
the best way to play UO is actually by using a virtual machine... like qemu or vmWare.

---

