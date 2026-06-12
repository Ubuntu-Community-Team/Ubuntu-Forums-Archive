---
title: "Custom kernel: how to?"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by uqbar on 2006-04-19
Hello all.
While I'm not new to Linux I am a newbye with Ubuntu. I'm willing to install 6.06.
And I do know it's not official yet.
My brand new laptop has a LAN card that is not supported by the "shipped" kernel, as already seen [here]("https://wiki.ubuntu.com/LaptopTestingTeam/AsusV6J"). I have to donload the source code and compile it (possibly) as a module.
My simple question is: how can I build an updated initrd image with that driver in it?
Of course I'd be able to do this while offline, because also the WLAN card is not recognized.
Many thanks in advance for the patience!
:D

---

### Post by macdo on 2006-04-19
The link you give also has a solution to your problem... It sends you to [http://www.realtek.com.tw/downloads/downloads1-3.aspx?keyword=8168](http://www.realtek.com.tw/downloads/downloads1-3.aspx?keyword=8168) to download a driver for your ethernet card.

---

### Post by uqbar on 2006-04-19
[QUOTE=macdo]The link you give also has a solution to your problem... It sends you to [http://www.realtek.com.tw/downloads/downloads1-3.aspx?keyword=8168](http://www.realtek.com.tw/downloads/downloads1-3.aspx?keyword=8168) to download a driver for your ethernet card.[/QUOTE]
You're rught. But I need to know the needed kernel options in order to do a full compile.
Then, I need to place the new kernel "back" into the inirtd image. I have no clue on hot to do this!

---

### Post by hw-tph on 2006-04-19
Try the [Ubuntu wiki](https://wiki.ubuntu.com/). It has [several articles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=kernel&titlesearch=Titles) on building your own kernel.

I build my own kernels mostly for special setups (music studio computer needs very low latency and uncommon drivers) and once you have done it a few times you will be configuring kernels in your sleep.


Håkan

---

